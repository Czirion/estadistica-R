---
title: "Regresión Lineal"
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

1. &nbsp;&nbsp;&nbsp; $ \hat{\beta}\_{0} = \bar{y} - \hat{\beta}\_{1} \bar{x} $ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; y &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $\hat{\beta}\_{1} = \frac{S_{xy}}{S_{xx}} $ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; en donde &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ S_{xy} = \sum\limits_{i=1}^{n} (x_{i} - \bar{x}) (y_{i} - \bar{y}) $ <br> <br>
2. &nbsp;&nbsp;&nbsp; $ E(\hat{\beta}\_{0}) = \beta_{0} $ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; y &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ E(\hat{\beta}\_{1}) = \beta_{1} $ <br> <br>
3. &nbsp;&nbsp;&nbsp; $ \textrm{var}(\hat{\beta}\_{1}) = \frac{\sigma^{2}}{S_{xx}} $ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ \textrm{var}(\hat{\beta}\_{0}) = (\frac{1}{n} + \frac{\bar{x}^{2}}{S_{xx}}) \sigma^{2} $ <br> <br>
4. &nbsp;&nbsp;&nbsp; $ \hat{\beta}\_{1} $, &nbsp;&nbsp;&nbsp; $ \bar{Y} $ &nbsp;&nbsp;&nbsp; y &nbsp;&nbsp;&nbsp; $ SCE $ &nbsp;&nbsp;&nbsp; son independientes <br> <br>
5. &nbsp;&nbsp;&nbsp; $ \sum\limits_{i = 1}^{n} (\frac{e_{i}}{\sigma})^{2} \sim Ji^{2}(n-2) $ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; y &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; $ \hat{\sigma}^{2} = \frac{SCE}{n-2} =: $ CME es insesgado 

## Las distribuciones de la teoría estadística

$$ Z = \frac{1}{\sqrt{\textrm{var}(x)}} \sum\limits_{i = 1}^{n} (X_{i} - \mu) $$ &nbsp;&nbsp;&nbsp; (Teorema del límite central)

$$ Ji^{2}(k) = \sum\limits_{i = 1}^{k} Z_{i}^{2} $$ &nbsp;&nbsp;&nbsp; (Suma de cuadrados normales estándar)

$$ T(k) = \frac{Z}{\sqrt{Ji^{2} (k) / k}} $$ &nbsp;&nbsp;&nbsp; (Estandarización usando $\hat{\sigma}$ en lugar de $\sigma$)

$$ F(k, r) = \frac{Ji^{2}(k)/k}{Ji^{2}(r)/r} $$ &nbsp;&nbsp;&nbsp; (Cociente de Ji cuadradas)

## Francis Galton

Francis Galton (1822-1911) fue un polímata, antropólogo, geógrafo, explorador, inventor, meteorólogo, estadístico, psicólogo y eugenista británico. Creó el concepto estadístico de correlación y regresión hacia la media, altamente promovido. El fue el primero en aplicar métodos estadísticos para el estudio de las diferencias humanas y la herencia de la inteligencia, introdujo el uso de cuestionarios y encuestas para recoger datos sobre las comunidades humanas.

## Regresión hacia la media

En estadística, la regresión hacia la media es el fenómeno en el que si una variable es extrema en su primera medición, tenderá a estar más cerca de la media en su segunda medición y, paradójicamente, si es extrema en su segunda medición, tenderá a haber estado más cerca de la media en su primera. 

## Regresión lineal simple

### Diagrama de dispersión

~~~
recta <- function(x) 1 + 5*x  #Defina una función lineal "recta(x)"
set.seed(415)
x <- c(1:10)
y <- recta(x) + rnorm(10, 0, 5)
dev.new(width=6, height=5)
par(cex=1.5)
plot(x, y)  #Para obtener el diagrama de dispresión
~~~
{: .language-r}

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph1.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph1.png" width="400" />

### Recta estimada

~~~
cor(x, y) # calcula la correlación entre x, y
~~~
{: .language-r}

~~~
[1] 0.907086
~~~
{: .output}

~~~
A <- lm(y ∼ x) # asigna a A el modelo estimado y=b+m∗x
print(A) # despliega los coeficientes calculados para el modelo
~~~
{: .language-r}

~~~
Call:
lm(formula = y ~ x)

