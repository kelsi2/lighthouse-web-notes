# TDD with Mocha & Chai

## Topics
  ### Practicing unit testing vis Test Driven Development (TDD) methodology
  ### Using Mocha BDD test framework
  ### Using Chai assertion library
  ### Creating/consuming modules using Node's default CommonJS syntax (module.exports and require)

1. Intro to Testing
2. Exporting/importing code
3. External packages

[Find notes and code here](https://github.com/andydlindsay/aug172020/tree/master/w02d01)

#### Manual Testing
  * Computer does EXACTLY what we tell it to. It's important to have a guess as to the output of our code
  * Manual testing means we are running the code ourselves in node using console.log

#### Unit Testing
  * Function testing: call function, listen for return, and compare that against expected return value
  * Need to use return instead of console.log in our functions so function is giving something back
  * Test using actual vs. expected
    * console.assert(actual === expected, "something went wrong") => if evaluates to truthy the falsy output will not show up
    * This can get lost in the shuffle, so we can bring in an assertion library!
* Node has a bunch of built in packages, see Node docs
  * Can use const assert = require("assert").strict at the top of the file to test our code in node
    * .strict means all assert.equal will test as strict rather than needing to use assert.strictEqual each time
      * Requires less code which means we are more efficient and need to do less debugging (less chance for error if there is less code!)
    * assert is an object (accessing with dot notation)
    * strict equal is the same as ===
  * assert.equal(actual, expected)
    * Can also include an optional message
    * This causes a huge error when it fails so our errors are OBVIOUS!
    * Anything below the error will not be seen due to the error, node will crash

#### Test Files
* Can seperate production code from test files to keep our files clean
  * const assert should be part of test file along with test code
* Use module.exports = <functionName> at the bottom of the original file to allow the test file to import it
* Node considers all files to be modules
* When importing a file with require we don't need to include .js: const sayHello = require("./sayhello") [./ refers to the current folder]
* module.exports can be wrapped in an object! 
  * Need to use const import and when using the function should call it as import.<functionName> because now we are importing an object instead of a function

#### Mocha
* We can save developers time (and money!) by using automated testing with Mocha (another package of code someone created)
* NPM = Node Package Manager (not the only package manager for Node but what we will be using)
* Need to initialize (npm init) before installing any outside packages
  * This creates a package.json file
  * Entry point = first thing that runs when a server starts (not important unless we are building an actual website)
  * GOOGLE LICENSES!!
  * package.json files can be manually edited after creation
  * Can run npm init -y to automatically accept default values
  * package.json manages our files for us, we need to include our dependenceis (ex. mocha)
  * Install with --save-dev mocha (not necessary to have global installation)
    * global installs don't use version control the same way as local installs
    * If it is installed globally it will NOT be included as part of the project (when it is cloned it will not be automatically installed, whereas a local installation will automatically make it part of the package)
  * Should be installed in the top level of the project (not in the test folder)

* Note: Lotide is a library with a number of modules in it
* Can name files with <filename>.test.js and VSCode will recognize this as a test file
  * Everything before the .js is part of the file name, using periods in file names is valid

* In Mocha we use describe() and it()
  * describe says what we are doing followed by a callback function, it() is our actual test
    * e.g. describe("sayHello function", () => {})
  * HOT TIP! Structure function syntax before writing code to make sure syntax is correct
  * describe is a test wrapper which goes around it
  * it("<what are we testing>", () => {});
  * Could have a describe for each aspect of the program we want to test and as many indivitual tests as needed for that section
  * Mocha will pass a test if there is nothing in the it block!
  * Use assert.equal in our it block to create an error

#### TDD
* TDD = Test Driven Development
  * Write the tests BEFORE writing the code to satisfy the tests

#### Ignoring Files/Folders
* Node_modules is automatically installed when we install npm packages
  * Mocha has a whole list of dependencies which need to be installed when we install mocha (those dependencies also have dependencies which get installed)
    * We can actually look through the code of ALL of our installed dependencies, COOL!! :D
  * We don't need to push all of these to Github so we tell git to ignore our node_modules
    * use .gitignore file (hidden file) to list files that git should ignore
      * Just list "node_modules" in the file to tell git to ignore those files

#### Chai Assertion Library
* Uses assert like Mocha
  * Unlike Mocha we can test HUNDREDS OF ASSERTIONS!

* Mocha vs. Chai:
  * Mocha gives describe and it functions
    * Each it is a test and each test should have at least one assertion
  * Chai is an assertion library
    * Designed to work with testing frameworks like Mocha