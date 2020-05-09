---
title: Parametric fitting
tags:
keywords:
last_updated: May 6, 2020
summary: "Parametric fitting."
sidebar: mydoc_sidebar
permalink: mydoc_parametricfit.html
folder: mydoc
---
## Introduction

<table>
<colgroup>
<col width="25%" />
<col width="75%" />
</colgroup>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td markdown="span">`Linear`</td>
<td markdown="span">Fit a different linear polynomial between each pair of data points.</td>
</tr>
<tr>
<td markdown="span">`Nearest neighbor`</td>
<td markdown="span">Set the value of an interpolated point to the value of the nearest data point. Note that this method does not generate any new data points.</td>
</tr>
<tr>
<td markdown="span">`Cubic spline`</td>
<td markdown="span">Fit a different cubic polynomial between each pair of data points.</td>
</tr>
<tr>
<td markdown="span">`Shape-preserving`</td>
<td markdown="span">Piecewise cubic Hermite interpolation (PCHIP). This method preserves monotonicity and the shape of the data.</td>
</tr>
</tbody>
</table>


{% include image.html file="c12alphb.gif" %}

{% include note.html content="Goodness of fit statistics, prediction bounds, and weights are not defined for interpolants. Additionally, the fit residuals are always zero (within computer precision) since interpolants pass through the data points." %}

$$p\sum_{i}w_{i}(y_{i} - s(x_{i}))^2 + (1 - p)\int{\left(d^{2}s \over dx^{2}\right)}^2dx$$

{% include links.html %}
