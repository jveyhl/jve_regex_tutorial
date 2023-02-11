# Tutorial: Email Regular Expression

The purpose or this tutorial is to explain how the components of a regular expression work -- but what are regular expressions? Regular expressions, also known as “Regex”, are a tool for searching and matching parts of a text by describing the patterns that should be used to identify those parts. This is accomplished by creating a set of symbols that describes the pattern of the text we are interested in.

One reason for using regex is to validate user input such as ensuring a credit card number has the correct number of digits or that an email address is in a valid format. In this tutorial, we will be learning about the latter.

## Summary

This tutorial describe and provide examples of the components in the regular expression `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/` that is used to match emails. This is regex is useful for validating the format of an email address submitted by a user.

Note that the forward slashes `/` only indicate the start and end of the regex and are not part of the pattern-matching process.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Conclusion: Bringing it all together](#conclusion-bringing-it-all-together)

## Regex Components

### Anchors

Anchors are used to specify a starting point and/or ending point of a pattern. For this tutorial, we will consider two types of anchor; the caret `^` and the dollar sign `$`. The caret indicates the start of a string or line. The dollar sign indicates the end of a string or line.

If we wanted to search a string that contains "apple" as its first word, we could use the following regex: `/^apple/`.

If we wanted to search a string that contains "apple" as its last word, we could use the following regex: `/apple$/`.

### Quantifiers

Quantifiers allow us to specify the number of times something is repeated. An open curly brace `{` signifies the start quantified repetition of a preceding item and a closing curly brace `}` signifies the end quantified repetition of a preceding item. Any values placed inside the curly braces represent the minimum and maximum number of times a preceding item can be repeated using the format `preceding_item{min,max}`.

If we wanted to match numbers with four to eight digits, we could use the following regex: `\d{4,8}`

Note that in the above example, `\d` matches any single digit (i.e. 0-9).

The plus `+` repetition operator specifies that a preceding item can be repeated a minimum of one time and any number above one.

If we wanted to match numbers with one to infinity digits, we could use the following regex: `\d+`

Note that the regex in the above example is equivalent to `\d{1,}` where no value after the comma represents a maximum value equal to infinity.

### Character Classes

A character class is a notation that matches any symbol from a certain set. The `\d` mentioned in the Quantifiers section of this tutorial is an example of a character class, specifically the “digit” class, and corresponds to any single digit from 0 to 9.

There are other character classes such as `\w`, which matches any alphanumeric character from the basic Latin alphabet, including the underscore (i.e. A-Z, a-z, 0-9 and \_).

If we wanted to match words or numbers that are four to eight characters in length, we could use the following regex: `\w{4,8}`

### Grouping and Capturing

Grouping is accomplished by using the open parenthesis `(` to denote the start of a grouped expression and the closing parenthesis `)` to denote the end of a grouped expression. One of the benefits of creating a grouped expression is that we can apply operators to the entire group.

If we wanted to search for a series of repeating characters like “abc” we could use the following regex: `/(abc)+/`

Note that in the above example, we are using the plus `+` quantifier, which allows the group of characters to match anywhere from one to infinity number of times. Therefore, the regex in our example would match on the string “abc” and the string “abcabcabc”.

Whenever you group an expression, the regex engine also captures it by default; it stores whatever text matches the grouped expression in memory for later use.

### Bracket Expressions

Bracket expressions are used to create character sets, and use an open square bracket `[` to denote the beginning of a character set, and a closing square bracket `]` to denote the ending of a character set. Character sets are used to define a customized list of characters that we want to match on.

If we wanted to search a text and find the word “grey” and its alternate spelling “gray” we could use the following regex: `/gr[ea]y/`

Note that the set will only match on ONE of the characters in the set. We would need to use a quantifier to match on more than one character in the set.

### Greedy and Lazy Match

The principle of greedy expressions describes how a regex engine makes choices about what it returns as a match. This becomes especially important when repetition expressions are used because these will make our strings an indeterminate length and may match several different things.

Standard repetition quantifiers are greedy by default, which means that the regex tries to match the longest possible string. The `+` is greedy; it only “gives back” as little as possible to make the match. It tries to match as much as possible before giving control to the next portion of the regex.

If we wanted to search a text for “Interstella 5555”, we could use the following regex: `/.+[0-9]+/`

The `.+` portion matches “Interstella 555” and the `[0-9]` portion will only match the last “5” in the string. This is because the `.+` is greedy and tries to match as much as possible before giving control to the `[0-9]+` portion of the regex.

Lazy expressions, as you might expect, are the opposite of greedy expressions. To change the default behaviour from greedy to lazy, we need to use a question mark `?` to make the preceding quantifier lazy. In this case “lazy” means that the affected portion of the regex will match as little as possible before giving control to the next portion of the regex.

To make the example above lazy, we could use the following regex: `/.+?[0-9]+/`

The `.+?` portion matches “Interstella ” (including the space between the “a” and the first “5”) and the `[0-9]` portion will match the “5555” in the string. This is because the `.+?` is lazy and tries to match as little as possible before giving control to the `[0-9]+` portion of the regex.

Note that the period `.` is a wildcard that will match any character except newline.

### Conclusion: Bringing it all together

Now that we know the purpose of each component that makes up the regex `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, we are able to explain how this expression can verify the format of an email address submitted by a user:

We can use the following email address as an example to explain how the regex will make its matches: <span style="color: magenta;">"test<area>@gmail.com"</span>.

The `^([a-z0-9_\.-]+)` part will match <span style="color: magenta;">"test"</span>. The regex is using a caret `^` to indicate the start of the string and is using opening and closing parentheses `(` and `)` to define a group that contains a character set. This character set is defined using opening and closing square brackets `[` and `]` and consist of all lowercase letters `a-z`, all integers `0-9`, the underscore `_`, the period `\.` (escaped using a backslash) and the dash `-`. Finally a `+` quantifier is applied to the character set so that it matches at least once.

The `@` part will match <span style="color: magenta;">"@"</span>.

The `([\da-z\.-]+)` part will match <span style="color: magenta;">"gmail"</span>. The regex is using opening and closing parentheses `(` and `)` to define a group that contains a character set. This character set is defined using opening and closing square brackets `[` and `]` and consist of the character class `\d` (matches any digit 0-9), all lowercase letters `a-z`, the period `\.` (escaped using a backslash) and the dash `-`. Finally a `+` quantifier is applied to the character set so that it matches at least once.

The `\.` part will match <span style="color: magenta;">"."</span>.

The `([a-z\.]{2,6})$` part will match <span style="color: magenta;">"com"</span>. The regex is using a dollar sign `$` to indicate the end of the string and is using opening and closing parentheses `(` and `)` to define a group that contains a character set. This character set is defined using opening and closing square brackets `[` and `]` and consist of all lowercase letters `a-z` and the period `\.` (escaped using a backslash). Finally a quantifier is applied to the character set by using opening and closing curly braces `{` and `}` so that it matches a minimum of two times and a maximum of 6 times.

## Author

Joseph Veyhl [Github](https://github.com/jveyhl/jve_regex_tutorial)
