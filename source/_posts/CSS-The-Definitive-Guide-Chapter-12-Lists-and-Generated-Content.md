---
title: 'CSS: The Definitive Guide-Chapter 12-Lists and Generated Content'
date: 2017-12-20 22:13:15
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> To see how all these list options fit together, we'll explore basic list styling befor moving on to examine the generation of content and counters.

<!--more-->

## Lists

### Types of Lists

list-style-type

- CSS2.1 values: disc | circle | square | decimal | decimal-leading-zero | lower-roman | upper-roman | lower-greek | lower-latin | upper-latin | armenian | georgian | none | inherit
- CSS2 values: disc | circle | square | decimal | decimal-leading-zero | upper-alpha | lower-alpha | upper-roman | lower-roman | lower-greek | hebrew | armenian | georgian | cjk-ideographic | hiragana | katakana | hiraganairoha | none | inherit
- Initial value: disc
- Applies to: Elements whose display value is list-item
- Inherited: Yes
- Computed value: As specified

### List Item Images

list-style-image

- Values: <uri> | none | inherit
- Initial value: none
- Applies to: Elements whose display value is list-item
- Inherited: Yes
- Comoputed value: For <uri> values, the absolute URI; otherwise, none

### List-Marker Positions

- Values: inside | outside | inherit
- Initial value: outside
- Applies to: Elements whose display value is list-item
- Inherited: Yes
- Computed value: As specified

### List Styles in Shorthand

list-style

- Values: [ <list-style-type> || <list-style-image> || <list-style-position> ] | inherit
- Initial value:  Refer to individual properties
- Applies to: Elements whose display value is list-item
- Inherited: Yes
- Computed value: See individual properties

## Generated Content

In ordered lists, the marker is a counter that increments by one for each successive list item.

### Inserting Generated Content

To insert generated content into the document, use the :before and :after pseudo-elements. These place generated content before or after the content of an element by way of the contetn property.

### Specifying Content

content

- Values: normal | [ <string> | <uri> | <counter> | attr(<identifier>) | open-quote | close-quote | no-open-quote | no-close-quote ]+ | inherit
- Initial value: normal
- Applies to: :befor and :after pseudo-elemnets
- Inherited: No
- Computed value: For <uri> values, an absolute URI; for attribute references, the resulting string; otherwise, as specified.

quotes

- Values: [<string><string>]+ | none | inherit
- Initial value; User agent-dependent
- Applies to: All elements
- Inherited: Yes
- Computed values: As specified

counter-reset

- Values: [<identifier><integer>?]+ | none | inherit
- Initial value: User agent-dependent
- Applies to: All elements
- Inherited: No
- Computed value: As specified

counter-increment

- Values: [<identifier><integer>?]+ | none | inherit
- Initial value: User agent-dependent
- Applies to: All elements
- Inherited: No
- Computed value: As specified

## Summary

Even though list styling isn't as sophisticated as we might like, and browser support for generated content is somewhat spotty, the ability to style lists is still highly userful. 