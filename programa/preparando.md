---
description: >-
  Realiza la instalación de todos lo necesario para comenzar a desarrollar
  dapps.
icon: computer
---

# Martes: Entornos de desarrollo y variables

<figure><img src="../.gitbook/assets/Picture5.png" alt=""><figcaption></figcaption></figure>

¡Listo para construir dApps en Internet Computer? Antes de comenzar, necesitamos configurar tu entorno de desarrollo. Te ofrecemos tres opciones flexibles para adaptarnos a tus preferencias y experiencia:

1. **Docker:** Si buscas un entorno aislado y consistente, Docker es tu aliado. Esta opción te permite tener todas las herramientas necesarias en contenedores, evitando conflictos y facilitando la instalación.
2. **Gitpod:** ¿Prefieres un entorno de desarrollo en la nube? Gitpod te ofrece un espacio de trabajo preconfigurado en tu navegador, listo para codificar con un solo clic.
3. **Instalación Local:** Para aquellos que prefieren tener el control total, esta opción te guía a través de la instalación manual de todas las herramientas necesarias en tu sistema operativo.

Elige la opción que mejor se adapte a tus necesidades y ¡prepárate para dar vida a tus ideas en Internet Computer!

{% hint style="info" %}
Cualquiera de las opciones es válida para realizar tu certificación. Recuerda que al final tendrás que entregar un repositorio público alojado en [GitHub](https://github.com/).
{% endhint %}

Dependiendo de la opción que hayas elegido, lo que necesitas instalar cambia. Acá te dejamos el resumen:

<table><thead><tr><th width="158">Ambiente</th><th>Instalación</th></tr></thead><tbody><tr><td>Docker</td><td>Docker, VS Code</td></tr><tr><td>Gitpod</td><td>Navegador de internet</td></tr><tr><td>Local</td><td>WSL (sólo en Windows), VS Code con sus extensiones y dfxvm.</td></tr></tbody></table>

{% embed url="https://internetcomputer.org/docs/tutorials/developer-liftoff/level-0/dev-env/" %}
Documentación oficial sobre la instalación del ambiente de desarrollo (en inglés)
{% endembed %}

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Motoko Playground

El Motoko Playground es un IDE en línea diseñado para facilitar el aprendizaje de Motoko, el lenguaje nativo de Internet Computer. Con esta herramienta, puedes desplegar canisters directamente en tu navegador, sin necesidad de descargar un SDK. Es una excelente opción para familiarizarte con la sintaxis y los conceptos básicos de Motoko.

Sin embargo, es importante tener en cuenta que el Motoko Playground está destinado principalmente a la **práctica** y la **experimentación**. Para el desarrollo completo de **dApps** y la creación de proyectos que puedas subir a GitHub, te recomendamos encarecidamente que elijas una de las opciones de instalación local **(Docker, Gitpod o instalación local directa)** que hemos descrito anteriormente. Estas opciones te proporcionarán un entorno de desarrollo completo y te permitirán trabajar de manera eficiente en tus proyectos de Internet Computer.

{% embed url="https://m7sm4-2iaaa-aaaab-qabra-cai.raw.ic0.app/" %}
dApp Motoko Playground
{% endembed %}

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Docker

<figure><img src="../.gitbook/assets/Docker-Logo-2.png" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="info" %}
Sólo es necesario instalar Docker si elegiste la primer opción de ambiente de desarrollo: **Docker**.
{% endhint %}

Docker te ofrece la posibilidad de crear un entorno de desarrollo completamente aislado y consistente, donde todas las herramientas y dependencias necesarias para desarrollar en Internet Computer se encuentran encapsuladas en contenedores. Esto significa que puedes evitar los problemas de compatibilidad y configuración que a menudo surgen al instalar herramientas directamente en tu sistema operativo. Además, Docker te permite replicar fácilmente tu entorno de desarrollo en diferentes máquinas, lo que facilita la colaboración y garantiza que todos los miembros del equipo trabajen con la misma configuración.

{% embed url="https://www.docker.com/get-started/" %}
Documentación oficial Docker
{% endembed %}

