---
title: fitoptions
tags:
keywords:
last_updated: May 4, 2020
summary: "Create or modify a fit options object."
sidebar: mydoc_sidebar
permalink: mydoc_fitoptions.html
folder: mydoc
---
## Syntax

`opts = fitoptions` <br>
`opts = fitoptions('ltype')`<br>
`opts = fitoptions('ltype','PropertyName',PropertyValue,...)`<br>
`opts = fitoptions('method',value)`<br>
`opts = fitoptions('method',value,'PropertyName',PropertyValue,...)`<br>
`opts = fitoptions(opts,'PropertyName',PropertyValue,...)`<br>
`opts = fitoptions(opts,newopts)`

where

|`'ltype'`|The name of a library model, spline, or interpolant|
|`'PropertyName'`|The name of a fit options property|
|`PropertyValue`|A valid value for `PropertyName`|
|`'method'`|Specify a fitting method|
|`value`|A supported fitting method value|
|`opts, newopts`|A fit options object|

## Description

`opts = fitoptions` creates the empty fit options object `opts`. The returned options are supported by all fitting methods, and are given by the properties below. Note that curly braces denote default property values.

|**Property**|**Description**|
|`Normalize`|Specifies whether the data is centered and scaled. The value can be {'off'} or 'on'|
|`Exclude`|A vector of one or more data points to exclude from the fit. You can use the [excludedata][mydoc_excludedata] function to create this vector.|
|`Weights`|A vector of weights associated with the response data|
|`Method`|The fitting method. A complete list of supported fitting methods is given below.|

`opts = fitoptions('ltype')` creates a default fit options object for the library or custom fit type specified by `ltype`. You can display the library model, interpolant, and smoothing spline names with the [cflibhelp][mydoc_cflibhelp] function.

`opts = fitoptions('ltype','PropertyName',PropertyValue,...)` creates a fit options object for the specified library fit type, and with the specified property names and property values. Note that you can specify `PropertyName` or `PropertyValue` without regard to case, and you can make use of name completion by supplying the minimum number of characters that uniquely identify the string.

`opts = fitoptions('method',value)` creates a default fit options object for the fitting method specified by `value`. A complete list of supported fitting methods is given below.

`opts = fitoptions('method',value,'PropertyName',PropertyValue,...)` creates a default fit options object for the specified fitting method, and with the specified property names and property values.

`opts = fitoptions(opts,'PropertyName',PropertyValue,...)` modifies the existing fit options object with the specified property names and property values.

`opts = fitoptions(opts,newopts)` combines the existing fit options object `opts` with a new fit options object `newopts`. If both objects have the same Method value, the nonempty properties in `newopts` override the corresponding properties in `opts`. If the objects have different Method values, the output object will have the same Method as `opts`, and only the Normalize, Exclude, and Weights properties of `newopts` will override the corresponding properties in opts.

## Additional Fit Options
To display the possible fit options property values, use the `set` function.
```
set(opts)
```

To display the current fit options property values, use the `get` function.

```
get(opts)
```

If `Method` is NearestInterpolant, LinearInterpolant, PchipInterpolant, or CubicSplineInterpolant, there are no additional fit options.

If `Method` is SmoothingSpline, then the SmoothingParam property is available to configure the smoothing parameter. You can specify any value between 0 and 1. The default value depends on the data set.

If `Method` is LinearLeastSquares, the additional fit option properties shown below are available.

|**Property**|**Description**|
|`Robust`|Specifies whether to use the robust linear least squares fitting method. The value can be {'off'} or 'on'|
|`Lower`|A vector of lower bounds on the coefficients to be fitted. The default value is an empty vector indicating that the fit is not constrained by lower bounds. If bounds are specified, the vector length must equal the number of coefficients. An unconstrained lower bound is specified by -Inf.|
|`Upper`|A vector of upper bounds on the coefficients to be fitted. The default value is an empty vector indicating that the fit is not constrained by upper bounds. If bounds are specified, the vector length must equal the number of coefficients. An unconstrained upper bound is specified by Inf.

If `Method` is NonlinearLeastSquares, the additional fit option properties shown below are available.

