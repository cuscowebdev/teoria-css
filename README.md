# TEORÍA CSS
# Clase N° 1 - ¿Qué es CSS?
[W3C](https://www.w3.org/standards/techs/css)

`C`ascade `S`tyle `S`heet `Hojas de estilo en cascada` significa que se leera de arriba para abajo. Osea que si una propiedad se repite el de mas abajo sera el que tiene mas importancia.

* Cuando sabes usar la cascada, es para nosotros una gran ventaja.

* CSS `nace` en 1995.
* Hacia 1998 se lanza `CSS2`.
* Hacia el año 1999 se pone en carrera el primer borrador de `CSS3` - que tiene la característica de separar las funcionalidades en `módulos`. Cada módulo tiene su propia especificación.
* Es ya casi un error llamar a CSS como CSS3 ya que estos estan basados en módulos.
* Lo que estaría bien seria llamrlos por niveles
* Los modulos avanzan por niveles.
  * Level 1 
  * Level 2 
  * Level 3 
  * Level 4 - los selectores
  
# Formas de importar
Existen 3

# Como manejar la cascada

# Sintaxis
[Para aprender la sintaxis](https://apps.workflower.fi/vocabs/css/en)

Todo comienza con un selector, este indica que parte de HTML se vera afectado con nuestros estilos.
```css
/* Comentarios o anotaciones */
tipodeselector {
  propiedad: valor;
}
```
Todo lo anterior se llama bloque de declaracion

# Recomendaciones para dominar CSS
Para un principiante es necesario aprender:
* Selectores
* Especifidad
* Cascada
* Herencia

Pero para un conocimiento más decente es necesario saber
* box-model
* position
* flex-box

Entonces...
# Introducción a Selectores
Los selectores indican, que elementos del HTML van a verse afectados.
* Lo mas básico es usar `selectores de etiquetas`, estos usan la etiqueta HTML de doc. `p`, `main`, `section`, `<etc>`
* Y tambien `selectores descendientes`, que son los selectores separados por un espacio el primero es un `padre` y el segundo un `hijo de cualquier nivel`.

```css
section {
  color: red;
}

section h1 {
  color: green;
}
/* Dentro de h1 hay un span */
section span {
  color: blue;
}
```
`Nota:` Es una recomendacion `nunca utilizar selectores descendientes`. A eso se le llama la `especifidad` que es un dolor de cabeza cuando comienzas con CSS.
```css
/* Asustate cuando veas esto */
body div header h1 span {
  color: green;
}
```
`OjO: Nunca hacer esto... El navegador te lo agradecerá ;)`

# Tipos de datos soportados en CSS
No tanto asi como los lenguajes de programación
Colores
* Palabra clave `red`
* funciones `hsl`
* `rgb()`
* hexadecimal `#fff`

Unidades de Tiempo:
* `Segundos`
* `Milisegundos`

Grados
* `deg` de degrees
* `turn` una vuelta, `2turn` dos vueltas

Calculos de números
* `calc(100% * 100px)`

Unidades
* 10px
* 10em
* 10rem

Números

Strings

# Variables y Herencia
Las variables es un contenedor de un valor - Un espacio en memoria.
Las variables en CSS se ponen iniciando con dos guiones `--`
```css
h1 {
  --color: red;
  background-color: var(--color);
}
```
* Este se basa en un `scope`, y ademas este se hereda a nivel de DOM? Document Object Model(Modelo de Objetos de Documento) Osea se basa en padres e hijos, ademas que se pueden sobreescribir.

# Estilos de Texto
Los más comunes son:
* `color`: Se aplica a los textos
* `font-size`: El tamaño de la fuente
* `font-family`: Familia tipográfica que vamos a utilizar, la forma correcta de poner valor es que siempre este el plan b ejm. `sans-serif: 'Ubuntu', Arial, sans-serif`
* `font-face`: Nos va a permitir usar cualquier tipo de fuente incluso fuentes que nos descarguemos de internet. fuentes que no estan en font google por ejemplo
* `line-height`: Es la altura de la linea(de cada line de texto), interlineado.

# Estilos por defecto del navegador
Internamente los navegadores tienen su propia hoja de estilos, es por eso que el `h1` tiene ese `font-size`, su `margin`, su `grosor de texto`, etc.

* Una de lo mas jodid* en CSS es hacer debugging...
* Consejo: Nunca pongas `0`(CERO) con alguna unidad... este siempre equivaldra a cero. :)
* Recomendacion: Limpiar los estilos por defecto del navegador. Una de las librerias mas utilizadas es `normalize.css`

# Selectores Simples e id
Introducción:

Con los selectores en CSS nosotros le decimos quienes seran afectados por todos los estilos que le demos.

Con esto llega algo importante que se llama `especifidad` y de esto nace algo que NUNCA deberiamo utilizarlo que sería `!important` y si lo usamos dejar alguna nota con los comentarios diciendo el porque hay un `!important`.

Y empezamos...

* `Selectores Simples:` Son aquellos formados por una sola palabra. y podemos clasificarlos de la siguiente manera
  * `Selectores de tipo o de Etiqueta:` Son los que usan un tag de HTML, estos tambien no debemos usarlos salvos en los estilos base(`normalize.css`)
  * `Selectores de id:` Son muy conocidos en CSS, una recomendacion es no usarlos, usan los atributos `id`, el `id` es único y eso es porque no debemos usarlos.
  * `Selectores de clase:` Estos son los que sí deberiamos utilizar, de hecho son los que mas se usan con CSS, nuestras clases deben ser semánticas, que nos digan casi el significado del elemento, para apuntar en css se usa el `.`
```html
<body>
  <style>
    /*Este es un selector de tipo o de tag*/
    li {
      background-color: yellow;
    }
    /*El no usarlos se basa fundamentalmente en el diseño ya que este no se podrá reutilizar para otros elementos...*/
    #item4 {
      background-color: yellow;
    }
    /*Selectores de clases*/
    .menu-item {
      background-color: red;
    }
  </style>
  <ul>
    <li class="menu-item">item1</li>
    <li class="menu-item">item2</li>
    <li class="menu-item">item3</li>
    <li class="menu-item" id="item4">item4</li>
    <li class="lie">item5</li>
  </ul>
</body>
```
## ESPECIFIDAD
Es feita al inicio pero una vez que la empiezas a entender todo fluye y empezamos acelerar en nuestro conocimiento

`Especifidad` viene de especifico, osea que nos dice que elementos son mas especificos entonces aqui vienen los problemas en los estilos, Entonces  cuando hay conflictos estos se solucionan con `especifidad`

* Es un algoritmo de CSS por el cual se resuelven los conflictos de estilos.
  * `selectores de tipo (type)` = 1
  * `selectores de clase (class)` = 10
  * `selectores de id (id)` = 100
  * `selectores de inline (inline)` = 1000
  * `!important` = gana a todos, nunca usar

Entonces de aqui viene la recomendación de no usar `id` para que así no tengamos que calcular sumando la especifidad, Ninguna clase le gana a un id y nos quedara usar una cosa realmente horrible llamada `!important`, pero si nosotros la usamos despues, ya no podremos sobreescribirla porque a `!important` le importa un carajo la especifidad.

# Selectores Compuestos
Se componen por mas de una palabra.
1. El mas conocido por todos es el `descendiente`
`ancestro descentiente { /*estilos*/ }`
2. Selectores `hijos directos`, Se indican con `>` ejm. `li > a { /*estilos*/ }`
3. Selector `hermano siguiente (adyacente)` selecciona al siguiente elemento
4. Selector `hermanos siguietes` Selecciona a `todos` los hermanos siguientes, esto se hace con `~` `h1 ~ p { /*Selectores*/ }`
5. Combinar selectores... ejmp. `h1.first { /*Selectores*/ }`

# Selectores de atributos
* Las clases y los id son atributos pero estos se seleccionan con `.` y `#` respectivamente.

Pero que pasa con el resto de atributos? Como hacemos para seleccionarlos?

* Usan corchetes o tambien llamadas llaves cuadradas `[]` para indicar el atributo.
```css
[title] {}
[href] {}
[title="mititle"] {}
[href="mihref"] {}
a[href="mihref"] {}
[title][href] {}
```

* Comodín `^` significa comienza con
```html
<style>
[title^="Escuela"] {
  background-color: red;
}
[class^="menu-"] {
  background-color: yellow
}
</style>
<body>
  <a href="https://escuela.digital" title="Escuela Digital">Escuela Digital</a>
  <a href="https://facebook.com">Facebook</a>
  <span title="Titulo">Soy un Span</span>
</body>
```

* Comodín `$` que significa `termina en`
```html
<style>
[href$="pdf"] {
  display: block;
  background: url(http://fresnostate.edu/webresources/images/128x128/128x128-pdf.png) left / contain;
  padding-left: 1.5em;
}
</style>
<body>
  <a href="/files/manual/2017.pdf">Descargar manual</a>
</body>
```
* Comodín `*` `Contiene` `[href*='nua'] {}`
```html
  <style>
    [href$="pdf"] {
      display: block;
      background: url(http://fresnostate.edu/webresources/images/128x128/128x128-pdf.png) left / contain no-repeat;
      padding-left: 1.5em;
    }
    [href*='nua'] {
      color: green;
    }
  </style>
</head>

<body>
  <a href="/files/manual/2017.pdf">Descargar manual</a>
</body>
```
* En CSS nivel 4 tenemos lo siguiente
* `[href*='nua' i] {}` esto es propio de CSS level 4, si ponemos una `i` le decimos a CSS le decimos a CSS que sea `caseInsensitive`
```html
  <style>
    [href$="pdf"] {
      display: block;
      background: url(http://fresnostate.edu/webresources/images/128x128/128x128-pdf.png) left / contain no-repeat;
      padding-left: 1.5em;
    }
    [href*='nua' i] {
      color: green;
    }
  </style>
</head>

<body>
  <a href="/files/maNual/2017.pdf">Descargar manual</a>
</body>
```

# PSEUDO CLASES ;)
* Existen muchas, pero haremos el intento
* Las pseudo-clases son selectores dinámicos, pueden actualizarse en el moment, que responden al texto a la interaccion del usuario o a algunas propiedades de los elementos. Son selectores muy poderosos.
* Las psudoclases se indican con dos puntos `:`
* Las psudoclases no necesariamente estan atadas a un elemento

## PseudoClases para los enlaces-hipervínculos
* `:hover` es cuando ponemos el cursor encima del elemento al que le apliquemos la pseudo clase
* `:active` Es la fraccion de segundos cuando pulsamos con el cursor el elemento.
* `:visited` Es una pseudoclase que nos indica que el hipervinculo ya ha sido visitado, a nivel de diseño ya no es recomendable en estos tiempos antes si porque los navegadores eran pobres.
* `body :hover` Podemos diseñar esto, decimos que todos los descendientes de body tendran el `:hover` que configuremos
```js
  <style>
    html {
      font-family: sans-serif;
    }
    a {
      display: inline-block;
      background-color: red;
      color: white;
      line-height: 2.5;
      padding: 0 1em;
      text-decoration: none
    }
    a:hover {
      background-color: darkred;
    }
    a:active {
      transform: scale(0.9)
    }
    a:visited {
      
    }
  </style>
</head>

<body>
  <a href="#">EDTeam</a>
</body>
```
* `:target` Indica que un elemento que ha sido alcanzado a traves de un marcador
```html
  <style>
    html {
      font-family: sans-serif;
    }
    nav {
      background-color: #222;
      position: fixed;
      width: 100%;
      height: 50px;
      top: 0;
      left: 0;
    }
    nav a {
      color: #fff;
      display: block;
      text-align: center;
      line-height: 50px;
      text-decoration: none;
    }
    #parrafo {
      margin-top: 50em;
      margin-bottom: 50em;
    }
    #parrafo:target {
      padding-top: 100px;
      background-color: red;
    }
  </style>
</head>

<body>
  <nav>
    <a href="#parrafo">EDTeam</a>
  </nav>
  <div id="parrafo">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dolorum tempora quia, explicabo iste dolor aspernatur nulla rem, illum sint ipsam libero ex quis tenetur ab non provident animi maxime accusantium repellat soluta. Ducimus doloremque facere ut, ratione delectus id eum maiores, laudantium similique dolorum ea cumque possimus excepturi consequuntur voluptatum doloribus illo facilis esse ad nostrum voluptates odit. Adipisci, asperiores dolorum deserunt vitae obcaecati mollitia, magni suscipit nemo, unde excepturi minus ad qui eaque. At vero optio accusantium nulla nostrum delectus ratione corporis aliquam sint numquam. Beatae rerum magnam officiis deleniti, recusandae dolores eaque perferendis accusamus assumenda, ea tenetur quidem?
  </div>
</body>
```
Nota: `:target` sin duda nos ayuda a simular JS sin JS Recomendado aprender

* `:root` Hay una pseudoclase que practicamente nunca la vamos a usar pero es bueno que lo sepas.., `:root` es la raíz de todo, este hace referencia a `<html>`
```css
:root {
  background-color: red;
}
```
* `:empty` es una pseudoclase que me indica un elemento vacío, selecciona un elemento vacío
```html
<style>
    html {
      font-family: sans-serif;
    }
    p {
      background-color: yellow;
      padding: .5rem;
    }
    p:empty {
      background-color: red;
      display: none;
    }
  </style>
</head>

<body>
  <p>Hola Mundo</p>
  <p></p>
  <p>Hola Mundo Otra Vez</p>
</body>
```
* `:not(selector)` Esta psudoclase realmente es una funcion que recibe un parámetro, lo que hace esto, selecciona un elemento que no cumpla lo que le estamos diciendo, es básicamente una negación., podemos pasarle cualquier selectoro pseudoclase menos otro `:not`

## PseudoClases de Formularios
En este hay un monton

* `:focus` es para cuando un elemetp ha sido enfocado con el cursor o con el tab
* `:enabled` Elementos activados
* `:disabled` Elementos desactivados
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    input:focus {
      background-color: yellow;
    }
    input:disabled {
      background-color: gray;
    }
    input:enabled {
      background-color: green;
    }
  </style>
</head>

<body>
  <form action="">
    <input type="text">
    <input type="text" disabled>
  </form>
</body>

</html>
```
* `:checked` Es para indicar o seleccionar un elemento que ha sido seleccionado, `input:radio`, `input:checkbox`, `select`
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    .elegir:checked + label {
      font-size: 2em;
      background-color: yellow;
      color: red;
    }
  </style>
</head>

<body>
  <form action="">
    <input type="radio" id="elegir" class="elegir">
    <label for="elegir">Opción elegida</label>
  </form>
</body>

</html>
```
* `:required :optional` required es cuando un elemento es obligatorio, y optional no.
* `:valid` `:invalid` cuando el elemento es valido o invalido
* `:in-range` `:out-of-range` cuando esta `dentro del rango` y cuando esta `fuera del rango`
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
/*
    input:optional {
      border: 1px solid green;
    }
*/
    form :optional {
      border: 1px solid green;
    }
/*
    input:required {
      border: 1px solid red
    }
*/
    form :required {
      border: 1px solid red
    }
    input:valid {
      background-color: yellow;
    }
    input:invalid {
      background-color: red;
    }
    input:in-range {
      background-color: fuchsia;
    }
    input:out-of-range {
      background-color: red;
    }
  </style>
</head>

<body>
  <form action="">
    <input type="text">
    <input type="text" required>
    <input type="email">
    <input type="number" max="10">
  </form>
</body>

</html>
```
## PseudoClases Child
Nos ayudan a encontrar `childs (hijos)` específicos dentro de un elemento
* `:first-child` Para encontrar solo el primer elemento
* `:last-child` Para encontrar solo el último elemento
* `:nth-child(param)` param puede tomar valores como `numero natural`, `even (par)`, `odd (impar)` o una `ecuación`
  * con ecuaciones:
    * `3n`: Me toma de 3 en 3, multiplos de n
    * `4n`: Mùltiplos de 4
    * `3n + 1`: (Multiplos de 3) + 1
    * `3n - 1`: (Multiplos de 3) - 1
    * `n + 5`: Nos selecciona a partir del 5
* `nth-last-child()` Es idèntico al anterior solo que empieza desde el final.
* `:only-child` Se le aplica siempre en cuando sea un `ùnico hijo`
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    p:first-child {
      color: red;
    }
    p:last-child {
      color: green;
    }
    p:nth-child() {
      background-color: blue;
      color: white;
    }
    p:only-child {
      background-color: darkorange;
    }
    span:only-child {
      background-color: darkcyan;
    }
  </style>
</head>

<body>
  <div>
    <p>Párrafo 1</p>
    <p>Párrafo 2</p>
    <p>Párrafo 3</p>
    <p>Párrafo 4</p>
    <p>Párrafo 5</p>
    <p>Párrafo 6</p>
    <p>Párrafo 7</p>
    <p>Párrafo 8</p>
    <p>Párrafo 9</p>
    <p>Párrafo 10</p>
  </div>
  <div>
    <span>Hola CSS!!</span>
  </div>
</body>

</html>
```
Pero aquí ay una trampa... Y te la presentamos
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    p:nth-child(3) {
      background-color: yellow;
    }
  </style>
</head>

<body>
  <div>
    <div>Párrafo 1</div>
    <div>Párrafo 2</div>
    <p>Párrafo 3</p> <!--Este sera el elemento que tendrá el bgc yellow-->
    <p>Párrafo 4</p>
    <p>Párrafo 5</p>
    <p>Párrafo 6</p>
    <p>Párrafo 7</p>
    <p>Párrafo 8</p>
    <p>Párrafo 9</p>
    <p>Párrafo 10</p>
  </div>
</body>

</html>
```
¿Si pongo a pintar el tercer `<p>` porque se pinta ese si los dos anteriores son div?
* Porque el es `3er hijo <p>`

¿Y entonces si yo realmente quiero al Párrafo 5 que es lo que tengo que hacer?
* Pues para eso tenemos las...

## Pseudoclases Type
Estas son igualitas a `:nth-child` con la diferencia de que ahora si te buscan basandose en el tipo de etiqueta.
PseudoClases Child | Pseudoclases type
------------------ | -----------------
`:first-child` | `:first-of-type`
`:last-child` | `:last-of-type`
`:nth-child` | `:nth-of-type`
`:nth-last-child` | `:nth-last-of-type`

## Recomendaciones
* Lee el sitio web donde nos aparecen todos los selectores
  * [W3C Editor's Draft](https://drafts.csswg.org/selectors-4/#overview)
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    p:nth-child(3) {
      background-color: yellow;
    }
    p:nth-of-type(3) {
      background-color: green;
    }
    .parrafo:nth-of-type(7) {
      background-color: darkblue;
    }
  </style>
</head>

<body>
  <div>
    <div>Párrafo 1</div>
    <div>Párrafo 2</div>
    <p class="parrafo">Párrafo 3</p>
    <p class="parrafo">Párrafo 4</p>
    <p class="parrafo">Párrafo 5</p>
    <p class="parrafo">Párrafo 6</p>
    <p class="parrafo">Párrafo 7</p>
    <p class="parrafo">Párrafo 8</p>
    <p class="parrafo">Párrafo 9</p>
    <p class="parrafo">Párrafo 10</p>
  </div>
</body>

</html>
```
# Box Model
Box model es `como se dibuja en la web`, en español significa `modelo de caja`, es muy importante porque cuando tu entiendes esto, entiendes completamente porque las cajas son asi, porque se desmaqueta, etc. Entendiendo el Box Model aprenderemos eso.

Sin embargo aprenderemos algo antes...

# Selectores agrupados
Sucede que nosotros queremos aplicarle los mismos estilos a varios elementos, entonces simplemente lo que hacemos es agrupar sus selectores con comas.
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    .titulo,
    .parrafo {
      text-decoration: underline;
    }
    .titulo {
      color: red;
      
    }
    .parrafo {
      color: blue;
    }
  </style>
</head>

<body>
  <h1 class="titulo">Hola Mundo</h1>
  <p class="parrafo">Bienvenidos a mi web</p>
</body>

</html>
```
# Selectores con Scope
Es el alcance de ciertas funciones. Por ejemplo si ponemos los siguiente se aplicara a todos los parrafos de forma global...
```css
p,
.red {
  color: red;
}
```
* Solo lo esta soportando Firefox
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
  </style>
</head>

<body>
  <article>
    <!--scoped nos permite que solo en este article se aplique estos estilos-->
    <!--Aún no lo soportan los navegadores(solo `firefox`) pero es siempre importante saberlo-->
    <style scoped>
      h2 {
        color: red;
      }
      
      p {
        color: blue;
      }
      
       :scope {
        background-color: yellow;
      }
    </style>
    <h2>Titulo del Artículo1</h2>
    <p>Yosoy el contenido del ariculo1</p>
  </article>
  <article>
    <h2>Titulo del Artículo2</h2>
    <p>Yosoy el contenido del ariculo2</p>
  </article>
</body>

</html>
```
Y continuamos con el `BoxModel`

# Box Model o Modelo de caja
Es el `algoritmo` que usa el navegador para saber como dibujar una caja en el navegador, tener en cuenta algo muy básico: No existen elementos triangulares, poligonales, `todos los elementos en HTML son cuadriláteros`.
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
  </style>
</head>

<body>
  <h1>Hola Mundo</h1>
  <a href="#">Hola 1</a>
  <a href="#">Hola 2</a>
  <!--
  Cuando analizamos al h1 y a la etiqueta a nos vamos a las propiedades computadas y vemos que en el h1 nos da una medida del tamaño de caja, pero cuando analizamos la etiqueta `a` nos da una medida de `auto x auto` que significa eso?
    Esta es la diferencia entre los elementos de linea y los elementos de bloque, los elementos de bloque se dibujan de lado a lado de la pantalla, no importa que su contenido ocupe o no todo ese espacio, viewport significa todo es elpacio disponible en nuestra pantalla de navegador, Un elemento de bloque ocupa todo el ancho del viewport, mientras que los elementos de linea solo ocupan un espacio segun su contenido por eso es que en su medida nos aparece `auto`.
    Algo muy importante de saber es que los elementos inline no tienen `height`, ni `width`, por eso es que nos da `auto x auto`
    Para solucionar esto, y que tengan la propiedad de height podemos decirle mediante CSS que tenga `display: block;` para que asi se comporte como elemento de bloque, pero si queremos que siga teniendo el comportamiento de `inline`, podemos decirle que tenga `display: inline-block;`
  -->
</body>

</html>
```
# Margin, Padding y colapsado de márgenes
Vamos a ver ahora cuales son los elementos en el modelo de caja, tenemos:
* Elementos Internos
  * `contenido:` Es todo lo que este dentro del elemento
  * `padding:` Es la distancia que hay entre el contenido y el final de la caja
  * `border:` Es el trazo que puede dibujarse alrededor de la caja
* Elementos Externos
  * `margin` Es la distancia que hay entre la caja y las cajas externas(vecinas)
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    
    .elemento {
      background-color: yellow;
      padding: 30px;
      display: inline-block;
      margin: 20px;
    }
  </style>
</head>

<body>
  <main>
    <article class="elemento">Hola Mundo</article>
    <article class="elemento">Hola Mundo 2</article>
  </main>
</body>

</html>
```
Sin embargo hay algo llamado
# Colapsado de márgenes
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    
    .elemento {
      background-color: yellow;
      padding: 30px;
      margin-bottom: 100px;
      /*Podemos observar que los margenes verticales no se suman y es otro dolor de cabeza para principiantes*/
      /*El margen que tomara sera el mayor*/
    }
    .elemento:nth-of-type(2) {
      margin-top: 100px;
    }
  </style>
</head>

<body>
  <main>
    <article class="elemento">Hola Mundo</article>
    <article class="elemento">Hola Mundo 2</article>
  </main>
</body>

</html>
```
Y tambien tenemos otro problema...
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    html {
      font-family: sans-serif;
    }
    h1 {
      margin: 0;
    }
    article {
      background-color: red;
    }
    body {
      background-color: yellow;
    }
  </style>
</head>

<body>
  <article>
    <h1>Hola Mundo</h1>
  </article>
</body>

</html>
```
* Este es un ejemplo claro del colapsado de márgenes...
  * Porque el artcle toma el margin de h1 ??
    * Pues porque el margin en lo vertical no se suma, y como el article tiene 0 de margin es el margin mayor el que se toma, y por esa razón es que el margin se colapsa y se toma el margin del h1 que lo separa del body y no del article como deberia de ser.

# Dimensiones de las cajas y Box-sizing
Sin dimensiones declaradas
* alto: contenido + padding + border
* ancho: contenido + paddin + border

Con dimensiones declaradas
* alto: heiht + padding + border
* ancho: width + paddin + border

Antes teniamos que estar midiendo a cada rato con nuestra calculadora para sacar una medida correcta...

Pero ahora hay un concepto que se llama `box-sizing (tamaño de la caja)`
Esto nos ayuda a trabajar de una manera mucho mas fácil

# Border
El border es el trazo que rodea a la caja
* `border: 2px solid red;` Esto es a lo que llamamos en CSS un `shorthand`
* `border: 2px solid` Toma el color de la letra que se usa en la caja.
* `border-style: solid dotted`
* `border-color: 10px 5px 50px 3px`
* `border-width: red green blue yellow`
* `border-left-color: black`
* `border-left-width: black`
* `border-left-style: black`

Como observamos existen muchas formas y combinaciones pero no son tan complicadas

# border-radius
Sirve para redondear los bordes de las cajas.
* `border-radius: 50%` Este es un shorthand
* `border-radius: 10px`
* `border-top-left-radius: 10px`
* `border-top-right-radius: 10px`
* `border-top-left-radius: 10px 50px` Forma una elipse, radio mayor y radio menor
* `border-radius: 200px 100px / 50px` Tmbien tenemos esto, y es que todos los que estan al lado izquierdo del slash son para el eje x y los del lado izquierdo son para el eje y

# Background
* `bacground-color`: color de fondo
* `bacground-image`: color de fondo
* `background: url() yellow`
* `background-repeat: no-repeat` 
* `background-position: center` 
* `background-position: bottom right` 

Podemos poner mas de dos `background-image` siempre en cuando los separemos por comas `,`
* `background: url(), url(), yellow` El color siempre tiene que ir al final

Y para editar las demas propiedades especificando cada background usamos igual la coma respetando el lugar en el que declaramos los `background`

* `background-repeat: no-repeat`
* `background-position: bottom right, top left`
* `background-size: 70%, 10%`

* Entonces cada imagen que nosotros importemos estas se manejan como capas, como si estariamos trabajando con phtoshop.

* `background-clip:` Me va a decir que parte del background se va a mostrar
* `background-origin:` Nos va a decir desde donde se va a empezar a poner el background mientras que `background-origin` nos va a decir en que parte se va a mostrar

# Pseudoelementos `after` y `before`
Los pseudoelementos son elementos que realmente no existen, se pueden crear para dibujar, añadir estilos, añadir efectos y por eso son muy importantes

* `:before`
* `:after`

* Estos elementos no existen, y podemos `crear contenido` desde ahi con la propiedad `content`.
* Siempre tengo que pasarle un `content` aunque sea `vacio`
* podemos crear una imagen con `content: url(mi-image.com)`
* Podemos imprimir el attribute `content: attr(id)`

* Ojo estos son `pseudoelementos` y no `psudoclases` por lo que, tenemos que pasarle siempre al costado un `elemento`.
* Este nos sirve para varios efectos y varios trucos ;)
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    *,
    *:before,
    *:after {
      box-sizing: border-box;
    }
    [href$='pdf']:after {
      content: url(data:image/jpeg;);
      display: inline-block
    }
    .download {
      display: block;
    }
  </style>
