# Tutorial: Email Regular Expression

The purpose or this tutorial is to explain how to use a regular expression -- but what are regular expressions? Regular expressions, also known as “Regex”, are a tool for searching and matching parts of a text by describing the patterns that should be used to identify those parts. This is accomplished by creating a set of symbols that describes the pattern of the text you are interested in. 

One reason for using regex is format validation for user input such as ensuring a credit card number has the correct number of digits or to test if an email address is in a valid format. In this tutorial, we will be learning about the latter.

## Summary

This tutorial is to explain how to use the regular expression ```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/``` to match emails. This is useful for validating the format of an email address submitted by a user.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
Anchors are used to specify a starting point and/or ending point of a pattern. For this tutorial, we will consider two types of anchor; the caret ```^``` and the dollar sign ```$```. The caret indicates the start of a string or line. The dollar sign indicates the end of a string or line.

### Quantifiers

### Character Classes

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

## Author

Joseph Veyhl [Github](https://github.com/jveyhl/jve_regex_tutorial)
