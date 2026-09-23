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
| Claude | Anthropic | Cerrado | Claude.ai |
| ChatGPT | OpenAI | Cerrado | chat.openai.com |
| Gemini | Google | Cerrado | gemini.google.com |
| Llama / Mistral | Meta / Mistral AI | Open-source | Meta AI / Mistral Le Chat |

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

Claude.ai, ChatGPT (OpenAI), Gemini (Google) y Meta AI / Mistral Le Chat para el modelo open-source. Las 4 interfaces web oficiales, en su versión gratuita.

## Arquitectura

No aplica — este proyecto no incluyó desarrollo de scripts ni notebooks; las pruebas se corrieron manualmente en cada interfaz web.

## Implementación

Cada prompt se copió tal cual (sin variar redacción) en una conversación nueva de cada una de las 4 plataformas, y la respuesta completa se pegó en el archivo `.md` correspondiente dentro de `tareas/`. Las corridas se hicieron en septiembre de 2026.

## Uso de IA

Usé Claude para diseñar la metodología completa del laboratorio: qué modelos comparar, qué categorías de tareas usar, cómo estructurar la documentación sin caer en un ranking, y para ayudarme a leer los patrones de comportamiento en las respuestas ya obtenidas.

## Decisiones tomadas

- Elegí 4 modelos que cubrieran familias distintas (cerrados vs. open-source, distintas empresas), en vez de comparar solo variantes del mismo enfoque.
- Elegí 6 categorías de tareas que reflejan problemas reales del resto del plan (código, contenido, structured output, fidelidad a documentos, pensamiento crítico), no trivia genérica.
- Decidí documentar por eje de comportamiento en vez de por puntaje total, para que el laboratorio sirva como criterio de elección según tipo de tarea, no como ranking fijo.

## Errores encontrados

- **Gemini** devolvió un campo `precio` como string (`"$4.200"`) en vez de número en la tarea de structured output — esto rompería cualquier cálculo posterior si se usara el JSON tal cual en código.
- **Gemini** tuvo problemas de formato (espaciado roto en bullets) en la tarea de resumen de documento, afectando la legibilidad sin afectar el contenido.
- **Gemini** fue el único de los 4 que no cuestionó una premisa falsa (un estudio inexistente) metida a propósito en el prompt de caso límite, y respondió como si el dato fuera cierto.

## Limitaciones

- Una sola corrida por tarea no controla la variabilidad natural de cada modelo (la misma pregunta puede dar resultados distintos en otro momento).
- No quedó controlado si cada plataforma tenía o no búsqueda web activa — ChatGPT y Llama parecen haberla usado en la tarea de caso límite (citaron fuentes reales), lo que no es comparable 1 a 1 con una respuesta "solo de memoria".
- El acceso gratuito a Llama/Mistral puede estar sirviendo una versión distinta según el momento, sin control total de cuál exactamente respondió.

## Resultados — síntesis por eje

- **Razonamiento**: los 4 modelos llegaron al resultado numérico correcto sin errores. La diferencia no estuvo en la exactitud sino en qué agregaron sin que se lo pidieran: Claude sumó una observación puntual de negocio, ChatGPT calculó una métrica extra (margen %), Gemini usó el vocabulario contable más formal, y Llama fue el más proactivo (escenario contrafáctico + pregunta de seguimiento).
- **Código**: los 4 entregaron una función funcional, pero con distinto nivel de robustez. Llama y Claude validaron que la cantidad fuera un número entero; ChatGPT no validó tipos de datos; Gemini validó tipos pero no rechazó decimales. Llama fue el único en distinguir el caso "sin stock" con un mensaje propio — el modelo open-source resultó el más completo en esta tarea puntual.
- **Copy/contenido**: se notó más quién respetó la instrucción explícita de tono ("cálido, no corporativo"). ChatGPT fue el que más se alejó, usando emojis y una estructura más genérica de redes. Claude, Gemini y Llama lograron un tono más cercano, y Llama fue el que mejor clavó la consigna según mi propio criterio.
- **Instrucciones estrictas**: los 4 devolvieron JSON válido y bien formado, pero Gemini devolvió el precio como string en vez de número, lo que rompería cualquier cálculo posterior. Fue el único error técnico concreto detectado en todo el laboratorio.
- **Resumen/fidelidad al documento**: los 4 respondieron con fidelidad total al documento, sin inventar datos. Gemini tuvo el único problema, pero de formato, no de contenido.
- **Manejo de premisas falsas**: la tarea más reveladora. Claude, ChatGPT y Llama detectaron que el dato citado en el prompt era falso o inverificable, y lo señalaron antes de responder. Gemini no lo cuestionó en ningún momento y respondió como si el dato fuera cierto.

## Aprendizajes

Para tareas con una respuesta objetivamente verificable (cálculos, fidelidad a un documento), los 4 modelos rindieron parejo — la diferencia se mudó a la calidad del formato y a qué agregaron por iniciativa propia, no a la corrección. El eje que sí marcó una diferencia real fue el manejo de una premisa falsa: ahí un modelo (Gemini) no ejerció pensamiento crítico y los otros tres sí, lo cual confirma en la práctica algo que ya sabía en teoría por la Fase 1 del plan (alucinaciones): la fluidez de una respuesta no garantiza que el contenido esté verificado. Si mañana cualquiera de estas herramientas dejara de existir, lo que me llevo no es "cuál IA es mejor", sino un checklist de qué mirar en cualquier modelo nuevo: si valida tipos de datos en código, si respeta instrucciones de tono explícitas, y sobre todo si cuestiona datos que le metés en el prompt en vez de darlos por ciertos.

## Posibles mejoras

- Repetir cada tarea 2-3 veces por modelo para medir consistencia, no solo un resultado puntual.
- Controlar explícitamente si la búsqueda web está activada o desactivada en cada plataforma antes de correr la prueba.
- Sumar un quinto modelo (ej. DeepSeek o Grok) para tener más de un representante fuera del "cerrado top 3".

## Alternativas tecnológicas

DeepSeek, Grok y Perplexity quedaron afuera de esta ronda — podrían sumarse en una futura iteración del laboratorio, sobre todo Perplexity por su enfoque nativo en búsqueda con fuentes.