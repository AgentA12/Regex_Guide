# A simple guide to Regular Expressions

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Summary

Above is a Regular Expression or Regex for short. This perticular Regex finds or "validates" a email. Regex's are very useful in validating and extracting strings of text. In this guide I will explain how they work and what regular expressions are all about.

To start, regular Expressions use what are called tokens to denote meaning and each token has a perticular use. Every Regex starts and ends with a forward slash /. Lets look at an example,

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

In the email regex we can see it takes advantage of anchors.

### Quantifiers

Next up are Quantifiers. This tokens specify how many instances of a certain character to match.

The first anchor is \*. This will match zero or more of the preceding character.

The regex `/foo*/` will match

<code><mark>fo</mark></code>

and

<code><mark>foooooooooooooooo</mark></code>

The + anchor will match one or more character preceding it.

Does not match

<code>fo</code>

Match's

<code><mark>foo</mark></code>

<code><mark>foooooooooo</mark></code>

There is also the question mark ? which will match a character string or a character string followed by its last char.

`/foo?/`

<code><mark>foo</mark> <mark>fo</mark> o<mark>fo</mark></code>

The most common quantifier token is the square brackets {}. They are used to match ranges.

For example

`/foo{5}/` Will match exactly 5 o's

<code><mark>fooooo</mark>ooooo</code>

<code>foooo</code>

Using a comma , we will match the specify number or more

`/foo{3,}/`

Note that three o's will not match in these case because we have two o's in "foo".

<code>fooo</code>

<code><mark>foooo</mark></code>

<code><mark>fooooooooooooo</mark></code>

We can combine these too matching a range between the numbers.

`/foo{3,6}/`

<code>fooo</code>

<code><mark>foooo</mark></code>

<code><mark>fooooooo</mark></code>

<code><mark>fooooooo</mark>ooooo</code>

There are also greedy, lazy and possessive quantifiers.

### OR Operator

OR uses the (|) and []. It will match the character on the left side OR the character on the right.

`/foo(a|b)/`

<code><mark>fooa</mark></code>

<code><mark>fooob</mark></code>

The square bracket will match only one or the other.

`/foo[ab]/`

<code><mark>fooa</mark>b</code>

<code><mark>foob</mark>a</code>

### Character Classes

Character classes match a class of characters.

`\d` will match a single character that is a digit.

`\w` will match a word character.

`\s` will match a white space character.

Some examples.

`/\d/`

<code> <mark>123</mark> Hello world! I am <mark>0</mark>b<mark>110100</mark> years old.</code>

`/\w/`

<code><mark>hello</mark> <mark>world</mark>!</code>

`/\s/`

<code>hello<mark> </mark>world!</code>

You can also match carriage returns `\r` and tabs `\t`.

Some more classes include . - will match any characters and \D will match ONE non-digit character.

### Flags

Flags change how a regex will search a perticular string. They are placed at the end of a regex,

right after the last foward slash / char. THere are tons of flags but the most common ones are

the global `/g`, multi line `/m` and the case sensitive `/i`.

If you add a global to the end of a regex, the regex wont return after the first match.

`/foo/` No global

<code><mark>foo</mark> foo</code>

`/foo/g` Global

<code><mark>foo</mark> <mark>foo</mark></code>

If you add a multi line `/m` the ^ and $ will match the start/end of a line.

`/^foo$/`

```
foo
foo
```

`/^foo$/m`

<code><mark>foo</mark></code>

<code>foo</code>

The `/i` flag when used will match a specified word regardless of casing.

`/foo/`

<code>FOO</code>

`/foo/i`

<code><mark>FOO</mark></code>

### Grouping and Capturing

When a regex "captures" a expression it will place it in groups. So if we had a regex like so

`/foobar@gmail.com/`

And captured the string

<code><mark>foobar@gmail.com</mark></code>

This would be group 0 or one group.

If we were to put a grouping parentheses around '(gmail)' it would be stored as different group.

We can refer to these groups and preform operations on just these groups.

We can for example replace certain captured groups using the $. If we were to type $1 in these case, we would get 'gmail' returned.

Lets look at an example

`/foobar@(gmail).(com)/`

Now our character string we are matching

<code><mark>foobar@gmail.com</mark></code>

When we use $1, the regex will return gmail. For $2 it will return com.

We could now replace and check certain groups. For example we could replace a credit card number will XXX-XXX etc...

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author