</head>

<body>
  <a href="blabla.pdf" class="download">Descargar Manual</a>
  <a href="blabla.txt" class="download">Descargar txt</a>
</body>

</html>
```

# FLOATS & OVERFLOWS
## Float
`float` fuen una propiedad que se uso por mucho tiempo para la maquetación web, sin embargo no habia flex, pero con la llegada de este hubo gente que dijo que nunca deberiamos usarla, y eso es totalmente mentira, no debemos usar `float` para layout porque con flex es mucho más fácil. Pero la podemos usar en casos específicos.

`float` es una propiedad que permite a un elemento salirse del flujo haciendo que este flote.
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    *,
    *:before,
    *:after {
      box-sizing: border-box;
    }
    
    article {
      width: 80%;
      margin: 1em auto;
    }
    
    p {
      text-align: justify;
    }
    
    .img {
      padding: 0 0 .5em .5em;
      float: right;
    }
  </style>
</head>

<body>
  <article>
    <h1>Mi Mascota</h1>
    <img src="/img/perro.jpg" alt="Perro feliz" class="img">
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Dicta architecto accusantium itaque vero laboriosam numquam, provident officia quo nulla explicabo enim, voluptatem asperiores molestias recusandae cupiditate, distinctio quos voluptate optio odit facilis maiores. Libero dicta eligendi, provident esse odio, expedita. Accusamus vel ad tempora inventore, dolorem iusto porro odit qui neque fuga perspiciatis, recusandae consequuntur impedit maiores totam quisquam harum facilis culpa ab necessitatibus rem! Ea molestiae nisi nostrum dolor qui expedita aut praesentium earum eos fugiat ducimus alias in molestias culpa hic, rerum deleniti, dolorem, accusantium quisquam nulla placeat voluptatibus quia et. Ullam laborum eligendi rem sed similique nam.</p>
  </article>
</body>

</html>
```

