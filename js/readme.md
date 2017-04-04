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

## Array.sort
`Array.sort` is sorting the array by **string**!!
```
// sort by string
var a = [123,678,45];
a.sort(); // a = [123,45,678]

// sort by number
var a = [123,678,45];
a.sort(function(a,b) { return a-b; }); // a = [45,123,678]
```

## Insert an element
```
// insert 9 before the element with index 3
var a = [5,2,7,6,8];
var b = a.splice(3,0,9); // a = [5,2,7,9,6,8]; b=[]
```

## Replace an element
```
// replace 9 to the element with index 3
var a = [5,2,7,6,8];
var b = a.splice(3,1,9); // a = [5,2,7,9,8]; b [6]
```

## Delete an element
```
// delete the element with index 3
var a = [5,2,7,6,8];
var b = a.splice(3,1); // a = [5,2,7,8]; b=[6]
```

## Delete element by one while loop
```
// delete all even numbers
var a = [5,2,7,6,8];
var i=a.length-1;
while (i>=0) {
  if (a[i] % 2 === 0) {
    a.splice(i,1);
  }
  i--;
}
```

