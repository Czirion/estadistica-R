---
title: "Regresión Lineal Simple"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Regresión Lineal Simple
Considere una variable $ Y $ de la forma

$$ Y = \beta_{0} + \beta_{1} x + \epsilon $$ 

en donde $ \beta\_{0} $ y $ \beta\_{1} $ son dos parámetros del modelo, $ x $ es una variable no aleatoria y

$$ \epsilon \sim Normal(0, \sigma^{2}) $$

Aquí, $ \sigma^{2} $ es el tercer parámetro del modelo. Suponga que tenemos _n_ pares de datos

$$ (x_{1}, Y_{1}), (x_{2}, Y_{2}), \cdots, (x_{n}, Y_{n}) $$

A partir de esta muestra, se obtienen estimaciones para los tres parámetros del modelo $ \hat{\beta}\_{0} $, $ \hat{\beta}\_{1} $ y $ \hat{\sigma}^{2} $

## Ejemplo de aplicación del modelo

![Forking Repositories]({{ page.root }}/fig/ejemplo_regresion_lineal.jpg)

## Propiedades de los estimadores del modelo

> ## Notación
>
> $ e_{i} = y\_{i} - \hat{y}\_{i} $ es el i-ésimo residual, siendo $ \hat{y}\_{i} = \hat{\beta}\_{0} + \hat{\beta}\_{1} x_{i} $
> 
> $ SCE = \sum\limits_{i=1}^{n} (y_{i} - \hat{y}\_{i})^{2} $ Es la suma de los cuadrados del error
{: .prereq}  

1. &nbsp;&nbsp;&nbsp; $ \hat{\beta}\_{0} = \bar{y} - \hat{\beta}\_{1} \bar{x} $ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; y &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $\hat{\beta}\_{1} = \frac{S_{xy}}{S_{xx}} $ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; en donde &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ S_{xy} = \sum\limits_{i=1}^{n} (x_{i} - \bar{x}) (y_{i} - \bar{y}) $
