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