|**Property**|**Description**|
|`Robust`|Specifies whether to use the robust nonlinear least squares fitting method. The value can be {'off'} or 'on'|
|`Lower`|A vector of lower bounds on the coefficients to be fitted. The default value is an empty vector indicating that the fit is not constrained by lower bounds. If bounds are specified, the vector length must equal the number of coefficients. An unconstrained lower bound is specified by -Inf.|
|`Upper`|A vector of upper bounds on the coefficients to be fitted. The default value is an empty vector indicating that the fit is not constrained by upper bounds. If bounds are specified, the vector length must equal the number of coefficients. An unconstrained upper bound is specified by Inf.|
|`StartPoint`|Vector of coefficient starting values. The default value is an empty vector. If the default value is passed to the fit function, then starting points for some library models are determined heuristically. For other models, the values are selected randomly on the interval (0,1).|
|`Algorithm`|Algorithm used for the fitting procedure. The value can be 'Levenberg-Marquardt','Gauss-Newton', or {'Trust-Region'}.|
|`DiffMax Change`|Maximum change in coefficients for finite difference gradients. The default value is 0.1.|
|`DiffMin Change`|Minimum change in coefficients for finite difference gradients. The default value is 10<sup>-8</sup>.|
|`Display`|Level of display. {'notify'} displays output only if the fit does not converge. 'final' displays only the final output. 'iter' displays output at each iteration. 'off' displays no output.|
|`MaxFunEvals`|Maximum number of function (model) evaluations allowed. The default value is 600.|
|`MaxIter`|Maximum number of fit iterations allowed. The default value is 400.|
|`TolFun`|Termination tolerance on the function (model) value. The default value is 10<sup>-6</sup>.|
|`TolX`|Termination tolerance on coefficients. The default value is 10<sup>-6</sup>.|

## Example
Create an empty fit options object and configure the object so that data is normalized before fitting.

```
opts = fitoptions;
opts.Normal = 'on'

opts =
 
    Normalize: 'on'
      Exclude: []
      Weights: []
       Method: 'None'
```

Creating an empty fit options object is particularly useful when you want to configure only the Normalize, Exclude, or Weights properties for a data set, and then fit the data using the same fit options object, but with different fitting methods. For example, fit the census data using a third degree polynomial, a one-term exponential, and a cubic spline.

```
load census
f1 = fit(cdate,pop,'poly3',opts);
f2 = fit(cdate,pop,'exp1',opts);
f3 = fit(cdate,pop,'cubicsp',opts);
```

You can return values for some fit options with the [fit][mydoc_fit] function. For example, fit the census data using a smoothing spline and return the default smoothing parameter. Note that this value is based on the data passed to fit.

```
[f,gof,out] = fit(cdate,pop,'smooth');
smoothparam = out.p
smoothparam =

    0.0089
```

Increase the default smoothing parameter by about 10% and fit again.

```
opts = fitoptions('Method','Smooth','SmoothingParam',0.0098);
[f,gof,out] = fit(cdate,pop,'smooth',opts);
```

Create two noisy Gaussian peaks -- one with a small width and one with a large width.

```
a1 = 15; b1 = 3; c1 = 0.02;
a2 = 35; b2 = 7.5; c2 = 4;
x = (1:0.01:10)';
rand('state',0)
gdata = a1*exp(-((x-b1)/c1).^2) + a2*exp(-((x-b2)/c2).^2) ...
    + 5*(rand(size(x))-.5);
```

Fit the data using the two-term Gaussian library model.

```
ftype = fittype('gauss2');
gfit = fit(x,gdata,ftype);
Maximum number of function evaluations exceeded. Increasing
MaxFunEvals (in fit options) may allow for a better fit, or 
the current equation may not be a good model for the data.
```

Since the Display property is set to its default value Notify, a message is included as part of the display since the fit did not converge. The message indicates that you should try increasing the number of function evaluations.

The fit results are shown below.

```
gfit
gfit =
     General model Gauss2:
       gfit(x) =  a1*exp(-((x-b1)/c1)^2) + a2*exp(-((x-b2)/c2)^2)
     Coefficients (with 95% confidence bounds):
       a1 =       43.59  (-411.9, 499.1)
       b1 =       7.803  (0.7442, 14.86)
       c1 =       4.371  (-3.065, 11.81)
       a2 =      -10.86  (-373.4, 351.7)
       b2 =       11.05  (-190.4, 212.5)
       c2 =       6.985  (-124.6, 138.5)
```

By examining the fitted coefficients, it is clear that the algorithm has difficulty fitting the narrow peak, and does a good job fitting the broad peak. In particular, note that the fitted value of the a2 coefficient is negative. To help the fitting procedure converge, specify that the lower bounds of the amplitude and width parameters for both peaks must be greater than zero. To do this, create a fit options object for the gauss2 model and configure the Lower property to zero for a1, c2, a2, and c2, but leave b1 and b2 unconstrained.

```
opts = fitoptions('gauss2');
opts.Lower = [0 -Inf 0 0 -Inf 0]; 
```

Fit the data using the new constraints.

```
gfit = fit(x,gdata,ftype,opts)
gfit =
     General model Gauss2:
       gfit(x) =  a1*exp(-((x-b1)/c1)^2) + a2*exp(-((x-b2)/c2)^2)
     Coefficients (with 95% confidence bounds):
       a1 =          35  (34.82, 35.17)
       b1 =        7.48  (7.455, 7.504)
       c1 =       3.993  (3.955, 4.03)
       a2 =       4.824  (2.964, 6.684)
       b2 =           3  (2.99, 3.01)
       c2 =     0.03209  (0.01774, 0.04643)
```

This is a much better fit although you can still improve the a2 value.

## See Also
[cflibhelp][mydoc_cflibhelp], [fit][mydoc_fit], [get][mydoc_get], [set][mydoc_set]

{% include links.html %}
