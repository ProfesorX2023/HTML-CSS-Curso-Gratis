# Clase 8: Efectos Avanzados y Transiciones

## 📌 Objetivos de la Clase

- Aprender a aplicar sombras de caja (box-shadow) para dar profundidad a los elementos
- Dominar el uso de opacidad (opacity) y colores RGBA para efectos de transparencia
- Entender las transformaciones básicas (rotate, scale, translate) para animar elementos
- Implementar transiciones suaves (transition) para mejorar la experiencia de usuario
- Crear botones interactivos con efectos hover atractivos
- Conocer técnicas para usar efectos sin afectar el rendimiento del sitio

## 🌥️ Sombra de caja (box-shadow)

La propiedad `box-shadow` en CSS permite añadir sombras a los elementos, creando efectos de profundidad y dimensiones.

### Sintaxis básica

```css
.elemento {
    box-shadow: offset-x offset-y blur-radius spread-radius color;
}
```

### Parámetros

- **offset-x**: Desplazamiento horizontal de la sombra (positivo = derecha, negativo = izquierda)
- **offset-y**: Desplazamiento vertical de la sombra (positivo = abajo, negativo = arriba)
- **blur-radius**: Difuminado de la sombra (mayor valor = más difuminado)
- **spread-radius**: Tamaño de expansión de la sombra (positivo = más grande, negativo = más pequeño)
- **color**: Color de la sombra

### Ejemplos prácticos

```css
/* Sombra simple */
.sombra-simple {
    box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
}

/* Sombra elevada (efecto de elevación) */
.sombra-elevada {
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

/* Sombra interna */
.sombra-interna {
    box-shadow: inset 2px 2px 5px rgba(0, 0, 0, 0.2);
}

/* Múltiples sombras */
.sombras-multiples {
    box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3),
                -5px -5px 10px rgba(255, 255, 255, 0.5);
}
```

### Consejos para sombras efectivas

- Usa valores `rgba()` para controlar la opacidad de la sombra
- Para efectos de elevación realistas, aumenta el `blur-radius` y reduce la opacidad
- Las sombras internas (`inset`) son excelentes para crear efectos de hundimiento
- Combina múltiples sombras para efectos complejos y realistas

## 🌫️ Opacidad (opacity) y rgba

### Propiedad opacity

Controla la transparencia de un elemento y todos sus hijos.

```css
.elemento {
    opacity: 0.7; /* 0 = totalmente transparente, 1 = totalmente opaco */
}
```

### Ventaja de RGBA

Mientras `opacity` afecta a todo el elemento y sus hijos, `rgba()` permite definir colores con transparencia sin afectar al contenido interno.

```css
/* Fondo transparente sin afectar al texto */
.fondo-transparente {
    background-color: rgba(0, 0, 0, 0.5); /* Negro al 50% de opacidad */
}

/* Texto con color transparente */
.texto-transparente {
    color: rgba(255, 0, 0, 0.7); /* Rojo al 70% de opacidad */
}
```

### Diferencias clave

- **opacity**: Afecta a todo el elemento y sus hijos (valores de 0 a 1)
- **rgba()**: Solo afecta al color específico (opacidad como cuarto valor)
- **hsla()**: Similar a rgba pero con sistema de color HSL

### Ejemplos prácticos

```css
/* Tarjeta con fondo semitransparente */
.tarjeta {
    background-color: rgba(255, 255, 255, 0.85);
    border: 1px solid rgba(0, 0, 0, 0.1);
}

/* Overlay sobre imágenes */
.imagen-overlay {
    position: relative;
}

.imagen-overlay::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.4);
}
```

## 🔄 Transformaciones básicas

Las transformaciones permiten modificar la forma, tamaño y posición de los elementos sin afectar el flujo del documento.

### rotate (rotación)

Rota un elemento en el plano 2D.

```css
.rotar-15 {
    transform: rotate(15deg);
}

.rotar-45 {
    transform: rotate(45deg);
}

/* Rotación en 3D */
.rotar-3d {
    transform: rotateX(45deg) rotateY(30deg);
}
```

