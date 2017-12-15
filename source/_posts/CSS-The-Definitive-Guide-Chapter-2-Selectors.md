---
title: 'CSS: The Definitive Guide-Chapter 2-Selectors'
date: 2017-12-10 01:01:04
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> One of the primary advatages of CSS——particularly to designers——is its ablility to easily apply a set of styles to all elements of the same type.

<!--more-->

## Basic Rules

CSS allows to create rules that are simple to change, edit, and apply to all the text elements.

- Rule Structure: Selector(,Selector)* {(property: value;)*}
- Element Selectors: A selector is most often an HTML elment, but not always.
- Declarations and Keywords: The declaration block contains one or more declarations.

## Grouping

- The comma(,) connected selectors with a group, share a public declaration block.
- The universal selector displayed as an asterisk(*). matches any element at all, much like a wildcard.
- Grouping Declarations: split by semicolons and ignore whitespace in style sheets.

## Class and ID Selectors

### Class Selectors

this simple class selector is the name of a class is preceded by a period(.)
and the multiple class selector connect with period(.) can match the elements contains all selectors.

### ID Selectors

ID selectors are preceded by an octothorpe(#). 

## Attribute Selectors

- Simple Attribute Selection: Selectors[attribute] Declarations
- Selection Based on Exact Attribute Value: Selectors[attribute='value'] Declarations
- Selection Based on Partial Attribute Values: Selectors[attribute(^|$|*)='value'] Declarations
- A Particular Attribute Selection Type: *[lang|="en"] {color: white;}

## Using Document Structure

- Parent-Child Relationship
- Ancestor-Descendant Relationship

### Descendant Selectors

In a descendant selector, the selector side of a rule is composed of two or more space-separated selectors.

### Selectiong Children

Use the child combinator which is the greater-than symbol choose the child of special element.

### Selecting Adjacent Sibling Elements

adjacent sibling combinator is represented as a plus symbol(+).

## Pseudo-Classes and Pseudo-Elements

- Pseudo-Class Selectors: Selectors:(link|visited|focus|hover|active|first-child|lang(*))
- Pseudo-Element Selectors: Slectors:(first-letter|first-line|before|after)

## Summary

By using selectors based on the documents's language, authors can create CSS rules that apply to a large number of similar elments just as easily as they can constructrules that aply in very narrow circumstances.