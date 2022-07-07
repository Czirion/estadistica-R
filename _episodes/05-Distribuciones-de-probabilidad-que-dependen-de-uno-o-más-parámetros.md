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

$$ \frac{1}{\Theta^{\alpha}\Gamma(\alpha)}x^{\alpha-1}e^{-x/\Theta} $$

en donde $ \alpha $ es el parámetro de forma y $ \Theta $ el parámetro de escala. En la figura, $ \alpha $ toma los valores 1.5, 2, 3, 4.5, 6. El parámetro de escala $ \Theta $ se mantuvo constante e igual a 1. Ver archivo `Gama.1.r`.

![Forking Repositories]({{ page.root }}/fig/Distribucion1.png)

## Método del rechazo para generar muestras
El método del rechazo nos permite simular la realización de una variable aleatoria definida por una funci ́on de densidad arbitraria. Esta función puede depender de uno o más parámetros. Ver el archivo `Método.del.Rechazo.r` .

~~~
> ejectionK <- function(fx, a, b, K) {
> # simula una variable con funci ́on de densidad fx
> # supone que fx es 0 fuera de [1, b] y acatada por K
>   while (TRUE) {
>     x <- runif(1, a, b)
>     y <- runif(1, 0, K)
>     if (y < fx(x)) return(x)
>   }
> }
~~~
{: .language-r}

1. Genere X∼Uni[a,b] y Y∼Uni[0,K], variables independientes.
2. Si Y < fx(X) entonces se reporta X, en otro caso, ir al paso 1.
