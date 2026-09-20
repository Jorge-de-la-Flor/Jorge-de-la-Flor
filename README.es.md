<div align="center">

[English](README.md) | Español

# Jorge de la Flor (aka FrostCore)

![Python](https://img.shields.io/badge/Python-Sistemas%20y%20Datos-3776AB?style=flat-square&logo=python&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-Programaci%C3%B3n%20de%20Sistemas-CE422B?style=flat-square&logo=rust&logoColor=white)
![C/C++](https://img.shields.io/badge/C%2FC%2B%2B-Desarrollo%20Embebido-00599C?style=flat-square&logo=cplusplus&logoColor=white)

![Embedded Systems](https://img.shields.io/badge/Embebidos-Tiempo%20Real-0078D4?style=flat-square)
![Distributed Systems](https://img.shields.io/badge/Sistemas%20Distribuidos-Edge%20Computing-FF6F00?style=flat-square)
![Cloud](https://img.shields.io/badge/Cloud-Azure%20%28prod%29%20%7C%20AWS-0089D6?style=flat-square)
![Language Engineering](https://img.shields.io/badge/Language%20Engineering-Transpiladores%20y%20Codegen-8A2BE2?style=flat-square)

**Desarrollador de Software y Sistemas Ciberfísicos**

**Python y Rust · Sistemas de bajo nivel, sistemas distribuidos, computación embebida, infraestructura cloud**

Construyo sistemas que se verifican contra la realidad — firmware que compila para toolchains reales de MCU, código transpilado que se ejecuta con `rustc` y `javac`, runtimes probados contra producción en vivo — desde un microcontrolador hasta un plano de control en Azure.

</div>

---

## 🧠 Sobre mí

Diseño y publico sistemas de bajo nivel y distribuidos: computación embebida, infraestructura cloud y herramientas de lenguajes y generación de código, principalmente en Python y Rust. Mi trabajo gira en torno a una pregunta — ¿esto realmente se sostiene en producción? — por eso cada generador, transpilador o runtime que publico se verifica contra toolchains y despliegues reales, no solo con tests unitarios sobre texto.

Desde 2023 construyo y mantengo el software sobre el que opera una empresa de administración de propiedades — desde la primera línea de código hasta una operación estable en producción.

También soy instructor técnico, mentor open-source y ponente en eventos de la comunidad tecnológica (Microsoft Build 2026 Community Event, CSWeek 2026, BoyaConf 2026).

Vengo de Negocios Internacionales, lo que me ayuda a traducir necesidades de negocio en sistemas que llegan a producción.

---

## 🚀 Proyectos destacados

### [sysgud](https://github.com/Jorge-de-la-Flor/sysgud) — Agente de operaciones con IA y aprobación humana, en Rust
`Rust · SQLite · REST/OpenAPI · Telegram Bot API · Anthropic API`

Un agente local de diagnóstico de procesos: un LLM convierte los logs en propuestas de acción, pero `KILL` y `EXECUTE` solo se ejecutan tras la aprobación de un usuario autorizado, por API REST o Telegram. Las decisiones se persisten en disco antes de actuar y nunca se reejecutan tras un reinicio; ningún comando pasa por un shell construido con texto del modelo, y los secretos se ocultan antes de almacenarse y antes de llegar al LLM. Workspace de cinco crates con fronteras de dependencias verificadas en CI, distribuido como contenedor endurecido (sistema de archivos de solo lectura, sin capabilities). Desarrollado en una hackathon, donde lideré al equipo en diseño, infraestructura y código.

### Apider — Runtime de automatización multi-tenant · [PyPI](https://pypi.org/project/apider/)
`Python · Azure Functions · PyPI · MCP · Paddle`

Un runtime serverless que expone Email, Telegram, WhatsApp, Discord, Slack, Google Sheets, HTTP, Webhooks y CloudScheduler mediante un SDK Python limpio, más un módulo de IA (tool-use agéntico, extracción estructurada, RAG stateless) que reutiliza el catálogo de herramientas MCP. Publicado en PyPI y validado por una suite end-to-end de 61 checks ejecutada contra un despliegue en producción — con derivación HMAC de claves por tenant, aislamiento ContextVar y sandboxing a nivel de proceso.

### OMNI-PY — Transpilador universal de lenguajes
`Python (ast) · Rust (PyO3) · Java · Go · JavaScript · Rust`

Cobertura completa 16/16 origen-destino entre Java, Go, JavaScript y Rust, usando Python como pivote universal de AST. El emitter de Rust es consciente del ownership (`.clone()`/`.to_string()` exactos, `Option<T>`, `div_euclid`/`rem_euclid` para la semántica de Python) — el borrow checker termina siendo el revisor más estricto del pipeline. Cada salida se verifica compilándola y ejecutándola con `rustc` y `javac`, respaldada por ocho lints estilo rustc y un analizador de seguridad de doble motor.

### Pyperantio — Generador de firmware multi-toolchain
`Python · Rust · embedded-hal · 5 toolchains de MCU`

Una sola API tipada en Python (`IOConfig`) describe el hardware una vez y genera firmware nativo para cinco toolchains distintos — sin reescribir el HAL completo al portar entre familias de MCU. El modelo de hardware se cosecha de fuentes de silicio de la industria (1.503 MCUs STM32, 70 AVR y 11 ESP32) en lugar de tablas escritas a mano. La validación en tiempo de diseño rechaza configuraciones de pines y periféricos eléctricamente inválidas antes de emitir código, con diagnósticos estilo rustc en el idioma del usuario. Verificado por el Rust generado compilando bajo `thumbv6m-none-eabi` y una suite de 401 casos. Charla en BoyaConf 2026 con demo en vivo multi-target.

### FrostCloud — Plano de control en Rust
`Rust · axum · SeaORM · PostgreSQL/SQLite`

Un workspace de Cargo íntegramente en Rust que provee cuentas, identidad, catálogo de servicios y activaciones por cuenta como plano de control fuera del camino de las peticiones. Las fronteras arquitectónicas se imponen por crate — la lógica de identidad no sabe nada de axum ni de SeaORM. Los tokens son CSPRNG de 256 bits, almacenados solo como hash SHA-256, con un test que verifica que el token en claro nunca es clave del almacén.

### Flow++ — Análisis de capacidad de pipelines
`Python · solo stdlib · CLI · Generador de ADR`

Convierte la planificación de capacidad de opinión en medición: una API fluida modela pipelines como stages con capacidad y latencia, localiza el cuello de botella, prescribe el cambio mínimo para alcanzar una tasa objetivo y emite un Architecture Decision Report compartible. 77 tests, cero dependencias.

### Plataforma de Sensado Distribuido — Sistema ciberfísico · [video demo](https://www.youtube.com/watch?v=wTfh7YRz6LQ)
`ESP32 · Raspberry Pi · Filtro de Kalman · MQTT · SQLite · SSE`

Un sistema ciberfísico de tres nodos: filtrado de Kalman en tiempo discreto sobre el MCU, pipeline multi-sensor controlado por FSM (PIR + ultrasónico), distribución UART → MQTT → edge, persistencia SQLite, API REST y dashboard en vivo con Server-Sent Events.

> OMNI-PY, Pyperantio, FrostCloud y el backend de Apider son de código cerrado mientras se convierten en productos. Con gusto muestro cualquiera de ellos en vivo por pantalla compartida.

---

## 🔬 Laboratorios de robótica y sistemas

Repositorios que exploran los principios de ingeniería detrás de la robótica y los sistemas ciberfísicos — sensado, estimación, control y coordinación distribuida bajo restricciones reales.

* **sensor-uncertainty-lab** — Modelos probabilísticos de mediciones ruidosas de sensores
* **bayesian-sensor-fusion** — Filtros de Kalman, filtros de partículas y fusión multi-sensor para estimación de estado
* **robot-perception-lab** — Percepción probabilística: mapas de ocupación, localización
* **control-systems-lab** — Controladores PID y dinámica de sistemas
* **embedded-state-machine-systems** — Arquitecturas FSM para robótica embebida
* **edge-device-coordination** — Patrones de coordinación para nodos embebidos distribuidos

---

## 🛠️ Stack técnico

| Área | Uso principal |
|---|---|
| 🐍 Python | Automatización, APIs backend, ingeniería de lenguajes (AST, codegen), pipelines de datos |
| 🦀 Rust | Sistemas, embebido, `embedded-hal`, tooling seguro de bajo nivel, servicios web (axum) |
| ⚙️ C/C++ | Arduino, ESP-IDF, STM32 (bare-metal / HAL), integración de SDKs propietarios |
| 🔌 Embebido e IoT | ESP32, STM32, Arduino, RP2040; PlatformIO, ESP-IDF, STM32Cube; UART, I2C, SPI, MQTT |
| ☁️ Cloud | Azure Functions (producción), servicios core de AWS (EC2, Lambda, S3, IAM), diseño serverless multi-tenant, contenedores (Podman/Docker) |
| 🗄️ Datos y almacenamiento | PostgreSQL, SQLite, SeaORM, SQLAlchemy |
| 🤖 Sistemas de agentes IA | Diseño de servidores MCP, tool-use agéntico, aprobación human-in-the-loop, JSON-RPC 2.0 |

---

## 🎤 Charlas y escritura

- *"Building a Multi-Tenant Python Runtime on Azure Functions"* — Microsoft Build 2026 Community Event, Azure User Group Latam (Lima, junio 2026)
- *"Aislamiento y Límites de Confianza en Producción: Construyendo Sistemas a Prueba de Fallos"* — CSWeek 2026 (Lima, agosto 2026)
- *"De Python a Bare-Metal: Repensando la Abstracción en Sistemas Embebidos"* — BoyaConf 2026 (Tunja, Colombia, noviembre 2026) · próxima
- Autor de *The Agnostic Engineer: Architecture Beyond Infrastructure* (manuscrito completo, sin publicar) — sobre diseñar sistemas que sobreviven a cambios de infraestructura, lenguaje y proveedor

---

## 📫 Dónde encontrarme

- 📧 **Email**: [frostcore@jafa.dev](mailto:frostcore@jafa.dev)
- 💼 [LinkedIn](https://linkedin.com/in/jorge-de-la-flor)
- 🌐 [jafa.dev](https://jafa.dev)
- 💡 Abierto a roles remotos de tiempo completo en software de sistemas, Rust, embebidos e infraestructura
- 🤝 Con gusto colaboro en sistemas embebidos, integración hardware–software y herramientas para desarrolladores
