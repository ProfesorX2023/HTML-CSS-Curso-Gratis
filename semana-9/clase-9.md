# Clase 9: Flexbox - Diseños Unidimensionales

## 📌 Objetivos de la Clase

- Entender qué es Flexbox y por qué es esencial en el diseño web moderno
- Dominar las propiedades del contenedor Flex (display, flex-direction, justify-content, align-items)
- Aprender a controlar el tamaño y comportamiento de los elementos con flex-grow, flex-shrink y flex-basis
- Crear una galería de imágenes responsiva utilizando Flexbox
- Conocer una guía rápida de Flexbox para consulta futura

## 🧩 Introducción a Flexbox y por qué es esencial

Flexbox (Flexible Box Layout) es un modelo de diseño CSS que permite crear diseños flexibles y responsivos de manera más sencilla y efectiva que los métodos tradicionales (como floats o posicionamiento absoluto).

### ¿Por qué Flexbox es esencial?

- Resuelve problemas comunes de diseño que eran difíciles de implementar con métodos anteriores
- Centrar elementos verticalmente de forma sencilla (un desafío clásico en CSS)
- Distribuir espacio entre elementos de manera flexible
- Crear diseños responsivos sin necesidad de media queries complejas
- Mantiene el flujo normal del documento mientras permite un control preciso del diseño

### Antes y después de Flexbox

**Antes de Flexbox**, para crear diseños flexibles y responsivos, los desarrolladores web tenían que recurrir a técnicas complicadas como:

- Uso excesivo de floats
- Posicionamiento absoluto
- Tablas CSS (¡no recomendado!)
- JavaScript para calcular tamaños

**Con Flexbox**, muchos de estos problemas se resuelven con solo unas pocas líneas de CSS.

### Conceptos clave de Flexbox

- **Contenedor flex**: El elemento padre que contiene a los elementos flexibles
- **Elementos flex**: Los hijos directos del contenedor flex
- **Eje principal**: Dirección en la que se colocan los elementos (definido por flex-direction)
- **Eje transversal**: Perpendicular al eje principal

## 📐 Propiedades del contenedor

### display: flex

Convierte un elemento en un contenedor flex.

```css
.contenedor {
    display: flex;
}
```

**Efecto:**
- Los hijos directos del contenedor se convierten en elementos flex
- El contenedor establece un nuevo contexto de formato flex
- Los elementos se colocan en una fila por defecto

### flex-direction

Define la dirección del eje principal.

```css
.contenedor {
    flex-direction: row;        /* Fila (izquierda a derecha) - valor por defecto */
    flex-direction: row-reverse; /* Fila (derecha a izquierda) */
    flex-direction: column;     /* Columna (arriba a abajo) */
    flex-direction: column-reverse; /* Columna (abajo a arriba) */
}
```

### justify-content

Distribuye los elementos a lo largo del eje principal.

```css
.contenedor {
    justify-content: flex-start;    /* Alinea elementos al inicio del eje principal (por defecto) */
    justify-content: flex-end;      /* Alinea elementos al final del eje principal */
    justify-content: center;        /* Centra los elementos en el eje principal */
    justify-content: space-between; /* Distribuye elementos con espacio entre ellos */
    justify-content: space-around;  /* Distribuye elementos con espacio alrededor */
    justify-content: space-evenly;  /* Distribuye elementos con espacio igualmente */
}
```

### align-items

Distribuye los elementos a lo largo del eje transversal.

```css
.contenedor {
    align-items: stretch;    /* Estira los elementos para llenar el contenedor (por defecto) */
    align-items: flex-start; /* Alinea elementos al inicio del eje transversal */
    align-items: flex-end;   /* Alinea elementos al final del eje transversal */
    align-items: center;     /* Centra los elementos en el eje transversal */
    align-items: baseline;   /* Alinea elementos por sus líneas de base */
}
```

### flex-wrap

