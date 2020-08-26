# Asynchronous Control Flow

## Topics
  ### Asynchronous Control Flow
  ### setTimeout and setInterval Functions
  ### Filesystem functions and their async nature
  ### Events and event handling, another asynchronous topic

  [Find lecture notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w02d02)
  [Find lecture recording here](https://us02web.zoom.us/rec/play/vJQuJOio_Wk3HIaSuASDCvYsW9S5fa-shCJIrPEIxB20BnlXO1ryMrZDY-DBSHzpyEWcOteuvgYoH7fZ?startTime=1598372062000&_x_zm_rtaid=HNqR1Dl6T0eN2yEOg5KSog.1598455092539.937e9f5ce5c8502e1274858785382931&_x_zm_rhtaid=680)

## Side Topic: Mock Test Review
[Find notes and code here](https://github.com/andydlindsay/aug172020/tree/master/breakout-mock-exam-review)
[Find recording here](https://us02web.zoom.us/rec/share/6Ituf6rT_0ZJeoXx0m-GXKkdGa_LT6a823cXrqVfzRpg1Ioo_rvbytkZoOcEl8ad) password: a0s.e*pE

* Javascript = synchronous programming language (everything runs in order)
  * setTimeout allows us to change the order of execution (we can set a delay in milliseconds [e.g. 1000 === 1 second])
  * Synchronous code will still happen as normal, then asynchronous will be processed
  * Can use setTimeout with 0 second delay to force that code to run immediately after the other code (because async runs after sync code)

* In an object a variable with an _ in front means the value is private (as in please don't change this value), javascript has no way to create hidden values so this is the closest option

**Async functions DO NOT HAVE RETURN VALUES!**
  * Use callback functions to call the data from the async function

* All the async timers start running at the same time (as soon as the synchronous order hits it, the timer starts)
  * The command will execute once the timer runs out OR when the current synchronous processes are completed

### setInterval
* setInterval is recursive so when the interval elapses it will call itself again and continue to call forever unless given a base case
  * Can cause memory leaks so a bit dangerous (interval will continue to run unless cleared so the browser will run out of memory because processes will continue to run in the background even if we aren't using them anymore)
  * Can use clearInterval to end the process
* To clearInterval we need to use a timeout because it will automatically run synchronously which means our interval will produce no output
* Can also clear interval from within the setInterval block but counter needs to be declared outside of the setInterval block
  * Functions throw away their values every time but if it is outside of the function the increment will be stured

### File System Functions ("fs")
* Built into node
* fs.readFile(path[, options], callback)
  * Options are optional (square brackets)
* fs.readFileSync(path[, options])
* ! will create an outline of an html doc (using Emmet)
* const fs = require('fs') to bring in fs (similar to chai)
* fs.readFileSync()
  * Return a file as a parameter
  * This is synchronous so it will execute as soon as the file is called
  * Can add {encoding: 'UTF-8'} to return the actual contents of the file rather than a hex code

* fs.readFile() is asynchronous
  * Takes in a callback with no return value
    * error and data
  * Also uses the same parameters as readFileSync