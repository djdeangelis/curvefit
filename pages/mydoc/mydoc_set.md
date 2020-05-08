---
title: set
tags:
keywords:
last_updated: May 4, 2020
summary: "Configure or display property values for a fit options object."
sidebar: mydoc_sidebar
permalink: mydoc_set.html
folder: mydoc
---
## Syntax

`set(opts)`<br>
`a = set(opts)`<br>
`set(opts,'PropertyName',PropertyValue,...)`<br>
`set(opts,PN,PV)`<br>
`set(opts,S)`

where

|`opts`|A fit options object|
|`'PropertyName'`|A property name for `opts`|
|`PropertyValue`|A property value supported by `PropertyName`|
|`PN`|A cell array of property names|
|`PV`|A cell array of property values|
|`S`|A structure with property names and property values|
|`a`|A structure array whose field names are the property names for `opts`, or cell array of possible values|

## Description
`set(opts)` displays all configurable property values for the fit options object `opts`. If a property has a finite list of possible string values, then these values are also displayed.

`a = set(opts)` returns all configurable properties and their possible values for `opts` to the structure `a`. The field names of `a` are the property names of `opts`, and the field values are cell arrays of possible property values. If the property does not have a finite set of possible values, then the cell array is empty.

`set(opts,'PropertyName',PropertyValue,...)` configures multiple property values with a single command.

`set(opts,PN,PV)` configures the properties specified in the cell array of strings `PN` to the corresponding values in the cell array `PV`.

`set(opts,S)` configures the named properties to the specified values for `opts`. The structure `S` has field names given by the fit options object properties, and the field values are the values of the corresponding properties.

## Example
Create a custom nonlinear model, and create a default fit options object for the model.

```
mymodel = fittype('a*x^2+b*exp(n*c*x)','prob','n');
opts = fitoptions(mymodel);
```

Configure the Robust and Normalize properties using property name/property value pairs.

```
set(opts,'Robust','LAR','Normalize','On')
```

Configure the Display, Lower, and Algorithm properties using cell arrays of property names and property values.

```
set(opts,{'Disp','Low','Alg'},{'Final',[0 0 0],'Levenberg'})
```

## See Also
[fitoptions][mydoc_fitoptions], [get][mydoc_get]

{% include links.html %}