### scale (escalado)

Cambia el tamaño del elemento.

```css
.escalar-1-2 {
    transform: scale(1.2); /* 120% del tamaño original */
}

.escalar-horizontal {
    transform: scaleX(1.5); /* Escala solo horizontalmente */
}

.escalar-vertical {
    transform: scaleY(0.8); /* Escala solo verticalmente */
}
```

### translate (desplazamiento)

Mueve el elemento sin afectar el flujo del documento.

```css
.mover-derecha {
    transform: translateX(20px);
}

.mover-abajo {
    transform: translateY(-10px);
}

.mover-diagonal {
    transform: translate(15px, -10px);
}
```

### skew (inclinación)

Inclina el elemento a lo largo de los ejes X e Y.

```css
.inclinar {
    transform: skew(10deg, 5deg);
}

.inclinar-horizontal {
    transform: skewX(15deg);
}
```

### Combinando transformaciones

```css
.transformacion-completa {
    transform: rotate(15deg) scale(1.1) translateX(10px);
}
```

### Punto de transformación

Define el punto desde el que se aplican las transformaciones.

```css
.tarjeta {
    transform-origin: center center; /* Valor por defecto */
    /* Otros valores: top left, 50% 50%, 20px 30px */
}
```

## ⏳ Transiciones suaves (transition)

Las transiciones permiten cambiar suavemente entre dos estados de un elemento.

### Propiedades de transición

- **transition-property**: Propiedad CSS que se animará
- **transition-duration**: Duración de la transición
- **transition-timing-function**: Curva de velocidad de la transición
- **transition-delay**: Retraso antes de que comience la transición

### Sintaxis abreviada

```css
.elemento {
    transition: [propiedad] [duración] [función de tiempo] [retraso];
}
```

### Ejemplos prácticos

```css
/* Transición básica */
.boton {
    background-color: #3498db;
    transition: background-color 0.3s ease;
}

.boton:hover {
    background-color: #2980b9;
}

/* Transición múltiple */
.tarjeta {
    transform: scale(1);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.tarjeta:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0,0,0,0.15);
}

/* Timing functions */
.ease-in {
    transition-timing-function: ease-in;
}

.ease-out {
    transition-timing-function: ease-out;
}

.ease-in-out {
    transition-timing-function: ease-in-out;
}

.linear {
    transition-timing-function: linear;
}

.cubic-bezier {
    transition-timing-function: cubic-bezier(0.25, 0.1, 0.25, 1);
}
```

### Funciones de tiempo comunes

- **ease**: Comienza lento, acelera y termina lento (por defecto)
- **ease-in**: Comienza lento y acelera
- **ease-out**: Comienza rápido y termina lento
- **ease-in-out**: Comienza y termina lento
- **linear**: Velocidad constante
- **cubic-bezier()**: Permite crear curvas personalizadas

## 🏆 Ejercicio práctico: Botones interactivos con efectos hover

