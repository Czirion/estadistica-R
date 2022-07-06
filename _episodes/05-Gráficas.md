---
title: "Gráficas"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

# Gráficas

Especifica las dimensiones de una gráfica

~~~
    > dev.new(width=6, height=5)
~~~
{: .language-r}

Especifica el tamano de los carácteres de la grafica: 

~~~
    > par(cex=1.5)
~~~
{: .language-r}

 Produce la gráfica:
 
~~~
    >x<-1:10
    >y<-x^2
    >plot(x, y)
~~~
{: .language-r}

<img src="https://raw.githubusercontent.com/Czirion/estadistica-R/gh-pages/fig/grafica1.png">

La gráfica anterior se puede imprimir en un archivo pdf mediante las siguientes instrucciones:

~~~
    >pdf("rplot.pdf", width=6, height=5)
    >par(cex=1.5)
    >plot(x, y)
    >dev.off()
~~~
{: .language-r}

Las funciones para graficar en R tienen varios parámetros. El comando `par` sirve para especificar de manera global los parámetros de las gráficas que se realizarán en la sesión. Por ejemplo:

~~~
    >par(cex=1.5) 
~~~
{: .language-r}

Sirve para definir el tamaño de los caracteres de las gráficas. `xlab` y `ylab` sirven para especificar las leyendas de los ejes horizontal y vertical.

~~~
    >plot(x, y, xlab="equis", ylab="cuadrado")
~~~
{: .language-r}

`col` y `bg` cambian el color de la gráfica y el color del fondo de la gráfica.

~~~
    >par(bg="yellow")
    >plot(x, y, col="red")
~~~
{: .language-r}

`pch` para seleccionar el símbolo para los puntos de la gráfica.

~~~
    >plot(x, y, pch=1:10)
~~~
{: .language-r}

`lty` y `lwd` cambian el tipo de línea y el grueso de la línea respectivamente. “lines” sirve para a ̃nadir a la gráfica una curva a trazo continuo.

~~~
    >plot(x, y, lwd=3)
    >lines(x, x ˆ 2, lty=5)
~~~
{: .language-r}

`cex` tamaño del texto y puntos de la gráfica.

~~~
    >plot(x, y, cex=2:3)
~~~
{: .language-r}

`main` es el título de la gráfica.

~~~
    >plot(x, y, main="hola")
~~~
{: .language-r}

`ps` sirve para especificar el tamaño del texto dentro de la gráfica.

~~~
    >par(ps=10, cex=1.5, cex.main=2)
    >plot(x, y, cex=2:3, main=“Cuadrado”)
~~~
{: .language-r}

`fg` especifica el color del marco de la gráfica.

~~~
    >plot(x, y, fg="blue")
~~~
{: .language-r}

`xlim` y `ylim` especifica el rango en el eje de la x y en el eje de las y, respectivamente.

~~~
    >plot(x, y, ylim=c(-10, 110), xlim=c(-1, 12))
~~~
{: .language-r}

`text` sirve para a ̃nadir texto a la gráfica.

~~~
    >text(4, 20, "(4, 16)")
~~~
{: .language-r}

`mtext` añade texto en los márgenes.

~~~
    > mtext("aqui", side=4)
~~~
{: .language-r}

`type` especifica el tipo de gráfica.

~~~
    > plot(x, y, type = "b")
~~~
{: .language-r}

La gráfica puede ser de uno de los tipos que se especifican en la siguiente tabla.

| Letra   | Significado |
| ------- | ----------- |
| `p` | Puntos. |
| `l` | Líneas. |
| `c` | Puntos vacíos con líneas.  |
| `o` | Puntos con líneas sobrepuestas. |
|  `s` o `S`  |  Dos tipos de función escalón. |
| `h` |  Tipo histograma. |
| `n` |  Ni puntos ni líneas. |

### Ejemplos Adicionales
~~~
    > plot(x, y, pch=21, lwd=2, col="red", bg="blue")
~~~
{: .language-r}

~~~
    > plot(x, y, pch=c("a", "b"), col=c("red", "blue"))
~~~
{: .language-r}

~~~
    > par(cex.lab=2, cex.main=2)
~~~
{: .language-r}

Tamaño de las leyendas en los ejes y título
~~~
    > plot(x, y, pch=c("a", "b"), col=c("red", "blue"), +main="cuadrado")
~~~
{: .language-r}

## Generación de Números Aleatorios
Se inicializa el generador de números aleatorios
~~~
    > set.seed(777)
~~~
{: .language-r}

Si el generador de números aleatorios se inicia con un mismo valor cada vez que se corra el comando, entonces la sucesión de números aleatorios permanecerá sin cambiar.
~~~
    > runif(5)
