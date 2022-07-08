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

## Método de Momentos
Los estimadores por el método de los momentos están dados por $ \widehat{\alpha}=\frac{m_{1}^{2}}{m_{2}-m_{1}^{2}} $ y $ \widehat{\Theta}=\frac{m_{2}-m_{1}^{2}}{m_{1}} $ en donde $ m_{k}= \frac{1}{n}\sum_{i=1}^{n}x_{i}^{k} $ .

En la figura se muestra el histograma de 10 000 estimaciones realizadas a partir de muestra de tamaño 50 cada una. La línea punteada en rojo muestra el valor real del parámetro.

![Forking Repositories]({{ page.root }}/fig/Histograma2.png)

Ver archivo `Gama.Momentos.r` .

Tamaño de la muestra:
~~~
> muestra <- 200
~~~
{: .language-r}

Número de muestras:
~~~
> tot <- 10000
~~~
{: .language-r}

Parámetro de forma:
~~~
> a <- 10
~~~
{: .language-r}

Parámetro de escala:
~~~
> t <- 0.5
~~~
{: .language-r}

Se inicializan las variables:
~~~
> t.hat <- c()
> a.hat <- c()
~~~
{: .language-r}

Y después:
~~~
> for(i in 1:tot) {
>   m <- rgamma(muestra, shape=a, scale=t)
>   m1 <- mean(m)
>   m2 <- sum(m^2)/muestra
>   t.hat[i] <- (m2-m1^2)/m1
>   a.hat[i] <- m1 ˆ 2/(m2-m1^2)
> }
~~~
{: .language-r}

Para ver la salida del código anterior:
~~~
> hist(a.hat)
> hist(t.hat)
~~~
{: .language-r}

La siguiente tabla contiene algunos estimadores según el método de los momentos. Note que $ m_{1}=\overline{X} $ .

| Nombre   | Formula |
| ------- | ----------- |
| Uniforme [0,a] | $ \widehat{\alpha}=2\overline{X} $ |
| Bernoulli(p) | $ \widehat{p}=\overline{X} $ |
| Binomial(n,p) | $ \widehat{p}=\overline{X} $  |
| Poisson $ (\alpha) $ | $ \widehat{p}=\overline{X} $ |
| Normal $ (\mu,\sigma^{2}) $ | $ \widehat{p}=\overline{X} $ |
