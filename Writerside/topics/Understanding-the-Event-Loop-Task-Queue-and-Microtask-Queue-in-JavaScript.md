# Understanding the Event Loop, Task Queue, and Microtask Queue in JavaScript

JavaScript operates on a single-threaded model, meaning it can only execute one operation at a time. To handle multiple tasks efficiently without blocking the main thread, JavaScript employs an event-driven concurrency model. This model uses various internal data structures, including the call stack, task queue (also known as the macrotask queue), and microtask queue, to manage asynchronous operations. Understanding how these components interact is crucial for effective debugging and optimization of JavaScript code.

## Key Internal Data Structures
1. Call Stack
   Definition: The call stack is a data structure that tracks the active function calls in a program. It operates on a Last In, First Out (LIFO) principle.

How It Works:

 - Function Call: When a function is called, a new stack frame is created and pushed onto the call stack. This frame holds the function's context, including its arguments and local variables.
 - Function Execution: As the function executes, it may call other functions, creating additional frames on top of the stack.
 - Function Return: When a function completes, its frame is popped off the stack, and control returns to the previous function.
![image.png](image.png)

### Call Stack Diagram

1. **Initial State:**
    ```plaintext
    +---------+
    |  Empty  |
    +---------+
    ```

   - The call stack is empty.

2. **Call `a()`:**
    ```plaintext
    +---------+
    |   a()   |
    +---------+
    ```

   - Function `a()` is pushed onto the stack.

3. **Call `b()` from `a()`:**
    ```plaintext
    +---------+         +---------+
    |   a()   |         |   b()   |
    +---------+         +---------+
    ```

   - Function `b()` is pushed onto the stack from within `a()`.

4. **Call `c()` from `b()`:**
    ```plaintext
    +---------+         +---------+         +---------+
    |   a()   |         |   b()   |         |   c()   |
    +---------+         +---------+         +---------+
    ```

   - Function `c()` is pushed onto the stack from within `b()`.

5. **Return from `c()`:**
    ```plaintext
    +---------+         +---------+
    |   a()   |         |   b()   |
    +---------+         +---------+
    ```

   - Function `c()` finishes executing and is popped off the stack.

6. **Return from `b()`:**
    ```plaintext
    +---------+
    |   a()   |
    +---------+
    ```

   - Function `b()` finishes executing and is popped off the stack.

7. **Return from `a()`:**
    ```plaintext
    +---------+
    |  Empty  |
    +---------+
    ```

   - Function `a()` finishes executing and is popped off the stack, leaving it empty.

### Explanation

1. **Initial State**: The call stack starts off empty.
2. **Call `a()`**: The function `a()` is pushed onto the stack, marking the beginning of its execution.
3. **Call `b()` from `a()`**: Inside function `a()`, function `b()` is called and pushed onto the stack.
4. **Call `c()` from `b()`**: Inside function `b()`, function `c()` is called and pushed onto the stack.
5. **Return from `c()`**: After function `c()` completes, it is removed from the stack, returning control to function `b()`.
6. **Return from `b()`**: Once function `b()` completes, it is removed from the stack, returning control to function `a()`.
7. **Return from `a()`**: Finally, function `a()` completes and is removed from the stack, leaving it empty again.

This structured format provides a clear visualization of the call stack's changes as functions are invoked and return.

2. Task Queue (Macrotask Queue)
    - Definition: The task queue holds tasks that are deferred for execution. These tasks include callbacks from setTimeout, setInterval, and other asynchronous operations.

How It Works:

 - Task Addition: When an asynchronous operation is completed (e.g., after a timeout), its callback is added to the task queue.
 - FIFO Order: Tasks are processed in the order they were added, following the First In, First Out (FIFO) principle.

![image_1.png](image_1.png)

3. Microtask Queue
    - Definition: The microtask queue handles microtasks, such as promise callbacks and mutation observers, which have higher priority over tasks in the task queue.

How It Works:

 - Microtask Addition: When a promise resolves or a mutation observer triggers, its callback is added to the microtask queue.
 - Priority: Microtasks are executed before tasks, even if they are added after tasks. The microtask queue is processed until it is empty before moving to the task queue.

![image_2.png](image_2.png)

4. The Event Loop
    - The event loop is the mechanism that drives the execution of code, handles events, 

```Javascript
while (true) {
  if (callStack.isEmpty()) {
    while (microtaskQueue.hasTasks()) {
      microtaskQueue.processNext();
    }
    if (taskQueue.hasTasks()) {
      taskQueue.processNext();
    }
  }
}
```

How It Works:

 - Check Call Stack: If the call stack is empty, the event loop proceeds to check the microtask queue.
 - Process Microtasks: The event loop processes all microtasks from the microtask queue before moving to the task queue.
 - Process Tasks: Once the microtask queue is empty, the event loop processes tasks from the task queue.

Example of code execution
```Javascript
console.log(1);

setTimeout(() => console.log(2), 1000);

Promise.resolve().then(() => console.log(3));

setTimeout(() => console.log(4), 0);

console.log(5);
```
### Execution Flow

1. **Synchronous Code Execution:**
   - `console.log(1)` logs `1`.
   - `setTimeout(() => console.log(2), 1000)` schedules a task for later.
   - `Promise.resolve().then(() => console.log(3))` schedules a microtask.
   - `setTimeout(() => console.log(4), 0)` schedules another task.
   - `console.log(5)` logs `5`.

2. **Microtask Execution:**
   - Microtasks (promise callbacks) are executed next. `console.log(3)` is logged.

3. **Task Queue Execution:**
   - Tasks from `setTimeout` are processed. Since the second timeout has a smaller delay, `console.log(4)` logs before `console.log(2)`.
```TEXText 
1
5
3
4
2

   ```

Common Pitfalls
 - Infinite Microtask Loops
 - Be cautious of creating infinite microtask loops, which can block the event loop. For example
```Javascript
 function loop() {
  Promise.resolve().then(loop);
}

loop();
 ```
This code creates an infinite loop of microtasks. Since the microtask queue is never empty, the event loop gets stuck processing these microtasks and doesn’t get a chance to execute tasks from the task queue.