~~~
{: .language-r}

Da como resultado:
~~~
    > [1] 0.6878574 0.4921926 0.3451156 0.9950499 0.6952672
~~~
{: .output}

R maneja distintos tipos de variables aleatorias. En la siguiente tabla se reportan los nombres de algunas de las variables aleatorias de uso común.

|-------------------|-----------------------|-------------------------|
|     Variable      |      Nombre en R      |        Parámetros       |
|-------------------|-----------------------|-------------------------|
|     Binomial      |        `binom`        |        `size`, `prob`   |
|-------------------+-----------------------|-------------------------|
|     Geométrica    |         `geom`        |            `p`          |
|-------------------|-----------------------|-------------------------|
|      Poisson      |         `pois`        |         `lambda`        |
|-------------------|-----------------------|-------------------------|
| Uniforme en (a,b) |          `unif`       |      `min`, `max`       |
|-------------------|-----------------------|-------------------------|
|    Exponencial    |          `exp`        |          `rate`         |
|-------------------|-----------------------|-------------------------|
|      Gama         |        `gamma`        |     `shape`, `scale`    |
|-------------------|-----------------------|-------------------------|
|     Logística     |         `logis`       |   `location`, `scale`   |
|-------------------|-----------------------|-------------------------|
|      Normal       |         `norm`        |      `mean`, `sd`       |
|-------------------|-----------------------|-------------------------|
|     Ji Cuadrada   |         `chisq`       |            `df`         |
|-------------------|-----------------------|-------------------------|
|    T de Student   |         `t`           |            `df`         |
|-------------------|-----------------------|-------------------------|
|         F         |           `f`         |      `df1`, `df2`       |
|-------------------|-----------------------|-------------------------|

Los nombres de las variables aleatorias se usan en conjunto con una raíz que indica la función a ejecutar.

| Nombre   | Significado |
| ------- | ----------- |
| `dnorm` | Función de densidad normal |
| `pnorm` | Función de distribución normal |
| `qnorm` | Cuantiles de la distribución normal  |
| `rnorm` | Números aleatorios normales |

~~~
    > rnorm(5, 1, 0.01)
~~~
{: .language-r}

Da como resultado:
~~~
    [1] 0.9979378 0.9962103 0.9969574 1.0005416 0.9811907
~~~
{: .output}

~~~
    > rbinom(5, size=10, prob=0.5)
~~~
{: .language-r}
 
Da como resultado:
~~~
    [1] 5 5 9 6 7
~~~
{: .output}

La siguiente instrucción sirve para calcular la probabilidad de que una variable aleatoria X ∼ Binomial(10, 5) sea igual a 7.
~~~
    > dbinom(7, size=10, prob=0.5)
~~~
{: .language-r}

~~~
    [1] 0.1171875
~~~
{: .output}

***Nota:*** R reconoce a `dbinom` como a una función de densidad, aún cuando en sentido estricto se trata de una función de distribución de masa.

Con la siguiente instrucción se calcula la probabilidad de que X ∼ Binomial(10, 5) sea menor o igual a 7.
~~~
    > pbinom(7, size=10, prob=0.5)
~~~
{: .language-r}

Da como resultado:
~~~
    [1] 0.9453125
~~~
{: .output}

Para calcular los cuantiles:
~~~
    > qnorm(0.99, mean = 0, sd = 1)
~~~
{: .language-r}

Dando como resultado:
~~~
    [1] 2.326348
~~~
{: .output}

Se puede obtener más información sobre las distribuciones de probabilidad en el contexto de R con las funciones de ayuda:
`?Normal`, `?Binomial`, `?TDist`, `?Chi-squared`, etcétera. Se sale de la página de ayuda con `q`.

## Construcción de un Histograma

El archivo `Histograma.Normal.r` contiene los comandos necesarios para generar la siguiente figura.

<img src="https://raw.githubusercontent.com/Czirion/estadistica-R/gh-pages/fig/Histograma1.png">

En particular, el comando `hist(x)` genera el histograma de los datosn en el vector x.
~~~
   dev.new(width=6, height=5)
   par(cex=1.5)
   y <- rnorm(1500, 0, 10)
   hist(y, breaks=50, col="yellow", freq=FALSE)
   x <- seq(from=-40, to=40, by=1)
   w <- dnorm(x, mean=0, sd=10)
   lines(x, w, lwd=3, col="red")
~~~
{: .language-r}

## Ley de los Grandes Números
En el histograma anterior, el tamaño de la muestra fue de 1500.
Por la ley de los grandes n ́umeros, cuando el tama ̃no de la muestra se incrementa, entonces el histograma tiende a coincidir con más exactitud con la función de densidad de la que se tomó la muestra.
