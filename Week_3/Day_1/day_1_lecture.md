# Web Servers 101

## Topics
### Intro to Web Servers(Express-less demo)
### Intro to Express
### Middlware
### Intro to Server-side view templates with EJS

[Notes and code here](https://github.com/hafbau/lecture_notes/tree/master/w3d1)

### HTTP
#### Important things about HTTP
* Protocol for hypertext transfer
* Language agnostic and works over tcp
* http library is pcaked into node.js runtime, no need to import
* Request/response cycle based, only get response to a request
* Very popular protocol that dominates the web
* Has a secure cousin called https

**Request**
#### Methods
* GET
* POST
* PUT
* PATCH
* DELETE

#### URL
* An address, people need to know where you are

**Response**
* Status code (100, 200, 300, 400, 500)
* Body (html, string, json)

**HTTP Stateless**
* Server cannot remember anything about you (it has amnesia!)

#### What do we want the server to do?
* Think of server like a shoe store: we want people to visit our store (url) and make purchases (requests)
  * Server needs to be able to sell them shoes (serve their request)
* Get server set up
```javascript
//const http = require('http :>> ', http); //this returns an object with methods, status codes, and a bunch of stuff we don't understand! Also has a ServerResponse section which includes createServer function, this is what we want!
const http = require('http')
const server = http.createServer() //this will also return an object with info about our server when console.logging
```
* Get it (server) listening for requests
* Get it to respond to request
* obj.on("event", functionToHandleEvent) <-- This is what we are creating

```javascript
server.on("request", (request, response) => { //.on() triggers an event. In this case it triggers an event when it receives a request. Need to be listening for customers, shoe store needs to be open, and we need a clerk to respond to customer requests
const {url, method} = request;
if (url === "/" && method === "GET") { //can use an if statement to change the response depending on the page. This can also be part of const server line and it will still work
  response.end("Home") //we can also make this a function call: response.end(render()) which contains the html for home (rather than writing the whole page in the request code). These functions should be stored and called from seperate files to keep this code tidy. See notes for other functions
} else if (url === "/rand" && method === "GET") {
  response.end(`${Math.random()}`)
} else {
  response.end("Not found")
}
  //response.end("Response from the server!") //this will cause an error because there is more than one response being called. We must remove this for server to run effectively
}) 
server.listen(4337, () => { //need to be listening for request (opening the shop door, if the door is closed no request can be received). Now it is waiting for a request.
console.log("Opened to sell shoes!);
}) //it doesn't matter if server.on or server.listen come first
```
* Check into npx nodemon -L node <filename> for restarting server automatically!!!

### Express
```javascript
//set up server
const express = require("express") //make sure to install express first
const app = express() //this will automatically create our server, you can also think of app as server

//setting up ejs with express. install ejs first
app.set("view engine", "ejs"); //this makes render() available. ejs = embedded js (looks like html with js in it). this line is ESSENTIAL to running ejs. Also need to create a views directory with out ejs pages

//get server listening for request
//app.[method](/url, (request, response) => {}) //this is our template
app.get("/", (req, res) => { //we now don't need the ugly if/else statements! This callback will only be triggered if we are on the given page. We just create get statements for each page
//res.render("filenameOfTemplateToRender", {variablesToBeAvailableForTemplateToUse}) //filename(string) = required, variables(object) = optional
res.render("index" , { //index file needs to have .ejs file extensions. ejs will search in views file for this so be sure it is in the right place. Second argument will contain an object with local variables (stored in index.ejs)
  imgUrl: "...",
  imgSrc: "..."
}) 
res.send("Home from express") //sending a response back from the server
})

app.listen(3000, () => console.log("Server listening on port", 3000)) //best practice to create a variable for port to avoid mistakes