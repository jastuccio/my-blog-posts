# Get the Middle Character

Return the middle character of a string. Return the middle 2 characters if the string is even length.

### Tests

```
getMiddle("test");     // should return "es"
getMiddle("testing");  // should return "t"
getMiddle("middle");   // should return "dd"
getMiddle("A");        // should return "A"
```

### My Solution
```
const getMiddle = (s) => {
  const middle = s.length / 2;
  
   return (s.length % 2) 
    ? s.charAt(middle)
    : s.slice(middle - 1, middle + 1);
}
```

### Notes

`return (s.length % 2)` uses the modulo operator to determine if `s` has an odd or even number of characters.  `s.length % 2` returns either 0 (false) or 1 (true)

When the string length is an odd number of characters `s.length % 2` = 1 (a truthy value). The code after the ternary operator "`:`" is executed `s.slice()` Even length strings execute the code after the "`?`"

It might help to think of the ternary statement as a shortened `if/else` statement.


`
if (s.length % 2 === 1) {
  return s.charAt(middle);
} else {
  return s.slice(middle - 1, middle + 1);
}
'

`string.slice` is used for odd length strings. `middle` = 2.5 in a 5 character string. `slice()` rounds 2.5 up to 3 so `slice(middle - 1, middle + 1);

### tags
 * string.length
 * string.charAt
 * string.slice
 * ternary operator
 * modulo


[codewars](http://www.codewars.com/kata/get-the-middle-character/train/javascript)