* Tener muy en cuenta de que si el parrafo es mas pequeño esto nos podria traer problemas pero lo solucionamos con `overflow: hidden`
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    *,
    *:before,
    *:after {
      box-sizing: border-box;
    }
    
    article {
      width: 80%;
      margin: 1em auto;
      overflow: hidden;/*Borrar y quitar para ver lo que soluciona*/
    }
    
    p {
      text-align: justify;
    }
    
    .img {
      padding: 0 0 .5em .5em;
      float: right;
    }
  </style>
</head>

<body>
  <article>
    <h1>Mi Mascota</h1>
    <img src="/img/perro.jpg" alt="Perro feliz" class="img">
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. </p>
  </article>
  <h2>Noticias de animales</h2>
</body>

</html>
```
## Overflow
* `overflow: hidden | scroll | auto`
* `overflow: auto`: Para añadir un scroll si es que lo necesita
* `overflow: scroll`: Para añadir un scroll siempre y se ve muy feo
* `overflow-x: scroll`: Para añadir un scroll siempre y se ve muy feo
* `overflow-y: scroll`: Para añadir un scroll siempre y se ve muy feo

# Y por fin!! Position!!!! :/ :)
Este tema es muy imcomprendido pero si lo entendemos podremos hacer cualquier diseño... ;)

Hoy dia veremos en la clase `position`, y es que atraves de esta propiedad podremos sobreescribir el flujo y podremos ponerlo en donde queramos, y podremos manejar las interfaces. Este tema es muy importante

`position !!`

Para esto comenzaremos entendiendo lo que es:
## Flujo (flow)
Es como los elementos van apareciendo en la pantalla, osea el primer elemento que aparece en el HTML ese sera el primer elemento que aparezca

## que es un elemento posicionado segun la especificación?
Es aquel elemento que ha salido de su flujo a traves de la propiedad position

`position: static | relative | absolute | fixed | sticky(es experimental)`

* Debemos tener presente que `| relative | absolute | fixed |` son posicionados, los que tengan position `static` NO. pero nos preguntamos porque si este tiene la propiedad position, lo que sucede es que este valor es por defecto y no se cuenta.
* `Cuando un elemento esta posicionado se sale del flujo`

* Tener algo muuuuy en cuenta....
  * Cuando nosotros posicionamos un elemento, este adquiere nuevas propiedades. Estas son 5(4 propiedades de offset):
    * `top` movimiento hacia arriba o hacia abajo (10 -10),  Indican el lugar desde el cual se empieza a contar. arriba hacia abajo
    * `right` movimiento derecha Indican el lugar desde el cual se empieza a contar. de derecha a izquierda
    * `bottom` movimiento abajo Indican el lugar desde el cual se empieza a contar. de abajo hacia arriba
    * `left` movimiento izquierda Indican el lugar desde el cual se empieza a contar. de izquierda a derecha
    * `z-index` es el apilamiento de las capas, eje z-index, '`Al usar HTML creamos capas`' en ahi ayuda esta propiedad para ver las capas en este.
  * Estas propiedades se le agregan a cualquier elemento posicionado, si las usamos en cualquier otro elemento que no este posicionado no tendrán ningun efecto.

# Position: relative
1. El elemento conserva su espacio en el flujo, por eso es que no se ve ningun cambio al inicio
2. Conserva sus dimensiones originales
3. Su contexto es su posición inicial
  * `¿Que es contexto?` Es un rectangulo imaginario, es un rectando desde el cual se calcula el movimiento si le damos `top`, `bottom`, `left`, `right`, eso lo define el contexto y este varia segun cada elemento.
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    *,
    *:before,
    *:after {
      box-sizing: border-box;
    }
    
    /*Position Relative*/
    div {
      /*Dibujamos como borde su contexto*/
      border: 3px dashed red;
    }
    h1 {
      position: relative;
      background-color: yellow;
      margin: 0;
      top: 50px;
      left: 20px;
    }
  </style>
</head>

<body>
  <div>
    <h1>Hola Mundo</h1>
  </div>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Fugiat reprehenderit magni autem dignissimos incidunt nulla et eaque tenetur quaerat commodi necessitatibus, consequuntur earum laboriosam. Facilis aliquid voluptatibus, laudantium minus perferendis adipisci autem? Illum voluptatibus voluptatum neque sapiente, beatae hic enim ipsam placeat voluptate pariatur optio minima tempora impedit qui possimus temporibus fuga id dolore itaque atque ipsa minus non. Asperiores id veritatis culpa eos, molestiae cumque. Quo necessitatibus amet minima quaerat dicta perspiciatis a adipisci enim velit! Qui, aliquid corrupti voluptates omnis accusamus eveniet saepe nulla modi atque minus vitae nihil provident, praesentium sequi est excepturi necessitatibus alias earum labore!</p>
</body>

</html>
```

