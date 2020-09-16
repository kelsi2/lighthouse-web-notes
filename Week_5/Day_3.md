# SQL From Our Apps

## Topics
### Reading and Writing Application Data using SQL
### Async Execution of Queries (using pg library with promises)
### Sanitization of User Input (how and why)

* node-postgres npm package allows node to talk to sql
* postgres instance url has everything we need for config:
  * // to : = user
  * : to @ = password
  * @ to : = host
  * : to / = port
  * After / = database
* Create new client instance
* client.connect creates a persistent connection to the database
  * This will not stop until we manually stop it with ctrl-c
  * Can use client.end to stop the instance automatically, but this is synchronous while connect is async! So we are immediately closing the instance before it starts
    * Need to use promises instead of callbacks
* Run client.query as a promise
  * This will return an array of objects with the data we need (called rows)

* Use process.argv[2] to take whatever the user enters in node
  * Use switch to for possible cases with a promise for each
  * browse, read, etc.
  * browse just returns the array of objects (response.rows)
  * read needs to use process.argv[3] to obtain an id (which row do you want to see?)
    * Can still console.log response.rows and it will return the correct part of the array
  * Use client.end() as part of each switch case to end after we receive a response

**DO NOT USE TEMPLATE LITERALS!!!! THIS ALLOWS FOR HACKING!!!!**
  * To avoid this pass in the user input as an array
  * Use $1 to refer to the position in the array we want to use (not 0 based), then [id] after the query to call our user input
  * It knows id needs to be an integer, if it's not it will throw an error

* edit requires moret than one input (what id are we editing and what we want to change it to)
  * id can be declared with let as a global variable so we can change it
  * id will be out of order after editing. We need to specify order in the browse query since there is no intrinsic order
  * No return for edit, add or delete (can however use SELECT * FROM ... if we just want to view the table)

* add doesn't require an id, we need name and breed, id will be automatically generated

* Delete needs to take in the id of the cat we want to delete
  * This will remove that id forever since we are autoincrementing, it will always increment to the next value never backwards
  * id is a primary key so adding new info to that key could impact the rest of the database (this is why we use cascade when deleting!)
    * Can use ON DELETE RESTRICT which means you cannot delete records that impact other records in the database. If it has no other connections you can delete it

* To avoid merge conflicts (2 or more edits at once) it's important to have very specific purposes for our files
  * e.g. server file should only be dealing with running the server, nothing else
  * Should also have one file that is running our database, then another file for queries
  * Everything can then be exported so we can use them in different files

* At this point we should not end our client, we want it to run for the lifetime of the application
  * Can return client.query since it returns a promise
  * We still need a .then to tell it to return something specific from the object (in this case response.rows[0] which contains our specific cat)
  * We can call .then again since we have returned a value from the original call
* We can call a callback (whatever was passed in) inside a promise in this case calling callback with response.rows to return our array of cats

* Create a routes file to handle HTTP requests (GET, POST, etc.)
  * Create a router which lives on express (express.Router())
  * Be sure to export router
  * This is the same thing we did in tinyapp except they are being done in a sepearate file from the server (we need to require the router in the server file)
  * set up routes within server to make sure they get passed to routes file using .use
    * Since we have put in /cats in our use call in server we don't need to type that into every route, the server knows this is there already
  
* We need to protect our keys!! Do not upload them to github because this will allow people to connect to our database
  * API keys, passwords, database connection information, etc.
* Need to use environment variables:
  * process.env.PORT || <PORT>
    * Package dotenv will create our environment variables automatically!
    * This should be the first line in our server so the environment variables are created immediately when app is run
    * Create .env file with key value pairs then call them in db config
    * Now no secrets are pushed to github!
    * .env is added to .gitignore
    * Make a copy of the .env file with no values so team knows what the keys are and input their own values