---
title: Units of Radar Cross Section
date: 2017-12-23 17:35:53
tags: Electromagnetics
description: The units of radar cross section - normalized to wavelength or 1 meter
mathjax: true
---

## Scattering Width: Two-Dimensional Target

$$\sigma_{2-D} = lim_{\rho\rightarrow\infty}[2\pi\rho\frac{|\mathrm{E}^s|^2}{|\mathrm{E}^i|^2}]$$

Thus the unit of the scattering width is meters. With 1 meter as the reference, the dB/meter is defined as

$$\sigma(dB/meter)=10log(\frac{\sigma_{2-D}}{1 meter})$$

The scattering width can also be normalize to the wavelength $\lambda$, which is in meters.

$$\sigma(dB/\lambda)=10log(\frac{\sigma_{2-D}}{\lambda})$$

## Radar Cross Section: Three-Dimensional Target

$$\sigma_{3-D} = lim_{r\rightarrow\infty}[4\pi{r^2}\frac{|\mathrm{E}^s|^2}{|\mathrm{E}^i|^2}]$$

$$\sigma(dB/sm)=10log(\frac{\sigma_{3-D}}{1 m^2})$$



