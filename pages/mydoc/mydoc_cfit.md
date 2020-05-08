---
title: cfit
tags:
keywords:
last_updated: May 4, 2020
summary: "Create a cfit object."
sidebar: mydoc_sidebar
permalink: mydoc_cfit.html
folder: mydoc
---
## Syntax
`fmodel = cfit(ftype,coef1,coef2,...)`

where

|`ftype`|A fit type object representing a custom or library model|
|`coef1,coef2,...`|The model coefficients|
|`fmodel`|The cfit object|

## Description
`fmodel = cfit(ftype,coef1,coef2,...)` creates the cfit object `fmodel` based on the custom or library model specified by `ftype`, and with the coefficients specified by `coef1, coef2,...`. You create `ftype` with the [fittype][mydoc_fittype] function.

`cfit` is called by the [fit][mydoc_fit] function. You should call `cfit` directly if you want to assign coefficients and problem parameters to a model without performing a fit.

## Example
Create a fit type object and assign values to the coefficients and to the problem parameter.

~~~
m = fittype('a*x^2+b*exp(n*x)','prob','n');
f = cfit(m,pi,10.3,3);
~~~

## See Also
[fit][mydoc_fit], [fittype][mydoc_fittype]

{% include links.html %}
