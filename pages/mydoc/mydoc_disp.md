---
title: disp
tags:
keywords:
last_updated: May 4, 2020
summary: "Display descriptive information for curve fitting objects."
sidebar: mydoc_sidebar
permalink: mydoc_disp.html
folder: mydoc
---
## Syntax
`obj` <br>
`disp(obj)`

where

|`obj`|A curve fitting object|

## Description
`obj` or `disp(obj)` displays descriptive information for cuve fitting object. You can create `obj` with the [cfit][mydoc_cfit], [fit][mydoc_fit], [fitoptions][mydoc_fitoptions], and [fittype][mydoc_fittype] functions.

## Example
The display for a custom fit type object is shown below.

```
ftype = fittype('a*x^2+b*x+c+d*exp(-e*x)')

ftype =
     General model:
       ftype(a,b,c,d,e,x) = a*x^2+b*x+c+d*exp(-e*x)
```

The display for a fit options object is shown below.

```
fopts = fitoptions('Method','Nonlinear','Normalize','on')

fopts =
        Normalize: 'on'
          Exclude: []
          Weights: []
           Method: 'NonlinearLeastSquares'
           Robust: 'Off'
       StartPoint: []
            Lower: []
            Upper: []
        Algorithm: 'Trust-Region'
    DiffMinChange: 1e-008
    DiffMaxChange: 0.1
          Display: 'Notify'
      MaxFunEvals: 600
          MaxIter: 400
           TolFun: 1e-006
             TolX: 1e-006
```

Note that all fit types have the Normalize, Exclude, Weights, and Method fit options. Additional fit options are available depending on the Method value. For example, if Method is SmoothingSpline, then the SmoothingParam fit option is available.

The display for a fit result object is shown below.

```
fresult = fit(cdate,pop,ftype,fopts)

Warning: Start point not provided, choosing random start point.
Maximum number of function evaluations exceeded. Increasing
MaxFunEvals (in fit options) may allow for a better fit, or 
the current equation may not be a good model for the data.

fresult =

     General model:
       fresult(x) = a*x^2+b*x+c+d*exp(-e*x)
       where x is normalized by mean 1890 and std 62.05
     Coefficients (with 95% confidence bounds):
       a =       21.14  (-27.61, 69.89)
       b =       64.49  (-188.5, 317.4)
       c =       49.92  (-421.5, 521.4)
       d =       11.96  (-458, 481.9)
       e =     -0.7745  (-10.25, 8.701)
```

## See Also
[cfit][mydoc_cfit], [fit][mydoc_fit], [fitoptions][mydoc_fitoptions], [fittype][mydoc_fittype]

{% include links.html %}
