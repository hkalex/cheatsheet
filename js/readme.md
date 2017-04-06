# Javascript cheatsheet


## Fastest for loop
```Javascript
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
```Javascript
// sort by string
var a = [123,678,45];
a.sort(); // a = [123,45,678]

// sort by number
var a = [123,678,45];
a.sort(function(a,b) { return a-b; }); // a = [45,123,678]

// or
a.sort((a,b)=>a-b); // a = [45,123,678]
```

## Insert an element
```Javascript
// insert 9 before the element with index 3
var a = [5,2,7,6,8];
var b = a.splice(3,0,9); // a = [5,2,7,9,6,8]; b=[]
```

## Replace an element
```Javascript
// replace 9 to the element with index 3
var a = [5,2,7,6,8];
var b = a.splice(3,1,9); // a = [5,2,7,9,8]; b [6]
```

## Delete an element
```Javascript
// delete the element with index 3
var a = [5,2,7,6,8];
var b = a.splice(3,1); // a = [5,2,7,8]; b=[6]
```

## Delete element by one while loop
```Javascript
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

## Binary search template
```Javascript
function binarySearch(ar, el, compare_fn) {
    var m = 0;
    var n = ar.length - 1;
    while (m <= n) {
        var k = (n + m) >> 1;
        var cmp = compare_fn(el, ar[k]);
        if (cmp > 0) {
            m = k + 1;
        } else if(cmp < 0) {
            n = k - 1;
        } else {
            return k;
        }
    }
    return -m - 1;
}
```


## Group-by function template
```Javascript
function group(arr, groupFun) {
  var result = [];
  var processed =[];

  for(var i=arr.length-1; i>=0; i--) {
    if (processed[i]) continue;

    var grouped = [];
    var cur = arr[i];
    processed[i] = 1;

    grouped.push(cur);

    for(var j=i-1; j>=0; j--) {
      if (processed[j]) continue;
      var cmp = arr[j];
      var groupFunResult = groupFun(cur, cmp);
      if (groupFunResult) {
        grouped.push(cmp);
        processed[j] = 1;
      }
    }
    result.push(grouped);
  }
  return result;
}
```

Here is an example
```Javascript
var a = [1,2,3,4,5];
var b = group(a, (a,b) => {
  return (a%2 === 0 && b%2 === 0) ||
        (a%2 === 1 && b%2 ===1)
});
```
The result of `b` is `[[1,3,5],[2,4]]`. They will be grouped by even and odd.
