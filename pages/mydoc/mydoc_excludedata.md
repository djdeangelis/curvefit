---
title: excludedata
tags:
keywords:
last_updated: May 4, 2020
summary: "Display descriptive information for curve fitting objects."
sidebar: mydoc_sidebar
permalink: mydoc_excludedata.html
folder: mydoc
---
## Syntax
`outliers = excludedata(xdata,ydata,'MethodName',MethodValue)`

where

|`xdata`|A column vector of predictor data|
|`ydata`|A column vector of response data|
|`'MethodName'`|The data exclusion method|
|`MethodValue`|The value associated with `MethodName`|
|`outliers`|A logical vector that defines data to be excluded from a fit|

## Description
`outliers = excludedata(xdata,ydata,'MethodName',MethodValue)` identifies data to be excluded from a fit using the specified `MethodName` and `MethodValue`. `outliers` is a logical vector containing 1's marking data points to exclude while fitting, and 0's marking data points to include while fitting. The data exclusion methods are given below.

| **Method**|**Description** |
|`box`|A four-element vector that specifies a box of data to include in a fit. Data outside the box is excluded. You specify the box as [$$x_{min}$$ $$x_{max}$$ $$y_{min}$$ $$y_{max}$$]|
|`domain`|A two-element vector that specifies the domain of data to include in a fit. Data outside this domain is excluded. You specify the domain as [$$x_{min}$$ $$x_{max}$$]|
|`indices`|A vector specifying the indices of the data points to be excluded|
|`range`|A two-element vector that specifies the range of data to include in a fit. Data outside this range is excluded. You specify the range as [$$y_{min}$$ $$y_{max}$$]|

You can combine data exclusion methods using logical operators. For example, to combine methods using the \| (OR) operator

```
outliers = excludedata(xdata,ydata,'indices',[3 5]);
outliers = outliers|excludedata(xdata,ydata,'box',[1 10 0 90]);
```

In some cases, you may want to use the ~ (NOT) operator to specify a box that contains all the data to exclude.

```
outliers = ~excludedata(xdata,ydata,'box',[1 10 0 90]);
```

## Example
Generate random data in the interval [0, 15], create a sine wave with noise, and add two outliers with the value 2.

```
rand('state',0);
x = 15*rand(150,1); 
y = sin(x) + (rand(size(x))-0.5)*0.5;
y(ceil(length(x)*rand(2,1))) = 2;
```

Identify outliers that are outside the interval [-1.5, 1.5] using the range method.

```
outliers = excludedata(x,y,'range',[-1.5 1.5]);
```

Identify the same outliers using the indices method.

```
ind = find((y>1.5)|(y<-1.5));
outliers = excludedata(x,y,'indices',ind);
```

You can pass outliers to the fit function to exclude the specified data points from a fit.

```
ftype = fittype('a*sin(b*x)');
fresult = fit(x,y,ftype,'startpoint',[1 1],'exclude',outliers);
```

## See Also
[fit][mydoc_fit]

{% include links.html %}
