# Objects - Basic Concepts

## Objects at a Glance
* Key-value pairs, each key maps to a value
* Keys are always strings (or symbols, less common and not important)
* Unique keys, cannot be duplicated in the same object
* Keys point to values (any type [number, string, boolean, null])
  * Can use undefined but not typical because undefined gets returned if a key is not defined in the object (can get confusing if a value is also undefined)

## Object Literals
* Some values can be represented by literals (string literals, number literals, arrays have literal syntax using square brackets)
  * Objects also have literal syntax using braces {}
  * Ex: const emptyObject = {} is an empty object literal assigned to a variable
  * Ex. const tinyObject = { "size": "Tiny} is an object literal with single key ("size") value ("Tiny") pair
    * Key doesn't always need quotes, easier to read without, does need quotes if key has spaces

* Objects can be pictured as 2-column tables (Key in column one, Value in column two)
  * Values can be accessed by referencing keys

* When using square brackets to access a key, be sure to use quotes to identify the key as a string. Otherwise the key will be read as a variable and won't be accessed properly

* Square bracket notation can also be used to assign new values to new or existing keys

* Can nest objects within objects (value that is another object)
  * Access using square bracket notation like: person["address"]["city"]

* Arrays within objects are objects and arrays (typeof array = object, instance of array is both object and array)

* Method: Object.keys(...) returns an array of objects (keys)
