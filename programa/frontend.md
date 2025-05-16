
# 💻 Martes: Integración de un frontend al canister 🎨🖌️

<figure><img src="../.gitbook/assets/frontend.png" alt=""><figcaption></figcaption></figure>

El desarrollo frontend en el Internet Computer Protocol (ICP) se centra en la creación de interfaces de usuario  dinámicas para aplicaciones descentralizadas (dApps). Estas interfaces permiten a los usuarios interactuar directamente con canisters (contratos inteligentes) y servicios alojados en la red ICP, ofreciendo experiencias web completamente descentralizadas.

Para facilitar la implementación y el alojamiento de estas interfaces, ICP introduce el concepto de **asset canisters**.
## ¿Qué un Asset Canister?
Un asset canister, también conocido como ``frontend canister``, es un tipo especial de canister diseñado para almacenar y servir activos web estáticos, como archivos HTML, CSS, JavaScript, imágenes y otros recursos necesarios para el frontend de una aplicación. Estos canisters compilan los activos frontend en un módulo WebAssembly (Wasm) que puede ser desplegado y ejecutado en la red ICP. 

La configuración de un asset canister se realiza mediante el archivo ``dfx.json`` del proyecto, donde se define el canister con el tipo "assets". Esto indica a dfx que compile los activos frontend utilizando código base en Rust, que luego se convierte en Wasm para su despliegue.

[🔗📖 Documentación oficial sobre Asset Canisters](https://internetcomputer.org/docs/building-apps/frontends/using-an-asset-canister)

## Lenguajes Compatibles para el Desarrollo de Frontend en ICP

El desarrollo de interfaces para aplicaciones en Internet Computer Protocol (ICP) es altamente flexible, permitiendo a los desarrolladores utilizar una variedad de frameworks modernos y ampliamente adoptados en la industria del desarrollo web. Actualmente el protocolo es compatible con frameworks basados en Node.js. Ejemplo de los mas usados son:

### Vanilla JavaScrip
<img src="../.gitbook/assets/vanilla.png" style="display: block; margin: 0 auto;" width="200"/> 
<br>
<br>

Vanilla JS es la forma más pura de escribir JavaScript, sin el uso de librerías ni frameworks. Es ideal para proyectos livianos, pruebas rápidas o cuando se desea un control total sobre el comportamiento del frontend.
 En ICP, Vanilla JS puede integrarse directamente con un asset canister y comunicarse con canisters backend mediante la librería ``@dfinity/agent``. Su simplicidad también lo hace ideal para comprender cómo funciona la interacción entre el frontend y la infraestructura descentralizada.

[🔗📖 Más información sobre Vanilla.js 🔎](http://vanilla-js.com/)

---
 ### React

<img src="../.gitbook/assets/react.png" style="display: block; margin: 0 auto;" width="200"/>
<br>
<br>

React es una biblioteca declarativa y basada en componentes para construir interfaces de usuario. Su popularidad, ecosistema y flexibilidad lo convierten en una de las mejores opciones para desarrollar frontends sobre ICP.

Utilizando herramientas como Vite o Webpack junto con ``@dfinity/agent`` y ``@dfinity/auth-client``, React permite crear experiencias ricas que se comunican con canisters de forma fluida. Además, al compilar el proyecto para producción (``npm run build``), los archivos generados pueden ser fácilmente desplegados en un asset canister.

[🔗📖 Más información sobre React 🔎](https://es.react.dev/)

---
### Netx.js

<img src="../.gitbook/assets/next.png" style="display: block; margin: 0 auto;" width="300"/>

<br>
<br>

Next.js es un framework de React que facilita funcionalidades avanzadas como enrutamiento, renderizado del lado del servidor (SSR) y generación estática. Aunque ICP no soporta SSR directamente dentro de los canisters debido a limitaciones en la ejecución de JavaScript en el backend, Next.js sigue siendo compatible si se utiliza con exportación estática (``next export``), convirtiendo el sitio en archivos HTML, JS y CSS estáticos listos para desplegar.

Esta estrategia permite aprovechar muchas de las ventajas de Next.js (como su estructura organizada, manejo de rutas, y optimización automática) mientras se mantiene la compatibilidad con los asset canisters del ICP.

[🔗📖 Más información sobre Next.js 🔎](https://nextjs.org/)


### Otros Frameworks

Además de los anteriormente mencionados, también se pueden usar otros frameworks como Vue.js, Svelte o incluso Lit para desarrollar dApps en ICP. Siempre que el resultado del proceso de construcción (``build``) genere archivos estáticos, estos pueden ser servidos por un asset canister.


## AuthClient e ICP Agent


## Despliegue de dApps

## Costos por Transacción y Almacenamiento

## Explorando Transacciones