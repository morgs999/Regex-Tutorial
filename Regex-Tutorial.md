# Regular Expression for Matching a URL

As an exercise for a Coding Boot Camp, I will define and explain individual elements from a regular expression  that is designed to match within text for URLs.

## Summary

The following regex:
```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```
is designed to match for URLs by looking for elements such as 'https://', a body of characters followed by a '.', and a suffix that is a certain number of characters.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Character Escapes](#character-escapes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)


## Regex Components

### Anchors
We have two simple anchors within our regex:  `^` at the beginning and `$` at the end.<br>
These set the beginning and end of the string to match.
<br><br>

### Quantifiers
We have 4 different kinds of quantifiers throughout the regex, the `*`, `+`, `?`, and `{}` symbols, each signifying different criteria for matching.

 - `https?` - designates 0 or 1 's' required
 - `(https?:\/\/)?` - designates 0 or 1 protocols (https://) required
 - `[\da-z\.-]+` - designates 1 or more domain addres required
 - `[\/\w \.-]*` - designates 0 or more of this bracket expression required
 - `([\/\w \.-]*)*` - designates 0 or more of this group required
 - `{2,6}` - designates between 2 and 6 characters is required

For quantifiers, 0 or 1 (?) means that the individual criteria is either present or not, our example being the 's' in http or https.  0 or more means that any number of the criteria are either present or not, our example being the additional pathways, the URL can either have no pathways, one additional pathway, or any number of additional pathways, such as "www.mysite.com/paintings/january/3rd".  1 or more means the criteria must be present, but there can be any number of them, our example being the domain address.  Finally, numbers contained within a set of curly brackets means there must be a number of characters matching the range within the brackets, for example between 2 and 6 characters must be present in ours (which happens to be the '.com' area).
<br><br>

### Character Classes
We have 2 character classes within the regex as follows:
 - `\d` - designates that a digit is acceptable (0-9)
 - `\w` - designates that a word class character is acceptable (A-Z, a-z, 0-9, _)

These are used as shorthand to include large classes of characters.  The `\d` is used in the domain address to designate any digit is acceptable; however `\w` is not used as we only want to match for lowercase letters, not uppercase.  But the `\w` is used in the pathways area as any number, uppercase or lowercase letter, or underscore is acceptable.
<br><br>

### Character Escapes
There are 2 character escapes within the regex, but they are both used multiple times:
 - `\/` - designates that a backslash (/) is required
 - `\.` - designates that a dot or period (.) is required.

The character escapes allow us to include these two characters as requirements in the match, as a backslash would usually signal the beginning or end of the regex expression, and a dot usually indicates a universal character criteria.  However, in a URL backslashes and dots are part of the skeleton, allowing us to separate sections such as the protocol and domain.  Therefore, we use 2 character escapes after "http:" or "https:" to match a url that reads "http://" or "https://"; as well as matching the dot (.) between the domain address and top level domain sections.
<br><br>

### Grouping and Capturing
We have 4 groups within the regex as follows:
```
(https?:\/\/)
```
```
([\da-z\.-]+)
```
```
([a-z\.]{2,6})
```
```
([\/\w \.-]*)
```
<br>This allows us to divide the URL into 4 parts, the protocol, the domain address, the top level domain, and any additional pathways.  This can be useful for either replacement, sorting, or identification at a later point.
<br><br>

### Bracket Expressions
We have 3 bracket expression within the regex as follows:
 - `[\da-z\.-]` - which designates a range that matches for any digit, any lowercase alpha character, any period ('.'), or any hyphen ('-').
 - `[a-z\.]` - which designates a range that matches for any lowercase alpha character, or any period ('.').
 - `[\/\w \.-]` - which designates a range that matches for a forward slash ('/'), any word/alphanumeric character, a space, a period ('.'), or any hyphen ('-').

These bracket expressions designate what we would like to include in our matches.  For example, the first two are designed to only include lowercase letters, however the third will allow for both uppercase and lowercase letters due to the `\w`criteria.  The first and second bracket expressions can also contain a hyphen or a period if they are present, but the second will only allow a match if a period is present, not matching if a hyphen is present within the matching area for that bracket expression (which happens to be the ".com" area).
<br><br>

## Author
This tutorial was prepared by Morgan Clarke, whose work can be found [here](https://github.com/morgs999).