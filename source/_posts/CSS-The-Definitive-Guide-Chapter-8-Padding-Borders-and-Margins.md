---
title: 'CSS: The Definitive Guide-Chapter 8-Padding, Borders, and Margins'
date: 2017-12-15 21:54:18
tags:
---
> These borders can set an element apart from others, accentuate its appearance, mark certain keinds of data as having been changed, or any number of other things.

<!--more-->

## Basic  Element Boxes

all document elements generate a rectangular box called the element box, which describes the amount of space that an element occupies in the layout of the document.

### Width and Height

width

- Values: <length> | <percentage> | auto | inherit
- Initial value: auto
- Applies to: Block-level and replaced elements
- Inherited: No
- Percentages: Refer to the width of the containing block
- Computed value: For auto and percentage values, as specified; otherwise, an absolute length, unless the property does not apply to the element (then auto)

height

- Value: <length> | auto | inherit
- Initial value: auto
- Applies to: Block-level and replaced elements
- Inherited: No
- Percentages: Calculated with respect to the height of the containing block
- Computed value: For auto and percentage value, as specified; otherwise, an absolute length, unless the property does not apply

### Margins Versus Padding

Element boxes provide only small amounts of space between elements. can add padding, margins, or a combination of padding and margins.

## Margins

### Replicationg Values

- If the value for left is missing, use the value provided for right.
- If the value for bottom is missing, use the value provided for top.
- If the value for right is missing, use the value provided for top.

### Single-Side Margin Properties

margin-top, margin-right, margin-bottom, margin-left

- Values: <length> | <percentage> | auto | inherit
- Initial value: 0
- Applies to: All elements
- Inherited: No
- Percentages: Refer to the width of the containing block
- Computed value: For percentages, as specified; otherwise, the absolute length

## Borders

### Borders with Style

border-style

- Values: [none | hidden | dotted | dashed | solid | double | groove | ridge | inset | outset]{1, 4} | inherit
- Initial value: Not defined for shorthand properties
- Applies to: All elements
- Inherited: No
- Computed value: See individual properties (border-top-style, etc.)
- Note: According to CSS1 and CSS2, HTML user agents are only required to support solid and none; the rest of the values (except for hidden) may be interpreted as solid; this restriction was dropped in later drafts of CSS2.1

border-top-style, border-right-style, border-bottom-style, border-left-style

- Values: none | hidden | dotted | dashed | solid | double | groove | ridge | inset | outset | inherit
- Initial value: none
- Applies to: All elements
- Inherited: No
- Computed value: As specified

### Border Widths

border-width
- Values: [ thin | medium | thick | <length>]{1, 4} | inherit
- Initial value: Not defined for shorthand properties
- Applies to: All elements
- Inherited: No
- Computed value: See individual properties (border-top-style, etc.)

border-top-width, border-tight-width, border-bottom-width, border-left-width

- Values: thin | medium | thick | <length> | inherit
- Initial value: medium
- Applies to: All elements
- Inherited: No
- Computed value: Absolute length; 0 if the style of the border is none or hidden

### Border Colors

border-color

- Values: [<corlr> | transparent]{1, 4} | inherit
- Initial value: Not defined for shorhand properties
- Applies to: All elements
- Inherited: No
- Computed value: See individual properties (border-top-color, etc.)

border-top-color, border-tight-color, border-bottom-color, border-left-color

- Values: <color> | transparent | inherit
- Initial value: The value of color for the element
- Applies to: All elements
- Inherited: No
- Computed value: If no value is specified, use the computed value of the property color for the same element; otherwise, as specified.

### Shorthand Border Properties

border-top, border-right, border-bottom, border-left

- Values: [<border-width> || <border-style> || <border-color>] | inherit
- Initial value: Not defined for shorthand properties
- Applies to: All elements
- Inherited: No
- Computed value: See individual properties (border-width, etc.)

### Global Borders

border

- Values: [<border-width> || <border-style> || <border-color>] | inherit
- Initial value: Refer to individual properties
- Applies to: All elements
- Inherited: No
- Computed value: As specified

## Padding

padding

- Values: [<length> | <percentage>]{1, 4} | inherit
- Initial value: Not defined for shorthand elements
- Applies to: All elements
- Inherited: No
- Percentages: Refer to the width of the containing block
- Computed value: See individual properties (padding-top, etc.)
- Note: Padding can never be negative

padding-top, padding-right, padding-bottom, padding-left

- Values: <length> | <percentage> | inherit
- Initial value: 0
- Applies to: All elements
- Inherited: No
- Percentages: Refer to the width of the containing block
- Computed value: For percentage values, as specified; for length values, the absolute length
- Note: Padding can never be negative

## Summary

The ability to apply margins, borders, and padding to any element is one of the things that set CSS so far above traditional web markup.