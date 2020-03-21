#  Regular Expressions Revisited

## Creation

``` 
const regex = new Regex('pattern', 'flags');
const regex = regexp = /pattern/flags
```

## Flags
*g* - Add this pattern and all matches are returned, not just the first occurence

*i* - Case insentivite flag

*m* - Multiline match

*y* - Sticky mode - searching text in exact position

## Searching
```
let str = "We will, we will rock you";
const matches =  str.match(/we/gi);
```

## Replacing

```
let str = 'We will, we will';
str = str.replace(/we will/, 'rock you');
```

```
$&  // inserts the whole match
$` // inserts a part of the string before the match
$' // inserts a part of the string after the match
$n // if n is a 1-2 digit number, then it inserts the content of the n-parenthesis
$<name> // inserts the content of the parentheses with the given name
$$ // inserts character $
```