{% hint style="info" %}
Recomendamos instalar [Docker Desktop](https://docs.docker.com/desktop/). Ten en cuenta que la instalación es diferente para cada sistema operativo.
{% endhint %}

{% embed url="https://docs.docker.com/desktop/setup/install/mac-install/" %}
Instalación Docker Desktop para Mac
{% endembed %}

{% embed url="https://docs.docker.com/desktop/setup/install/windows-install/" %}
Instalación Docker Desktop para Windows
{% endembed %}

{% embed url="https://docs.docker.com/desktop/setup/install/linux/" %}
Instalación Docker Desktop para Linux
{% endembed %}

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## VsCode

<figure><img src="../.gitbook/assets/vscode.png" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="info" %}
Sólo es necesario instalar VS Code si elegiste la primera o la tercera opción de ambiente de desarrollo: **Docker** ó **Local**.
{% endhint %}

Para una experiencia de desarrollo óptima en Motoko, te recomendamos instalar Visual Studio Code (**VS Code**). Este editor de código, ampliamente utilizado por desarrolladores de todo el mundo, ofrece una gran cantidad de extensiones útiles que facilitan la programación en Motoko. Además, contar con un IDE (Entorno de Desarrollo Integrado) como VS Code es esencial para escribir, depurar y organizar tu código de manera eficiente. VS Code te proporcionará las herramientas necesarias para construir dApps en Internet Computer de forma profesional y productiva.

{% embed url="https://code.visualstudio.com/download" %}
Descargar VS Code
{% endembed %}

Si elegiste **Docker** para tu ambiente de desarrollo, las extensiones necesarias serán instaladas al seguir las indicaciones de tu instructor. De otra manera, es necesario instalarlas manualmente.

{% embed url="https://marketplace.visualstudio.com/items?itemName=dfinity-foundation.vscode-motoko" %}
Extensión VS Code Motoko
{% endembed %}

{% hint style="info" %}
Tambien puedes instalar extensiones en GitPod.
{% endhint %}

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Instalación Local

### WSL

Si estás utilizando Windows y deseas desarrollar dApps en Internet Computer, es esencial instalar el Subsistema de Windows para Linux (WSL). DFX, la herramienta de línea de comandos que te permite interactuar con la blockchain de ICP, está diseñada para funcionar en entornos Linux o macOS. WSL te proporciona un entorno Linux dentro de Windows, lo que te permite ejecutar DFX y otras herramientas necesarias sin necesidad de cambiar de sistema operativo. Instalar WSL te abre las puertas al desarrollo de dApps en ICP, permitiéndote aprovechar todas las funcionalidades de DFX en tu entorno Windows.

{% embed url="https://learn.microsoft.com/es-mx/windows/wsl/install" %}
Documentación oficial
{% endembed %}

De igual manera, para que VS Code pueda interactuar con tu instancia de Linux en Windows, es necesario instalar la siguiente extensión:

{% embed url="https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl" %}
Extensión VS Code WSL
{% endembed %}

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

### DFX: El SDK del Internet Computer Protocol

DFX es tu herramienta esencial para crear y gestionar dApps en ICP. Este kit de desarrollo incluye: `dfx`, una interfaz de línea de comandos para administrar proyectos, identidades y ciclos; `dfxvm`, un gestor de versiones para DFX; `moc`, el compilador de Motoko; y `replica`, una instancia local de la red para pruebas y desarrollo. Instalar DFX te permite interactuar con la blockchain de ICP, compilar tus canisters y probar tus aplicaciones localmente, proporcionándote todo lo necesario para construir en Internet Computer.

{% hint style="info" %}
Recuerda que si estás usando Windows, la instalación de DFX debe ser hecha en WSL.
{% endhint %}

{% embed url="https://internetcomputer.org/docs/building-apps/getting-started/install" %}
Documentación oficial sobre la instalación de DFX
{% endembed %}

{% embed url="https://internetcomputer.org/docs/tutorials/developer-liftoff/level-0/intro-dfx" %}
Introducción a DFX
{% endembed %}

<figure><img src="../.gitbook/assets/Separador2.jpg" alt=""><figcaption></figcaption></figure>

