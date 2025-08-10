# Clase 10: CSS Grid - Diseños Bidimensionales

## 📌 Objetivos de la Clase

- Entender qué es CSS Grid y cómo se diferencia de Flexbox
- Dominar las propiedades del contenedor Grid (grid-template-columns, grid-template-rows, grid-gap)
- Aprender a posicionar elementos con grid-column y grid-row
- Crear diseños complejos con áreas definidas (grid-template-areas)
- Implementar un layout de blog completo utilizando CSS Grid
- Conocer cuándo usar Grid vs Flexbox en proyectos reales

## 🧩 Introducción a CSS Grid y diferencias con Flexbox

CSS Grid Layout es un módulo de diseño en CSS que permite crear layouts basados en rejillas bidimensionales. Es ideal para dividir la página en regiones y definir la relación en términos de tamaño, posición y capa entre las partes de un control HTML.

### Características principales de CSS Grid:

- **Es bidimensional**: Permite el control tanto de filas como de columnas simultáneamente
- **Flexibilidad en la distribución**: Control preciso sobre la posición de cada elemento
- **Fácil de adaptar a diseños responsivos**: Con media queries y funciones como auto-fit y auto-fill
- **Definición de áreas**: Permite crear diseños complejos con nombres descriptivos

### Diferencias clave entre Flexbox y Grid:

| Aspecto | Flexbox | CSS Grid |
|---------|---------|----------|
| **Dimensionalidad** | Unidimensional (fila o columna) | Bidimensional (filas y columnas) |
| **Propósito** | Distribuir espacio en una sola dimensión | Crear diseños de página completos |
| **Control** | Control sobre el eje principal | Control sobre filas y columnas simultáneamente |
| **Posicionamiento** | Los elementos se colocan secuencialmente | Los elementos pueden posicionarse en cualquier lugar de la rejilla |
| **Mejor para** | Componentes pequeños, barras de navegación | Layouts de página completos, diseños complejos |

### Cuándo usar cada uno:

**Usa Flexbox cuando:**
- Necesitas un diseño unidimensional (solo filas o solo columnas)
- Quieres distribuir espacio entre elementos en una sola dirección
- Estás creando una barra de navegación o galería de elementos en fila

**Usa CSS Grid cuando:**
- Necesitas un diseño bidimensional (filas y columnas)
- Quieres controlar explícitamente la posición de los elementos en filas y columnas
- Estás creando un layout de página completo
- Necesitas superponer elementos en la rejilla
- Quieres crear diseños complejos con áreas definidas

## 📐 Propiedades del contenedor Grid

### display: grid

Convierte un elemento en un contenedor Grid.

```css
.contenedor {
    display: grid;
}
```

**Efecto:**
- Los hijos directos del contenedor se convierten en elementos Grid
- El contenedor establece un nuevo contexto de formato Grid

### grid-template-columns

Define el número y tamaño de las columnas.

```css
.contenedor {
    /* Valores fijos */
    grid-template-columns: 100px 200px 100px;
    
    /* Valores fr (fracciones) */
    grid-template-columns: 1fr 2fr 1fr;
    
    /* Función repeat() */
    grid-template-columns: repeat(3, 1fr);
    
    /* Unidades mixtas */
    grid-template-columns: 100px 1fr 200px;
    
    /* Unidades auto-fit y auto-fill */
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}
```

### grid-template-rows

Define el número y tamaño de las filas.

```css
.contenedor {
    /* Valores fijos */
    grid-template-rows: 100px 200px 100px;
    
    /* Valores fr (fracciones) */
    grid-template-rows: 100px 1fr 100px;
}
```

### grid-gap (o gap)

Define el espacio entre filas y columnas (ahora reemplazado por gap, pero grid-gap sigue siendo ampliamente compatible).

```css
.contenedor {
    /* Un valor: aplica a filas y columnas */
    grid-gap: 10px;
    
    /* Dos valores: filas columnas */
    grid-gap: 15px 10px;
}
```

### grid-template-areas

Define áreas nombradas en el grid para crear diseños complejos.

```css
.contenedor {
    grid-template-areas: 
        "header header header"
        "nav main sidebar"
        "footer footer footer";
}
```

### grid-auto-rows y grid-auto-columns

Define el tamaño de las filas y columnas creadas implícitamente.

```css
.contenedor {
    grid-auto-rows: 100px;
    grid-auto-columns: 1fr;
}
```

