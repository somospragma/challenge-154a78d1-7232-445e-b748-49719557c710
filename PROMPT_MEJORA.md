# Prompt para Mejorar el Codigo Base

Copia y pega el contenido del bloque de abajo en un asistente de IA (Claude, ChatGPT)
para obtener un ZIP con el proyecto completo y arrancable.

Si preferis trabajar en tu editor con un agente local (Claude Code, Cursor, Copilot), usa `AGENTS.md` en vez de este archivo: dice lo mismo pero para que escriba los archivos en disco.

## Las dos reglas que no se negocian

1. **Completa el boilerplate.** Todo lo que el proyecto necesita para compilar y arrancar: manifiesto de dependencias, punto de entrada, configuracion, capa de interfaz, y las capas del patron arquitectonico declarado. Eso es andamiaje y es tu trabajo.
2. **NO resuelvas el reto.** Los entregables de las fases son el trabajo de la persona. El hueco pedagogico se deja como esta: el proyecto arranca, pero lo que el reto pide implementar NO esta implementado.

Dicho de otra forma: si algo impide compilar, arreglalo. Si algo es logica de negocio incompleta, validaciones ausentes, un secreto hardcodeado o un patron mejorable, dejalo exactamente como esta — es lo que la persona tiene que encontrar.

## Superficie de practica — NO resuelvas

Estos archivos SON el ejercicio de la persona. No los implementes; deja stubs.

- `policies/security.yaml` — El topic pide autenticacion/seguridad: este archivo es el ejercicio.
- `openapi.yaml` — El topic pide el contrato de API: openapi.yaml es el ejercicio.

## Lo que le falta a este proyecto

Esto NO lo tenes que adivinar: salio de comparar el proyecto contra la arquitectura declarada del reto y de un analisis estatico del codigo. Completalo TODO.

### Archivos corruptos — arreglar primero

El contenido no corresponde a la extension. Regeneralos completos:

- `tests/contract.postman_collection.json` — El contenido no corresponde a un archivo json. Hay que regenerarlo completo.

## Como saber que terminaste

```bash
npx --yes @redocly/cli lint openapi.yaml
```

Ese comando corriendo sin errores es la definicion de "listo".

---

