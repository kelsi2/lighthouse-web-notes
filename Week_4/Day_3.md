# AJAX

### Intro to AJAX
### XMLHttpRequest (XHR Object)
### AJAX using jQuery
### Use AJAX to submit data to a server
### Without refreshing browser!

### AJAX
* Axynchronous JS and XML
  * XML used to be used in the same way as JSON for retrieving data, now not used
* Used to retrieve information/data - making HTTP requests
* Used to need to refresh to get new HTTP data in Outlook so found a way to make asynch requests using js
  * Now information is retrieved behind the scenes without refreshing
* URL can be relative path

* Default behaviour of a form is to create a new URL wit key value pairs which requires refreshing the page, this is the opposite of what we want!
  * Use this.serialize to create an object of the returned form data, this is the data the server expects but it still refreshes and adds the data to the url
  * event.preventDefault() to change the default behaviour (changing url and refreshing)

### XHR
* XHR object used to interact with servers
  * Can retrieve data without doing full refresh