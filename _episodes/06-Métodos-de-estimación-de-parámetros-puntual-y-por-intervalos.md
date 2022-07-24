---
title: "Métodos de Estimación de Parámetros, Puntual y por Intervalos"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Máxima Verosimilitud

Ronald Fisher (1890-1962) se dio cuenta de que los métodos que Karl Pearson había estado usando para estimar los parámetros de una distribución, producían estadísticos
que no necesariamente eran consistentes y que con frecuencia presentaban un sesgo. Para producir estadísticos consistentes y eficientes, Fisher propuso algo que
́él denominó <<estimadores de máxima verosimilitud>>.

La función de verosimilitud de una muestra $ X_{1},..., X_{n} $ está dada por: 

$$ L(\Theta)= f(x_{1}|\Theta)f(x_{2}|\Theta)...(x_{n}|\Theta) $$ 

El estimador máximo verosímil $ \widehat{\Theta} $ del parámetro $ \Theta $ , es aquel valor para el cual:

$$ \mathscr{l}(\Theta)= log L(\Theta) $$

es máximo. Si el tamaño  $ n $  de la muestra es grande, entonces $ \widehat{\Theta} $ tiene una distribución aproximadamente normal con media $ \Theta $ y varianza:

$$ var(\widehat{\Theta_{n}}) =\frac{1}{nE [{\frac{d}{d\Theta}}logf(X|\Theta)]^{2}} $$

Note que $ var(\widehat{\Theta_{n}})\to 0 $ cuando $ n\to \infty $ . Ver el archivo `EMV.Exponencial.r`.

~~~
> LL <- function(r) { #el log de la función de verosimilitud
>   R <- dexp(x, r)
>   -sum(log(R))
> }
~~~
{: .language-r}

~~~
> rt <- 2.5; N <- 1250; x <- rexp(N, rate=rt)
> optim(rt, LL, method = “Brent”, lower=0.001, upper=100)$par
~~~
{: .language-r}

~~~
> tot <- 2000
> a <- c()
> for(i in 1:tot) {
>     x <- rexp(N, rate=rt)
>     a[i] <- optim(rt, LL, method = "Brent", lower=0.001,
>                   upper=100)$par
>     if(i % %100==0) {print(i)}
> }
~~~
{: .language-r}

~~~
> hist(a)
~~~
{: .language-r}

### Máxima Verosimilitud: Ajuste de una distribución

Con el comando `fitdistr` de la librería `MASS` es posible estimar los parámetros de una distribución mediante el método de máxima verosimilitud. He aquí algunos ejemplos.

~~~
> x <- rnorm(500, mean=0, sd=1)
> library(MASS)
> fitdistr(x, "normal")
~~~
{: .language-r}

~~~
> x <- rgamma(100, shape=10, scale=0.5)
> fitdistr(x, "gamma")
~~~
{: .language-r}

~~~
> x <- rgeom(100, p=0.1)
> fitdistr(x, "geometric")
~~~
{: .language-r}

> ## `Nota`
> En el último ejemplo, el comando `fitdistr` se ejecutó con el nombre "geometric" y no con el nombre "geom".
> [Consulte la siguiente página.](https://stat.ethz.ch/R-manual/R-devel/library/MASS/html/fitdistr.html)
{: .callout}

## Extracción de información en objetos

Considere nuevamente la tarea del ajuste de una distribución

~~~
> x <- rnorm(500, mean=0, sd=1)
> library(MASS)
> fit <- fitdistr(x, "normal")
~~~
{: .language-r}

El comando `summary(fit)` despliega el contenido en el objeto fit.

|            | Length | Class  | Mode    |
|------------|--------|--------|---------|
| `estimate` | 2      | -none- | numeric |
| `sd`       | 2      | -none- | numeric |
| `vcov`     | 4      | -none- | numeric |
| `n`        | 1      | -none- | numeric |
| `loglik`   | 1      | -none- | numeric |

Mediante `fit$estimate`, o `fit[[1]]`, se obtienen las estimaciones obtenidas.

Mediante `fit$estimate[[1]]`, o `fit[[1]][[1]]`, se obtiene el valor estimado para el primero de los parámetros

## Error Cuadrático Medio (ECM)

Un estimador $ \widehat{\Theta_{1}} $ es mejor que $ \widehat{\Theta_{2}} $ si $ ECM(\widehat{\Theta_{1}}) $ < $ ECM(\widehat{\Theta_{2}}) $ .

Si $ \widehat{\Theta} $ es insesgado, entonces $ ECM(\widehat{\Theta})= var(\widehat{\Theta}) $ .

**Ejemplo.** La población: $ X ∼ $ Uniforme $ (0,\Theta) $ . Los estimadores: $ \widehat{\Theta_{1}}= 2\overline{X} $ y $ \widehat{\Theta_{2}}= \frac{n +1}{n}max(X_{1},...,X_{n}) $ .

Las varianzas de los estimadores:

$ var(\widehat{\Theta_{2}})=\frac{\Theta^{2}}{n(n+2)} $ y $ var(\widehat{\Theta_{1}})=\frac{\Theta^{2}}{3n} $ .

![Forking Repositories]({{ page.root }}/fig/ECM.png)

Ver el archivo `Contraejemplo.r`.
