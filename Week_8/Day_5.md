# Intro to Ruby

## Topics
### Ruby vs. JS/Node
  * Conventions
  * Paradigms
  * Usage in the wild
  * Concurrency model
  * Inheritance model
### Similarities to JS/Node
### Blocks in Ruby
### Debugging Tips
  * Using raise with .inspect

[Notes here](https://gist.github.com/kvirani/c9ee855f2c48740e3c7d105f49adc52e)

Research and Reflect topic idea: Intersection of machine learning/AI and web dev

#### Why are we starting another language already?
* Happens often on the job (learn another language because you need it for the job)
* Become polyglot (many languages, many tools in your toolbelt)
* Learning to learn

#### Why Ruby not a different language?
* Ruby is more likely to be used for web dev (not necessarily for other things like data science, but very good for web dev)
* See articles in slides
* Used to be primary language, switched to JS 2016 because of direction tech was going

### Jungle
* eCommerce app
* Inherit code base (more real world)
  * Work on bug fixes and improvements
* Integrated with Stripe (payment software)
* How to be productive when you don't know loanguage, code base, etc.

### History
* Ruby popularized by Rails in 2004 (initiallly invented 1993 but fairly unknown)
* Integrated in OS X 2006 with Rails
* Main premise is to focus on developer happiness (easy to read, learn, and understand)
  * JS has been influenced immensely by this and changed to make it easier to learn and understand

TIP: **Try to cause errors by breaking things and have a hypothesis about what the result will be**
* Being wrong about what will happen helps to learn about a new language and helps us remember more than being right about something

* Gem === external library like npm
* Bundler: manages gems so you know what gems you are using and the version
  * Allows for control over the gems you have installed in your project (just like npm install, this creates a Gemfile [same as a package.json but for Ruby])
* rubygems.org (like npm, find new packages)

**.inspect for debugging**
 * developer friendly string so we can see what we are looking at

* Ruby implicitly calls .to_string when using response (automatically uses response.body.to_string)
  * Like a default to help you get what you are most likely to be calling

* .class.inspect to find the type of whatever it is (string, integer, etc.)
  * Can also infer this often from inspect because it will put quotes around a string

* JSON.parse(response.body)
  * This will appear as a # (Hash [Ruby term], Dictionary, Object) when using inspect
  * Can access this the same way as objects in JS (key = value)
    * Now we have extracted just the value (the ip we are trying to access in this case)

* For template strings in Ruby we use #{} instead of ${} but they work the same way

* JS Concurrency Model: Events Loop (easy to tell the order things will happen)
* Ruby Concurrency Model: Threads, Processes (Harder to achieve async programming than in JS because things are not in a stack, they happen all at once)
  * Rails needs to be more concerned about this, in Ruby we just write the logic for how to deal with one request. Not concerned with dealing with hundreds of requests a time

* Error handling:
  * begin
  * rescue StandardError => e
    puts ...error message ... 
  * end
    * This can be done for all code so we have error handling in place and code can continue if something is wrong

### Sinatra
* Equivalent of Express (unlike Rails which is a huge framework)
* Best for APIs, lightweight and very fast
* erb === embedded ruby (like ejs)

**RuboCop like eslint, need to install**
* ERB syntax highlighting