### HTML Structure

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Botones con Efectos Avanzados</title>
    <style>
        /* Estilos base */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 40px 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .page-title {
            text-align: center;
            color: white;
            font-size: 2.5rem;
            margin-bottom: 50px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .buttons-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }
        
        .button-container {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        
        .button-title {
            font-size: 1.2rem;
            font-weight: bold;
            margin-bottom: 20px;
            color: #333;
        }
        
        /* Estilos base para todos los botones */
        .btn {
            display: inline-block;
            padding: 12px 30px;
            font-size: 16px;
            font-weight: 600;
            text-decoration: none;
            border-radius: 8px;
            margin: 10px 5px;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }
        
        /* Botón con gradiente */
        .btn-gradient {
            background: linear-gradient(45deg, #ff6b6b, #ee5a52);
            color: white;
            transition: all 0.3s ease;
        }
        
        .btn-gradient:hover {
            background: linear-gradient(45deg, #ee5a52, #ff6b6b);
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(255, 107, 107, 0.4);
        }
        
        /* Botón con borde animado */
        .btn-border {
            background-color: transparent;
            color: #3498db;
            border: 2px solid #3498db;
            transition: all 0.3s ease;
        }
        
        .btn-border:hover {
            background-color: #3498db;
            color: white;
            border-color: #2980b9;
        }
        
        /* Botón con escala */
        .btn-scale {
            background-color: #e74c3c;
            color: white;
            transition: all 0.3s ease;
        }
        
        .btn-scale:hover {
            transform: scale(1.08);
        }
        
        /* Botón con sombra interna */
        .btn-inset {
            background-color: #9b59b6;
            color: white;
            box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);
            transition: all 0.3s ease;
        }
        
        .btn-inset:hover {
            background-color: #8e44ad;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }
        
        /* Botón 3D */
        .btn-3d {
            background-color: #f39c12;
            color: white;
            transform: perspective(500px) rotateX(0deg);
            transition: all 0.3s ease;
        }
        
        .btn-3d:hover {
            transform: perspective(500px) rotateX(10deg) translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
        }
        
        /* Código de ejemplo */
        .code-container {
            background: #2c3e50;
            color: #ecf0f1;
            padding: 20px;
            border-radius: 8px;
            margin-top: 20px;
            font-family: 'Courier New', monospace;
            font-size: 14px;
            text-align: left;
            overflow-x: auto;
        }
        
        .code-property {
            color: #3498db;
        }
        
        .code-value {
            color: #e74c3c;
        }
        
        .code-comment {
            color: #95a5a6;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .buttons-grid {
                grid-template-columns: 1fr;
            }
            
            .page-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="page-title">Botones con Efectos Avanzados</h1>
        
        <div class="buttons-grid">
            <!-- Botón con gradiente -->
            <div class="button-container">
                <div class="button-title">Botón con Gradiente</div>
                <a href="#" class="btn btn-gradient">Botón Gradiente</a>
                <div class="code-container">
                    <span class="code-comment">/* Botón con gradiente */</span><br>
                    .btn-gradient {<br>
                    &nbsp;&nbsp;background: linear-gradient(45deg, <span class="code-value">#ff6b6b</span>, <span class="code-value">#ee5a52</span>);<br>
                    &nbsp;&nbsp;<span class="code-property">transition</span>: all 0.3s ease;<br>
                    }<br><br>
                    
                    .btn-gradient:hover {<br>
                    &nbsp;&nbsp;transform: <span class="code-value">translateY(-2px)</span>;<br>
                    &nbsp;&nbsp;box-shadow: 0 10px 20px rgba(255, 107, 107, 0.4);<br>
                    }
                </div>
            </div>
            
            <!-- Botón con borde animado -->
            <div class="button-container">
                <div class="button-title">Botón con Borde Animado</div>
                <a href="#" class="btn btn-border">Botón con Borde</a>
                <div class="code-container">
                    <span class="code-comment">/* Botón con borde animado */</span><br>
                    .btn-border {<br>
                    &nbsp;&nbsp;background-color: transparent;<br>
                    &nbsp;&nbsp;color: <span class="code-value">#3498db</span>;<br>
                    &nbsp;&nbsp;border: 2px solid <span class="code-value">#3498db</span>;<br>
                    &nbsp;&nbsp;<span class="code-property">transition</span>: all 0.3s ease;<br>
                    }<br><br>
                    
                    .btn-border:hover {<br>
                    &nbsp;&nbsp;background-color: <span class="code-value">#3498db</span>;<br>
                    &nbsp;&nbsp;color: white;<br>
                    &nbsp;&nbsp;border-color: <span class="code-value">#2980b9</span>;<br>
                    }
                </div>
            </div>
            
            <!-- Botón con escala -->
            <div class="button-container">
                <div class="button-title">Botón con Efecto de Escala</div>
                <a href="#" class="btn btn-scale">Botón Escalado</a>
                <div class="code-container">
                    <span class="code-comment">/* Botón con efecto de escala */</span><br>
                    .btn-scale {<br>
                    &nbsp;&nbsp;<span class="code-property">transition</span>: all 0.3s ease;<br>
                    }<br><br>
                    
                    .btn-scale:hover {<br>
                    &nbsp;&nbsp;transform: <span class="code-value">scale(1.08)</span>;<br>
                    }
                </div>
            </div>
            
            <!-- Botón con sombra interna -->
            <div class="button-container">
                <div class="button-title">Botón con Sombra Interna</div>
                <a href="#" class="btn btn-inset">Botón con Sombra</a>
                <div class="code-container">
                    <span class="code-comment">/* Botón con sombra interna */</span><br>
                    .btn-inset {<br>
                    &nbsp;&nbsp;box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.2);<br>
                    &nbsp;&nbsp;<span class="code-property">transition</span>: all 0.3s ease;<br>
                    }<br><br>
                    
                    .btn-inset:hover {<br>
                    &nbsp;&nbsp;background-color: <span class="code-value">#8e44ad</span>;<br>
                    &nbsp;&nbsp;box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);<br>
                    }
                </div>
            </div>
            
            <!-- Botón 3D -->
            <div class="button-container">
                <div class="button-title">Botón con Transformación 3D</div>
                <a href="#" class="btn btn-3d">Botón 3D</a>
                <div class="code-container">
                    <span class="code-comment">/* Botón con transformación 3D */</span><br>
                    .btn-3d {<br>
                    &nbsp;&nbsp;transform: perspective(500px) rotateX(0deg);<br>
                    &nbsp;&nbsp;<span class="code-property">transition</span>: all 0.3s ease;<br>
                    }<br><br>
                    
                    .btn-3d:hover {<br>
                    &nbsp;&nbsp;transform: perspective(500px) rotateX(10deg) translateY(-3px);<br>
                    &nbsp;&nbsp;box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);<br>
                    }
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

### Pasos para completar el ejercicio

1. Crea un nuevo archivo en tu editor de código y guárdalo como `botones-efectos.html`
2. Copia la estructura básica de HTML
3. Agrega las secciones de estilos en el `<head>`
4. Personaliza los colores, tamaños y efectos según tus preferencias
5. Experimenta con diferentes combinaciones de sombras, transformaciones y transiciones
6. Ajusta los valores de duración y timing function para ver cómo afectan a la animación
7. Prueba tus botones en diferentes dispositivos para verificar su comportamiento
8. Guarda el archivo y ábrelo en tu navegador

## 📎 Recurso adicional: Cheat Sheet de efectos avanzados

### Sombra de caja (box-shadow)

```css
/* Sintaxis */
box-shadow: [inset] offset-x offset-y blur-radius spread-radius color;

/* Ejemplos */
box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3); /* Sombra simple */
box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2); /* Sombra elevada */
box-shadow: inset 2px 2px 5px rgba(0, 0, 0, 0.2); /* Sombra interna */
box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3), -5px -5px 10px rgba(255, 255, 255, 0.5); /* Múltiples sombras */
```

### Opacidad y RGBA

```css
/* Opacidad del elemento completo */
opacity: 0.7; /* 0 = transparente, 1 = opaco */

/* Colores con transparencia (solo afecta al color) */
background-color: rgba(255, 0, 0, 0.5); /* Rojo al 50% de opacidad */
color: rgba(0, 0, 255, 0.8); /* Azul al 80% de opacidad */

/* HSL con transparencia */
background-color: hsla(120, 100%, 50%, 0.6); /* Verde al 60% de opacidad */
```

### Transformaciones

```css
/* Rotación */
transform: rotate(15deg);
transform: rotateX(45deg) rotateY(30deg);

/* Escalado */
transform: scale(1.2);
transform: scaleX(1.5) scaleY(0.8);

/* Desplazamiento */
transform: translate(10px, -5px);
transform: translateX(20px) translateY(-10px);

/* Inclinación */
transform: skew(10deg, 5deg);
transform: skewX(15deg);

/* Punto de transformación */
transform-origin: center center; /* Valores: top, bottom, left, right, % */
```

### Transiciones

```css
/* Sintaxis completa */
transition: property duration timing-function delay;

/* Ejemplos */
transition: background-color 0.3s ease;
transition: all 0.4s cubic-bezier(0.25, 0.1, 0.25, 1);
transition: transform 0.3s ease, box-shadow 0.3s ease;

/* Timing functions */
transition-timing-function: ease; /* Por defecto */
transition-timing-function: ease-in;
transition-timing-function: ease-out;
transition-timing-function: ease-in-out;
transition-timing-function: linear;
transition-timing-function: cubic-bezier(0.25, 0.1, 0.25, 1);
```

## 💡 Consejo: Cómo usar efectos sin afectar el rendimiento

Los efectos avanzados pueden mejorar la experiencia del usuario, pero si no se usan correctamente pueden afectar el rendimiento del sitio. Aquí te comparto consejos profesionales para implementar efectos sin comprometer la velocidad:

### Propiedades que no afectan el rendimiento

Algunas propiedades son más eficientes para animar porque el navegador puede manejarlas en la GPU:

- `transform` (scale, rotate, translate)
- `opacity`

```css
/* Buen rendimiento */
.elemento {
    transition: transform 0.3s ease, opacity 0.3s ease;
}
```

### Propiedades que afectan el rendimiento

Evita animar estas propiedades si es posible, ya que obligan al navegador a recalcular el layout y el paint:

- `width`, `height`
- `padding`, `margin`
- `top`, `left`, `right`, `bottom`
- `border`

```css
/* Mal rendimiento (evita si es posible) */
.elemento {
    transition: width 0.3s ease, height 0.3s ease;
}
```

### Técnicas para optimizar efectos

#### 1. Usa will-change para indicar al navegador

```css
.elemento {
    will-change: transform, opacity;
}
```

> **Nota**: Usa con moderación, solo para elementos que realmente se animarán

#### 2. Fuerza el uso de la GPU

```css
.elemento {
    transform: translateZ(0);
    /* O */
    backface-visibility: hidden;
}
```

#### 3. Limita la complejidad de las sombras

```css
/* En lugar de */
box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);

/* Usa */
box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
```

#### 4. Controla el número de elementos animados

- Evita animar demasiados elementos simultáneamente
- Usa `@media` para desactivar animaciones en dispositivos móviles si es necesario

#### 5. Ajusta la duración de las transiciones

```css
/* Duraciones óptimas */
transition: all 200-500ms; /* Demasiado corto o largo afecta la experiencia */
```

#### 6. Usa cubic-bezier personalizados para mejor rendimiento

```css
transition-timing-function: cubic-bezier(0.25, 0.1, 0.25, 1);
```

### Prueba el rendimiento con herramientas del navegador

- Chrome DevTools > Performance
- Firefox DevTools > Performance
- Busca "layout thrashing" y "paint flashing"

### Regla de oro

> "Siempre prioriza la experiencia del usuario sobre los efectos visuales. Un sitio rápido con efectos simples es mejor que un sitio lento con efectos impresionantes."

## 🏆 Reto Adicional: Crear una Galería de Proyectos con Efectos Interactivos

¡Felicidades por completar los ejercicios de efectos avanzados y transiciones! Aquí tienes un reto adicional para que practiques aún más:

### 📚 Descripción del Reto

Crea una galería de proyectos interactiva con los siguientes elementos:

- Tarjetas de proyecto que reaccionen al pasar el mouse con múltiples efectos
- Efecto de "zoom" suave en las imágenes al hacer hover
- Superposición de información con opacidad controlada
- Transiciones suaves para todos los efectos
- Efecto de elevación realista al hacer hover
- Diseño responsivo que funcione en móviles y escritorio

### 📌 Ejemplo de Cómo Debería Verse

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galería de Proyectos Interactiva</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 40px 20px;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .gallery-title {
            text-align: center;
            color: white;
            font-size: 3rem;
            margin-bottom: 60px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
        }

        .project-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.4s cubic-bezier(0.25, 0.1, 0.25, 1);
            transform: translateY(0);
        }

        .project-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
        }

        .project-image {
            position: relative;
            overflow: hidden;
            height: 250px;
        }

        .project-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }

        .project-card:hover .project-image img {
            transform: scale(1.1);
        }

        .project-overlay {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.7);
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .project-card:hover .project-overlay {
            opacity: 1;
        }

        .project-title {
            color: white;
            font-size: 1.5rem;
            margin-bottom: 10px;
            transform: translateY(20px);
            transition: transform 0.3s ease;
        }

        .project-category {
            color: #ecf0f1;
            font-size: 1rem;
            transform: translateY(20px);
            transition: transform 0.3s ease 0.1s;
        }

        .project-card:hover .project-title,
        .project-card:hover .project-category {
            transform: translateY(0);
        }

        .project-info {
            padding: 25px;
        }

        .project-info h2 {
            color: #2c3e50;
            font-size: 1.3rem;
            margin-bottom: 15px;
        }

        .project-description {
            color: #7f8c8d;
            line-height: 1.6;
            margin-bottom: 20px;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-bottom: 20px;
        }

        .tag {
            background: #e8f4fd;
            color: #3498db;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 500;
        }

        .btn {
            display: inline-block;
            background: linear-gradient(45deg, #3498db, #2980b9);
            color: white;
            padding: 12px 25px;
            text-decoration: none;
            border-radius: 25px;
            font-weight: 600;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(52, 152, 219, 0.4);
        }

        @media (max-width: 768px) {
            .gallery-title {
                font-size: 2rem;
            }
            
            .project-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="gallery-title">Mi Portafolio</h1>
        
        <div class="project-grid">
            <!-- Proyecto 1 -->
            <div class="project-card">
                <div class="project-image">
                    <img src="https://via.placeholder.com/600x400/3498db/ffffff?text=Sitio+Web" alt="Proyecto 1">
                    <div class="project-overlay">
                        <h2 class="project-title">Sitio Web Corporativo</h2>
                        <p class="project-category">Desarrollo Web</p>
                    </div>
                </div>
                <div class="project-info">
                    <h2>Sitio Web Corporativo</h2>
                    <p class="project-description">Desarrollo completo de sitio web responsivo para empresa de tecnología, incluyendo sistema de gestión de contenidos y optimización SEO.</p>
                    <div class="project-tags">
                        <span class="tag">HTML5</span>
                        <span class="tag">CSS3</span>
                        <span class="tag">JavaScript</span>
                        <span class="tag">PHP</span>
                    </div>
                    <a href="#" class="btn">Ver Proyecto</a>
                </div>
            </div>
            
            <!-- Proyecto 2 -->
            <div class="project-card">
                <div class="project-image">
                    <img src="https://via.placeholder.com/600x400/e74c3c/ffffff?text=App+Móvil" alt="Proyecto 2">
                    <div class="project-overlay">
                        <h2 class="project-title">Aplicación Móvil</h2>
                        <p class="project-category">Desarrollo Móvil</p>
                    </div>
                </div>
                <div class="project-info">
                    <h2>Aplicación Móvil</h2>
                    <p class="project-description">Aplicación para gestión de tareas con interfaz intuitiva y sincronización en tiempo real entre dispositivos.</p>
                    <div class="project-tags">
                        <span class="tag">React Native</span>
                        <span class="tag">Firebase</span>
                        <span class="tag">UI/UX</span>
                    </div>
                    <a href="#" class="btn">Ver Proyecto</a>
                </div>
            </div>
            
            <!-- Proyecto 3 -->
            <div class="project-card">
                <div class="project-image">
                    <img src="https://via.placeholder.com/600x400/9b59b6/ffffff?text=UI/UX+Design" alt="Proyecto 3">
                    <div class="project-overlay">
                        <h2 class="project-title">Diseño UI/UX</h2>
                        <p class="project-category">Experiencia de Usuario</p>
                    </div>
                </div>
                <div class="project-info">
                    <h2>Diseño UI/UX</h2>
                    <p class="project-description">Rediseño completo de la interfaz de usuario para una aplicación de finanzas personales, mejorando la usabilidad en un 40%.</p>
                    <div class="project-tags">
                        <span class="tag">Figma</span>
                        <span class="tag">Prototipado</span>
                        <span class="tag">Investigación</span>
                    </div>
                    <a href="#" class="btn">Ver Proyecto</a>
                </div>
            </div>
            
            <!-- Proyecto 4 -->
            <div class="project-card">
                <div class="project-image">
                    <img src="https://via.placeholder.com/600x400/f39c12/ffffff?text=Sistema+Admin" alt="Proyecto 4">
                    <div class="project-overlay">
                        <h2 class="project-title">Sistema Administrativo</h2>
                        <p class="project-category">Desarrollo Web</p>
                    </div>
                </div>
                <div class="project-info">
                    <h2>Sistema Administrativo</h2>
                    <p class="project-description">Plataforma para gestión de inventario y ventas con panel de administración intuitivo y reportes en tiempo real.</p>
                    <div class="project-tags">
                        <span class="tag">PHP</span>
                        <span class="tag">MySQL</span>
                        <span class="tag">Bootstrap</span>
                    </div>
                    <a href="#" class="btn">Ver Proyecto</a>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

### 💡 Consejos para Completar el Reto

1. **Usa transform y opacity para todas las animaciones** (mejor rendimiento)
2. **Implementa el efecto de "zoom" en las imágenes** con `transform: scale()`
3. **Crea superposiciones con rgba()** para controlar la transparencia sin afectar al texto
4. **Usa will-change y translateZ(0)** para optimizar el rendimiento
5. **Ajusta los tiempos de transición** para crear una secuencia de animación suave
6. **Prueba diferentes timing functions** para ver cómo afectan a la sensación de los efectos
7. **Asegúrate de que el diseño sea responsivo** probando en diferentes tamaños de pantalla
8. **Si te sientes cómodo, añade un efecto de "parallax" suave** al hacer hover

### 📅 Entrega

¡Tómate el tiempo que necesites! Cuando termines, comparte tu código en el grupo de WhatsApp y te daré feedback personalizado.

**Bonus**: Si completas este reto, ¡recibirás una colección de efectos avanzados de CSS que utilizan animaciones keyframes para proyectos profesionales!

¿Te animas a aceptar el reto? ¡Tu galería de proyectos podría ser el elemento más destacado de tu portafolio! 🌟✨

---

## 📝 Resumen de la Clase

En esta clase hemos aprendido:

### ✅ Conceptos Clave

- **Box-shadow**: Crear sombras simples, elevadas, internas y múltiples
- **Opacity vs RGBA**: Diferencias y cuándo usar cada una
- **Transformaciones**: rotate, scale, translate, skew y sus combinaciones
- **Transiciones**: Sintaxis, timing functions y optimización
- **Efectos de hover**: Implementación profesional en botones
- **Optimización de rendimiento**: Qué propiedades animar y cuáles evitar

### 🎯 Skills Desarrollados

- Crear efectos visuales atractivos y profesionales
- Optimizar animaciones para mejor rendimiento
- Implementar transiciones suaves y naturales
- Combinar múltiples efectos de manera armoniosa
- Diseñar componentes interactivos modernos

### 🚀 Próximos Pasos

1. **Practica con el ejercicio de botones** hasta dominar cada efecto
2. **Acepta el reto de la galería** para consolidar todos los conceptos
3. **Experimenta con diferentes combinaciones** de efectos
4. **Aplica estos efectos** en tus proyectos personales
5. **Prepárate para la siguiente clase** donde veremos animaciones keyframes

¡Felicidades por completar esta clase! Has dado un gran paso hacia convertirte en un desarrollador frontend con habilidades avanzadas en CSS. 🎉
