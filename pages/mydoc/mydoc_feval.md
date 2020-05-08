---
title: feval
tags:
keywords:
last_updated: May 4, 2020
summary: "Evaluate a fit result object or a fit type object."
sidebar: mydoc_sidebar
permalink: mydoc_feval.html
folder: mydoc
---
## Syntax
`f = feval(fresult,x)` <br>
`f = feval(ftype,coef1,coef2,...,x)`

where

|`fresult`|A fit result object|
|`x`|A column vector of values at which `fresult` or `ftype` is evaluated|
|`ftype`|A fit type object|
|`coef1,coef2,...`|The model coefficients assigned to `ftype`|
|`f`|A column vector containing the result of evaluating `fresult` or `ftype` at `x`|

## Description
`f = feval(fresult,x)` evaluates the fit result object `fresult` at the values specified by `x`, and returns the result to `f`. You create a fit result object with the [fit][mydoc_fit] function.

`f = feval(ftype,coef1,coef2,...,x)` evaluates the fit type object `ftype` using the coefficients specified by `coef1, coef2,...`. You create a fit type object with the [fittype][mydoc_fittype] function.

You can also evaluate a fit result or a fit type object using the following syntax.

```
f = fresult(x);
f = ftype(coef1,coef2,...,x);
```

## Example
Create a fit type object and evaluate the object at x using the specified model coefficients.

```
x = (0:0.1:10)';
ftype = fittype('a*x^2+b*x');
f = feval(ftype,1,2,x);
```

Create a fit result object and evaluate the object over a finer range in x.

```
y = x.^2+(rand(size(x))-0.5);
xx = (0:0.05:10)';
fresult = fit(x,y,ftype);
f = feval(fresult,xx);
```

## See Also
[fit][mydoc_fit], [fittype][mydoc_fittype]

{% include links.html %}
