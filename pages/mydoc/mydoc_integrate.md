---
title: integrate
tags:
keywords:
last_updated: May 4, 2020
summary: "Integrate a fit result object."
sidebar: mydoc_sidebar
permalink: mydoc_integrate.html
folder: mydoc
---
## Syntax
`inty = integrate(fresult,x,x0)`

where

|`fresult`|A fit result object|
|`x`|The values at which `fresult` is integrated|
|`x0`|The integration starting point|
|`inty`|A vector of integration values|

## Description
`inty = integrate(fresult,x,x0)` integrates the fit result object `fresult` at the values specified by `x` starting from `x0`, and returns the result to `inty`. The `fresult` object is a fit result object generated by the [fit][mydoc_fit] function. `x` is a scalar or column vector and `inty` is the same size as `x`. `x0` is a scalar.

## Example
Create a noisy sine wave on the interval [-2$$\pi$$, 2$$\pi$$].

```
rand('state',0);
x = (-2*pi:0.1:2*pi)';
y = sin(x) + (rand(size(x))-0.5)*0.2;
```

Create a custom fit type, and fit the data using reasonable starting values.

```
ftype = fittype('a*sin(b*x)');
fit1 = fit(x,y,ftype,'startpoint',[1 1]);
```

Calculate the integral for each value of x starting at -2$$\pi$$

```
inty = integrate(fit1,x,x(1));
```

## See Also
[differentiate][mydoc_differentiate], [cfit][mydoc_cfit], [fit][mydoc_fit]

{% include links.html %}