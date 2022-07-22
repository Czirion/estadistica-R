---
title: "Análisis de Varianza"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Análisis de Varianza
En 1919, la Estación Rothamsted contrató al joven estadístico Ronals Aylmer Fisher para que aprovecara los datos ahí acumulados. El análisis de Fisher sugería que la relación entre la lluvia y el crecimiento de las plantas era más significativa que la relación entre el fertilizante y el crecimiento de las plantas. A los científicos de la estación de Rothamsted, no les interesaba la lluvia como factor determinante de la cosecha, sino el fertilizante. No se sabía separar los efectos d ela lluvia d elso efectos del fertilizante. Fisher comprendió que los efectos se podían seprar si los experimentos se diseñaban de manera apropiada. 

El análisis de varianza (ANOVA) de un sólo factor se utiliza para comparar las medias I poblaciones. Es de interés la hipótesis

$$ H_{0} : \mu_{1} = \mu_{2} = \cdots = \mu_{I} $$

En el ANOVA se tienen datos de la forma

$$ X_{ij} = \mu_{i} + \epsilon_{ij} $$

en donde \epsilon_{ij} son las desviaciones (o errores) aleatorios que la j-ésima observación respecto de la i-ésima media poblacional \mu_{i}. Se supone que los errores \epsilon_{ij} son independientes con media cero y desviación estándar constante.

Si $ H_{0} $ se cumple, entonces el estadístico de prueba $ F_{cal} = CMTr/CME $ tiene un valor de 1. Valores grandes de $ F_{cal} $ sugieren que $ H_{0} $ es falsa. ¿Qué tan grande debe ser $ F_{cal} $ para poder rechazar a $ H_{0} $?

~~~
> set.seed(777)
> a <- 1.0 + rnorm(10, 0, 0.7)
> b <- 1.5 + rnorm(10, 0, 0.7)
> c <- 2.0 + rnorm(10, 0, 0.7)
> obs <- c(a, b, c)
> A <- rep("A", 10)
> B <- rep("B", 10)
> C <- rep("C", 10)
> fac <- factor(c(A, B, C))
> datos <- data.frame(obs, fac)
> mod <- oneway.test(obs ∼ fac, data=datos, var.equal=TRUE)
> print(mod) # se obtiene como resultado lo siguiente:
~~~
{: .language-r}

~~~
	One-way analysis of means

data:  obs and fac
F = 1.6901, num df = 2, denom df =
27, p-value = 0.2034
~~~
{: .output}

En la figura de la izquierda se reportan los diagramas de caja de las tres poblacionse generadas por el código anterior. Dentro de cada caja yacen las observaciones entre loso cuartiles $ Q_{1} $ y $ Q_{3} $ de cada población. Los "bigotes" se extienden hasta los valores máximo de la serie o hasta $ 1.5 x (Q_{3} - Q{1}) $.

En la figura de la derecha se reportan los intervalos "estudentizados" mediante el procedimiento de Tukey.

En estos diagramas de caja se muestra el consumo de personal de energía eléctrina por bimestre.

tabla

Para la hipótesis nula según la cual no hay diferencias en el consumo, se tiene un p-valor de 0.0126. Por lo tanto se rechaza esta hipótesis. En la figura, los intervalos estudentizados de Tukey. Se observa la mayor diferencia entre los bimestres junio - julio contra febrero - marzo. 

nota

### El ANOVA de un factor como un caso de la regresión

En el archivo `Solo.Variables.Indicadoras` se considera un modelo de regresión de la forma

$$ Y = \beta_{0} + \beta_{1} v + \beta_{2} w + \epsilon $$

en donde $ v $ y $ w $ son variables indicadoras que solamente toman los valores 0 a 1, pero no se da el caso de que $ v = w = 1 $. Note que 

$$
E(Y) = 
     \begin{cases}
       \beta_{0} &\quad\text{si } v = 0 \text{ y } w = 0\\
       \beta_{0} + \beta_{1} &\quad\text{si } v = 1 \text{ y } w = 0\\
       \beta_{0} + \beta_{2} &\quad\text{si } v = 0 \text{ y } w = 1\\
     \end{cases}
$$

Cuando se varían los valores $ \beta_{0} $, $ \beta_{1} $, $ \beta_{2} $ se cambian los niveles del factor.

### ANOVA con dos factores
Un acumulador de energía eléctrica se puede construir de tres tipo distintos de materiales (factor 1 con tres niveles) y trabajará a distintas temperaturas (factor 2). Es de interés el número de horas de servicio del acumulador. El acumulador será probado a tres temperaturas distintas (los tres niveles del factor 2). En la tabla se reportan las horas de servicio obtenidas al aplicar cada tratamiento (combinación de niveles de los factores) a 4 acumuladores elegidos de forma aleatoria

| Temperatura        | 15°                | 70°                | 125°            |
|--------------------|--------------------|--------------------|-----------------|
| Tipo 1 de material | 130, 155,  74, 180 | 34, 40, 80, 75     | 20, 70, 82, 58  |
| Tipo 2 de material | 150, 188, 159, 126 | 136, 122, 106, 115 | 25, 70, 58, 45  |
| Tipo 3 de material | 138, 110, 168, 160 | 174, 120, 150, 139 | 96, 104, 82, 60 |

Con los siguientes comandos se realiza el análisis de varianza con dos factores para el problema planteado anteriormente.

~~~
> vida <- c(130, 74, 150, 159, 138, 168, 155, 180, 188, 126, 110, 160, 34, 80, 135, 106, 174, 150, 40, 75, 122, 115, 120, 139, 20, 82, 25, 58, 96, 82, 70, 58, 70, 45, 104, 60)
> material <- rep(c(1,1,2,2,3,3), 6)
> temp <- rep(c(15, 70, 125), each=12)
> dat <- data.frame(resp=vida, tipo=factor(material), temperatura=factor(temp))
> fit <- aov(resp ∼ tipo∗temperatura, data=dat)
> summary(fit)
~~~
{: .language-r}

~~~
            Df Sum Sq Mean Sq F value   Pr(>F)    
tipo         2  10678    5339   6.269  0.00531 ** 
temp         1  39043   39043  45.841 1.66e-07 ***
tipo:temp    2   2315    1158   1.359  0.27226    
Residuals   30  25551     852                     
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1
~~~
{: .output}

Ver el archivo `ANOVA.Acumulador.r`




