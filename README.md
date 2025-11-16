# 4_Tutorial_Taller_Estructuras-de-Datos_v2_JavaScript
Taller 4 de JavaScript para compañeros del SENA de la carrera de ADSO

# Sección 11: Estructuras de Datos - Arrays 🗃️

Hasta ahora hemos trabajado con variables que guardan un solo dato a la vez (un número, un texto, un booleano). ¡Pero el verdadero poder de la programación se desata cuando podemos trabajar con colecciones de datos! Los **arrays** son la estructura de datos más fundamental y versátil de JavaScript.

---

## 11.1 Concepto de Array

- **¿Qué es?** Un array es una **colección ordenada y mutable** de elementos.  
  - **Colección:** Puede contener múltiples valores.  
  - **Ordenada:** Los elementos mantienen un orden específico. El primer elemento que añades es el primero, el segundo es el segundo, y así sucesivamente.  
  - **Mutable:** ¡Puedes cambiar su contenido! Puedes añadir, eliminar o modificar elementos después de haberlo creado.  

Un array puede contener elementos de diferentes tipos de datos, ¡incluso otros arrays!

**Creación de Arrays:**  
Se crean usando corchetes `[]` y separando los elementos con comas.

### Ejemplo Básico:

```javascript
// Array vacío
const arrayVacio = [];
console.log(`Array vacío: ${JSON.stringify(arrayVacio)}`);

// Array de números enteros
const notas = [5, 4, 3, 5, 2];
console.log(`Array de notas: ${JSON.stringify(notas)}`);

// Array de cadenas de texto (strings)
const aprendices = ["Carlos", "Ana", "Luis"];
console.log(`Array de aprendices: ${JSON.stringify(aprendices)}`);

// Array con tipos de datos mixtos
const miArrayMixto = ["Carlos", 25, 1.75, true];
console.log(`Array mixto: ${JSON.stringify(miArrayMixto)}`);
```

---

## 11.2 Acceso a Elementos por Índice

Como los arrays son ordenados, cada elemento tiene una posición o índice. ¡En JavaScript, los índices **empiezan en 0**!  

- El primer elemento tiene **índice** `0`.  
- El segundo elemento tiene índice `1`.  
- ... y así sucesivamente.  

También puedes usar **índices negativos** (con librerías o manualmente, pero nativamente JS no soporta negativos directamente; usa `at()` en ES2022+ o calcula manualmente).  

Para acceder a un elemento, usas el nombre del array seguido de corchetes con el índice dentro: `nombreArray[indice]`.

### Ejemplos Prácticos:

```javascript
const programasSena = ["ADSO", "Multimedia", "Contabilidad", "Mecatrónica"];
// Índices:            0         1             2              3
// Índices Neg (con .at()): -4        -3            -2             -1

// Accediendo con índices positivos
const primerPrograma = programasSena[0];
console.log(`El primer programa en el array es: ${primerPrograma}`);

const tercerPrograma = programasSena[2];
console.log(`El tercer programa en el array es: ${tercerPrograma}`);

// Accediendo con índices negativos (usando .at() en ES2022+)
const ultimoPrograma = programasSena.at(-1);
console.log(`El último programa en el array es: ${ultimoPrograma}`);

const penultimoPrograma = programasSena.at(-2);
console.log(`El penúltimo programa en el array es: ${penultimoPrograma}`);

// Si intentas acceder a un índice que no existe, retorna undefined
// console.log(programasSena[4]); // undefined
```

---

## 11.3 Slicing (Rebanadas) de Arrays

El "slicing" te permite obtener un **sub-array** (una porción o "rebanada") de un array existente usando `.slice()`.

Sintaxis: `nombreArray.slice(inicio, fin)`  

- `inicio`: El índice donde empieza la rebanada (**incluido**). Si se omite, es 0.  
- `fin`: El índice donde termina la rebanada (**no incluido**). Si se omite, es hasta el final.  
- No soporta `paso` directamente; usa bucles o librerías para eso.

### Ejemplos Prácticos:

