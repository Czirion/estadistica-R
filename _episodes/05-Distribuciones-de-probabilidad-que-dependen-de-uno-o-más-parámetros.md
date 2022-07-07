---
title: "Distribuciones de Probabilidad que Dependenden de Uno o Más Parámetros"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

El científico realiza mediciones y las usa para encontrar fórmulas matemáticas que describan la naturaleza. Karl Pearson (1857-1936) tuvo la idea de que cuando se realiza un número grande de mediciones, lo que se obtiene es una distribución de valores. Esta distribución de valores se describe mediante una fórmula matemática que depende de uno o mas parametros.

## La distribución Gama y sus parámetros
La función de densidad de una variable Gamma está dada por:

$$ \frac{1}{\Theta^{\alpha}\Gamma(alpha)}x^{\alpha-1}e^{-x/\Theta} $$

en donde $ \alpha $ es el parámetro de forma y $ \Theta $ el parámetro de escala. En la figura, $ \alpha $ toma los valores 1.5, 2, 3, 4.5, 6. El parámetro de escala $ \Theta $ se mantuvo constante e igual a 1. Ver archivo `Gama.1.r`.
