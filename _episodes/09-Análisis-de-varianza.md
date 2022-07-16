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



