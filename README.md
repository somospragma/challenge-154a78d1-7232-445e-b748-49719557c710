# Exposición segura de API a terceros

Debes exponer la API de consulta de movimientos a un tercero, aplicando políticas de seguridad y limitación de tasa en el gateway. La API debe ser accesible para un tercero específico, con un límite de 100 solicitudes por minuto y autenticación basada en API key. El gateway debe rechazar solicitudes que no cumplan con estas políticas.

## Informacion General

| Campo | Valor |
|-------|-------|
| **Tema** | gestión de APIs y políticas de gateway |
| **Nivel** | advanced-l2 |
| **Tipo** | practical |
| **Tiempo estimado** | 8 horas |

## Fases del Reto

### Fase 0: Configuración del Proyecto

**Objetivo:** Obtener el proyecto base funcional enviando el Código Base a un asistente de IA, que lo analizará, corregirá errores y generará un ZIP listo para usar.

**Tiempo estimado:** 15-30 minutos

**Instrucciones:**

- Asegúrate de tener instalado para ejecutar el proyecto: Node.js 18+, npm, VS Code o similar.
- Copia todo el contenido del campo **Código Base** de este reto — incluyendo el texto de instrucciones que aparece al inicio.
- Abre un asistente de IA (Claude en claude.ai, ChatGPT o Gemini — se recomienda Claude), pega el contenido copiado en el chat y envíalo.
- El asistente analizará los archivos, corregirá errores y generará un archivo ZIP descargable. Descárgalo y extráelo en la carpeta donde quieras trabajar.
- Ejecuta `npm install && npm run build` (o `npm start`). Si no hay errores, estás listo.

**Entregable:** El proyecto compila/arranca sin errores.

<details>
<summary>Pistas de conocimiento</summary>

- Copia el Código Base completo incluyendo el texto de instrucciones al inicio — esas instrucciones le indican al asistente exactamente qué hacer con los archivos.
- Si el asistente no genera el ZIP automáticamente al terminar el análisis, escríbele: "genera el ZIP ahora".
- Si el proyecto tiene errores al arrancar, comparte el mensaje de error con el mismo asistente para que lo corrija.

</details>

### Fase 1: Configuración inicial del gateway

**Objetivo:** Tener un gateway operativo con políticas de seguridad y limitación de tasa configuradas.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Identificar las políticas de seguridad y limitación de tasa necesarias para la API.
- Configurar el gateway para aplicar estas políticas a la API de consulta de movimientos.

**Entregable:** Gateway configurado con políticas de seguridad y limitación de tasa.

<details>
<summary>Pistas de conocimiento</summary>

- Considera los tipos de autenticación que puede soportar el gateway.
- Evalúa los impactos de la limitación de tasa en la disponibilidad de la API.

</details>

### Fase 2: Exposición de la API al tercero

**Objetivo:** Hacer la API accesible para el tercero con las políticas configuradas.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Exponer la API de consulta de movimientos al tercero, asegurando que se apliquen las políticas de seguridad y limitación de tasa.
- Verificar que el tercero puede acceder a la API y que las políticas se aplican correctamente.

**Entregable:** API de consulta de movimientos expuesta al tercero con políticas de seguridad y limitación de tasa aplicadas.

<details>
<summary>Pistas de conocimiento</summary>

- Considera los métodos para exponer la API al tercero de forma segura.
- Evalúa los posibles impactos de la exposición de la API en la seguridad del sistema.

</details>

### Fase 3: Validación y ajuste de las políticas

**Objetivo:** Asegurar que las políticas aplicadas son efectivas y ajustar si es necesario.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Realizar pruebas para validar que las políticas de seguridad y limitación de tasa son efectivas.
- Ajustar las políticas si es necesario para asegurar la correcta operación de la API.

**Entregable:** Políticas de seguridad y limitación de tasa validadas y ajustadas si es necesario.

<details>
<summary>Pistas de conocimiento</summary>

- Considera los métodos para realizar pruebas de la API con las políticas aplicadas.
- Evalúa los posibles ajustes que puedas necesitar para asegurar la correcta operación de la API.

</details>

## Dimensiones Evaluadas

- **queEs**: ¿Qué son las políticas de seguridad y limitación de tasa en el contexto de una API expuesta a terceros?
- **paraQueSirve**: ¿Para qué sirven las políticas de seguridad y limitación de tasa en una API expuesta a terceros?
- **comoSeUsa**: ¿Cómo se aplican las políticas de seguridad y limitación de tasa en un gateway?
- **erroresComunes**: ¿Cuáles son los errores comunes al aplicar políticas de seguridad y limitación de tasa en una API?
- **queDecisionesImplica**: ¿Qué decisiones debes tomar al configurar y ajustar las políticas de seguridad y limitación de tasa en una API?

## Criterios de Evaluacion

- Configuración correcta del gateway con políticas de seguridad y limitación de tasa.
- Exposición efectiva de la API al tercero con las políticas aplicadas.
- Validación y ajuste adecuado de las políticas para asegurar la correcta operación de la API.

## Como trabajar con un asistente de IA

Hay dos caminos, elegi uno:

- **AGENTS.md** (recomendado) — instrucciones nativas del repo. Abri esta carpeta con tu agente local (Claude Code, Cursor, Codex, Copilot, Gemini) y las carga solo. Sabe que archivos faltan y con que comando se verifica, y completa el scaffold escribiendo en disco.
- **PROMPT_MEJORA.md** — para copiar y pegar en un chat (claude.ai, ChatGPT). Devuelve un ZIP con el proyecto. Sirve si no tenes un agente en el IDE.

Ninguno de los dos resuelve las fases del reto: eso es tu trabajo.

## Verificacion

El proyecto esta listo para trabajar cuando este comando corre sin errores:

```bash
npx --yes @redocly/cli lint openapi.yaml
```

---

*Reto generado automaticamente por Challenge Generator - Pragma*
