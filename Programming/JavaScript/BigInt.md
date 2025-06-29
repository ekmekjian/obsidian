# BigInt
A numeric data type. It can be used for arbitrarily large integers. `BigInt` allows you to safely store and operate on large integers that are even beyond the safe integer limit.
- JS has a method under the `Number` object called `MAX_SAFE_INTEGER` which is equal to `9007199254740991`. This is the largest integer that can be safely represented and manipulated in JS. Any integer larger than this will be rounded to the nearest safe integer. This is where `BigInt` comes in. It allows you to safely store and operate on large integers that are even beyond the safe integer limit.
concating `n` to a number will convert it to a `BigInt`.
- Most operators work on `BigInt` the only one that doesn't is `>>>` (Unsigned right shift operator). A `BigInt` isn't technically a number with the same mathmatical value but it's considered one loosely.
- Will throw `TypeError` if you try to mix with regular numbers in arithmetic expressions, or they are implicitly converted.
