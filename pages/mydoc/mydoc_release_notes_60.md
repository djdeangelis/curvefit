---
title: Release notes 6.0
tags: [getting_started]
keywords: release notes, announcements, what's new, new features
last_updated: July 16, 2016
summary: "Version 6.0 of the Documentation theme for Jekyll, released July 4, 2016, implements relative links so you can view the files offline or on any server without configuring urls and baseurls. Additionally, you can store pages in subdirectories. Templates for alerts and images are available."
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_60.html
folder: mydoc
---

## Relative links

You can now view the site offline rather than solely through the Jekyll preview server or deployed on a web server. The linking approach in both the sidebar and with inline links uses relative linking throughout.

$$
\begin{align}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align}
$$

Here's another example

$$
\begin{align}
\sqrt{37} & = \sqrt{\frac{73^2-1}{12^2}} \\
 & = \sqrt{\frac{73^2}{12^2}\cdot\frac{73^2-1}{73^2}} \\ 
 & = \sqrt{\frac{73^2}{12^2}}\sqrt{\frac{73^2-1}{73^2}} \\
 & = \frac{73}{12}\sqrt{1 - \frac{1}{73^2}} \\ 
 & \approx \frac{73}{12}\left(1 - \frac{1}{2\cdot73^2}\right)
\end{align}
$$

Inline equations
$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$

When $$a \ne 0$$, there are two solutions to $$ax^2 + bx + c = 0$$ and they are
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$

GREEK characters
$$\alpha, \beta, \gamma, \Gamma, \pi, \Pi, \phi, \varphi, \mu, \Phi$$


## Subfolders for pages

You can creates folders and subfolders for your pages, similar to how you can store posts in folders and subfolders. When Jekyll builds the site, all pages get pushed into the root directory as single html files (rather than being pushed inside folders, or remaining in subfolders). See [Pages][mydoc_pages] for more details.

## Alerts templates

You can use include templates for notes, tips, and warnings. These include templates make it easier to insert notes. If you make an error, you're immediately made aware since the site won't build. See [Alerts][mydoc_alerts] for more details.

## Image templates

Similar to alerts, images also have include templates. You can insert both regular images and inline images, such as images that are a button or icon. See [Images][mydoc_images] for more details.

## Automated links using Markdown formatting

Instead of using YAML references to handle links, I've switched to a Markdown reference style approach. A links.html file iterates through the sidebar files and formats the content in the Markdown reference. You then just use Markdown syntax for the links. See [Links][mydoc_hyperlinks] for more details.

## Workflow maps

If you want to display a workflow map for a process, you can do so by adding some properties in your frontmatter. The workflow map helps guide users through a process. Both simple and complex workflow maps are available. For more details, see [Workflow maps][mydoc_workflow_maps].

## Upgrading

If you want to upgrade from an earlier version of the theme, I recommend that you download the new theme and copy of your Markdown files into the new theme. You'll then need to make adjustments to your page frontmatter, to the sidebar table of contents, links, image references, and alert references. In short, there's no easy upgrade path. But all of this won't take too long if you don't have mountains of content.

{% include links.html %}