# Position: absolute
1. El elementon no conserva su espacio en el flujo
2. Sus dimensiones se adaptan al contenido, o a las dimensiones definidas
3. Su contexto es su ancestro posicionado más cercano, si este no tiene algun ancestro posicionado este toma de contexto el viewport.
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
  <style>
    *,
    *:before,
    *:after {
      box-sizing: border-box;
      font-family: sans-serif;
    }
    
  </style>
</head>

<body>
  <div class="poster">
    <img src="https://i.kinja-img.com/gawker-media/image/upload/s--S24cks6n--/c_scale,f_auto,fl_progressive,q_80,w_800/19fk32sw3nt1wjpg.jpg" alt="">
    <p class="caption">Star Wars de 1970</p>
  </div>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Voluptate harum accusamus rerum maiores tenetur magni, molestiae quibusdam nulla placeat doloribus laudantium maxime voluptates culpa possimus quaerat saepe eveniet pariatur! Vel.</p>
</body>

</html>
```
# Position fixed
Realizaremos un menu desplegable
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
</head>

<body>
  <ul class="menu">
    <li><a href="">Item 1</a></li>
    <li><a href="">Item 2</a></li>
    <li><a href="">Item 3</a>
      <ul>
        <li><a href="">Sub Item 1</a></li>
        <li><a href="">Sub Item 2</a></li>
        <li><a href="">Sub Item 3</a>
          <ul>
            <li><a href="">Sub Sub Item 1</a></li>
            <li><a href="">Sub Sub Item 2</a></li>
            <li><a href="">Sub Sub Item 3</a></li>
          </ul>
        </li>
      </ul>
    </li>
    <li><a href="">Item 4</a></li>
    <li><a href="">Item 5</a></li>
    <li><a href="">Item 6</a></li>
  </ul>
</body>

</html>
```
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

.menu,
.menu ul {
  list-style: none;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: 0;
}

.menu {
  display: table;
  background-color: #333;
}

.menu > li {
  float: left;
}

.menu li {
  position: relative;
}

.menu a {
  display: block;
  padding: .5rem 1.5em;
  color: #eee;
  text-decoration: none;
  /*Ojo con esta propiedad ;)*/
  white-space: nowrap; /*Hace que no salte de línea y se acomode al texto-se aplica al `a` porque es el que contiene el texto*/
}

.menu a:hover {
  background-color: rgba(0, 0, 0, 0.76);
}

.menu li > ul {
  position: absolute;
  background-color: #222;
  display: none;
}

.menu li:hover > ul {
  display: block;
}

.menu ul ul {
  background-color: gray;
  top: 0;
  left: 100%;
}
```
# Positio Fixed
Este fija un elemento respecto al viewport
1. Pierde su espacio en el flujo
2. Su contexto es el viewport siempre
3. Sus dimensiones se ajustan al contenido, es igual al `position absolute`, salvo que se haya declarado su tamaño
4. Se queda fijo en el viewport sin moverse con el scroll
* Tener en cuenta de que si usamos esta propiedad tenemos que compensar esto con un padding-top o colucionar con margin etc.
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
</head>

<body>
  <header class="main-header">Escuela Digital</header>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consectetur aliquid non enim, ad perspiciatis ex ea delectus, voluptatum omnis pariatur quam fugit beatae, voluptas commodi placeat? Pariatur iste ab eos ad veritatis tempore, culpa, atque a similique eaque laborum perferendis, odit modi dolorem voluptas dolorum, quibusdam ullam accusantium illo cum hic deleniti est? Molestias omnis odio minus dolor tenetur deleniti sint impedit dicta mollitia, dolores facere inventore nesciunt rerum repellendus suscipit hic ipsam repudiandae eligendi voluptatem dolorem quae quia beatae sunt? Eius sequi quam voluptatem non sapiente explicabo animi harum rerum cum labore! Obcaecati est maiores, cum. Sint excepturi, sit.</p>
</body>

</html>
```
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}
body {
  padding-bottom: 100em;
  margin: 0;
}
.main-header {
  background-color: #5a65b4;
  color: #eee;
  padding: 1em;
  text-align: center;
  font-weight: bold;
  position: fixed;
  top: 0;
  width: 100%;
}
```
Menu de navegacion lateral
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
</head>

<body>
  <nav class="main-nav">
    <ul class="main-menu">
      <li class="menu-item"><a class="menu-link" href="#item1">Item 1</a></li>
      <li class="menu-item"><a class="menu-link" href="#item2">Item 2</a></li>
      <li class="menu-item"><a class="menu-link" href="#item3">Item 3</a></li>
      <li class="menu-item"><a class="menu-link" href="#item4">Item 4</a></li>
      <li class="menu-item"><a class="menu-link" href="#item5">Item 5</a></li>
      <li class="menu-item"><a class="menu-link" href="#item6">Item 6</a></li>
      <li class="menu-item"><a class="menu-link" href="#item7">Item 7</a></li>
      <li class="menu-item"><a class="menu-link" href="#item8">Item 8</a></li>
      <li class="menu-item"><a class="menu-link" href="#item9">Item 9</a></li>
      <li class="menu-item"><a class="menu-link" href="#item10">Item 10</a></li>
      <li class="menu-item"><a class="menu-link" href="#item11">Item 11</a></li>
      <li class="menu-item"><a class="menu-link" href="#item12">Item 12</a></li>
      <li class="menu-item"><a class="menu-link" href="#item13">Item 13</a></li>
      <li class="menu-item"><a class="menu-link" href="#item14">Item 14</a></li>
      <li class="menu-item"><a class="menu-link" href="#item15">Item 15</a></li>
      <li class="menu-item"><a class="menu-link" href="#item15">Item 16</a></li>
      <li class="menu-item"><a class="menu-link" href="#item15">Item 17</a></li>
      <li class="menu-item"><a class="menu-link" href="#item15">Item 18</a></li>
      <li class="menu-item"><a class="menu-link" href="#item15">Item 19</a></li>
      <li class="menu-item"><a class="menu-link" href="#item15">Item 120</a></li>
    </ul>
  </nav>
  <main>
    <section>
      <h2 id="item1">Section 1</h2>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vero cumque odit odio enim! Libero iure quae delectus ut harum voluptas dicta saepe, tempora incidunt impedit veniam suscipit distinctio, rem dolores.</p>
    </section>
    <section>
      <h2 id="item2">Section 2</h2>
      <p>Ut eaque possimus officiis cum quia ab assumenda quidem obcaecati, maiores tenetur, veniam libero, nobis veritatis illum repellendus id ipsum iusto, suscipit placeat. Pariatur eveniet totam, aliquid ratione fuga voluptas.</p>
    </section>
    <section>
      <h2 id="item3">Section 3</h2>
      <p>Tenetur soluta officia distinctio quam eligendi, minima reprehenderit quod possimus beatae, labore tempora nulla et fugiat aut, consequatur dolores saepe impedit ad omnis dicta rem maiores consequuntur temporibus vitae, deserunt!</p>
    </section>
    <section>
      <h2 id="item4">Section 4</h2>
      <p>Autem debitis laudantium, numquam fugit dolores vitae voluptates, dolor porro. Ratione ipsam laborum rerum repudiandae, sit dicta vitae quia et fuga, sunt, reiciendis iste adipisci dolorum commodi harum ex velit.</p>
    <section>
      <h2 id="item5">Section 5</h2>
      <p>Facere beatae, cupiditate ducimus perferendis sapiente officia et dicta repudiandae, nihil quisquam, eius dignissimos quis? Perspiciatis accusamus, sit asperiores natus praesentium deserunt qui mollitia distinctio incidunt magnam, porro iure impedit.</p>
    </section>
    <section>
      <h2 id="item6">Section 6</h2>
      <p>Amet itaque ea quae repellendus dolores molestiae dolorum quia eos iusto. Beatae pariatur facilis ducimus dolor aliquid magni nam sed modi corporis cupiditate ratione nihil, qui distinctio aut odit laborum.</p>
    </section>
    <section>
      <h2 id="item7">Section 7</h2>
      <p>Itaque repudiandae, eos totam deleniti at porro possimus odio vel, consequuntur facilis, fugiat aspernatur ipsam fuga expedita repellat placeat nisi. Sint ex debitis corporis culpa maxime, asperiores veniam veritatis magni!</p>
    </section>
    <section>
      <h2 id="item8">Section 8</h2>
      <p>Eos blanditiis, vel pariatur eum atque reprehenderit tempora. Accusantium tenetur, nesciunt libero esse quos temporibus voluptate assumenda quibusdam quidem quia expedita, nam error magni aliquam in voluptates nemo repellat ex.</p>
    </section>
    <section>
      <h2 id="item9">Section 9</h2>
      <p>Debitis soluta eveniet tempora repudiandae explicabo, molestiae iste fugit veniam eligendi! Iure architecto qui, ipsum, sunt laudantium quas nobis atque possimus facilis distinctio unde. Accusamus numquam neque, exercitationem eius porro!</p>
    </section>
    
  </main>
</body>

</html>
```
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  margin: 0;
}

