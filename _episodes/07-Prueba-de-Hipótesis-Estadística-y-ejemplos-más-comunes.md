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

![Forking Repositories]({{ page.root }}/fig/PHipotesis1.png)

Tres personajes son responsables de haber desarrollado el análogo estadístico al falsacionismo de Popper.

Una prueba de hipótesis es forma de verificar una afirmación sobre la distribución de una variable aleatoria $ X $ . Se trata de ver si la información acerca de $ X $ que está contenida en una muestra $ X_{1},...,X_{n} $ , tiende a confirmar la afirmación o más bien la contradice.

Consideremos un ejemplo. Sabemos que $ X \sim Normal(\mu,2) $ , en donde $ \mu\in\{0,2 \} $ . ¿Cómo podemos utilizar la información en una muestra $ X_{1},...,X_{n} $ , para decidir si la afirmación:

$$ H_{0}: \mu = 0 $$

es cierta o no?

Note que si $ H_{0} $ es cierta, entonces $ \overline{X} $ debería estar muy cerca de 0. ¿Qué pasa si observamos que $ \overline{X} = 2 $ ? Por otro lado, ¿es el valor $ \overline{X} = 0.75 $ evidencia suficiente como para afirmar que $ H_{0} $ es falsa?


