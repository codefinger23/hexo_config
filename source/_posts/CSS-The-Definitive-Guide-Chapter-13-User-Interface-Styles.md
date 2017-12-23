---
title: 'CSS: The Definitive Guide-Chapter 13-User Interface Styles'
date: 2017-12-23 16:01:13
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> The vast majority of CSS is concerned with styling documents, but is offers a passel of userful interface-styling tools for more than just documents.

## Sytetem Fonts and Colors

There may be times when you want your document to mimic the user's computing environment as closely as possibles.

### System Fonts

If the requested system font style is not available or can't be determinded, the user agent is allowed to guess at an appropriate set of font styles.

### System Colors

An obvious drawback of the vague nature of the system color keywords is that different user agents may interpret the keywords in different ways, even if the user agents are running in the same operating system.

## Cursors

cursor

- Values: [[<uri>,]*[ auto | default | pointer | crosshair | move | e-resize | ne-resize | nw-resize | n-resize | se-resize | sw-resize | s-resize | w-resize | text | wait | help | progeress ]] | inherit
- Initial value: auto
- Applies to: All elements
- Inhrited: Yes
- Computed value: For <uri> values, an absolute value; otherwise, as specified

## Outlines

CSS2 introduces one last major piece of user-interface styling: outlines. An outline is sort of like a border, but there are two very important differences.

outline-style

- Values: none | dotted | dashed | solid | double | groove | ridge | inset | outset | inherit
- Initial valuel: none
- Applies to: All elements
- Inherited: No
- Computed value: As specified

outline-width

- Values: thin | medium  | thick | <length> | inherit
- Initial value: medium
- Applies to: All elements
- Inherited: No
- Computed value: Absolute length; 0 if the style of the border is none or hidden

outline-color

- Values: <color> | invert | inherit
- Initial value: invert (or user agent-specific; see text)
- Applies to: All elements
- Inherited: No
- Computed value: As specified

outline

- Values: [ <outline-color> || <outline-style> || <outline-width> ] | inherit
- Initial value: Not defined for shorthand properties
- Applies to: All elements
- Inherited: No
- Computed value:See individual properties (outline-color, etc.)

## Summary

Thanks to user interface styles, ,it's possible for an author to make a document look more like the user's computing environment, especially with a creative use of system color and fonts.