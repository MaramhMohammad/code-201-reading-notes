# **Class 10 Reading Notes**

## Debugging and Error Handling
Debugging is a process of testing finding and eliminating errors from you code. Debugging in Javascript is sometimes tedious and can require support form JAvascript debugger tools such as ESLINT and other third party tools which can help identify syntax errors. Some common errors in JavaScript include:

- syntax errors
- spelling errors


### Overview: ERROR HANDLING & DEBUGGING
- Order of Execution
  * To find the source of an error, it helps to know how scripts are processed
  * The order in which statements are executed can be complex; some tasks cannot complete until another statement or function has been run
- Execution Contexts
  * The JavaScript interpreter uses the concept of **execution contexts**
  * There is one global execution context; plus, each function creates a new new execution context - they correspond to variable scope
- The Stack
  * The JavaScript interpreter processes one line of code at a time
  * When a statement needs data from another function, it **stacks**, *or piles* the new function on top of the current task

  
  ### Error Objects

Error Objects can help you find where your mistakes are and browsers have tools to help you read them


Properties of an Error Object

|**Property** | **Description** | 
|-------------------|-----------------------|
| `name` | type of error | 
| `message` | Description | 
| `fileNumber` | name of the javascript file | 
| `lineNumber` | line number of error | 


Types of Error Objects

|**Object** | **Description** | 
|-------------------|-----------------------|
| `Error` | Generic error - the other errors are all based on this error | 
| `SyntaxError` | Syntax has not been followed | 
| `ReferenceError` | Tried to reference a variable that is not declared/within scope | 
| `TypeError` | An unexpected data type that cannot be coerced | 
| `RangeError` | Numbers not in a acceptable range | 
| `URIError` | encodeURI(), decodeURI(), similar methods used incorrectly | 
| `EvalError` | eval() function used incorrectly | 


### Handling Errors

1. Debug the script to fix errors
	1. Where is the problem
	2. What exactly is the problem
2. Handle errors gracefully

### Console methods
There are more than just console.log!

- `console.info()` - can be used for general information
- `console.warn()` - can be used for warnings
- `console.error()` - can be used to hold errors
- `console.group()` - groups messages together
- `console.table()` - outputs a table showing objects and arrays
- `console.assert()` - test if a condition is met and write to the console only if evaluates to false


### Breakpoints
- You can pause the execution of a script on any line using breakpoints. 

- You can set multiple breakpoints and step through them one by one to see were a problem might occur

- Conditional breakpoints can be used to if a condition you specify is met

- SUMMARY: ERROR HANDLING & DEBUGGING
  * Debugging is the process of finding errors, it involves a process of deduction
  * The console helps narrow down the area in which the error is located, so you can try to find the exact error
  * JavaScript has 7 different types of errors, each created its own error object which can tell you its line number and gives a description error
  * If you know that you may get an error, you can handle it gracefully using *try, catch, finally* statements; use them to give your users helpful feedback
