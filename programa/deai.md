<!-- ---
description: Conoce la propuesta de valor en IA de ICP.
icon: brain
--- -->

# 🧠 Viernes: Autenticación y módulos 🔐

<figure><img src="../.gitbook/assets/asdwq.png" alt=""><figcaption></figcaption></figure>

## Internet Identity

Internet Identity (II) es un sistema de identidad descentralizado que te permite autenticarte de forma segura y anónima en las dApps de Internet Computer (ICP). Para los desarrolladores, II es crucial ya que simplifica la gestión de la identidad del usuario en sus aplicaciones. Al integrar II, puedes ofrecer a tus usuarios una experiencia de inicio de sesión fluida y segura, sin necesidad de almacenar contraseñas o datos personales. Además, II te permite probar y depurar tu código localmente, simulando la autenticación de usuarios reales. Al utilizar Internet Identity, puedes construir dApps más seguras y fáciles de usar, aprovechando al máximo el potencial de Internet Computer.

<!-- {% embed url="https://github.com/dfinity/internet-identity/tree/main/demos/using-dev-build" %}
Repositorio Oficial
{% endembed %} -->
🔗 📚  <a href="https://github.com/dfinity/internet-identity/tree/main/demos/using-dev-build" target="_blank">Repositorio Oficial</a>.
<!-- {% embed url="https://internetcomputer.org/docs/building-apps/authentication/integrate-internet-identity" %}
Documentación oficial sobre la integración de Internet Identity
{% endembed %} -->
🔗 🔐 <a href="https://internetcomputer.org/docs/building-apps/authentication/integrate-internet-identity" target="_blank">Documentación oficial sobre la integración de Internet Identity</a>.
<!-- {% hint style="info" %}
Recuerda que puedes crear tu propia identidad [acá](https://identity.ic0.app/). Sin embargo, las identidades que usaremos en desarrollo son identidades ficticias.
{% endhint %} -->
> ℹ️ Recuerda que puedes crear tu propia identidad <a href="https://identity.ic0.app/" target="_blank">acá 🔗</a>. Sin embargo, las identidades que usaremos en desarrollo son identidades ficticias.
<!-- {% embed url="https://4rnkm-6yaaa-aaaag-ab6qq-cai.icp0.io/" %}
dApp de Ejemplo
{% endembed %} -->
🔗 📱 <a href="https://4rnkm-6yaaa-aaaag-ab6qq-cai.icp0.io/" target="_blank">dApp de Ejemplo</a>.
<br>

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Módulos Externos: Ampliando las Capacidades de tu Desarrollo en Motoko

Los módulos externos, también conocidos como librerías, son componentes de código reutilizables que extienden las funcionalidades de Motoko. Al igual que en otros lenguajes de programación, te permiten aprovechar el trabajo de otros desarrolladores, ahorrando tiempo y esfuerzo en la creación de tus dApps. Utilizar módulos externos te permite acceder a funcionalidades predefinidas, como estructuras de datos complejas, algoritmos optimizados o integraciones con servicios externos, lo que te permite construir aplicaciones más robustas y eficientes. Para gestionar estos módulos, Motoko cuenta con gestores de paquetes como Mops y Vessel, que facilitan la instalación y actualización de las librerías que necesitas para tu proyecto.

<!-- {% embed url="https://mops.one/" %}
Mops
{% endembed %} -->
🔗 <a href="https://mops.one/" target="_blank">Mops</a>.
<!-- {% embed url="https://github.com/dfinity/vessel" %}
Vessel
{% endembed %} -->
🔗 <a href="https://github.com/dfinity/vessel" target="_blank">Vessel</a>.
<!-- {% embed url="https://internetcomputer.org/docs/tutorials/developer-liftoff/level-3/3.1-package-managers" %}
Documentación oficial
{% endembed %} -->
🔗 📖 <a href="https://internetcomputer.org/docs/tutorials/developer-liftoff/level-3/3.1-package-managers" target="_blank">Documentación oficial</a>.

<figure><img src="../.gitbook/assets/Separador.jpg" alt=""><figcaption></figcaption></figure>

## Construye Agentes de IA Soberanos con Canisters en Internet Computer

Internet Computer te empodera para crear y desplegar servicios de software a prueba de manipulaciones, otorgándote verdadera propiedad y soberanía digital. Estos servicios, conocidos como canisters, ahora pueden integrarse con Modelos de Lenguaje Grandes (LLMs) con unas pocas líneas de código. Imagina construir agentes de Inteligencia Artificial que realmente posees y controlas, ejecutándose directamente en la blockchain de ICP. En este programa, aprenderás a aprovechar esta poderosa combinación para desarrollar aplicaciones innovadoras y descentralizadas que marcan la diferencia.

```rust
import LLM "mo:llm";

await LLM.prompt(#Llama3_1_8B, "Cuál es la velocidad de la luz?")
```

<!-- {% embed url="https://internetcomputer.org/ai" %}
Documentación oficial
{% endembed %} -->
🔗 📖 <a href="https://internetcomputer.org/ai" target="_blank">Documentación oficial</a>.
<!-- {% embed url="https://internetcomputer.org/ai-agents" %}
Agentes de IA en ICP
{% endembed %} -->
🔗 🤖  <a href="https://internetcomputer.org/ai-agents" target="_blank">Agentes de IA en ICP</a>.

### Demostración

Puedes probar esta capacidad de ICP utilizando este pequeño Live Demo.

<figure><img src="../.gitbook/assets/Picture7.png" alt=""><figcaption></figcaption></figure>

<!-- {% embed url="https://vgjrt-uyaaa-aaaal-qsiaq-cai.icp0.io/" %} -->
🔗 📱 <a href="https://vgjrt-uyaaa-aaaal-qsiaq-cai.icp0.io" target="_blank">Live demo</a>.

🔗 🚀 Si deseas desplegarlo por ti mismo, puedes hacerlo desde <a href="https://icp.ninja/projects/llm-chatbot" target="_blank">acá</a>.
<!-- {% embed url="https://icp.ninja/projects/llm-chatbot" %} -->

<figure><img src="../.gitbook/assets/Separador2.jpg" alt=""><figcaption></figcaption></figure>