```javascript
const numeros = [0, 10, 20, 30, 40, 50, 60];
// Índices: 0,  1,  2,  3,  4,  5,  6

// Desde el índice 2 hasta el 4 (el 5 no se incluye)
const subArray1 = numeros.slice(2, 5);
console.log(`numeros.slice(2,5) -> ${JSON.stringify(subArray1)}`); // [20, 30, 40]

// Desde el principio hasta el índice 2 (no incluido)
const subArray2 = numeros.slice(0, 2);
console.log(`numeros.slice(0,2) -> ${JSON.stringify(subArray2)}`); // [0, 10]

// Desde el índice 4 hasta el final
const subArray3 = numeros.slice(4);
console.log(`numeros.slice(4) -> ${JSON.stringify(subArray3)}`); // [40, 50, 60]

// Toda el array (una copia)
const copiaArray = numeros.slice();
console.log(`numeros.slice() -> ${JSON.stringify(copiaArray)}`);

// Con índices negativos (últimos elementos)
const subArrayNeg = numeros.slice(-3);
console.log(`numeros.slice(-3) -> ${JSON.stringify(subArrayNeg)}`); // [40, 50, 60]
```

---

## 11.4 Mutabilidad y Operaciones con Arrays

**Mutabilidad:**  
Los arrays son **mutables**, lo que significa que puedes cambiar sus elementos después de crearlos. Puedes reasignar un valor a un elemento específico usando su índice.

```javascript
let misCalificaciones = [3.0, 4.5, 2.5];
console.log(`Calificaciones originales: ${JSON.stringify(misCalificaciones)}`);

// Modificar la última calificación (índice 2 o -1 con .at())
misCalificaciones[2] = 3.5;
console.log(`Calificaciones modificadas: ${JSON.stringify(misCalificaciones)}`);
```

### Operaciones con Arrays:

- **Longitud (`.length`)**: Devuelve el número de elementos en el array.  
- **Concatenación (`.concat()`)**: Une dos arrays para crear uno nuevo.  
- **Repetición**: No directo; usa bucles o `Array.from()`.  
- **Pertenencia (`.includes()`)**: Verifica si un elemento existe en el array.

### Ejemplos Prácticos:

```javascript
const herramientasAdso = ["Python", "Java", "SQL"];
const herramientasMultimedia = ["Photoshop", "Illustrator"];

// Longitud
console.log(`Número de herramientas de ADSO: ${herramientasAdso.length}`);

// Concatenación
const todasLasHerramientas = herramientasAdso.concat(herramientasMultimedia);
console.log(`Todas las herramientas: ${JSON.stringify(todasLasHerramientas)}`);

// Repetición (usando spread y concat)
const repetirPython = Array(3).fill("Python");
console.log(`Repitiendo Python: ${JSON.stringify(repetirPython)}`);

// Pertenencia
console.log(`¿'Java' es una herramienta de ADSO? ${herramientasAdso.includes("Java")}`); // true
console.log(`¿'Figma' es una herramienta de ADSO? ${!herramientasAdso.includes("Figma")}`); // true
```

### Iteración sobre Arrays:
El bucle `for...of` es la forma más común y natural de recorrer cada elemento de un array. También puedes usar `.forEach()`.

```javascript
const calificacionesTrimestre = [4.2, 3.8, 5.0, 2.9, 4.5];
let sumaCalificaciones = 0.0;

console.log("\nRecorriendo calificaciones:");
for (let nota of calificacionesTrimestre) {
  console.log(`- Nota: ${nota}`);
  sumaCalificaciones += nota;
}

const promedio = sumaCalificaciones / calificacionesTrimestre.length;
console.log(`La suma es: ${sumaCalificaciones}`);
console.log(`El promedio es: ${promedio.toFixed(2)}`);
```

---

## ¡A Tu Teclado!

**Ejercicio 11.1:**  
Crea un array llamado `mercado` con 5 productos que comprarías (como strings).  
Imprime el primer y el último producto del array.  
Imprime la cantidad de productos en tu array de mercado usando `.length`.  
Modifica el segundo producto del array por otro diferente.  
Imprime el array completo para ver el cambio.

```javascript
const mercado = ["Manzanas", "Bananos", "Leche", "Pan", "Huevos"];
console.log(`Primer producto: ${mercado[0]}`);
console.log(`Último producto: ${mercado.at(-1)}`);
console.log(`Cantidad de productos: ${mercado.length}`);

mercado[1] = "Naranjas"; // Modificar segundo
console.log(`Array modificado: ${JSON.stringify(mercado)}`);
```

---

**Ejercicio 11.2:**  
Crea un array `numeros` con valores `[10, 20, 30, 40, 50]`.  
Usa slicing para obtener:  
- Los primeros 3 números.  
- Los últimos 2 números.  
- Del segundo al cuarto (índices 1 a 3).  
Imprime cada sub-array.

