<!-- ---
description: Aprende a cómo guardar información en los canisters de ICP.
icon: box
--- -->

# 💾 Jueves: Estructuras de datos y persistencia 📦
Aprende a cómo guardar información en los canisters de ICP

<figure><img src="../.gitbook/assets/Picture4.png" alt=""><figcaption></figcaption></figure>

Internet Computer maneja el almacenamiento de datos persistente mediante una característica conocida como **memoria estable**. La memoria estable es una característica única de Internet Computer que define un almacén de datos separado del almacén de datos de memoria **Wasm** regular del canister, conocido como **memoria heap**. La memoria heap de un canister no es almacenamiento persistente y **no** se conserva durante las actualizaciones del canister; los datos y el estado del canister almacenados en la memoria heap se eliminan cuando se actualiza o reinstala un canister. Para canisters inmutables que utilizan menos del límite de memoria heap de 4GiB, se puede utilizar la memoria heap. Para canisters más grandes, y especialmente aquellos que pretenden actualizarse y cambiarse con el tiempo, la memoria estable es importante ya que persiste durante las actualizaciones del canister, tiene una capacidad de almacenamiento mucho mayor que la memoria heap y es muy beneficiosa para escalar verticalmente una dApp.

Para utilizar la memoria estable, se requiere anticipar e indicar qué datos del canister se desea conservar después de una actualización del canister. Para algunos canisters, estos datos podrían ser todos los datos del canister, mientras que para otros podrían ser solo ciertas partes o ninguna. Por defecto, la memoria estable comienza vacía y puede contener hasta **500GiB** siempre que la **subred** en la que se ejecuta el canister tenga el espacio disponible. Si un canister utiliza más memoria estable que 500GiB, el canister se bloqueará y se volverá irrecuperable.

### Tipos de memoria y términos

* **Memoria Estable**
La memoria estable se refiere a la característica de almacenamiento de datos a largo plazo de Internet Computer. La memoria estable no es específica del lenguaje y puede ser utilizada por canisters escritos en Motoko, Rust o cualquier otro lenguaje. La memoria estable puede contener hasta **500GiB** si la subred puede acomodarlo.

* **Memoria Heap**
La memoria heap se refiere al almacén de datos de memoria Wasm regular para cada canister. Este almacenamiento es temporal y no se conserva durante las actualizaciones del canister. Los datos almacenados en la memoria heap se eliminan cuando se actualiza o reinstala el canister. La memoria heap está limitada a **4GiB**.

* **Almacenamiento Estable**
El almacenamiento estable es un término específico de Motoko que se refiere a la característica de almacenamiento estable de Motoko. El almacenamiento estable utiliza la memoria estable de ICP para persistir los datos durante las actualizaciones del canister.

* **Variables Estables**
Las variables estables son una característica específica de Motoko que se refiere a las variables definidas en Motoko que utilizan el modificador `stable`, que indica que el valor de la variable debe conservarse durante las actualizaciones del canister.

<!-- {% embed url="https://internetcomputer.org/docs/tutorials/developer-liftoff/level-2/2.1-storage-persistence" %}
Documentación Oficial
{% endembed %} -->
ℹ️ 🔗 <a href="https://internetcomputer.org/docs/tutorials/developer-liftoff/level-2/2.1-storage-persistence" target="_blank">Documentación oficial </a>.

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Colecciones en Motoko: Organizando tus Datos

Las colecciones son estructuras de datos que te permiten almacenar y organizar múltiples elementos de manera eficiente en Motoko. Son esenciales para el desarrollo de aplicaciones complejas, ya que facilitan la manipulación y el acceso a grandes cantidades de datos. Desde listas simples hasta mapas complejos, las colecciones te proporcionan las herramientas necesarias para gestionar tus datos de forma efectiva. Es importante tener en cuenta que el tipo de memoria utilizada (heap o estable) dependerá de la colección específica y de cómo se implemente en tu canister, tal como se explicó en la sección anterior.

<table><thead><tr><th width="150">Colección</th><th>Descripción</th></tr></thead><tbody><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Array">Arrays</a></td><td>Arreglos mutables e inmutables. Ideales para almacenar secuencias de elementos del mismo tipo.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/List">Listas</a></td><td>Listas enlazadas simples puramente funcionales. Útiles para implementar pilas y colas.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Buffer">Buffers</a></td><td>Listas mutables de elementos de un tipo específico. Permiten la modificación eficiente de la secuencia de elementos.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/HashMap">HashMaps</a></td><td>Mapas hash que asocian claves con valores. Eficientes para buscar, insertar y eliminar elementos por clave.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/AssocList">AssocLists</a></td><td>Mapas implementados como listas enlazadas de pares clave-valor. Útiles para mantener el orden de inserción.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Deque">Deques</a></td><td>Colas de doble extremo que permiten insertar y eliminar elementos desde ambos extremos. Ideales para implementar colas y pilas.</td></tr><tr><td><a href="https://internetcomputer.org/docs/motoko/main/base/Heap">Heaps</a></td><td>Colas de prioridad que mantienen los elementos ordenados según su prioridad. Útiles para implementar algoritmos de búsqueda y ordenamiento.</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/Separador2.jpg" alt=""><figcaption></figcaption></figure>

