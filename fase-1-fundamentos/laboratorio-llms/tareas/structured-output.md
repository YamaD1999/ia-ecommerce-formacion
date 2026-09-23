# Tarea: Structured output / instrucciones estrictas

## Prompt usado

Devolveme un JSON con la información de estos 3 productos de mi ecommerce de aromas: (1) Vela de Lavanda 200g $4.200, (2) Difusor de Jazmín 100ml $5.800, (3) Sahumerio de Palo Santo x20 $1.500. El JSON debe tener exactamente estos campos por producto: nombre, precio, categoria. No agregues ningún campo extra. No agregues texto antes ni después del JSON. No uses la palabra "producto" en ningún valor del JSON.

## Respuestas

### Claude
[
  {
    "nombre": "Vela de Lavanda 200g",
    "precio": 4200,
    "categoria": "Velas"
  },
  {
    "nombre": "Difusor de Jazmín 100ml",
    "precio": 5800,
    "categoria": "Difusores"
  },
  {
    "nombre": "Sahumerio de Palo Santo x20",
    "precio": 1500,
    "categoria": "Sahumerios"
  }
]

### ChatGPT
[
{
"nombre": "Vela de Lavanda 200g",
"precio": 4200,
"categoria": "Velas"
},
{
"nombre": "Difusor de Jazmín 100ml",
"precio": 5800,
"categoria": "Difusores"
},
{
"nombre": "Sahumerio de Palo Santo x20",
"precio": 1500,
"categoria": "Sahumerios"
}
]


### Gemini
[
{
"nombre": "Vela de Lavanda 200g",
"precio": "$4.200",
"categoria": "Velas"
},
{
"nombre": "Difusor de Jazmín 100ml",
"precio": "$5.800",
"categoria": "Difusores"
},
{
"nombre": "Sahumerio de Palo Santo x20",
"precio": "$1.500",
"categoria": "Sahumerios"
}
]

### Llama / Mistral
[
  {"nombre": "Vela de Lavanda 200g", "precio": 4200, "categoria": "Velas"},
  {"nombre": "Difusor de Jazmín 100ml", "precio": 5800, "categoria": "Difusores"},
  {"nombre": "Sahumerio de Palo Santo x20", "precio": 1500, "categoria": "Sahumerios"}
]

## Observaciones

Modelo	Comportamiento	Fortalezas	Limitaciones	Notas
Claude	JSON limpio, precio como número (4200)	Cumple el schema al pie de la letra, formato correcto para usar directo en código	Ninguna relevante	Indentado con 2 espacios, legible
ChatGPT	JSON limpio, precio como número	Igual de correcto que Claude	Indentación irregular (sin sangría consistente) — cosmético, no afecta el parseo	Funcionalmente idéntico a Claude
Gemini	JSON limpio en estructura, pero precio es un string ("$4.200") en vez de número	Ninguna sobre los otros — de hecho es el único con un problema real	Esto rompe el uso práctico: si intentás sumar precios, ordenar por precio o hacer cualquier cálculo, "$4.200" no es un número, vas a tener que parsearlo primero	Es el único de los 4 que no devolvió el precio como dato numérico limpio
Llama/Mistral	JSON limpio, precio como número	Correcto y además el más compacto (todo en una línea por objeto)	Ninguna relevante	Formato distinto (compacto vs. multilínea) pero funcionalmente igual a Claude/ChatGPT

## Qué me llamó la atención

en las tareas anteriores todos "cumplían" más o menos bien, acá Gemini se equivocó en algo concreto y verificable — devolvió el precio con el símbolo $ y el separador de miles como texto, cuando vos necesitás un número para poder usarlo en cualquier lógica de tu ecommerce (calcular totales, filtrar por rango de precio, etc.). Los otros 3 respetaron el tipo de dato correcto sin que se lo tuvieras que aclarar explícitamente.

Buen dato para el README final: para generar datos estructurados que después vas a usar en código (no solo mostrar), conviene revisar siempre el tipo de cada campo — no asumir que "parece JSON válido" significa "sirve tal cual".
