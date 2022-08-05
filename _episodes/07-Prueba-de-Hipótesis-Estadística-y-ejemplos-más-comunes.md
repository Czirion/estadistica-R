---
title: "El concepto de Prueba de Hipótesis Estadística y ejemplos de las pruebas más comunes.En particular las pruebas de bondad de ajuste."
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Prueba de Hipótesis

![Forking Repositories]({{ page.root }}/fig/PHipotesis1.png)

Tres personajes son responsables de haber desarrollado el análogo estadístico al falsacionismo de Popper.

Una prueba de hipótesis es forma de verificar una afirmación sobre la distribución de una variable aleatoria $ X $ . Se trata de ver si la información acerca de $ X $ que está contenida en una muestra $ X_{1},...,X_{n} $ , tiende a confirmar la afirmación o más bien la contradice.

Consideremos un ejemplo. Sabemos que $ X \sim Normal(\mu,2) $ , en donde $ \mu\in\{0,2 \} $ . ¿Cómo podemos utilizar la información en una muestra $ X_{1},...,X_{n} $ , para decidir si la afirmación:

$$ H_{0}: \mu = 0 $$

es cierta o no?

Note que si $ H_{0} $ es cierta, entonces $ \overline{X} $ debería estar muy cerca de 0. ¿Qué pasa si observamos que $ \overline{X} = 2 $ ? Por otro lado, ¿es el valor $ \overline{X} = 0.75 $ evidencia suficiente como para afirmar que $ H_{0} $ es falsa?


Es natural rechazar la hipótesis $ H_{0} $ cuando $ \overline{X} $ sea grande, digamos, mayor que $ q $ . ¿Qué tan grande debe ser $ q $ para que la probabilidad

$$ \alpha=P\{error\;tipo\; I\}= P \{rechazar\; H0 \;|\;H0 \;es \;verdadera\} $$

de equivocarnos cuando rechazamos $ H_{0} $ sea tolerable?

Cuando el tamaño de la muestra es igual a $ n $ , entonces $ \overline{X}\sim Normal(\mu,\frac{2}{\sqrt{n}}) $ . Poniendo $ \alpha = 0.05 $ se obtiene que

$$ 0.05 = P\{ \overline{X}\;\ge \;q\;|\;\mu=0\}= P\{\frac{\overline{X}}{2\sqrt{n}}\;\ge\;\frac{\sqrt{n}}{2}q\;|\;\mu=0\ \} = P\{Z\;\ge\;\frac{\sqrt{n}}{2}q  \} $$

Por lo tanto $ q = \frac{2}{\sqrt{n}}\phi_{0.095}(Z)=\frac{3.28971}{\sqrt{n}}. $

El siguiente código implementa la prueba de hipótesis que se dedujo en la transparencia anterior

~~~
> mu <- 0  #el valor de la media de la población
> n <- 5  #el tamaño de la muestra
> q <- 3.289707/sqrt(n) #ver ejercio anterior
> tot <- 10  #número de veces que se aplica la prueba
> sum <- 0 
> for(i in 1:tot) {
>   x <- rnorm(n, mean=mu, sd=2)
>   x.bar <- mean(x)
>   if(x.bar < q) {sum <- sum+1}
> }
> print(sum/tot) #porcentaje de error tipo I
~~~
{: .language-r}

Córrase este código con distintos valores para la variable `tot`. Ver el archivo `Prueba.de.Hipótesis.r` .

### Prueba de Hipótesis: Tipos de Error

Error tipo I: rechazar $ H_{0} $ cuando $ H_{0} $ correcta.

Error tipo II: no rechazar $ H_{0} $ cuandob$ H_{0} $ incorrecta.

![Forking Repositories]({{ page.root }}/fig/PHipotesis2.png)

## El falsacionismo de Karl Popper

El falsacionismo, o principio de falsabilidad, es una corriente epistemológica fundada por Karl Popper (1902-1994). Para Popper, contrastar una teoría significa
intentar refutarla mediante un contraejemplo. Si no es posible refutarla, dicha teoría queda corroborada, pudiendo ser aceptada provisionalmente, pero no verificada;
es decir, ninguna teoría es absolutamente verdadera, sino a lo sumo se mantiene como ***no refutada***. El falsacionismo es uno de los pilares del método científico.
 
