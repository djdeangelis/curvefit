---
title: confint
tags:
keywords:
last_updated: May 4, 2020
summary: "Compute confidence bounds for fitted coefficients."
sidebar: mydoc_sidebar
permalink: mydoc_confint.html
folder: mydoc
---
## Syntax
`ci = confint(fresult)` <br>
`ci = confint(fresult,level)`

where

|`fresult`|A fit result object|
|`level`|The confidence level|
|`ci`|An array of confidence bounds|

## Description
`ci = confint(fresult)` returns 95% confidence bounds to `ci` for the fit coefficients associated with `fresult`. `fresult` is the fit result object returned by the [fit][mydoc_fit] function. `ci` is a 2-by-n array where n is the number of coefficients associated with `fresult`. The top row of the array contains the lower bound, while the bottom row of the array contains the upper bound for each coefficient

`ci = confint(fresult,level)` returns the confidence level specified by `level` to `ci`. You specify level on the interval (0,1). For example, if level is 0.99, then 99% confidence bounds are calculated.

To calculate confidence bounds, confint uses R<sup>-1</sup> (the inverse R factor from QR decomposition of the Jacobian), the degrees of freedom for error, and the root mean squared error. This information is automatically returned by the fit function and contained within the fit result object.

The fit function automatically returns 95% confidence bounds for coefficients. If coefficients are bounded and one or more of the estimates are at their bounds, then those estimates are regarded as fixed, and do not have confidence bounds. Note that you cannot calculate confidence bounds for the smoothing spline and interpolant fit types.

## Example
Fit the census data to a second degree polynomial. The display for `fresult` includes the 95% confidence bounds for the fitted coefficients.

```
load census
fresult = fit(cdate,pop,'poly2')

fresult =
     Linear model Poly2:
       fresult(x) = p1*x^2 + p2*x + p3
     Coefficients (with 95% confidence bounds):
       p1 =    0.006541  (0.006124, 0.006958)
       p2 =      -23.51  (-25.09, -21.93)
       p3 =  2.113e+004  (1.964e+004, 2.262e+004)
```

Calculate 95% confidence bounds for the fitted coefficients using `confint`.

```
ci = confint(fresult,0.95)
ci =

    0.0061242      -25.086        19641
    0.0069581      -21.934        22618
```

Note that the fit display and the array returned by `confint` present the confidence bounds using slightly different formats. The fit display mimics an n-by-3 array where n is the number of coefficients, the first column is the coefficient variable, the second column is the fitted coefficient value, and the third column is the lower and upper bound. `confint` returns a 2-by-n array where the top row contains the lower bound and the bottom row contains the upper bound for each coefficient.

## See Also
[fit][mydoc_fit]

{% include links.html %}