Controla si los elementos flex se envuelven en múltiples líneas.

```css
.contenedor {
    flex-wrap: nowrap;  /* No permite envoltura (por defecto) */
    flex-wrap: wrap;    /* Permite envoltura (arriba a abajo) */
    flex-wrap: wrap-reverse; /* Permite envoltura (abajo a arriba) */
}
```

### flex-flow (abreviatura)

Combina flex-direction y flex-wrap.

```css
.contenedor {
    flex-flow: row wrap; /* Dirección fila y envoltura */
    flex-flow: column nowrap; /* Dirección columna sin envoltura */
}
```

### align-content

Distribuye las líneas de flex a lo largo del eje transversal (solo cuando hay múltiples líneas).

```css
.contenedor {
    align-content: stretch;    /* Estira las líneas para llenar el contenedor (por defecto) */
    align-content: flex-start; /* Alinea líneas al inicio del eje transversal */
    align-content: flex-end;   /* Alinea líneas al final del eje transversal */
    align-content: center;     /* Centra las líneas en el eje transversal */
    align-content: space-between; /* Distribuye líneas con espacio entre ellas */
    align-content: space-around;  /* Distribuye líneas con espacio alrededor */
}
```

## 📏 Propiedades de elementos

### order

Controla el orden en que aparecen los elementos dentro del contenedor flex.

```css
.elemento {
    order: 0; /* Valor por defecto */
}

.elemento-1 {
    order: 2; /* Aparecerá después de los elementos con order: 1 */
}

.elemento-2 {
    order: 1; /* Aparecerá antes de los elementos con order: 2 */
}
```

### flex-grow

Define la capacidad de crecimiento de un elemento relativo a los demás elementos.

```css
.elemento {
    flex-grow: 0; /* No crece (por defecto) */
}

.elemento-1 {
    flex-grow: 1; /* Crecerá si hay espacio disponible */
}

.elemento-2 {
    flex-grow: 2; /* Crecerá el doble que elemento-1 si hay espacio disponible */
}
```

### flex-shrink

Define la capacidad de encogimiento de un elemento relativo a los demás elementos.

```css
.elemento {
    flex-shrink: 1; /* Se encogerá si es necesario (por defecto) */
}

.elemento-1 {
    flex-shrink: 0; /* No se encogerá */
}

.elemento-2 {
    flex-shrink: 2; /* Se encogerá el doble que elemento-1 */
}
```

### flex-basis

Define el tamaño base del elemento antes de distribuir el espacio libre.

```css
.elemento {
    flex-basis: auto; /* Tamaño basado en el contenido (por defecto) */
    flex-basis: 200px; /* Tamaño fijo */
    flex-basis: 50%; /* Tamaño relativo al contenedor */
}
```

### flex (abreviatura)

Combina flex-grow, flex-shrink y flex-basis.

```css
.elemento {
    flex: 0 1 auto; /* Valores por defecto */
    flex: 1 1 200px; /* flex-grow: 1, flex-shrink: 1, flex-basis: 200px */
    flex: 2; /* flex-grow: 2, flex-shrink: 1, flex-basis: 0% */
}
```

### align-self

Permite que un elemento individual anule el valor de align-items del contenedor.

```css
.elemento {
    align-self: auto;       /* Valor por defecto (sigue align-items del contenedor) */
    align-self: flex-start; /* Alinea al inicio del eje transversal */
    align-self: flex-end;   /* Alinea al final del eje transversal */
    align-self: center;     /* Centra en el eje transversal */
    align-self: baseline;   /* Alinea por líneas de base */
    align-self: stretch;    /* Estira para llenar el contenedor */
}
```

