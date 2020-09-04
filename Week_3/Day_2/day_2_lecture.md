# CRUD with Express

## Topics
### Implementing CRUD over HTTP with Express
### Render vs. Redirect pattern in multi-page apps
### Forms (action, method)
### Links (a tags) compared to Forms
### Exploring the DevTools network tab in Chrome
  #### Explore the full lifecycle of GET -> Submit Form -> POST -> Redirect -> GET
  #### Query string params vs. Post Data params (and how they are encoded)
### Express debugging tactics

[Notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w03d02)
[Lecture here](https://us02web.zoom.us/rec/play/SLTGj5seENwpK2vESr6ZCK1R5-vY-rXDEyA4gOUduKwhjl4Wr0OwDfLiO61kgCkWvTNdBT8f3fnkxz3c.UkO6TzJHcTPo26jN?startTime=1598977171000&_x_zm_rtaid=9d-F1vRrRQm6aY4r3ThDow.1599052624963.d4e0a94a89e66b58a66581e3dbe9945d&_x_zm_rhtaid=500)

### CRUD
* Create, Read, Update, Delete
* Basic operations you can perform on a resource
* Also BREAD: Browse, Read, Edit, Add, Delete => More clear description of what we can do to a user
  * Browse returns everything, Read returns one single data point

* process.env.PORT means we will use the port environment variable if it's available, otherwise we use the defined variable (basically a default)

**add NPM Morgan for ALL express apps!!**
  * This should be installed as a normal dependency, not a dev dependency, it is middleware so should be visible in production
  * app.use(morgan('dev'))
  * This will log all requests along with the result

* Easiest to use objects because then we can use keys (arrays require iteration, objects don't)

### BREAD
* Browse: GET 
  * /students to return all students in the object
  * Create students.ejs to iterate the studentDatabase

* Read: GET
  * /students/:student_id to access a particular student (/students/7 will return student 7 for example <-- Note we drop the : after the / )
  * req.params to access the object (will return an object with the student_id: "<value in url>")
  * studentDatabase[studentID] <--Think of square brackets as saying @... this information is DYNAMIC so dot notation won't work
  * Create student.ejs to return one student (no need to iterate)
  * To create links we need to use ejs to access the url (e.g. a href="/students/<%= studentID %>")

* Edit: POST
  * Exchanging information with the server so using post
  * Editing a preexisting student so use /students/:student_id (NOTE: colon indicates a variable. We use this in the server but not in the ejs file)
  * Form fields (see notes):
  <input
  <label>Set year: </label> <-- This tells the user what to put into the field
  type= "number" <-- forces the data to be a number type
  name= "year" <-- whatever the user entered
  />
  * Default behaviour is to make a GET request to the same page where the form was submitted because we haven't told it where to go
    * We instead need to use a POST request (add to form method)
    * Add studentID to the templateVars so that is passed along with the students object and can be easily included in the form action field
  * Can add a button to submit form, must have type "submit" or it will not work!!
  * Post request has a body (this is what we return with req.body), this will include whatever is returned by the form the user fills out --> must install body parser middleware
    * By default urls are encoded, body parser parses them for us so we can see what is in the body
  * Need to add redirect to complete the request


* Add: POST
  * Use /students because we aren't accessing a specific student, we are only adding to the database
  * AddForm GET /students/new, then app.post to receive the information from the app.get form
  * Only need to use res.render in the get request because we are generating a static page with a form (GET request)
  * POST request should contain an object with the expected structure (we add the submitted info to this object so it can be added to our database)
    * This can then be added to the studentDatabase
  * Once again we need to redirect (always do this with a POST request), in this case redirect to the /students page so we can see the new student

* Delete: POST
  * POST request since we are UPDATING DATA
  * /students/:student_id/delete to make it a different request from /students/:studentID
  * Create const studentId again so we can access it
  * delete studentDatabase[studentId]
  * Redirect again to /students page so we can see that it has been deleted
  * On student.ejs page we need to create a new form since the delete action is different (we are not updating anymore)
    * All we need is a button (Delete student) since we aren't asking for any information

**GET = Retrieve information, POST = modify information**