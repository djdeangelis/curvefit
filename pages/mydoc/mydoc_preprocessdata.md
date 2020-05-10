---
title: More preprocessing steps
tags:
keywords:
last_updated: May 9, 2020
summary: "Transform the response data and remove non-finite data values."
sidebar: mydoc_sidebar
permalink: mydoc_preprocessdata.html
folder: mydoc
---
## Transforming the response data
In some cases, you may want to transform the response data. Common transformations include the logarithm $$ln(y)$$ and power functions such as 	$$y^{1/2}$$ and $$y^{-1}$$. Using these transformations, you can linearize a nonlinear model, contract response data that spans one or more orders of magnitude, or simplify a model to one that involves fewer coefficients.

{% include note.html content="You must transform variables at the command line, and then import the variables into the Curve Fitting Tool. You cannot transform variables using any of the graphical user interfaces." %}

For example, suppose you want to use the following model to fit your data:

$$y = {1\over{ax^{2} + bx + c}}$$

If you decide to use the power transform $$y^{-1}$$, then the transformed model is given by:

$$y^{-1} = ax^{2} + bx + c$$

As another example, the equation:

$$y = ae^{bx}$$

becomes linear if you take the log transform of both sides:

$$ln(y) = ln(a) + bx$$

You can now use linear least squares fitting procedures.

There are several disadvantages associated with performing transformations:

* For the log transformation, negative response values cannot be processed.
* For all transformations, the basic assumption that the residual variance is constant is violated. To avoid this problem, you can plot the residuals on the transformed scale. For the power transformation shown above, the transformed scale is given by the residuals:

$$r_{i} = y_{i}^{-1} - \hat{y_{i}}^{-1}$$

Deciding on a particular transformation is not always obvious. However, a scatter plot will often reveal the best form to use. In practice you can experiment with various transforms and then plot the residuals from the command line using the transformed scale. If the errors are reasonable (they appear random with minimal scatter, and don't exhibit any systematic behavior), then the transform is a good candidate.

## Removing Infs, NaNs, and outliers
Although the Curve Fitting Tool ignores Infs and NaNs when fitting data, and you can exclude outliers during the fitting process, you may still want to remove this data from your data set. To do so, you modify the associated data set variables from the command line.

For example, when using functions such as [fit][mydoc_fit] from the command line, you must supply predictor (x) and response (y) vectors that contain finite numbers. To remove Infs from both vectors, you can use the `isinf` function.

~~~
ind = find(isinf(x));
x(ind) = [];
y(ind) = [];
~~~

To remove NaNs from both vectors, you can use the `isnan` function in a similar way.

~~~
ind = find(isnan(x));
x(ind) = [];
y(ind) = [];
~~~

{% include links.html %}
