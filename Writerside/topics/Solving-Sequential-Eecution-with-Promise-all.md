# Solving Sequential Eecution with Promise.all

## Using `Promise.all` to Improve Asynchronous Code Execution

In JavaScript, managing asynchronous operations efficiently is crucial for performance and readability. One common approach is using `Promise.all`, which allows you to handle multiple asynchronous operations concurrently. Here’s how you can use `Promise.all` to simplify your code and solve the sequential execution problem.

### Sequential Execution Problem with `async`/`await`

When using `async`/`await` without `Promise.all`, asynchronous operations are executed sequentially. This means each operation must complete before the next one starts, which can lead to slower performance if the operations could be executed concurrently.

#### Example of Sequential Execution:

````Javascript
async function fetchSequential() {
    const data1 = await fetchData1();
    const data2 = await fetchData2();
    const data3 = await fetchData3();
    return [data1, data2, data3];
}
````
In this example, `fetchData2` waits for `fetchData1` to complete, and `fetchData3` waits for `fetchData2` to complete. This sequential execution can be inefficient if `fetchData1`, `fetchData2`, and `fetchData3` can run independently.

## Using `Promise.all` for Concurrent Execution

`Promise.all` is a method that takes an array of promises and returns a single promise that resolves when all the promises in the array have resolved. This allows you to execute multiple asynchronous operations concurrently, improving performance.

### Example Using `Promise.all`:
```Javascript
const fetchData1 = () => new Promise((resolve) => setTimeout(resolve, 1000, "data1"));
const fetchData2 = () => new Promise((resolve) => setTimeout(resolve, 1000, "data2"));
const fetchData3 = () => new Promise((resolve) => setTimeout(resolve, 1000, "data3"));

const fetchedPromiseAll = async () => {
    const data = await Promise.all([fetchData1(), fetchData2(), fetchData3()]);
    return data;
}

fetchedPromiseAll().then((data) => {
    console.log(`This is concurrent data fetch: ${data}`); // Output: This is concurrent data fetch: [ 'data1', 'data2', 'data3' ]
});

```
In this example, `fetchData1`, `fetchData2`, and `fetchData3` are executed concurrently. `Promise.all` waits for all promises to resolve and then returns the results in an array.

## Refactoring Code with `Promise.all`

Let’s apply `Promise.all` to refactor code that handles multiple asynchronous operations:

```Javascript
function loginUser(email, password) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("We have logged in");
            resolve({ userEmail: email });
        }, 3000);
    });
}

function recentlWatchedVideos(user) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("We have the data of all videos");
            resolve(["star wars", "The Mando", "Prison Break"]);
        }, 3000);
    });
}

function getVideoDetails(video) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("We are getting the details of one video");
            resolve({ video, name: video });
        }, 3000);
    });
}

function getRecentTimestamp(videos) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("Got recent timestamp");
            resolve({
                videos,
                recentVideo: videos[1],
                timestamp: "00:25:30",
            });
        }, 1000);
    });
}

function getStoppingTime(video) {
    return new Promise((resolve) => {
        setTimeout(() => {
            console.log("Got stopping time");
            resolve({
                video,
                stoppingTime: "00:20:00",
            });
        }, 500);
    });
}

async function playBackVideoWithPromiseAll() {
    try {
        // Login to Netflix
        const user = await loginUser("job@gmail.com", "password");
        console.log("Logged into Netflix", user);

        // Get all recently watched videos
        const watchedVideos = await recentlWatchedVideos(user);
        console.log("We have all recently watched videos", watchedVideos);

        // Use Promise.all to handle multiple asynchronous operations concurrently
        const [recentlyTimeStampedData, stoppingTimeData] = await Promise.all([
            getRecentTimestamp(watchedVideos),
            getStoppingTime(watchedVideos[0])
        ]);

        // Extract and log results
        const { recentVideo, timestamp } = recentlyTimeStampedData;
        const { stoppingTime } = stoppingTimeData;
        console.log(`The timestamp of ${recentVideo} is ${timestamp}`);
        console.log(`The stopping time of ${recentVideo} is ${stoppingTime}`);

    } catch (error) {
        console.error("Error:", error);
    }
}

playBackVideoWithPromiseAll();

```
### Sequential Execution Problem

Using `async`/`await` alone can lead to sequential execution, where each operation waits for the previous one to complete.

### `Promise.all` Solution

`Promise.all` allows concurrent execution of multiple promises. It resolves when all promises in the array have resolved, improving performance.

### Refactoring with `Promise.all`

By using `Promise.all`, you can handle multiple asynchronous operations concurrently, making your code more efficient and easier to manage.

