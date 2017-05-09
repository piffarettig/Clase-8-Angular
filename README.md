# Angular y el mundo de las SPAs

## Introducción al concepto de Single Page Applications

Esta clase tiene como objetivo introducirlos en el concepto de las SPAs y comenzar a ver a Angular como una tecnología para lograrlo.
Es interesante ver cómo esta "nueva"  forma de contruir aplicaciones web (aunque hoy en día ya tiene sus años) 
se diferencia de las maneras más "tradicionales", teniendo como objetivo entender qué diferencias residen entre una modalidad y otra.

### ¿Cómo funcionaban las web applications tradicionalmente? 

En el pasado, el flujo que exista en una aplicación web era algo así:

1) Se tenía un **Web Server** que provee "al mundo" el contenido de nuestro sitio (html, js, css, etc).
2) Luego, se utilizaba un **Browser** para ir a buscar dicho contenido, a partir de una solicitud HTTP.  Por ejemplo, cada vez que entramos a **http://www.starwars.es/**

En el momento en el que obteníamos la página, nuestro **Browser/Explorador** tenía la lógica para mostrarla (renderizarla), y, en cada interacción/clic/evento subsiguiente que nosotros dispararamos sobre dicho html,
el browser se encargaba de ir a pedir un nuevo .html al Web Server para mostrar el contenido asociado al mismo.

IMAGEN - Intercambio Requests

Este tipo de aplicaciones son conocidas como **Round-Trip Applications** (o **RTAs**).

Durante mucho tiempo, las aplicaciones web se fueron pensando como Round-Trip: el Browser hace el request inicial del documento HTML al servidor, las interacciones del Usuario hacían que el browser solicitara y recibiera un documento HTML completamente nuevo cada vez. En este tipo de aplicación, **el browser es solo una especie de renderer de HTML**, y toda la lógica de la aplicación va del lado del servidor. El browser realiza una serie de Requests HTTP sin estado que el server maneja generando documentos html dinámicamente.

Este modelo, si bien se sigue usando hoy en día, tiene algunas **desventajas**. Por ejemplo:

1) El usuario debe esperar mientras el siguiente documento HTML se genera, requieren mayor infraestructura del lado del servidor para procesar todos los requests y manejar el estado de la aplicación, y requieren más ancho de banda, ya que cada documento HTML debe estar autocontenido.


2) A su vez, la experiencia de usuario se degrada por factores como el efecto de refreshing (pestañeo) y el tiempo en ir a pedir los recursos al servidor.

### ¿Cómo funcionan las SPAs? 

Las *SPAs*, si bien siguen manteniendo la misma forma de interactuar **cliente-servidor**, toman un enfoque diferente. En la petición inicial, un HTML inicial se envía al browser, pero las interacciones del usuario generan requests a través de **AJAX** para pequeños fragmentos de HTML/datos que se insertan en lo que se le muestra al usuario

**El documento HTML inicial nunca se recarga**, y el usuario puede seguir intercalando con el html existente mientras las requests ajax terminan de ejecutarse asincrónicamente.

Particularmente veremos un framework que está 100% orientado a la construcción de SPAs: **Angular**.

El mismo logra logra sus mejores resultados cuando la aplicación a desarrollar se acerca al modelo de **Single-Page**. No quiere decir que no se pueda usar para Round-trip, pero hay otras herramientas, como **jQuery**, que lo hacen mejor.


IMAGEN 2

### Caractersticas de las SPAs 

1) Como ya dijimos, este tipo de Web Apps es conocida porque tienen la posibilidad de redibujar la UI sin tener que realizar una nueva petición (**Round-Trip**) al servidor. 

2) Mejoran la UX por el hecho de que los usuarios tienen una experiencia ininterrumpida, sin que la página se refresque, y sin agregar complejidad. 

3) Son ideales para el mundo tanto web y mobile: no se agrega complejidad desde el lado del servidor para poder servir a diferentes dispositivos o plataformas. la lógica de lograr que nuestras web apps sean "responsive" siempre va desde el lado del cliente (browser), no se cargan nuevas páginas todo el tiempo.

