# ERB (Embedded Ruby)

* ERB is very similar to EJS templates, they render the view we see on the page
* _ in front of the name means a partial
  * In the view we say render "<fileName>" within erb tags
* We can render a path string instead of a symbol (like :show) if we want to direct to somewhere outside of the normal path Ruby would follow to find that template (in this case ProductsController#show)
* Instance variables (params) are passed through the controller to the view, so they are not rendered as part of the template the way EJS does
* The layouts folder contains templates (by default application template) which contains the html for rendering the views templates so we don't need to repeat this code for each view
  * Can pass instance variables (product: @product) here so you can use a regular variable in the view => known as a local variable
* render is a method with two arguments (partial, locals [can be as many as you want, this is one hash with key value pairs])

# Navigating Rails
* Rails gives quite a bit of info in the console (queries that are running, renders, where is the code that is running this, etc.)
* For debugging can use raise to throw an error
  * Whatever is in the raise call shows on the browser rather than looking through the log for a puts call
  * You can do this with a variable to see what it looks like (raise @category.inspect will show us exactly what is in that variable)
* Use ctrl-p to find a file by name
* In ERB templates you can say <%= debug @category %> which renders a serialized version of the object, you can see all the attributes attached to it
* Use find in project as much as you need to to find code that refers to the thing you are looking for