# Async-Await

In JavaScript, `async` and `await` are features that simplify working with asynchronous code. They make it easier to write and understand compared to traditional promise chaining. Here’s a deeper look at how they work and some common pitfalls.

### What is `async` and `await`?

- **`async` Function:**  
  When you declare a function as `async`, it automatically returns a Promise. Inside this function, you can use `await` to pause execution until the Promise resolves.

- **`await` Keyword:**  
  The `await` keyword is used inside `async` functions to pause execution until the Promise is resolved. It allows you to write asynchronous code in a synchronous-like manner, making it easier to read.

Here’s a basic example:
```Javascript
async function add(x, y) {
    return x + y; // This returns a Promise that resolves to x + y
}

const AddMarks = async () => {
    // We can use await here to pause execution until add resolves
    const result = await add(5, 10);
    console.log(result); // Logs 15
}
```
## Benefits of `async`/`await` Over Promises

- **Simplified Syntax:**  
  `async`/`await` makes asynchronous code look and behave more like synchronous code. This often makes it easier to read and maintain.

- **Error Handling:**  
  Handling errors with `async`/`await` is straightforward using `try`/`catch` blocks, similar to synchronous code.

- **Avoiding Callback Hell:**  
  With `async`/`await`, you can avoid deeply nested callback functions, which can be difficult to manage and read.

## Sequential Execution Problem with `async`/`await`

While `async`/`await` simplifies asynchronous code, it can lead to sequential execution problems if not used properly. Each `await` pauses the function until the Promise is resolved, which means that code following an `await` will not run until the awaited Promise is resolved. This can cause performance issues if multiple asynchronous tasks could run in parallel.

Here’s an example using `async`/`await`:



````Javascript

async function playBackVideo() {
    try {
        // Login to Netflix
        const user = await loginUser("job@gmail.com", "kjbfdkvhjcxvhjx");
        console.log("Logged into Netflix", user);

        // Get all recently watched videos
        const watchedVideos = await recentlWatchedVideos(user);
        console.log("We have all recently watched videos", watchedVideos);

        // Get details of a selected video
        const videoIndex = 1;
        const selectedVideo = watchedVideos[videoIndex];
        console.log(selectedVideo);

        // Get the details of the selected video
        const selectedVideoDetails = await getVideoDetails(selectedVideo);
        console.log("Data of recently watched video:", selectedVideoDetails);

        // Get the stopping time of the video
        const stoppingTime = await getStoppingTime(selectedVideoDetails);
        console.log(`The stopping time of: ${stoppingTime.video} is ${stoppingTime.stopping}`);

        // Render the video
        renderVideo(selectedVideoDetails, stoppingTime);
    } catch (error) {
        console.error("An error occurred:", error);
    }
}

````
In this example:

- Each `await` pauses execution until the Promise resolves.
- If each asynchronous function takes time to complete, the code will run sequentially, waiting for each Promise to resolve before moving on to the next task. This can result in slower performance if tasks can be performed concurrently.

## Resolving Sequential Execution Issues

To avoid unnecessary delays, you can run multiple asynchronous operations in parallel using `Promise.all`:


```Javascript
async function playBackVideo() {
    try {
        const user = await loginUser("job@gmail.com", "kjbfdkvhjcxvhjx");
        console.log("Logged into Netflix", user);

        // Run both functions in parallel
        const [watchedVideos, selectedVideoDetails] = await Promise.all([
            recentlWatchedVideos(user),
            getVideoDetails('some video') // This is just an example
        ]);

        console.log("We have all recently watched videos", watchedVideos);
        console.log("Data of recently watched video:", selectedVideoDetails);

        // Continue with further steps...
    } catch (error) {
        console.error("An error occurred:", error);
    }
}

```

`async`/`await` simplifies asynchronous code by allowing you to write code that appears synchronous, making it easier to understand and maintain.

### Sequential Execution Problem

Each `await` pauses execution until the Promise resolves, which can lead to performance issues if not managed properly.

### Parallel Execution

Use `Promise.all` to run multiple asynchronous operations concurrently when possible.

