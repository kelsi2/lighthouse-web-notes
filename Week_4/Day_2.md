# Client Side JavaScript and jQuery

## Topics
### Intro to Client Side JS
  ### DOM
  ### Events and Event Propagation
  ### Event Object
  ### Navigator Object
  ### Document Object
  ### Using DevTools (sources tab) and Debugger
### Intro to jQuery
  ### Why does it exist?
  ### How much additional behaviour does it add to the browser
  ### Library or framework? Why?
  ### Why is it important to learn / use jQuery?
  ### Event handling with jQuery
  ### Element creation with jQuery

[Notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w04d02)
[Lecture here](https://us02web.zoom.us/rec/play/WAnW-l_K_CmCa5lLASLUHzC_BgjXlpeQDPWmv2zjes4zrDSmVrJDZSzSmMjTVqyv0sHPWB3pRlB7-vZ3.VHQD6fRPvYix9Ou2?startTime=1599582152000&_x_zm_rtaid=Wnq9iXCYTLSTrAJP0eZO9w.1599668681234.9ae5c20b8f273e70d0e2c2eb2425b793&_x_zm_rhtaid=826)

* process refers to node, it will not work in the browser
  * process === window (represents entire browser tab)
* window.document represents the page we are looking at
* Whatever is between two tags (h1, p, div, etc.) is considered a child of those tags (the parents)
* append === push
  * Elements are not real until they are appended. They are basically floating in space
* Use prepend to add to the beginning (like unshift for arrays)

## jQuery
* Events are always happening but we have to listen for them
  * We can do this with jQuery to use much less syntax
* We only listen to the things we find important, not all events
* document.ready should surround all of the page js to ensure the page is fully loaded before calling anything
  * script tags should be placed at the very bottom of the html body to ensure the code works regardless of other issues