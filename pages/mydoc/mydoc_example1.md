---
title: Example 1
tags: [getting_started]
keywords: release notes, announcements, what's new, new features
last_updated: May 4, 2020
summary: "Curve Fit example 1."
sidebar: mydoc_sidebar
permalink: mydoc_example1.html
folder: mydoc
---

## Relative links

This example fits the ENSO data using several custom nonlinear equations.
The ENSO data are monthly averaged atmospheric pressure differences
between Easter Island and Darwin, Australia. This difference drives the trade
winds in the southern hemisphere.
As shown in “Example: Smoothing Data” on page 2-33, the ENSO data are
clearly periodic, which suggests they can be described by a Fourier series.

The question to be answered in this example is how many cycles (periods)
exist? As a first attempt, assume a 12 month cycle and fit the data using one
sine term and one cosine term.

$$y = a_0 + a_1\cos(2\pi) + + b_1\sin(2\pi)$$

{% include links.html %}