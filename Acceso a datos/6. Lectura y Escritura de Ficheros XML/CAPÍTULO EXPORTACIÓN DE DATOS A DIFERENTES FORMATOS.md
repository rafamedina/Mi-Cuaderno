

## 🎯 Objetivos de Aprendizaje

Al finalizar este capítulo, serás capaz de:

✅ Entender qué son CSV, XML y JSON y cuándo usar cada uno  
✅ Escribir archivos en formato CSV con Java  
✅ Escribir archivos en formato XML con Java  
✅ Escribir archivos en formato JSON con Java  
✅ Comparar ventajas y desventajas de cada formato  
✅ Elegir el formato adecuado según el contexto  
✅ Gestionar excepciones en operaciones de escritura  

---

## 📖 Índice del Capítulo

1. [Introducción a los Formatos de Exportación](#1-introducción)
2. [Formato CSV](#2-formato-csv)
3. [Formato XML](#3-formato-xml)
4. [Formato JSON](#4-formato-json)
5. [Comparación de Formatos](#5-comparación)
6. [Ejemplo Práctico: Gestión de Tienda](#6-ejemplo-práctico)
7. [Ejercicios Guiados](#7-ejercicios)

---

## 1. Introducción a los Formatos de Exportación

### ¿Por qué exportar datos?

En el desarrollo de aplicaciones, frecuentemente necesitamos:

📤 **Exportar datos** para que otros sistemas los consuman  
📊 **Generar informes** legibles para usuarios  
🔄 **Intercambiar información** entre aplicaciones  
💾 **Crear copias de seguridad** en formatos estándar  
📈 **Analizar datos** en herramientas especializadas  

### Los tres formatos más comunes

```
┌─────────────┬──────────────────────┬────────────────────────┐
│   FORMATO   │    MEJOR PARA        │    HERRAMIENTAS        │
├─────────────┼──────────────────────┼────────────────────────┤
│    CSV      │ • Hojas de cálculo   │ • Excel                │
│             │ • Datos tabulares    │ • Google Sheets        │
│             │ • Análisis simple    │ • LibreOffice          │
├─────────────┼──────────────────────┼────────────────────────┤
│    XML      │ • Intercambio datos  │ • Navegadores web      │
│             │ • Configuraciones    │ • Sistemas empresas    │
│             │ • Documentos compl.  │ • Herramientas XML     │
├─────────────┼──────────────────────┼────────────────────────┤
│    JSON     │ • APIs web           │ • Aplicaciones web     │
│             │ • Configuraciones    │ • JavaScript           │
│             │ • Datos anidados     │ • APIs REST            │
└─────────────┴──────────────────────┴────────────────────────┘
```

---

## 2. Formato CSV (Comma-Separated Values)

### 🔍 ¿Qué es CSV?

**CSV** es un formato de texto plano que representa datos tabulares (como una tabla) donde:
- Cada línea es una fila
- Los valores están separados por un delimitador (coma, punto y coma, tabulador)

### Ejemplo visual

**Tabla de productos:**

| ID | Nombre | Precio | Stock |
|----|--------|--------|-------|
| 1 | Laptop | 899.99 | 15 |
| 2 | Ratón | 19.99 | 50 |
| 3 | Teclado | 45.00 | 30 |

**Mismo contenido en CSV:**

```csv
ID;Nombre;Precio;Stock
1;Laptop;899.99;15
2;Ratón;19.99;50
3;Teclado;45.00;30
```

### ✅ Ventajas de CSV

✅ **Simplicidad**: Formato muy simple de leer y escribir  
✅ **Universal**: Compatible con Excel, Sheets, bases de datos  
✅ **Ligero**: Archivos pequeños, rápidos de procesar  
✅ **Estándar**: Ampliamente soportado  

### ❌ Desventajas de CSV

❌ **Limitado**: Solo datos tabulares (no jerarquías)  
❌ **Sin tipos**: Todo es texto (no hay números, fechas, booleanos nativos)  
❌ **Ambigüedad**: Problemas con comas o saltos de línea en los datos  
❌ **Sin metadata**: No guarda información sobre la estructura  

### 🎯 ¿Cuándo usar CSV?

✅ Exportar datos para Excel o Google Sheets  
✅ Generar informes financieros o estadísticos  
✅ Intercambiar datos tabulares simples  
✅ Cuando la simplicidad y compatibilidad son prioritarias  

### 📝 Sintaxis básica en Java

```java
// Estructura básica para escribir CSV
BufferedWriter writer = new BufferedWriter(new FileWriter("archivo.csv"));

// Escribir encabezado
writer.write("ID;Nombre;Precio;Stock");
writer.newLine();

// Escribir datos
writer.write("1;Laptop;899.99;15");
writer.newLine();

writer.close();
```

**⚠️ IMPORTANTE:**
- En España se usa ";" como separador (Excel lo reconoce)
- En países anglosajones se usa "," como separador
- Siempre usar `newLine()` en lugar de `\n` (portabilidad)

---

## 3. Formato XML (eXtensible Markup Language)

### 🔍 ¿Qué es XML?

**XML** es un lenguaje de marcado que representa datos en estructura jerárquica mediante etiquetas, similar a HTML pero más estricto y extensible.

### Ejemplo visual

**Datos de un producto:**

```
Producto:
  - ID: 1
  - Nombre: Laptop Gaming
  - Precio: 899.99
  - Stock: 15
  - Categoría: Informática
```

**Mismo contenido en XML:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<producto>
  <id>1</id>
  <nombre>Laptop Gaming</nombre>
  <precio>899.99</precio>
  <stock>15</stock>
  <categoria>Informática</categoria>
</producto>
```

### ✅ Ventajas de XML

✅ **Estructurado**: Soporta jerarquías y datos complejos  
✅ **Autodocumentado**: Las etiquetas describen los datos  
✅ **Validación**: Se puede validar con esquemas (XSD, DTD)  
✅ **Estándar**: Usado en sistemas empresariales y servicios web  
✅ **Extensible**: Fácil de añadir nuevos campos  

### ❌ Desventajas de XML

❌ **Verboso**: Mucho texto repetido (etiquetas de apertura/cierre)  
❌ **Pesado**: Archivos grandes  
❌ **Complejo**: Requiere más código para parsear  
❌ **Menos legible**: Más difícil de leer que JSON para humanos  

### 🎯 ¿Cuándo usar XML?

✅ Intercambio de datos entre sistemas empresariales  
✅ Configuraciones de aplicaciones  
✅ Servicios web SOAP  
✅ Cuando se necesita validación estricta  
✅ Documentos con estructura compleja  

### 📝 Sintaxis básica en Java

```java
// Estructura básica para escribir XML
BufferedWriter writer = new BufferedWriter(new FileWriter("archivo.xml"));

// Declaración XML
writer.write("<?xml version=\"1.0\" encoding=\"UTF-8\"?>");
writer.newLine();

// Elemento raíz
writer.write("<producto>");
writer.newLine();

// Elementos hijos
writer.write("  <id>1</id>");
writer.newLine();
writer.write("  <nombre>Laptop Gaming</nombre>");
writer.newLine();

// Cierre elemento raíz
writer.write("</producto>");
writer.newLine();

writer.close();
```

**⚠️ IMPORTANTE:**
- Siempre incluir declaración XML en la primera línea
- Las etiquetas deben estar bien formadas (abrir y cerrar)
- Escapar caracteres especiales: `<` → `&lt;`, `>` → `&gt;`, `&` → `&amp;`
- Usar UTF-8 como encoding

---

## 4. Formato JSON (JavaScript Object Notation)

### 🔍 ¿Qué es JSON?

**JSON** es un formato ligero de intercambio de datos que usa una notación basada en objetos JavaScript. Es fácil de leer para humanos y fácil de parsear para máquinas.

### Ejemplo visual

**Datos de un producto:**

```
Producto:
  - ID: 1
  - Nombre: Laptop Gaming
  - Precio: 899.99
  - Stock: 15
  - Categoría: Informática
  - Características: ["16GB RAM", "512GB SSD", "RTX 3060"]
```

**Mismo contenido en JSON:**

```json
{
  "id": 1,
  "nombre": "Laptop Gaming",
  "precio": 899.99,
  "stock": 15,
  "categoria": "Informática",
  "caracteristicas": [
    "16GB RAM",
    "512GB SSD",
    "RTX 3060"
  ]
}
```

### ✅ Ventajas de JSON

✅ **Ligero**: Menos verboso que XML  
✅ **Legible**: Fácil de leer para humanos  
✅ **Flexible**: Soporta objetos, arrays, tipos de datos  
✅ **Estándar web**: Nativo en JavaScript, ideal para APIs  
✅ **Rápido**: Parsing eficiente  

### ❌ Desventajas de JSON

❌ **Sin validación nativa**: No tiene esquemas como XML (aunque existe JSON Schema)  
❌ **Sin comentarios**: No permite comentarios en el formato estándar  
❌ **Menos soporte legacy**: Algunos sistemas antiguos no lo soportan  

### 🎯 ¿Cuándo usar JSON?

✅ APIs REST y servicios web modernos  
✅ Configuraciones de aplicaciones web  
✅ Intercambio de datos entre frontend y backend  
✅ Aplicaciones móviles  
✅ Cuando la ligereza y legibilidad son importantes  

### 📝 Sintaxis básica en Java

```java
// Estructura básica para escribir JSON
BufferedWriter writer = new BufferedWriter(new FileWriter("archivo.json"));

// Objeto JSON
writer.write("{");
writer.newLine();

// Propiedades
writer.write("  \"id\": 1,");
writer.newLine();
writer.write("  \"nombre\": \"Laptop Gaming\",");
writer.newLine();
writer.write("  \"precio\": 899.99");
writer.newLine();

// Cierre objeto
writer.write("}");
writer.newLine();

writer.close();
```

**⚠️ IMPORTANTE:**
- Las claves (keys) DEBEN ir entre comillas dobles
- Los strings DEBEN ir entre comillas dobles
- NO poner coma después del último elemento
- Escapar comillas dentro de strings: `"texto con \"comillas\""`
- Tipos de datos: números (sin comillas), strings, booleanos, null, arrays, objetos

---

## 5. Comparación de Formatos

### Tabla comparativa completa

```
┌──────────────────┬─────────┬─────────┬─────────┐
│   CARACTERÍSTICA │   CSV   │   XML   │  JSON   │
├──────────────────┼─────────┼─────────┼─────────┤
│ Legibilidad      │   ★★★   │   ★★☆   │  ★★★★   │
│ Tamaño archivo   │  Pequeño│  Grande │  Medio  │
│ Velocidad        │  Rápido │  Lento  │  Rápido │
│ Jerarquías       │    NO   │   SÍ    │   SÍ    │
│ Tipos de datos   │    NO   │   NO    │   SÍ    │
│ Excel            │   ★★★★  │   ★☆☆   │   ☆☆☆   │
│ APIs web         │   ☆☆☆   │   ★★☆   │  ★★★★   │
│ Curva aprendizaje│  Fácil  │  Media  │  Fácil  │
│ Validación       │    NO   │  ★★★★   │   ★☆☆   │
└──────────────────┴─────────┴─────────┴─────────┘
```

### Ejemplo comparativo: Lista de productos

**CSV:**
```csv
ID;Nombre;Precio;Stock
1;Laptop;899.99;15
2;Ratón;19.99;50
```
📊 **Tamaño:** ~50 bytes  
⚡ **Ideal para:** Abrir en Excel  

**XML:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<productos>
  <producto>
    <id>1</id>
    <nombre>Laptop</nombre>
    <precio>899.99</precio>
    <stock>15</stock>
  </producto>
  <producto>
    <id>2</id>
    <nombre>Ratón</nombre>
    <precio>19.99</precio>
    <stock>50</stock>
  </producto>
</productos>
```
📊 **Tamaño:** ~240 bytes  
⚡ **Ideal para:** Intercambio entre sistemas  

**JSON:**
```json
{
  "productos": [
    {
      "id": 1,
      "nombre": "Laptop",
      "precio": 899.99,
      "stock": 15
    },
    {
      "id": 2,
      "nombre": "Ratón",
      "precio": 19.99,
      "stock": 50
    }
  ]
}
```
📊 **Tamaño:** ~140 bytes  
⚡ **Ideal para:** API REST  

### 🎯 Guía de decisión

**Usa CSV cuando:**
- ✅ Necesites abrir datos en Excel
- ✅ Los datos sean tabulares simples
- ✅ Quieras el archivo más ligero posible
- ✅ No necesites jerarquías

**Usa XML cuando:**
- ✅ Necesites validación estricta
- ✅ Integración con sistemas legacy
- ✅ Documentos con estructura compleja
- ✅ Servicios web SOAP

**Usa JSON cuando:**
- ✅ Desarrolles una API REST
- ✅ Aplicación web moderna
- ✅ Necesites balance entre legibilidad y tamaño
- ✅ Trabajes con JavaScript

---

## 6. Ejemplo Práctico: Gestión de Tienda

En la siguiente sección trabajaremos con un ejemplo completo de una tienda que gestiona productos. Veremos cómo exportar el inventario a los tres formatos.

### Clases del ejemplo

```
Producto
  - id: int
  - nombre: String
  - precio: double
  - stock: int
  - categoria: String
  - descripcion: String
  
Tienda
  - productos: ArrayList<Producto>
  - agregarProducto()
  - exportarCSV()
  - exportarXML()
  - exportarJSON()
```

---

## 7. Ejercicios Guiados

Al final del capítulo encontrarás ejercicios progresivos para practicar cada formato:

1. **Nivel Básico:** Exportar lista simple de estudiantes
2. **Nivel Intermedio:** Exportar catálogo de libros con categorías
3. **Nivel Avanzado:** Exportar sistema de reservas con relaciones

---

## 📚 Recursos Adicionales

- [RFC 4180 - CSV Specification](https://tools.ietf.org/html/rfc4180)
- [W3C - XML Specification](https://www.w3.org/XML/)
- [JSON.org - Introducing JSON](https://www.json.org/)
- [Oracle - Java I/O Tutorial](https://docs.oracle.com/javase/tutorial/essential/io/)

---

## ✅ Autoevaluación

Antes de continuar, asegúrate de poder responder:

1. ¿Qué formato elegirías para exportar datos a Excel? ¿Por qué?
2. ¿Cuál es la diferencia principal entre XML y JSON?
3. ¿Por qué JSON es más popular en aplicaciones web modernas?
4. ¿Qué formato soporta mejor datos jerárquicos complejos?
5. ¿Cómo se escapan caracteres especiales en XML?

---

