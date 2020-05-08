---
title: Release notes 6.1
tags: [getting_started]
keywords: release notes, announcements, what's new, new features
last_updated: May 3, 2020
summary: "Version 6.1 of the Documentation theme for Jekyll."
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_61.html
folder: mydoc
---

## Links
Link to an internal HTML page: [Install Jekyll on Mac][mydoc_install_jekyll_on_mac]

Link to an external target: [Bundler](http://bundler.io/) to make 

## Math
Aligning equatons 

$$
\begin{align}
\sqrt{37} & = \sqrt{\frac{73^2-1}{12^2}} \\
 & = \sqrt{\frac{73^2}{12^2}\cdot\frac{73^2-1}{73^2}} \\ 
 & = \sqrt{\frac{73^2}{12^2}}\sqrt{\frac{73^2-1}{73^2}} \\
 & = \frac{73}{12}\sqrt{1 - \frac{1}{73^2}} \\ 
 & \approx \frac{73}{12}\left(1 - \frac{1}{2\cdot73^2}\right)
\end{align}
$$

The Fourier series is the trigonometric series representing functions that
are periodic.

$$
f\left( x\right) =\frac{a\left( 0\right) }2+\sum\limits_{n=1}^\infty \left(
a\left( n\right) \cos \frac{n\pi x}L+b\left( n\right) \sin \frac{n\pi x}L\right)
$$
  
where $$a\left( 0\right)$$, $$a\left( n\right)$$ and $$b\left( n\right)$$ are the Fourier coefficients.

Here is an inline equations $$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$

When $$a \ne 0$$, there are two solutions to $$ax^2 + bx + c = 0$$ and they are
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

GREEK characters
$$\alpha, \beta, \gamma, \Gamma, \pi, \Pi, \phi, \varphi, \mu, \Phi$$

## Code
MATLAB code

```Matlab
m = fittype('a*x^2+b*exp(n*x)','prob','n');
f = cfit(m,pi,10.3,3);
````
Generic code

```
m = fittype('a*x^2+b*exp(n*x)','prob','n');
f = cfit(m,pi,10.3,3);
````

Inline code

Use `Kramdown::Document.new(text).to_html`
to convert the `text` in kramdown
syntax to HTML.

## Tables

A simple table

| A simple | table |
| with multiple | lines|

Another simple table

|`ftype`|A fit type object representing a custom or library model|
|`coef1,coef2,...`|The model coefficients|
|`fmodel`|The cfit object|

An HTML table

<table>
<colgroup>
<col width="30%" />
<col width="70%" />
</colgroup>
<tbody>
<tr>
<td markdown="span">`ftype`</td>
<td markdown="span">A fit type object representing a custom or library model</td>
</tr>
<tr>
<td markdown="span">`coef1,coef2,...`</td>
<td markdown="span">The model coefficients</td>
</tr>
<tr>
<td markdown="span">`fmodel`</td>
<td markdown="span">The cfit object</td>
</tr>
</tbody>
</table>

## Reference format

### Purpose      
Create a cfit object

### Syntax
`fmodel = cfit(ftype,coef1,coef2,...)`

## Images

Include an image withna caption.

{% include image.html file="c12alpha.gif" url="http://jekyllrb.com" caption="12C curve fit result" %}

## Notes and Callouts

Notes

{% include note.html content="This is my note. All the content I type here is treated as a single paragraph. <br/><br/> Now I'm typing on a  new line." %}

Callouts

{% include callout.html content="This is my callout. It has a border on the left whose color you define by passing a type parameter. I typically use this style of callout when I have more information that I want to share, often spanning multiple paragraphs. " type="primary" %} 

{% include links.html %}
