---
title: Use LaTeX in MarkdownPad with Typora
mathjax: true
description: Use LaTeX with MathJax
date: 2019-01-01 00:00:00
---

1. In the front matter, set `mathjax: true` in order to use mathjax for equation rendering.
2. Open `marked.js` (in directory `\node_modules\marked\lib`)
   * Solve the problem of `\\,\{, \} `
   * Reference: http://blog.csdn.net/emptyset110/article/details/50123231

This is an equation in a separate line

$$x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$

This is an equation within text, $x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}$

Maxwell equations
$$
\begin{eqnarray}
\nabla\cdot\vec{E} &=& \frac{\rho}{\epsilon_0} \\
\nabla\cdot\vec{B} &=& 0 \\
\nabla\times\vec{E} &=& -\frac{\partial \vec{B}}{\partial t} \\
\nabla\times\vec{B} &=& \mu_0\left(\vec{J}+\epsilon_0\frac{\partial \vec{E}}{\partial t} \right)
\end{eqnarray}
$$
However, the equations are not well displayed after being deployed.

In order to solve the problem,`hexo-math`is adopted to render the equations.

1. `npm install hexo-math --save`
2. `hexo math install`

