# Node.js Server Unresponsiveness Bug

This repository demonstrates a common Node.js server issue where a long-running synchronous operation in the request handler causes the server to hang and become unresponsive.  The provided `bug.js` file showcases this problem, while `bugSolution.js` presents a solution using asynchronous operations to prevent blocking.

## Bug Description

The server in `bug.js` simulates a long-running task (5 seconds) within the request handler.  Because this task is synchronous, it blocks the event loop, preventing the server from processing any other requests until it completes. This leads to unresponsiveness and poor performance.

## Solution

The solution (`bugSolution.js`) addresses this by using asynchronous techniques (e.g., `setTimeout` or promises) to avoid blocking the event loop.  Asynchronous operations allow the server to handle concurrent requests without performance degradation.

## How to reproduce the bug

1. Clone this repository.
2. Navigate to the repository's directory.
3. Run `node bug.js`.
4. Open multiple browser tabs and try to access `http://localhost:3000`. You will observe that only one request is processed at a time and the server hangs until the first request completes.

## How to run the solution

1. Run `node bugSolution.js`
2. Open multiple browser tabs and try to access `http://localhost:3000`.  The server will now handle requests concurrently without hanging.