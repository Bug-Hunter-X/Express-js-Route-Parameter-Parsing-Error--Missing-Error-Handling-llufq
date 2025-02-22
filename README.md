# Express.js Route Parameter Parsing Error: Missing Error Handling

This repository demonstrates a common error in Express.js applications where insufficient error handling is implemented when parsing route parameters.  Specifically, the `/users/:id` route lacks error handling for scenarios where the `:id` parameter is not a valid integer.

## Bug

The `bug.js` file contains the buggy code.  It attempts to find a user based on the provided ID. If the ID is not an integer, `parseInt(userId)` returns `NaN`, which causes the `find` method to fail silently or throw an error depending on the implementation of the `users` array.

## Solution

The `bugSolution.js` file provides a corrected version.  It explicitly checks if `parseInt(userId)` results in `NaN` and handles the error appropriately by returning a 400 Bad Request status code.

## How to Reproduce

1. Clone the repository.
2. Navigate to the project directory in your terminal.
3. Run `npm install express` to install the necessary dependencies.
4. Run `node bug.js` and try accessing the `/users/:id` route with a non-numeric ID. Observe the behavior.
5. Run `node bugSolution.js` and repeat step 4. Note the improved error handling.

## Lessons Learned

Always validate user inputs, especially those coming from route parameters. Handle potential errors gracefully to prevent unexpected application crashes and provide informative error messages to the client.