```javascript
const numeros = [10, 20, 30, 40, 50];
const primerosTres = numeros.slice(0, 3);
console.log(`Primeros 3: ${JSON.stringify(primerosTres)}`);

const ultimosDos = numeros.slice(-2);
console.log(`Últimos 2: ${JSON.stringify(ultimosDos)}`);

const delSegundoAlCuarto = numeros.slice(1, 4);
console.log(`Del segundo al cuarto: ${JSON.stringify(delSegundoAlCuarto)}`);
```

---

## 11.5 Métodos de Arrays (Métodos Mutables)

JavaScript ofrece métodos para manipular arrays. Algunos modifican el array original (mutables), otros retornan uno nuevo (inmutables).

- **.push(elemento)**: Añade al final.  
- **.pop()**: Elimina y retorna el último.  
- **.unshift(elemento)**: Añade al inicio.  
- **.shift()**: Elimina y retorna el primero.  
- **.splice(indice, cuantosEliminar, ...elementosNuevos)**: Inserta/elimina en posición específica.  
- **.sort()**: Ordena el array (modifica original).  
- **.reverse()**: Invierte el array (modifica original).

### Ejemplos Prácticos:

```javascript
let tareas = ["Estudiar", "Comer"];
console.log(`Tareas iniciales: ${JSON.stringify(tareas)}`);

// .push()
tareas.push("Dormir");
console.log(`Después de push: ${JSON.stringify(tareas)}`);

// .pop()
const tareaEliminada = tareas.pop();
console.log(`Tarea eliminada: ${tareaEliminada}`);
console.log(`Después de pop: ${JSON.stringify(tareas)}`);

// .unshift()
tareas.unshift("Despertar");
console.log(`Después de unshift: ${JSON.stringify(tareas)}`);

// .shift()
const primeraTareaEliminada = tareas.shift();
console.log(`Primera tarea eliminada: ${primeraTareaEliminada}`);
console.log(`Después de shift: ${JSON.stringify(tareas)}`);

// .splice()
tareas.splice(1, 0, "Ejercicio"); // Insertar en índice 1
console.log(`Después de splice (insertar): ${JSON.stringify(tareas)}`);

tareas.splice(2, 1); // Eliminar 1 elemento en índice 2
console.log(`Después de splice (eliminar): ${JSON.stringify(tareas)}`);

// .sort() y .reverse()
const numerosDesordenados = [5, 3, 8, 1];
numerosDesordenados.sort((a, b) => a - b); // Orden ascendente
console.log(`Ordenados: ${JSON.stringify(numerosDesordenados)}`);

numerosDesordenados.reverse();
console.log(`Invertidos: ${JSON.stringify(numerosDesordenados)}`);
```

---

## ¡A Tu Teclado!

**Ejercicio 11.3:**  
Crea un array `colores` con ["rojo", "azul", "verde"].  
Añade "amarillo" al final con `.push()`.  
Elimina el primer color con `.shift()`.  
Inserta "negro" en el índice 1 con `.splice()`.  
Imprime el array final.

```javascript
let colores = ["rojo", "azul", "verde"];
colores.push("amarillo");
console.log(`Después de push: ${JSON.stringify(colores)}`);

colores.shift();
console.log(`Después de shift: ${JSON.stringify(colores)}`);

colores.splice(1, 0, "negro");
console.log(`Después de splice: ${JSON.stringify(colores)}`);
```

---

## 11.6 Métodos de Arrays (Métodos Inmutables)

- **.concat(otroArray)**: Retorna un nuevo array unido.  
- **.join(separador)**: Une elementos en una string.  
- **.slice(inicio, fin)**: Retorna sub-array.  
- **.indexOf(elemento)**: Retorna índice del elemento o -1 si no existe.  
- **.includes(elemento)**: Retorna true si existe.  
- **.filter(callback)**: Retorna nuevo array con elementos que cumplen condición.  
- **.map(callback)**: Retorna nuevo array transformado.  
- **.reduce(callback, inicial)**: Reduce a un valor único.  
- **.find(callback)**: Retorna primer elemento que cumple condición.  
- **.some(callback)** / **.every(callback)**: Verifica si algunos/todos cumplen condición.

### Ejemplos Prácticos:

