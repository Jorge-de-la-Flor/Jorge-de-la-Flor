<div align="center">

[English](README.md) | Español

# Jorge de la Flor (aka FrostCore)

![Python](https://img.shields.io/badge/Python-Systems%20%26%20Data-3776AB?style=flat-square&logo=python&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-Systems%20Programming-CE422B?style=flat-square&logo=rust&logoColor=white)
![C/C++](https://img.shields.io/badge/C%2FC%2B%2B-Embedded%20Development-00599C?style=flat-square&logo=cplusplus&logoColor=white)

![Embedded Systems](https://img.shields.io/badge/Embedded-Real--Time%20Systems-0078D4?style=flat-square)
![Distributed Systems](https://img.shields.io/badge/Distributed%20Systems-Edge%20Computing-FF6F00?style=flat-square)
![Cloud](https://img.shields.io/badge/Cloud-Azure%20%7C%20AWS-0089D6?style=flat-square)
![Language Engineering](https://img.shields.io/badge/Language%20Engineering-Transpilers%20%26%20Codegen-8A2BE2?style=flat-square)

**Software & Cyber-Physical Systems Developer**

**Python y Rust · Sistemas de bajo nivel, sistemas distribuidos, computación embebida, infraestructura cloud**

Construyo sistemas de alto rendimiento con un enfoque centrado en la seguridad, la verificación de software y la confiabilidad en producción — desde firmware en un microcontrolador hasta planos de control corriendo en Azure.

</div>

---

## 🧠 Sobre mí

Diseño y despliego sistemas de bajo nivel y distribuidos: computación embebida, infraestructura cloud y herramientas de generación de código/lenguajes, principalmente en Python y Rust. Mi trabajo gira alrededor de una sola pregunta — ¿esto realmente aguanta en producción? — por eso cada generador, transpilador o runtime que publico se verifica contra toolchains y despliegues reales, no solo con aserciones sobre texto.

También soy instructor técnico, mentor open-source y ponente en eventos de la comunidad tecnológica (Microsoft Build 2026 Community Event, CSWeek 2026).

Vengo de Negocios Internacionales, lo cual me ayuda a traducir necesidades de negocio en sistemas que sí se lanzan.

---

## 🚀 Proyectos destacados

### Apider — Runtime de Automatización Multi-Tenant
`Python · Azure Functions · PyPI · MCP · Paddle`

Runtime serverless que expone Email, Telegram, WhatsApp, Discord, Slack, Google Sheets, HTTP, Webhooks y CloudScheduler mediante un SDK Python limpio, más un módulo de IA (tool-use agéntico, extracción estructurada, RAG stateless) que reutiliza el catálogo de herramientas MCP. Publicado en PyPI y validado por una suite end-to-end de 61 checks ejecutada contra un despliegue vivo en producción — con derivación HMAC de claves por tenant, aislamiento ContextVar y sandboxing a nivel de proceso.

### OMNI-PY — Transpilador Universal de Lenguajes
`Python (ast) · Rust (PyO3) · Java · Go · JavaScript · Rust`

Cobertura completa 16/16 origen-destino entre Java, Go, JavaScript y Rust, usando Python como pivote universal de AST. El emitter de Rust es consciente del ownership (`.clone()`/`.to_string()` exactos, `Option<T>`, `div_euclid`/`rem_euclid` para la semántica de Python) — el borrow checker termina siendo el revisor más estricto del pipeline. Cada salida se verifica compilándola y ejecutándola de verdad con `rustc` y `javac`, respaldado por ocho lints estilo rustc y un analizador de seguridad de doble motor.

### Pyperantio — Generador de Firmware Multi-Toolchain
`Python · Rust · embedded-hal · 5 toolchains de MCU`

Una sola API tipada en Python (`IOConfig`) describe el hardware una vez y genera firmware nativo para cinco toolchains distintas — se acabaron las reescrituras completas de HAL al portar entre familias de MCU. La validación en tiempo de diseño rechaza configuraciones de pines/periféricos eléctricamente inválidas antes de emitir código, con diagnósticos estilo rustc localizados al idioma del usuario. Verificado por el Rust generado compilando bajo `thumbv6m-none-eabi` y 343 tests.

### FrostCloud — Plano de Control en Rust
`Rust · axum · SeaORM · PostgreSQL/SQLite`

Workspace de Cargo íntegramente en Rust que provee cuentas, identidad, catálogo de servicios y activaciones por cuenta como un plano de control que se mantiene fuera del camino de las peticiones. Las fronteras arquitectónicas se imponen a nivel de crate — la lógica de identidad no conoce ni axum ni SeaORM. Los tokens son CSPRNG de 256 bits, almacenados solo como hash SHA-256, con un test que verifica que el token en claro nunca es clave del almacén.

### Flow++ — Análisis de Capacidad de Pipelines
`Python · solo stdlib · MIT`

Convierte la planificación de capacidad de opinión en medición: una API fluida modela pipelines como stages con capacidad y latencia, localiza el cuello de botella, prescribe el cambio mínimo para alcanzar una tasa objetivo, y emite un Architecture Decision Report compartible. 77 tests, cero dependencias.

### Plataforma de Sensado Distribuido — Sistema Ciber-Físico
`ESP32 · Raspberry Pi · Filtro de Kalman · MQTT · SQLite · SSE`

Sistema ciber-físico sobre tres nodos: filtrado de Kalman en tiempo discreto sobre el MCU, pipeline multi-sensor controlado por FSM (PIR + ultrasónico), distribución UART → MQTT → edge, persistencia SQLite, REST API y dashboard en vivo con Server-Sent Events.

---

## 🔬 Robotics & Systems Labs

Repositorios que exploran los principios de ingeniería detrás de la robótica y los sistemas ciber-físicos — sensado, estimación, control y coordinación distribuida bajo condiciones reales.

* **sensor-uncertainty-lab** — Modelos probabilísticos de mediciones de sensores ruidosos
* **bayesian-sensor-fusion** — Filtros de Kalman, filtros de partículas y fusión multi-sensor para estimación de estado
* **robot-perception-lab** — Percepción probabilística: occupancy grids, localización
* **control-systems-lab** — Controladores PID y dinámica de sistemas
* **embedded-state-machine-systems** — Arquitecturas FSM para robótica embebida
* **edge-device-coordination** — Patrones de coordinación para nodos embebidos distribuidos

---

## 🛠️ Stack tecnológico

| Área | Uso principal |
|---|---|
| 🐍 Python | Automatización, APIs backend, ingeniería de lenguajes (AST, codegen), pipelines de datos |
| 🦀 Rust | Sistemas, embebido, `embedded-hal`, herramientas de bajo nivel seguras, servicios web (axum) |
| ⚙️ C/C++ | Arduino, ESP-IDF, STM32 (bare-metal / HAL), integración de SDKs propietarios |
| 🔌 Embebido & IoT | ESP32, STM32, Arduino, RP2040; PlatformIO, ESP-IDF, STM32Cube; UART, I2C, SPI, MQTT |
| ☁️ Cloud | Azure Functions (producción), servicios core de AWS (EC2, Lambda, S3, IAM), diseño serverless multi-tenant |
| 🗄️ Datos & almacenamiento | PostgreSQL, SQLite, SeaORM, SQLAlchemy |
| 🤖 Sistemas de agentes IA | Diseño de servidores MCP, tool-use agéntico, JSON-RPC 2.0 |

---

## 🎤 Charlas y escritura

- *"Building a Multi-Tenant Python Runtime on Azure Functions"* — Microsoft Build 2026 Community Event, Azure User Group Latam (Lima, junio 2026)
- *"Aislamiento y Límites de Confianza en Producción: Construyendo Sistemas a Prueba de Fallos"* — CSWeek 2026 (Lima, agosto 2026)
- Autor de *The Agnostic Engineer: Architecture Beyond Infrastructure* (manuscrito completo, sin publicar) — sobre diseñar sistemas que sobreviven a cambios de infraestructura, lenguaje y proveedor

---

## 📫 Dónde encontrarme

- 📧 **Email**: [frostcore@jafa.dev](mailto:frostcore@jafa.dev)
- 💼 [LinkedIn](https://linkedin.com/in/jorge-de-la-flor)
- 🌐 [jafa.dev](https://jafa.dev)
- 💡 Abierto a colaborar en sistemas embebidos, automatización industrial e integración hardware-software
- 🌎 Disponible para consultoría remota y roles de asesoría técnica con equipos internacionales
