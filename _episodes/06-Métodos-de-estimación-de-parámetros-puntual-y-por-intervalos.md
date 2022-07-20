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

