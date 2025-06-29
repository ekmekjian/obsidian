# Text Search with Regular Expressions
#programming/notes/javascript
*Source URL: [](https://www.freecodecamp.com/challenges/sift-through-text-with-regular-expressions).*
- - - -

`Regular expressions` are used to find certain words or patterns inside of `strings`.

For example, if we wanted to find the word `the` in the string `The dog chased the cat`, we could use the following `regular expression`: `/the/gi`

Let's break this down a bit:

`/` is the start of the regular expression.

`the` is the pattern we want to match.

`/` is the end of the regular expression.

`g` means `global`, which causes the pattern to return all matches in the string, not just the first one.

`i` means that we want to ignore the case (uppercase or lowercase) when searching for the pattern.

// Setup

var testString = "Ada Lovelace and Charles Babbage designed the first computer and the software that would have run on it.";

// Example

// search all repeat for the word software while ignoring uppercase and lowercase
var expressionToGetSoftware = /software/gi;
var softwareCount = testString.match(expressionToGetSoftware).length;

One selector is the digit selector `\d` which is used to retrieve one digit (e.g. numbers 0 to 9) in a string.

Appending a plus sign (`+`) after the selector, e.g. `/\d+/g`, allows this regular expression to match one or more digits.
Allows the search for numbers like 35 and see it as one rather 3 and 5 resulting in a return of two

var testString = "There are 3 cats but 4 dogs.";

var expression = /\d+/g;  // Change this line

We can also use regular expression selectors like `\s` to find whitespace in a string.

The whitespace characters are `" "` (space), `\r` (the carriage return), `\n` (newline), `\t` (tab), and `\f` (the form feed).

The whitespace regular expression looks like this:

`/\s+/g`

//This is the test string
var testString = "How many spaces are there in this sentence?";
//count all occurrences of a space in the string

var expression = /\s+/g;  // Change this line

//counter for all spaces in string

var spaceCount = testString.match(expression).length;
