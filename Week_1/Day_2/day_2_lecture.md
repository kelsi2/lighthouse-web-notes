# Day 2 Lecture Notes

[Lecture slides here](https://docs.google.com/presentation/d/1m3R_aN4S5YoCBmXRbjaZQGatygWyZXYLcN-fkcP_HWA/edit)
[Lecture notes and code here](https://github.com/tborsa/lectures/tree/master/week1/day2)

## Curriculum

* Fundamental Fridays
  * Programming tests
    * Mock test this week
    * FOCAL, not building apps
    * See where we are at, assessing progress
  * Computer science topics
    * Fundamental programming topics (math, terms, etc.)
  * Research, reflect, and write

* See slides for curriculum breakdown by week

### Four Major Solo Projects

* W 3, W 4, W 7-8, W 9-10

### Four Tech Interviews

* W 2, 3, 8, 9

### Multiple Choice Quizzes

* Only in first four weeks

## Basic Git Workflow

### GIT
* Repository: System for tracking changes in source code during development
  * Remembers history of code
  * Documents changes with commit messages, listing author of changes
  * Remote git repo to back up data
  * Undo changes
  * Easy to collaborate

1) "git init" to initiate empty repo
  * File now includes .git file to track changes
2) "git add ." => add everything in the folder
  * "git status" to see what is happening
3) "git commit -m '...'" to add message explaining what the commit is
  * Have now added first node in chain of commit history!

### Git Gud
#### Local
* Working directory: local folder of all files 
  * Can only be in one (current) state

=> git add
* Staging Area
  * Check over added files to be sure they need to be added to localrepo

=> git commit
* Local repo
  * Includes all states (past and current) of a directory
    * Allows you to move back and forth in time to different states

=> git push
#### Remote
* Remote repo

### Git Commands
* Init: initializes a git repository for the current directory/folder.

-->
* Add: Adds the specified files to the staging area for future commits.

-->
* Commit: Saves the staged files to the local git repository. (commit often)

-->
* Remote: Adds a remote repository

-->
* Push: Updates the remote git repository with any new changes in the local git repository.

## Writing Code Incrementally

* Break problems into smaller steps
  * Easier to isolate errors and debug
  * Refactor/improve code as we go
* Lint code as you go
  * Avoid copy/pasting!
* console.log to understand data
* Use node debug with debugger

### Goal: 
Write a node program that takes in an unlimited number of command line arguments, goes through each and prints out the sum of them. If any argument is not a whole number, skip it. Do support negative numbers though. 

* NOTE: DO NOT CODE ALONG! Pay attention and collaborate/give feedback
  * Take notes and ask questions
  * Leave lecture with general understanding and research/do activities to understand specifics

* Create pseudocode in plain english first THEN move to JS
  * Worry about syntax later
  * Each block of logic should have a function to do that task
  * SEE LECTURE FILES FOR CODE


1) Get the input/arguments/numbers from user
    * process.argv only works in node
    * slice off first two indexes to access args
    * test function using console.log

2) Check if input is whole number

      i) Check if input is number
  
      ii) Check if number is integer

  * Remember our checks

3) Filter to remove/skip non-integers (merge into the check?)

  * Use "Number()" to check if input is a number
  * If number is true, use "isInteger()" to check if number is an integer
  * Return integer or false
  * Test using console.log() --> use multiple test cases! (strings, integers, decimals, negative numbers)

4) Add a list of numbers together

* new function: sumIntegerValues
  * Loop through args, use checkInt function, then sum
* Input = array
* Create sum variable outside loop
* For/of loop, console(log inside to check if this loop works)
  * Returns each element in array
* Check if input is valid integer
  * If true, add input to sum
* Test using console.log(), should only sum integers and ignore other inputs
* Return sum OUTSIDE for loop

5) Print/display the calculated sum 

* Get args from user
  * Test with console.log()
* Use args to get sum based on user inputs
  * Test with console.log()
* Clean up code (remove extra test console.logs, remove extra comments, make sure variable names are clear), optimize where possible (can we simplify?)
* Create string to display calculated sum ('The total sum is: ' + sum)

* Functions should have ONE purpose, should be easy to explain what each function is doing
  * How can our functions be simplified? Do they need to be split?

* Can create function to include variables where we call the functions (this is better than using global scope, prevents variables from being accidentally redefined later)

* Comments should explain why something is done or context, not necessarily to explain what is being done (that should be clear if code is written well)
  * Can also use comments for organization (create sections of function declarations, for example)

## Debugging

1) Logical errors
  * Use console.logs and debugger to understand why
  * Dry run of code in your head
2) Parsing errors
  * Look for syntax errors and research
  * Practice reading errors before copy pasting to Google
  * MDN for examples
  * Experiment with Googling
    * Included relevant information?
    * If mentor googles pay attention to what they search
    * Do you need mentor support?

## Tools

[JavaScript Tutor](http://pythontutor.com/javascript.html#mode=edit)

[Node Debugger](https://nodejs.org/api/debugger.html)

  * node inspect <filename>