```javascript
const frutas = ["manzana", "banano", "naranja"];
const verduras = ["zanahoria", "lechuga"];

// .concat()
const alimentos = frutas.concat(verduras);
console.log(`Alimentos: ${JSON.stringify(alimentos)}`);

// .join()
const cadenaFrutas = frutas.join(", ");
console.log(`Cadena de frutas: ${cadenaFrutas}`);

// .indexOf()
const indiceBanano = frutas.indexOf("banano");
console.log(`Índice de banano: ${indiceBanano}`);

// .filter()
const numerosPares = [1, 2, 3, 4, 5].filter(num => num % 2 === 0);
console.log(`Números pares: ${JSON.stringify(numerosPares)}`);

// .map()
const mayusculas = frutas.map(fruta => fruta.toUpperCase());
console.log(`Mayúsculas: ${JSON.stringify(mayusculas)}`);

// .reduce()
const sumaNumeros = [1, 2, 3, 4].reduce((acc, num) => acc + num, 0);
console.log(`Suma: ${sumaNumeros}`);

// .find()
const primeraLarga = frutas.find(fruta => fruta.length > 6);
console.log(`Primera fruta larga: ${primeraLarga}`);

// .some() / .every()
const tieneManzana = frutas.some(fruta => fruta === "manzana");
console.log(`¿Tiene manzana? ${tieneManzana}`);
const todasLargas = frutas.every(fruta => fruta.length > 5);
console.log(`¿Todas largas? ${todasLargas}`);
```

---

## ¡A Tu Teclado!

**Ejercicio 11.4:**  
Crea un array `numeros` = [1, 2, 3, 4, 5].  
Usa `.map()` para duplicar cada número.  
Usa `.filter()` para obtener solo pares.  
Usa `.reduce()` para sumar todos.  
Imprime resultados.

```javascript
const numeros = [1, 2, 3, 4, 5];
const duplicados = numeros.map(num => num * 2);
console.log(`Duplicados: ${JSON.stringify(duplicados)}`);

const pares = numeros.filter(num => num % 2 === 0);
console.log(`Pares: ${JSON.stringify(pares)}`);

const suma = numeros.reduce((acc, num) => acc + num, 0);
console.log(`Suma: ${suma}`);
```

---

# Sección 12: Concepto de Tupla (en JS: Arrays Inmutables)

En JS no hay tuplas nativas, pero podemos simularlas con arrays y `Object.freeze()` para hacerlos inmutables.

### Ejemplo Básico:

```javascript
const coordenadas = Object.freeze([10.5, 20.3]);
console.log(`Coordenadas: ${JSON.stringify(coordenadas)}`);

// Intentar modificar da error en strict mode
// coordenadas[0] = 15; // Error si usas 'use strict'
```

---


# Sección 13: Estructuras de Datos - Diccionarios (Objetos y `Map`) 

Los **diccionarios** son una de las estructuras de datos más potentes de JavaScript. A diferencia de los **arrays** que se organizan por un **índice numérico**, los diccionarios se organizan mediante un sistema de **clave-valor**.

---

### 13.1 Concepto de Diccionario

* **¿Qué es?** Un diccionario es una **colección de pares clave-valor**, donde:
    * **Colección:** Almacena múltiples datos.
    * **Ordenada por inserción (desde ES2020):** Tanto los objetos `{}` como `Map` **mantienen el orden en que se insertaron los elementos**.
    * **Mutable:** Puedes añadir, modificar y eliminar pares clave-valor.
    * **Pares Clave-Valor:** Cada elemento consta de:
        * Una **clave (`key`)**: Identificador único.  
          - En **objetos `{}`**: Solo permite `strings` o `Symbol`.  
          - En **`Map()`**: Permite **cualquier tipo** (números, objetos, funciones, arrays, etc.).
        * Un **valor (`value`)**: El dato asociado. Puede ser **cualquier tipo** (número, string, array, objeto, función, etc.).

> **Analogía:** Es como un contacto en tu celular: buscas por **nombre** (clave) para obtener **teléfono, email, etc.** (valor).

---

### Creación de Diccionarios

#### 1. **Objetos `{}`** → Ideal para datos estructurados simples

