---
title: cflibhelp
tags:
keywords:
last_updated: May 4, 2020
summary: "Display information about library models, splines, and interpolants."
sidebar: mydoc_sidebar
permalink: mydoc_cflibhelp.html
folder: mydoc
---
## Syntax
`cflibhelp`<br>
`cflibhelp group`

where

|`group`|The name of the fit type group|

## Description
`cflibhelp` displays the names, equations, and descriptions for all the fit types in the curve fitting library. You can use the fit type name as an input parameter to the [cfit][mydoc_cfit], [fit][mydoc_fit], and [fittype][mydoc_fittype] functions.

`cflibhelp group` displays the names, equations, and descriptions for the fit type group specified by `group`. The supported fit type groups are given below.

|**Group**|**Description**|
|`distribution`|Distribution models such as Weibull|
|`exponential`|One-term and two-term exponential equations|
|`fourier`|Sums of sine and cosine equations up to eight terms|
|`gaussian`|Sums of Gaussian equations up to eight terms|
|`interpolant`|Interpolant fit types including linear, nearest neighbor, cubic spline, and <br>shape-preserving interpolation|
|`polynomial`|Polynomial equations up to ninth degree|
|`power`|One-term and two-term power equations|
|`rational`|Ratios of polynomial equations up to degree 5 in both numerator and denominator|
|`sin`|Sums of sine equations up to eight terms|
|`spline`|Cubic spline and smoothing spline fit types|

## Example
Display the names and descriptions for the spline fit type group.

~~~
cflibhelp spline

SPLINES

        SPLINETYPE             DESCRIPTION

        cubicspline            cubic interpolating spline
        smoothingspline        smoothing spline
~~~

Display the model names and equations for the polynomial fit type group.

~~~
cflibhelp polynomial

  POLYNOMIAL MODELS

        MODELNAME             EQUATION

          poly1                Y = p1*x+p2
          poly2                Y = p1*x^2+p2*x+p3
          poly3                Y = p1*x^3+p2*x^2+...+p4
          ...
          poly9                Y = p1*x^9+p2*x^8+...+p10
~~~

## See Also
[cfit][mydoc_cfit], [fit][mydoc_fit], [fittype][mydoc_fittype]

{% include links.html %}
