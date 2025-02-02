# Unhandled Error in Express Route Handler: Invalid User ID

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  Specifically, the provided code lacks checks for non-numeric user IDs, leading to potential crashes or vulnerabilities.

## Bug Description

The `GET /users/:id` route attempts to parse the `id` parameter as an integer using `parseInt()`.  If the parameter is not a valid integer (e.g., a string or a non-numeric value), `parseInt()` will return `NaN`.  The subsequent `find()` operation will then fail silently, potentially leading to unexpected behavior or server crashes.

## Bug Solution

The solution involves adding robust error handling to the route handler. This includes:

1.  Checking if the `userId` is a valid number using `isNaN()`.
2. Handling the case where the user is not found with appropriate error codes and responses.

## How to Reproduce

1. Clone this repository.
2. Install dependencies: `npm install express`
3. Run the application: `node bug.js`
4. Make a request to `/users/abc` to observe the unhandled error.  Then, run `node bugSolution.js` and test again to see the corrected behaviour.
