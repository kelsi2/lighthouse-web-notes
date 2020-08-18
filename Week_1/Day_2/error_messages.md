## Syntax Errors
* First line of error messages tell us file and line of error
* SyntaxError: Unexpected identifier will tell us where the error is exactly and means we are missing something usually

## Stack Traces
* More details later but shows file names we didn't use (vm.js, module.js, node.js)
  * Error in code not written by us but caused by our code

## Tricky Errors
* SyntaxError: Unexpected token can indicate the wrong line. This indicates we are missing some type of bracket BEFORE the line where the error occured causing that line of code to not work properly

## Reference Errors
* Indicates an undefined variable (usually caused by typos or not using let/const to define the variable before using it)

## Type Errors
* Indicates something is not a function. In the example it was a matter of just forgetting the function name (using toLower() instead of toLowerCase())

## Conclusion
* Pattern to error messages
  * Always indicates file, line error is on, where in that line the error is occuring
* When we know what the message is telling us we can inspect the code more deeply to find the cause of the error (typos, syntax errors, etc.)