.main-nav {
  position: fixed;
  background-color: #ddd;
  width: 25%;
  top: 0;
  height: 100%;
  overflow: auto;
}

.main-menu {
  list-style: none;
  margin-top: 0;
  margin-bottom: 0;
  padding-left: 0;
}

.menu-item {
  border-bottom: 1px solid #bbb;
}

.menu-link {
  display: block;
  line-height: 3;
  text-decoration: none;
  color: #222;
  padding-left: 1em;
}

main {
  margin-left: 27%;
}
```
# Z-index
Tips:
* Evitar poner z-index correlativos osea `(1, 2, 3, ...)`, NO usar esto, ponerlo cada 10 o cada 20, en el proyecto se deben de especificar estas reglas.
* `pseudoelementos`
  * Cuando nosotros hacemos uso de `pseudoelementos` y queremos ponerlo detras de su padre este no nos dejara hasta que el elemento original no tenga `z-index` si no tiene ya nos hara caso
```css
.uno {
  position: relative;
  z-index: ; /*No nos hará caso el z-index del pseudoelemento hasta que este desaparezca*/
} 
.uno::before {
  content: '';
  display: block;
  width: 150px;
  height: 150px;
  position: absolute;
  z-index: -1 | 1;
}
```
# Position sticky
Position sticky es una mezcla entre position relative y position fixed
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  margin: 0;
  padding-bottom: 150em;
  text-align: center;
}


nav {
  width: 100%;
  padding: 1em;
  background-color: hsl(190, 80%, 50%);
  color: white;
  /**/
  position: sticky;
  /*Indicarle desde cuantos pixeles se convertira a sticky*/
  top: 0px;
}
```
* Recomendación: Por ahora no usar sticky, y seguir usando JS. :)

# Fundamentos FlexBox
Caja flexible, es un nuevo modelo de layout que revolucionó por completo el diseño web, cambiaron para bien, pero a la vez este nos trajo retos pero estos ya se vencieron para este año 2017, asi que no hay temor para usarlos, 
Es un nuevo modelo de layout, y un modelo de layout es algo que el navegador usa para dibujar elementos y para saber como este se relacionara con los elementos que estan a sus costados y sus hijos, saber donde lo va a poner, que dimensiones como va a calcular su ancho, alto::: position es un modelo de layout, box-model es otro modelo de layput, table-layout tambien es otro modelo de layout pero este no estan importante algunos tips y listo, y otros recien llegaditos que son `flexbox layout` y `grid`

Flexbox llega para solucionar varios problemas algunos de estos son: 
* alineacion vertical
* centrar elementos, con anchos no declarados.
* Tener elementos de la misma altura,
* Nos trae una serie de propiedades muy importante

Es un modelo de layout, osea que agrupa varias propiedades asi como `position`

## Qué requiere flexbox
* Flexbox requiere de un elemento padre y de al menos un elemento  hijo directo no descendiente
* El `padre` se llama flex-container
* El `hijo` es llamado flex-item

* PADRE
  * `display: flex | inline-flex;` Crea un **contexto** flex para sus hijos, la diferencia es que inline lo convierte en inline, es el comportamiento que va a tener con sus elementos vecinos
* HIJOS
  * Los hijos (flex-items) son las cajas flexibles
  * Elementos hijos directos del flex-container
  * pseudoelementos ::before y ::after
  * el texto
Viendo que el texto automaticamente es un flex-item
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
</head>

<body>
  <div class="container">
    Hola Mundo
    <div class="item">1</div>
  </div>
</body>

</html>
```
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  display: flex;
  width: 500px;
  height: 500px;
  background-color: hsl(240, 100%, 90%);
  justify-content: space-between;
  align-items: flex-end;
}

.item {
  align-self: flex-start;
  order: -1;
}
```
# Main axis y cross-axis
* main axis: eje principal
* cross axis: eje secundario

* Tenemos tambien `main size` que sería equivalente a width
* Tenemos tambie `cross size` que seria equivalente a height

* Tenemos tambien el `cross start` y `cross end`
* Tenemos tambien el `main start` y `main end`

# Dirección de ejes
Ya que los ejes podrian cambiar su orientación
* `flex-direction` : Este es el unico que puede variar el flujo de direcciones
* `flex-wrap`: Nos ayuda a que los flex-items se acomoden en la caja dando saltos de linea
* `flex-flow: flex-direction flex-wrap`: Este es un shorthand

# Alineación de ejes
## Alineacion en eje principal
* `justify-content`

* Los margenes en flexbox existen.. osea que no se colapsan.. podriamos editarlo manualmente...
* Respeta el margin top y bottom, no se colapsan

* Uno de los trucos mas importantes en Flexbox es `margin: auto` al poner esto este absorbe todo el espacio libre en la direccion que se encuentre...
ejemplo
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
</head>

<body>
  <div class="container">
    <item class="item">1</item>
    <item class="item">2</item>
    <item class="item">3</item>
    <item class="item">4</item>
    <item class="item">5</item>
    <item class="item">5</item>
  </div>
</body>

</html>
```

```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  width: 500px;
  height: 500px;
  background-color: hsl(240, 100%, 90%);
  /**/
  display: flex;
  flex-direction: column;
  /**/
}

.item {
  width: 30px;
  height: 30px;
  background-color: yellow;
  text-align: center;
  line-height: 30px;
  margin: 10px;
}

.item:nth-child(even) {
  background-color: green;
  color: white;
}

.item:nth-child(5) {
  margin-top: auto;
}
```
Otro ejemplo
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
</head>

<body>
  <div class="container">
    <item class="item">1</item>
    <item class="item">2</item>
    <item class="item">3</item>
    <item class="item">4</item>
    <item class="item">5</item>
  </div>
</body>

</html>
```
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  width: 500px;
  height: 500px;
  background-color: hsl(240, 100%, 90%);
  /**/
  display: flex;
  flex-direction: column;
  /**/
}

.item {
  width: 30px;
  height: 30px;
  background-color: yellow;
  text-align: center;
  line-height: 30px;
  margin: 10px;
}

.item:nth-child(even) {
  background-color: green;
  color: white;
}

.item:nth-child(3) {
  margin-top: auto;
  margin-bottom: auto;
}
```
Centrado absoluto
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  width: 500px;
  height: 500px;
  background-color: hsl(240, 100%, 90%);
  /**/
  display: flex;
  /**/
}

.item {
  width: 30px;
  height: 30px;
  background-color: yellow;
  text-align: center;
  line-height: 30px;
  /**/
  margin: auto; /*Centrado absoluto*/
  /**/
}
```

## Alineación en eje secundario
* `align-item` cuando solo hay una linea
* `align-content` cuando hay mas de una linea es decir usamos `flex-wrap`

# Propiedades de los hijos
## order
* Es un numero entero
* Todos los `flex-item` tienen por defecto `0` 

## align-self
* Toma un solo hijo para que edite su alineacion.

# Cajas flexibles - `flex-items`
* `flex-basis` main-size inicial
* `flex-grow` factor de crecimiento
  * Recibe numero entero
  * Por default es `0`
* `flex-shrink` factor de encogimiento
  * Recibe numero entero
  * Por default es `1`

* `flex: grow shrink basis`
* `flex: 2` Edita al flex-grow
* `flex: none` Dejan de ser flexibles.