## 🏆 Ejercicio práctico: Crear una galería de imágenes responsiva

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galería de Imágenes con Flexbox</title>
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
        
        /* Contenedor de la galería */
        .gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 30px;
        }
        
        /* Opciones de vista */
        .view-options {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .view-btn {
            padding: 8px 15px;
            background-color: #ecf0f1;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .view-btn.active, .view-btn:hover {
            background-color: #3498db;
            color: white;
        }
        
        /* Tarjetas de imagen */
        .gallery-item {
            flex: 0 0 calc(33.33% - 10px);
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.08);
            transition: all 0.3s ease;
        }
        
        .gallery-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
        }
        
        .gallery-img {
            width: 100%;
            height: 200px;
            background-color: #e0e0e0;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #7f8c8d;
            font-style: italic;
            overflow: hidden;
        }
        
        .gallery-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .gallery-info {
            padding: 15px;
        }
        
        .gallery-title {
            font-size: 1.2rem;
            margin-bottom: 8px;
            color: #2c3e50;
        }
        
        .gallery-desc {
            color: #7f8c8d;
            font-size: 0.95rem;
            margin-bottom: 10px;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            height: 40px;
        }
        
        .gallery-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
        }
        
        .tag {
            background-color: #eaf2f8;
            color: #2c3e50;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 0.75rem;
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            .gallery-item {
                flex: 0 0 calc(50% - 10px);
            }
        }
        
        @media (max-width: 768px) {
            .gallery-item {
                flex: 0 0 calc(100% - 10px);
            }
        }
        
        /* Vistas alternativas */
        .gallery.compact .gallery-item {
            flex: 0 0 calc(16.66% - 10px);
        }
        
        .gallery.medium .gallery-item {
            flex: 0 0 calc(25% - 10px);
        }
        
        .gallery.large .gallery-item {
            flex: 0 0 calc(50% - 10px);
        }
        
        @media (max-width: 992px) {
            .gallery.compact .gallery-item,
            .gallery.medium .gallery-item {
                flex: 0 0 calc(33.33% - 10px);
            }
            
            .gallery.large .gallery-item {
                flex: 0 0 calc(100% - 10px);
            }
        }
        
        @media (max-width: 768px) {
            .gallery.compact .gallery-item,
            .gallery.medium .gallery-item,
            .gallery.large .gallery-item {
                flex: 0 0 calc(100% - 10px);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Galería de Imágenes con Flexbox</h1>
            <p class="subtitle">Descubre cómo crear una galería de imágenes responsiva utilizando las propiedades de Flexbox</p>
        </header>
        
        <div class="view-options">
            <button class="view-btn active" data-view="default">Por Defecto</button>
            <button class="view-btn" data-view="large">Vista Grande</button>
            <button class="view-btn" data-view="medium">Vista Mediana</button>
            <button class="view-btn" data-view="compact">Vista Compacta</button>
        </div>
        
        <div class="gallery">
            <!-- Imagen 1 -->
            <div class="gallery-item">
                <div class="gallery-img">
                    <span>Imagen 1</span>
                </div>
                <div class="gallery-info">
                    <h2 class="gallery-title">Paisaje Natural</h2>
                    <p class="gallery-desc">Hermoso paisaje con montañas y lagos en tonos naturales y vibrantes.</p>
                    <div class="gallery-tags">
                        <span class="tag">Naturaleza</span>
                        <span class="tag">Paisaje</span>
                    </div>
                </div>
            </div>
            
            <!-- Imagen 2 -->
            <div class="gallery-item">
                <div class="gallery-img">
                    <span>Imagen 2</span>
                </div>
                <div class="gallery-info">
                    <h2 class="gallery-title">Arquitectura Moderna</h2>
                    <p class="gallery-desc">Diseños innovadores de edificios contemporáneos en entornos urbanos.</p>
                    <div class="gallery-tags">
                        <span class="tag">Arquitectura</span>
                        <span class="tag">Ciudad</span>
                    </div>
                </div>
            </div>
            
            <!-- Imagen 3 -->
            <div class="gallery-item">
                <div class="gallery-img">
                    <span>Imagen 3</span>
                </div>
                <div class="gallery-info">
                    <h2 class="gallery-title">Retrato Profesional</h2>
                    <p class="gallery-desc">Fotografía de alta calidad de personas en entornos profesionales.</p>
                    <div class="gallery-tags">
                        <span class="tag">Retrato</span>
                        <span class="tag">Profesional</span>
                    </div>
                </div>
            </div>
            
            <!-- Imagen 4 -->
            <div class="gallery-item">
                <div class="gallery-img">
                    <span>Imagen 4</span>
                </div>
                <div class="gallery-info">
                    <h2 class="gallery-title">Comida Gourmet</h2>
                    <p class="gallery-desc">Platos gourmet con presentación artística y detalles culinarios.</p>
                    <div class="gallery-tags">
                        <span class="tag">Comida</span>
                        <span class="tag">Gourmet</span>
                    </div>
                </div>
            </div>
            
            <!-- Imagen 5 -->
            <div class="gallery-item">
                <div class="gallery-img">
                    <span>Imagen 5</span>
                </div>
                <div class="gallery-info">
                    <h2 class="gallery-title">Aventura Extrema</h2>
                    <p class="gallery-desc">Imágenes emocionantes de deportes extremos en entornos naturales.</p>
                    <div class="gallery-tags">
                        <span class="tag">Aventura</span>
                        <span class="tag">Deportes</span>
                    </div>
                </div>
            </div>
            
            <!-- Imagen 6 -->
            <div class="gallery-item">
                <div class="gallery-img">
                    <span>Imagen 6</span>
                </div>
                <div class="gallery-info">
                    <h2 class="gallery-title">Arte Digital</h2>
                    <p class="gallery-desc">Obras de arte creadas digitalmente con técnicas innovadoras.</p>
                    <div class="gallery-tags">
                        <span class="tag">Arte</span>
                        <span class="tag">Digital</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        // Funcionalidad para cambiar vistas
        const viewButtons = document.querySelectorAll('.view-btn');
        const gallery = document.querySelector('.gallery');
        
        viewButtons.forEach(button => {
            button.addEventListener('click', () => {
                // Remover clase active de todos los botones
                viewButtons.forEach(btn => btn.classList.remove('active'));
                // Añadir clase active al botón clickeado
                button.classList.add('active');
                
                // Remover clases de vista anteriores
                gallery.classList.remove('default', 'large', 'medium', 'compact');
                
                // Añadir nueva clase de vista
                const view = button.getAttribute('data-view');
                if (view !== 'default') {
                    gallery.classList.add(view);
                }
            });
        });
    </script>
</body>
</html>
```

### Pasos para completar el ejercicio:

1. Crea un nuevo archivo en tu editor de código y guárdalo como **galeria-flexbox.html**
2. Copia la estructura básica de HTML
3. Agrega las secciones de estilos en el `<head>`
4. Personaliza los colores, imágenes y contenido según tus preferencias
5. Experimenta con diferentes valores de **flex-direction**, **justify-content** y **align-items**
6. Ajusta los valores de **flex-grow**, **flex-shrink** y **flex-basis** para ver cómo afectan al diseño
7. Agrega el código JavaScript para la funcionalidad de cambio de vistas
8. Prueba el diseño en diferentes tamaños de pantalla
9. Guarda el archivo y ábrelo en tu navegador

## 📎 Recurso adicional: Guía rápida de Flexbox

### Propiedades del contenedor

```css
.contenedor {
    /* Básicas */
    display: flex;          /* Activa Flexbox */
    flex-direction: row;    /* row | row-reverse | column | column-reverse */
    flex-wrap: nowrap;      /* nowrap | wrap | wrap-reverse */
    flex-flow: row nowrap;  /* Abreviatura de flex-direction y flex-wrap */
    
    /* Distribución */
    justify-content: flex-start;  /* flex-start | flex-end | center | space-between | space-around | space-evenly */
    align-items: stretch;         /* stretch | flex-start | flex-end | center | baseline */
    align-content: stretch;       /* stretch | flex-start | flex-end | center | space-between | space-around */
}
```

### Propiedades de los elementos flex

```css
.elemento {
    /* Orden */
    order: 0;                   /* Número entero (por defecto 0) */
    
    /* Tamaño flexible */
    flex-grow: 0;               /* Factor de crecimiento (por defecto 0) */
    flex-shrink: 1;             /* Factor de encogimiento (por defecto 1) */
    flex-basis: auto;           /* Tamaño base (auto | tamaño | %) */
    flex: 0 1 auto;             /* Abreviatura de flex-grow, flex-shrink, flex-basis */
    
    /* Alineación individual */
    align-self: auto;           /* auto | flex-start | flex-end | center | baseline | stretch */
}
```

### Valores comunes para justify-content

| Valor | Descripción |
|-------|-------------|
| `flex-start` | Elementos al inicio del eje principal |
| `flex-end` | Elementos al final del eje principal |
| `center` | Elementos centrados en el eje principal |
| `space-between` | Espacio igual entre elementos, sin espacio al inicio ni al final |
| `space-around` | Espacio igual alrededor de los elementos |
| `space-evenly` | Espacio igual entre elementos e igual al inicio y final |

### Valores comunes para align-items

| Valor | Descripción |
|-------|-------------|
| `stretch` | Estira los elementos para llenar el contenedor (por defecto) |
| `flex-start` | Elementos al inicio del eje transversal |
| `flex-end` | Elementos al final del eje transversal |
| `center` | Elementos centrados en el eje transversal |
| `baseline` | Elementos alineados por sus líneas de base |

### Fórmula para calcular el tamaño final

```
Tamaño final = Tamaño base + (Espacio libre * factor de crecimiento)
```

## Consejos prácticos

- Siempre usa `box-sizing: border-box` para evitar problemas con el cálculo de tamaños

- Para centrar elementos vertical y horizontalmente:
```css
.contenedor {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

- Para crear una barra de navegación con elementos distribuidos:
```css
nav {
    display: flex;
    justify-content: space-between;
}
```

- Para crear una galería responsiva:
```css
.gallery {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
}

.gallery-item {
    flex: 0 0 calc(25% - 15px); /* 4 columnas con espacio entre ellas */
}
```

## 💡 Consejo: Cuándo usar Flexbox vs Grid

### Usa Flexbox cuando:
- Necesitas un diseño **unidimensional** (fila o columna)
- Quieres distribuir espacio entre elementos en una sola dirección
- Necesitas alinear elementos en una única línea
- Quieres que los elementos tengan el mismo tamaño sin importar su contenido
- Estás creando una barra de navegación, galería de imágenes o elementos en fila

### Usa CSS Grid cuando:
- Necesitas un diseño **bidimensional** (filas y columnas)
- Quieres controlar explícitamente la posición de los elementos en filas y columnas
- Estás creando un layout de página completo
- Necesitas superponer elementos en la rejilla
- Quieres crear diseños complejos con áreas definidas

### Regla de oro:
> "Si solo necesitas controlar una dimensión (horizontal o vertical), usa Flexbox. Si necesitas controlar ambas dimensiones (horizontal y vertical), usa CSS Grid."

## 🏆 Reto Adicional: Crear un Dashboard Administrativo con Flexbox

¡Felicidades por completar los ejercicios de Flexbox! Aquí tienes un reto adicional para que practiques aún más:

### 📚 Descripción del Reto

Crea un dashboard administrativo responsivo utilizando Flexbox con las siguientes características:

- Un diseño organizado en secciones con diferentes tamaños y propiedades flex
- Uso de `flex-direction` para cambiar la orientación en diferentes tamaños de pantalla
- Implementación de `justify-content` y `align-items` para una distribución óptima
- Efectos de hover en los elementos del dashboard
- Diseño responsivo que se adapte a móviles, tablets y escritorio
- Uso de `order` para reorganizar elementos en móviles

### 📌 Ejemplo de Cómo Debería Verse

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard Administrativo con Flexbox</title>
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
            background-color: #f5f7fa;
            padding: 20px;
        }
        
        .container {
            max-width: 1400px;
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
            margin: 0 auto 20px;
        }
        
        /* Barra de navegación */
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #2c3e50;
            color: white;
            padding: 15px 20px;
            border-radius: 8px;
            margin-bottom: 25px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        .nav-links {
            display: flex;
            list-style: none;
            gap: 20px;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            transition: all 0.3s;
        }
        
        .nav-links a:hover {
            color: #3498db;
        }
        
        /* Dashboard */
        .dashboard {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }
        
        /* Sidebar */
        .sidebar {
            flex: 0 0 250px;
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .sidebar h2 {
            margin-bottom: 15px;
            color: #2c3e50;
            padding-bottom: 10px;
            border-bottom: 1px solid #ecf0f1;
        }
        
        .sidebar-menu {
            list-style: none;
        }
        
        .sidebar-menu li {
            margin-bottom: 10px;
        }
        
        .sidebar-menu a {
            display: block;
            padding: 10px 15px;
            color: #34495e;
            text-decoration: none;
            border-radius: 4px;
            transition: all 0.3s;
        }
        
        .sidebar-menu a:hover {
            background-color: #ecf0f1;
            color: #2c3e50;
        }
        
        .sidebar-menu a.active {
            background-color: #3498db;
            color: white;
        }
        
        /* Contenido principal */
        .main-content {
            flex: 1 1 calc(100% - 270px);
        }
        
        /* Estadísticas */
        .stats-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 25px;
        }
        
        .stat-card {
            flex: 1 1 calc(25% - 15px);
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        .stat-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
        }
        
        .users-icon {
            background-color: #e1f5fe;
            color: #0288d1;
        }
        
        .revenue-icon {
            background-color: #e8f5e9;
            color: #388e3c;
        }
        
        .orders-icon {
            background-color: #fff8e1;
            color: #f57c00;
        }
        
        .visitors-icon {
            background-color: #f3e5f5;
            color: #7b1fa2;
        }
        
        .stat-title {
            color: #7f8c8d;
            font-size: 0.9rem;
        }
        
        .stat-value {
            font-size: 1.8rem;
            font-weight: bold;
            color: #2c3e50;
        }
        
        /* Contenido de tarjetas */
        .card {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #ecf0f1;
        }
        
        .card-title {
            font-size: 1.2rem;
            color: #2c3e50;
        }
        
        .card-content {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
        }
        
        .chart-placeholder {
            flex: 1 1 calc(66.66% - 10px);
            height: 300px;
            background-color: #ecf0f1;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #7f8c8d;
        }
        
        .chart-sidebar {
            flex: 1 1 calc(33.33% - 10px);
        }
        
        .chart-sidebar-item {
            margin-bottom: 15px;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 6px;
        }
        
        .chart-sidebar-title {
            font-weight: bold;
            margin-bottom: 8px;
            color: #2c3e50;
        }
        
        .chart-sidebar-value {
            font-size: 1.3rem;
            color: #3498db;
        }
        
        /* Tabla de usuarios */
        .users-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .users-table th {
            text-align: left;
            padding: 12px 15px;
            background-color: #f8f9fa;
            color: #2c3e50;
            font-weight: 600;
        }
        
        .users-table td {
            padding: 12px 15px;
            border-bottom: 1px solid #ecf0f1;
        }
        
        .users-table tr:hover {
            background-color: #f8f9fa;
        }
        
        .user-status {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
        }
        
        .status-active {
            background-color: #e8f5e9;
            color: #388e3c;
        }
        
        .status-inactive {
            background-color: #ffebee;
            color: #d32f2f;
        }
        
        /* Responsive */
        @media (max-width: 1200px) {
            .stat-card {
                flex: 1 1 calc(33.33% - 15px);
            }
        }
        
        @media (max-width: 992px) {
            .stat-card {
                flex: 1 1 calc(50% - 15px);
            }
            
            .sidebar {
                flex: 0 0 200px;
            }
            
            .main-content {
                flex: 1 1 calc(100% - 220px);
            }
        }
        
        @media (max-width: 768px) {
            .dashboard {
                flex-direction: column;
            }
            
            .sidebar {
                flex: 0 0 100%;
                margin-bottom: 20px;
            }
            
            .main-content {
                flex: 1 1 100%;
            }
            
            .stat-card {
                flex: 1 1 100%;
            }
            
            .chart-placeholder {
                flex: 1 1 100%;
            }
            
            .chart-sidebar {
                flex: 1 1 100%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Dashboard Administrativo con Flexbox</h1>
            <p class="subtitle">Descubre cómo crear un dashboard responsivo utilizando las propiedades de Flexbox para una distribución óptima</p>
        </header>
        
        <!-- Barra de navegación -->
        <nav class="navbar">
            <div class="logo">Admin Dashboard</div>
            <ul class="nav-links">
                <li><a href="#">Inicio</a></li>
                <li><a href="#">Usuarios</a></li>
                <li><a href="#">Productos</a></li>
                <li><a href="#">Reportes</a></li>
                <li><a href="#">Configuración</a></li>
            </ul>
        </nav>
        
        <div class="dashboard">
            <!-- Sidebar -->
            <aside class="sidebar">
                <h2>Menú</h2>
                <ul class="sidebar-menu">
                    <li><a href="#" class="active">Panel de Control</a></li>
                    <li><a href="#">Usuarios</a></li>
                    <li><a href="#">Productos</a></li>
                    <li><a href="#">Pedidos</a></li>
                    <li><a href="#">Reportes</a></li>
                    <li><a href="#">Configuración</a></li>
                    <li><a href="#">Soporte</a></li>
                </ul>
            </aside>
            
            <!-- Contenido principal -->
            <main class="main-content">
                <!-- Estadísticas -->
                <div class="stats-container">
                    <div class="stat-card">
                        <div class="stat-header">
                            <div>
                                <div class="stat-title">Usuarios</div>
                                <div class="stat-value">2,450</div>
                            </div>
                            <div class="stat-icon users-icon">👥</div>
                        </div>
                        <div>+12% desde el mes pasado</div>
                    </div>
                    
                    <div class="stat-card">
                        <div class="stat-header">
                            <div>
                                <div class="stat-title">Ingresos</div>
                                <div class="stat-value">Q 45,200</div>
                            </div>
                            <div class="stat-icon revenue-icon">💰</div>
                        </div>
                        <div>+8% desde el mes pasado</div>
                    </div>
                    
                    <div class="stat-card">
                        <div class="stat-header">
                            <div>
                                <div class="stat-title">Pedidos</div>
                                <div class="stat-value">1,280</div>
                            </div>
                            <div class="stat-icon orders-icon">📦</div>
                        </div>
                        <div>+5% desde el mes pasado</div>
                    </div>
                    
                    <div class="stat-card">
                        <div class="stat-header">
                            <div>
                                <div class="stat-title">Visitantes</div>
                                <div class="stat-value">8,750</div>
                            </div>
                            <div class="stat-icon visitors-icon">👀</div>
                        </div>
                        <div>+15% desde el mes pasado</div>
                    </div>
                </div>
                
                <!-- Gráficos -->
                <div class="card">
                    <div class="card-header">
                        <h2 class="card-title">Análisis de Ventas</h2>
                        <div>
                            <select>
                                <option>Últimos 7 días</option>
                                <option>Últimos 30 días</option>
                                <option>Este mes</option>
                                <option>Este año</option>
                            </select>
                        </div>
                    </div>
                    <div class="card-content">
                        <div class="chart-placeholder">
                            Gráfico de análisis de ventas (simulación)
                        </div>
                        <div class="chart-sidebar">
                            <div class="chart-sidebar-item">
                                <div class="chart-sidebar-title">Ventas Totales</div>
                                <div class="chart-sidebar-value">Q 45,200</div>
                            </div>
                            <div class="chart-sidebar-item">
                                <div class="chart-sidebar-title">Productos Vendidos</div>
                                <div class="chart-sidebar-value">1,280</div>
                            </div>
                            <div class="chart-sidebar-item">
                                <div class="chart-sidebar-title">Clientes Nuevos</div>
                                <div class="chart-sidebar-value">245</div>
                            </div>
                            <div class="chart-sidebar-item">
                                <div class="chart-sidebar-title">Tasa de Conversión</div>
                                <div class="chart-sidebar-value">3.8%</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Tabla de usuarios -->
                <div class="card">
                    <div class="card-header">
                        <h2 class="card-title">Usuarios Recientes</h2>
                        <div>
                            <button>Ver Todos</button>
                        </div>
                    </div>
                    <table class="users-table">
                        <thead>
                            <tr>
                                <th>Nombre</th>
                                <th>Email</th>
                                <th>Fecha de Registro</th>
                                <th>Estado</th>
                                <th>Acciones</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>María González</td>
                                <td>maria@example.com</td>
                                <td>15/05/2024</td>
                                <td><span class="user-status status-active">Activo</span></td>
                                <td>
                                    <button>Editar</button>
                                </td>
                            </tr>
                            <tr>
                                <td>Carlos Ramírez</td>
                                <td>carlos@example.com</td>
                                <td>14/05/2024</td>
                                <td><span class="user-status status-active">Activo</span></td>
                                <td>
                                    <button>Editar</button>
                                </td>
                            </tr>
                            <tr>
                                <td>Ana López</td>
                                <td>ana@example.com</td>
                                <td>12/05/2024</td>
                                <td><span class="user-status status-inactive">Inactivo</span></td>
                                <td>
                                    <button>Editar</button>
                                </td>
                            </tr>
                            <tr>
                                <td>Juan Pérez</td>
                                <td>juan@example.com</td>
                                <td>10/05/2024</td>
                                <td><span class="user-status status-active">Activo</span></td>
                                <td>
                                    <button>Editar</button>
                                </td>
                            </tr>
                            <tr>
                                <td>Laura Martínez</td>
                                <td>laura@example.com</td>
                                <td>08/05/2024</td>
                                <td><span class="user-status status-active">Activo</span></td>
                                <td>
                                    <button>Editar</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </main>
        </div>
    </div>
</body>
</html>
```

### 💡 Consejos para Completar el Reto

1. Empieza con la estructura básica del dashboard antes de añadir estilos
2. Usa `display: flex` en los contenedores principales para organizar el layout
3. Experimenta con diferentes valores de `flex-direction` para ver cómo afectan al diseño
4. Ajusta los valores de `flex-grow`, `flex-shrink` y `flex-basis` para controlar el tamaño de los elementos
5. Usa `order` para cambiar el orden de los elementos en vistas móviles
6. Implementa media queries para hacer el diseño responsivo
7. Prueba tu dashboard en diferentes tamaños de pantalla
8. Si te sientes cómodo, añade animaciones sutiles con `:hover`

### 📅 Entrega

¡Tómate el tiempo que necesites! Cuando termines, comparte tu código en el grupo de WhatsApp y te daré feedback personalizado.

**Bonus**: Si completas este reto, ¡recibirás una colección de diseños profesionales de dashboard que utilizan Flexbox y CSS Grid juntos!

¿Te animas a aceptar el reto? ¡Tu dashboard administrativo podría ser el inicio de tu carrera como diseñador UI/UX! 🖥️✨
