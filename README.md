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

## Testing

```
let str = 'I love javascript'
let regex = /LOVE/i

const result = regexp.test(str) // true
```

## Unicode Properties

The u flag enables support of Unicode in regular expressions

```
let regex = /\p{Sc}\d/gu; // identifier for a currency in junction with u flag
let str = `Prices: $2, €1, ¥9`;

const matches = str.match(regex) // $2,€1,¥9
```

## Anchors

The caret `^` & dollar `$` have special meaning in regex. They are called anchors.

The `^` matches at the beginning of text and the `$` matches at the end.

The pattern `^Mary` means "Start the word with Mary"

```
let str1 = "Mary had a little lamb"
const result = /^Mary/.test(str1) // true

str1 = 'It's fleece was white as snow";
result = /snow$/.test(str1) // true
```


