---
title: 'CSS: The Definitive Guide-Chapter 9-Colors and Backgrounds'
date: 2017-12-16 15:06:15
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> CSS takes color and backgrounds even further, letting you apply many different colors and backgrounds to a single page, and all without a single FONT or TABLE tag.

<!--more-->

## Colors

### Forground Colors

The easiest way to set the foreground color of an element is with the property color.

color

- Value: <color> | inherit
- Initial value: User agent-specific
- Applies to: All elements
- Computed value: As specified

### Replacingn Attributes

There are many users for color, the most basic of which is to replace the HTML 3.2 BODY attributes TEXT, LINK, ALINK, and VLINK. With th eanchor pseduo-classes, color can replace these BODY attributes outright.

### Affecting Borders

The value of color can also affect the borders around an element.

## Backgrounds

The background area of an element consists of all of the space behind the foreground to the outer edge of the borders; thus, the content box and the padding are all part of an elements's background, and the borders are drawn on top of the background.

background-color

- Values: <color> | transparent | inherit
- Initial value: transparent
- Applies to: All elements
- Inherited: No
- Computed value: As specified

background-image

- Values: <uri> | none | inherit
- Initial value: none
- Applies to: All elements
- Inherited: No
- Computed value: Absolute URI

background-repeat

- Values: repeat | repeat-x | repeat-y | no-repeat | inherit
- Initial value: repeat
- Applies to: All elements
- Inherited: No
- Computed value: As specified

background-position

- Values: [[<percentage> | <length> | left | center | right] [<percentage> | <length> | top | center | bottom]?] || [[left | center | right] || [top | center | bottom]] | inherit
- Initial value: 0% 0%
- Applies to: Block-level and replaced elements
- Inherited: No
- Percentages: Refer to the corresponding point on both the element and the origin image (see explanation in "Percentage values" later in this chapter)
- Computed value: The absolute length offsets, if <length> is specified; otherwise, percentage values

background-attachment

- Values: scroll | fixed | inherit
- Initial value: scroll
- Applies to: All elements
- Inherited: No
- Computed value: As specified

background

- Values: [ <background-color> || <background-image> || <background-repeat> || <background-attachment> || <background-postiton>] | inherit
- Initial value: Refer to individual properties
- Applies to: All elements
- Inherited: No
- Percentages: Values are allowed for <backgroudn-position>
- Computed value: See individual properties

## Summary

Setting colors and backgrounds on elements gives authors a great deal of power. The advatage of CSS over traditional methods is that colors and backgrounds can be applied to any element in a document——not just table cells, for example, or anything enclosed in a FONT tag.