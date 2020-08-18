## Using Process.argv

Global object, no additional libraries need to be imported. Just pass arguments to Node.js:
1. file system path point to node executable
2. name of JS file being executed
3. first argument passed by user

```javascript
'use strict';

for (let j = 0; j < process.argv.length; j++) {
  console.log(j + ' -> ' + (process.argv[j]));
}
```
output: 

$ node processargv.js tom jack 43
0 -> /Users/scott/.nvm/versions/node/v4.8.0/bin/node
1 -> /Users/scott/javascript/processargv.js
2 -> tom
3 -> jack
4 -> 43

1) path to node executable
2) path to script file
3) arguments passed in sequence