### Ejercicios
#### Menú
menu.html
```html
<!DOCTYPE html>
<html lang="es">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge, chrome=1">
   <title>Menu con FLEX</title>
   <meta name="description" content="">
   <link rel="stylesheet" href="./menu.css">
</head>
<body>
   <ul class="menu">
      <li class="menu__item"><a class="menu__link" href="#">Item 1</a>
         <ul>
            <li><a href="">Sub Item 1</a></li>
            <li><a href="">Sub Item 2</a></li>
            <li><a href="">Sub Item 3</a>
               <ul>
                  <li><a href="">Sub Sub Item 1</a></li>
                  <li><a href="">Sub Sub Item 2</a></li>
                  <li><a href="">Sub Sub Item 3</a></li>
               </ul>
            </li>
         </ul>
      </li>
      <li class="menu__item"><a class="menu__link" href="#">Item 2</a></li>
      <li class="menu__item"><a class="menu__link" href="#">Item 3</a></li>
      <li class="menu__item"><a class="menu__link" href="#">Item 4</a></li>
      <li class="menu__item"><a class="menu__link" href="#">Item 5</a></li>
      <li class="menu__item"><a class="menu__link" href="#">Item 6</a></li>
   </ul>
</body>
</html>
```
menu.css
```css
.menu {
   display: flex;
   background-color: #333;
}

ul {
   margin-top: 0;
   margin-bottom: 0;
   padding-left: 0;
   list-style: none;
}

.menu__item {
   flex: auto;
}

li {
   position: relative;
}

li > ul {
   display: none;
   background-color: #333;
}

li:hover > ul {
   display: block;
}

li > ul {
   position: absolute;
}

li ul ul {
   left: 100%;
   top: 0;
}

a {
   color: #ffffff;
   text-decoration: none;
   display: block;
   text-align: center;
   padding: 0.5em;
   white-space: nowrap;
}
```

#### 2.
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>CSS Desde cero 2017</title>
  <link rel="stylesheet" href="estilos.css">
</head>

<body>
  <div class="banner">
    <div class="item"><span>Excelencia</span></div>
    <div class="item"><span>Experiencia</span></div>
    <div class="item"><span>Calidad</span></div>
    <div class="item"><span>Calidez</span></div>
  </div>
</body>

</html>
```
```css
*,
*:before,
*:after {
  box-sizing: border-box;
  font-family: sans-serif;
}

body {
  margin: 0;
}

.banner {
  display: flex;
  width: 80%;
  margin-left: auto;
  margin-right: auto;
  height: 250px;
}

.item:nth-child(1) {
  background-color: #fd5555;
}
.item:nth-child(2) {
  background-color: #82ff86;
}
.item:nth-child(3) {
  background-color: #82ffec;
}
.item:nth-child(4) {
  background-color: #fff9ea;
}

.item {
  flex: 1 0 80px;
  display: flex;
  transition: all .3s;
}

.item span {
  margin: auto;
  transform: rotate(-90deg);
  transition: all .3s;
}

.item:hover {
  flex: 10 0 auto;
}

.item:hover span {
  transform: none
}
```

# Display: table
Todos los detalles de display table casi nunca lo usaremos :'), su uso es realmente limitadisimo.

Display table nos iba a dar layout pero no funciono :)

```html
<!DOCTYPE html>
<html lang="es">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge, chrome=1">
   <title>Display table</title>
   <meta name="description" content="">
   <link rel="stylesheet" href="./6.1.tablas.css">
</head>
<body>
   <div class="table">
      <h2>Descuento</h2>
      <a href="#">Comprar</a>
   </div>
</body>
</html>
```

```css
/*El problema de display inline es que no me centra cuando hago esto*/

.table {
   width: 30%;
   background-color: yellow;
   /* display: inline-block; */
   display: block;
   margin-left: auto;
   margin-right: auto;
   text-align: center;
}

/*Bueno esto lo solucionamos con un width y un display: block*/

/*Pero que pasa si nosotros queremos que el contenido se acomode al contenido y que ademas de eso lo vayamos a centrar*/

/*aqui es donde display table nos salva la vida*/

.table {
   background-color: yellow;
   display: table;
   margin-left: auto;
   margin-right: auto;
   text-align: center;
}
```
Otro uso interesante del display table, es cuando tu quieres limpiar `floats` aunque ahora ya no se use pero si necesitamos usarla aqui la tenemos.
```css

/*OTRO USO */

.table {
   background-color: yellow;
   margin-left: auto;
   margin-right: auto;
   text-align: center;
}

h2 {
   float: left;
}
a {
   float: right;
}

/*vemos que el contenedor ya no contiene ni al elemento `h2` ni tampoco a `a`*/
.table {
   display: table;
   background-color: yellow;
   margin-left: auto;
   margin-right: auto;
   text-align: center;
}

h2 {
   float: left;
}
a {
   float: right;
}
/*y listo lo solucionamos claro que podemos darle un width de 100% para mejorarlo*/
```
Esos son los dos usos más conocidos. de seguro que hay mas pero estas son las mejores.

Recomendacion nunca usarlo para layout. ni para imagenes

A parte de estos hay:
* `display: table-cell` para que un elemento se comporte con una celda.
* `display: table-row` para imitar el comportamiento de una fila en una tabla.

## tablas con CSS
```html
<!DOCTYPE html>
<html lang="es">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge, chrome=1">
   <title></title>
   <meta name="description" content="">
   <link rel="stylesheet" href="./6.3.cssTablas.css">
</head>
<body>
   <div class="table-container">
         <table>
               <tr>
                  <th>Columna 1</th>
                  <th>Columna 2</th>
                  <th>Columna 3</th>
               </tr>
               <tr>
                  <td>Hola Mundo</td>
                  <td>Hola Mundo</td>
                  <td>Hola Mundo</td>
               </tr>
               <tr>
                  <td>Hola Mundo numero 2</td>
                  <td>Hola Mundo</td>
                  <td>Hola Mundo</td>
               </tr>
               <tr>
                  <td>Hola Mundo numero 2</td>
                  <td>Hola Mundo</td>
                  <td>Hola Mundo</td>
               </tr>
               <tr>
                  <td>Hola Mundo numero 2</td>
                  <td>Hola Mundo</td>
                  <td>Hola Mundo</td>
               </tr>
               <tr>
                  <td>Hola Mundo numero 2</td>
                  <td>Hola Mundo</td>
                  <td>Hola Mundo</td>
               </tr>
               <tr>
                  <td>Hola Mundo numero 2</td>
                  <td>Hola Mundo</td>
                  <td>Hola Mundo</td>
               </tr>
            </table>
   </div>
</body>
</html>
```
Tener muy en claro que las propiedades de box model(margin, padding) no se aplican a este modelo de tabla...
```css
* {
   box-sizing: border-box;
}

/*tabla responsive*/
.table-container {
   overflow: auto;
}

table {
   margin: 2em auto;

   border-collapse: collapse; /*para colapsar el espacio en el borde*/
   /*border-spacing: 10px;*/ /*para aumentar el espacio del borde*/
   /*cuando le damos table-layou tenemos que darle un width para que asi todas tengan el mismo ancho*/
   table-layout: fixed;
   width: 80%;


   /*tabla responsive*/
   width: 75%;
   min-width: 600px;
}

tr:nth-child(even) {
   background-color: #eee;
}

td {
   border: 1px solid #ccc; /*si se dibuja*/
   padding: .3em;
}

th {
   background-color: teal;
   color: #ffffff;
   padding: 0.5em;
   border-right: 1px solid rgba(255, 255, 255, .5);
}

th:last-child {
   border-right: none;
}
th:first-child {
   border-left: 1px solid teal;
}
```

# Colores en CSS
Se puede expresar a traves de varias formas:
* palabra clave `red` `yellow` `green` `blue`
* hexadecimal 
* funciones `rgb` `rgba` `hsl` `hsla`

hay 4 funciones de color, hay mas pero aun los navegadores no lo soportan...

Tambien hablaremos de los degradados de color...

* `color`
* `background-color`
* `box-shadow`
* `border-color`


## hexadecimal
color `rgb` 

`rrggbb`

La notacioin exadecimal va de 0 a f
1234567890 abcdef
```css
body {
   /*f es el maximo*/
   background-color: #ffffff; /*todo rrggbb*/
   background-color: #ff00ff; /*todo rr00bb*/
   background-color: #ffff00; /*todo rrgg00*/
   background-color: #ff0000; /*todo rr0000*/
   background-color: #0000ff; /*todo rr0000*/
   background-color: #00ff00; /*todo rr0000*/
   
   /*si las parejas son iguales las podemos resumir en uno solo*/
   background-color: #fff; /*todo rrggbb*/
   background-color: #f0f; /*todo rr00bb*/
   background-color: #ff0; /*todo rrgg00*/
   background-color: #f00; /*todo rr0000*/
   background-color: #00f; /*todo rr0000*/
   background-color: #0f0; /*todo rr0000*/
   

   /*Entonces cuando veamos un hexadecimal de 3 no nos asustemos, pero aqui viene viene el problema*/
   background-color: #59a;
   /*que pasa si este color yo lo necesito más intenso? o mas saturado que hago?*/
   /*Normalmente usamos otros programas como PS o Sass*/
   /*Un neutro no es un color eje. #fff o #000 etc este es un neutro que no es conocido como color, estoy frente a un gris*/
}
```

## color RGB y RGBA
```css
body {
   /*Rgb es lo mismo de hexadecimal sigo usando estos colores fundamentales, con la diferencia que ya no escribe en hexadecima escribes de 0 a 255 separado por comas*/
   background-color: rgb(255, 0, 0);
   background-color: rgb(255, 255, 0);
   background-color: rgb(255, 0, 255);
   background-color: rgb(0, 255, 255);
   background-color: rgb(0, 0, 255);
   background-color: rgb(0, 255, 0);

   /*Tambien podemos usar RGBA y lo que le agrega es el canal alpha que le da transparencia*/
   background-color: rgba(0, 255, 0, .5);
   background-color: rgba(0, 255, 0, 1);
   background-color: green;

   /*Tener en cuenta que el verde no es verde :v puedes verificarlo arriba*/
   /*El verde real es lime*/
   background-color: lime;
}
```

## Color HSL y HSLA
Es una funcion de color que es muy facil de aprender, al comienzo cuesta pero cuando lo aprendemos nos da posibilidades enormes.

* `H Hue` Es es angulo
* `S Saturation` Es la fuerza de color
* `L Ligthnees` Cuanta luz tiene el color

```css
/*

hsl(hue, saturacion%, ligthnees%)
hsl(color360°, saturacion%, luz%)

red es 0° o 360°

*/
body {
   background-color: hsl(0, 100%, 50%); /*rojo puro*/
   background-color: hsl(60, 100%, 50%); /*amarillo puro*/
   background-color: hsl(120, 100%, 50%); /*lime(verde) puro*/
   background-color: hsl(180, 100%, 50%); /*cyan puro*/
   background-color: hsl(270, 100%, 50%); /*magenta puro*/
   background-color: hsl(360, 100%, 50%); /*rojo puro*/
   background-color: hsl(360, 100%, 25%); /*rojo rojo con 25 de luz*/
   background-color: hsl(360, 100%, 75%); /*rojo con 75 de luz*/
   background-color: hsl(360, 50%, 75%); /*rojo con 50% de saturacion y 75 de luz*/
   background-color: hsl(360, 0%, 80%); /*gris*/

   /*de AHI tenemos HSLA que nos da la transparencia*/
   background-color: hsla(0, 100%, 50%, .5);
}
```

### example
```css
button {
   background-color: hsl(200, 80%, 50%);
   border: none;
   color: white;
   padding: .5em 1em;
}

