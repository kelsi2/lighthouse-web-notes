# Data Flow in MVC

## Model-View-Controller (MVC)
* M => ActiveRecord
* Rails application structure includes application directory (app/) which has subdirectories: models, views, controllers, etc.
  * MVC enforces seperation between data in the application (e.g. user information) and code used to display it which is a common way to structure GUI (Graphical User Interface)
* When interacting with Rails browser sends a request => received by webserver => passed to Rails controller
  * Sometimes view is redered (template converted to HTML and sent to browser)
  * For dynamic sites controller more commonly interacts with a model (Ruby object that represents an element of the site [such as a user] and is in charge of communicating with DB)
    * Controller then renders the view and returns web page to browser as HTML

## MVC in Action
1. Browser issues a request for the /users URL
  * Result of typing URL or clicking a link
2. Rails routes /users to the index action in the Users controller
  * Request hits the router which sends request to the proper controller action based on the URL
  * Controller contains collection of related actions and pages correspond to actions in the Users controller
  * More actions than pages, as the controller also contains create, update, edit, and destroy actions (CRUD)
    * Not for rendering pages but for modifying information about users in the database
  * Suite of controller actions represents implementation of REST, based on representational state transfer
3. Index action asks User model to retrieve all users (@users = User.all)
  * Rails uses Active Record to return all users in the database and stores them in the @users variable
4. User model pulls all users from the database
5. User model returns list of users to the controller
6. Controller captures users in the @users variable which is passed to the index view
  * @users = instance variable (starts with @ sign) => these are automatically available in the views
  * In this example the index.html.erb view iterates through @users and outputs a line of HTML for each one
7. View uses embedded Ruby to render page as HTML
8. Controller passes HTML back to the browser for display

## REST
* REpresentational State Transfer
* Most application components (e.g. users, microposts, etc.) are modeled as resources that can be created, updated, and deleted (correspond to CRUD and HTTP request methods: POST, GET, PATCH, DELETE)
* Helps to decide which controllers and actions to write (structure application using resources that get created, read, updated, and deleted)

## MVC Intro Video
* Model: talks to DB through ActiveRecord (this is for Rails the most popular library but there are others, especially in other languages)
* View: ERB (Embedded Ruby) templates that render HTML (there are alternatives to ERB as well, such as slim)
* Controller: Basically the Project Manager (ensures request is fulfilled by interacting with the other components)
  * Deals with the user by ensuring the model and view do what they are supposed to so the user gets the data they requested

User => Controller => Model => View => User
  * View creats the thing the user sees and the controller makes it all happen by communicating with model, view, and user

* Controller sits behind a router which communicates with the browser
  * The router ensures that the request goes to the correct controller which is responsible for the right information

* root(another way of saying "/") to "products#index" is saying get the products controller followed by index action
  * Old method would be get "/" => { controller: "products", action: "index" } but this has become more concise over time
  * Products controller has index and show methods, we have told it to go to the index method so it will use the model to fetch the information for that page (@products = Product.all.order(created_at: :desc)) then the view to render :index (<= this code is behind the scenes because the name is the same as the method)

* MVC is a design or architectural pattern for user interfaces