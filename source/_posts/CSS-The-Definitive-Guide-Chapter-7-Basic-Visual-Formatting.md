---
title: 'CSS: The Definitive Guide-Chapter 7-Basic Visual Formatting'
date: 2017-12-14 23:04:45
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> with a model as open add powerful as that contained within CSS, no book could hope to cover every possible way of combining properties and effects.

<!--more-->

## Basic Boxes

CSS assumes that every element generates one or more rectangular boxes, called elment boxes. Each element box has a content area at its core.

- Normal flow: The left-to-right, top-to-bottom rendering of text in Western languages and the familiar text layout of traditional HTML documents.
- Nonreplaced element: An elemnt whose content is contained within the document.
- Replaced element: An element that serves as a placeholder for something else.
- Block-level element: An element such as a paragraph, heading, or a div.
- Inline element: An element such as strong or span.
- Root element: The element at the top of document tree.

## Block-Level Elements

Block-level elements can behave in both predictable and surprising ways.

### Horizontal Formatting

Horizontal formatting is often more complex than you'think.

- Horizontal properties: margin-left, border-left, padding-left, width, padding-right, border-right, margin-right.
- Using auto: set properties to a value of auto, and give the remaining two properties specific values, then the property that is set to auto determines the length required to make the element box's width equal to the parent element's width.
- More than one auto: If both margins are set to auto, they are set to equal lengths, thus centering the element within its parent.
- Negative margins: With a negative left margin, not only does the paragraph spill beyongd the borders of the div, but it also spills beyond the edge of the brower window itself.
- Percentage: The bottom line is that it's impossible to create a fully flexible element layout based solely on percentages unless you're willing to avoid using borders
- Replaced elements: When a replaced element's width is changed from its intrinsic width, the value of height is scaled to match, unless height has been set to an explicit value of its own.

### Vertical Formatting

Like horizontal formatting, vertical formatting of block-level elements has its own set of interesting behaviors.

- Vertical properties: margin-top, border-top, padding-top, height, padding-bottom, border-bottom, margin-bottom.
- Percentage heights:
- Auto heights
- Collapsing vertical margins
- Negative margins


### List Items

List items have a few special rules of their own. They are typically preceded by a marker, such as a small dot or a number.

## Inline Elements

Nonreplaced and replaced elements are treated somewhat differently in the inline context, and we'll look at each in turn as we explore the construction of inline elements

- Anonymous text: This is any string of characters that is not contained within an inline element.
- Em box: This is defined in the given font, otherwise known as the character box.
- Content area: In nonreplaced elements, the content area can be one of two things, and the CSS2.1 specification allows user agents to choose which one.
- Leading: The leading is the difference between the values of font-size and line -height
- Inline box: This is the shortest box that bounds the highest and lowest points of the inline boxes that are found in the line.

## Altering Element Display

display

- Values: none | inline | block | inline-block | list-item | run-in | table | inline-table | table-row-group | table-header-group | table-footer-group | table-row | table-column-group | table-column | table-cell | tabel-caption | inherit
- Initial value: inline
- Applies to: All elements
- Inherited: No
- Computed value: Varies for floated, positioned, and root elements (see CSS2.1, section 9.7); otherwise, as specified.
- Note: The values compact and marker appeared in CSS2 but were dropped from CSS2.1 due to lack of widespread support.

## Summary

Although some aspects of the CSS formatting model may seem counterintuitive at first, they begin to make sense as you work with them more.In many cases, rules that initially seem nonsensical or even idiotic turn out to prevent bizarre or otherwise undesirable document displays.