### grid-auto-flow

Controla cómo se colocan los elementos en las celdas no definidas explícitamente.

```css
.contenedor {
    /* row (por defecto), column, row dense, column dense */
    grid-auto-flow: row;
}
```

## 📏 Posicionamiento con grid-column y grid-row

### grid-column

Controla la ubicación del elemento en las columnas.

```css
.elemento {
    /* Inicio / fin */
    grid-column: 1 / 3;
    
    /* Span (cuántas columnas ocupa) */
    grid-column: 2 / span 2;
    
    /* Nombre de área */
    grid-column: sidebar-start / sidebar-end;
}
```

### grid-row

Controla la ubicación del elemento en las filas.

```css
.elemento {
    /* Inicio / fin */
    grid-row: 2 / 4;
    
    /* Span (cuántas filas ocupa) */
    grid-row: 1 / span 3;
}
```

### grid-area

Propiedad abreviada que combina grid-row-start, grid-column-start, grid-row-end y grid-column-end.

```css
.elemento {
    /* fila-inicio / columna-inicio / fila-fin / columna-fin */
    grid-area: 1 / 2 / 3 / 4;
    
    /* Nombre de área */
    grid-area: header;
}
```

## 🌐 Grid Areas para diseños complejos

Las áreas nombradas permiten crear diseños complejos de manera visualmente intuitiva.

```css
.contenedor {
    display: grid;
    grid-template-columns: 1fr 3fr 1fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas: 
        "header header header"
        "nav main sidebar"
        "footer footer footer";
    gap: 10px;
}

.header { grid-area: header; }
.nav { grid-area: nav; }
.main { grid-area: main; }
.sidebar { grid-area: sidebar; }
.footer { grid-area: footer; }
```

### Ventajas de usar Grid Areas:

- **Legibilidad**: El diseño se entiende visualmente al ver la plantilla
- **Mantenibilidad**: Cambiar la posición de un elemento es tan simple como mover su nombre en la plantilla
- **Flexibilidad**: Permite crear diseños complejos con superposición de elementos

## 📱 Diseño responsivo con CSS Grid

CSS Grid se integra perfectamente con media queries para crear diseños responsivos.

### Técnicas responsivas con Grid:

#### 1. Cambiar el número de columnas con media queries

```css
.contenedor {
    display: grid;
    grid-template-columns: 1fr;
    gap: 15px;
}

@media (min-width: 768px) {
    .contenedor {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (min-width: 1024px) {
    .contenedor {
        grid-template-columns: repeat(3, 1fr);
    }
}
```

#### 2. Usar auto-fill y minmax para columnas fluidas

```css
.contenedor {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 15px;
}
```

#### 3. Reordenar áreas en diferentes tamaños de pantalla

```css
.contenedor {
    display: grid;
    grid-template-areas: 
        "header"
        "main"
        "sidebar"
        "footer";
}

@media (min-width: 768px) {
    .contenedor {
        grid-template-areas: 
            "header header"
            "sidebar main"
            "footer footer";
    }
}
```

## 🏆 Ejercicio práctico: Crear un layout de blog completo

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Layout de Blog con CSS Grid</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f8f9fa;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        h1 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #7f8c8d;
            max-width: 600px;
            margin: 0 auto;
        }
        
        /* Layout del blog con CSS Grid */
        .blog-layout {
            display: grid;
            grid-template-columns: 1fr 3fr;
            grid-template-rows: auto 1fr auto;
            grid-template-areas: 
                "header header"
                "sidebar main"
                "footer footer";
            gap: 20px;
            min-height: 100vh;
        }
        
        /* Estilos para cada área */
        .header {
            grid-area: header;
            /* Continúa con los estilos específicos... */
        }
    </style>
</head>
<body>
    <!-- Estructura HTML del blog -->
