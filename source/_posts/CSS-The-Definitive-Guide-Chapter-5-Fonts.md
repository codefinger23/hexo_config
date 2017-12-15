---
title: 'CSS: The Definitive Guide-Chapter 5-Fonts'
date: 2017-12-12 22:45:20
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> CSS does not provide ultimate control over fonts any more than a word processor does.

<!--more-->

## Font Families

- Values: [[<family-name> | <generic-family>],]* [<family-name> | <generic-family>] | inherit
- Initial value: User agent-specific
- Applies to: All elements
- Inherited: Yes
- Computed value: As specified

## Font Weights

- Values: normal | bold | bolder | lighter | 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 | inherit
- Initial value: normal
- Applies to: All elements
- Inherited: Yes
- Computed value: One of the numeric values(100, et.), or one of the numeric values plus one of the relative values (bloder or lighter)

## Font Size

- Values: xx-small | x-small | small | medium | large | x-large | xx-large | smaller | larger | <length> | <percentage> | inherit
- Initial value: medium
- Applies to: All elements
- Inherited: Yes
- Percentages: Calculated with respect to the parent elements's font size
- Computed value: An absolute length

## Styles and Variants

### Fonts with Style

- Values: italic | oblique | normal | inherit
- Initial value: normal
- Applies to: All elements
- Inherited: Yes
- Computed value: As specified

### Font Variations

- Values: small-caps | normal | inherit
- Initial value: normal
- Applies to: All elements
- Inherited: Yes
- Computed value: As specified

## Stretching and Adjusting Fonts

font-stretch

- Values: normal | wider | narrower | ultra-condensed | extra-condensed | condensed | semi-condensed | semi-expanded | semi-expanded | expanded | extra-expand | ultra-expanded | inherit
- Initial value: normal
- Applies to: All elements
- Inherited: Yes

font-size-adjust

- Values: <number> | none | inherit
- Initial value: none
- Applies to: All elements
- Inherited: Yes

## Font Matching

1. The user agent creates, or otherwise access, a database of font propertis.
2. The user agent takes apart an elment to which font properties have been applied and constructs a list of font properties necessary for the display of that element.
3. If there was no font match in Step 2, the user agent looks for alternate fonts within the same font family.
4. Assuming a generic match has been found, but it doesn't contain everything needed to display a given element——the font is missing the copyright symbol, for instance——then the user agent goes back to Step 3, which entails a search for another alternate font and another trip through Step 2.
5. Finally, if no match has been made and all alternate fonts have been tried, then the user agent selects the default font for the given generic font family and does the best it can can to display the element correctly.

## Font-Face Rules

- Font-name matching
- Intelligent font matching
- Font synthesis
- Font download

## Summary

Although authors cannot count on a specific font being used in a document, they can very easily specify generic font families to be used.