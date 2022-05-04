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
- "Escribir buen texto alternativo y pies de figura."
- "Utilizar el código adecuado para insertar cajas."
- "Desarrollar diversos tipos de ejercicios."

keypoints:
- "Los elementos de apoyo sirven como guía para el desarrollo y el uso de los episodios. Deben ser breves y consistentes entre sí."
- "Se debe utilizar `##` para los encabezados de las secciones."
- "Todas las figuras tienen texto que las describa."
- "Existen distintos tipos de cajas para usar según su función."
- "Los ejercicios promueven la evaluación formativa y todos tienen solución."
---

## Elementos de apoyo

Los elementos de apoyo son las preguntas, objetivos y puntos clave incluidos en los episodios.   

Guía para escribirlos:  
  - Intenta escribirlos antes de desarrollar el contenido del episodio para que te sirvan como guía en el desarrollo. Podrás ajustarlos después.
  - Haz que las preguntas, los objetivos y los puntos clave sean consistentes entre sí.
  
  - Las **preguntas** deben ser preguntas que se haría el estudiante.
  
  - Escribe los **objetivos** en términos de lo que el estudiante va a poder *hacer* y no en lo que va a *aprender*.
  - Un episodio debe tener entre 5 y 7 objetivos. Si tienen más considera separarlo en más episodios.

  - En los **puntos clave** has un resumen muy breve de las partes más importantes aprendidas en el episodio.
  - Los puntos clave pueden estar escritos como breves respuestas a las preguntas.
  - Si en el episodio se enseñaron comandos o programas, menciónalos en los puntos clave.

## Formato de los encabezados y del texto

### Formato de los encabezados (El anterior es un encabezado nivel 2 y este es un encabezado nivel 3)

El título de la lección corresponde al mayor nivel de encabezado, el que se especifica con un gato `#`.
No debe haber ningún encabezado de este nivel en los episodios.  
Las secciones se deben delimitar con encabezados de nivel 2, es decir con doble gato `##`.

#### Subsecciones (Este es un encabezado nivel 4)

Y si hay subsecciones se deben poner con el nivel 3 (`###`) y dentro de ellas se puede usar el nivel 4 (`####`).
Es decir, que no debe haber saltos entre niveles de encabezados (p. ej. usar un nivel 4 despues de un nivel 2).  

### Formato del texto

Siempre deja un renglón vacío antes y después de cada encabezado.  
Cada línea de texto debe ser de 100 caracteres máximo. Al terminar los 100 caracteres puedes pasar a una siguiente línea, 
y aún así se va a ver como un párrafo normal.  
Para que se vea un salto de línea debes dejar dos espacios al final de la línea. (La línea final terminó con dos espacios)

## Formato para insertar figuras

Todas las figuras deben de estar dentro de la carpeta `fig/` del repositorio y deben tener su nombre en formato `LL-EE-FF.png`
(Número de lección-Número de episodio-Número de figura dentro del episodio.png).  
Debes utilizar el siguiente código para insertar las figuras en el cuerpo del episodio:  
~~~
<a href="{{ page.root }}/fig/03-07-01.png">
  <img src="{{ page.root }}/fig/03-07-01.png" alt="Aquí va el texto que describe a la imagen." />
</a>
<em> Figure 1. Aquí va el numero de figura y el pie de figura, que no debe de ser el mismo que el texto alternativo. <em/>
~~~
{:language-html}

Si no queda bien el tamaño de la figura se pueden incluir los parámetro `height` y `width` así:  
~~~
<a href="{{ page.root }}/fig/03-07-01.png">
  <img src="{{ page.root }}/fig/03-07-01.png" width="435" height="631" alt="Aquí va el texto que describe a la imagen." />
</a>
<em> Figure 1. Aquí va el numero de figura y el pie de figura, que no debe de ser el mismo que el texto alternativo. <em/>
~~~
{:language-html}

Las personas con discapacidades visuales utilizan lectores de pantalla, éstos son programas que leen en voz alta el contenido de una página. 

{% include links.md %}
