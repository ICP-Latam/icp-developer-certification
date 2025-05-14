<!-- ---
description: Conociendo las bases para programar en el lenguaje exclusivo de ICP.
icon: square-terminal
--- -->

# 🏗️ Miércoles: Métodos y estructuras de control 🧩

<figure><img src="../.gitbook/assets/motoko.png" alt=""><figcaption></figcaption></figure>

**Motoko** es un lenguaje de programación diseñado específicamente por DFINITY para el desarrollo de canisters en Internet Computer (ICP). Su arquitectura está optimizada para aprovechar las características únicas y los flujos de trabajo de ICP, ofreciendo un entorno de programación robusto y familiar. Con una sintaxis similar a lenguajes como JavaScript, Ruby, Python o Solidity, Motoko es fácil de aprender y usar para el desarrollo de aplicaciones.

```rust
// Un canister simple utilizando Motoko.

actor Main {
  public query func hello() : async Text {
    "Hola ICP Devs! :D"
  };
};

await Main.hello();
```

**Atributos de Motoko:**

* **Soporte completo para Candid:** Motoko tiene soporte completamente automático para Candid, integrado en el tiempo de ejecución y el sistema compilador de Motoko.
* **Soporte para memoria estable:** Motoko soporta automáticamente la memoria estable.
* **Soporte para flujo de datos y control asíncronos:** Soporte nativo.
* **Soporte para el paradigma de actores:** Soporte nativo.
* **Análisis estático específico de ICP:** Aplicado a través de múltiples comprobaciones de seguridad.
* **Tamaño binario Wasm:** El tamaño binario Wasm es muy pequeño.
* **Tiempo de compilación:** Motoko tiene un tiempo de compilación más rápido que Rust.
* **Dificultad de aprendizaje:** Aprender Motoko es bastante fácil.
* **Gestión de memoria:** La memoria se gestiona mediante un proceso automático de recolección de basura.
* **Soporte para interfaz de funciones externas:** Aún no soportado.

