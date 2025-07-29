# Clase 4: Aplicando CSS - Estilos Básicos y Selectores

## 📌 Objetivos de la Clase
- Aprender las tres formas de aplicar estilos CSS (en línea, interno y externo)
- Dominar selectores básicos (elemento, clase, id) para aplicar estilos
- Conocer propiedades esenciales para dar estilo al texto y fondos
- Aprender la sintaxis correcta y buenas prácticas en CSS
- Crear tu primera hoja de estilos para dar estilo a la biografía del Video 1
- Organizar tu archivo CSS para proyectos grandes

## 🎨 ¿Qué es CSS?

CSS significa **Cascading Style Sheets** (Hojas de Estilo en Cascada). Es el lenguaje que utilizamos para describir la presentación de un documento escrito en HTML.

Mientras que HTML define la estructura y contenido de una página web (como el esqueleto del cuerpo humano), CSS define cómo se ve ese contenido (como la piel, la ropa y el estilo del cuerpo).

### Ventajas de usar CSS:
- **Separación de contenido y presentación**: El HTML se enfoca en la estructura, CSS en el diseño
- **Consistencia**: Establece un estilo uniforme en todas las páginas
- **Mantenimiento**: Cambia el diseño de todo el sitio modificando un solo archivo
- **Rendimiento**: Los navegadores cachean los archivos CSS, acelerando la carga de páginas

## 📁 Tres formas de aplicar CSS

### 1. CSS en línea (inline)
Se aplica directamente en el atributo `style` de un elemento HTML.

```html
<p style="color: blue; font-size: 18px;">Este es un párrafo con estilo en línea</p>
```

**Cuándo usarlo**: Para estilos muy específicos y excepcionales (no recomendado para uso general).