4) Estan 100% alineadas al concepto de las APIs REST, debido a que estas simplemente exponen puntos para transaccionar y/o recibir o devolver datos, de una forma totalmente separada de la forma en que se van a mostrar.

IMAGEN 3

## ¿Qué es Angular?

IMAGEN LOGO ANGULAR

### Introducción

Angular |
------------- | 
Framework de JavaScript | 
Orientado a construir Client-Side Apps  |
Basado en HTML, CSS y JavaScript |

La meta de angular es traer las herramientas y capacidades que han estado disponibles para el desarrollo de back-end al cliente web, facilitando el desarrollo, test y mantenimiento de aplicaciones web complejas y ricas en contenido.

Angular funciona permitiéndonos extender HTML, expresando funcionalidad a través de elementos, atributos, clases y comentarios. 

### ¿Por qué Angular?

* Angular hace que nuestro HTML sea más expresivo, permitiéndole embeber/agregar features y lógica al HTML para lograr un data-binding con nuestros modelos. Esto nos permite mostrar campos que tengan valores de nuestros modelos/datos de forma sencilla, y tener un seguimiento de los mismos (actualización en tiempo real). 


* Angular promueve la modularidad desde su diseño, siendo fácil crear y lograr reuso de los componentes y del contenido.


* Angular a su vez tiene soporte ya incluido para comunicación con servicios de back-end (es fácil que nuestras webs apps se conecten a nuestros backends y ejecuten leogica del lado del servidor).
 
### El problema que Angular quiere resolver

Complejidad de manejar el DOM  y la lógica de una aplicación manualmente.


### Angular 2 vs "Angular 1"

La versión del framework que usaremos es comunmente llamada como "Angular 2", o simplemente, Angular. Esta versión provee una serie de ventajas interesantes respecto a la versión anterior:

1) Es más rápido. Está más optimizado y **corre de 3-5 veces más rápido** que Angular 1 .

2) Es más moderno, y toma en cuenta **features modernas de  JavaScript** que no estaban en otros frameworks de JavaScript (clases, modelos y decorators).

3) Angular 2 tiene una API simple que se engancha con varios exploradores.

4) Mejora la productividad de forma sencilla:  **define patrones y building blocks** para la construcción de web apps.

También podemos realizar una comparativa a más detallada:

IMAGEN TABLA COMPARATIVA.

De aquí en adelante, siempre que hablemos de *Angular*, nos estaremos refiriendo a *Angular 2*.

## Arquitectura de una aplicación Angular

En **Angular **, una aplicación **se define a partir de un conjunto de componentes**, del mismo modo que también de servicios subyacentes que son comunes a ellos  y permiten el reuso de la lógica. Por ejemplo: servicios para contectarse con APIs REST, servicios que manejen la sesión desde el lado del cliente, servicios de autenticación, etc.


IMAGEN ARQUITECTURA ANGULAR 

### Pero… ¿Qué es un componente en Angular?

Un componente es una una unidad modularizada que define la vista y la lógica para controlar una porción de una pantalla en Angular. Cada componente se compone de:

- Un **template (que es el HTML para la UI, tambin llamado la View)**. Sin los datos, por eso un template. Los datos serán inyectados de forma dinámico.


- Una **clase que es el código asociado a la View**, teniendo properties/datos que están disponibles para el uso de las Views, y métodos que son lógica o acciones para dichas views. Por ejemplo: responder a un click de un botón, o a un evento.


- **Metadata**, la cual provee información adicional del componente a Angular. Es lo que identifica a la clase  asociada al componente.

IMAGEN COMPONENTES

### ¿Y cómo hacemos que todos estos componentes se integren en una app en Angular?

Esto lo logramos a partir de lo que se llaman, **Angular Modules**. Estos nos permiten organizar nuestros componentes en funcionalidad cohesiva. Cada app angular tiene por lo menos un Angular Module, llamado el **Root Angular Module**.

Por convención, al Root Module le llamaremos **AppModule** en nuestra Angular app.

Una app puede tener un número de modulos adicionales, incluyendo **‘Feature Angular Modules’**, que los usamos para lograr una funcionalidad en especial. Consolidan un conjunto de componentes para una feature particular de una aplicación.