```javascript
// Objeto vacío
const objetoVacio = {};
console.log(`Objeto vacío: ${JSON.stringify(objetoVacio)}`);

// Objeto con datos
const aprendiz = {
  nombre: "Ana María",
  edad: 22,
  programa: "ADSO",
  activo: true,
  notas: [4.5, 5.0, 4.8]
};
console.log(`Aprendiz: ${JSON.stringify(aprendiz, null, 2)}`);

// Claves dinámicas (útil con variables)
const campo = "puntuacion";
const estudiante = {
  nombre: "Luis",
  [campo]: 4.8,
  fecha: new Date().toISOString().split('T')[0]
};
console.log(`Estudiante con clave dinámica: ${JSON.stringify(estudiante)}`);
```

#### 2. **`Map()`** → Ideal para claves complejas o iteración frecuente

```javascript
// Map vacío
const mapaVacio = new Map();

// Map con datos iniciales
const notasMap = new Map([
  ["Carlos", 4.5],
  ["Ana", 5.0],
  ["Luis", 3.8],
  ["María", 4.9]
]);
console.log(`Notas Map: ${JSON.stringify([...notasMap])}`);

// Claves de cualquier tipo
const claveObjeto = { id: 1 };
const claveFuncion = function() { return "hola"; };
const claveArray = [1, 2, 3];

const mapaComplejo = new Map();
mapaComplejo.set(claveObjeto, "Objeto como clave");
mapaComplejo.set("texto", "Valor string");
mapaComplejo.set(123, "Número como clave");
mapaComplejo.set(claveFuncion, "Función como clave");
mapaComplejo.set(claveArray, "Array como clave");

console.log(`Map con claves complejas: ${JSON.stringify([...mapaComplejo], null, 2)}`);
```

---

### 13.2 Acceso, Modificación y Eliminación

#### Con **Objetos `{}`**

```javascript
const persona = {
  nombre: "María",
  edad: 25,
  ciudad: "Bogotá"
};

// Acceso
console.log(`Nombre: ${persona.nombre}`);
console.log(`Ciudad: ${persona["ciudad"]}`);

// Acceso con variable
const campoAcceso = "edad";
console.log(`Edad: ${persona[campoAcceso]}`);

// Modificación
persona.edad = 26;
persona["ciudad"] = "Medellín";
persona.redSocial = "@maria_dev"; // Añadir nueva clave
console.log(`Actualizado: ${JSON.stringify(persona)}`);

// Eliminación
delete persona.ciudad;
console.log(`Sin ciudad: ${JSON.stringify(persona)}`);

// Verificar existencia
console.log(`¿Tiene edad? ${"edad" in persona}`);     // true
console.log(`¿Tiene email? ${"email" in persona}`);   // false
```

#### Con **`Map()`**

```javascript
const calificaciones = new Map();
calificaciones.set("Juan", 4.2);
calificaciones.set("Pedro", 3.9);
calificaciones.set("Laura", 5.0);

// Acceso
console.log(`Nota de Juan: ${calificaciones.get("Juan")}`);

// Modificación (usa .set() nuevamente)
calificaciones.set("Juan", 4.7);
console.log(`Map actualizado: ${JSON.stringify([...calificaciones])}`);

// Eliminación
calificaciones.delete("Pedro");
console.log(`Sin Pedro: ${JSON.stringify([...calificaciones])}`);

// Verificar existencia y tamaño
console.log(`¿Tiene Juan? ${calificaciones.has("Juan")}`); // true
console.log(`Tamaño: ${calificaciones.size}`);             // 2
console.log(`Claves: ${[...calificaciones.keys()]}`);
console.log(`Valores: ${[...calificaciones.values()]}`);
```

---

### 13.3 Iteración sobre Objetos y `Map`

#### Iterar **Objetos**

```javascript
const config = {
  tema: "oscuro",
  idioma: "es",
  notificaciones: true,
  volumen: 75
};

// 1. Solo claves
console.log("Claves:");
for (let clave in config) {
  if (config.hasOwnProperty(clave)) {
    console.log(`- ${clave}`);
  }
}

// 2. Solo valores
console.log("Valores:");
Object.values(config).forEach(valor => {
  console.log(`- ${valor}`);
});

// 3. Pares clave-valor (recomendado)
console.log("Pares clave-valor:");
Object.entries(config).forEach(([clave, valor]) => {
  console.log(`  ${clave}: ${valor}`);
});
```

#### Iterar **`Map`**

