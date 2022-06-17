---
title: "Lineamientos para desarrollar episodios"
teaching: 15
exercises: 0
questions:
- "¿Cómo escribo buenas preguntas, objetivos y puntos clave?"
- "¿Qué formato debo usar para los encabezados?"
- "¿Cómo hago que las imágenes sean accesibles para quienes usan lectores de pantalla?"
- "¿Qué formato debo usar para las cajas de código y las cajas especiales?"
- "¿Cómo deben ser los ejercicios?"

objectives:
- "Redactar buenas preguntas, objetivos y puntos clave."
- "Utilizar los encabezados adecuados."
- "Escribir buen texto alternativo."
- "Utilizar el código adecuado para insertar cajas."
- "Desarrollar diversos tipos de ejercicios."

keypoints:
- "Los elementos de apoyo sirven como guía para el desarrollo y el uso de los episodios. Deben ser breves y consistentes entre sí."
- "Se debe utilizar `##` para los encabezados de las secciones."
- "Todas las figuras tienen texto que las describa."
- "Existen distintos tipos de cajas para usar según su función."
- "Los ejercicios promueven la evaluación formativa y todos tienen solución."
---


Estos lineamientos están basados en el [Curriculum Development Handbook](https://carpentries.github.io/curriculum-development/)
y la [Lección ejemplo](https://carpentries.github.io/lesson-example/).

## Planear una lección

Es importante tener claros los **objetivos de la lección antes de empezar**; definir qué habilidades
queremos que los aprendices tengan y qué conceptos queremos que conozcan al completar la lección. A partir
de esto ya puedes desarrollar los ejercicios que pondrán en práctica estas habilidades. Finalmente puedes identificar qué se
necesita enseñar para que los aprendices adquieran estas habilidades y con esto desarrollar el texto y el código de los episodios.  
Dar **conocimiento de más** (que no está en nuestra lista de objetivos) incrementa la carga cognitiva
y resulta distractor, por lo tanto hay que evitarlo.  

> ## Los primeros pasos
>
> - Define las habilidades que se adquirirán con la lección.  
> - Desarrolla ejercicios que pongan en prática y demuestren las habilidades.  
> - Identifica qué necesitas enseñar para lograr los pasos previos.
> - Desarrolla el código de los episodios de acuerdo con lo que identificaste.
> - Desarrolla el texto del episodio cuando ya tengas listo el código.
>
{: .checklist}

## Comenzar un episodio

En la carpeta de episodios haz un nuevo archivo. El formato del nombre debe ser `EE-nombreDelEpisodio.md` (EE: Número del episodio en
formato de dos dígitos.)  
En el cuerpo del archivo copia el siguiente código:
~~~
---
title: "Título del episodio"
teaching: FIXME
exercises: FIXME
questions:
- "FIXME"

objectives:
- "FIXME"

keypoints:
- "FIXME"
---

Aquí va el cuerpo del episodio.

~~~
{: .source}

La última línea del episodio debe decir: `% include links.md %` encerrado en llaves `{}`. (Aquí no se puede poner encerrado en llaves porque se correría el código en lugar de mostrarlo.)

## Elementos de apoyo

Los elementos de apoyo son las preguntas, objetivos y puntos clave incluidos en los episodios.   

> ## Overview
>
> En una caja como esta van los objetivos, las preguntas y el tiempo de enseñanza y ejercicios.
> 
> - Intenta **escribirlos antes** de desarrollar el contenido del episodio para que te sirvan como guía en el 
> desarrollo. Podrás ajustarlos después.
> - Haz que las preguntas, los objetivos y los puntos clave sean **consistentes** entre sí.
> - Las preguntas deben ser **preguntas que se haría el estudiante**.
> - Escribe los objetivos en términos de **lo que el estudiante va a poder *hacer*** y no en lo que va a
> *aprender*.
> - Un episodio debe tener **entre 5 y 7** objetivos. Si tienen más considera separarlo en más episodios.
> 
{: .objectives}

> ## Key points
> 
> En una caja como esta, al final del episodio van los puntos clave.
> - En los puntos clave has un resumen muy breve de las **partes más importantes** aprendidas en el
> episodio.
> - Los puntos clave pueden estar escritos como **breves respuestas** a las preguntas.
> - Si en el episodio se enseñaron **comandos o programas**, menciónalos en los puntos clave.
> 
{: .keypoints}


## Formato de los encabezados y del texto

### Formato de los encabezados (El anterior es un encabezado nivel 2 y este es un encabezado nivel 3)

El título de la lección corresponde al mayor nivel de encabezado, el que se especifica con un gato `#`.
No debe haber ningún encabezado de este nivel en los episodios.  
Las secciones se deben delimitar con encabezados de nivel 2, es decir con doble gato `##`.

#### Subsecciones (Este es un encabezado nivel 4)

Y si hay subsecciones se deben poner con el nivel 3 (`###`) y dentro de ellas se puede usar el nivel 4
(`####`).
Es decir, que no debe haber saltos entre niveles de encabezados (p. ej. usar un nivel 4 despues de un nivel 2).  
Siempre deja un renglón vacío antes y después de cada encabezado.

### Formato del texto

Cada línea de texto debe ser de 100 caracteres máximo. Al terminar los 100 caracteres puedes pasar
a una siguiente línea, 
y aún así se va a ver como un párrafo normal.  
Para que se vea un salto de línea debes dejar dos espacios al final de la línea.

## Formato para insertar figuras

Todas las figuras deben de estar dentro de la carpeta `fig/` del repositorio y deben tener su nombre en formato `LL-EE-FF.png`
(Número de lección-Número de episodio-Número de figura dentro del episodio.png).  
Debes utilizar el siguiente código para insertar las figuras en el cuerpo del episodio:  
~~~
<a href="{{ page.root }}/fig/01-01-01.png">
  <img src="{{ page.root }}/fig/01-01-01.png" alt="Aquí va el texto que describe a la imagen." />
</a>
~~~
{:language-html}

Si no queda bien el tamaño de la figura se pueden incluir los parámetro `height` y `width` así:  
~~~
<a href="{{ page.root }}/fig/01-01-01.png">
  <img src="{{ page.root }}/fig/01-01-01.png" width="435" height="631" alt="Aquí va el texto que describe a la imagen." />
</a>
~~~
{:language-html}

### Accesibilidad de las imágenes

Las personas con discapacidades visuales pueden utilizar lectores de pantalla, éstos son programas que leen en voz alta el
contenido de una página. Para que las imágenes logren su objetivo cuando las utiliza alguien con un lector de pantalla deben
de estar descritas en el texto alternativo. Éste va en el parámetro `alt=` dentro del código con el que se inserta la imagen 
(como se ve en las cajas de código anteriores). 

- Cuando la imagen es **decorativa** el texto alternativo debe de estar vacío de
esta manera:`alt=""`, para que el lector de pantalla no lea nada, ya que en ausencia del parámetro `alt=` se leería el
nombre del archivo, lo cual no es útil. 
- El texto alternativo debe ser **breve** y enfocado al mensaje que se quiere dar con la imagen.
- No debe haber **pies de figura**.

Sigue las recomendaciones de las páginas [Accesible Images Best Practices](https://it.ucsf.edu/how-to/accessible-images-best-practices)
y [Avoid these common alt-text mistakes](https://bighack.org/avoid-these-mistakes-when-writing-alt-text-descriptions-for-images/) para aprender a escribir texto alternativo útil.

Para evaluar la accesibilidad de una página puedes utilizar la herramienta [WAVE](https://wave.webaim.org/).

## Formato de las cajas de código

Para insertar una caja de código usa el siguiente código y modifícalo según el tipo de caja que necesites.

{% raw %}
    ~~~
    Aquí va el código.
    ~~~
    {: .aqui-va-el-tipo-de-caja}
{% endraw %}

Para una caja sencilla utiliza: `{: .source}`  
Para una caja de *Output* utiliza: `{: .output}`  
Para una caja de *Error* utiliza: `{: .error}`  
Para que tenga el formato de sintaxis de algún lenguage de programación y el nombre del lenguage
en la cajita usa el nombre del lenguage así:  
  `{: .language-html}`  
  `{: .language-bash}`  
  `{: .language-make}`  
  `{: .language-matlab}`  
  `{: .language-python}`  
  `{: .language-r}`  
  `{: .language-sql}`  
  
## Formato para las cajas especiales

Existen muchos tipo de cajas para contenido especial. Según el tipo de caja va a tener un color y un símbolo
diferente.

Para insertar una caja todo el contenido debe de tener un símbolo `>` antes de cada línea y el título
debe tener `##`. Debe haber líneas vacías entre la línea del título y el texto, y entre el texto y las 
cajas de código. El tipo de caja se especifica al final. Así:  

~~~
> ## Título de la caja
>
> texto
> texto
> texto
>
> ~~~
> código
> ~~~
> {: .tipo-de-caja-de-codigo}
{: .tipo-de-caja-especial}
~~~
{: .source}  

Los tipos de caja son los siguientes:  

> ## Notas extra o comentarios
>
> El tipo de esta caja es: `{: .callout}`
{: .callout}  
  
> ## Lista de tareas
>
> El tipo de esta caja es: `{: .checklist}`
{: .checklist}  

> ## Discusiones
>
> El tipo de esta caja es: `{: .discussion}`
{: .discussion}   

> ## Puntos clave
>
> El tipo de esta caja es: `{: .keypoints}`
{: .keypoints}  

> ## Objetivos
>
> El tipo de esta caja es: `{: .objectives}`
{: .objectives}  

> ## Prerequisitos
>
> El tipo de esta caja es: `{: .prereq}`
{: .prereq}  

> ## Alguna cita interesante
>
> El tipo de esta caja es: `{: .testimonial}`
{: .testimonial}  

> ## Ejercicio 1: Título del ejercicio
> 
> Los ejercicios deben tener número de ejercicio y título.
> El tipo de esta caja es: `{: .challenge}`
> 
> > ## Solución
> > 
> > Esta es la solución del ejercicio. Todos los ejercicios deben tener solución.
> > ~~~
> > Este es el código de la solución. El tipo de las cajas de solución es `{: .solution}`
> > ~~~
> > {: .source}
> > Para anidar una caja dentro de otra como en este caso el código es así:
> > ~~~
> > > ## Ejercicio 1: Título del ejercicio
> > > 
> > > Este es un ejercicio.
> > > 
> > > ~~~
> > > ls
> > > ~~~
> > > {: .language-bash}
> > > 
> > > > ## Solución
> > > > 
> > > > Esta es la solución.
> > > {: .solution}
> > {: .challenge}
> > ~~~
> > {: .source}
> {: .solution}
{: .challenge}

Así queda la caja de ejercicio hecha con el código que se ve en la solución anterior:

> ## Ejercicio 1: Título del ejercicio
> 
> Este es un ejercicio.
> 
> ~~~
> ls
> ~~~
> {: .language-bash}
> 
> > ## Solución
> > 
> > Esta es la solución.
> {: .solution}
{: .challenge}


## Diseñar ejercicios

Los ejercicios de una lección deben mezclar ejercicios de **aplicación directa** (implementación
de un concepto que se acaba de exponer) y ejercicios de **síntesis** (integración de habilidades
recién adquiridas con habilidades que se vieron previamente en la lección).  
Los ejercicios deben ser una forma de **evaluación formativa**; se deben poner en práctica las habilidades
aprendidas y deben servir para identificar malentendidos.
Es útil empezar por diseñar el ejercicio **final** y más complejo del episodio.  
Idealmente hay un ejercicio por **cada 10 o 15 minutos** de enseñanza. (Una sesión de dos horas necesitaría
~ 6 ejercicios). Planea que el tiempo de enseñanza entre ejercicios sea de 12 minutos y el tiempo de
resolución del ejercicio sea de 8 minutos.

### Tipos de ejercicios

- Preguntas de opción múltiple: Intenta que las opciones incorrectas revelen algún posible problema
de entendimiento.
- Problemas de Parsons: Consiste en pedirle al aprendiz que ordene las líneas de código de tal manera que
resulte un código completo funcional. Una versión difícil es incluir líneas de código que no forman parte de
la solución.
- Problemas de rellenar los vacíos: Consiste en pedir que agreguen las palabras o comandos faltantes a
un enunciado o línea de código, respectivamente. Se puede hacer más fácil agregando un banco de palabras y
más difícil poniendo muchos vacíos que llenar.
- Usar un concepto en otro contexto: Aplicar un concepto en un contexto distinto al que se enseñó puede
requerir que el estudiante haga búsquedas en internet o en los manuales del código. Por ejemplo, se puede
pedir que utilicen diferentes parámetros para modificar una gráfica previamente mostrada.

{% include links.md %}

