# What are Symbols?
An object whose constructor returns the primitive `Symbol()` data type. Symbols are unique and immutable. They are used to create unique objects keys that won't collide even though they may have the same key, these keys are just strings.
```javascript
const sym1 = Symbol();
const sym2 = Symbol("foo");
const sym3 = Symbol("foo");

Symbol("foo") === Symbol("foo"); // false
```
## Shared Symbols in the global symbol registry
To create symbols aross files, each with their own global scope, using methods `Symbol.for()` and `Symbol.keyFor()`. `Symbol.for()` creates a new symbol in the global symbol registry, or returns an existing symbol if the key is already present. `Symbol.keyFor()` returns the key of a symbol from the global symbol registry.
- the registry is fictitous and is not held by any DS and cannot be accesses directly with JS code other that through `Symbol`


## Best Practices
- Use symbols as object keys when you want to create a unique key that won't collide with other keys.
	- Don't assign `new Symbol()` to a variable, it will throw a type error.
```javascript
const sym = Symbol("foo");
typeof sym; // "symbol"
const symObj = Object(sym);
typeof symObj; // "object"
```

## Examples
- Return a Symbol: `Symbol.for("key")`
- Return the key of a Symbol: `Symbol.keyFor(Symbol.for("key"))`