```
## Briefing del reto (autoridad)
Este bloque manda sobre los archivos adjuntos. El stack y el rol salen de AQUÍ, no de un topic genérico ni de markdown placeholder.

### Perfil
Chapter Integración, Especialidad Desarrollador, Tecnología API, Advanced

### Brecha de conocimiento
Aplica politicas de gateway de seguridad y limitacion de tasa sobre una API expuesta a terceros

### Misión / candidato
Exponer la API de consulta de movimientos a un tercero

### Datos adicionales
Candidato con 3 años en API management

### Reto
- Tema: gestión de APIs y políticas de gateway
- Seniority: advanced-l2
- Tipo: practical
- Título: Exposición segura de API a terceros
- Tiempo estimado: 8 horas

### Fases (trabajo del HUMANO — PROHIBIDO completarlas)
No implementes estos entregables. Dejalos como hueco pedagógico. El asistente solo materializa el proyecto arrancable para que el participante pueda trabajar.
- Fase 1: Configuración inicial del gateway — objetivo: Tener un gateway operativo con políticas de seguridad y limitación de tasa configuradas. — entregable (NO resolver): Gateway configurado con políticas de seguridad y limitación de tasa.
- Fase 2: Exposición de la API al tercero — objetivo: Hacer la API accesible para el tercero con las políticas configuradas. — entregable (NO resolver): API de consulta de movimientos expuesta al tercero con políticas de seguridad y limitación de tasa aplicadas.
- Fase 3: Validación y ajuste de las políticas — objetivo: Asegurar que las políticas aplicadas son efectivas y ajustar si es necesario. — entregable (NO resolver): Políticas de seguridad y limitación de tasa validadas y ajustadas si es necesario.

Eres un asistente experto en análisis, corrección y generación de archivos de cualquier tipo:
código fuente, documentación, hojas de cálculo, documentos Word, configuraciones, entre otros.
Voy a enviarte una cadena de texto que contiene uno o más archivos. Cada archivo está delimitado por un marcador con el siguiente formato:
// === ARCHIVO: ruta/del/archivo.extension ===
o también puede aparecer como:
## === ARCHIVO: ruta/del/archivo.extension ===
Lo que sigue al marcador puede ser:

El contenido real del archivo (código, texto, YAML, etc.)
Una descripción en lenguaje natural de lo que debe contener el archivo


TU TAREA
PASO 0 — ¿Esto es un proyecto o una carcasa?
Antes de extraer archivos, leé el Briefing (si está) y diagnosticá el adjunto.

Es CARCASA si ocurre CUALQUIERA de estas:
- No hay manifiesto de dependencias del stack del briefing (manifest.json de VTEX IO / package.json / pom.xml / build.gradle / requirements.txt / go.mod / *.tf / *.csproj, según corresponda)
- Hay un "binario" que en realidad es un comentario ("no puede ser mostrado como texto plano", placeholder .fig/.docx vacío)
- Los markdowns ya completan entregables de fases posteriores ("se implementó fade-in", lista de áreas ya resuelta)

Si es CARCASA:
- MATERIALIZÁ un proyecto que arranca en el stack del briefing (VTEX IO Store Framework, Angular, Terraform, pytest, Nest, etc.). Incluí manifiesto, punto de entrada y capa de interfaz reales.
- NO copies los markdowns de "solución" como si fueran el producto. Son ruido de generación.
- NO resuelvas las fases del briefing (están marcadas PROHIBIDO). Dejá el hueco pedagógico: el flujo existe, las microinteracciones/calidad/infra que el reto pide NO están hechas.
- Después seguí al PASO 5 (ZIP).

Si es un proyecto REAL (manifiesto + código que compila o arranca):
- Seguí PASO 1 en adelante. 🔴 compilación sí. 🟡 pedagógico no.

PASO 1 — Detección y extracción
Identifica todos los archivos presentes en la cadena. Para cada archivo extrae:

Su ruta completa (ej: src/main/java/com/pragma/Service.java)
Su contenido o descripción

PASO 2 — Clasificación por tipo
Clasifica cada archivo en una de estas categorías:
A) Código fuente (Java, Python, TypeScript, JavaScript, Kotlin, etc.)
B) Configuración / documentación (YAML, properties, Markdown, JSON, txt, etc.)
C) Excel (.xlsx, .xls, .csv)
D) Word (.docx, .doc)
E) Otro tipo de archivo binario o especial
PASO 3 — Clasificación de errores en código fuente

Objetivo prioritario: que el proyecto compile. No corrijas flujo de negocio ni lógica funcional.

Antes de modificar cualquier archivo de código fuente, clasifica cada problema encontrado en una de estas dos categorías:
🔴 ERROR DE COMPILACIÓN — corregir siempre
Son errores que impiden que el proyecto arranque, sin valor pedagógico:

Import faltante o incorrecto
Clase, método o variable referenciada que no existe en ningún archivo del proyecto
Error de sintaxis
Anotación con atributos inválidos
Dependencia ausente en pom.xml, package.json, etc.
Archivo referenciado que no existe y debe ser creado con implementación mínima

→ CORREGIR estos errores.
🟡 PROBLEMA FUNCIONAL O DE CALIDAD — preservar siempre
Son problemas que no impiden compilar. Pueden ser intencionales para el aprendizaje:

Clave secreta hardcodeada ("secret", "password123")
API deprecada que funciona pero tiene reemplazo moderno
Lógica de negocio incorrecta o incompleta
Código redundante o de baja legibilidad
Falta de validaciones en flujo de negocio
Patrones de diseño incorrectos pero funcionales
Concurrencia no segura
Configuración funcional pero no óptima

→ PRESERVAR tal cual. No corregir, no mejorar, no comentar.
PASO 4 — Procesamiento según tipo de archivo
Tipo A — Código fuente
Aplica únicamente las correcciones clasificadas como 🔴 ERROR DE COMPILACIÓN.
No alteres ningún elemento clasificado como 🟡 PROBLEMA FUNCIONAL O DE CALIDAD.
Si falta un archivo referenciado, créalo con la implementación mínima necesaria para compilar.
Tipo B — Configuración / documentación
Extrae el contenido tal cual, sin modificaciones salvo errores evidentes de sintaxis
(ej: YAML mal indentado).
Tipo C — Excel (.xlsx)
Si viene con contenido real, genera el archivo respetando ese contenido.
Si viene con descripción en lenguaje natural, genera un archivo Excel funcional con:

Fila de encabezados en negrita con color de fondo distintivo
Columnas con ancho ajustado al contenido
Tipos de dato correctos por columna
Validaciones si la descripción lo indica
Hojas nombradas descriptivamente si hay más de una
Filas de ejemplo si no hay datos reales

Tipo D — Word (.docx)
Si viene con contenido real, genera el archivo respetando ese contenido.
Si viene con descripción en lenguaje natural, genera un documento Word funcional con:

Estilos de título (Título 1, Título 2) para jerarquía de secciones
Fuente legible (Calibri o equivalente), tamaño 11-12pt para cuerpo
Márgenes estándar
Tabla de contenido si tiene múltiples secciones
Tablas con encabezados en negrita si aplica

Tipo E — Otro
Genera el archivo con el contenido o estructura más apropiada según la descripción.
PASO 5 — Exportación en ZIP
Empaqueta todos los archivos en un único archivo ZIP descargable respetando exactamente
la estructura de rutas indicada por los marcadores.
El ZIP debe incluir:

Archivos de código con únicamente los errores de compilación corregidos
Archivos de configuración y documentación sin cambios
Archivos nuevos creados para resolver dependencias de compilación faltantes
Archivos Excel y Word generados desde descripción

IMPORTANTE: El ZIP debe estar listo para descargar al finalizar. No preguntes si el usuario
quiere generarlo. Simplemente genera el archivo y proporciona el enlace de descarga; No debes desplegar en el chat el resumen de lo que arreglaste al Zip, solo entregalo.

REGLAS IMPORTANTES

No omitas ningún archivo aunque no tenga errores ni modificaciones
Respeta los nombres y rutas exactas indicadas por los marcadores
Si un archivo no tiene marcador claro, infiere el nombre desde su contenido
Si la cadena contiene solo documentación, placeholders o binarios fake, NO la reproduzcas:
aplicá PASO 0 (materializar el proyecto del briefing). Reproducir la carcasa es un fallo.
No agregues texto después del enlace de descarga del ZIP
No preguntes si el usuario quiere el ZIP: simplemente generalo siempre
Si detectas que falta un archivo de configuración necesario para compilar
(pom.xml, package.json, requirements.txt, build.gradle, etc.), créalo e inclúyelo
inferiendo su contenido desde los imports y frameworks detectados en el código
Nunca corrijas problemas 🟡 aunque parezcan obvios o fáciles de mejorar.
El participante que recibirá este proyecto los debe encontrar y resolver él mismo.


INPUT
Aquí está la cadena con los archivos:

// === ARCHIVO: package.json ===
{
  "name": "api-gateway-policies",
  "version": "1.0.0",
  "description": "API Gateway con políticas de seguridad y rate limiting para exposición de API a terceros",
  "main": "openapi.yaml",
  "scripts": {
    "lint": "npx @redocly/cli lint openapi.yaml",
    "validate": "npx @redocly/cli lint openapi.yaml --config=redocly.yaml",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "openapi",
    "api-gateway",
    "security",
    "rate-limiting",
    "third-party-integration"
  ],
  "author": "Pragma S.A.",
  "license": "ISC",
  "devDependencies": {
    "@redocly/cli": "^1.12.0"
  },
  "dependencies": {},
  "redocly": {
    "lint": {
      "extends": ["recommended"],
      "rules": {
        "info-license": "off",
        "operation-operationId": "error",
        "operation-summary": "error",
        "path-params": "error",
        "no-unused-components": "warn",
        "no-ambiguous-paths": "error",
        "security-defined": "error"
      },
      "theme": {
        "openapi": {
          "hideHostname": false,
          "expandResponses": "200,201",
          "requiredPropsFirst": true,
          "jsonSampleExpandLevel": 2
        }
      }
    }
  }
}

// === ARCHIVO: openapi.yaml ===
openapi: 3.1.0
info:
  title: API de consulta de movimientos
  version: 1.0.0
  description: API para consultar movimientos con políticas de seguridad y limitación de tasa.
paths:
  /movements:
    get:
      summary: Obtener movimientos
      operationId: getMovements
      security:
        - api_key: []
      responses:
        '200':
          description: Movimientos obtenidos
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/MovementResponse'
components:
  securitySchemes:
    api_key:
      type: apiKey
      in: header
      name: X-API-KEY
  schemas:
    MovementResponse:
      type: object
      properties:
        movements:
          type: array
          items:
            type: object
            properties:
              id:
                type: string
              amount:
                type: number
              date:
                type: string
                format: date-time

// === ARCHIVO: README.md ===
# API de consulta de movimientos

## Despliegue del gateway
1. Instala las dependencias con `npm install`.
2. Ejecuta `npm run lint` para verificar el contrato OpenAPI.

## Configuración de políticas
- Política de seguridad: define `X-API-KEY` en `security.yaml`.
- Política de limitación de tasa: configura en `rate-limiting.yaml`.

## Validación del funcionamiento
1. Ejecuta `npm run validate` para lintear el contrato OpenAPI.
2. Verifica que el gateway rechaza solicitudes sin `X-API-KEY` o con exceso de solicitudes por minuto.

// === ARCHIVO: policies/security.yaml ===
# Política de seguridad para autenticación basada en API key

type: SecurityScheme
description: Autenticación basada en API key para el endpoint expuesto.

# SUPERFICIE DE PRÁCTICA - Stub sin implementación

// === ARCHIVO: policies/rate-limiting.yaml ===
# Política de limitación de tasa

type: RateLimiting
description: Limitación de tasa que restringe a 100 solicitudes por minuto para el tercero específico.

requests: 100
perMinute: true

// === ARCHIVO: environments/dev.yaml ===
endpoints:
  - url: https://api-dev.example.com/v1
    description: Endpoint de desarrollo para la API de consulta de movimientos
credentials:
  apiKey: dev-api-key-12345
  secret: dev-secret-abcdef

// === ARCHIVO: environments/prod.yaml ===
endpoints:
  - url: https://api-prod.example.com/v1
    description: Endpoint de producción para la API de consulta de movimientos
credentials:
  apiKey: prod-api-key-67890
  secret: prod-secret-ghijkl

// === ARCHIVO: tests/contract.postman_collection.json ===
{
  "info": {
    "name": "API Gateway Contract Tests",
    "_postman_id": "12345678-90ab-cdef-1234-567890abcdef",
    "description": "Postman collection to validate the API Gateway contract, including security and rate limiting policies.",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "item": [
    {
      "name": "Test Security Policy",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "api-key",
            "value": "{{apiKey}}"
          }
        ],
        "url": {
          "raw": "{{endpoint}}/movements"
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "exec": [
              "pm.test('Status code is 200', function () {\n    pm.response.to.have.status(200);\n});\n\n"            
          }
        }
      ]
    },
    {
      "name": "Test Rate Limiting Policy",
      "request": {
        "method": "GET",
        "header": [
          {
            "key": "api-key",
            "value": "{{apiKey}}"
          }
        ],
        "url": {
          "raw": "{{endpoint}}/movements"
        }
      },
      "event": [
        {
          "listen": "test",
          "script": {
            "exec": [
              "pm.test('Status code is 429 after exceeding rate limit', function () {\n    pm.response.to.have.status(429);\n});\n\n"            
          }
        }
      ]
    }
  ],
  "variable": [
    {
      "key": "endpoint",
      "value": "{{endpoint}}"
    },
    {
      "key": "apiKey",
      "value": "{{apiKey}}"
    }
  ]
}
```