<!-- {% embed url="https://internetcomputer.org/docs/tutorials/developer-liftoff/level-0/intro-languages/" %}
Documentación oficial lenguajes ICP
{% endembed %} -->
[🔗📖 Documentación oficial de los lenguajes compatibles con ICP](https://internetcomputer.org/docs/tutorials/developer-liftoff/level-0/intro-languages/)
<!-- {% embed url="https://internetcomputer.org/docs/motoko/main/getting-started/motoko-introduction" %}
Introducción de Motoko
{% endembed %} -->
[🔗🛠️ Introducción a Motoko](https://internetcomputer.org/docs/motoko/main/getting-started/motoko-introduction)

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Motoko: Un Inicio Rápido

Esta sección te guiará a través de los pasos esenciales para crear tu primer proyecto en Motoko, desde la configuración inicial hasta el despliegue de tu primer canister. Aprenderás a utilizar las herramientas clave, como DFX, y a escribir código Motoko básico para interactuar con la blockchain de Internet Computer. Este tutorial rápido te proporcionará una base sólida para comenzar a construir tus propias dApps y explorar el potencial de Motoko en el ecosistema de ICP.

### Crear un nuevo proyecto

Abre una ventana de la terminal en tu computadora. Crea un directorio nuevo en donde almacenaremos los archivos de nuestro proyecto y navega a este directorio:

```
mkdir hello_world
cd hello_world
```

Ahora, utilizaremos `dfx` para crear nuestro proyecto:

```
dfx new hello_world
```

Obtendrás una pantalla similar a la siguiente, esta es la configuración inicial de nuestro proyecto:

<pre class="language-bash"><code class="lang-bash"><strong>? Select a backend language: ›
</strong>❯ Motoko
Rust
TypeScript (Azle)
Python (Kybra) code
</code></pre>

Selecciona Motoko, posteriormente seleccionamos la opción `No frontend canister` dado a que estaremos trabajando exclusivamente con un smart contract backend:

```bash
? Select a frontend framework: ›
SvelteKit
React
Vue
Vanilla JS
No JS template
❯ No frontend canister
```

Tambien puedes incluir algunas características extras en tu proyecto, por lo pronto sólo presiona `Enter` para confirmar la creación del proyecto:

```bash
? Add extra features (space to select, enter to confirm) ›
⬚ Internet Identity
⬚ Bitcoin (Regtest)
⬚ Frontend tests
```

### Código del smart contract

Este actor `hello_world` tiene una sola función llamada `saludar`. Está marcada como `query` porque no modifica el estado del actor. La función acepta un nombre como entrada de tipo `Text` y devuelve un saludo de tipo `Text`.

```rust
actor {
  public query func saludar(nombre: Text) : async Text {
    return "Hola, " # nombre # "!";
  };
};
```

### Inicializando el ambiente de desarrollo

Ahora vamos a utilizar `dfx`para inicializar el ambiente de desarrollo donde estaremos desplegando nuestro smart contract:

```
dfx start --background --clean
```

Para desplegar, utilizaremos el comando:

```
dfx deploy
```

Obtendrás algo como lo siguiente en pantalla:

```
...
Committing batch.
Committing batch with 18 operations.
Deployed canisters.
URLs:
Backend canister via Candid interface:
        access_hello_world_backend: http://127.0.0.1:4943/?canisterId=cbopz-duaaa-aaaaa-qaaka-cai&id=ctiya-peaaa-aaaaa-qaaja-cai
```

Para finalizar, interactúa con tu contrato recien desplegado haciendo click en el link que se generó en tu terminal.

<!-- {% embed url="https://internetcomputer.org/docs/motoko/main/getting-started/quickstart" %}
Quickstart oficial en inglés
{% endembed %} -->
[🔗⚡ Quickstart oficial en inglés](https://internetcomputer.org/docs/motoko/main/getting-started/quickstart)

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Explorando la Documentación de Motoko: Tu Guía de Referencia

A medida que avances en tu desarrollo con Motoko, la documentación oficial se convertirá en tu recurso indispensable. Encontrarás información detallada sobre la sintaxis del lenguaje, las funciones disponibles y los conceptos avanzados que necesitarás para construir tus canisters. Aunque la documentación está en inglés, no te preocupes, durante las sesiones de aprendizaje cubriremos los aspectos esenciales para completar tu proyecto final y obtener tu certificación. Te animamos a explorar la documentación para profundizar en tus conocimientos y convertirte en un desarrollador de Motoko experto.

<!-- {% embed url="https://internetcomputer.org/docs/motoko/main/base/" %}
Documentación base Motoko
{% endembed %} -->
[🔗📖 Documentación base Motoko](https://internetcomputer.org/docs/motoko/main/base/)
<!-- {% embed url="https://internetcomputer.org/docs/motoko/main/reference/language-manual" %}
Referencia del lenguaje Motoko
{% endembed %} -->
[🔗📖 Referencia del lenguaje Motoko](https://internetcomputer.org/docs/motoko/main/reference/language-manual)
### Apoyo con IA

La página oficial del Internet Computer Protocol ofrece una pequeña IA para ayudarte con tus consultas. Puedes acceder a ella utilizando el <mark style="color:red;">siguiente botón</mark> en la parte superior derecha:

<figure><img src="../.gitbook/assets/aa.png" alt=""><figcaption></figcaption></figure>

Lo cual traerá la siguiente ventana al frente:

<figure><img src="../.gitbook/assets/asfa.png" alt=""><figcaption></figcaption></figure>

Esta IA acepta preguntas en español, así que no dudes en utilizarla.

### AI Chatbot

También ponemos a tu disposición este pequeño chatbot que te podrá ayudar con **dudas básicas** sobre el desarrollo en Motoko.

<!-- {% embed url="https://icp-ai-chat-frontend.vercel.app/" %}
AI Chatbot ICP
{% endembed %} -->
[🔗🤖 AI Chatbot ICP](https://icp-ai-chat-frontend.vercel.app/)
<!-- {% hint style="warning" %}
Este chatbot se encuentra en desarrollo, por lo que la información o código que te proporcione pueden no ser siempre correctos.
{% endhint %} -->
> ⚠️ Este chatbot se encuentra en desarrollo, por lo que la información o código que te proporcione pueden no ser siempre correctos.
<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Tipos de datos primitivos en Motoko

En Motoko, los tipos de datos primitivos son los bloques de construcción fundamentales para representar valores simples y comunes. Estos tipos incluyen booleanos (verdadero/falso), enteros con y sin signo de diferentes tamaños, caracteres y texto. La elección del tipo de dato primitivo adecuado es crucial, ya que determina qué operaciones (aritméticas, lógicas, relacionales) pueden aplicarse a los valores que representan. La categoría de un tipo, por lo tanto, define el conjunto de operadores disponibles, permitiendo a los desarrolladores realizar cálculos y manipulaciones de datos de manera precisa y eficiente.

<table><thead><tr><th width="182">Identificador</th><th>Descripción</th></tr></thead><tbody><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Bool">Bool</a></td><td>Valores booleanos <code>true</code> y <code>false</code>, y operadores lógicos.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Char">Char</a></td><td>Caracteres Unicode.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Text">Text</a></td><td>Cadenas de caracteres Unicode con concatenación <code>_ # _</code> e iteración.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Float">Float</a></td><td>Valores de punto flotante de 64 bits.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Int">Int</a></td><td>Valores enteros con signo con aritmética (sin límites).</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Int8">Int8</a></td><td>Valores enteros con signo de 8 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Int16">Int16</a></td><td>Valores enteros con signo de 16 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Int32">Int32</a></td><td>Valores enteros con signo de 32 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Int64">Int64</a></td><td>Valores enteros con signo de 64 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Nat">Nat</a></td><td>Valores enteros no negativos con aritmética (sin límites).</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Nat8">Nat8</a></td><td>Valores enteros no negativos de 8 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Nat16">Nat16</a></td><td>Valores enteros no negativos de 16 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Nat32">Nat32</a></td><td>Valores enteros no negativos de 32 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Nat64">Nat64</a></td><td>Valores enteros no negativos de 64 bits con aritmética comprobada.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Blob">Blob</a></td><td>Blobs binarios con iteradores.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Principal">Principal</a></td><td>Principales.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Error">Error</a></td><td>Valores de error.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Region">Region</a></td><td>Objetos de región de memoria estable.</td></tr></tbody></table>

<!-- {% embed url="https://internetcomputer.org/docs/motoko/main/reference/language-manual#primitive-types" %}
Documentación Oficial
{% endembed %} -->
[🔗📖 Documentación Oficial](https://internetcomputer.org/docs/motoko/main/reference/language-manual#primitive-types)
<figure><img src="../.gitbook/assets/Separador2.jpg" alt=""><figcaption></figcaption></figure>

