# Javascript cheatsheet


## Fastest for loop
```
/**
 * Don't use "let i=0". It has scope check so slower.
 * Don't use forEach function. Function call is much much slower.
 * 
 * This is faster than the tranditional for-loop as
 * the length is cached.
 */
var arr = [];
for (var i=0, l=arr.length; i<l; i++) {
  // do something
}
```
