---
title: get
tags:
keywords:
last_updated: May 4, 2020
summary: "Return properties for a fit options object."
sidebar: mydoc_sidebar
permalink: mydoc_get.html
folder: mydoc
---
## Syntax
`get(opts)`<br>
`a = get(opts)`<br>
`a = get(opts,'PropertyName')`

where

|`opts`|A fit options object|
|`'PropertyName'`|The name of a fit options property, or a cell array of property names|
|`ftype`|A structure or cell array of fit options property values|

## Description
`get(opts)` returns all property names and their current values to the command line for the fit options object `opts`.

`a = get(opts)` returns the structure `a` where each field name is the name of a property of `opts`, and each field contains the value of that property.

`a = get(opts,'PropertyName')` returns the value of the property specified by `PropertyName` for `opts`. If `PropertyName` is replaced by a cell array of strings containing property names, then get returns a cell array of values to `a`.

## Example
Create a fit options object for a second degree polynomial, and return the current property values to the command line.

```
opts = fitoptions('poly2');
get(opts)

ans = 
    Normalize: 'off'
      Exclude: []
      Weights: []
       Method: 'LinearLeastSquares'
       Robust: 'Off'
        Lower: []
        Upper: []
```

## See Also
[set][mydoc_set]

{% include links.html %}
