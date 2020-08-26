# Networking with TCP and HTTP

## Topics
  ### What is Networking?
  ### TCP Introduction and Demo
  ### HTTP Fundamentals
    * Request and response nature
    * How it leverages HTTP
    * Important parts of a request
    * Common status codes such as 200, 302, 404, 500
  ### Simple node HTTP Client Example Using Request

[Find notes and code here](https://github.com/tborsa/lectures/tree/master/week2/day3)

* We send a message (request) to the server and the server returns a response with the requested data/information/whatever
  * Acheived with HTTP (Hyper-Text-Transfer-Protocol) => Information highway

* Protocol: Procedure/rules for governing interactions between servers, routers, phones, computers, etc. Determine how to send, format, and receive data between networked devices

**SEE NOTES FOR LAYERS**

## TCP (Transmission Control Protocol)
* #4 (transport layer) on OSI model
* Used to establish networked communication between applications
* Built on top of IP and responsible for dividing file into segments to be sent through IP (internet protocol) and combining segments back into file when they are received
  * Like mailing a letter in multiple pieces that needs to be glued together at the other end
* Connection needs to be established before info is sent
* Congestion control (information can be transfered over any path between A and B so it is not traveling over crowded pathways)
* Error detection (checks if info is received properly as sent)
* Lost data handling
* Adds port
* Focused on accuracy over speed (more worried about it being received properly than quickly)

## Servers
* Need to require npm net
  * Must git init
* 3000 ports are generally reserved for development and testing
* server.on('connection', (conn) => {})
  * on connection process the conn callback

* See notes for more info about requests and server response