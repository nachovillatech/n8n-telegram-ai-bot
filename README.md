# 🤖 n8n Telegram AI Agent (PostgreSQL + Local LLM / OpenAI API)

Flujo avanzado de automatización en **n8n** que implementa un **Agente de IA autónomo para Telegram**. 

El bot es capaz de mantener memoria de conversación persistente en PostgreSQL, consultar bases de datos relacionales en tiempo real mediante *Tools* personalizadas y responder a través del modelo de lenguaje local (LM Studio / Ollama / vLLM) o APIs compatibles.

---

## ✨ Características Principales

- 💬 **Interfaz de Chat en Telegram:** Atención e interacción directa con usuarios o empleados desde dispositivos móviles.
- 🧠 **Agente de IA Autónomo:** Implementación basada en arquitecturas de agentes que deciden cuándo consultar la BBDD o responder directamente.
- 💾 **Memoria Persistente (Postgres Chat Memory):** Conserva el historial de chat de cada usuario en la base de datos para mantener el contexto en conversaciones largas.
- 🛠️ **Herramientas de Consulta SQL (SQL Tools):** Capacidad de ejecutar consultas `SELECT` seguras para extraer datos en tiempo real de inventarios, pedidos o stock.
- ⚡ **100% Integrable con LLMs Locales:** Compatible con LM Studio, vLLM u Ollama usando el conector OpenAI Chat Model.

---

## 🛠️ Stack Tecnológico

| Componente | Tecnología |
|---|---|
| Orquestación de Flujos | n8n |
| Canales de Entrada/Salida | Telegram Bot API (Webhooks) |
| Motor de IA | LM Studio / Ollama / OpenAI API Compatible |
| Persistencia & Memoria | PostgreSQL (`Postgres Chat Memory`) |
| Formateo de Datos | JavaScript Code Nodes (n8n) |

---

## 🏗️ Arquitectura del Flujo (n8n)

```
📲 Mensaje en Telegram
         │
         ▼
💬 Telegram Trigger (Webhook HTTPS)
         │
         ▼
     🤖 AI Agent (Orquestador principal)
      ├── 🧠 Motor LLM (LM Studio / vLLM local)
      ├── 💾 Memoria de Chat (PostgreSQL Chat Memory)
      └── 🛠️ Herramientas (Execute SQL Query en Postgres)
         │
         ▼
   ⚙️ Code Node (Formateo JavaScript)
         │
         ▼
📤 Send Text Message (Respuesta automática a Telegram)
```

---

## 🚀 Requisitos para Despliegue y Pruebas

1. **Servicios activos:**
   - Instancia de **n8n** en ejecución.
   - Servidor **PostgreSQL** accesible para la memoria y consultas.
   - **LM Studio / vLLM** corriendo en modo servidor (puerto `1234` u `11434`).
2. **Configuración del Webhook HTTPS:**
   - Telegram exige conexiones seguras SSL/HTTPS. En entornos de pruebas locales o red privada, se requiere un túnel seguro (ej. `ngrok`, `Cloudflare Tunnel` o la variable `WEBHOOK_URL` en n8n).

---

## 📁 Estructura del Repositorio

- `workflows/`: Archivos `.json` exportados listos para importar en n8n (`telegram_ai_agent.json`).
- `docs/`: Diagramas de flujo e instrucciones de configuración.
- `scripts/`: Scripts auxiliares de formateo.

---

## 👤 Autor

**Ignacio** — [GitHub Profile](https://github.com/nachovillatech)
