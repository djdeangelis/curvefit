---
title: fit
tags:
keywords:
last_updated: May 4, 2020
summary: "Fit data using a library or custom model, a smoothing spline, or an interpolant."
sidebar: mydoc_sidebar
permalink: mydoc_fit.html
folder: mydoc
---
## Syntax
`fresult = fit(xdata,ydata,'ltype')` <br>
`fresult = fit(xdata,ydata,'ltype','PropertyName',PropertyValue,...)` <br>
`fresult = fit(xdata,ydata,'ltype',opts)` <br>
`fresult = fit(xdata,ydata,'ltype',...,'problem',values)` <br>
`fresult = fit(xdata,ydata,ftype,...)` <br>
`[fresult,gof] = fit(...)` <br>
`[fresult,gof,output] = fit(...)`

where

|`xdata`|A column vector of predictor data|
|`ydata`|A column vector of response data|
|`'ltype'`|The name of a library model, spline, or interpolant|
|`'PropertyName'`|The name of a fit options property|
|`PropertyValue`|A valid value for `PropertyName`|
|`opts`|A fit options object|
|`'problem'`|Specify problem parameters|
|`values`|A cell array of problem parameter values|
|`ftype`|A fit type object|
|`fresult`|The fit result object|
|`gof`|Goodness of fit statistics|
|`output`|A structure containing information that is associated with the fitting procedure|

## Description
`fresult = fit(xdata,ydata,'ltype')` fits the data specified by `xdata` and `ydata` to the library model, interpolant, or smoothing spline specified by `ltype`. The fit result is returned to `fresult`. You can display the library fit type names with the [cflibhelp][mydoc_cflibhelp] function. `xdata` and `ydata` cannot contain Infs or NaNs. Additionally, only the real part of a complex value is used.

`fresult = fit(xdata,ydata,'ltype',PropertyName, PropertyValue,...)` fits the data using the options specified by ``PropertyName`` and `PropertyValue`. You can display the fit options available for the specified library fit type with the [fitoptions][mydoc_fitoptions] function.

`fresult = fit(xdata,ydata,'ltype',opts)` fits the data using options specified by the fit options object `opts`. You create a fit options object with the [fitoptions][mydoc_fitoptions] function. This is an alternative syntax to specifying property name/property value pairs.

`fresult = fit(xdata,ydata,'ltype',...,'problem',values)` assigns values to problem parameters. `values` is a cell array with one element per parameter. Problem parameters are problem-dependent constants that you define as part of your model. See the [fittype][mydoc_fittype] function for more information on problem parameters.

`fresult = fit(xdata,ydata,ftype,...)` fits the data to the fit type object specified by `ftype`. You create a fit type object with the [fittype][mydoc_fittype] function.

`[fresult,gof] = fit(...)` returns goodness of fit statistics to the structure `gof`, which includes the fields shown below.

|**Field**|**Description**|
|`sse`|Sum of squares due to error|
|`rsquare`|Coefficient of determination|
|`dfe`|Degrees of freedom|
|`adjrsquare`|Degree-of-freedom adjusted coefficient of determination|
|`rmse`|Root mean squared error (standard error)|

`[fresult,gof,output] = fit(...)` returns the structure `output`, which contains information that is associated with the fitting procedure used. Supported fitting procedures include linear least squares, robust nonlinear least squares, and so on. Some information applies to all fitting procedures, while other information is relevant only for specific fitting procedures. For example, the information returned for nonlinear least squares fits is given below.

|**Field**|**Description**|
|`numobs`|Number of observations (response values)|
|`numparam`|Number of unknown parameters to fit|
|`residuals`|Vector of residuals|
|`Jacobian`|Jacobian matrix|
|`exitflag`|Describes the exit condition. If exitflag > 0, the function converged to a solution. If exitflag = 0, the maximum number of function evaluations or iterations was exceeded. If exitflag < 0, the function did not converge to a solution.|
|`iterations`|Number of iterations used to complete the fit|
|`funcCount`|Number of function evaluations used to complete the fit|
|`firstorderopt`|Measure of first-order optimality|
|`algorithm`|Fitting algorithm used|

{% include note.html content="For rationals and Weibull library models, the coefficient starting values are randomly selected in the range [0,1]. Therefore, if you perform multiple fits to a data set using the same equation, you may get different coefficient results due to different starting values. To avoid this situation, pass in a vector of starting values each time you fit or define a specific state for the random number generator, `rand` or `randn`, before fitting." %}

## Example
Fit the census data with a second degree polynomial library model and return the goodness of fit statistics and the output structure.

```
load census
[fit1,gof1,out1] = fit(cdate,pop,'poly2');
```

Normalize the data and fit with a third degree polynomial.

```
[fit1,gof1,out1] = fit(cdate,pop,'poly3','Normalize','on');
```

Fit the data with a single-term exponential library model.

```
[fit2,gof2,out2] = fit(cdate,pop,'exp1','Normalize','on');
```

Create a fit options object, and try to find a better fit by overriding the default starting points for the fit coefficients.

```
opts = fitoptions('exp1','Norm','on','start',[100 0.1]);
[fit3,gof3,out3] = fit(cdate,pop,'exp1',opts);
```

Fit the data to a custom model that contains the problem parameter, n.

```
mymodel = fittype('a*exp(b*n*x)+c','problem','n');
opts = fitoptions(mymodel);
set(opts,'normalize','on')
[fit4,gof4,out4] = fit(cdate,pop,mymodel,opts,'problem',{2});

Warning: Start point not provided, choosing random start point.
```

The warning occurs whenever you fit data with a custom nonlinear model and do not provide starting points.

## See Also
[cflibhelp][mydoc_cflibhelp], [fitoptions][mydoc_fitoptions], [fittype][mydoc_fittype]

{% include links.html %}
