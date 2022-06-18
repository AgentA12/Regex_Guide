# A simple guide to Regular Expressions

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

## Summary

Above is a Regular Expression or Regex for short. This particular Regex finds or "validates" a email. Regex's are very useful in validating strings of text. In this guide I will explain how they work and what regular expressions are all about.

To start, regular Expressions use what are called tokens to denote meaning and each token has a perticular use. Every Regex starts and ends with a forward slash /. Lets look at an example,

This is a Regex.

`/foo/`

It searchs for the collection of characters "foo"

It will match any instances of "foo"

<code><mark>foo</mark>bar</code>

<code>bar<mark>foo</mark>bar</code>

This is the most basic regex you can make. I will go over some useful regex tokens in this guide.

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

## Regex Components

### Anchors

The first set of tokens we will review are called Anchors. Anchors are use to denote the start and end or a word boundary of a Regex.

The tokens for anchors are ^ $

^ (carot) denotes the start of a string while $ denotes the end of a string.

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

Next up are Quantifiers. This tokens specify how many instances of a certain character the regex will match.

The first anchor is \*. This will match zero or more of the preceding character.

The regex `/foo*/` will match

<code><mark>fo</mark></code>

and

<code><mark>foooooooooooooooo</mark></code>

The + anchor will match one or more characters preceding it.

`/foo+/`

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

Using a comma , we will match the specified number or more

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

Some more classes include the . and  - will match any characters and \D will match ONE non-digit character.

### Flags

Flags change how a regex will search a particular string. They are placed at the end of a regex,

right after the last foward slash / char. TH=here are tons of flags but the most common ones are

the global `/g`, multi line `/m` and the case insensitive `/i`.

If you add a global to the end of a regex, the regex won't return after the first match.

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

When a regex "captures" an expression it will place it in a group. So if we had a regex like so

`/foobar@gmail.com/`

And captured the string

<code><mark>foobar@gmail.com</mark></code>

This would be group 0 or one group.

If we were to put a grouping parentheses around '(gmail)' it would be stored as different group.

We can refer to these groups and preform operations on these groups.

We can for example, replace certain captured groups using the $. If we were to type $1 in this case, we would get 'gmail' returned.

Lets look at an example

`/foobar@(gmail).(com)/`

Now our character string we are matching

<code><mark>foobar@gmail.com</mark></code>

When we use $1, the regex will return gmail. For $2 it will return com.

We could now replace and check certain groups. For example we could replace a credit card number will XXX-XXX etc...

### Bracket Expressions

Bracket expressions are used to match a single character inside the brackets or a collection of characters.

`/[foobar]/` will match <code><mark>foobar</mark></code> 

or if the global flag is used will match all characters inside the brackets 

`/[foobar]/g`

<code><mark>foobar</mark> <mark>raboof</mark> <mark>ofbra</mark></code>

brackets can also have ranges.

`/[a-z]/` will match any lowercase char from a-z. This can be done with digits also.

`/[^a-e]/` will match any chars that are not in the range of a-e.

We can also use .  and == in bracket notation.

### Greedy and Lazy Match

Greedy and lazy matching refer to how a regex will search. Greedy regex's will consume as many instances as possible while lazy match's consume as few instances as possible.

For example the + would be considered greedy where a ? would be lazy.

### Boundaries

Boundaries are like anchors but they only match a word boundary. 

For example

`/\bfoobar\b/`

will match 

<code><mark>foobar</mark> foo bar bar foo barfoo </code>

### Back-references

Back references refer to groups. They use \1,\2 and so on. 

\1 will match any characters that appear twice one after the other

`/([foobar])\1/`

<code>f<mark>oo</mark>bar barfoo foo ba<mark>rr</mark></code>

### The email validator

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

So now lets try and understand what is going on here

To start off we have our anchor specifying were to start and end the search ^ and $. Pretty straight foward.

Then we have our first group. Group One

`([a-z0-9_\.-]+)`

In this group we are looking for any character from a-z and digits 0-9. Also we have to use the case insensitive flag to match capital letters.

We are also allowing any _. or dashes. Note we have a backslash before the ., recall the . has a special meaning so we need to escape it with \\.

We then end with a + (greedy). This makes our first group. "John_doe" will be valid.

Second Group.

`@([\da-z\.-]+)`

Notice the @ before the group. This must be inbetween the first and second group to form a valid email.

After the @ we have our second group with a bracket.

In this bracket we allow digits \d and chars from a-z, and a period (escaped) also a -. Ended with a +.

Any other special characters are not allowed.

Third Group

`\.([a-z\.]{2,6})$`

Again notice the \\. before the group. A period is required inbetween the first and second group.

Then inside our group we have a bracket allowing a-z and . characters, also only allowing a range of 2 to 6 {2, 6}. (so .ca or .com) Then our end anchor $.

Thats it! I hope you learned something new. Now you can put regexs to practice for powerful validation.

## Author

Hi, my name is Andrew and I'm a web developer that loves learning and solving problems. You can see my github here:

[https://github.com/AgentA12?tab=repositories](https://github.com/AgentA12?tab=repositories)

