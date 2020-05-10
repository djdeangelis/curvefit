---
title: Overview
keywords: 
tags:
sidebar: mydoc_sidebar
permalink: index.html
summary: "Overview of features, environment, and workflow."
---
## Introduction
The Curve Fitting Tool is a collection of graphical user interfaces (GUIs) and script functions built on a full-featured scientific computing platform. The tool provides you with these core features:

* Data preprocessing, such as sectioning and smoothing.
* Parametric and nonparametric data fitting:
  * Parametric fits use library equations or custom equations. Library equations include polynomials, exponentials, rationals, and sums of Gaussians. Custom equations are equations that you define.
  * Nonparametric fits use a smoothing spline or various interpolants.
* Standard linear least squares, nonlinear least squares, weighted least squares, constrained least squares, and robust fitting procedures.
* Fit statistics to assist you in determining the goodness of fit.
* A graphical environment that allows you to:
  * Explore and analyze data sets and fits both visually and numerically.
  * Save your work in various formats including script files, binary files, and workspace variables.

## Exploring the environment
The Curve Fitting Tool consists of two different environments: a graphical environment and a command line environment. Although the two environments are functionally equivalent, you generally cannot mix the two when performing a given curve fitting task. 

For example, you cannot generate a fit at the command line, and then import that fit into the graphical environment. However, you can create a fit in the graphical environment and then generate an associated script file. You can then recreate the fit from the command line and modify the script file. For this reason, as well as for the enhanced data analysis and exploration tools that are available, you should use the graphical environment for most tasks.

To explore the graphical environment:

~~~
cftool
~~~

To explore the command line environment:

~~~
help curvefit
~~~

To view the code for any function:

~~~
type function_name
~~~

To view the help for any function:

~~~
help function_name
~~~

{% include note.html content="You can change the way any toolbox function works by copying and renaming the script file, and then modifying your copy. However, these changes will not be reflected in the graphical environment." %}

## Example data sets
To help you learn how to use the Curve Fitting Tool, several data sets of measured and generated data are provided. Some of these data sets are used in the examples included in this guide.

<table>
<colgroup>
<col width="20%" />
<col width="80%" />
</colgroup>
<thead>
<tr class="header">
<th>Data set</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td markdown="span">`carbon12alpha`</td>
<td markdown="span">Measured angular correlation data from the <sup>12</sup>C(e,e',$$\alpha$$)<sup>8</sup>Be nuclear reaction</td>
</tr>
<tr>
<td markdown="span">`census`</td>
<td markdown="span">United States population figures for the years 1790 to 1990 in 10-year increments</td>
</tr>
<tr>
<td markdown="span">`enso`</td>
<td markdown="span">Measured data of monthly averaged atmospheric pressure differences between Easter Island and Darwin, Australia</td>
</tr>
<tr>
<td markdown="span">`gauss3`</td>
<td markdown="span">Generated data consisting of two poorly resolved Gaussian peaks on an exponential background</td>
</tr>
<tr>
<td markdown="span">`hahn1`</td>
<td markdown="span">Measured data of the thermal expansion of copper as a function of temperature</td>
</tr>
</tbody>
</table>

## Curve fitting workflow
The basic workflow steps involved in any curve fitting scenario are:

1. Import data -- Load predictor data, response data, and weights as vectors in the workspace. 
2. Preprocess data -- View the data, mark data points to be excluded from the fit, and smooth the data.
3. Fit data -- Explore parametric and nonparametric fits, and compare fit results graphically and numerically.
4. Analyze results -- Evaluate (interpolate or extrapolate), differentiate, or integrate the fit results.
5. Save your work -- Save your work for documentation purposes or for later analysis.

These workflow steps are illustrated via a specific example where you will fit US census data to several library models, find the best fit, and extrapolate the best fit to predict the US population in future years.

{% include links.html %}
