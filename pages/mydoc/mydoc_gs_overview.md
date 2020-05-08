---
title: Overview
tags:
keywords:
last_updated: May 5, 2020
summary: "Overview of the core curve fitting features."
sidebar: mydoc_sidebar
permalink: mydoc_gs_overview.html
folder: mydoc
---
## Introduction
This section describes a particular example in detail to help you get started using the Curve Fitting Tool. In this example, you will fit US census data to several library models, find the best fit, and extrapolate the best fit to predict the US population in future years. In doing so, the basic steps involved in any curve fitting scenario are illustrated:

* Importing data -- The predictor data, response data, and weights must exist as vectors in the workspace. After importing, you can view the data, mark data points to be excluded from the fit, and smooth the data.
* Fitting the data -- Explore various parametric and nonparametric fits, and compare fit results graphically and numerically.
* Analyzing the fit -- Evaluate (interpolate or extrapolate), differentiate, or integrate the fit.
* Saving your work -- Save your work for documentation purposes or for later analysis.

## Load the census data
The first step is to load the census data from the built-in `census` file.

~~~
load census
~~~

The workspace now contains two new variables:

* `cdate` is a column vector containing the years 1790 to 1990 in 10-year increments.
* `pop` is a column vector with the US population figures that correspond to the years in `cdate`.

## Open the Curve Fitting Tool
The Curve Fitting Tool is a graphical user interface (GUI) that allows you to:

* Visually explore one or more data sets and fits as scatter plots.
* Graphically evaluate the goodness of fit using residuals and prediction bounds.
* Access additional interfaces for importing and fitting data, and for plotting and analyzing fits to the data.

You open the curve fitting tool with the `cftool` command:

~~~
cftool
~~~

{% include image.html file="cftool1_.gif" %}

{% include links.html %}
