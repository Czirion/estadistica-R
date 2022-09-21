---
title: "Introducción al lenguaje R"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---


## Comandos básicos

El lenguaje R es sensible a las mayúsculas: no es lo mismo `variable1` que `Variable1`.

Para interrumpir un cálculo extenso, oprimir `Esc`.

Para salir de R:

~~~
  q()
~~~
{: .language-r}

Asigna el valor "5" a la variable $ x $ :

~~~
  x<-5
~~~
{: .language-r}

Da la lista de las variables, u objetos, definidos por el usuario:

~~~
  ls()
~~~
{: .language-r}

Elimina la variable $ x $ :

~~~
    > rm("x") 
~~~
{: .language-r}

Elimina todos los objetos definidos por el usuario:

~~~
    > rm(list=ls())
~~~
{: .language-r}

Muestra el directorio en uso:

~~~
    > getwd()
~~~
{: .language-r}

Cambia el directorio en uso:

~~~
    >setwd("/media/euba/ADATA UFD/Diplomado/Programas")
~~~
{: .language-r}

Muestra los archivos en el directorio en uso:

~~~
    > dir()
~~~
{: .language-r}

Nos da los últimos 10 comandos ejecutados:

~~~
    > history(10)
~~~
{: .language-r}
 
 Guarda la lista de comandos ejecutados en el archivo `borrar.txt`:
 
 ~~~
    > savehistory("borrar.txt") 
~~~
{: .language-r}

Carga el archivo `borrar.txt`:

~~~
    > loadhistory("borrar.txt")
~~~
{: .language-r}

R puede ejecutar un conjunto de instrucciones leyéndolas desde un archivo externo. Por ejemplo, considere el archivo `Sumar.r`  que se muestra a continuación:

~~~
    > #suma
    > a<-1
    > b<-2
    
    > print(a+b)
~~~
{: .language-r}

Para ejecutar el archivo `Sumar.r` se usa el comando:

~~~
    > source("Sumar.r")
~~~
{: .language-r}

## Ambiente de Cálculo

Define el vector $ y $ :

~~~
    > y <-c(1, 2, 3, 4, 5, 6, 7, 8, 9)
    > y 
~~~
{: .language-r}

Y despliega lo siguiente:

~~~
    > [1] 1 2 3 4 5 6 7 8 9
~~~
{: .output}

Define la matriz de $ 3x3 $ :

~~~
    > m <-matrix(y, 3, 3) 
    > m
~~~
{: .language-r}

~~~
    >     [,1]    [,2]    [,3]
      [,1]  1       2       3
      [,2]  4       5       6
      [,3]  7       8       9
~~~
{: .output}

Define la matriz $ u $ de $ 3x1 $
~~~
    > u<-matrix(1, 3, 1)
    > u
~~~
{: .language-r}

~~~
    >   [,1]
     [1,] 1
     [2,] 1
     [3,] 1
~~~
{: .output}

Calcula la media de las entradas en el vector $ y $ :

~~~
    > mean(y)
~~~
{: .language-r}

En la siguiente tabla se reportan los comandos para calcular otros estadísticos básicos.

|-------------------|--------------------------------------------------------|
|      Comando      |                         Función                        |
|-------------------|--------------------------------------------------------|
|    `length(y)`    |           Número de entradas en el vector $ y $        |
|-------------------|--------------------------------------------------------|
|      `sum(y)`     |                Suma de las entradas de $ y $           |
|-------------------|--------------------------------------------------------|
|      `sort(y)`    |                  Ordena de menor a mayor               |
|-------------------|--------------------------------------------------------|
|  `min(y), max(y)` |           Obtiene el mínimo y el máximo de $ y $       |
|-------------------|--------------------------------------------------------|
|     `mean(y)`     |                    Media del vector $ y $              |
|-------------------|--------------------------------------------------------|
|    `median(y)`    |                  Mediana del vector $ y $              |
|-------------------|--------------------------------------------------------|
|      `sd(y)`      |           Desviación estándar del vector  $ y $        |
|-------------------|--------------------------------------------------------|
|      `var(y)`     |                Varianza del vector  $ y $              |
|-------------------|--------------------------------------------------------|
|     `cor(x, y)`   |                Correlación entre $ x, y $              |
|-------------------|--------------------------------------------------------|
|    `cov(x, y)`    |                Covarianza entre  $ x, y $              |
|-------------------|--------------------------------------------------------|

