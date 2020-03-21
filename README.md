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

**Full Match**

Both anchors together `^...$` are often used to test for a full match

```
const str = 'test'
const regex = /^test$/

const test = regex.test(str) // only case where this will ever be true

```

## Multiline mode ##

Multiline mode is enabled by the `m` flag.

This only affect the behavior of `^` and `$`

In multiline mode they match not only at the beginning and end of the sting, but the start / end of a line.

```
let str = '1st place: Winnie
2nd place: Homer
3rd palce: Peter';

const matches = str.match(/^\d/gm); // 1 , 2 , 3

```
Without the `m` flag only the first digit is matched

```
let str = `1st place: Winnie
2nd place: Homer
3rd palce: Peter`;

const matches = str.match(/^\d/g); // 1
```

Similarily for the end of a string, the `$` sign behaves similarily
The regex `\d$` finds the last digit in every line
```
let str = let str = 'Winnie: 1
Piglet: 2
Eeyore: 3';

const matches = str.match(/\d$/gm); // 1,2,3
```

Without the flag `m` the dollar `$` would only match the last digit in the whole text which is 3

**Searching for \n instead of ^$**
```
let str = 'Winnie: 1 
Piglet 2
Eeyore 3'

const matches = str.match(/\d/n/gm); // 1\n 2\n
```
As we can see, there are 2 matches instead of 3 and the result contains the newline character

## Word Boundaries ##

A word boundary is a test, similar to `^` & `$`

There are three different positions that qualify as words boundaries:
- At the start of the string, if the first string character is a word character `\w`
- Between two characters in the string, where one is a word character `\w` and the other is not
- At the end of the string, if the last string character is a word `/w`

```
let str = 'Hello Java!";
const regex = /\bJava\b/;
let matches = str.match(regex) // Java

str = 'Hello JavaScript!';
matches = str.match(regex); // null;
```

```
let result = "Hello, Java!".match(/\bHello\b/); // Hello
result = "Hello, Java!".match(/\bJava\b/); // Java
result = "Hello, Java!".match(/\Hell\b/); // Null - No Match 
result = "Hello, Java!".match(/\Java!\b/); // Null - No Match 
```

Digits can also be used in boundaries: 
```
let result = "1 23 456 78".match(/\b\d\d\b/g);  // 23,78
result = "12,34,56".match(/b\d\d\b/g); // 12,34,56
```

```
const str = 'Breakfeast at 09:00 in the room 123:456';
const regex = '/\b\d\d\:\d\d\b/';
const result = str.match(regex); // 09:00
```



