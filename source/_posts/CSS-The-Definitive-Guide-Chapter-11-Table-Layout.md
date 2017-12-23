---
title: 'CSS: The Definitive Guide-Chapter 11-Table Layout'
date: 2017-12-19 22:15:05
tags: [读书笔记, 'CSS: The Definitive Guide']
---
> Tables are unique, compared to the rest of document layout. As of CSS2.1, tables alone possess the the ability to associate element sizes with other elments——all the cells in a row have the same height, for example, no matter how much or how litle content each individual cell might contain.

<!--more-->

## Table Formatting

This is referred to as table formatting, and it is quite distinct from table layout: the latter is possible only after the former has been completed.

### Visually Arranging a Table

CSS draws a distinction between table elements and internal table elemnts.

- Each row box encompasses a single row of grid cells.
- A row group's box encompasses the same grid cells as the row boxes it contains.
- A column box encompasses one or more columns of grid cells.
- A column group's box encompasses the same grid cells as the column boxes that it contains.
- Although cells may span several rows or columns, CSS does not define how this happens.
- A cell's box cannot extend beyond the last row box of a table or row group.

### Table Display Values

display

- Values: noen | inline | block | inline-block | list-item | run-in | table | inline-table | table-row-group | table-header-group | table-header-group | table-footer-group | table-row | table-column-group | table-column | table-cell | table-caption | inherit
- Initial value: inline
- Applies to: All elments
- Inherited: No
- Computed value: Varies for floated, positioned, and root elemnts; otherwise, as specified
- Note: The values compact and marker appeared in CSS2 but were dropped from CSS2.1 due to a lack of widespread support

### Anonymous Table Objects

1. If a table-cell element's parent is not a table-row elemnt, then an anonymous table-row object is inserted between the table-cell elemnt and its parent.
2. If a table-row elment's parent is not a table, inline-table, or table-row-group elemnt, then an anonymous table element is inserted between the table-row elemnt and its parent.
3. If a table-column elemnt's parent is not a table, inline-table, or table-column-group elemnt, then an anonymous table element is inserted between the table-column element and its parent.
4. If the parent element of a table-row-group, table-header-group, table-footer-group, table-column-group, or table-caption element is not a table element, then an anonymous table object is inserted between the element and its parent.
5. If a child elemnet of a table or inline-table elemnt is not a table-row-group, table-header-group, table-footer-group, table-row, or table-caption element, then an anonymous table-row object is inserted between the table element and its child element.
6. If a child element of a table-row-group, table-header-group, or table-footer-group element is not a table-row element, than an anonymous table-row object is inserted between the element and its child element.
7. If a child element of a table-row element is not a table-cell element, then an anonymous table-cell object is inserted between the element and its child element.

### Table Layers

To assemble a table's presentation, CSS defines six individual "layers" on which the various aspects of a table are placed.

### Captions

caption-side

- Values: top | bottom
- Initial value: top
- Applies to: Elements with the display value table-caption
- Inherited: Yes
- Computed value: As specified
- Note: The values left and right appeared in CSS2 but were dropped from CSS2.1 due to a lack of widespread support.

## Table Cell Borders

border-collapse

- Values: collapse | separate | inherit
- Initial value: separate
- Applies to: Elements with the display value table or table-inline
- Inherited: Yes
- Computed value: As specified
- Note: In CSS2, the default was collapse

border-spacing

- Values: <length><length>? | inherit
- Initial value: 0
- Applies to: Elements with the display value table or table-inline
- Inherited: Yes
- Computed value: Two absolute lengths
- Note: Property is ignored unless border-collapse value is separate

empty-cells

- Values: show | hide | inherit
- Initial value: show
- Applies to: Elements with the display value table-cell
- Inherited: Yes
- Computed value: As specified
- Note: Property is ignoreed unless border-collapse value is separate

## Table Sizing

### Width

Since thre are two different ways to figure out the width of a table, it's only logical that there be a way to declare which should be used for a given table.

table-layout

- Values: auto | fixed | inherit
- Initial value: auto
- Appplies to: Elements with the display value table or inline-table
- Inherited: Yes
- Computed value: As specified


### Height

The easiest situation to describe is one in which the height is explicityly set via the height property.

## Summary

Due to the legacy of HTML table construction, the CSS table model is row-centric, but it does, thankfully, accommodate columns and limited column styling.