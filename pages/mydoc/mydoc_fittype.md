---
title: fittype
tags:
keywords:
last_updated: May 4, 2020
summary: "Create a fit type object."
sidebar: mydoc_sidebar
permalink: mydoc_fittype.html
folder: mydoc
---
## Syntax
`ftype = fittype('ltype')`<br>
`ftype = fittype('expr')`<br>
`ftype = fittype('expr','PropertyName',PropertyValue,...)`

where

|`'ltype'`|The name of a library model, spline, or interpolant|
|`'expr'`|An expression representing a custom model|
|`'PropertyName'`|The name of a fit type object property|
|`PropertyValue`|A valid value for `PropertyName`|
|`ftype`|A fit type object|

## Description
`ftype = fittype('ltype')` creates the fit type object ftype from the library model, spline, or interpolant specified by `ltype`. You can display the library fit type names with the [cflibhelp][mydoc_cflibhelp] function.

`ftype = fittype('expr')` creates the fit type object from the expression specified by `expr`, which represents the custom model you will use to fit your data. To create a general (nonlinear) custom model, specify the entire equation as one expression. To create a linear custom model, pass in a cell array of expressions to `expr` but do not include the coefficients. Each element of the cell array corresponds to one term of the model. If there is a constant term, use "1" as the corresponding element in the cell array.

By default, the independent variable is assumed to be x, the dependent variable is assumed to be y. There are no problem-dependent variables, and all other variables are assumed to be coefficients of the model. All coefficients must be scalars.

`ftype = fittype('expr','PropertyName',PropertyValue,...)` creates a fit type object using the specified property name/property value pairs. The supported property names are given below.

|**Property Name**|**Description**|
|`coefficients`|Specify the coefficient names. Use a cell array if there are multiple names.|
|`dependent`|Specify the dependent (response) variable name|
|`independent`|Specify the independent (predictor) variable name|
|`options`|Specify the default fit options for the current expression|
|`problem`|Specify the problem-dependent (constant) names. Use a cell array if there are multiple names|

## Example
Create a fit type object for a custom general equation and define the problem-dependent name to be "n".

```
ftype = fittype('a*x+b*exp(n*x)','problem','n');
```

Define the independent variable to be "chan".

```
ftype = fittype('a*chan+b*exp(n*chan)','ind','chan','prob','n')
ftype =
     General model:
       ftype(a,b,n,chan) = a*chan+b*exp(n*chan)
```

Create a fit type object for a custom linear equation and specify names for the coefficients.

```
ftype = fittype({'cos(x)','1'},'coeff',{'a1','a2'})

ftype =
     Linear model:
       ftype(a1,a2,x) = a1*cos(x) + a2
```

Create a fit type object for the Rat33 library model. Note that the display includes the full equation.

```
ftype = fittype('rat33')

ftype =
   General model Rat33:
   ftype(p1,p2,p3,p4,q1,q2,q3,x) = (p1*x^3 + p2*x^2 + p3*x + p4)/
                (x^3 + q1*x^2 + q2*x + q3)
```

Create a fit type object and include the existing fit options object `opts`, and fit to the census data.

```
load census
opts = fitoptions('Method','Nonlinear','Normalize','On');
ftype = fittype('a*exp(b*x)+c','options',opts);
f1 = fit(cdate,pop,ftype);
```

## See Also
[cflibhelp][mydoc_cflibhelp]

{% include links.html %}
