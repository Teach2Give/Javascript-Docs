# Promise

# What is a Promise?

A **Promise** is a JavaScript object representing the eventual completion or failure of an asynchronous operation. It provides a way to handle asynchronous operations more elegantly compared to traditional callback-based approaches.

## Promise States

A Promise can be in one of three states:

- **Pending**: Initial state, neither fulfilled nor rejected.
- **Fulfilled**: The operation was completed successfully.
- **Rejected**: The operation failed.

![image_4.png](image_4.png)

## Basic Syntax

Creating a Promise:
```javascript
let promise = new Promise((resolve, reject) => {
    // Asynchronous operation
    if (/* operation successful */) {
        resolve('Success message'); // Resolve with a success message
    } else {
        reject('Error message'); // Reject with an error message
    }
});
```

# How to Consume a Promise

Once a Promise is created, it needs to be consumed to handle the result of the asynchronous operation. Consuming a Promise is done using the `.then()` and `.catch()` methods, which allow you to define how to handle success and failure, respectively.

## Consuming a Promise

### Handling Success with `.then()`

The `.then()` method is used to specify what should happen when the Promise is fulfilled (i.e., the asynchronous operation completes successfully). It takes a function as an argument that receives the result of the Promise.

**Syntax:**
```javascript
myPromise.then(result => {
    // Handle success
});
```

#### Consuming a Promise:
```Javascript
const myPromise = new Promise((resolve, reject) => {
  // Asynchronous operation
  if (/* operation successful */) {
    resolve(value); // Fulfilled
  } else {
    reject(error); // Rejected
  }
});
```

# Handling Promises

## Handling Success with `.then()`

The `.then()` method is used to specify what should happen when the Promise is fulfilled (i.e., the asynchronous operation completes successfully). It takes a function as an argument that receives the result of the Promise.

**Result:** The value that was passed to the `resolve()` function when the Promise was fulfilled.

## Handling Failure with `.catch()`

The `.catch()` method is used to specify what should happen if the Promise is rejected (i.e., the asynchronous operation fails). It takes a function as an argument that receives the error or reason for the failure.

**Syntax:**
```javascript
myPromise.catch(error => {
    // Handle failure
});
```

**Error:** The value that was passed to the `reject()` function when the Promise was rejected.

## Example

Here's an example of how you might consume a Promise:

````Javascript
let myPromise = new Promise((resolve, reject) => {
    let success = true; // Change to `false` to test rejection
    if (success) {
        resolve('Operation was successful');
    } else {
        reject('Operation failed');
    }
});

myPromise
  .then(result => {
    console.log(result); // Logs: 'Operation was successful'
  })
  .catch(error => {
    console.error(error); // Logs: 'Operation failed'
  });

````
In this example:

- If success is true, the Promise is fulfilled and the message 'Operation was successful' is logged to the console.
- If success is false, the Promise is rejected and the error message 'Operation failed' is logged to the console.

By chaining `.then()` and `.catch()`, you can handle both the successful and failed outcomes of the Promise, making it easier to manage asynchronous operations.


## Example: Handling Callback Hell with Promises

Callback hell, also known as "Pyramid of Doom," occurs when multiple nested callbacks make the code difficult to read and maintain. Promises can simplify this by chaining `.then()` calls.

**Scenario:** We need to:

1. Log in to Netflix.
2. Get all recently watched videos.
3. Retrieve details of a specific video.
4. Get the timestamp of the video.

### Callback Hell Example:
```Javascript
login(email, password, (error, user) => {
  if (error) {
    console.log("Login failed");
  } else {
    getRecentlyWatchedVideos(user, (error, videos) => {
      if (error) {
        console.log("Failed to get videos");
      } else {
        getVideoDetails(videos[0], (error, videoDetails) => {
          if (error) {
            console.log("Failed to get video details");
          } else {
            getVideoTimestamp(videoDetails, (error, timestamp) => {
              if (error) {
                console.log("Failed to get timestamp");
              } else {
                renderVideo(videoDetails, timestamp);
              }
            });
          }
        });
      }
    });
  }
});
```
Rewriting with Promises:

```Javascript
// Define the functions returning Promises

function loginUser(email, password) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Logged into Netflix");
      resolve({ userEmail: email });
    }, 3000);
  });
}

function recentlyWatchedVideo({ userEmail }) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Retrieved recently watched videos");
      resolve({
        userEmail,
        videos: ["Star Wars", "The Mando", "The Lord of The Rings"]
      });
    }, 3000);
  });
}

function getDetailsOfOneVideo(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Getting details of the video");
      resolve({ video, name: "The Mando" });
    }, 3000);
  });
}

function getTimeStamp(video) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log("Getting timestamp of the video");
      resolve({ video, stoppingTime: "00:24:45" });
    }, 3000);
  });
}

function renderVideo(video, timestamp) {
  console.log(`Rendering ${video} from timestamp ${timestamp}`);
}

// Chain Promises

loginUser("job@gmail.com", "kjvhjsdvhj")
  .then(user => recentlyWatchedVideo(user))
  .then(videos => {
    const searchElement = "The Mando";
    const videoIndex = videos.videos.indexOf(searchElement);
    
    if (videoIndex !== -1) {
      return getDetailsOfOneVideo(videos.videos[videoIndex]);
    } else {
      throw new Error("Video was not found");
    }
  })
  .then(video => getTimeStamp(video))
  .then(({ video, stoppingTime }) => renderVideo(video, stoppingTime))
  .catch(err => {
    console.log("Error:", err);
  });
```


## Explanation

- **loginUser:**  
  Logs in the user and returns a Promise that resolves with user data.

- **recentlyWatchedVideo:**  
  Retrieves recently watched videos for the logged-in user and returns a Promise.

- **getDetailsOfOneVideo:**  
  Retrieves details of a specific video and returns a Promise.

- **getTimeStamp:**  
  Retrieves the timestamp for a video and returns a Promise.

- **renderVideo:**  
  Renders the video from a given timestamp.

### Promise Chain

- Each `.then()` handles the resolved value from the previous promise.
- `.catch()` is used for handling any errors that occur in the chain.

### Benefits of Using Promises

- **Improved Readability:** Flat promise chains are more readable compared to nested callbacks.
- **Error Handling:** `.catch()` handles errors from any step in the chain.
- **Maintainability:** Code is easier to maintain and debug with promises.

Using promises simplifies handling asynchronous operations and avoids the pitfalls of callback hell, making your code more structured and easier to follow.
