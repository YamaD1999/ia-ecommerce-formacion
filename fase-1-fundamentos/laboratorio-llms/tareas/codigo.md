# Tarea: Código

## Prompt usado

Escribí una función en JavaScript que valide si se puede agregar un producto al carrito de compras. La función recibe: la cantidad que el cliente quiere comprar, el stock disponible del producto, y un mínimo de compra de 1 unidad y máximo de 10 unidades por producto. Debe devolver si la operación es válida y, si no lo es, el motivo específico.

## Respuestas

### Claude
```javascript
function validarAgregarAlCarrito(cantidad, stockDisponible, minimo = 1, maximo = 10) {
  if (!Number.isInteger(cantidad)) {
    return { valido: false, motivo: 'La cantidad debe ser un número entero' };
  }

  if (cantidad < minimo) {
    return { valido: false, motivo: `La cantidad mínima de compra es ${minimo} unidad(es)` };
  }

  if (cantidad > maximo) {
    return { valido: false, motivo: `La cantidad máxima de compra es ${maximo} unidades por producto` };
  }

  if (cantidad > stockDisponible) {
    return { valido: false, motivo: `No hay stock suficiente. Stock disponible: ${stockDisponible}` };
  }

  return { valido: true, motivo: null };
}
```

Ejemplos de uso:

```javascript
console.log(validarAgregarAlCarrito(5, 10));  
// { valido: true, motivo: null }

console.log(validarAgregarAlCarrito(0, 10));  
// { valido: false, motivo: 'La cantidad mínima de compra es 1 unidad(es)' }

console.log(validarAgregarAlCarrito(15, 20)); 
// { valido: false, motivo: 'La cantidad máxima de compra es 10 unidades por producto' }

console.log(validarAgregarAlCarrito(5, 3));   
// { valido: false, motivo: 'No hay stock suficiente. Stock disponible: 3' }
```

Algunas decisiones de diseño:

- **Devuelve un objeto** (`{ valido, motivo }`) en vez de solo `true/false`, para que puedas mostrarle el motivo exacto al usuario en la UI.
- **Los parámetros `minimo` y `maximo` tienen valores por defecto** (1 y 10), pero podés pasarlos explícitamente si en algún momento varían por producto.
- **Valida que `cantidad` sea un entero** — evita casos raros como `2.5` unidades.
- El orden de validaciones prioriza primero las reglas de negocio fijas (mínimo/máximo) y después el stock, pero si preferís que el stock se chequee primero, es un cambio de una línea.

¿Querés que la adapte para que también valide el caso de `stockDisponible <= 0` con un mensaje tipo "sin stock", o que la integre a alguna estructura de carrito que ya tengas (por ejemplo, sumando lo que ya hay en el carrito antes de agregar más)?

### ChatGPT
Podés resolverlo con una función que valide cada condición y devuelva un objeto con `valido` y el `motivo`:

```javascript
function validarProducto(cantidad, stock) {
    const MINIMO = 1;
    const MAXIMO = 10;

    if (cantidad < MINIMO) {
        return {
            valido: false,
            motivo: "La cantidad mínima de compra es 1 unidad."
        };
    }

    if (cantidad > MAXIMO) {
        return {
            valido: false,
            motivo: "La cantidad máxima de compra es 10 unidades."
        };
    }

    if (cantidad > stock) {
        return {
            valido: false,
            motivo: `No hay stock suficiente. Solo quedan ${stock} unidades.`
        };
    }

    return {
        valido: true,
        motivo: "El producto puede agregarse al carrito."
    };
}
```

### Ejemplos

```javascript
console.log(validarProducto(3, 10));
```

Resultado:

```javascript
{
    valido: true,
    motivo: "El producto puede agregarse al carrito."
}
```

Si pide más unidades de las disponibles:

```javascript
console.log(validarProducto(8, 5));
```

Resultado:

```javascript
{
    valido: false,
    motivo: "No hay stock suficiente. Solo quedan 5 unidades."
}
```

Si supera el máximo:

```javascript
console.log(validarProducto(15, 20));
```

Resultado:

```javascript
{
    valido: false,
    motivo: "La cantidad máxima de compra es de 10 unidades."
}
```

**Detalle importante:** puse primero las reglas de cantidad mínima/máxima y después el stock. Así, si alguien intenta comprar `15` unidades pero hay `20` disponibles, el motivo será correctamente que **supera el máximo permitido**, no que hay stock insuficiente.


### Gemini
Aquí tienes una función en JavaScript que realiza las validaciones solicitadas. Devuelve un objeto con un booleano (`isValid`) indicando si la operación es exitosa y un mensaje descriptivo en caso de que falle.

```javascript
function validarProductoCarrito(quantity, stock) {
  const MIN_COMPRA = 1;
  const MAX_COMPRA = 10;

  // Validación de tipos de datos
  if (typeof quantity !== 'number' || typeof stock !== 'number' || isNaN(quantity) || isNaN(stock)) {
    return {
      isValid: false,
      reason: "Los valores de cantidad y stock deben ser numéricos válidos."
    };
  }

  // Validar mínimo de compra
  if (quantity < MIN_COMPRA) {
    return {
      isValid: false,
      reason: `La cantidad mínima de compra es de ${MIN_COMPRA} unidad(es).`
    };
  }

  // Validar máximo por producto
  if (quantity > MAX_COMPRA) {
    return {
      isValid: false,
      reason: `La cantidad máxima permitida por producto es de ${MAX_COMPRA} unidades.`
    };
  }

  // Validar stock disponible
  if (quantity > stock) {
    return {
      isValid: false,
      reason: `No hay suficiente stock disponible. Stock actual: ${stock}.`
    };
  }

  // Si pasa todas las validaciones
  return {
    isValid: true,
    reason: "El producto se puede agregar correctamente al carrito."
  };
}

```