### 2. CSS interno (embedded)
Se define dentro de la etiqueta `<style>` en la sección `<head>` del documento.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>CSS Interno</title>
    <style>
        body {
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        p {
            color: #666;
            line-height: 1.5;
        }
    </style>
</head>
<body>
    <h1>Título Principal</h1>
    <p>Párrafo con estilo interno</p>
</body>
</html>
```

**Cuándo usarlo**: Para estilos específicos de una sola página.

### 3. CSS externo
El método recomendado para la mayoría de los proyectos. Los estilos se definen en un archivo separado con extensión `.css`.

**Archivo styles.css:**
```css
body {
    background-color: #f0f0f0;
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

h1 {
    color: #333;
    text-align: center;
    padding: 20px;
}

p {
    color: #666;
    line-height: 1.5;
    padding: 0 20px;
}
```

**Archivo HTML:**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>CSS Externo</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Título Principal</h1>
    <p>Párrafo con estilo externo</p>
</body>
</html>
```

#### Ventajas del CSS externo:
- Separa completamente estructura y presentación
- Permite mantener un estilo consistente en todo el sitio
- Los navegadores cachean el archivo CSS, mejorando el rendimiento
- Facilita los cambios globales (modificas un archivo y se actualiza todo el sitio)

## 🧩 Sintaxis y selectores básicos de CSS

### Sintaxis básica
```css
selector {
    propiedad: valor;
    /* Más propiedades */
}
```

### Selectores comunes

#### 1. Selector de elemento:
```css
/* Aplica a todas las etiquetas p */
p {
    color: #333;
    font-size: 16px;
}
```

#### 2. Selector de clase:
```css
/* Aplica a cualquier elemento con class="texto-destacado" */
.texto-destacado {
    background-color: yellow;
    font-weight: bold;
}
```

```html
<p class="texto-destacado">Este texto está destacado</p>
```

#### 3. Selector de ID:
```css
/* Aplica al elemento con id="cabecera" */
#cabecera {
    text-align: center;
    padding: 20px;
}
```

```html
<div id="cabecera">Contenido de la cabecera</div>
```

### Reglas importantes sobre selectores:
- Las clases pueden usarse en múltiples elementos
- Los IDs deben ser únicos en toda la página
- Puedes combinar selectores: `h1, h2, h3 { color: blue; }`
- Los selectores de clase e ID pueden usarse con elementos: `p.texto-destacado { ... }`

## 🖌️ Propiedades esenciales para texto y colores

### Propiedades de texto:
```css
.texto-ejemplo {
    color: #333;                /* Color del texto */
    font-family: Arial, sans-serif; /* Tipo de letra */
    font-size: 16px;            /* Tamaño de fuente */
    font-weight: bold;          /* Peso de la fuente (normal, bold, 400, 700) */
    font-style: italic;         /* Estilo (normal, italic) */
    text-align: center;         /* Alineación (left, right, center, justify) */
    text-decoration: underline; /* Decoración (none, underline, overline, line-through) */
    line-height: 1.5;           /* Altura de línea */
    text-transform: uppercase;  /* Transformación (none, uppercase, lowercase, capitalize) */
    letter-spacing: 1px;        /* Espacio entre letras */
    word-spacing: 2px;          /* Espacio entre palabras */
}
```

### Modelos de color:
```css
.ejemplo-colores {
    color: red;                 /* Nombre del color */
    color: #ff0000;             /* Hexadecimal */
    color: rgb(255, 0, 0);     /* RGB */
    color: rgba(255, 0, 0, 0.5); /* RGBA (con transparencia) */
    color: hsl(0, 100%, 50%);  /* HSL */
    color: hsla(0, 100%, 50%, 0.5); /* HSLA (con transparencia) */
}
```

### Propiedades de fondo:
```css
.ejemplo-fondo {
    background-color: #f0f0f0;  /* Color de fondo */
    background-image: url("imagen.jpg"); /* Imagen de fondo */
    background-repeat: no-repeat; /* Repetición (repeat, no-repeat, repeat-x, repeat-y) */
    background-position: center; /* Posición (left, center, right, top, bottom, valores en px/% */
    background-size: cover;     /* Tamaño (auto, cover, contain, valores específicos) */
}
```

## 📋 Sintaxis correcta y buenas prácticas

### Sintaxis correcta:
- Siempre usa punto y coma después de cada declaración
- Organiza por grupos lógicos (reset, variables, elementos base, secciones)
- Usa comentarios para dividir secciones
- Mantén una indentación consistente

```css
/* ==============================
   RESET
   ============================== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* ==============================
   VARIABLES
   ============================== */
:root {
    --color-primary: #3498db;
    --color-secondary: #2c3e50;
    --color-accent: #e74c3c;
    --font-main: 'Arial', sans-serif;
}

/* ==============================
   ELEMENTOS BASE
   ============================== */
body {
    font-family: var(--font-main);
    line-height: 1.6;
    color: var(--color-secondary);
    background-color: #f8f9fa;
    padding: 20px;
}

h1, h2, h3, h4, h5, h6 {
    margin-bottom: 15px;
    color: var(--color-secondary);
}

p {
    margin-bottom: 20px;
}

a {
    color: var(--color-primary);
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}
```

### Buenas prácticas:
- Usa variables CSS para colores y fuentes comunes
- Evita el uso excesivo de `!important`
- Usa clases descriptivas (evita nombres como "rojo", "grande")
- Organiza tu CSS en secciones lógicas
- Mantén tu código limpio con comentarios y formato consistente
- Usa el modelo `box-sizing: border-box` para simplificar el cálculo de tamaños

## 🏆 Ejercicio práctico: Dar estilo a la biografía creada en el Video 1

En la Clase 1 creaste una página de biografía. Ahora le daremos estilo usando CSS externo.

### Pasos para completar el ejercicio:

1. Crea un archivo llamado `styles.css` en la misma carpeta que tu `biografia.html`

2. Vincula el CSS en el `<head>` de tu HTML:
```html
<link rel="stylesheet" href="styles.css">
```

3. Agrega los siguientes estilos a tu archivo CSS:

```css
/* styles.css */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: #f5f5f5;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: #333;
    padding: 20px;
}

h1 {
    color: #2c3e50;
    text-align: center;
    margin: 20px 0;
    padding-bottom: 10px;
    border-bottom: 2px solid #3498db;
}

h2 {
    color: #2980b9;
    margin: 25px 0 15px;
}

p {
    margin-bottom: 15px;
    font-size: 18px;
}

ul {
    margin-left: 20px;
    margin-bottom: 20px;
}

li {
    margin-bottom: 8px;
}

strong {
    color: #c0392b;
    font-weight: bold;
}

em {
    color: #27ae60;
    font-style: italic;
}

mark {
    background-color: #f1c40f;
    padding: 2px 5px;
}

/* Estilos adicionales para mejorar la apariencia */
body {
    max-width: 800px;
    margin: 0 auto;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
    border-radius: 5px;
    padding: 30px;
}

a {
    color: #3498db;
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}
```

4. Personaliza los colores y estilos según tus preferencias
5. ¡Prueba diferentes combinaciones de colores y tipografías!

## 📎 Recurso adicional: Cheat Sheet de CSS básico

### Sintaxis básica:
```css
selector {
    propiedad: valor;
}
```

### Selectores:
- `p` - Selector de elemento
- `.clase` - Selector de clase
- `#id` - Selector de ID
- `h1, h2, h3` - Selector múltiple
- `p span` - Selector descendiente

### Propiedades de texto:
- `color` - Color del texto
- `font-family` - Tipo de letra
- `font-size` - Tamaño de fuente
- `font-weight` - Grosor de la fuente
- `text-align` - Alineación del texto
- `line-height` - Altura de línea

### Propiedades de color:
- `color: red;` - Por nombre
- `color: #ff0000;` - Hexadecimal
- `color: rgb(255, 0, 0);` - RGB
- `color: rgba(255, 0, 0, 0.5);` - RGBA (con transparencia)

### Propiedades de fondo:
- `background-color` - Color de fondo
- `background-image` - Imagen de fondo
- `background-repeat` - Repetición del fondo
- `background-position` - Posición del fondo
- `background-size` - Tamaño del fondo

## 📌 Consejo: Organizar tu archivo CSS para proyectos grandes

Cuando trabajas en proyectos grandes, es crucial mantener tu CSS organizado para facilitar el mantenimiento y colaboración. Aquí te comparto un esquema efectivo:

### Estructura recomendada para CSS en proyectos grandes:

```css
/* ==============================
   1. RESET Y NORMALIZACIÓN
   ============================== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* ==============================
   2. VARIABLES CSS (THEME)
   ============================== */
:root {
    /* Colores */
    --primary-color: #3498db;
    --secondary-color: #2c3e50;
    --accent-color: #e74c3c;
    --light-color: #ecf0f1;
    --dark-color: #2c3e50;
    
    /* Tipografía */
    --font-main: 'Arial', sans-serif;
    --font-heading: 'Georgia', serif;
    --font-size-base: 16px;
    --line-height: 1.6;
    
    /* Espaciado */
    --spacing-xs: 0.5rem;
    --spacing-sm: 1rem;
    --spacing-md: 1.5rem;
    --spacing-lg: 2rem;
    --spacing-xl: 3rem;
}

/* ==============================
   3. ELEMENTOS BASE
   ============================== */
body {
    font-family: var(--font-main);
    font-size: var(--font-size-base);
    line-height: var(--line-height);
    color: var(--dark-color);
    background-color: var(--light-color);
}

h1, h2, h3, h4, h5, h6 {
    margin-bottom: var(--spacing-sm);
    color: var(--secondary-color);
    line-height: 1.2;
}

p {
    margin-bottom: var(--spacing-md);
}
```

### Beneficios de esta estructura:
- **Mantenibilidad**: Facilita encontrar y modificar estilos específicos
- **Consistencia**: Usa variables para colores, espaciado y tipografía
- **Escalabilidad**: Agregar nuevas secciones es sencillo y organizado
- **Colaboración**: Otros desarrolladores pueden entender la estructura rápidamente
- **Eficiencia**: Reduce la duplicación de estilos y facilita la reutilización

### Consejos adicionales:
- Nunca mezcles estilos de diferentes categorías en el mismo bloque
- Usa comentarios claros para dividir secciones
- Mantén una longitud de línea razonable (70-80 caracteres)
- Ordena las propiedades alfabéticamente dentro de cada regla
- Evita selectores demasiado específicos que dificulten la sobreescritura

## 🏆 Reto Adicional: Crear un Diseño de Blog Personal

¡Felicidades por completar los ejercicios de CSS básico! Aquí tienes un reto adicional para que practiques aún más:

### 📚 Descripción del Reto
Crea una página web que simule un blog personal. Debe incluir:

- Un diseño con CSS externo bien organizado siguiendo la estructura recomendada
- Un encabezado (`<header>`) con:
  - Título del blog
  - Breve descripción
  - Navegación básica (Inicio, Acerca de, Contacto)
- Contenido principal (`<main>`) con:
  - Al menos 2 artículos de blog
  - Cada artículo debe tener título, fecha y contenido
  - Usa clases para estilos consistentes
- Un sidebar (`<aside>`) con:
  - Foto de perfil
  - Breve biografía
  - Enlaces a redes sociales
- Un pie de página (`<footer>`) con:
  - Copyright
  - Enlace a política de privacidad

### 📌 Ejemplo de Cómo Debería Verse

**Archivo HTML (blog.html):**
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Blog Personal</title>
    <link rel="stylesheet" href="blog.css">
</head>
<body>
    <header>
        <h1>Mi Blog de Tecnología</h1>
        <p>Aprendiendo y compartiendo sobre desarrollo web</p>
        <nav>
            <ul>
                <li><a href="#">Inicio</a></li>
                <li><a href="#">Acerca de</a></li>
                <li><a href="#">Contacto</a></li>
            </ul>
        </nav>
    </header>

    <div class="container">
        <main>
            <article class="post">
                <h2>Primeros pasos en HTML</h2>
                <p class="post-date">Publicado el 15 de mayo de 2024</p>
                <p>En este artículo comparto mis primeros pasos aprendiendo HTML...</p>
            </article>
            
            <article class="post">
                <h2>Introducción a CSS</h2>
                <p class="post-date">Publicado el 22 de mayo de 2024</p>
                <p>Descubre cómo CSS transforma tus páginas HTML...</p>
            </article>
        </main>

        <aside class="sidebar">
            <img src="perfil.jpg" alt="Foto de perfil">
            <h3>Sobre mí</h3>
            <p>Soy un apasionado de la tecnología y el desarrollo web...</p>
            <h3>Redes sociales</h3>
            <ul>
                <li><a href="#">Twitter</a></li>
                <li><a href="#">LinkedIn</a></li>
                <li><a href="#">GitHub</a></li>
            </ul>
        </aside>
    </div>

    <footer>
        <p>&copy; 2024 Mi Blog Personal. Todos los derechos reservados.</p>
        <a href="#">Política de privacidad</a>
    </footer>
</body>
</html>
```

**Archivo CSS (blog.css):**
```css
/* ==============================
   1. RESET Y NORMALIZACIÓN
   ============================== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* ==============================
   2. VARIABLES CSS (THEME)
   ============================== */
:root {
    --primary-color: #2c3e50;
    --secondary-color: #3498db;
    --accent-color: #e74c3c;
    --light-color: #f8f9fa;
    --dark-color: #2c3e50;
    --font-main: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    --font-heading: 'Georgia', serif;
    --font-size-base: 16px;
    --line-height: 1.6;
    --spacing-xs: 0.5rem;
    --spacing-sm: 1rem;
    --spacing-md: 1.5rem;
    --spacing-lg: 2rem;
    --spacing-xl: 3rem;
}

/* ==============================
   3. ELEMENTOS BASE
   ============================== */
body {
    font-family: var(--font-main);
    line-height: var(--line-height);
    color: #333;
    background-color: var(--light-color);
}

h1, h2, h3, h4, h5, h6 {
    font-family: var(--font-heading);
    margin-bottom: var(--spacing-sm);
}

p {
    margin-bottom: var(--spacing-md);
}

a {
    color: var(--secondary-color);
    text-decoration: none;
}

a:hover {
    text-decoration: underline;
}

/* ==============================
   4. COMPONENTES REUTILIZABLES
   ============================== */
.btn {
    display: inline-block;
    padding: var(--spacing-xs) var(--spacing-sm);
    background-color: var(--secondary-color);
    color: white;
    border-radius: 4px;
    transition: all 0.3s ease;
}

.btn:hover {
    background-color: var(--dark-color);
}

.card {
    background: white;
    border-radius: 5px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    padding: var(--spacing-md);
    margin-bottom: var(--spacing-lg);
}

/* ==============================
   5. LAYOUT PRINCIPAL
   ============================== */
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: var(--spacing-md);
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: var(--spacing-lg);
}

/* ==============================
   6. HEADER
   ============================== */
header {
    background-color: var(--primary-color);
    color: white;
    text-align: center;
    padding: var(--spacing-xl) var(--spacing-md);
}

header h1 {
    font-size: 2.5rem;
    margin-bottom: var(--spacing-sm);
}

header p {
    font-size: 1.2rem;
    margin-bottom: var(--spacing-lg);
}

nav ul {
    list-style: none;
    display: flex;
    justify-content: center;
    gap: var(--spacing-lg);
}

nav a {
    color: white;
    font-weight: bold;
    padding: var(--spacing-xs) var(--spacing-sm);
    border-radius: 4px;
    transition: background-color 0.3s ease;
}

nav a:hover {
    background-color: rgba(255,255,255,0.2);
    text-decoration: none;
}

/* ==============================
   7. MAIN CONTENT
   ============================== */
main {
    background: white;
    border-radius: 8px;
    padding: var(--spacing-lg);
}

.post {
    border-bottom: 1px solid #eee;
    padding-bottom: var(--spacing-lg);
    margin-bottom: var(--spacing-lg);
}

.post:last-child {
    border-bottom: none;
    margin-bottom: 0;
}

.post h2 {
    color: var(--primary-color);
    font-size: 1.8rem;
    margin-bottom: var(--spacing-xs);
}

.post-date {
    color: #666;
    font-size: 0.9rem;
    font-style: italic;
    margin-bottom: var(--spacing-md);
}

/* ==============================
   8. SIDEBAR
   ============================== */
.sidebar {
    background: white;
    border-radius: 8px;
    padding: var(--spacing-lg);
    height: fit-content;
}

.sidebar img {
    width: 100%;
    max-width: 150px;
    border-radius: 50%;
    display: block;
    margin: 0 auto var(--spacing-md);
}

.sidebar h3 {
    color: var(--primary-color);
    border-bottom: 2px solid var(--secondary-color);
    padding-bottom: var(--spacing-xs);
    margin-bottom: var(--spacing-sm);
}

.sidebar ul {
    list-style: none;
}

.sidebar li {
    margin-bottom: var(--spacing-xs);
}

.sidebar a {
    display: block;
    padding: var(--spacing-xs);
    border-radius: 4px;
    transition: background-color 0.3s ease;
}

.sidebar a:hover {
    background-color: var(--light-color);
    text-decoration: none;
}

/* ==============================
   9. FOOTER
   ============================== */
footer {
    background-color: var(--dark-color);
    color: white;
    text-align: center;
    padding: var(--spacing-lg);
    margin-top: var(--spacing-xl);
}

footer a {
    color: var(--secondary-color);
    margin-left: var(--spacing-md);
}

/* ==============================
   10. RESPONSIVE DESIGN
   ============================== */
@media (max-width: 768px) {
    .container {
        grid-template-columns: 1fr;
    }
    
    nav ul {
        flex-direction: column;
        gap: var(--spacing-sm);
    }
    
    header h1 {
        font-size: 2rem;
    }
}
```

### 💡 Consejos para Completar el Reto
- Empieza con la estructura HTML antes de añadir estilos
- Usa variables CSS para colores y espaciado
- Organiza tu CSS siguiendo la estructura recomendada
- Aplica el reset CSS básico (`* { margin: 0; padding: 0; box-sizing: border-box; }`)
- Usa unidades relativas (rem, em) en lugar de px para mayor flexibilidad
- Experimenta con diferentes combinaciones de colores y tipografías
- Usa Google Fonts para añadir fuentes profesionales a tu blog

### 📅 Entrega
¡Tómate el tiempo que necesites! Cuando termines, comparte tu código en el grupo de WhatsApp y te daré feedback personalizado.

**Bonus**: Si completas este reto, ¡recibirás una guía avanzada de CSS con técnicas que aprenderemos en la próxima clase!

¿Te animas a aceptar el reto? ¡Tu blog personal podría ser el inicio de tu presencia en línea como desarrollador web! 🌐✏️
