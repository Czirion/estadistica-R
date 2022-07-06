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

El lenguaje R es sensible a las may ́usculas: no es lo mismo `variable1` que `Variable1`.

Para interrumpir un cálculo extenso, oprimir `Esc`.

Para salir de R:

~~~
    > q() #para salir de R
~~~
{: .language-r}

Asigna el valor "5" a la variable x:

~~~
    > x<-5
~~~
{: .language-r}

Da la lista de las variables, u objetos, definidos por el usuario:

~~~
    > ls()
~~~
{: .language-r}

Elimina la variable x:

~~~
    > rm(“x”) 
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

Define el vector y:

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

Define la matriz de 3x3:

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

Define la matriz u de 3x1
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

Calcula la media de las entradas en el vector y:

~~~
    > mean(y)
~~~
{: .language-r}

En la siguiente tabla se reportan los comandos para calcular otros estadísticos básicos.

|-------------------+--------------------------------------------------------|
|      Comando      |                         Función                        |
|:-----------------:+:------------------------------------------------------:|
|    `length(y)`    |            Número de entradas en el vector y           |
|-------------------+--------------------------------------------------------|
|      `sum(y)`     |                Suma de las entradas de y               |
|-------------------+--------------------------------------------------------|
|      `sort(y)`    |                  Ordena de menor a mayor               |
|-------------------+--------------------------------------------------------|
|  `min(y), max(y)` |            Obtiene el mínimo y el máximo de y          |
|-------------------+--------------------------------------------------------|
|     `mean(y)`     |                     Media del vector y                 |
|-------------------+--------------------------------------------------------|
|    `median(y)`    |                    Mediana del vector y                |
|-------------------+--------------------------------------------------------|
|      `sd(y)`      |             Desviación estándar del vector y           |
|-------------------+--------------------------------------------------------|
|      `var(y)`     |                  Varianza del vector y                 |
|-------------------+--------------------------------------------------------|
|     `cor(x, y)`   |                  Correlación entre x, y                |
|-------------------+--------------------------------------------------------|
|    `cov(x, y)`    |                   Covarianza entre x, y                |
|-------------------+--------------------------------------------------------|

En la siguiente tabla se reportan algunas operaciones matemáticas.

|-------------------+--------------------------|-----------------------------|-----------------------------|
|      Comando      |         Operación        |           Comando           |          Operación          |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|        `+`        |           Suma           |          `trunc(x)`         |      Elimina decimales      |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|        `-`        |           Resta          |     `round(x, digits=0)`    |          Redondea x         |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|        `*`        |      Multiplicación      |     `round(x, digits=3)`    |          Redondea x         |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|        `/`        |          División        |           `log(x)`          |      Logaritmo natural      |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|      `x%%y`       |        x módulo y        |       `log(x, base=2)`      |         log base 2          |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|      `abs(x)`     |      Valor absoluto      |         `log10(x)`          |    Logaritmo base 10 de x   |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|     `sqrt(x)`     |       Raíz cuadrada      |           `exp(x)`          |       Exponencial de x      |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|    `ceiling(x)`   |      Función techo       |           `% * %`           |     Multiplica matrices     |
|-------------------+--------------------------|-----------------------------|-----------------------------|
|     `floor(x)`    |       Función piso       |            `n:m`            |     Genera n, n+1, ..., m   |
|-------------------+--------------------------|-----------------------------|-----------------------------|

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

Si x es un vector, entonces x[i] es la i-ésima entrada de x.  Por ejemplo:

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

### Gráficas

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
    >y<-x ˆ 2
    >plot(x, y)
~~~
{: .language-r}

<img src="https://raw.githubusercontent.com/Czirion/estadistica-R/gh-pages/fig/grafica1.png">

La gráfica anterior se puede imprimir en un archivo pdf mediante las siguientes instrucciones:

~~~
    >pdf(“rplot.pdf ”, width=6, height=5)
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
    >plot(x, y, xlab=“equis”, ylab=“cuadrado”)
~~~
{: .language-r}

`col` y `bg` cambian el color de la gráfica y el color del fondo de la gráfica.

~~~
    >par(bg=“yellow”)
    >plot(x, y, col=“red”)
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
    >plot(x, y, main=“hola”)
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
    >plot(x, y, fg=“blue”)
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
    > > plot(x, y, pch=c("a", "b"), col=c("red", "blue"), +main="cuadrado")
~~~
{: .language-r}
