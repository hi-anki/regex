# Regular Expressions
Regular Expressions are a string of characters that express a search pattern.
## Charset (Character Sets)
+ Defined by `[characters enclosed withing square brackets]`
+ Example:
  ```regex
  [abc] : will match all the occurrences containing characters a,b and c
  [abc]z : will match all the occurrences of az, bz and cz
  z[abc] : will match all the occurrences of za, zb and zc
  ```

## Range
+ Defined using a `-`.
+ Example:
  ```regex
  [a-c] will match all the occurrences containing a,b and c. Same as [abc]
  [a-c]z = [abc]z
  [1-9] : matches numbers 1 to 9
  ```

### Multiple Ranges
```regex
[a-cx-z] = matches a, b, c, x, y and z
[a-cx-z]z = matches az, bz, cz, xz, yz and zz
```

## Character Exclusion (Negated Character Sets)
To exclude a character from charset, use `^` symbol.

Example: 
```regex
[^k]ing : matches words like ring, ping, sing, zing but not king

<!-- To exclude a range of characters -->
[^abc]at : matches fat, sat, rat but not bat or cat
```

## Wildcard
To match any character at a place except `\n`, use `.` 

## Quantification
A quantifier after an element (such as a token, character, or group) specifies how many times the preceding element is allowed to repeat.

```regex
[a.c] : matches all the occurrences that are 3 letters long, start with a and end with c. eg: abc, acc, aac, adc, a0c, a@c....
```

To make a character optional, use `?`.

```regex
[abc?] : matches occurrences with ab or abc, as c is made optional here.
```

**Note**: To match for a literal `.` or `?`, use escape sequence `\`.
```regex
[a\.c] : will match the occurrences of a.c
[a\?c] : will match the occurrences of a?c
```

## Whitespace Characters
`\ ` : single whitespace

`\t` : tabspace

`\n` : new line

`\r` : carriage return

## Repetition
`expr{num}` : matches the `expr` .... `num` times.

```regex
z{5} : matches all the occurrences of zzzzz
z{1,5} : matches all the occurrences of z, zz, zzz, zzzz, zzzzz
z{2, } : matches all the occurrences of zz or z's more than two times.
z* : matches zero or more occurrences of z ('', z, zz, zzz, zzzz .....)
z+ : matches zero or more occurrences of z (z, zz, zzz, zzzz .....)
```

## Starts With
To check if a string starts with an expr, use `^`.

```regex
^abc : matches occurrences starting with abc
```

**Note**: `^` When used with characters set works as an excluder.

## Ends With
To check if a string ends with an expr, use `$`.

```regex
xyz$ : matches occurrences ending with xyz
```

## Grouping
Parentheses are used to define the scope and precedence of the operators.

## Conditional (Boolean OR)
```regex
Buy More (Bread|Milk) : matches (Buy More Bread, Buy More Bread)
``

## Meta-Characters
+ To match a single digit: `\d`
+ To match a single non-digit: `\D`
+ To match a single alphanumeric character (including _): `\w`
+ To match a single special character: `\W`
+ To match a single whitespace character: `\s`
+ To match a single character non-whitespace character: `\S` 

# Useful Ones
+ To match all the alphabets: `[a-zA-Z]`
+ To match files having a numbered pattern: `file_name[1-9]` : will match file1, file2, ...... file8, file9
+ To match all the numbered files except file with number 4: `file_name[^7]`
+ To match all the lines not starting with a number: `^\D`
+ We can use `seriali[sz]e` to match both variations of the word serialize.