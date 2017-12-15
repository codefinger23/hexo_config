---
title: 'CSS: The Definitive Guide-Chapter 3-Structure and the Cascade'
date: 2017-12-10 20:20:01
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> The structural tree is what allows selectors to function and is also central to a similarly crucial aspect of CSS: inheritance.

<!--more-->

## Specificity

A selector's specificity is determined by the the components of the selector itself. A specificity value is expressed in four parts, like this: 0,0,0,0. The actual specificity of a selector is determined as follows:

- For every ID attribute value given in the selector, add 0,1,0,0.
- For every class attribute value, attribute selection, or pseudo-class given in the selection, add 0,0,1,0.
- For every element and pseudo-element given in the selector, add 0,0,0,1.
- Combinators and the universal selector do not contribute anything to the specificity(more on the these value later)

The first zero is reserved for inline style declarations, which trump any other declaration's specificity.

> The primacy of inline style declarations is new to CSS2.1, and it exists to captrue the state of web brower behavior at the time CSS2.1 was written. In CSS2, the specificity of inline style declaration was 1,0,0(CSS2 specificities had three values, not four). In other words, it had the same specificity as an ID selector, which would have easily overridden inline styles.

important declarations can let a declaration outweights all other considerations. mark them by inserting !important just before the terminating semicolon in a declaration.

## Inheritance

Inheritance is the mechanism by which styles are applied not only to a specified element, but also to its descendats.The value is then propagated down the tree to the descendant elements and continues on until there are no more descendants to inherit the value.

> some properties are not inherited. As it happens, most of the box-model properties——including margins, padding, backgrounds, and borders——are not inherited.

## The Cascade

CSS is based on a method of causing styles to cascade together, which is made possible by combining inheritance and specificity.

1. Find all rules that contain a selector that matches a given element.
2. Sort by explicit weight all declarations applying to the element. Those rules marked !important are given higher weight than those that are not. Sort by origin all declarations applying to a given element. There are three origins: author, reader, and user agent. Under normal circumstances, the author's styles win out over the reader's styles. !important reader styles are stronger than any other styles, including !important author styles. Both auther and reader styles override the user agent 's default styles.
3. Sort by specificity all declarations applying to a given element. Those elments with a higher specificity have more weight than those with lower specificity.
4. Sort by order all declarations applying to a given elment. The later a declaration appears in the style sheet or document, the more weight it is given. Declarations that appear in an imported style sheet are considered to come before all declarations within the style sheet that imports them.

### Sorting by Weight and Origin

There are five levels to consider in terms of declaration weight. In order of most to least weight.

1. Reader important declarations
2. Author important declarations
3. Author normal declarations
4. Reader normal declarations
5. User agent declarations

### Sorting by Specificity

According to the third rule, if conflicting declarations apply to an element and they all have the same weight, they should be sorted by specificity, with the most specific declaration winning out.

### Sorting by Order

Finally, under the fourth rule, if two rules have exactly the same weight, origin, and specificity, then the one that occurs later in the style sheet wins out.

## Summary

Perhaps the most fundamental aspect of Cascading Style Sheets is the cascade itself——the process by which conflicting declarations are sorted out and from which the final document presentation is determined. Integral to this process is the specificity of selectors and their associated declarations, and the mechanism of inheritance.