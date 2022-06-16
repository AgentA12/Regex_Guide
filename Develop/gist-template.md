# A simple guide to Regular Expressions

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Summary

Above is a Regular Expression or Regex for short. This perticular Regex finds or "validates" a email. Regex's are very useful in validating and extracting strings of text. In this guide I will explain how they work and what regular expressions are all about.

Regular Expressions use what are called tokens to denote meaning and each token has a perticular use. Every Regex starts and ends with a forward slash. Lets look at an example,

This is a Regex.

`/foo/`

It searchs for the collection of characters <code><mark>foo</mark></code>

It will match any instances of "foo"

<code><mark>foo</mark>bar</code>

<code>bar<mark>foo</mark>bar</code>

I will go over some common token types in this guide.

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

The first set of tokens we will review are called Anchors. Archors are use to denote the start, end or a word boundary of a Regex.

The tokens for anchors are ^ $

^ denotes the start of a string while $ denotes the end of a string.

Lets look at an example

The Regex `/^foo/` will only match the start of a string with "foo"

<code><mark>foo</mark>bar and foobar</code>

So `/foo$/` will match the end of a string containing "foo"

<code>foobar and bar<mark>foo</mark></code>

If you put the two together `/^foo$/` , the Regex would search for an exact string match. Beginning and ending with "foo".

<code>foobar and foobar</code>

<code>foobar and barfoo</code>

<code><mark>foo</mark></code>

There is also /b and /B which match a character beginning or ending with a \w (white space character).

### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
