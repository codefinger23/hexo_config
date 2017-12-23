---
title: 'CSS: The Definitive Guide-Chapter 6-Text Properties'
date: 2017-12-13 23:23:55
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> Because text is so important, there are many CSS properties that affect it in one way or another. 

<!--more-->

## Indentation and Horizontal Alignment

### Indenting Text

Indenting the first ilne of a paragraph on a web page is one of the most sought-after text-formatting effects.

text-indent

- Value: <length> | <percentage> | inherit
- Initial value: 0
- Applies to: Block-level elements
- Inherited: Yes
- Percentages: Refer to the width of the containing block
- Computed value: For percentage values, as specified; for length values, the absolute length

### Horizontal Alignment

text-align

- CSS2.1 values: left | center | right | justify | inherit
- CSS2 values: left | center | right | justify | <string> | inherit
- Initial value: User agent-specific; may also depend on writing direction
- Applies to: Block-level elements
- Inherited: Yes
- Computed value: As specified
- Node: CSS2 included a <string> value that was dropped from CSS2.1 due to a lack of implementation

## Vertical Alignment

The line-height property refers to the distance between the baselines of lines of text rather than the size of the font, and it determines the amount by which the height of each element's box is increased or decreased.

line-height

- Values: <length> | <percentage> | <number> | normal | inherit
- Initial value: normal
- Applies to: All elements (but see text regarding replaced and block-level elements)
- Inherited: Yes
- Percentages: Relative to the font size of the element
- Computed value: For length and percentage values, the absolute value; other wise, as specified

## Word Spacing and Letter Spacing

### Word Spacing

The word-spacing property accepts a positive or negative length.

word-spacing

- Values: <length> | normal | inherit
- Initial value: normal
- Applies to: All elements
- Inherited: Yes
- Computed value: For normal, the absolute length 0; otherwise, the absolute length

### Letter Spacing

Many of the issues you encounter with word-spacing also occur with letter-spacing.

letter-spacing

- Values: <length> | normal | inherit
- Initial value: normal
- Applies to: All elements
- Inherited: Yes
- Computed value: For length values, the absolute length; otherwise, normal

## Text Transformation

text-transform

- Values: uppercase | lowercase | capitalize | none | inherit
- Initial value: none
- Applies to: All elements
- Inherited: Yes
- Computed value: As specified

## Text Decoration

text-decoration

- Values: none | [underline || overline || line-through || blink] | inherit
- Initial value: none
- Applies to: All elements
- Inherited: No
- Computed value: As specified

## Text Shadows

CSS2 include a property for adding drop shadows to text, but this property did not make it into CSS2.1 because no browser had implemented full support for it by the time CSS2.1 was completed.

text-shadow

- Values: none | [<color> || <length> <length> <length>? ,]* [<color> || <length> <length> <length> ?] | inherit
- Initial value: none
- Applies to: All elements
- Inherited: No

white-space

- Values: normal | nowrap | pre | pre-wrap | pre-line | inherit
- Initial value: normal
- Applies to: All elements (CSS2.1); block-level elements (CSS1 and CSS2)
- Inherited: No
- Computed value: As specified

direction

- Values: ltr | rtl | inherit
- Initial value: ltr
- Applies to: All elements
- Inherited: Yes
- Computed value: As specified

## Summary

even without altering the font in use, there are many ways to change the appearance of text. There are classic effects such as underlinging, of course, but CSS also enables you to draw lines over text or through it, change the amount of space between words and letters, indent the first line of a paragraph, align text to the left or right, and much more.