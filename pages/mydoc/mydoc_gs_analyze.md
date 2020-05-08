---
title: Analyzing fit results
tags:
keywords: 
last_updated: May 5, 2020
summary: "Analyze fit results."
sidebar: mydoc_sidebar
permalink: mydoc_gs_analyze.html
folder: mydoc
---
## Introduction
You can evaluate (interpolate or extrapolate), differentiate, or integrate a fit over a specified data range with the Analysis GUI. You open this GUI by pressing **Analysis** on the Curve Fitting Tool.

For this example, you will extrapolate the quadratic polynomial fit to predict the US population from the year 2000 to the year 2050 in 10 year increments. To do so, enter the appropriate data vector in the **Analyze at Xi** field, select the **Evaluate fit at Xi** check box, and then press the **Apply** button. The numerical extrapolation results are shown below.

{% include image.html file="ch_sta8a.gif" %}

By selecting the **Plot results** and **Plot data set** check boxes, and pressing **Apply**, you can plot the extrapolated values and the data in a new figure window.

{% include image.html file="extrap1_.gif" %}

## Saving the Analysis Results
Press the **Save to workspace** button to save the extrapolated values as a structure to the workspace.

{% include image.html file="save_ana.gif" %}

The resulting analysis structure is shown below.

~~~
analysisresults

analysisresults = 
      xi: [6x1 double]
    yfit: [6x1 double]
~~~

{% include links.html %}
