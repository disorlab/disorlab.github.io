# DisorLAb
Sitio web del laboratorio en Métodos Digitales e Inventivos de Investigación social de la Universidad del Rosario, Colombia.

El sitio web se despliega en disorlab.org.

## Instrucciones

El sitio web usa [Jekyll](https://jekyllrb.com/) que es un generador de sitios web estáticos. Jekyll toma archivos escritos en formato markdown y los convierte en archivos html que pueden ser vistos en un navegador.

La estructura del sitio se puede dividir en dos: elementos que determinan el formato y funcionamiento del sitio y contenidos.

### Formato y funcionamiento del sitio

- `_config.yml`: archivo con la configuración para Jekyll.
- `_includes`: carpeta que contiene los archivos html de los encabezados y los pies de página.
- `_layouts`: carpeta que contiene las plantillas que usa Jekyll para producir las páginas del sitio. Tenemos 5 plantillas:
	- `blog.html`: determina la página del blog.
	- `default.html`: es la base de todas las demás y llama a los encabezados y los pies de página que están en _includes.
	- `home.html`: determina qué hay en home.
	- `page.html`: determina cómo se ve cada entrada o post.
- `_site`: es la carpeta donde Jekyll guarda el sitio resultante (de ahí que lo "estático"). Esta carpeta no se toca.
- `_assets`: esta carpeta contiene el archivo de estilo del sitio (style.css) y las imágenes que se quieran incluir en un post o página.

### Contenidos del sitio
Los contenidos del sitio se dividen en dos: páginas y posts.

- `_pages`: corresponde a todas las páginas que no son posts. Acá se encuentran:
	- `about.md`: acerca del laboratorio.
	- `blog.md`: Jekyll genera la página donde aparecen todos los posts a partir de este archivo. No contiene más que el preámbulo porque su contenido se genera automáticamente según lo que haya en la plantilla o layout `blog.html`.
	- `index.md`: Jekyll genera el home a partir de este archivo. No contiene más que el preámbulo porque su contenido se genera automáticamente según lo que haya en la plantilla `home.html`.
	- `projects.md`: lista de proyectos.
- `_posts`: entradas o posts en el blog.


### Cómo hacer un post

Todos los post se guardan en la carpeta `_posts` para que Jekyll los procese. Hay dos grandes requisitos para escribir un post: (1) el nombre del archivo sigue un formato y (2) debe tener un preámbulo con cierta información.

#### Nombre del archivo
El nombre del archivo debe ser `AAAA-MM-DD-nombre-entre-guiones.md` donde AAAA es año, MM es mes y DD el día. Jekyll usa esta información para producir la fecha del documento o post.

#### Preámbulo e información
Todos los archivos de contenido (los que van en `_pages` y `_posts` tienen un preámbulo que usa Jekyll para generar el sitio. 

El preámbulo se demarca con tres guiones `---` al principio y al final así:

```
---
# Acá va el preámbulo
---
```

El preámbulo de los posts para el sito del laboratorio requiere los siguientes elementos:

1. `layout` le dice a Jekyll qué plantilla usar de las que están en la carpeta `_layouts`.
2. `title` es el título del post y se genera automáticamente. Este título se usa en las listas de entradas que aparecen en el home y en la página `blog`. 
3. `destacado` es el texto que aparece como resumen de la entrada en la página `blog`. No debería superar 140 caracteres con espacios.
4. `autor` es quien aparece acreditado como autor del texto. Todos los anuncios de eventos e invitaciones generales del laboratorio deberían aparecer a nombre de Disorlab.

La plantilla para el preámbulo es:

```
---
layout: post
title:
destacado:
autor: 
---
```

El preámbulo terminado de una de las entradas actuales se ve así:

```
---
layout: post
title: Evento - Pensar con el espacio - mapas para la visualización de datos
destacado: Ciclo de charlas "pensar es cuestión de método". Hablaremos con Javier David Ávila sobre el uso de mapas para la visualización de datos.
autor: Disorlab
--- 
```

#### Agregar imágenes

Para agregar una imagen hay que indicar dónde se encuentra la imagen, un texto que describa bien la imagen y que aparece sólo si no se puede cargar la imagen o en los lectores de accesibilidad y un título de la imagen útil para señalar la fuente o un comentario.

El código para incluir una imagen es el siguiente:

```
<figure>
    <img src="[URL o ruta de la imagen]" alt="[texto descriptivo]">
    <figcaption>[atribución o comentario]</figcaption>
</figure>
```

La imagen puede provenir de una URL en internet o del propio sitio. En el segundo caso, las imágenes tienen que ubicarse en ``assets/images``.


Un ejemplo completo de cómo insertar una imagen se vería así:

```
<figure>
    <img src="/assets/images/who.jpg" alt="Edificio de la OMS">
    <figcaption>Fuente: Wikipedia</figcaption>
</figure>
```

No se incluyen los paréntesis `[]` entre las comillas `"` al reemplazar la fuente de la imagen, el texto descriptivo y la atribución.

#### Agregar videos

Para agregar un video, es necesario usar el siguiente código dentro del archivo markdown:

```
<div class="video">
    <iframe src="[URL DEL VIDEO]" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
```

La dirección va entre las comillas `"` y no incluye los paréntesis `[]`. Un ejemplo de cómo se ve la sección específica donde se agrega el video se vería así:

`<iframe src="https://www.youtube.com/watch?v=2ZFKyurxi28" frameborder ...`

### Tablas

Para agregar una tabla, es necesario usar el siguiente código dentro del archivo markdown:

```
<table>
                <caption>título de la tabla</caption>
                <thead>
                    <tr>
                        <th scope="col">Columna 1</th>
                        <th scope="col">Columna 2</th>
                        <th scope="col">Columna 3</th>
                        <th scope="col">Columna 4</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td data-label="Columna 1">Contenido</td>
                        <td data-label="Columna 2">Contenido</td>
                        <td data-label="Columna 3">Contenido</td>
                        <td data-label="Columna 4">Contenido</td>
                    </tr>
                    <tr>
                        <td scope="row" data-label="Columna 1">Contenido</td>
                        <td data-label="Columna 2">Contenido</td>
                        <td data-label="Columna 3">Contenido</td>
                        <td data-label="Columna 4">Contenido</td>
                    </tr>
                    <!--- Acá se agrega el código de las demás filas según sea necesario ---!>
                </tbody>
            </table>
```


Para agregar una nueva **fila** se repite el siguiente código, cambiando siempre el nombre de la columna por el dato correspondiente:

```
<tr>
 <td scope="row" data-label="Columna 1">Contenido</td>
 <td data-label="Columna 2">Contenido</td>
 <td data-label="Columna 3">Contenido</td>
 <td data-label="Columna 4">Contenido</td>
</tr>
```

### Cómo crear un proyecto

Para crear un proyecto hay que hacer dos cosas: (1) crear la página del proyecto y (2) añadir el proyecto en la lista de proyectos.

#### Crear la página del proyecto

1. Crear una página para un nuevo proyecto se crea un archivo markdown en la carpeta `_pages`. 

2. El nombre del archivo sigue la siguiente convención: `pAA-nombre.md` donde AA son los dos últimos dígitos del año del proyecto. Ejemplos de nombres de proyecto son:

- `p20-abuso-rrss.md`
- `p20-pladts.md`

3. El preámbulo del archivo del proyecto debe tener lo siguiente: `layout:page`
4. El preámbulo lleva el título fijo así: `title:proyecto`.

5. El preámbulo debe indicar dónde se crea la página así: `permalink:/proyectos/pAA-nombre.html`. **Atención:** el nombre del proyecto debe coincidir con el nombre del archivo markdown que se está creando. No debe contener mayúsculas ni caracteres especiales. La extension del archivo que se refiere es `html`. 

Un preámbulo terminado de un proyecto se ve así: 

```
---
layout: page
title: proyecto
permalink: /proyectos/p20-abuso-rrss.html
---
```

6. El contenido del proyecto sigue al preámbulo como se hace con las entradas de blog.

#### Agregar el proyecto en la página de la lista de proyectos

1. Abrir `_pages/projects.md`
2. Agregar el siguiente código:

```
<div class="box" onclick="location.href='[nombre del archivo del proyecto].html';" style="cursor: pointer;">
	<h4>Nombre del proyecto</h4>
	<p>descripción corta del proyecto.</p>
</div>
```

El nombre del archivo del proyecto va sin los paréntesis `[]` y debe corresponder al nombre de archivo que se especificó en el campo `permalink` en el preámbulo de la página del proyecto.