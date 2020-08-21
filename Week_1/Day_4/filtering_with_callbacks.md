```javascript
const numbers = [1, 2, 3, 4, 5, 7, 10, 14, 17, 18];
const evens = numbers.filter(function(num) {
  return (num % 2 == 0);
});
console.log("Subset of even numbers:", evens);
```
Returns: Subset of even numbers: [ 2, 4, 10, 14, 18 ]

* Array offers filter mthod to iterate through elements and return true or false (whether element should be included in results or not)
  * Used to filter values into smaller list

```javascript
function(num) {
  return (num % 2 == 0);
}
```
* This is an anonymous callback function