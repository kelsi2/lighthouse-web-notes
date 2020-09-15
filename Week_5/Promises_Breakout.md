# Promises

* Promises (all async) will not run until all code has finished running
* Basic pattern: make promise => give it a callback
  * use .then for callback, .catch to handle rejections (when promises cannot be fulfilled)
* A then() or catch() returns a promise
* Final piece of the chain is .finally()
  * Full chain: promise.then().catch().finally()
  * Finally always happens regardless of what else fires in the chain
  * Can be used for database cleanup because we know it will always occur
* axios: makes HTTP calls (GET, POST, etc.) => will be used in React
* Promise.all() => uses the class Promise and takes in multiple promises (an array of promises)
  * Calls all of them and waits for them to resolve or catch before firing
* Can use ternery operator to ensure promise keeps running despite an error in previous lines
* Can also precatch errors when creating a promise variable
* Promise.allSettled will return array of objects with status (fulfilled or rejected) and value
* If we call the same promise twice we will get the same result twice!