### Ejemplos de uso

Puedes probar la función con diferentes escenarios:

```javascript
// 1. Caso válido (dentro de los rangos y con stock suficiente)
console.log(validarProductoCarrito(3, 15)); 
// Resultado: { isValid: true, reason: 'El producto se puede agregar correctamente al carrito.' }

// 2. Supera el máximo permitido por producto
console.log(validarProductoCarrito(12, 20)); 
// Resultado: { isValid: false, reason: 'La cantidad máxima permitida por producto es de 10 unidades.' }

// 3. Supera el stock disponible
console.log(validarProductoCarrito(5, 2)); 
// Resultado: { isValid: false, reason: 'No hay suficiente stock disponible. Stock actual: 2.' }

// 4. Cantidad menor al mínimo de compra
console.log(validarProductoCarrito(0, 10)); 
// Resultado: { isValid: false, reason: 'La cantidad mínima de compra es de 1 unidad(es).' }

```

### Llama / Mistral
Acá tenés una función simple, clara y lista para usar en tu carrito:

```javascript
function validarAgregarAlCarrito(cantidadDeseada, stockDisponible) {
  const MINIMO = 1;
  const MAXIMO = 10;

  // 1. Validar que sea un número válido
  if (typeof cantidadDeseada !== 'number' || !Number.isInteger(cantidadDeseada)) {
    return {
      valido: false,
      motivo: 'La cantidad debe ser un número entero.'
    };
  }

  // 2. Validar mínimo
  if (cantidadDeseada < MINIMO) {
    return {
      valido: false,
      motivo: `La cantidad mínima de compra es de ${MINIMO} unidad.`
    };
  }

  // 3. Validar máximo permitido por producto
  if (cantidadDeseada > MAXIMO) {
    return {
      valido: false,
      motivo: `La cantidad máxima permitida por producto es de ${MAXIMO} unidades.`
    };
  }

  // 4. Validar stock
  if (cantidadDeseada > stockDisponible) {
    if (stockDisponible === 0) {
      return {
        valido: false,
        motivo: 'El producto está sin stock.'
      };
    }
    return {
      valido: false,
      motivo: `Stock insuficiente. Solo quedan ${stockDisponible} unidades disponibles.`
    };
  }

  // Si pasó todo, es válido
  return {
    valido: true,
    motivo: null
  };
}
```

### Cómo se usa

```javascript
console.log(validarAgregarAlCarrito(3, 20));
// { valido: true, motivo: null }

console.log(validarAgregarAlCarrito(0, 20));
// { valido: false, motivo: 'La cantidad mínima de compra es de 1 unidad.' }

console.log(validarAgregarAlCarrito(12, 50));
// { valido: false, motivo: 'La cantidad máxima permitida por producto es de 10 unidades.' }

console.log(validarAgregarAlCarrito(5, 2));
// { valido: false, motivo: 'Stock insuficiente. Solo quedan 2 unidades disponibles.' }

console.log(validarAgregarAlCarrito(1, 0));
// { valido: false, motivo: 'El producto está sin stock.' }
```

**Lógica que aplica:**
1.  Primero verifica que la cantidad sea un entero.
2.  Verifica que esté entre 1 y 10.
3.  Por último verifica que haya stock suficiente.

Si querés que lo integre directamente a tu lógica de carrito con `alert` o para deshabilitar el botón de "Agregar", te lo adapto.

## Observaciones

Modelo	Comportamiento	Fortalezas	Limitaciones	Notas
Claude	Valida que la cantidad sea un entero, usa parámetros con valores por defecto (minimo=1, maximo=10)	La función queda reusable — si mañana un producto tiene otro máximo, no hay que tocar el código	No maneja el caso especial de stock en cero con mensaje propio	Termina preguntando si querés integrarla a tu carrito real — el único que ofreció ir más allá del pedido puntual
ChatGPT	No valida el tipo de dato (asume que cantidad ya viene como número válido)	Código más corto y directo, fácil de leer	Si le pasás un string o un decimal, no lo detecta — puede fallar silenciosamente	Es el único que explica por qué eligió ese orden de validaciones (evitar mensaje de error incorrecto)
Gemini	Valida tipo de dato con typeof e isNaN, pero no rechaza decimales (2.5 pasaría)	Es el más defensivo contra datos "sucios" que no sean números	Usa nombres en inglés (isValid, reason) mezclado con el resto en español — inconsistencia de idioma	El único que valida explícitamente NaN, útil si el dato viene de un input mal parseado
Llama/Mistral	Valida entero (como Claude) y además distingue el caso "sin stock" (0) con un mensaje distinto a "stock insuficiente"	Es el más completo en experiencia de usuario — el mensaje que le llegaría a tu cliente es más preciso según el caso	Constantes fijas adentro de la función, no reusable sin editar el código	También ofrece integrarlo a tu lógica real, como Claude

## Qué me llamó la atención

Claude y Llama tienden a ofrecerte el siguiente paso ("¿querés que lo integre a tu carrito?"), mientras que ChatGPT y Gemini entregan la respuesta cerrada y completa tal como la pediste, sin abrir la conversación. Y en cuanto a calidad técnica pura, para este caso específico Llama fue el más robusto (validación de tipo + caso de stock en cero) — justo el que muchos asumirían "más débil" por ser el open-source gratuito. Ese es un buen dato para anotar: la fama de un modelo no siempre predice el resultado en una tarea puntual.
