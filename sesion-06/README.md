# Sesión: Agregando filas y columnas con CSS Grid

Sigue el contenido a continuación durante clase para que no te pierdas ningún
detalle de lo que estás a punto de aprender.

## Objetivos

En esta sesión aprenderás:

- Usar componentes de Bootstrap para nuestra página.
- Reutilizar clases de Bootstrap.
- Desplegar los cambios a nuestra página web hosteada en Netlify.

## Contenido

### Agregando Bootstrap

#### Concepto: Framework CSS

Antes de continuar con el desarrollo de nuestro proyecto, hemos decidido hacer
una pausa con las demás secciones de la página y darnos el tiempo de refactorizar
ciertas partes haciendo uso de un framework de CSS, ¿pero qué es este último
término?

Hasta ahora, nosotros hemos escrito todo el código CSS para tener nuestro
proyecto como se ve ahora, lo cual está genial porque hemos puesto en práctica
varios conceptos y aprendido un montón de cosas en el camino, pero, ¿te has puesto
a pensar qué tan factible es hacer esto a una empresa en cada proyecto que
desarrolle?

Definitivamente es demasiado tiempo que la mayoría de empresas no está dispuesta
a invertir, o no al menos en cada proyecto, ante esto, muchas empresas y personas
de la comunidad (personas que hacen código CSS como tú) han optado por crear
código que pueda ser reutilizable en más de un proyecto además de una colección
de componentes interactivos que suelen estar presentes en una amplia variedad de
páginas, a dicha colección reutilizable se le denomina **Framework CSS\***.

Usar un framework de CSS puede tener una curva de aprendizaje al inicio que tal
vez te de la sensación que te toma más tiempo que hacer tu proyecto con CSS, sin
embargo, una vez que _le agarres el truco_ verás que tu velocidad de desarrollo
irá incrementando poco a poco. Algo a tener en cuenta es que como la apariencia
de los componentes de cara a las necesidades de los proyectos pueden ser muy
variadas, existen varios frameworks de CSS, que dependiendo de tu proyecto puedes
utilizar, aquí te listamos algunos de los más usados a la fecha:

- [Bootstrap](https://getbootstrap.com/)
- [Materialize](https://materializecss.com/)
- [Foundation](https://get.foundation/)
- [Bulma](https://bulma.io/)
- [Semantic UI](https://semantic-ui.com/)
- [Tailwind CSS](https://tailwindcss.com/)

Como verás, existen más opciones a las que listamos aquí, pero estas suelen ser
de las más usadas, cuando revises cada una de ellas, verás algunas similitudes
en la galería de componentes que tienen disponibles, pero a su vez notarás
diferencias en la apariencia de las mismas. Para nuestro proyecto, usaremos
Bootstrap y a continuación estas son las razones:

- Es un framework muy usado al día de hoy.
- La base de componentes con las que cuenta hace que migrar a otro Framework sea
  un proceso más sencillo.
- Tiene aun buena demanda en el mercado.

Adicionalmente, Bootstrap es un framework desarrollado por Twitter que tiene una
comunidad grande debido al gran uso que tiene en muchos proyectos de diversa
índole, dado esto, hace que las dudas que puedan surgir para lograr ciertos
objetivos sea más sencillo debido al soporte de la comunidad.

#### Guía: Agregando estilos de Bootstrap al proyecto

Ahora que ya sabemos que vamos a usar un framework de CSS y que será Bootstrap,
necesitamos agregarlo a nuestro proyecto para empezar a usarlo.

La forma de agregar Boostrap es a través de links externos que hacen referencia
a un archivo de CSS y algunos archivos de **JavaScript**. Este término puede que
sea nuevo o tal vez lo recuerdes desde el prework de la primera sesión. En
cualquier caso, JavaScript es el único lenguaje de programación que el navegador
soporta nativamente, y es el lenguaje que nos permite agregar interacción y
funcionalidad a nuestra web. En este curso, no estaremos programando en
JavaScript, pero dado que Bootstrap lo usa para ciertos componentes, lo usaremos
a través del framework sin que nosotros necesariamente tengamos que programar.

Empecemos agregando solo el CSS, para esto, debemos ingresar a la sección de
[empezar con Bootstrap](https://getbootstrap.com/docs/4.4/getting-started/introduction/#css),
en el apartado de `CSS` encontraremos una etiqueta `<link />` con una sintaxis
similar a la que nosotros usamos para indicarle a nuestro HTML dónde encontrar
los estilos de nuestra web. Vamos a copiar toda esa línea de código y la vamos
a pegar en nuestro `index.html`. La ubicación en la cual lo peguemos es
importante, dado que `CSS` al ser un lenguaje en cascada, si coincide algún
nombre de clase que usa Boostrap con alguna que nosotros estamos, podríamos
terminar sobreescribiendo los nombres y el que prevalezca dependerá del orden en
el que encuentre nuestras hojas de estilo.

Por lo tanto, nosotros queremos agarrar la mayoría de estilos que Bootstrap nos
trae consigo, pero en caso algo no esté alineado con nuestro diseño, debemos de
personalizarlo, por ello pondremos primero el `<link />` de Bootstrap seguido
por el nuestro, quedando algo como:

```html
<head>
  <!-- Aquí van las otras etiquetas del head -->
  <link
    rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
    integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh"
    crossorigin="anonymous"
  />
  <link rel="stylesheet" type="text/css" href="./styles.css" />
</head>
```

#### Concepto: Etiqueta `<link />`

En las primeras sesiones habíamos revisado la etiqueta `<link />` y alguno de
sus atributos como `rel`, `type` y `href`. Sin embargo, en la nueva etiqueta que
acabamos de añadir, usa un par de atributos más (`integrity` y `crossorigin`).

Ambos atributos son usados para implementar una funcionalidad de seguridad
llamada [integridad de subrecurso](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity)
que permiten asegurar que el recurso (CSS) pueda ser obtenido correctamente y no
sufra ningún problema de seguridad cuando el navegador lo descargue en nuestra
página web. Para mayor detalle, puedes revisar [esta respuesta en Stackoverflow](https://stackoverflow.com/questions/32039568/what-are-the-integrity-and-crossorigin-attributes).

---

Con esta etiqueta añadida, ya tenemos los estilos de Bootstrap a nuestra
disposición. Ahora practiquemos el concepto de [refactorización](https://es.wikipedia.org/wiki/Refactorizaci%C3%B3n).

### Refactorizando la barra de navegación

Bootstrap viene con un conjunto de componentes, entre los cuales encontramos la
[barra de navegación](https://getbootstrap.com/docs/4.4/components/navbar/) que
tiene la particularidad de funcionar responsivamente, volviendo el menú de
navegación en una hamburguesa cuando se encuentra en un dispositivo pequeño.

#### Guía: Agregando el navbar

Comencemos por comentar la barra de navegación que actualmente tenemos para
evitar que se mezcle con la barra de navegación de Bootstrap.

```html
<body>
  <!-- Esto es lo que se verá en el navegador web -->
  <!-- <section class="fixed-header">
    <header class="header">
      <a href="/" class="logo">
        <img
          src="https://getmatcha.com/wp-content/themes/getmatcha/img/footer_logo.svg"
          alt="Matcha"
        />
      </a>
      <nav class="navbar">
        <ul class="menu">
          <li class="menu-item">Platform</li>
          <li class="menu-item">Pricing</li>
          <li class="menu-item">Customers</li>
          <li class="menu-item">Resources</li>
          <li class="menu-item">About</li>
        </ul>
      </nav>
      <div class="actions">
        <a>Sign In</a>
        <button>Start free trial</button>
      </div>
    </header>
  </section> -->
</body>
```

De tal forma podemos agregar la [barra de navegación de ejemplo](https://getbootstrap.com/docs/4.4/components/navbar/#supported-content)
que nos da Bootstrap y adaptarla a lo que nosotros necesitamos:

```html
<body>
  <!-- Nuestra barra de navegación comentada va aquí -->
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">Navbar</a>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link" href="#"
            >Home <span class="sr-only">(current)</span></a
          >
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a
            class="nav-link dropdown-toggle"
            href="#"
            id="navbarDropdown"
            role="button"
            data-toggle="dropdown"
            aria-haspopup="true"
            aria-expanded="false"
          >
            Dropdown
          </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">Action</a>
            <a class="dropdown-item" href="#">Another action</a>
            <div class="dropdown-divider"></div>
            <a class="dropdown-item" href="#">Something else here</a>
          </div>
        </li>
        <li class="nav-item">
          <a
            class="nav-link disabled"
            href="#"
            tabindex="-1"
            aria-disabled="true"
            >Disabled</a
          >
        </li>
      </ul>
      <form class="form-inline my-2 my-lg-0">
        <input
          class="form-control mr-sm-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
        />
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">
          Search
        </button>
      </form>
    </div>
  </nav>
</body>
```

Debería verse algo similar a:

![Barra de navegación de ejemplo de Bootstrap agregada](./assets/bootstrap-default-navbar.png)

¡Vamos a adaptarla a lo que necesitamos!

#### Challenge: Personaliza el contenido de tu navbar

Cambia el texto usado en el navbar por defecto al contenido que actualmente
tenemos en nuestra página.

<details>
  <summary>Posible solución</summary>

```html
<body>
  <!-- Nuestra barra de navegación comentada va aquí -->
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <a class="navbar-brand" href="#">
      <img
        src="https://getmatcha.com/wp-content/themes/getmatcha/img/footer_logo.svg"
        alt="Matcha"
      />
    </a>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link" href="#">Platform</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Pricing</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Customers</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Resources</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">About</a>
        </li>
      </ul>
      <form class="form-inline my-2 my-lg-0">
        <a>Sign In</a>
        <button>Start free trial</button>
      </form>
    </div>
  </nav>
</body>
```

Viéndose algo como:

![Barra de navegación de Bootstrap con contenido](./assets/bootstrap-default-navbar-with-content.png)

</details>

Si bien ya tenemos el contenido correspondiente a nuestra barra de navegación,
hay detalles notorios en la apariencia que se perdieron con la introducción de
Bootstrap, así que ahora procederemos a corregirlo para que recupere la
apariencia que tenía antes que usemos Bootstrap.

#### Guía: Recuperando los estilos de la barra de navegación

Comencemos por indicarle a la barra de navegación que ocupe todo el ancho de la
pantalla para que no se quede cortado como está en este momento.

Si analizamos los estilos que tiene la etiqueta `nav`, nos daremos cuenta que
tiene un estilo que limita su ancho al 70% del ancho de su contendor:

![Estilos de la barra de navegación](./assets/devtools-navbar.png)

Y como bien indica las herramientas de desarrollo, son estilos que se aplicaron
en el archivo `styles.css` que nosotros creamos.

:::tip

¿Por qué se puede haber originado este error? Resulta que Bootstrap utiliza una
clase llamada `navbar` para ponerle sus propios estilos, y nosotros
coincidentemente usamos el mismo hombre, sin embargo, al momento de nosotros
poner los estilos de Bootstrap antes que el nuestro (al momento que pusimos las
etiquetas `<link />` en el HTML), nuestros estilos terminan predominando sobre
los de Bootstrap a pesar de tener el mismo nombre.

:::

Eliminando el ancho de la clase `.navbar` quedaría así:

```css
.navbar {
  text-align: center;
  color: #025157;
  font-weight: 500;
}
```

Resultando en la barra de navegación tomando el ancho disponible del contenedor:

![Barra de navegación con el ancho habitual](./assets/navbar-width.png)

Lo siguiente que corregiremos será el color, ya que ha tomado un color gris que
la mayoría de componentes de Bootstrap usa por defecto. Para esto, no es
necesario sobreescribir los estilos en la clase `.navbar` ya que en si, el color
de fondo viene dada po una clase utilitaria de Bootstrap que nosotros pegamos
en nuestro código al usar el ejemplo de la documentación oficial de Bootstrap.

Dicha clase es `bg-light` que está añadida a la etiqueta `<nav></nav>`.
Quitándola de la lista de clases que tiene esta etiqueta, recuperaremos el color
original de la barra.

Quedando nuestra etiqueta nav de la siguiente forma:

```html
<nav class="navbar navbar-expand-lg navbar-light">
  <!-- resto del código -->
</nav>
```

:::tip

Si deseas saber que otras clases relacionadas con los colores de fondo existen
en Bootstrap, puedes consultar [esta sección de la documentación](https://getbootstrap.com/docs/4.4/utilities/colors/#background-color).

:::

Ahora procedamos a corregir el alineamiento del menú de navegación, ya que
aparece apegada al logo en la parte izquierda de la pantalla y debería de estar
alineado al centro del espacio disponible del contenedor. Para esto, debemos de
modificar los estilos de la etiqueta `<ul></ul`. Dicha etiqueta en estos
momentos tiene 2 clases (`navbar-nav` y `mr-auto`), la primera clase `navbar-nav`
es importante para poder indicar que los elementos de dicha lista son los que
conformarán el menú de navegación, mientras que la segunda clase `mr-auto` indica
que dicha lista debe tener un margen derecho automático, y dado que los elementos
de la lista Bootstrap les asigna un `display: block;` podemos alinear su
contenido aplicando un margen automático a cada lado, Bootstrap nos permite hacer
dicho comportamiento a través de una clase llamada `mx-auto`. Por lo tanto,
reemplazaremos la clase `mr-auto` por `mx-auto`:

```html
<ul class="navbar-nav mx-auto">
  <!-- lista del menú de navegación -->
</ul>
```

:::tip

Si deseas saber qué otras clases utilitarias relacionas a espaciado que tiene
Bootstrap para ti, puedes revisar [esta sección de la documentación](https://getbootstrap.com/docs/4.4/utilities/spacing/).

:::

Resultando en:

![Menú de navegación centrado](./assets/navbar-centered.png)

Para terminar de cambia la barra de navegación a como estaba originalmente, nos
falta corregir los estilos de la sección de acciones, y si analizamos un poco
los estilos que teníamos anteriormente, nos daremos cuenta que sus estilos
dependían de la clase de su contenedor llamada `actions`. Así que para no
sobreescribir ningún estilo o escribir una clase nueva, podemos tomar la clase
que nosotros habíamos creado y agregársela a las clases que actualmente tiene el
formulario, resultando de la siguiente manera:

```html
<form class="form-inline my-2 my-lg-0 actions">
  <!-- acciones -->
</form>
```

Como último detalle de las acciones, podemos notar que el espacio que existe
hacia el lado derecho entre el botón y el borde del navegador es más grande que
el espacio entre el logo y el borde izquierdo del navegador. Esto sucede debido
a que la clase `form-inline` convierte al formulario en un _flex container_ y le
asigna que debe estar el contenido alineado al centro horizontalmente, mientras
que nosotros necesitaríamos que se alínea hacia el final de su eje horizontal,
normalmente lograríamos esto usando `justify-content: flex-end;`, dado que
usamos Bootstrap, podemos hacer uso de una clase llamada `justify-content-end`:

```html
<form class="form-inline my-2 my-lg-0 actions justify-content-end">
  <!-- acciones -->
</form>
```

:::tip

Si deseas saber qué otras clases relacionadas a Flexbox tiene Bootstrap para ti,
puedes revisar [esta sección de la documentación](https://getbootstrap.com/docs/4.4/utilities/flex/#justify-content).

:::

Con estos cambios la mayoría de estilos debería de volver a verse similar a como
lo teníamos antes:

![Barra de navegación con estilos](./assets/navbar-styled.png)

#### Challenge: Revisando el responsive de las acciones del navbar

Si comenzamos por cambiar el tamaño del navegador a uno más pequeño, llegaremos
a un punto en el que nuestra barra de navegación se rompe:

![Estilos de acciones en el navbar rotos](./assets/broken-navbar-actions.png)

<details>
  <summary>Posible solución</summary>

En este caso, el problema viene dado por que la clase `actions` tiene una
propiedad `width` asignándola al 15% del tamaño de su contenedor, y dado que
Bootstrap está usando Flexbox para manejar el ancho de sus elementos, no es
necesaria dicha propiedad. Así que una solución es eliminar dicha propiedad,
quedando la clase `actions` de la siguiente manera:

```css
.actions {
  text-align: right;
  font-weight: 600;
  font-size: 14px;
}
```

</details>

#### Guía: Revisando el responsive del navbar

Si activamos el emulador de responsive para nuestra web veremos que un
comportamiento diferente sucede en nuestra barra de navegación:

![Responsive navbar](./assets/responsive-navbar.png)

¡La barra de navegación no aparece 😱!

Si revisamos los estilos en el devtools, nos daremos cuenta que hay un media
query que se está aplicando a las clases `navbar` y `actions` indicando que
tenga un `display: none;`, así que para solucionar este problema, procederemos
a borrar ese estilo de nuestro media query.

![Responsive navbar mostrándose otra vez](./assets/responsive-navbar-2.png)

Notaremos que ahora tenemos una especie de ícono (comunmente llamado
_menú hamburguesa_) que al darle click debería de mostrarnos el menú, pero dicha
característica aun no funciona. ¿A qué se puede deber?

#### Concepto: Interactividad con JavaScript

Es en este punto donde nos toca hablar de JavaScript. Recordando lo visto en la
primera sesión, habíamos indicado que principalmente existen 3 lenguajes
utilizados en el lado del Front-end: HTML, CSS y JavaScript. Hasta el momento,
nosotros hemos implementado HTML y CSS. Sin embargo, JavaScript, es el que tiene
el poder de agrega dinamismo a una página web. Esto quiere decir que con este
lenguaje de programación nosotros podemos agregar reacción a eventos (por ejemplo,
cuando damos clic a un botón y queremos que mande un mensaje o muestre una
sección oculta), entre muchas otras funcionalidades.

Dado que ahora nosotros queremos que un menú que no está visible se muestre al
darle click a un ícono de menú hamburguesa, esto solo es posible a través de
JavaScript, sin embargo, Bootstrap ha intentado abstraer toda esa funcionalidad
que es común en páginas webs para que nosotros con solo importar su código fuente
podemos obtener toda esa funcionalidad sin escribir una sola línea de JavaScript.

#### Guía: Agregando scripts de Bootstrap para interactividad

En la sección de inicio de la documentación de Bootstrap, nosotros encontramos
los links para el código fuente del CSS de este framework y los agregamos a
nuestro HTML. Lo mismo sucede con JavaScript. En esta ocasión, nosotros no
queremos agregar el CSS de Bootstrap, ahora queremos agregar el JS que este
framework nos provee. Para esto, podemos ir a [esta sección de la documentación](https://getbootstrap.com/docs/4.4/getting-started/introduction/#js)
y copiar los 3 scripts que se listan.

Ahora la pregunta, es dónde lo insertamos en el HTML, ¿en la etiqueta HEAD puesto
que es algo que no se ve? Si bien el razonamiento es completamente válido y
lógico 🤓, existen otras implicaciones relacionadas al rendimiento de una página
web que hace que insertarlo en otra ubicación nos pueda ayudar a tener una mejor
experiencia de usuario.

Donde lo vamos a posicionar es antes de cerrar la etiqueta `</body>` y después de
la última etiqueta que se encuentre dentro de esta.

```html
<body>
  <!-- Todo el código de nuestro HTML viene aquí -->
  <script
    src="https://code.jquery.com/jquery-3.4.1.slim.min.js"
    integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n"
    crossorigin="anonymous"
  ></script>
  <script
    src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
    integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo"
    crossorigin="anonymous"
  ></script>
  <script
    src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js"
    integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6"
    crossorigin="anonymous"
  ></script>
</body>
```

:::tip

Si quieres conocer los fundamentos de porqué es mejor ingresar la etiqueta
`<script></script>` antes de cerrar el body del HTML, puedes leer esta
[pregunta y respuesta de Stack Overflow](https://es.stackoverflow.com/questions/25088/cu%C3%A1l-es-el-mejor-lugar-para-colocar-los-tag-scripts-src-en-html).

:::

Si recargas ahora la página, al darle click al menú hamburguesa desde la vista
de un móvil, ¡verás que funciona! 😉.

#### Challenge: Corrige el menú desplegado en un móvil

Ahora con el menú funcionando en dispositivos pequeños, notaremos que la
alineación de las opciones y tal vez el color del texto no se logra a percibir
muy bien, para esto puedes usar algunos estilos en el media query para adaptarlo
como tu prefieras.

![Menú responsive desplegado](./assets/responsive-menu.png)

<details>
  <summary>Posible solución</summary>

Este reto es libre, por ejemplo, en nuestro caso cambiamos el color de fuente de
cada uno de los items del menú para un mejor contraste y cambiamos el color del
menú hamburguesa.

```css
.navbar-light .nav-item .nav-link {
  color: #025157;
}

.navbar-light .navbar-toggler {
  border-color: #025157;
}

.navbar-light .navbar-toggler-icon {
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='0 0 30 30'%3e%3cpath stroke='rgb(3, 81, 77)' stroke-linecap='round' stroke-miterlimit='10' stroke-width='2' d='M4 7h22M4 15h22M4 23h22'/%3e%3c/svg%3e");
}
```

</details>

#### Challenge: Volviendo la barra de navegación fija

Recuerdas que la barra de navegación tenía un posicionamiento fijo para que esta
nos acompañe cuando hagamos scroll dentro de la página. ¿Has notado que este
comportamiento ya no está presente? ¿Puedes solucionarlo?

:::tip

Al ser este un caso común, Bootstrap tiene clases utilitarias que pueden ayudar
a lograr este comportamiento. Revisa [esta sección de navbar de la documentación](https://getbootstrap.com/docs/4.4/components/navbar/#placement)
para que te des una idea de qué podrías usar.

:::

<details>
  <summary>Posible solución</summary>

La clase `fixed-top` de Bootstrap nos ayuda a solucionar este problema:

```html
<nav class="navbar navbar-expand-lg navbar-light fixed-top">
  <!-- Contenido de la barra de navegación -->
</nav>
```

Si bien nuestra barra se posiciona como queremos, al momento de hacer scroll nos
damos cuenta que no tiene un color de fondo porque el texto se mezcla con el
resto del contenido de la página. Para esto, podemos agregale un color de fondo
en la clase `.navbar` que tenemos sobreescrita en nuestros estilos:

```css
.navbar {
  background-color: #fffbf7;
  text-align: center;
  color: #025157;
  font-weight: 500;
```

</details>

Ya con esto, podemos proceder a limpiar nuestro HTML y CSS eliminando los
elementos que comentamos en un inicio y los estilos que hemos dejado de usar.

Eso significa que debemos de borrar en el HTML:

```html
<!-- <section class="fixed-header">
  <header class="header">
    <a href="/" class="logo">
      <img
        src="https://getmatcha.com/wp-content/themes/getmatcha/img/footer_logo.svg"
        alt="Matcha"
      />
    </a>
    <nav class="navbar">
      <ul class="menu">
        <li class="menu-item">Platform</li>
        <li class="menu-item">Pricing</li>
        <li class="menu-item">Customers</li>
        <li class="menu-item">Resources</li>
        <li class="menu-item">About</li>
      </ul>
    </nav>
    <div class="actions">
      <a>Sign In</a>
      <button>Start free trial</button>
    </div>
  </header>
</section> -->
```

Y los siguientes estilos:

```css
.fixed-header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: #fffbf7;
  z-index: 1;
}

.header {
  margin-top: 40px;
  margin-left: 20px;
  margin-right: 20px;
  font-size: 0;
  height: 45px;
  font-family: sans-serif;
}

.header > * {
  display: inline-block;
  font-size: 16px;
  height: 100%;
  vertical-align: middle;
  line-height: 45px;
}

.logo {
  width: 15%;
}

.menu-item {
  display: inline;
  margin-right: 25px;
  margin-left: 25px;
}
```

### Agregando carousel de casos de éxito

En un postwork anterior, habíamos indicado que se realice la estructura de la
sección de casos de éxito usando Flexbox, sin embago, hicimos la acotación de que
la parte del slider no se haga aun, esto debido a que en esta sesión veríamos
cómo realizarlo con Bootstrap.

#### Guía: Agregando carousel de Bootstrap

Al igual que con el navbar, Bootstrap cuenta con un [componente de Carousel](https://getbootstrap.com/docs/4.4/components/carousel/)
que nos permitirá cambiar automáticamente los casos de éxito. Para esto,
comencemos por comentar nuestro código actual del carousel de casos de éxito:

```html
<article class="stories-carousel">
  <!-- <div class="card">
    <div class="card-media">
      <figure>
        <img
          src="https://getmatcha.com/wp-content/uploads/2019/05/profile-headshot-square.png"
          alt="Everly worker"
        />
      </figure>
      <div class="company">
        <img
          src="https://getmatcha.com/wp-content/uploads/2019/05/everly_logo_blue_v3_x60@2x.png"
          alt="Everly"
        />
      </div>
    </div>
    <div class="card-body">
      <h4>Everly</h4>
      <h3>
        Early-Stage CPG Brand Increases Lead Conversion 20x, Ecommerce
        Revenue 20%
      </h3>
      <div class="results">
        <img
          src="https://getmatcha.com/wp-content/themes/getmatcha/img/icon_cart.png"
          alt="Cart icon"
        />
        <p>22% of monthly revenue influenced by content</p>
      </div>
    </div>
    <div class="card-footer">
      <button>See Case Study</button>
    </div>
  </div> -->
</article>
```

Y agreguemos el [código de ejemplo de Bootstrap](https://getbootstrap.com/docs/4.4/components/carousel/#with-indicators),
agregaremos ese ejemplo en particular porque tiene los indicadores que
permitirán manipular el slide que se quiere ver a través de un click:

```html
<article class="stories-carousel">
  <!-- Aquí debería estar el código que acabamos de comentar -->
  <div
    id="carouselExampleIndicators"
    class="carousel slide"
    data-ride="carousel"
  >
    <ol class="carousel-indicators">
      <li
        data-target="#carouselExampleIndicators"
        data-slide-to="0"
        class="active"
      ></li>
      <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
      <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
    </ol>
    <div class="carousel-inner">
      <div class="carousel-item active">
        <img src="..." class="d-block w-100" alt="..." />
      </div>
      <div class="carousel-item">
        <img src="..." class="d-block w-100" alt="..." />
      </div>
      <div class="carousel-item">
        <img src="..." class="d-block w-100" alt="..." />
      </div>
    </div>
    <a
      class="carousel-control-prev"
      href="#carouselExampleIndicators"
      role="button"
      data-slide="prev"
    >
      <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a
      class="carousel-control-next"
      href="#carouselExampleIndicators"
      role="button"
      data-slide="next"
    >
      <span class="carousel-control-next-icon" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
</article>
```

Buscando entender el contenido del HTML del ejemplo de Bootstrap, podemos ver
que primero tenemos una lista ordenada (`<ol></ol>`), dicha lista son los
indicadores que se ven como líneas sobre la imagen para indicar cuál es la que
se está mostrando y cuántos elementos hay dentro del carousel. Seguido
encontramos el `div.carousel-inner` que contiene 3 divs con clase `carousel-item`
que contiene cada uno de los elementos del carousel dentro (en este caso las
etiquetas `<img />`). Por último están 2 enlaces que representan las flechas que
se sobreponen sobre los elementos del carousel para controlar manualmente si
queremos avanzar o retroceder en el carousel.

#### Challenge: Cambiando el contenido del carousel

Una vez revisado la estructura del ejemplo de Bootstrap, debemos de cambiar el
contenido del carousel para que contenga lo que nosotros teníamos. No te
preocupes si los estilos no quedan perfecto, de momento solo nos enfocaremos en
que en vez de imágenes rotas girando en el carousel, debe de ser el contenido que
nosotros estamos esperando ver al final.

:::tip

Recuerda en qué sección del código del ejemplo se ponen los elementos del
carousel para que pongas el código que hemos comentado previamente. Por último,
recuerda que nosotros solo teníamos las imágenes y texto de uno de los elementos
del carousel, usa tus habilidades del manejo de las herramientas de desarrollo
del desarrollo para obtener las imágenes.

:::

<details>
  <summary>Posible solución</summary>

Se debe de reemplazar las imágenes dentro de cada contenedor con clase
`carousel-item` por el contenido que tenemos comentado.

```html
<div class="carousel-inner">
  <div class="carousel-item active">
    <div class="card">
      <div class="card-media">
        <figure>
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/profile-headshot-square.png"
            alt="Everly worker"
          />
        </figure>
        <div class="company">
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/everly_logo_blue_v3_x60@2x.png"
            alt="Everly"
          />
        </div>
      </div>
      <div class="card-body">
        <h4>Everly</h4>
        <h3>
          Early-Stage CPG Brand Increases Lead Conversion 20x, Ecommerce Revenue
          20%
        </h3>
        <div class="results">
          <img
            src="https://getmatcha.com/wp-content/themes/getmatcha/img/icon_cart.png"
            alt="Cart icon"
          />
          <p>22% of monthly revenue influenced by content</p>
        </div>
      </div>
      <div class="card-footer">
        <button>See Case Study</button>
      </div>
    </div>
  </div>
  <div class="carousel-item">
    <div class="card">
      <div class="card-media">
        <figure>
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/profile-headshot-square.png"
            alt="Everly worker"
          />
        </figure>
        <div class="company">
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/everly_logo_blue_v3_x60@2x.png"
            alt="Everly"
          />
        </div>
      </div>
      <div class="card-body">
        <h4>Everly</h4>
        <h3>
          Early-Stage CPG Brand Increases Lead Conversion 20x, Ecommerce Revenue
          20%
        </h3>
        <div class="results">
          <img
            src="https://getmatcha.com/wp-content/themes/getmatcha/img/icon_cart.png"
            alt="Cart icon"
          />
          <p>22% of monthly revenue influenced by content</p>
        </div>
      </div>
      <div class="card-footer">
        <button>See Case Study</button>
      </div>
    </div>
  </div>
  <div class="carousel-item">
    <div class="card">
      <div class="card-media">
        <figure>
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/profile-headshot-square.png"
            alt="Everly worker"
          />
        </figure>
        <div class="company">
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/everly_logo_blue_v3_x60@2x.png"
            alt="Everly"
          />
        </div>
      </div>
      <div class="card-body">
        <h4>Everly</h4>
        <h3>
          Early-Stage CPG Brand Increases Lead Conversion 20x, Ecommerce Revenue
          20%
        </h3>
        <div class="results">
          <img
            src="https://getmatcha.com/wp-content/themes/getmatcha/img/icon_cart.png"
            alt="Cart icon"
          />
          <p>22% of monthly revenue influenced by content</p>
        </div>
      </div>
      <div class="card-footer">
        <button>See Case Study</button>
      </div>
    </div>
  </div>
</div>
```

Y luego cambiar el texto e imágenes de los siguientes elementos en el carousel:

```html
<div class="carousel-inner">
  <div class="carousel-item active">
    <div class="card">
      <div class="card-media">
        <figure>
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/profile-headshot-square.png"
            alt="Everly worker"
          />
        </figure>
        <div class="company">
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/05/everly_logo_blue_v3_x60@2x.png"
            alt="Everly"
          />
        </div>
      </div>
      <div class="card-body">
        <h4>Everly</h4>
        <h3>
          Early-Stage CPG Brand Increases Lead Conversion 20x, Ecommerce Revenue
          20%
        </h3>
        <div class="results">
          <img
            src="https://getmatcha.com/wp-content/themes/getmatcha/img/icon_cart.png"
            alt="Cart icon"
          />
          <p>22% of monthly revenue influenced by content</p>
        </div>
      </div>
      <div class="card-footer">
        <button>See Case Study</button>
      </div>
    </div>
  </div>
  <div class="carousel-item">
    <div class="card">
      <div class="card-media">
        <figure>
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/08/0.jpg"
            alt="Seato Summit worker"
          />
        </figure>
        <div class="company">
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/08/SeatoSummitLogo.png"
            alt="Seato Summit Logo"
          />
        </div>
      </div>
      <div class="card-body">
        <h4>Sea to Summit</h4>
        <h3>
          Sea to Summit’s Ecommerce Site Traffic Climbs 189%, New Subscribers
          820%
        </h3>
        <div class="results">
          <img
            src="https://getmatcha.com/wp-content/themes/getmatcha/img/icon_audiences.png"
            alt="Audience icon"
          />
          <p>500% increase in traffic from social media</p>
        </div>
      </div>
      <div class="card-footer">
        <button>See Case Study</button>
      </div>
    </div>
  </div>
  <div class="carousel-item">
    <div class="card">
      <div class="card-media">
        <figure>
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/06/matt-and-margaret_headshot.png"
            alt="Mambe workers"
          />
        </figure>
        <div class="company">
          <img
            src="https://getmatcha.com/wp-content/uploads/2019/06/mambe-logo-1.png"
            alt="Mambe"
          />
        </div>
      </div>
      <div class="card-body">
        <h4>Mambe Waterproof Blankets</h4>
        <h3>
          How Mambe Increased Conversions by 327%, Reduced CPL by 60%
        </h3>
        <div class="results">
          <img
            src="https://getmatcha.com/wp-content/themes/getmatcha/img/icon_target.png"
            alt="Target icon"
          />
          <p>+327% more popup conversions at a 60% lower cost</p>
        </div>
      </div>
      <div class="card-footer">
        <button>See Case Study</button>
      </div>
    </div>
  </div>
</div>
```

</details>

Luego de aplicado los cambios debería quedarr algo similar a:

![Carousel de casos de éxito](./assets/carousel-with-content.png)

Con esto, podemos detectar ciertos detalles que debemos corregir en la
apariencia:

- La flecha de siguiente se sale de la tarjeta y probablemente no la necesitamos.
- Los indicadores no se logran ver aunque no los hemos borrado del código.
- La tarjeta tiene espacios en blanco en la parte superior e inferior.
- El color del botón para ver el caso de estudio tiene un color de fondo que
  antes no tenía.

Procedamos a corregir estos detalles 😎.

#### Guía: Eliminando flechas de control de carousel

Las flechas no las necesitamos y no están encajando bien en el comportamiento
por defecto de nuestro carousel, así que podemos eliminarlos. Como lo habíamos
analizado previamente, las flechas son los elementos `<a></a>` que estaban al
final del carousel, asegúrate de eliminarlos del código:

```html
<a
  class="carousel-control-prev"
  href="#carouselExampleIndicators"
  role="button"
  data-slide="prev"
>
  <span class="carousel-control-prev-icon" aria-hidden="true"></span>
  <span class="sr-only">Previous</span>
</a>
<a
  class="carousel-control-next"
  href="#carouselExampleIndicators"
  role="button"
  data-slide="next"
>
  <span class="carousel-control-next-icon" aria-hidden="true"></span>
  <span class="sr-only">Next</span>
</a>
```

#### Guía: Cambiando de posición a los indicadores del carousel

El siguiente problema a solucionar son los indicadores, ya que estos en realidad
están en la interface, pero dado que por defecto son de color blanco y se
posicionan sobre los elementos del carousel, estos no se logran ver. Podemos
analizar sus estilos por defecto en el devtools:

![Estilos de los indicadores del carousel](./assets/carousel-indicators.png)

Lo que se puede notar de acá es que el valor de la propiedad `position` es
`absolute`, lo cual hace que salga del flujo original del documento, y a través
de la propiedad `bottom: 0` logra ubicarlo en la parte inferior de la tarjeta que
tiene una posición diferente a `static`.

Para poder ubicar los indicadores debajo de los elementos de carousel debemos de
sobreescribir la propiedad `position`:

```css
.success-stories .stories-carousel .carousel-indicators {
  position: initial; /** ó: position: static; */
}
```

:::tip

El valor `initial` hace que la propiedad asignada tome el valor inicial que esta
propiedad fue asignada. Para mayor información puedes consultar la
[documentación oficial de MDN](https://developer.mozilla.org/es/docs/Web/CSS/initial).

:::

Con esto, deberíamos lograr tener un resultado simila a:

![Indicadores de carousel con position static](./assets/carousel-indicators-position.png)

Si bien los indicadores ahora ya no se encuentran sobre la imagen, aparecen en
la parte superior del carousel, esto debido a que respeta el flujo del documento
y en el HTML la lista ordenada de indicadores viene escrita antes de los
elementos del carousel, por lo que tendremos que invertir el orden resultando en
algo como:

```html
<article class="stories-carousel">
  <div
    id="carouselExampleIndicators"
    class="carousel slide"
    data-ride="carousel"
  >
    <div class="carousel-inner">
      <!-- Elementos del carousel van aquí -->
    </div>
    <ol class="carousel-indicators">
      <li
        data-target="#carouselExampleIndicators"
        data-slide-to="0"
        class="active"
      ></li>
      <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
      <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
    </ol>
  </div>
</article>
```

Después de este cambio, la posición de los indicadores estará correcta pero aun
veremos que aparenta no estar centrada. Este problema puede deberse a que el
contenedor de los indicadores está tomando un ancho diferente al de las tarjetas.
Y si revisamos los estilos de la clase `.card` encontraremos lo siguiente:

```css
.success-stories .stories-carousel .card {
  max-width: 370px;
  width: 100%;
  background-color: #fff;
  border-radius: 10px;
}
```

Hay un ancho máximo definido, que dependiendo del tamaño de la pantalla que lo
estemos viendo, nos podremos topar con este detalle. Dado que esta propiedad
está indicando que si el ancho del contenedor supera los 370px, se deberá
aplicar esta medida. Si bien es algo que permite una buena apariencia, está
definida en un lugar erróneo, dado que al aplicarse solo a las tarjetas, los
indicadores no toman la misma medida. Podríamos optar por aplicarle la misma
propiedad a los indicadores, pero mejor aun podríamos establer dicha propiedad
a un elemento que contenga tanto a los elementos del carousel como a los
indicadores. Este elemento puede ser el div con clase `carousel` dado que
contiene a todos los elementos que forman parte del carousel y eliminar la
propiedad del elemento `div.card`:

```css
.success-stories .stories-carousel .carousel {
  max-width: 370px;
}

.success-stories .stories-carousel .card {
  width: 100%;
  background-color: #fff;
  border-radius: 10px;
}
```

#### Challenge: Cambiando los estilos de los elementos del carousel

¡Yay! Ya tenemos casi listo nuestro carousel y con interactividad gracias a
Bootstrap. Ahora es tu turno de darle los toques finales. Elimina los espacios
en blanco dentro de las tarjetas y cambia el color y el borde que engloca al
botón de ver los casos de éxito.

<details>
  <summary>Posible solución</summary>

Para eliminar el espacio superior entre la imagen y el borde de la tarjeta,
debemos de eliminar el `margin-top` que todos los elementos `<figure></figure>`
tienen.

```css
.success-stories .stories-carousel figure {
  margin-top: 0;
}
```

Y para elimianr el borde y color de fondo del botón en la parte inferior,
debemos de sobreescribir las propiedads de `background-color` y `border-color`
que Bootstrap le puso por coincidir en el nombre de clase que usan. Para lograr
esto, podemos agregar las propiedades a los estilos que tenemos de la clase
`card-footer`:

```css
.success-stories .stories-carousel .card .card-footer {
  margin-bottom: 20px;
  background-color: transparent;
  border-color: transparent;
}
```

</details>

Listo, con esto nuestro carousel quedó funcionando y viéndose como lo teníamos
previamente. No te olvides de eliminar el código comentado y dado que utilizamos
todos los estilos que declaramos en la primera versión de este código, no es
necesario eliminar ninguna clase o selector de estilos en el CSS.

### Desplegando nuestros cambios

Esto probablemente ya lo has venido haciendo muchas veces, pero no está demás
recordarlo.

Agrega tus cambios realizados a `git`:

```bash
$ git add -A
```

Agrega un mensaje descriptivo a tu nueva versión:

```bash
$ git commit -m "Agrega componentes de Bootstrap"
```

Sube tus cambios a Github para que tengas un respaldo y siempre lo puedas
descargar en cualquier otro ordenador:

```bash
$ git push origin <nombre-rama> # `master` si no estás trabajando en otra rama
```

Al realizar este último comando tus cambios estarán reflejados en `Netlify` y
podrás revisar tu web publicada en internet, esperando que se vea algo como (o
incluso mucho mejor):

![Resultado de home responsive](./assets/end-result.png)