Coefficients:
(Intercept)            x  
      5.192        4.666 
~~~
{: .output}

~~~
abline(A) # añade la recta de regresión al diagrama de dispersión
~~~
{: .language-r}

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph2.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph2.png" width="400" />


~~~
plot(A, which=1, add.smooth=FALSE) # grafica los residuales
~~~
{: .language-r}

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph3.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph3.png" width="400" />

### Estadísticos del modelo

~~~
summary(A) # para obtener el resumen del modelo
~~~
{: .language-r}

~~~
Call:
lm(formula = y ~ x)

Residuals:
   Min     1Q Median     3Q    Max 
-7.623 -3.364 -1.708  3.693 14.355 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)   5.1919     4.7498   1.093 0.306184    
x             4.6657     0.7655   6.095 0.000291 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 6.953 on 8 degrees of freedom
Multiple R-squared:  0.8228,	Adjusted R-squared:  0.8007 
F-statistic: 37.15 on 1 and 8 DF,  p-value: 0.0002911
~~~
{: .output}

## Coeficiente de determinación $ R^{2} $

El coeficiente de determinación de la regresión está dado por:

$$ R^{2} = \frac{\textrm{suma de cuadrados de la regresión}}{\textrm{suma de cuadrados del error}} = \frac{S_{xy}^{2}}{S_{xx} S_{yy}} $$

El estadístico $R^{2}$ nos dice cuál es el porcentaje de variación de los datos que se explica por el modelo. $R^{2}$ no debe usarse para evaluar el ajuste del modelo a los datos

## Gráfica de los residuales

~~~
set.seed(405)
x <- seq(from=0.1, to=10, by=0.1)
Y <- recta(x)+rnorm(length(x), 0, 5)
A <- lm(Y ∼ x)
modelo <- function(x) -0.3041+5.2817∗x
Y1 <- modelo(x)
qqnorm(Y-Y1, pch="o")
~~~
{: .language-r}

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph4.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph4.png" width="400" />

~~~
qqline(Y-Y1)
~~~
{: .language-r}

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph5.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph5.png" width="400" />

## Estructura de datos

R usa cuatro tipos básicos de estructuras de datos:

1. Un vector puede tener entradas numéricas, de texto o de valores lógicos.
2. Un arreglo (array) es un vector con especificaciones de dimensión. El arreglo más común es la matriz.
3. Un factor es un objeto usado para definir variables categóricas.
4. Un marco de datos (data frame) es una lista de vectores de la misma dimensión. Cada vector en un marco de datos corresponde a una variable de un experimento

~~~
vec2 <- c(1, 2, 3.4, 5.6, 7)
vec3 <- c("tipo A", "tipo B", "tipo C", "tipo D", "tipo E")
vec4 <- c(TRUE, TRUE, FALSE, TRUE, FALSE)
f1 <- factor(vec3) # usa el vector vec3 para hacer el factor f1
datos <- data.frame(vec2, f1, vec4) 
print(datos)
~~~
{: .language-r}

~~~
  vec2     f1  vec4
1  1.0 tipo A  TRUE
2  2.0 tipo B  TRUE
3  3.4 tipo C FALSE
4  5.6 tipo D  TRUE
5  7.0 tipo E FALSE
~~~
{: .output}

Con el comando fix(datos) se pueden hacer modificaciones a este marco de datos

## Regresión Lineal Multiple

~~~
set.seed(777)
f <- function(x, y) 3∗x-5∗y+1
x <- runif(20, 0, 10)
y <- runif(20, 0, 10)
resp <- f(x, y) + rnorm(20, 0, 3)
datos <- data.frame(x, y, resp)
plot(datos, cex=1.5, cex.axis=2) # genera la gr´afica: >lm(datos$resp∼datos$x+datos$y)
~~~
{: .language-r}

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph6.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph6.png" width="500" />

~~~
lm(datos$resp∼datos$x+datos$y)
~~~
{: .language-r}

~~~
Call:
lm(formula = datos$resp ~ datos$x + datos$y)

Coefficients:
(Intercept)      datos$x      datos$y  
     -0.658        3.256       -4.958 
~~~
{: .output}

Ver el archivo `Regresión.Múltiple.r`

### Varios comandos para la regresión lineal

