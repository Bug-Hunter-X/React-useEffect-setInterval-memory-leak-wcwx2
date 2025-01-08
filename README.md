# React useEffect setInterval memory leak

This repository demonstrates a common mistake in React applications involving the `useEffect` hook and `setInterval`.  The example showcases a memory leak that occurs when `setInterval` is used without proper cleanup.

## Problem

The provided code creates a simple counter that increments every second using `setInterval`.  However, it lacks a cleanup function to stop the interval when the component unmounts. This leads to unnecessary interval calls after the component is no longer needed. This results in a memory leak, which can significantly affect the application's performance, especially with many such components.

## Solution

The solution involves returning a cleanup function from the `useEffect` hook. This function clears the interval when the component is unmounted, preventing the memory leak.

## How to reproduce

1. Clone this repository.
2. Run `npm install` to install the necessary dependencies.
3. Run `npm start` to start the development server.
4. Observe the continuously increasing count in the browser.  Open the browser's developer tools and check the memory usage over time to observe the memory leak.

## How to fix

Refer to `bugSolution.js` for the corrected code.  The key change is adding a `clearInterval(intervalId)` call in the cleanup function.