button:hover {
   background-color: hsl(200, 80%, 45%);
   background-color: hsl(300, 80%, 50%); /*cambio el color pero dejo la sat y la luz como estaban*/
}
```

# Degradado Lineal y Radial
Son bases transiciones de color comienzas en uno y teminas en otro, y el cambio no es brusco sino que el navegador dibuja todos los colores intermedios...

## D. Lineal
linear-gradient(red, yellow)

## D. Radial
radial-gradient
```css
bodys {
   height: 100vh;
   background-image: linear-gradient(red, magenta);
   background-image: linear-gradient(red, orange, magenta);
   background-image: linear-gradient(red, yellow);
   
   /*Nosotros podemos indicarle al navegador cuanto de pureza va a tener nuestro color*/
   background-image: linear-gradient(
      hsl(60, 100%, 80%) 98%, /*hasta el 98%*/
      hsl(0, 70%, 45%) 98% /*desde el 98%*/
   );
   background-size: 50px;
}

body {
   height: 100vh;
   background-image: linear-gradient( /*tambien podemos usar radial-gradient*/
      40deg,/* to right | to left | to bottom | to top | circle */
      hsl(60, 100%, 85%),/*hasta el 50%*/
      hsl(0, 60%, 45%) /*desde el 50%*/
   );
}
```

# Display GRID
Modelo de layput cmo flexbox, Grid ya esta muy pronto a estandarizarse, aunque ya podemos usar prefijos, en los mobiles falta pero esto ya se viene!! :)

Un error es usar algo cuando algo ya es estandar, es como llegaste tarde y te perdiste del momento... es bueno estudiarlo de una vez.

Y es un estandar!!! :D

Es un modelo de layout, es un algoritmo del navegador que nos dice como un elemento se distribuye en el documento y como se relaciona con sus elementos primos.

Y viene a solucionar conceptos que nisiquiera flexbox podia solucionar, nosotros seguimos atrapados con el flujo del HTML, si bien es cierto tenemos order, es un avance pero no es completo, sin embargo este nos ayuda en el eje principal pero no hace nada en el eje secundario no hay un order.

Display grid solo trabaja con un eje, 

hay lineas lo alinea realmente flexbox los distribuye en un solo eje el otro eje nos ayuda ayudarnos a alinear, pero no hay una forma de cruzar.

Y bueno los podemos hacer con flexbox pero necesitamos varios contenedores, pero con elementos hermanos es imposible, conGRID si podemos, Grid trabaja con celdas 

* comlumnas
* filas

El orden no nos interesa como esta el HTML y nosotros podemos manipularlo como nosotros querramos.

con Display Grid no nos interesa...

Es similar a `display: flex;` ya que necesitamos un papa y unos hijos.

```css
html {
   box-sizing: border-box;
   font-size: 16px;
}

*,
*:after,
*:before {
   margin: 0;
   padding: 0;
   box-sizing: inherit;
}

.grid-container {
   display: grid;
   /*1. definir las columnas y las filas*/
   grid-template-columns: repeat(2, 2fr) 1fr;
   grid-template-rows: 1fr 3fr .5fr .6fr;
   grid-gap: 10px;
}

.grid-item {
   background-color: hsl(300, 100%, 50%);
   text-align: center;
   display: flex;
   justify-content: center;
   align-items: center;
   font-size: 2rem;
   color: white;
}


.grid-item:nth-child(even) {
   background-color: hsl(220, 100%, 50%);
}

.grid-item:nth-child(5) {
   grid-column: span 2;
}

/*
Ni bien ponemos display grid ya tenemos un contexto
*/
```
* padres
   * grid-template-columns
   * grid-template-rows
   * grid-gap
* hijos
   * grid-column
   * grid-row

# TRANSFORMACIONES ANIMACIONES EN 3D
Veremos lo basico de cada uno de estos conceptos ;)

## Transformaciones
En css todos los elementos tienen coordenadas, en la mayoría de los casos el eje(0,0) se encuentra en la parte superior-izquierda..., por ejemplo background-position usa esto y muchas mas propiedades son asi, hacia abajo es positivo, cuando estamos frente a transform ese eje cambia y se ubica en el centro del container...

Estas son las 4 posibles tranformaciones:

`transform: rotate | scale | skew | translate`

Pueden expresarse de dos formas

* `rotate(<angle>) || rotate(x, y) || [rotateX, rotateY](Estos ya son en 3 dimensiones)`: rota, angle se representa por `deg` o por turn que es una vuelta
* `scale(x=y) || scale(x, y) || scaleX scaleY`:  escala o agranda
* `skew(x=y) || skew(x, y) || skewX, skewY`: deforma
* `translate(x=y) || translate(x, y) || translateX, translateY`: mueve

Tener siempre en cuenta el orden
```css
:root {
   --size: 200px;
}

.container {
   width: var(--size);
   height: var(--size);
   border: 1px solid hsl(0, 100%, 0%);
   margin: auto;
   position: relative;
}

.container-item {
   position: absolute;
   border: 1px solid hsl(0, 100%, 50%);
   background-image: linear-gradient(
      transparent 99px, 
      red 99px,
      red 100px,
      transparent 100px
   ),
   linear-gradient(
      to left,
      transparent 99px,
      blue 99px,
      blue 100px,
      transparent 100px
   );
   width: var(--size);
   height: var(--size);
   width: 50px;
   height: 50px;
   text-align: center;
   line-height: var(--size);
   font-size: 2em;
   opacity: .8;
   /*transform*/
   transform: rotate(50deg) translateY(200px) scaleY(2); /*Mucho ojo con translate ya que cambia hasta sus ejes de movimiento(coordenadas).*/

   /*Tener en cuenta tambien de que si primero ponemos el translate primero hará eso y después hará el rotate.*/
   transform: translateX(200px) rotate(50deg) scaleY(2);
   
   /*y tambien*/
   transform: translateX(200px) scaleY(2) rotate(50deg);

   /*Entonces primera moraleja en transformaciones: el orden de las transformaciones importa, podemos hacer varias separandolas por espacio pero el orden importa porque estamos cambiando varias veces el eje de coordenadas */
   transform: rotate(45deg);
   transform: scale(1.2);
   transform: translate(10px, 0);
   /*Nota tener en cuenta que en translate podemos usar el tamaño del mismo objeto como si fuera un position absolute con respecto a este*/
   transform: translate(100%, 0);
   /*con translate podiamos centrar ya que antes no habia flexbox*/
   top: 50%;
   left: 50%;
   transform: translate(-50%, -50%);

   transform: skew(20deg); /*lo que hace es que lo aplana... y forma como un paralelogramo*/
}
```
### Ejercicios
efecto darth vader :3
```html
<!DOCTYPE html>
<html lang="es">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge, chrome=1">
   <title>HTML5 desde cero</title>
   <meta name="description" content="HTML5 desde cero">
   <link rel="stylesheet" href="./index.css">
</head>
<body>
   <h1>Transformaciones</h1>
   <div class="container">
   </div>
</body>
</html>
```

```css
.container {
   width: 500px;
   height: 300px;
   background: url('./img/perro.jpg') center / cover;
   position: relative;
}

.container::before {
   position: absolute;
   content: "Perro";
   background-color: rgba(181, 156, 156, 0.78);
   display: block;
   width: 100%;
   height: 100%;
   left: 0;
   top: 0;
   z-index: 10;
   color: white;
   display: flex;
   justify-content: center;
   font-size: 3em;
   align-items: center;

   transform: scale(0.01);
   opacity: 0;
   transition: all .3s;
}

.container:hover::before{
   transform: scale(1);
   opacity: 1;
}
```
ejercicio card con transform
```css
.container {
   position: relative;
   width: 300px;
   height: 300px;
   background-color: hsl(300, 100%, 70%);
   margin: auto;
   overflow: hidden;
   display: flex;
}

.container::before {
   content: "";
   position: absolute;
   height: 100%;
   width: 100%;
   background-color: hsl(160, 100%, 70%);
   top: 50%;
   left: -50%;
   border-radius: 50%;
   opacity: .5;
   transform: scale(.01);
   transition: all .3s;
}

.container::after {
   content: "Hola Mundo";
   display: block;
   margin: auto;
   font-size: 3em;
   color: #fff;
   z-index: 10;
   transform: translate(-200%, 200%);
   transition: all .3s;
}

.container:hover::before{
   transform: scale(3)
}

.container:hover::after{
   transform: translate(0,0)
}
```
corazón en css
```css
.corazon {
   width: 400px;
   height: 280px;
   margin: auto;
   position: relative;

}

.corazon::before,
.corazon::after {
   content: "";
   display: block;
   position: absolute;
   height: 100%;
   width: 50%;
   background-color: red;
   border-radius: 50% 50% 0 0;
}

.corazon::after {
   left: 50%;
   transform: rotate(-50deg);
   transform-origin: bottom left;
}