![Forking Repositories]({{ page.root }}/fig/karlpopper.png)
  
### Prueba de hipótesis para la diferencia de medias.

Suponga que tenemos dos poblaciones:

$$  X \sim Normal(\mu_{x},\sigma_{x}^{2}) \; y \; Y \sim Normal(\mu_{y},\sigma_{y}^{2}) $$

Estamos interesados en probar la hipótesis:

$$ H_{0}: \mu_{x}-\mu_{y}=\Delta_{0} \; conta \; H_{1}: \mu_{x}-\mu_{y}\neq \Delta_{0} $$

Sean $ X_{1},...,X_{n_{x}} $ y $ Y_{1},...,Y_{n_{y}} $ muestras de las poblaciones $ X $ y $ Y $ . Es estadístico de prueba es:

$ T_{0}=\frac{\overline{X}-\overline{Y}-\Delta_{0}}{\sqrt[s_{p}]{\frac{1}{n_{x}}+\frac{1}{n_{y}}}} $  en donde  $ s_{p}^{2}= \frac{(n_{x}-1) + (n_{y}-1)s_{y}^{2}}{n_{x}-n_{y}-2} $ y $ s_{x}^{2}= \frac{1}{n_{x}-1}\sum_{i=1}^{n_{x}}(X_{i}-\overline{X})^{2} $  el estimador de la varianza  $ \sigma_{x}^{2} $ .

Es claro que valores de $ \abs{T_{0}} $ pequeños son congruentes con la hipótesis $ H_{0} $ . ¿Qué tan grande debe ser $ \abs{T_{0}} $ para poder rechazar $ H_{0} $ ? Puesto que la distribución del estadístico de prueba es conocida (distribución T de Student) entonces es posible calcular el valor $ q $ tal que $ H_{0} $ se rechaza siempre que $ \abs{T_{0}} \gt  q $ con una probabilidad de error tipo I prefijada.


El comando:

~~~
> t.test(x, y, mu=0.0)
~~~
{: .language-r}

Realiza la prueba de la hipótesis $ H_{0} $ en donde  $ mu = \Delta_{0} $ . Como resultado de ejecutar este comando se obtendrá el así llamado p-valor.

## William Sealy Gosset

William Sealy Gosset (1876-1937) fue un estadístico, mejor conocido por su sobrenombre literario Student. Estudió química y matemática en el New College de Oxford. Tras graduarse en 1899, se incorporó a las destilerías Guinness en Dublín. Guinness era un negocio agroquímico y ahí Gosset pudo aplicar sus conocimientos estadísticos tanto a la destilería como a la granja para seleccionar las mejores variedades de cebada.

![Forking Repositories]({{ page.root }}/fig/WilliamSealyGosset.png)

Gosset introdujo la distribución T de Student para realizar la prueba de diferencia de medias.

$$ T(k)=\frac{Z}{\frac{Ji^{2}(k)}{k}} $$

## El p-valor de una prueba de hipótesis

El p-valor es la probabilidad de que se observe un valor del estadístico de prueba como el que se ha observado al realizar el experimento, bajo el supuesto de que $ H_{0} $ es cierta.

Por lo tanto, p-valores pequeños deben interpretarse como evidencia en contra de $ H_{0} $ .

Como ayuda para asimilar el concepto de p-valor, se puede correr el código en el archivo `Prueba.T.de.Student.r` con distintos para las medias de $ X $ y $ Y $ .

Tamaño de la muestra de $ X $ :

~~~
> nx <- 100
~~~
{: .language-r}

Tamaño de la muestra de $ Y $ :

~~~
> ny <- 50
~~~
{: .language-r}

Desviación estándar común de las dos poblaciones:

~~~
> desviacion <- 1
> x <- rnorm(nx, 0.0, sigma)
> y <- rnorm(ny, 0.5, sigma)
~~~
{: .language-r}

Prueba de la hipótesis $ H_{0}: \mu_{x}= \mu_{y} $ :

~~~
> t.test(x, y, mu=0)
~~~
{: .language-r}

### Aplicación al consumo de energía eléctrica 

