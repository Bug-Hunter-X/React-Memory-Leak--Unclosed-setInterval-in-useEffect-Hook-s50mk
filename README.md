# React Memory Leak: Unclosed setInterval in useEffect Hook

This repository demonstrates a common React memory leak scenario and its solution.  The bug involves improper usage of the `setInterval` function within the `useEffect` hook, leading to continued execution even after the component is unmounted. This results in a memory leak, particularly noticeable with frequent component mounting/unmounting.

## Bug Description:

The `bug.js` file contains a React functional component that uses `setInterval` to update a counter every second. However, it lacks the necessary cleanup function within the `useEffect` hook's return statement.  This means that the interval continues to run even after the component is unmounted, leading to a memory leak.

## Solution:

The `bugSolution.js` file presents a corrected version. The solution involves adding a cleanup function to the `useEffect` hook. This function, returned by the `useEffect` hook, clears the interval using `clearInterval` when the component is unmounted, preventing the memory leak.

## How to reproduce:

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm start` to start the development server.
4. Observe the component in your browser.  (Note that the memory leak may not be immediately apparent in the browser's developer tools, more frequent component mount/unmount would highlight the issue)

## Learning Points:

- Always include a cleanup function in `useEffect` hooks when using functions like `setInterval`, `setTimeout`, or event listeners that could cause memory leaks.
- Thoroughly test React components to identify and prevent memory leaks, especially those which have asynchronous operations.  