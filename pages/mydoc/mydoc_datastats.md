---
title: datastats
tags:
keywords:
last_updated: May 4, 2020
summary: "Return descriptive statistics about the data."
sidebar: mydoc_sidebar
permalink: mydoc_datastats.html
folder: mydoc
---
## Syntax
`xds = datastats(xdata)` <br>
`[xds,yds] = datastats(xdata,ydata)`

where

|`xdata`|A column vector of predictor data|
|`ydata`|A column vector of response data|
|`xds`|A structure containing descriptive statistics for `xdata`|
|`yds`|A structure containing descriptive statistics for `ydata`|

## Description
`xds = datastats(xdata)` returns statistics for `xdata` to the structure `xds`. The structure contains the fields shown below.

|**Field**|**Description**|
|`num`|The number of data values|
|`max`|The maximum data value|
|`min`|The minimum data value|
|`mean`|The mean value of the data|
|`median`|The median value of the data|
|`range`|The range of the data|
|`std`|The standard deviation of the data|

`[xds,yds] = datastats(xdata,ydata)` returns statistics for `xdata` and `ydata` to the structures `xds` and `yds`.

`xdata` and `ydata` are column vectors of the same size, which contain the fields shown above. Infs or NaNs are ignored, and only the real part of complex data  values are used in the statistics computations.

## Example
Return data statistics for the census data.

```
load census
[xds,yds] = datastats(cdate,pop)

xds = 

       num: 21
       max: 1990
       min: 1790
      mean: 1890
    median: 1890
     range: 200
       std: 62.048

yds = 

       num: 21
       max: 248.7
       min: 3.9
      mean: 85.729
    median: 62.9
     range: 244.8
       std: 78.601
```

{% include links.html %}