</body>
</html>
```

### Pasos para completar el ejercicio:

1. Crea un nuevo archivo en tu editor de código y guárdalo como **blog-grid.html**
2. Copia la estructura básica de HTML
3. Agrega las secciones de estilos en el `<head>`
4. Personaliza los colores, imágenes y contenido según tus preferencias
5. Experimenta con diferentes valores de `grid-template-columns` y `grid-template-areas`
6. Ajusta los valores de `gap` para ver cómo afecta al espaciado
7. Modifica los valores de `grid-column` y `grid-row` para reorganizar elementos
8. Prueba el diseño en diferentes tamaños de pantalla
9. Guarda el archivo y ábrelo en tu navegador

## 📎 Recurso adicional: Cheat Sheet de CSS Grid

### Propiedades del contenedor

```css
.contenedor {
    /* Básicas */
    display: grid;          /* Activa CSS Grid */
    grid-template-columns: 1fr 1fr 1fr; /* Define columnas */
    grid-template-rows: auto 100px;     /* Define filas */
    grid-template-areas: 
        "header header"
        "sidebar content"; /* Define áreas nombradas */
    
    /* Espaciado */
    gap: 10px;             /* Espacio entre filas y columnas (reemplaza grid-gap) */
    row-gap: 15px;         /* Espacio entre filas */
    column-gap: 10px;      /* Espacio entre columnas */
    
    /* Flujo automático */
    grid-auto-columns: 1fr; /* Tamaño para columnas implícitas */
    grid-auto-rows: 100px;  /* Tamaño para filas implícitas */
    grid-auto-flow: row;    /* row | column | row dense | column dense */
}
```

### Propiedades de los elementos Grid

```css
.elemento {
    /* Posicionamiento */
    grid-column: 1 / 3;    /* Inicio / fin (columnas) */
    grid-row: 2 / 4;       /* Inicio / fin (filas) */
    
    /* Span (cuántas filas/columnas ocupa) */
    grid-column: 2 / span 2;
    grid-row: 1 / span 3;
    
    /* Propiedad abreviada */
    grid-area: 1 / 2 / 3 / 4; /* fila-inicio / columna-inicio / fila-fin / columna-fin */
    grid-area: header;     /* Nombre de área definido en grid-template-areas */
}
```

### Funciones útiles

```css
/* repeat() - Repite un patrón de tamaño */
grid-template-columns: repeat(3, 1fr);

/* minmax() - Define un rango de tamaño */
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));

/* fit-content() - Tamaño basado en contenido */
grid-template-columns: fit-content(200px) 1fr;
```

### Valores comunes para grid-template-columns

| Valor | Descripción |
|-------|-------------|
| `1fr` | Una fracción del espacio disponible |
| `minmax(200px, 1fr)` | Mínimo 200px, máximo 1fr |
| `repeat(3, 1fr)` | Tres columnas de igual tamaño |
| `repeat(auto-fill, minmax(200px, 1fr))` | Columnas responsivas con ancho mínimo |
| `100px 1fr 200px` | Columnas con tamaños fijos y flexibles |

### Ejemplo de layout con áreas

```css
.container {
    display: grid;
    grid-template-columns: 200px 1fr 300px;
    grid-template-rows: auto 1fr auto;
    grid-template-areas: 
        "header header header"
        "nav main sidebar"
        "footer footer footer";
    gap: 15px;
}

.header { grid-area: header; }
.nav { grid-area: nav; }
.main { grid-area: main; }
.sidebar { grid-area: sidebar; }
.footer { grid-area: footer; }
```

## Consejos prácticos

- Usa el modo de inspección de Grid en Chrome DevTools para visualizar las líneas de la rejilla

- Para centrar elementos en Grid:
```css
.container {
    display: grid;
    place-items: center; /* Centra vertical y horizontalmente */
}
```

- Para crear una galería de imágenes responsiva:
```css
.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 15px;
}
```

- Para diseños con superposición:
```css
.container {
    display: grid;
}

