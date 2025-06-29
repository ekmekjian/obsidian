## Arrow Functions
Arrow functions are a shorter way to write a function. They are also known as fat arrow functions. They are always anonymous and can be used as a function expression or a function statement. They are best used for non-method functions and cannot be used as constructors. Its syntax is `() => {// expression here}`
There are many ways to write an arrow function. Here are some examples:
1. `() => expression`
2. `param => expression`
3. `(param) => expression`

4. `(param1, paramN) => expression`
5. 
`() => {
  statements
}`
6. 
`param => {
  statements
}`

7. `(param1, paramN) => {
  statements
}`

## Closure
Offers the ability to trate functions as values.
```js
function wrapValue(n){
  let local = n;
  return () => local;
}
let wrap1 = wrapValue(1);
console.log(wrap1());
// => 1
```
What this does is creates a function that creates a local binding, that only exists as long as the function exists, and returns a functions that returns the local binding. When it's store in `wrap1` it stores the function that returns the local binding. When `wrap1` is called it returns the local binding.

## Recursion
A function that calls itself is called Recursion.
```js
function power(base, exponent){
  if (exponent == 0){
	return 1;
  } else {
	return base * power(base, exponent - 1);
  }
}
console.log(power(2,3));
```
This function checks the exponent to see its at 0 for it's escape condition. If not then it will return the base times the power function with the base and exponent - 1. This will continue until the exponent is 0 and then it will return 1. This will then return the base times 1 and then the base times 2 and then the base times 3. This will return 8.
- Despite the simplicity of the solution it is actually slower thant doing this with a loop.

```js
function findSolution(target) {
	function find(current, history) {
		if (current === target) {
			return history;
		} else if (current > target) {
			return null;
		} else {
			return find(current + 5, `(${history} + 5)`) ||
				find(current * 3, `(${history} * 3)`);
		}
	}
	return find(1, "1");
}
console.log(findSolution(24));
```
This creates two branches of recuresion. The goes as follows if the first is true return otherwise reuturn the second. And what you see is the branch try different routes to find the target number. This will return `(((1 * 3) + 5) * 3)`.
The first branch tries to add 5 till it goes beyond that takes a step back then tries to multiply. If after trying that branch keeps exceeding the target the function will just return null and the other branch will continue. If the other branch finds the target it will return the history and the function will end.



## Optional Arguments
This code runs with no issues:
```javascript
function square(x){return x *x;}
console.log(square(4,true,"hedgehog"));
```
This will return 16 because the extra arguments are ignored.
Javascript will allow fewer arugments and will just auto fill the rest with undefined.
### Examples
```Javascript
function multi (a,b,c){
console.log(a);
console.log(b);
console.log(c);
}
multi('Hello World');
```
This will return `a` as `Hello World` and `b` and `c` as `undefined`.
