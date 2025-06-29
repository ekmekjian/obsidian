
# Big O Notation

```typescript
function sun_char_codes(n: string): number{
	let sum = 0;
	// for loop run for the length of the string
	for (let i = 0; i < n.length; ++i){
		sum += n.charCodeAt(i);
	}
	return sum
}
```
- constants are important in theory because it will be typically faster than n^2
- N = 1000, O(10N) = 10000, O(N^2) = 100,000,000 N^2 being 1000x bigger
- Just because N is faster than N^2, doesn't mean practically it's always faster for smaller input
- insertion sort = n^2 quick sort = n 
- with smaller data sets O(N^2) can sometimes be better 
- Insertion works best with those smaller sets
####  Important concepts:
	   1. growth is with respect to the input
	   2. Constants are dropped
	   3. Worst case is usually the way we measure,