```javascript
const agenda = new Map([
  ["Lunes", "Reunión equipo ADSO"],
  ["Miércoles", "Capacitación JavaScript"],
  ["Viernes", "Entrega proyecto final"]
]);

// 1. Con for...of (más limpio)
console.log("Agenda semanal:");
for (let [dia, actividad] of agenda) {
  console.log(`- ${dia}: ${actividad}`);
}

// 2. Con .forEach()
agenda.forEach((actividad, dia) => {
  console.log(`  ${dia} → ${actividad}`);
});
```

---

### 13.4 Métodos Útiles

| Operación         | Objeto `{}`                  | `Map()`                       |
|-------------------|------------------------------|-------------------------------|
| Tamaño            | `Object.keys(obj).length`    | `mapa.size`                   |
| Claves            | `Object.keys(obj)`           | `[...mapa.keys()]`            |
| Valores           | `Object.values(obj)`         | `[...mapa.values()]`          |
| Pares             | `Object.entries(obj)`        | `[...mapa.entries()]`         |
| Copia superficial | `{...obj}`                   | `new Map(mapa)`               |

```javascript
// Ejemplo: Copiar un Map
const copiaNotas = new Map(notasMap);
console.log(`Copia: ${JSON.stringify([...copiaNotas])}`);
```

---

## ¡A Tu Teclado!

### Ejercicio 13.1: Registro de Aprendices (con Objeto)

Crea un objeto `aprendiz` con:
- `nombre`, `documento`, `programa`, `notaFinal`, `activo`

Imprime todos los datos usando `Object.entries()`.

```javascript
const aprendiz = {
  nombre: "Carlos Andrés Pérez",
  documento: "1001234567",
  programa: "Análisis y Desarrollo de Software",
  notaFinal: 4.6,
  activo: true
};

console.log("=== Registro del Aprendiz ===");
Object.entries(aprendiz).forEach(([clave, valor]) => {
  console.log(`  ${clave.charAt(0).toUpperCase() + clave.slice(1)}: ${valor}`);
});
```

---

### Ejercicio 13.2: Calificaciones por Estudiante (con `Map`)

Crea un `Map` llamado `calificaciones` con 4 estudiantes y sus notas.  
Luego:
1. Añade un nuevo estudiante.
2. Modifica la nota de uno existente.
3. Elimina un estudiante.
4. Imprime el `Map` final con formato bonito.

```javascript
const calificaciones = new Map([
  ["Juan Camilo", 4.2],
  ["Pedro López", 3.9],
  ["Laura Martínez", 5.0],
  ["Sofía Ramírez", 4.7]
]);

// 1. Añadir
calificaciones.set("Andrés Gómez", 4.1);

// 2. Modificar
calificaciones.set("Juan Camilo", 4.5);

// 3. Eliminar
calificaciones.delete("Pedro López");

// 4. Imprimir
console.log("=== Calificaciones Finales ===");
for (let [nombre, nota] of calificaciones) {
  const estado = nota >= 3.5 ? "Aprobado" : "Reprobado";
  console.log(`- ${nombre}: ${nota} [${estado}]`);
}
```

---

### Ejercicio 13.3: Contador de Palabras (con Objeto)

Dada una frase, cuenta cuántas veces aparece cada palabra usando un **objeto**.

```javascript
const frase = "el sol sale por el este y se pone por el oeste";
const contador = {};

frase.toLowerCase().split(" ").forEach(palabra => {
  contador[palabra] = (contador[palabra] || 0) + 1;
});

console.log("Frecuencia de palabras:");
Object.entries(contador).forEach(([palabra, veces]) => {
  console.log(`  "${palabra}": ${veces} vez${veces > 1 ? 'es' : ''}`);
});
```

---

## Resumen: ¿Cuándo usar qué?

| Necesidad                              | Usa...           | ¿Por qué? |
|----------------------------------------|------------------|---------|
| Datos estructurados simples             | **Objeto `{}`**  | Sintaxis limpia, acceso con `.prop` |
| Claves que no son strings               | **`Map()`**      | Soporta objetos, funciones, etc. |
| Iterar mucho o mantener orden           | **`Map()`**      | `for...of` nativo, `.size` directo |
| JSON o configuración                    | **Objeto `{}`**  | Fácil de serializar con `JSON.stringify` |
| Evitar colisiones accidentales          | **`Map()`**      | Claves son referencias exactas |

---

**¡Los diccionarios son la base de la programación estructurada en JavaScript!**  
Domínalos y podrás manejar datos reales como nunca antes.

