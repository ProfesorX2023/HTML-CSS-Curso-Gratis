# Clase 5: Propiedades Avanzadas de Texto y Color

## 📌 Objetivos de la Clase

- Aprender propiedades avanzadas para el manejo de texto en CSS
- Entender los diferentes modelos de color y cuándo usar cada uno
- Aprender a trabajar con diferentes fuentes tipográficas
- Dominar el uso de sombras de texto para efectos visuales
- Crear un banner atractivo aplicando todos los conocimientos

## 🖌️ Propiedades avanzadas de texto

### font-size

Controla el tamaño de la fuente. Puede usarse con diferentes unidades:

- **px (píxeles)**: Tamaño fijo
- **em**: Relativo al tamaño de fuente del elemento padre
- **rem**: Relativo al tamaño de fuente del elemento raíz
- **%**: Porcentaje del tamaño de fuente del elemento padre
- **vw/vh**: Relativo al ancho/alto de la ventana

```css
.titulo {
    font-size: 24px; /* Tamaño fijo en píxeles */
}

.subtitulo {
    font-size: 1.5em; /* Relativo al tamaño del elemento padre */
}

.parrafo {
    font-size: 1rem; /* Relativo al tamaño del elemento raíz */
}
```

### font-weight

Controla el grosor de la fuente:

- **Valores numéricos**: 100, 200, 300, 400 (normal), 500, 600, 700 (negrita), 800, 900
- **Palabras clave**: normal, bold, bolder, lighter

```css
.texto-normal {
    font-weight: 400; /* Normal */
}

.texto-negrita {
    font-weight: 700; /* Negrita */
}

.texto-extra-negrita {
    font-weight: 900; /* Extra negrita */
}
```

### text-align

Controla la alineación del texto:

- **left**: Izquierda
- **right**: Derecha
- **center**: Centro
- **justify**: Justificado

```css
.texto-izquierda {
    text-align: left;
}

.texto-derecha {
    text-align: right;
}

.texto-centrado {
    text-align: center;
}

.texto-justificado {
    text-align: justify;
}
```

## 🎨 Modelos de color

### Colores por nombre

CSS tiene 140 colores con nombre predefinidos:

```css
.color-rojo {
    color: red;
}

.color-azul {
    color: blue;
}

.color-verde-claro {
    color: lightgreen;
}
```

### Colores hexadecimales

Formato: `#RRGGBB` (donde RR, GG, BB son valores hexadecimales de 00-FF)

```css
.color-rojo-hex {
    color: #FF0000;
}

.color-azul-hex {
    color: #0000FF;
}

.color-verde-hex {
    color: #00FF00;
}

/* Formato abreviado (3 dígitos) */
.color-rojo-abrev {
    color: #F00; /* Equivalente a #FF0000 */
}
```

### Colores RGB

Formato: `rgb(R, G, B)` donde R, G, B son valores de 0-255

```css
.color-rojo-rgb {
    color: rgb(255, 0, 0);
}

.color-azul-rgb {
    color: rgb(0, 0, 255);
}

.color-verde-rgb {
    color: rgb(0, 255, 0);
}
```

### Colores RGBA (con transparencia)

Formato: `rgba(R, G, B, A)` donde A es el valor alfa (transparencia) de 0-1

```css
.color-rojo-transparente {
    color: rgba(255, 0, 0, 0.5);
}

.color-azul-transparente {
    color: rgba(0, 0, 255, 0.8);
}
```

## ✍️ Trabajar con fuentes

### font-family

Especifica la familia de fuentes de un texto:

```css
.parrafo {
    font-family: "Arial", sans-serif;
}

.titulo {
    font-family: "Georgia", serif;
}

.cita {
    font-family: "Courier New", monospace;
}
```

### @font-face

Permite usar fuentes personalizadas que no están instaladas en el sistema del usuario:

```css
@font-face {
    font-family: 'MiFuentePersonalizada';
    src: url('mifuente.woff2') format('woff2'),
         url('mifuente.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

.titulo-especial {
    font-family: 'MiFuentePersonalizada', sans-serif;
}
```

### Usando Google Fonts

1. Ve a https://fonts.google.com
2. Selecciona las fuentes que deseas usar
3. Incluye el enlace en tu HTML
4. Usa la fuente en tu CSS

```html
<!-- En el <head> de tu HTML -->
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
```

```css
/* En tu CSS */
body {
    font-family: 'Roboto', sans-serif;
}
```

## 🌥️ Sombra de texto (text-shadow)

Formato: `text-shadow: h-shadow v-shadow blur-radius color;`

```css
.sombra-simple {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
}

.sombra-doble {
    text-shadow: 1px 1px 0 #fff, 
                 2px 2px 0 #333;
}

.sombra-neon {
    text-shadow: 0 0 5px #fff, 
                 0 0 10px #fff, 
                 0 0 20px #00f, 
                 0 0 40px #00f;
}
```