.elemento {
    grid-column: 1 / -1; /* Ocupa todas las columnas */
    z-index: 1;
}
```

## 💡 Consejo: Cuándo usar Grid vs Flexbox en proyectos reales

### Casos de uso para CSS Grid:

#### Layouts de página completos
- Cuando necesitas controlar tanto filas como columnas
- **Ejemplo**: Diseños con header, sidebar, contenido principal y footer

#### Galerías de imágenes responsivas
- Cuando necesitas una cuadrícula de elementos que se ajuste al tamaño de la pantalla
- **Ejemplo**: `grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));`

#### Diseños con superposición
- Cuando necesitas posicionar elementos en lugares específicos
- **Ejemplo**: Elementos que se superponen en esquinas o centros

#### Interfaces de usuario complejas
- Cuando necesitas un control preciso sobre la posición de cada elemento
- **Ejemplo**: Paneles de administración con múltiples secciones

### Casos de uso para Flexbox:

#### Barras de navegación
- Cuando necesitas distribuir elementos en una sola dirección
- **Ejemplo**: `display: flex; justify-content: space-between;`

#### Centrar elementos verticalmente
- Cuando necesitas centrar un elemento en el centro de su contenedor
- **Ejemplo**: `display: flex; align-items: center; justify-content: center;`

#### Elementos en fila con tamaño flexible
- Cuando necesitas que los elementos se ajusten al espacio disponible
- **Ejemplo**: Tarjetas de producto que crecen para llenar el espacio

#### Reordenamiento en móviles
- Cuando necesitas cambiar el orden de los elementos en diferentes tamaños de pantalla
- **Ejemplo**: `order: 2;` en un elemento para cambiar su posición

### Reglas prácticas:

> **"Grid para la estructura, Flexbox para los componentes"**

- Usa **Grid** para el layout general de la página
- Usa **Flexbox** dentro de los componentes individuales

#### Si solo necesitas controlar una dimensión, usa Flexbox
- Si solo te importa cómo se distribuyen los elementos en fila o en columna

#### Si necesitas controlar ambas dimensiones, usa Grid
- Si necesitas controlar cómo se distribuyen los elementos en fila y en columna

#### Puedes combinar ambos en el mismo proyecto
- Un contenedor Grid puede contener elementos con `display: flex`
- Un contenedor Flex puede contener elementos con `display: grid`

### Ejemplo de combinación Grid + Flexbox:

```css
/* Layout principal con Grid */
.page {
    display: grid;
    grid-template-columns: 250px 1fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas: 
        "header header"
        "nav main"
        "footer footer";
    gap: 15px;
}

/* Componentes internos con Flexbox */
.header {
    grid-area: header;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.nav-links {
    display: flex;
    gap: 25px;
}
```

## 🏆 Reto Adicional: Crear un Portafolio Profesional con CSS Grid

¡Felicidades por completar los ejercicios de CSS Grid! Aquí tienes un reto adicional para que practiques aún más:

### 📚 Descripción del Reto

Crea un portafolio profesional responsivo utilizando CSS Grid con las siguientes características:

- Un diseño organizado en áreas definidas usando `grid-template-areas`
- Uso de `grid-column` y `grid-row` para posicionar elementos específicos
- Implementación de un diseño responsivo con `auto-fill` y `minmax`
- Efectos de hover en los proyectos del portafolio
- Diseño responsivo que se adapte a móviles, tablets y escritorio
- Uso de `grid-gap` para un espaciado consistente

### 📌 Ejemplo de Cómo Debería Verse

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portafolio Profesional con CSS Grid</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f8f9fa;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            margin-bottom: 40px;
        }
        
        h1 {
            color: #2c3e50;
            margin-bottom: 10px;
        }
        
        .subtitle {
            color: #7f8c8d;
            max-width: 600px;
            margin: 0 auto;
        }
        
        /* Barra de navegación */
        .navbar {
            display: flex;
            justify-content: center;
            background-color: #2c3e50;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 30px;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
            gap: 20px;
        }
        
        /* Continúa el CSS... */
    </style>
</head>
<body>
    <!-- Estructura HTML del portafolio -->
</body>
</html>
```

### 💡 Consejos para Completar el Reto

1. Empieza con la estructura básica del portafolio antes de añadir estilos
2. Usa `display: grid` en los contenedores principales para organizar el layout
3. Experimenta con diferentes valores de `grid-template-columns` y `grid-template-areas`
4. Ajusta los valores de `gap` para controlar el espaciado entre elementos
5. Usa `repeat(auto-fill, minmax())` para crear una galería de proyectos responsiva
6. Implementa media queries para hacer el diseño responsivo
7. Prueba tu portafolio en diferentes tamaños de pantalla
8. Si te sientes cómodo, añade animaciones sutiles con `:hover`

### 📅 Entrega

¡Tómate el tiempo que necesites! Cuando termines, comparte tu código en el grupo de WhatsApp y te daré feedback personalizado.

**Bonus**: Si completas este reto, ¡recibirás una plantilla profesional de portafolio que puedes personalizar y subir a GitHub Pages en minutos!

¿Te animas a aceptar el reto? ¡Tu portafolio profesional con CSS Grid podría ser la llave para conseguir tu próximo trabajo! 🌐✨