En la figura se muestran dos histogramas sobrepuestos. El histograma en color rojo representa el consumo personal diario de energía eléctrica durante los meses de verano, y en verde, en consumo en los meses de invierno. 

![Forking Repositories]({{ page.root }}/fig/PHipotesis3.png)

Se aplicó la prueba T de Student para contrastar la hipótesis nula según cual no existe diferencia en los consumos, y se observó un p-valor igual a 0.02701, con lo cual podemos rechazar esta hipótesis. Ver el archivo `Consumo.Electricidad.r`.

## Prueba para la igualdad de dos varianzas
Sean $ \sigma_{1}^{2} $ y $ \sigma_{2}^{2} $ las varianzas de dos poblaciones normales e independientes. Para probar la hipótesis:

$$ H_{0}:\sigma_{1}^{2}=\sigma_{2}^{2} $$

se usa el comando `var.test` cuyos dos primeros argumentos son dos vectores numéricos que contienen los datos de cada muestra.

~~~
> x <- rnorm(50, mean=0, sd=1)
> y <- rnorm(50, mean=0, sd=2)
> var.test(x, y)
~~~
{: .language-r}

F test to compare two variances data: x and y

$ F = 0.28962 $ , $ num df = 49 $, $ denom df = 49 $ , $ p-value = 2.808e-05 $

alternative hypothesis: true ratio of variances is not equal to 1

> ## `Nota`
> Ver la página siguiente para más detalles de este comando.
> 
> [var.test: F Test to Compare Two Variances.](www.rdocumentation.org/packages/stats/versions/3.5.1/topics/var.test)
{: .callout}

## Prueba de significancia para la correlación

El comando `cor.test(x, y)` nos permite probar la hipótesis nula de que los vectores $ x, y $ no están correlacionados.

Definimos la relaci ́on entre $ x, y $ : 

~~~
> recta <- function(x) 1+5∗x 
> set.seed(415)
> x <- c(1:10)
> y <- recta(x)+rnorm(10, 0, 5)
> cor.test(x, y, method="pearson") #otro método: spearman
~~~
{: .language-r}

Pearson’s product-moment correlation data: x and y

t = 6.0949, df = 8, p-value = 0.0002911

alternative hypothesis: true correlation is not equal to 0

95 percent confidence interval:
0.6469479 0.9780966

sample estimates: 
cor 0.907086

## La prueba de bondad de ajuste de Kolmogorov-Smirnov

Dada una muestra $ X_{1},...,X_{n} $ , tomada de una población $ X $ , nos interesa probar la siguiente hipótesis:

$$ H_{0}: X\;tiene\;una\;distribución\;F(x) $$

El comando `ks.test` nos permite realizar la prueba de bondad de ajuste de Kolmogorov y Smirnov. He aquí algunos ejemplos.

~~~
> y <- rnorm(20, mean=0, sd=5)
> ks.test(y, "pnorm", mean=0, sd=3)
~~~
{: .language-r}

~~~
> y <- rchisq(50, df=5)
> ks.test(y, "pchisq", df=2)
~~~
{: .language-r}

Si el p-valor obtenido es pequeño, entonces no es creíble que la muestra haya sido generada por la distribución $ F(x) $ .

## La transformación Box-Cox

Cuando un conjunto de datos no se distribuye normalmente, entonces es posible transformarlos de manera que los datos transformados sí se distribuyan normalmente. En el lado derecho tenemos una muestra de una población gamma. En el lado derecho tenemos la misma muestra despu ́es de que se aplicó la transformación Box-Cox. Ver el archivo `Box.Cox.r`.

![Forking Repositories]({{ page.root }}/fig/BoxCox.png)

Aquí se puede usar la prueba de Kolmogorov-Smirnov para evaluar el ajuste de los datos transformados a la distribución normal.

## La prueba Ji cuadrada de bondad de ajuste

Suponga que una variable $ X $ tiene una función de distribución de masa de probabilidad (dmp) dada por la siguiente tabla.

| $ j $      | 1         | 2         | 3         | 4         | 5         |
|------------|-----------|-----------|-----------|-----------|-----------|
| $ P{X=j} $ | $ p_{1} $ | $ p_{2} $ | $ p_{3} $ | $ p_{4} $ | $ p_{5} $ |
