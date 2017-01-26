# HTML, CSS y Markdown

## 1. HTML

## 2. CSS

## 3. Markdown

### 3.1. ¿Qué es Markdown?

[Markdown](http://daringfireball.net/projects/markdown/) es un lenguaje que permite convertir texto en HTML. Gracias a él puedes controlar el formato de texto, crear listas, añadir imágenes usando texto convencional junto con un número reducido de carácteres no alfabéticos como `#` o `*`.

### 3.2. ¿Dónde utilizar Markdown?

Puedes usar Markdown en la mayoría de sitios en GitHub:

* Gists
* READMEs
* Comentarios en Issues y Pull Requests
* Archivos con la extensión `.md` o `.markdown`

### 3.3. Guía rápida

#### Texto

* Negritas: \*\*hola\*\* ó \_\_hola\_\_ se verá como **hola**
* Itálicas: \*hola\* ó \_hola\_ se verá como _hola_
* Links: \[link to GitHub!\](http://github.com) se verá como [link to GitHub!](http://github.com)

#### Citas

\> Esto es una cita.

> Esto es una cita.

#### Encabezados

Los encabezados empiezan con `#`. Cuantos menos añadas más importante en jerarquía.

#### Listas

Las listas sin orden usan `*` para cada elemento:

* Primer elemento
* Segundo elemento

Puedes anidar varias listas:

* Primer elemento de la lista
  * Primer elemento de la sublista
  * Segundo elemento de la sublista
* Segundo elemento de la lista

Las listas ordenadas usan números seguidas de un punto:

1. Primer elemento
2. Segundo elemento

Puedes combinar listas sin orden y ordenadas.

#### Imágenes

Markdown permite añadir imágenes siguiendo la misma sintáxis que links pero con un signo de exclamación delante:

![markdown](https://github.com/GeoinquietosMadrid/webmapping/blob/master/img/markdown.png)

#### Código

Por último puedes añadir líneas de código entre simples comillas `\`\`` o triples comillas `\`\`\`` si es un párrafo. Para especificar el lenguaje de programación, es necesario añadirlo después de las primeras comillas:

Esto es un ejemplo de código en línea `UPDATE`.

```sql
UPDATE
  table_name
SET
  double_field = 2 * field
```


