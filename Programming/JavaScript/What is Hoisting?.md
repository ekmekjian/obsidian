# What is Hoisting?
A process where the interpertor movies all the function declarations to the top of the file.
Behaviors of hoisting:
- using variables values before declartion ("Value hoisting")
- referencing a varible in a scope before the line declaration ("Declaration hoisting"):
	- Without throwing `ReferenceError` exception but hte value is always `undefined`
- The declaration of the variable causes behavior change in a scope before the declaration line

## Examples
```javascript
const x = 10;
{
	console.log(x); // undefined
	const x = 20;
}
```
The interpreter sees the `const x` in the block and it taints the scope causing the `console.log` to throw `ReferenceError` exception.
## Value hoisting
```javascript
a = 5;
console.log(a); // 5
var a;
```
This is hoisiting because we can the read the value of a before the declaration line.If this were to be attempted with `let` or `const` it would throw `ReferenceError` exception
