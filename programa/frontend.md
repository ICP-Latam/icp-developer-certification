---
icon: paintbrush
---

# Martes: Integrando frontend a un canister

El desarrollo frontend en el Internet Computer Protocol (ICP) se centra en la creación de interfaces de usuario dinámicas para aplicaciones descentralizadas (dApps). Estas interfaces permiten a los usuarios interactuar directamente con canisters (contratos inteligentes) y servicios alojados en la red ICP, ofreciendo experiencias web completamente descentralizadas.

Para facilitar la implementación y el alojamiento de estas interfaces, ICP introduce el concepto de **asset canisters**.

## ¿Qué un Asset Canister?

Un asset canister, también conocido como `frontend canister`, es un tipo especial de canister diseñado para almacenar y servir activos web estáticos, como archivos HTML, CSS, JavaScript, imágenes y otros recursos necesarios para el frontend de una aplicación. Estos canisters compilan los activos frontend en un módulo WebAssembly (Wasm) que puede ser desplegado y ejecutado en la red ICP.

La configuración de un asset canister se realiza mediante el archivo `dfx.json` del proyecto, donde se define el canister con el tipo "assets". Esto indica a dfx que compile los activos frontend utilizando código base en Rust, que luego se convierte en Wasm para su despliegue.

[🔗📖 Documentación oficial sobre Asset Canisters](https://internetcomputer.org/docs/building-apps/frontends/using-an-asset-canister)

## Lenguajes Compatibles para el Desarrollo de Frontend en ICP

El desarrollo de interfaces para aplicaciones en Internet Computer Protocol (ICP) es altamente flexible, permitiendo a los desarrolladores utilizar una variedad de frameworks modernos y ampliamente adoptados en la industria del desarrollo web. Actualmente el protocolo es compatible con frameworks basados en Node.js. Ejemplo de los mas usados son:

### Vanilla JavaScrip

Vanilla JS es la forma más pura de escribir JavaScript, sin el uso de librerías ni frameworks. Es ideal para proyectos livianos, pruebas rápidas o cuando se desea un control total sobre el comportamiento del frontend.\
En ICP, Vanilla JS puede integrarse directamente con un asset canister y comunicarse con canisters backend mediante la librería `@dfinity/agent`. Su simplicidad también lo hace ideal para comprender cómo funciona la interacción entre el frontend y la infraestructura descentralizada.

[🔗📖 Más información sobre Vanilla.js 🔎](http://vanilla-js.com/)

***

### React

React es una biblioteca declarativa y basada en componentes para construir interfaces de usuario. Su popularidad, ecosistema y flexibilidad lo convierten en una de las mejores opciones para desarrollar frontends sobre ICP.

Utilizando herramientas como Vite o Webpack junto con `@dfinity/agent` y `@dfinity/auth-client`, React permite crear experiencias ricas que se comunican con canisters de forma fluida. Además, al compilar el proyecto para producción (`npm run build`), los archivos generados pueden ser fácilmente desplegados en un asset canister.

[🔗📖 Más información sobre React 🔎](https://es.react.dev/)

***

### Netx.js

Next.js es un framework de React que facilita funcionalidades avanzadas como enrutamiento, renderizado del lado del servidor (SSR) y generación estática. Aunque ICP no soporta SSR directamente dentro de los canisters debido a limitaciones en la ejecución de JavaScript en el backend, Next.js sigue siendo compatible si se utiliza con exportación estática (`next export`), convirtiendo el sitio en archivos HTML, JS y CSS estáticos listos para desplegar.

Esta estrategia permite aprovechar muchas de las ventajas de Next.js (como su estructura organizada, manejo de rutas, y optimización automática) mientras se mantiene la compatibilidad con los asset canisters del ICP.

[🔗📖 Más información sobre Next.js 🔎](https://nextjs.org/)

### Otros Frameworks

Además de los anteriormente mencionados, también se pueden usar otros frameworks como Vue.js, Svelte o incluso Lit para desarrollar dApps en ICP. Siempre que el resultado del proceso de construcción (`build`) genere archivos estáticos, estos pueden ser servidos por un asset canister.

## Integración de Frontend con ICP: Uso de AuthClient y Agent

En el desarrollo de dApps sobre el Internet Computer Protocol (ICP), uno de los aspectos clave es la interacción segura entre el frontend y los canisters que componen el backend de la aplicación. Para ello, el ecosistema de DFINITY proporciona dos herramientas esenciales: `AuthClient` y `Agent`.

### AuthClient: Autenticación con Internet Identity

`@dfinity/auth-client` es una biblioteca que permite integrar autenticación de usuarios en aplicaciones ICP mediante `Internet Identity`, el sistema de identidad descentralizado nativo del protocolo.

Con `AuthClient`, los usuarios pueden iniciar sesión de forma segura en una dApp utilizando anclas de identidad que no requieren nombres de usuario ni contraseñas tradicionales. En su lugar, utilizan mecanismos criptográficos como WebAuthn, que pueden estar respaldados por biometría o llaves físicas.

**Características principales:**

* Permite iniciar y cerrar sesión en la dApp.
* Administra tokens de delegación, que otorgan acceso temporal a un usuario autenticado.
* Se integra fácilmente con el HttpAgent para firmar peticiones a canisters en nombre del usuario.

**Ejemplo de implementación:**

```rust
import { AuthClient } from '@dfinity/auth-client';

const environment = process.env.DFX_NETWORK === 'local'

const authClient = await AuthClient.create()
await authClient.login({
      maxTimeToLive: BigInt(7 * 24 * 60 * 60 * 1000 * 1000 * 1000), 
      identityProvider: environment? 
      `http://${process.env.CANISTER_ID_INTERNET_IDENTITY}.localhost:4943/` : 
      "https://identity.ic0.app", 
      onSuccess: async () => {
        window.location.reload()
        }
    })
```

### Agent: Comunicación con Canisters

Un `agente` es una API usada para interactuar con la API publica de ICP y lo canisters desplegados dentro de la blockchain. Estos agentes cuentan con un soporte de autenticacion atraves de la libreria `auth-client`, que es la que usa el servicio de Internet Identity. Existen dos maneras para gestionar la duración de la sesión, la primera de ellas es establecer un tiempo de vida a la autenticación mediante el `maxTimeToLive` y la segunda es el `idle Manager`, que se encarga de monitorear la ausencia de interacciones con la pagina o aplicacion mediante la actividad de los perifericos automaticamente la sesion se cierra tras 10 min de inactividad, sin embargo este valor puede cambar para una mayor personalizacion

`@dfinity/agent` es una biblioteca que permite a aplicaciones frontend interactuar con canisters desplegados en la red ICP. Este paquete expone la clase `HttpAgent`, que puede enviar mensajes (`update` o `query`) firmados a los canisters.

Junto con IDL (el lenguaje de descripción de interfaces de ICP), `Agent` permite construir interfaces de comunicación entre el frontend y los métodos públicos de un canister.

**Funciones clave del Agent:**

* Se conecta con canisters usando sus IDs.
* Firma solicitudes con la identidad del usuario (cuando se combina con AuthClient).
* Soporta peticiones tanto en modo de lectura (query) como de escritura (update).
* Puede configurarse para apuntar a redes locales (réplica) o a la mainnet de ICP.

**Ejemplo de implementación:**

```rust
import { createActor, canisterId } from "dirección de la carpeta 'declarations'"

import { HttpAgent } from '@dfinity/agent' 

const localHost = "http://localhost:4943"
const productionHost = "https://ic0.app"

const identity = authClient.getIdentity()
  const agent = new HttpAgent ({
    identity, 
    host: environment? localHost : productionHost,
  })
  const actor = createActor(canisterId, {
    agent
  })
```

[🔗📖 Documentación oficial sobre Internet Identity y como integrarlo en un proyecto](https://internetcomputer.org/docs/tutorials/hackathon-prep-course/authentication)

## Despliegue de dApps

Uno de los pasos más importantes en el desarrollo de una aplicación descentralizada (dApp) en Internet Computer Protocol (ICP) es el despliegue de canisters, los "contratos inteligentes" nativos de esta red. Los canisters contienen la lógica de negocio, el almacenamiento de datos, y también pueden servir activos del frontend. En ICP, desplegar tu canister significa lanzar tu aplicación a una red escalable, segura y completamente descentralizada.

**El proceso puede realizarse en dos entornos:**

### 1. Despliegue Local (Entorno de Desarrollo) 🚧

Antes de publicar tu canister en la red principal, puedes probarlo localmente utilizando la herramienta `dfx` (el CLI oficial de DFINITY). Esto simula una instancia local del Internet Computer para desarrollo y pruebas.

Para esto debes posicionar tu terminal en la carpeta raiz del proyecto. Estando ahí, ejecuta los siguientes comandos:

* `dfx start --clean --background`: Este comando inicia una réplica local del Internet Computer en tu computadora para simular el comportamiento de la red ICP.
* `dfx deploy`: Este comando compila e instala (o actualiza) los canisters en el entorno que estás usando (puede ser local o en la red principal).

Al finalizar el `deploy` aparecerán los siguientes mensajes en la consola, donde se proporcionaran los enlaces para acceder al `frontend` de la aplicación como al `backend` mediante `candid UI`.

> ⚠️ En el caso de acceder al frotnend, usar de preferencia los enlaces recomendados.

### 2. Despliegue en Mainnet (Red Principal de ICP) 🌐

Una vez que tu canister esté listo para producción, puedes desplegarlo en la **red principal del Internet Computer (ICP)**, lo que permitirá que sea accesible públicamente a través de dominios como `icp0.io`. Para lograrlo, es necesario transferir **ICP tokens** a una **identidad**, y luego convertir esos tokens en **cycles**, que son el "combustible" que utilizan los canisters para ejecutar operaciones.

#### Pasos para el despliegue en mainnet:

* Crear una identidad nueva: `dfx identity new <Nombre de la identidad>`
* Seleccionar una identidad: `dfx identity use <Nombre de la identidad>`
* Obtener el `account-id` para hacer transeferencias: `dfx ledger account-id`

> ⚠️ El id resultante es la dirección a la cúal se deben transferir los tokens de ICP

* Ver el balance en tokens: `dfx ledger balance --network=ic`
* Convertir `tokens` de ICP a `cycles`: `dfx cycles convert --amount AMOUNT --network=ic`
* Ver el balance en `cycles`: `dfx cycles balance --network=ic`
* Hacer ping a la mainnet: `dfx ping ic`

> ⚠️ Una conexión correcta con la mainnet debe de dar una respuesta parecida 👇:
>
> {\
> "replica\_health\_status": "healthy",\
> "root\_key": \[48, 129, 130, 48, 29, 6, 13, 43, 6, 1, 4, 1, 130, 220, 124, 5, 3, 1, 2, 1, 6, 12, 43, 6, 1, 4, 1, 130, 220, 124, 5, 3, 2, 1, 3, 97, 0, 129, 76, 14, 110, 199, 31, 171, 88, 59, 8, 189, 129, 55, 60, 37, 92, 60, 55, 27, 46, 132, 134, 60, 152, 164, 241, 224, 139, 116, 35, 93, 20, 251, 93, 156, 12, 213, 70, 217, 104, 95, 145, 58, 12, 11, 44, 197, 52, 21, 131, 191, 75, 67, 146, 228, 103, 219, 150, 214, 91, 155, 180, 203, 113, 113, 18, 248, 71, 46, 13, 90, 77, 20, 80, 95, 253, 116, 132, 176, 18, 145, 9, 28, 95, 135, 185, 136, 131, 70, 63, 152, 9, 26, 11, 170, 174]\
> }

* Desplegar el proyecto en la mainnet: `dfx deploy --network ic`

[🔗📖 Documentación oficial sobre creación de identidades y conversión a cycles](https://internetcomputer.org/docs/tutorials/developer-liftoff/level-1/1.4-using-cycles)

[🔗📖 Documentación oficial sobre el despliegue en mainnet](https://internetcomputer.org/docs/tutorials/developer-liftoff/level-1/1.5-deploying-canisters)

## ¿Qué son los **Cycles** en el Internet Computer?

En el Internet Computer, los **cycles** son la unidad de medida que representa los recursos computacionales. Funcionan como el **combustible** que alimenta a los canisters (contenedores inteligentes donde vive la lógica de tu dApp). Sin cycles, un canister no puede ejecutar código ni almacenar datos.

### ¿Para qué sirven los cycles?

Los cycles son necesarios para:

* 💻 Ejecutar funciones y lógica de negocio dentro de un canister.
* 🧠 Almacenar información de manera persistente.
* 🔁 Enviar y recibir mensajes entre canisters o hacia el exterior (por ejemplo, solicitudes HTTP).
* ⏱ Procesar tareas asincrónicas o temporizadas (como `Timers`).

> Piensa en los cycles como el "gas" de Ethereum, pero con costos predecibles, escalables y mucho más eficientes.

***

### ¿Cómo se consumen los cycles?

Cada operación que realiza tu canister —desde guardar datos, responder a una solicitud, hasta realizar llamadas a otros canisters— **consume una cantidad específica de cycles**. Para más información visita la siguiente documentación oficial:

[🔗📖 Más informacion sobre las operaciones de los canisters y sus recursos 🔎](https://internetcomputer.org/docs/building-apps/essentials/gas-cost)

[🔗📖 Tabla de costos (en cycles y USD) por operación 📊](https://internetcomputer.org/docs/references/cycles-cost-formulas)

[🔗📖 Calculadora de costos 🧮](https://3d5wy-5aaaa-aaaag-qkhsq-cai.icp0.io/)

## Transacciones en el Internet Computer

En el ecosistema del **Internet Computer (ICP)**, una **transacción** representa cualquier operación que involucra el movimiento de tokens ICP o la ejecución de acciones dentro de un canister que consume recursos computacionales (cycles). Las transacciones son una parte fundamental tanto para el despliegue como para la operación continua de aplicaciones descentralizadas (dApps).

***

### Tipos de transacciones

Las transacciones pueden clasificarse en dos grandes grupos:

* **Transacciones financieras**:
  * Envío de tokens ICP entre identidades o wallets.
  * Conversión de ICP a cycles para alimentar canisters.
* **Transacciones computacionales**:
  * Despliegue o actualización de canisters.
  * Llamadas a funciones expuestas por los canisters (por ejemplo, agregar datos, ejecutar lógica, etc.).
  * Llamadas entre canisters.

Cada una de estas acciones genera un evento dentro de la red del Internet Computer, el cual queda registrado y puede ser consultado públicamente.

***

### ICP Explorer: Explorando transacciones en la red

El **ICP Explorer** es una herramienta oficial que permite visualizar y auditar la actividad de la red del Internet Computer. Funciona como una especie de "explorador de bloques", similar a Etherscan en Ethereum.

Con esta herramienta puedes:

* Buscar una transacción específica por su hash.
* Ver el historial de actividad de una identidad o dirección (`account-id`).
* Consultar el estado y uso de un canister.
* Ver cuánto ICP fue transferido, a quién y cuándo.
* Ver conversiones de ICP a cycles.

[🔗🚀 Ir a ICP Explorer](https://www.icpexplorer.org/#/)
