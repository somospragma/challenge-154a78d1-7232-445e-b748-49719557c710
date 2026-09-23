# AGENTS.md

Instrucciones para el agente de IA que abra este repositorio (Claude Code, Cursor, Codex, Copilot, Gemini). Se cargan solas: no hay que pegar nada en ningun chat.

## Que es este repositorio

Es el codigo base de un reto de aprendizaje de Pragma: **Exposición segura de API a terceros**.

| | |
|---|---|
| Tema | gestión de APIs y políticas de gateway |
| Nivel | advanced-l2 |
| Chapter | Integración — Desarrollo |
| Especialidad | Api |
| Stack | YAML / OpenAPI 3.1 |
| Patron arquitectonico | API Gateway con políticas de seguridad y rate limiting (API First) |
| Tiempo estimado | 8 horas |

## Receta del stack

Esqueleto obligatorio:

- `openapi.yaml con paths, schemas y responses completos`
- `policies/ con las politicas del gateway (rate limit, auth, transformacion)`
- `environments/ con la configuracion por ambiente`
- `tests/ con la coleccion de contrato`
- `README.md con el contrato y los codigos de error`

Dependencias:

- @redocly/cli n/a
- Postman n/a
- OpenAPI 3.1 specification n/a

## Tu tarea

Dejar este proyecto en estado **verificable**: que el comando de verificacion corra sin errores. Escribi los archivos en disco, en este repositorio. No generes ZIPs ni archivos adjuntos.

En orden:

1. Corre `npx --yes @redocly/cli lint openapi.yaml` y mira que falla.
2. Completa lo que falte de la lista de abajo: manifiesto de dependencias, punto de entrada, capa de interfaz y las capas del patron declarado.
3. Arregla SOLO los errores que impiden compilar o arrancar.
4. Volve a correr `npx --yes @redocly/cli lint openapi.yaml` hasta que pase.
5. Pará ahí.

## Regla dura: las fases son trabajo del humano

**PROHIBIDO implementar los entregables de las fases.** El valor del reto esta en que la persona los resuelva. Tu trabajo es que tenga un proyecto que arranca; el hueco pedagogico se queda como esta.

No resuelvas nada de esto:

- **Fase 1 — Configuración inicial del gateway**: Gateway configurado con políticas de seguridad y limitación de tasa.
- **Fase 2 — Exposición de la API al tercero**: API de consulta de movimientos expuesta al tercero con políticas de seguridad y limitación de tasa aplicadas.
- **Fase 3 — Validación y ajuste de las políticas**: Políticas de seguridad y limitación de tasa validadas y ajustadas si es necesario.

Distincion operativa:

- **Arreglar** (si): import faltante, tipo que no existe, dependencia sin declarar, error de sintaxis, archivo referenciado que no existe.
- **No tocar** (no): logica de negocio incompleta, validaciones ausentes, secretos hardcodeados, APIs deprecadas que funcionan, concurrencia insegura, patrones mejorables. Eso es lo que la persona tiene que encontrar.

## Superficie de practica (NO completes)

Estos archivos SON el ejercicio de la persona. No los implementes; deja stubs. No toques la logica que el reto pide completar.

- [ ] `policies/security.yaml` — El topic pide autenticacion/seguridad: este archivo es el ejercicio.
- [ ] `openapi.yaml` — El topic pide el contrato de API: openapi.yaml es el ejercicio.

## Lo que falta y tenes que completar

### Archivos corruptos (1) — arreglá esto primero

El contenido de estos archivos no corresponde a su extension. Regeneralos completos:

- [ ] `tests/contract.postman_collection.json` — El contenido no corresponde a un archivo json. Hay que regenerarlo completo.

### Presentes (8)

- `package.json`
- `openapi.yaml`
- `README.md`
- `policies/security.yaml`
- `policies/rate-limiting.yaml`
- `environments/dev.yaml`
- `environments/prod.yaml`
- `tests/contract.postman_collection.json`

### Capas del patron declarado

Cada una tiene que existir como directorio real con al menos un archivo. Codigo plano en la raiz no satisface el patron.

- `environments`
- `policies`
- `tests`
- `api`

## Verificacion

```bash
npx --yes @redocly/cli lint openapi.yaml
```

El comando tiene que pasar SIN implementar los archivos de la superficie de practica: solo andamiaje.

Ese comando pasando es la definicion de "terminado" para vos.

## Convenciones que tenes que respetar

- Un solo ecosistema: no declares librerias de otro lenguaje ni mezcles gestores de paquetes.
- Toda libreria que uses tiene que estar declarada en el manifiesto de dependencias.
- Todo import declarado tiene que usarse; todo tipo usado tiene que existir o venir de una dependencia declarada.
- El patron es **API Gateway con políticas de seguridad y rate limiting (API First)**: los contratos (interfaces, puertos) los define la capa interna y los implementa la externa, nunca al revés.
- Los archivos que crees llevan implementacion real, no stubs: sin `TODO`, sin cuerpos vacios, sin `// getters y setters`.

## Contexto del candidato

Sirve para calibrar el nivel del codigo, no para resolver las fases.

- Perfil: Chapter Integración, Especialidad Desarrollador, Tecnología API, Advanced
- Brecha que el reto ataca: Aplica politicas de gateway de seguridad y limitacion de tasa sobre una API expuesta a terceros
- Mision: Exponer la API de consulta de movimientos a un tercero

---

*Generado por Challenge Generator — Pragma. `README.md` tiene el enunciado completo del reto para la persona. `PROMPT_MEJORA.md` es la variante para pegar en un chat, si se prefiere ese flujo.*
