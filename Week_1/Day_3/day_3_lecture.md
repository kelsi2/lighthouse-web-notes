# Objects in JS

## Topics
  ### Primitive data types
  ### Object fundamentals
    - Advantages for data lookup vs. arrays
    - How objects are passed to functions
  ### Functions as object methods
    - Using this when inside an object's function

* Find lecture notes here: [Lecture notes and code](https://github.com/tborsa/lectures/tree/master/week1/day3)

* Objects: Way of remembering/storing information in JS
  * AKA: Associative array, map, dictionary, hash
  * Similar to phonebook (key: name, value: phone number)

* To access can use dot notation (ex. roofus.age will return age [key] value)
  * No need to use quotes
  * Use same notation followed by = new value to update the value (ex. roofus.age = 6 will change the value of age to 6)
  * Can add new key the same way (ex. roofus.description = "...")
  * To remove a key use delete (ex. delete roofus.description to remove that key)
    * Can also set value to null or undefined if key may be used again in future

* Access can also be done with [] (ex. roofus["age"])
  * Same as accessing arrays but we don't use indexes, we use keys
  * Must use quotes around string
  * Best method to access information dynamically or programatically
  * Can run functions or any executable JS in square brackets (ex. roofus[getKey()] will run the function)
  * Can be used to access user input (dot notation will return undefined since userInput is not a key in our object)

## Primitive Data Types

* String
* Number
* Boolean

* Variables are boxes where values are stored
  * Variables can be reassigned easily
  * Can also copy the value from one variable to another without affecting the original variable value

* Objects and arrays both stored by reference
  * Variable still stored in boxes but storing reference to the location of the information (not the information itself) in the box
  * If object or array is copied to another variable it is pointing to the SAME LOCATION as the original object (new storage but same location!)
    * This means if the data gets changed in the copy, the data is ALSO changed in the original because the data is the same for both!! Be careful!!
  * Can use slice when making a copy of an array to avoid this (making a true copy, a new array)
    * With objects this is trickier (will be practicing this with Lotide project)
  * Spread operator works on both objects and arrays
    * This only copies the top level (a shallow copy) so if you have nested arrays or objects this will still create a reference to the data, not a true deep copy

* If using dot notation to reassign value, the object is affected. If value is just reassigned with equals the original object is not affected

* Objects can include functions as a value
  * Can use dot notation without brackets to show what the function looks like, or include brackets to call the function itself 
  * Known as a method