---

# Sección 14: Estructuras de Datos - Conjuntos (`Set`) 🧩

Hemos visto **arrays** (ordenados, mutables) y cómo simular tuplas inmutables con `Object.freeze()`. Ahora conoceremos los **conjuntos** (`Set`), una estructura de datos nativa de JavaScript optimizada para:

- **Unicidad**: No permite duplicados  
- **Operaciones matemáticas rápidas**: unión, intersección, diferencia  
- **Verificación de pertenencia eficiente**: `has()` es más rápido que `includes()` en arrays grandes

---

### ¿Qué es un `Set`?

Un `Set` es una **colección de valores únicos** sin orden definido.  
Cada valor aparece **solo una vez**, aunque lo intentes añadir varias veces.

```javascript
const miSet = new Set([1, 2, 2, 3, 3, 3]);
console.log(miSet); // Set {1, 2, 3}
```

---

### Características clave

| Característica       | Detalle |
|----------------------|--------|
| **Valores únicos**   | Duplicados se ignoran automáticamente |
| **Sin índices**      | No puedes acceder por `set[0]` |
| **Sin orden garantizado** | No confíes en el orden de inserción (aunque en la práctica suele mantenerse) |
| **Cualquier tipo**   | Puede contener números, strings, objetos, funciones, etc. |
| **Métodos poderosos** | `.add()`, `.delete()`, `.has()`, `.size`, etc. |

---

### Creación de `Set`

```javascript
// Vacío
const conjuntoVacio = new Set();

// Desde array (elimina duplicados)
const programas = new Set(["ADSO", "Multimedia", "ADSO", "Contabilidad"]);
console.log(programas); // Set {"ADSO", "Multimedia", "Contabilidad"}

// Directo
const lenguajes = new Set();
lenguajes.add("JavaScript");
lenguajes.add("Python");
lenguajes.add("Java");
```

---

### Operaciones básicas

```javascript
const herramientas = new Set();

// Añadir
herramientas.add("VS Code");
herramientas.add("Git");
herramientas.add("VS Code"); // Ignorado

// Verificar
console.log(herramientas.has("Git")); // true

// Eliminar
herramientas.delete("Git");

// Tamaño
console.log(herramientas.size); // 1

// Limpiar todo
herramientas.clear();
console.log(herramientas.size); // 0
```

---

### Operaciones matemáticas (¡Lo más poderoso!)

```javascript
const frontend = new Set(["HTML", "CSS", "JavaScript", "React"]);
const backend = new Set(["Node.js", "Python", "SQL", "JavaScript"]);

// Unión: todos los elementos
const fullstack = new Set([...frontend, ...backend]);

// Intersección: elementos comunes
const comunes = new Set([...frontend].filter(x => backend.has(x)));

// Diferencia: solo en frontend
const soloFrontend = new Set([...frontend].filter(x => !backend.has(x)));

// Diferencia simétrica: en uno pero no en ambos
const diferenciaSimetrica = new Set([
  ...[...frontend].filter(x => !backend.has(x)),
  ...[...backend].filter(x => !frontend.has(x))
]);

console.log("Fullstack:", [...fullstack]);
console.log("Comunes:", [...comunes]);
console.log("Solo Frontend:", [...soloFrontend]);
```

---

### ¡A Tu Teclado!

#### Ejercicio 14.1: Elimina Duplicados
```javascript
const votos = ["Ana", "Luis", "Ana", "Pedro", "Luis", "Ana"];
const votantesUnicos = new Set(votos);
console.log("Votantes únicos:", [...votantesUnicos]);
console.log("Total:", votantesUnicos.size);
```

#### Ejercicio 14.2: Habilidades Full-Stack
```javascript
const habilidadesDev = new Set(["JavaScript", "HTML", "CSS", "Git"]);
const habilidadesData = new Set(["Python", "SQL", "Pandas", "JavaScript"]);

// ¿Qué habilidades tiene en común?
// ¿Cuáles son únicas de cada rol?
// ¿Qué habilidades totales tiene un Full-Stack?
```

---

**¡Los `Set` son ideales cuando necesitas unicidad y operaciones rápidas!**  
Úsalos para: eliminar duplicados, verificar pertenencia, comparar colecciones.
```

¡Muy bien! Has cubierto las estructuras de datos fundamentales en JavaScript. Las arrays, objetos y sets son herramientas que usarás constantemente.
