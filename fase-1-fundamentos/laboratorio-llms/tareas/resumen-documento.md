# Tarea: Resumen de documento

## Prompt usado

Basándote únicamente en el documento que te compartí, respondé: ¿en qué mes del roadmap empieza la Fase 5, cuáles son sus temas principales, y cuál es el proyecto de esa fase? No agregues información que no esté en el documento.

## Respuestas

### Claude
Según el documento, la Fase 5 (Automatización) arranca en el mes 6 y abarca los meses 6 a 8.

Sus temas principales son las APIs REST (GET, POST, PUT, DELETE, JSON y autenticación), los webhooks, las herramientas n8n, Make y Zapier, las bases de datos e integraciones, y la automatización de procesos.

El proyecto de esa fase es automatizar el flujo de pedidos: compra → pago → registro → stock → envío → comunicación al cliente → actualización de datos.
### ChatGPT
La **Fase 5 — Automatización** empieza en el **mes 6** y se extiende hasta el **mes 8**. 

**Temas principales:**

* APIs REST: GET, POST, PUT, DELETE, JSON y autenticación.
* Webhooks.
* n8n, Make y Zapier.
* Bases de datos e integraciones.
* Automatización de procesos. 

**Proyecto de la fase:**

* **Automatizar el flujo de pedidos:** compra → pago → registro → stock → envío → comunicación al cliente → actualización de datos. 


### Gemini
Basándote en el documento proporcionado, aquí tienes los detalles de la Fase 5:

* **Mes del roadmap en el que empieza:** Mes 6.


* **Temas principales:**
* APIs REST, GET, POST, PUT, DELETE, JSON y autenticación.


* Webhooks.


* n8n, Make y Zapier.


* Bases de datos e integraciones.


* Automatización de procesos.




* **Proyecto de la fase:** Automatizar el flujo de pedidos (compra, pago, registro, stock, envío, comunicación al cliente y actualización de datos).

### Llama / Mistral
Basándote únicamente en el documento que compartiste:

**FASE 5 — Automatización**

**Mes en el que empieza:** Meses 6-8

**Temas principales:**
* APIs REST, GET, POST, PUT, DELETE, JSON y autenticación.
* Webhooks.
* n8n, Make y Zapier.
* Bases de datos e integraciones.
* Automatización de procesos.

**Proyecto de la fase:**
* Automatizar el flujo de pedidos: compra → pago → registro → stock → envío → comunicación al cliente → actualización de datos.

## Observaciones

Modelo	Comportamiento	Fortalezas	Limitaciones	Notas
Claude	Respuesta en prosa fluida, sin bullets ni encabezados	Fácil de leer de corrido, tono natural	Al no usar formato estructurado, es un poco más difícil "escanear" rápido si solo querés un dato puntual	El único que integró los 3 datos pedidos en un texto corrido en vez de secciones separadas
ChatGPT	Estructura clara con encabezados en negrita y bullets	Fácil de escanear, bien organizado	Ninguna relevante	Formato prolijo y consistente
Gemini	Estructura con bullets, pero con saltos de línea excesivos entre cada ítem (se ve "roto" en el archivo)	Contenido correcto	El formato Markdown quedó desprolijo — muchos renglones vacíos entre bullets que no deberían estar ahí	Es un defecto de renderizado/formato, no de contenido — pero afecta la legibilidad real del archivo
Llama/Mistral	Estructura clara con encabezados, respetó literalmente "Meses 6-8" como aparece en tu documento	Formato limpio, sin errores	Ninguna relevante	Es el que más citó literal la redacción original del plan ("Meses 6-8" en vez de reformular a "mes 6 a 8")

## Qué me llamó la atención

en una tarea de fidelidad a un documento, la precisión del contenido dejó de ser el diferenciador (los 4 la resolvieron bien) — lo que varió fue la calidad del formato de salida. Gemini, que en las tareas anteriores venía bien, acá tuvo el único problema real: bullets con espaciado roto que hacen el texto menos prolijo de leer. Es un buen ejemplo de que "acertar el contenido" y "entregar un resultado usable" no son siempre lo mismo.