Suponga que se tienen datos de la siguiente forma

$$ y_{i} = \beta_{0} + \beta_{1} u_{i} + \beta_{2} v_{i} + \beta_{3} w_{i} + \epsilon_{i} $$

Con el comando `>fit <- lm(y ∼ u + v + w)` se obtiene el ajuste del modelo. La tabla siguiente contiene comandos para obtener distintas estadísticos de la regresión

|-------------------|--------------------------------------------------------|
|      Comando      |                         Función                        |
|:-----------------:+:------------------------------------------------------:|
|     anova(fit)    |                      Tabla ANOVA                       |
|-------------------|--------------------------------------------------------|
|coefficientes(fit) |                 Coeficientes del modelo                |
|-------------------|--------------------------------------------------------|
|    confint(fit)   |      Intervalos de confianza para los coeficientes     |
|-------------------|--------------------------------------------------------|
|    fitted(fit)    |              valores estimados $ y_{i} $               |
|-------------------|--------------------------------------------------------|
|  residuals(fit)   |                    Los residuales                      |
|-------------------|--------------------------------------------------------|
|    summary(fit)   |       Los principales estadísticos de la regresión     |
|-------------------|--------------------------------------------------------|

Ver el archivo `Regresión.Comandos.Varios.r`

Con el comando `>lm(y ∼ x + 0)` se ajusta el modelo sin término constante $ y_{i} = \beta x_{i} + \epsilon_{i} $

Con el comando `>lm(y ∼ u∗v)` se ajusta el modelo

$$ y_{i} = \beta_{0} + \beta_{1} u_{i} + \beta_{2} v_{i} + \beta_{3} u_{i} v_{i} + \epsilon_{i} $$

Ver el archivo `Regresión.Términos.Cruzados.r`

Con los dos comandos que siguen, es posible seleccionar el mejor conjunto de variables explicativas.

~~~
full.model <- lm(y ∼ u + v + w + z)
reduced.model <- step(full.model, direction="backward")
~~~
{: .language-r}

Ver el archivo `Regresión.Modelo.Reducido.r`

## Análisis de regresión
### Variables indicadoras

Considere el modelo $ y = \beta_{0} + \beta_{1} u+ \beta_{2} v + \epsilon $, en donde la variable $ v $ solamente puede tomar los valores 0 o 1. En la gráfica los valores de $ y $ que se obtienen cuando $ v = 0 $, aparecen en negro y los mismos valores cuando $ v = 1 $, aparecen en rojo. Es interesante la prueba de hipótesis según la cual dos interceptan (cuando $ v = 0 $ y $ v = 1 $) son iguales 

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph7.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph7.png" width="400" />

Ver el archivo `Variables.Indicadores.r`

Con el modelo de la lámina anterior, $ Y = \beta_{0} + \beta_{1} u + \beta_{2} v + \epsilon $ consideramos ahora el ajuste del modelo ampliado

$$ Y = \beta_{0} + \beta_{1} u + \beta_{2} v + \beta_{12} u v + \epsilon $$

Cuando $ v = 0 $, se obtiene que

$$ E(Y) = \beta_{0} + \beta_{1} u $$

Cuando $ v = 1 $, se obtiene que 

$$ E(Y) = \beta_{0} + \beta_{1} u + \beta_{2} + \beta_{12} u = (\beta_{0} + \beta_{2}) + (\beta_{1} + \beta_{12}) u $$

Son interesante las hipótesis nulas $ H_{0} : \beta_{2} = 0 $  y $ H_{0} : \beta_{12} = 0 $

## Regresión polinomial

Cuando queremos ajustar a un conjunto de datos, un modelo de la forma

$$ y = \beta_{0} + \beta_{1} u + \beta_{2} u^{2} + \cdots + \beta_{p} u^{p} + \epsilon $$

se usa el comando `>lm(y ∼ poly(u, p, raw=TRUE))` , en donde $ p $ es el grado del polinomio que queresmo ajustar.

<!-- ![Forking Repositories]({{ page.root }}/fig/regresion_lineal_graph8.png) -->
<img src="https://raw.githubusercontent.com/czirion/estadistica-R/master/fig/regresion_lineal_graph8.png" width="400" />

Ver el archivo `Regresión.Polinomial.r`
