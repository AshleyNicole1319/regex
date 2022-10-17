# Regex Tutorial: Matching a Hex Value

A **regex** (short for **regular expression**) is used for finding a specific pattern in programming languages. With a regex, you can validate inputs, find a replace text, and reformat text. In this tutorial, we will discuss the regex used for matching a hex value.

What is a hex value? Hex values are codes writen in hexadecimal format that are used priamarily to identify colors. Typically beginning with `#` and followed by three sets of 2 alphanumeric characters. The numbers would range between `0-9` and the letters `a-f`. 

If you've worked with CSS, you have probably seen colors defined, either using hexidecimal format or the RGB color values. For example:  

| :large_red_circle: Color Code | Red Value  | Green Value | Blue Value |
| :---: | :---: | :---: | :---: |
| `rgb(255, 0, 0)` | 255 | 0 | 0 |
| `#ff0000` | ff | 00 |  00 |

The RGB color value ranges from `0-255` and can be converted to the 2 alphanumeric characters mentioned above. As you can see the RGB of red would be `rgb(255,0,0)` and the hex value would be `#ff0000`. It's important to note that in some cases, the hex value can be shortened from 6-digits to 3-digits. See the following table for some examples:


| Color | RGB  | 6-Digit Hex | 3-Digit Hex |
| :---: | :---: | :---: | :---: |
| White | rgb(255, 255, 255) | #ffffff | #fff |
| Red | rgb(255, 0, 0) | #ff0000 | #f00 |
| Yellow | rgb(255, 255, 0) | #ffff00 | #ff0 |
| Blue | rgb(0, 0, 255) | #0000ff | #00f |
| Black | rgb(0, 0, 0) | #000000 | #000 |

## Summary
So, what is the spefic regex for matching hex values? We will break it down, but here's a quick look:

**<p align="center">/^#?([a-f0-9]{6}|[a-f0-9]{3})$/</p>**

This could be useful if trying to find a specific color in large body of code. If there is an issue in formatting, causing the color not to appear, the regex could make the search easier. The regex would perform the following sequence of events:

1. Check for the first `#` character
2. Check for lowercase letters between a and f
3. Check for numerical values between 0 and 9
4. Check if the length is 3 or 6 digits - with or without the `#` sign

## Table of Contents
- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors
/`^`#?([a-f0-9]{6}|[a-f0-9]{3})`$`/

**Anchors** indicate the beginning and end of a regex. `^` indicates the beginning and `$` indicates the end. 

In the hex value matching regex specifically: `^#` means look for the `#` and the beginning of the string.

### Quantifiers
/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/

**Quantifiers** indicate how many characters we need. The hex value regex demonstrates multiple examples of quantifiers.

The `{6}` and `{3}` are quantifiers that tell us to look for the preceeding characters 6 or 3 times. In other words, look for a string that is 6 or 3 characters long, that contains `a-f0-9`. This does not include the `#`.

The `?` quantifier makes the preceding character optional. In this case, the `#`. So, when looking for a specific number of characters, the `#` is not included. 

Let's look at an example of this using `/armou?r/`

This would find `armour` or `armor`. How specifically? It will look for *one* `a`, *one* `r`, *one* `m`, *one* `o`, **zero or one** `u`, and *one* `r`.

### OR Operator
/^#?([a-f0-9]{6}`|`[a-f0-9]{3})$/

The `|` represents the **OR operator**, which you may recognize from Javascript. Each part that is separated by `|` is called an **alternative**. The regex will look for a string that is either one alternative or the other.

Our regex, specifically, is looking for a string that is 6 characters long containing a-f0-9 (`[a-f0-9]{6}`) *OR* a string that is 3 characters long containing a-f0-9 (`[a-f0-9]{3}`).

### Character Classes
/^#?([`a-f0-9`]{6}|[`a-f0-9`]{3})$/

Character classes identify character types and tries to find those defined within the bracket. In this regex, there are two ranges in the character class: `a-f` and `0-9`. 

It's important to note that this character class will not look for uppercase letters. In order for uppercase to be included, the character class would have to look something like the following: [a-fA-F0-9]

This could find `#A7B6C5`, `#a7b6c5` or even `#A7b6c5`, and any variation in between.

### Grouping and Capturing
/^#?`(`[a-f0-9]{6}|[a-f0-9]{3}`)`$/

If you **capture** a set of characters within `()`, it would be considered a **group**. This allows the set to act as a single block instead of individual pieces.  

Our regex shows one big group with two expressions.

### Bracket Expressions
/^#?(`[`a-f0-9`]`{6}|`[`a-f0-9`]`{3})$/

**Bracket expressions** are used to match whatever is contained inside those square brackets. The square brackets specify character sets that are followed by the **quantifiers**. This means the character set within square brackets, is followed by the specific quanitifier that applies to it. 

### Greedy and Lazy Match
/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/

Quantifiers are considered **greedy** by default, meaning that they try to match the string as much as possible in all ways possible. If the `?` was removed from our regex, it would work to match every string that begins with `#`, followed by the rest of the items. So #a4f5d0 or #f00 for example.

With the `?` though, the quantifier becomes **lazy**. A **lazy** quantifier means that it will match the string as little as possible. So #f00, #a4f5d0, f00, or a4f5d0

## Author
Ashley Warford is new to coding and learning as she goes! Hoping to be a successful full-stack developer one day. Contact her at <a-warford96@comcast.net> or visit her github <https://github.com/AshleyNicole1319>