.corazon::before {
   /* transform: translateX(-70px) rotate(-45deg); */
   transform: rotate(50deg);
   transform-origin: bottom right;
}
```
## Transfor origin
```css
.point {
   width: 10px;
   height: 10px;
   background-color: red;
   border-radius: 50%;
   transform: rotate(0deg);/*jugar con esto*/
   transform-origin: 100px 20px;
}
```
# Transiciones time, function
Permite que un cambio de estilos se haga en cierto tiempo, generando asi una animación, eso lo hace `transition`
```css
h1 {
   background-color: red;

   transition: background-color 3s;
}

h1:hover {
   background-color: green;
}
```
* transition-delay
   * transition: background-color time-transition delay
   * transition: background-color .3s 2s

Ejemplo con delay
```css
h1 {
   background-color: red;

   transition: background-color .3s;
}

h1::before {
   content: 'Hola Mundo';
   color: #ffffff;
   transition: color 3s 2s;
}

h1:hover {
   background-color: green;
}

h1:hover::before {
   color: yellow;
}
```
Funciones de timepo (aka timing function)

* `ease` funcion de tiempo hace que al final desacelere.
* `linear` funcion de tiempo hace que la velocidad sea constante.
* `ease-in` para que la aceleracion sea al inicio
* `ease-out` para que la aceleracion sea al final
* `ease-in-out` para que la desaceleracion sea al final y al inicio

Como hemos observado lo que nosotros estamos usando es un shorthand, las propiedades individuales son:
* `transition-property`: all, color, etc
* `transition-duration`: 2s
* `transition-delay`: 3s
* `transition-timing-function` ease, ease-in, etc

## ¿Cómo funciona el 3D y sus propiedades?
Recomendacion [ver video]

## Animaciones
```css
.ball {
   width: 100px;
   height: 100px;
   border-radius: 50%;
   background-image: radial-gradient(
      circle at 0 0,
      hsl(60, 100%, 50%) 25%,
      hsl(60, 100%, 30%) 70%,
      hsl(60, 100%, 1%)
   );
   animation-name: rebota; /*para darle un nombre a nuestra animacion*/
   animation-duration: 3s; /*la duracion que tendra nuestra animacion*/
   animation-delay: 0; /*El tiempo que esperara para realizar la animacion*/
   animation-direction: alternate; /*como realizara la animacion ida y vielta o solo ida*/
   animation-iteration-count: infinite;/*cuantas iteraciones tendra la animacion, pueden ser numeros o infinite*/
   animation-play-state: running;/*detener la animacion o hacerla correr, tunning paused, con hover detener u otra cosa*/
   animation-fill-mode: forwards;/*Como va a quedar la animacion a final none->para que quede en su estado inicial, o forwards para que quede en su estado final*/
   animation-timing-function: ease-in;/*igualito que transition*/
}
```

#### flip-card
```html
<!DOCTYPE html>
<html lang="es">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge, chrome=1">
   <title></title>
   <meta name="description" content="">
   <link rel="stylesheet" href="./flip-card.css">
</head>
<body>
   <div class="card-container">
      <div class="card">
         <div class="face front">Hola</div>
         <div class="face back">Adiós</div>
      </div>
   </div>
</body>
</html>
```
```css
.card-container {
   perspective: 1000px;
}
.card {
   width: 200px;
   height: 300px;
   position: relative;
   transition: all 3s;
   transform-style: preserve-3d; /*propiedad que lo hace todo*/
}

.card-container:hover .card {
   transform: rotateY(180deg);
}
.card-container:hover .back {
   backface-visibility: visible; /*propiedad que lo hace todo*/
   background-color: green;
}

.face {
   position: absolute;
   width: 100%;
   height: 100%;
   display: flex;
   justify-content: center;
   align-items: center;
   background-color: red;
   color: #fff;
   font-size: 2em;
}

.back {
   transform: rotateY(180deg);
   backface-visibility: hidden; /*propiedad que lo hace todo*/
}
```
#### esfera en 3D
```html
<!DOCTYPE html>
<html lang="es">

<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge, chrome=1">
   <title>HTML5 desde cero</title>
   <meta name="description" content="HTML5 desde cero">
   <link rel="stylesheet" href="./index.css">
</head>

<body>
   <div class="sphere">
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
      <div class="circle"></div>
   </div>
</body>

</html>
```
```css
body {
   background-color: #111;
   display: flex;
   min-height: 100vh;
   margin: 0;
}

.sphere {
   perspective: 10000px;
   position: relative;
   margin: auto;
   width: 200px;
   height: 200px;
   animation: sphere 2s infinite linear;
   transform-style: preserve-3d;
}

@keyframes sphere {
   to {
      transform: rotateY(1turn);
   }
}

.circle {
   position: absolute;
   width: 200px;
   height: 200px;
   border: 1px solid red;
   border-radius: 50%;
}

.circle:nth-child(2) {
   transform: rotateY(40deg);

}
.circle:nth-child(3) {
   transform: rotateY(80deg);
   
}
.circle:nth-child(4) {
   transform: rotateY(120deg);
}
.circle:nth-child(5) {
   transform: rotateY(160deg);
}
.circle:nth-child(6) {
   transform: rotateY(200deg);
}
.circle:nth-child(7) {
   transform: rotateY(240deg);
}
.circle:nth-child(8) {
   transform: rotateY(280deg);
}
.circle:nth-child(9) {
   transform: rotateY(320deg);
}
```

## Proyecto final
Usar el editor con el que te sientas más comodo

* usaremos cualquier editor
* usaremos prepros

### ESTRUCTURA
* tener un `index.php`

* trabajar con `archivos de desarrollo` y `archivos de producción`.

#### Pequeña introduccion en CSS
Sass es un metalenguaje de CSS o un superset que es un superset, un superset en un lenguaje que se basa en otros para rindarle mejores funcionalidades, Sass esta Basado en CSS, todo CSS valido es a la vez un scss válido.

##### ¿Por qué es cvr Sass?
* 1ero. Porque nos da variables
```scss
$color = green;

body {
   background: $color;
}
```
En sass tenemos todo tipo de operaciones a lo que en css puro las variables pueden tener errores al usar css mas que tdo por el tipo de datos.

Otra ventaja es que podemos importar archivos con:

```scss
@import "ruta/al/archivo";
```

Otra ventaja es que podemos anidar selectores... aunque no sea las mejores de las ideas
```scss
body {
   div {
      color: red;
   }
}
```
esto se compila a:
```css
body div {
   color: red;
}
```
Una ultima cosa es que podemos crear selectores usando `&`, dentro de un selector podemos usar de referencia al padre.
```scss
.element {
   background-color: $color;
   &:hover {
      background: red;
   }
   &__child {
      /**/
   }
   article & {

   }
}
```
En css esto sería
```css
.element:hover {
   background: red;
}
body__child {
   /**/
}
article .element {

}
```

Para convertirlo tenemos que usar prepros.

## Métodología BEM
Es una metodología que mas se usa en el mundo. Con el tema de React y Web Components tenemos que saber un decente JS.

* B Block
* E Element
* M Modifier

o bloque elemento modificador

Es una metodología muy conocida en el mundo, que nos ayuda a diseñar los componentes de nuestro sitio


Bloque 

es un elemento que es una entidad, que es algo autonomo ejemplo un menu, un footer, un articulo, este debe de funcionar de manera autonoma, osea que si esta en el header y yo lo muevo al footer debe seguir funcionando.

Uno cuando esta empezando hace cosas como las siguientes:
```css
header nav .menu {
   /* Code smell- es una jerga para señalar al codigo que apesta osea que no es bueno usarla, osea que aqui algo se va a descontrolar*/
}
/*lo podemos solucionar usando solo*/
.menu {

}
/*pero esto nos puede traer problemas si lo necesitamos en otra página de nuestro sitio.*/

/*Es ahí donde viene a salvarnos BEM*/
```

.main-menu (bloque)

.main-menu__item (elementos con dos guiones bajos `(__)`)

.main-menu--footer (algun modificador de nuestro main-menu) como por ejemplo que este main-menu lo usaremos en el footer pero con otro color de la letra solo eso, lo demas tiene que ser igualito.

## Métodología SMACSS
Es otra metodología que tambien se usa en todo el mundo que realmente revoluciono la forma de pensar en CSS, luego salieron otras como OCSS atomic design, pero este marco un antes y un despues, bootstrap foundation se basan en eso, tanto asi que el creador se pasa dictando conferencias que tienen un buen costo $.$ este es ya casi un gurú.

* Scalable and
* Modular
* Architecture for
* CSS

Y es que lo malo de CSS es que no es un lenguaje de programacion y eso es uno de los calvarios mas grandes para el desarrollador, cuando nosotros usamos un lenguaje de programacion tenemos guias de estilos, y nos mandan error pero con CSS podemos hacer lo que queramos y que si escribimos y escribimos alguna de esas lineas funcionaran otras no pero igual sigue funcionando y ni nos mandan error. CSS es muy permitivo.

SMACSS viene a decirnos que tenermos que organizar nuestros css en archivos incluso en carpetas.

Nos dice que tengamos grupos de:
* `Base` aplicados a elementos HTML no `clases` no `id`, es casi como un normalize, inicializar tus estilos.
* `Tema` Es el look and feel de la web o aplicacion, osea los estilos de diseño, lo que queremos comunicar.colores tipografias etc
* `Estado` Cambios de estado, elementos que aparecen y desaparecen, tenemos que usar `.is-hide` / `.is-show` ED GRID solo te hace el layout.
* `Layout` Maquetación sin estilos de tema
* `Módulos` Los componentes que se repiten a lo largo de la aplicacion, que no estan atados a ningun lugar de la aplicacion, iconos, widgets, botones

En la medida de lo posible podemos seguirlo pero no es necesario segurle al pie de la letra. behands, pinterest

### Media querys
Son consultas que se hacen al navegador para saber su tamaño de vp resolucion densidad de pixeles hay muchas media queries incluso podemos saber si el telefono esta en horizontal o vertical,

```css
@media screen and () and () () and () and() {

}

/*Todos los and son nuestras condicionales*/

@media print and () and () {

}

@media all and () {

}

```
* `screen`, `print` son los medios que si o si debemos definir, o bueno por ultimo `all`

```css
@media screen and (min-width: 480px) {

}
```

puden ir min-width max-width
