# Laboratorio de LLMs

> Proyecto de la Fase 1 — Fundamentos de IA (Plan de Especialización: IA aplicada a Ecommerce, Contenido y Automatización)

## Problema

*(¿Qué problema de entendimiento resuelve este laboratorio? Ej: no tener criterio propio para elegir qué modelo usar en cada tipo de tarea, más allá de la fama o el marketing de cada empresa.)*

## Objetivo

Comparar el comportamiento de distintos LLM frente a las mismas tareas, documentando capacidades, limitaciones y patrones de comportamiento — **sin declarar un modelo ganador**. El objetivo no es rankear, es desarrollar criterio propio para elegir la herramienta adecuada según el tipo de problema.

## Contexto

*(Por qué armás este laboratorio ahora, en qué momento del plan, qué sabías antes de empezar y qué no.)*

## Modelos comparados

| Modelo | Proveedor | Tipo | Acceso usado |
|---|---|---|---|
| Claude | Anthropic | Cerrado | — |
| ChatGPT | OpenAI | Cerrado | — |
| Gemini | Google | Cerrado | — |
| Llama / Mistral | Meta / Mistral AI | Open-source | — |

## Metodología

- Mismo prompt exacto para los 4 modelos en cada tarea (sin ajustar redacción entre uno y otro).
- 6 categorías de tareas, una tarea por categoría.
- Documentación por eje de comportamiento, no por puntaje ni ranking.
- Cada tarea documentada en su propio archivo dentro de `tareas/`.

## Tareas evaluadas

1. [Razonamiento/lógica](tareas/razonamiento.md)
2. [Código](tareas/codigo.md)
3. [Copy de producto](tareas/copy-producto.md)
4. [Structured output / instrucciones estrictas](tareas/structured-output.md)
5. [Resumen de documento](tareas/resumen-documento.md)
6. [Caso límite / premisa falsa](tareas/caso-limite.md)

## Herramientas utilizadas

*(Claude.ai, ChatGPT, Gemini, playground de Llama/Mistral usado, etc. — completar al terminar.)*

## Arquitectura

*(No aplica a nivel técnico en este proyecto — o completar si armaste algún script/notebook para automatizar las corridas.)*

## Implementación

*(Cómo ejecutaste las pruebas en la práctica: interfaz usada, fecha de las corridas, versión de cada modelo si la sabés.)*

## Uso de IA

*(En qué medida usaste IA para ayudarte a diseñar el laboratorio en sí — ej. Claude para estructurar la metodología.)*

## Decisiones tomadas

*(Por qué estas 6 categorías y no otras, por qué estos 4 modelos, por qué esta forma de documentar.)*

## Errores encontrados

*(Completar durante las corridas: respuestas rotas, alucinaciones detectadas, inconsistencias entre corridas del mismo modelo, etc.)*

## Limitaciones

*(Ej: una sola corrida por tarea no controla la variabilidad del modelo; versiones de los modelos pueden cambiar después de esta fecha; acceso gratuito puede limitar el modelo real usado en el open-source.)*

## Resultados — síntesis por eje

*(Completar al final, con las 6 tareas ya hechas. No poner "ganador" — sintetizar patrones. Ejemplos de formato:)*

- **Razonamiento**: ...
- **Código**: ...
- **Copy/contenido**: ...
- **Instrucciones estrictas**: ...
- **Resumen/fidelidad al documento**: ...
- **Manejo de premisas falsas**: ...

## Aprendizajes

*(Qué entendiste sobre cómo funcionan los LLM en general, no solo sobre estos 4 modelos puntuales — la pregunta guía del plan: "¿qué pasaría si mañana esta herramienta dejara de existir?")*

## Posibles mejoras

*(Ej: repetir cada tarea varias veces para medir consistencia, sumar un quinto modelo, probar con temperatura distinta.)*

## Alternativas tecnológicas

*(Otros modelos que quedaron afuera y por qué — ej. Grok, DeepSeek, Perplexity, etc.)*