## 🏆 Ejercicio práctico: Banner tipográfico básico

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Banner Tipográfico</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@700&family=Open+Sans:wght@400;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Open Sans', sans-serif;
            background-color: #f5f5f5;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        
        .banner {
            width: 100%;
            max-width: 800px;
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
            border-radius: 15px;
            padding: 60px 40px;
            text-align: center;
            color: white;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        .banner-title {
            font-family: 'Montserrat', sans-serif;
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .banner-subtitle {
            font-size: 1.3rem;
            margin-bottom: 30px;
            opacity: 0.9;
            line-height: 1.6;
        }
        
        .banner-button {
            display: inline-block;
            background-color: #fff;
            color: #6a11cb;
            padding: 15px 30px;
            border-radius: 25px;
            text-decoration: none;
            font-weight: 600;
            transition: transform 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .banner-button:hover {
            transform: translateY(-2px);
        }
    </style>
</head>
<body>
    <div class="banner">
        <h1 class="banner-title">Diseño Creativo</h1>
        <p class="banner-subtitle">Transforma tus ideas en realidad con tipografía moderna y colores vibrantes</p>
        <a href="#" class="banner-button">Comenzar Ahora</a>
    </div>
</body>
</html>
```

## 📎 Paletas de colores recomendadas

### 1. Paleta Minimalista
- **Primario**: #3498db (Azul brillante)
- **Secundario**: #2c3e50 (Azul oscuro)
- **Acento**: #e74c3c (Rojo)
- **Fondo**: #ecf0f1 (Gris claro)
- **Texto**: #2c3e50 (Azul oscuro)

### 2. Paleta Profesional
- **Primario**: #2980b9 (Azul)
- **Secundario**: #1abc9c (Turquesa)
- **Acento**: #f39c12 (Naranja)
- **Fondo**: #ffffff (Blanco)
- **Texto**: #34495e (Gris azulado)

### 3. Paleta Energética
- **Primario**: #9b59b6 (Morado)
- **Secundario**: #3498db (Azul)
- **Acento**: #2ecc71 (Verde)
- **Fondo**: #f8f9fa (Gris muy claro)
- **Texto**: #212529 (Negro suave)

## 🛠️ Herramientas para crear paletas de colores

- **Adobe Color**: https://color.adobe.com/es/create/color-wheel
- **Coolors**: https://coolors.co
- **Paletton**: https://paletton.com
- **Material Design Colors**: https://material.io/resources/color

## 💡 Consejos para elegir paletas

- Limita tu paleta a 3-5 colores principales
- Usa un color dominante (60%), un secundario (30%) y un acento (10%)
- Considera el contraste para accesibilidad
- Prueba cómo se ven los colores en diferentes dispositivos
- Usa herramientas de simulación de daltonismo para verificar accesibilidad

## 🏆 Reto Adicional: Banner de Bienvenida Avanzado

Crea un banner de bienvenida para un sitio web específico con:

- Diseño responsivo
- Al menos dos fuentes diferentes
- Paleta de colores coherente
- Efectos de sombra de texto
- Llamado a la acción destacado
- Animaciones sutiles (opcional)

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Banner de Bienvenida - Blog Personal</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Raleway:wght@400;600&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Raleway', sans-serif;
            background-color: #f8f9fa;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        
        .welcome-banner {
            width: 100%;
            max-width: 1000px;
            background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)), 
                        url('https://images.unsplash.com/photo-1522202176988-66273c2fd55f?ixlib=rb-4.0.3&auto=format&fit=crop&w=1000&q=80') 
                        no-repeat center center/cover;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.25);
            color: white;
        }
        
        .banner-content {
            padding: 60px 50px;
            text-align: center;
        }
        
        .banner-title {
            font-family: 'Playfair Display', serif;
            font-size: 3.2rem;
            font-weight: 700;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
            letter-spacing: -0.5px;
        }
        
        .banner-subtitle {
            font-size: 1.6rem;
            font-weight: 300;
            margin-bottom: 35px;
            line-height: 1.7;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
            opacity: 0.95;
        }
        
        .banner-highlight {
            color: #f1c40f;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
            font-weight: 600;
        }
        
        .banner-cta {
            display: inline-block;
            background-color: #f1c40f;
            color: #2c3e50;
            padding: 18px 35px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            box-shadow: 0 8px 20px rgba(241, 196, 15, 0.3);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .banner-cta:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 25px rgba(241, 196, 15, 0.4);
            background-color: #f39c12;
        }
        
        .banner-stats {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin-top: 40px;
        }
        
        .stat-item {
            text-align: center;
        }
        
        .stat-number {
            font-size: 2rem;
            font-weight: 700;
            color: #f1c40f;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
        }
        
        .stat-label {
            font-size: 0.9rem;
            opacity: 0.8;
            margin-top: 5px;
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .banner-content {
                padding: 40px 30px;
            }
            
            .banner-title {
                font-size: 2.5rem;
            }
            
            .banner-subtitle {
                font-size: 1.3rem;
            }
            
            .banner-stats {
                flex-direction: column;
                gap: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="welcome-banner">
        <div class="banner-content">
            <h1 class="banner-title">Bienvenido a mi <span class="banner-highlight">Blog</span></h1>
            <p class="banner-subtitle">
                Descubre historias inspiradoras, consejos útiles y contenido de calidad 
                que transformará tu perspectiva del mundo digital
            </p>
            <a href="#" class="banner-cta">Explorar Contenido</a>
            
            <div class="banner-stats">
                <div class="stat-item">
                    <div class="stat-number">150+</div>
                    <div class="stat-label">Artículos</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">5K+</div>
                    <div class="stat-label">Lectores</div>
                </div>
                <div class="stat-item">
                    <div class="stat-number">25+</div>
                    <div class="stat-label">Categorías</div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

## 📚 Pasos para completar el ejercicio

1. Crea un nuevo archivo en tu editor de código y guárdalo como `banner-tipografico.html`
2. Copia la estructura básica de HTML
3. Agrega la sección de estilos en el `<head>`
4. Personaliza los colores, tipografía y contenido según tus preferencias
5. Experimenta con diferentes sombras de texto
6. Ajusta el diseño para que sea responsivo
7. Guarda el archivo y ábrelo en tu navegador

¡Experimenta con diferentes combinaciones y crea tu propio estilo único!
