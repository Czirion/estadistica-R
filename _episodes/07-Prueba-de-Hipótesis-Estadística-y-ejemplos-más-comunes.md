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