En la siguiente tabla se reportan algunas operaciones matemáticas.

|-------------------|--------------------------|-----------------------------|-----------------------------|
|      Comando      |         Operación        |           Comando           |          Operación          |
|-------------------|--------------------------|-----------------------------|-----------------------------|
|        `+`        |           Suma           |          `trunc(x)`         |      Elimina decimales      |
|-------------------|--------------------------|-----------------------------|-----------------------------|
|        `-`        |           Resta          |     `round(x, digits=0)`    |       Redondea  $ x $       |
|-------------------|--------------------------|-----------------------------|-----------------------------|
|        `*`        |      Multiplicación      |     `round(x, digits=3)`    |       Redondea  $ x $       |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|        `/`        |          División        |           `log(x)`          |      Logaritmo natural      |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|      `x%%y`       |  $  x $ módulo $ y $     |       `log(x, base=2)`      |         log base 2          |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|      `abs(x)`     |      Valor absoluto      |         `log10(x)`          | Logaritmo base 10 de $ x $  |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|     `sqrt(x)`     |       Raíz cuadrada      |           `exp(x)`          |     Exponencial de $ x $    |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|    `ceiling(x)`   |      Función techo       |           `% * %`           |     Multiplica matrices     |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|     `floor(x)`    |       Función piso       |            `n:m`            |  Genera $ n, n+1, ..., m $  |
|-------------------|--------------------------|-----------------------------|-----------------------------|

### Ejemplos

~~~
    > y <- c(1:5)
~~~
{: .language-r}

Sirve para generar el vector:

~~~
    > [1] 1 2 3 4 5
~~~
{: .output}

~~~
    > seq(from=1, to=13, by=3)
~~~
{: .language-r}

Da como resultado:

~~~
    > [1] 1 4 7 10 13
~~~
{: .output}

Si $ x  $ es un vector, entonces $ x[i] $ es la i-ésima entrada de $ x $ .  Por ejemplo:

~~~
    > x <-c(4, 6, 2, 4, 8, 9, 1, 5)
    > x[3]
    [1] 2
    > x[1:3]
~~~
{: .language-r}

Da como resultado:

~~~
    > [1] 4 6 2
~~~
{: .output}

## Gráficas

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

`lty` y `lwd` cambian el tipo de línea y el grueso de la línea respectivamente. `lines` sirve para a ̃nadir a la gráfica una curva a trazo continuo.

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

`xlim` y `ylim` especifica el rango en el eje de la $ x  $ y en el eje de las $ y $ , respectivamente.

~~~
    >plot(x, y, ylim=c(-10, 110), xlim=c(-1, 12))
~~~
{: .language-r}

`text` sirve para añadir texto a la gráfica.

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

La siguiente instrucción sirve para calcular la probabilidad de que una variable aleatoria $ X \sim  Binomial(10, 5) $ sea igual a 7.
~~~
    > dbinom(7, size=10, prob=0.5)
~~~
{: .language-r}

~~~
    [1] 0.1171875
~~~
{: .output}

> ## `Nota`
> R reconoce a `dbinom` como a una función de densidad, aún cuando en sentido estricto se trata de una función de distribución de masa.
{: .callout}

Con la siguiente instrucción se calcula la probabilidad de que X \sim  Binomial(10, 5) sea menor o igual a 7.
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

![Forking Repositories]({{ page.root }}/fig/Histograma1.png)

En particular, el comando `hist(x)` genera el histograma de los datos $ n $ en el vector $ x $ .
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
Por la ley de los grandes números, cuando el tama ̃no de la muestra se incrementa, entonces el histograma tiende a coincidir con más exactitud con la función de densidad de la que se tomó la muestra.

![Forking Repositories]({{ page.root }}/fig/LeyGrandesNum.png)

