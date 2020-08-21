# Objects - Iteration

* Objects not iterable like arrays, need to use for...in statement

Ex: 
```javascript
var planetMoons = {
  mercury: 0,
  venus: 0,
  earth: 1,
  mars: 2,
  jupiter: 67,
  saturn: 62,
  uranus: 27,
  neptune: 14
};

for (var planet in planetMoons) {
  var numberOfMoons = planetMoons[planet];
  console.log("Planet: " + planet + ", # of Moons: "+ numberOfMoons);
}
```
* Key is available in the loop (planet variable), loops over each key using for loop

* For in can have interesting results, be careful!
  * Objects can have inherited properties from prototype chain and method names
  * Additional filtering with hasOwnProperty:

```javascript
for (var planet in planetMoons) {
  // additional filter for object properties:
  if (planetMoons.hasOwnProperty(planet)) {
    //  ...
  }
}
```
