# Clase 5: Entendiendo el Modelo de Caja en CSS

## 📌 Objetivos de la Clase
- Comprender el modelo de caja (box model) y sus componentes
- Dominar el uso de márgenes (margin) y relleno (padding)
- Aprender a trabajar con bordes (border) y sus propiedades
- Entender la diferencia entre box-sizing: border-box y content-box
- Crear tarjetas de producto con espaciado adecuado

## 📦 Modelo de Caja - Conceptos Básicos

### Cálculo del tamaño total de un elemento
```
Ancho total = margin-left + border-left + padding-left + width + padding-right + border-right + margin-right
Alto total = margin-top + border-top + padding-top + height + padding-bottom + border-bottom + margin-bottom
```

## 📏 Márgenes (margin) y Relleno (padding)

### Márgenes
```css
/* Propiedades individuales */
.elemento {
    margin-top: 10px;
    margin-right: 20px;
    margin-bottom: 10px;
    margin-left: 20px;
}

/* Forma abreviada */
.elemento {
    /* top right bottom left */
    margin: 10px 20px 10px 20px;
    
    /* También se puede usar con 2 valores: */
    /* vertical horizontal */
    /* margin: 10px 20px; */
    
    /* O con 3 valores: */
    /* top horizontal bottom */
    /* margin: 10px 20px 15px; */
}
```

### Relleno (padding)
```css
/* Propiedades individuales */
.elemento {
    padding-top: 10px;
    padding-right: 20px;
    padding-bottom: 10px;
    padding-left: 20px;
}

/* Forma abreviada */
.elemento {
    /* top right bottom left */
    padding: 10px 20px 10px 20px;
}
```

## 🔲 Bordes (border) y sus propiedades

### Estilos de borde
```css
/* Forma detallada */
.elemento {
    border-width: 2px;
    border-style: solid;
    border-color: #333;
}

/* Forma abreviada */
.elemento {
    border: 2px solid #333;
}

/* Bordes individuales */
.elemento {
    border-top: 1px solid #000;
    border-right: 2px dashed #f00;
    border-bottom: 3px double #0f0;
    border-left: 4px dotted #00f;
}

/* Bordes redondeados */
.elemento {
    border-radius: 15px;
    /* También se puede especificar cada esquina */
    /* border-radius: 10px 20px 30px 40px; */
}
```

## 📐 Box-sizing: border-box vs content-box

### content-box (valor por defecto)
```css
.contenido-box {
    box-sizing: content-box;
    width: 300px;
    padding: 20px;
    border: 10px solid #333;
    /* Ancho total = 300px + 20px + 20px + 10px + 10px = 360px */
}
```

### border-box (recomendado)
```css
.border-box {
    box-sizing: border-box;
    width: 300px;
    padding: 20px;
    border: 10px solid #333;
    /* Ancho total = 300px (incluye padding y borde) */
}
```

### Configuración recomendada
```css
* {
    box-sizing: border-box;
}
```

## 🏆 Ejercicio Práctico: Tarjetas de Producto

### HTML Completo
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tarjetas de Producto - Modelo de Caja</title>
    <style>
        /* Reset básico y box-sizing */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            color: white;
            margin-bottom: 40px;
        }

        header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .subtitle {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 40px;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .product-image {
            background: linear-gradient(45deg, #f093fb 0%, #f5576c 100%);
            height: 200px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 1.1rem;
        }

        .product-info {
            padding: 20px;
        }

        .product-title {
            font-size: 1.4rem;
            color: #333;
            margin-bottom: 10px;
        }

        .product-description {
            color: #666;
            line-height: 1.5;
            margin-bottom: 15px;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #e74c3c;
            margin-bottom: 15px;
        }

        .product-tags {
            margin-bottom: 20px;
        }

        .tag {
            display: inline-block;
            background: #3498db;
            color: white;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 0.8rem;
            margin-right: 8px;
            margin-bottom: 5px;
        }

        .tag:nth-child(even) {
            background: #2ecc71;
        }

        .btn {
            display: inline-block;
            background: #667eea;
            color: white;
            padding: 12px 25px;
            text-decoration: none;
            border-radius: 25px;
            font-weight: 500;
            transition: background 0.3s ease;
            text-align: center;
            width: 100%;
        }

        .btn:hover {
            background: #5a6fd8;
        }

        @media (max-width: 768px) {
            .product-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Nuestra Colección de Productos</h1>
            <p class="subtitle">Descubre nuestros productos destacados con diseños modernos y funcionalidades excepcionales</p>
        </header>
        
        <div class="product-grid">
            <div class="product-card">
                <div class="product-image">Imagen del Producto 1</div>
                <div class="product-info">
                    <h2 class="product-title">Producto Premium</h2>
                    <p class="product-description">Diseño elegante y funcionalidad avanzada para satisfacer todas tus necesidades.</p>
                    <p class="product-price">Q 299.99</p>
                    <div class="product-tags">
                        <span class="tag">Destacado</span>
                        <span class="tag">Nuevo</span>
                    </div>
                    <a href="#" class="btn">Agregar al carrito</a>
                </div>
            </div>
            
            <div class="product-card">
                <div class="product-image">Imagen del Producto 2</div>
                <div class="product-info">
                    <h2 class="product-title">Producto Estándar</h2>
                    <p class="product-description">Calidad confiable a un precio accesible, perfecto para uso diario.</p>
                    <p class="product-price">Q 149.99</p>
                    <div class="product-tags">
                        <span class="tag">Popular</span>
                    </div>
                    <a href="#" class="btn">Agregar al carrito</a>
                </div>
            </div>
            
            <div class="product-card">
                <div class="product-image">Imagen del Producto 3</div>
                <div class="product-info">
                    <h2 class="product-title">Producto Básico</h2>
                    <p class="product-description">Esencial y funcional, todo lo que necesitas sin complicaciones.</p>
                    <p class="product-price">Q 79.99</p>
                    <div class="product-tags">
                        <span class="tag">Económico</span>
                        <span class="tag">Mejor valor</span>
                    </div>
                    <a href="#" class="btn">Agregar al carrito</a>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
```

## 🏆 Reto Adicional: Catálogo de Productos Responsivo

### HTML del Catálogo Avanzado
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Catálogo de Productos Responsivo</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: #f8f9fa;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
        }

        h1 {
            color: #2c3e50;
            font-size: 2.5rem;
            margin-bottom: 10px;
        }

        .subtitle {
            color: #7f8c8d;
            font-size: 1.1rem;
        }

        .filters {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 8px 20px;
            background: #ecf0f1;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .filter-btn.active,
        .filter-btn:hover {
            background: #3498db;
            color: white;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .product-card {
            background: white;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
        }

        .product-image {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            height: 180px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            position: relative;
        }

        .product-info {
            padding: 20px;
        }

        .product-title {
            font-size: 1.2rem;
            color: #2c3e50;
            margin-bottom: 8px;
        }

        .product-description {
            color: #7f8c8d;
            font-size: 0.9rem;
            margin-bottom: 12px;
        }

        .product-price {
            font-size: 1.4rem;
            font-weight: bold;
            color: #e74c3c;
            margin-bottom: 10px;
        }

        .product-meta {
            display: flex;
            gap: 15px;
            font-size: 0.8rem;
            color: #95a5a6;
            margin-bottom: 12px;
        }

        .product-tags {
            margin-bottom: 15px;
        }

        .tag {
            display: inline-block;
            background: #ecf0f1;
            color: #2c3e50;
            padding: 4px 10px;
            border-radius: 15px;
            font-size: 0.7rem;
            margin-right: 6px;
            margin-bottom: 4px;
        }

        .btn-container {
            display: flex;
            gap: 10px;
        }

        .btn {
            flex: 1;
            padding: 10px;
            text-decoration: none;
            text-align: center;
            border-radius: 6px;
            font-weight: 500;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .btn-primary {
            background: #3498db;
            color: white;
        }

        .btn-primary:hover {
            background: #2980b9;
        }

        .btn-secondary {
            background: #ecf0f1;
            color: #2c3e50;
        }

        .btn-secondary:hover {
            background: #bdc3c7;
        }

        .pagination {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 40px;
        }

        .page {
            padding: 10px 15px;
            text-decoration: none;
            background: white;
            color: #2c3e50;
            border-radius: 6px;
            transition: all 0.3s ease;
        }

        .page.active,
        .page:hover {
            background: #3498db;
            color: white;
        }

        @media (max-width: 768px) {
            .product-grid {
                grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            }
            
            .filters {
                flex-direction: column;
                align-items: center;
            }
            
            h1 {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Catálogo de Productos</h1>
            <p class="subtitle">Encuentra exactamente lo que necesitas</p>
        </header>
        
        <div class="filters">
            <button class="filter-btn active">Todos</button>
            <button class="filter-btn">Electrónica</button>
            <button class="filter-btn">Ropa</button>
            <button class="filter-btn">Hogar</button>
            <button class="filter-btn">Deportes</button>
        </div>
        
        <div class="product-grid">
            <!-- Producto 1 -->
            <div class="product-card">
                <div class="product-image">
                    <span>Imagen del Producto 1</span>
                </div>
                <div class="product-info">
                    <h2 class="product-title">Smartphone Pro Max</h2>
                    <p class="product-description">Teléfono inteligente de última generación con cámara de 108MP y 5G.</p>
                    <p class="product-price">Q 2,499.99</p>
                    <div class="product-meta">
                        <span>⭐ 4.7 (1,234 reseñas)</span>
                        <span>🔥 156 vendidos</span>
                    </div>
                    <div class="product-tags">
                        <span class="tag">Electrónica</span>
                        <span class="tag">Destacado</span>
                    </div>
                    <div class="btn-container">
                        <a href="#" class="btn btn-primary">Comprar</a>
                        <a href="#" class="btn btn-secondary">+ Lista</a>
                    </div>
                </div>
            </div>
            
            <!-- Producto 2 -->
            <div class="product-card">
                <div class="product-image">
                    <span>Imagen del Producto 2</span>
                </div>
                <div class="product-info">
                    <h2 class="product-title">Laptop Ultra Slim</h2>
                    <p class="product-description">Laptop ultraligera con procesador i7, 16GB de RAM y SSD de 512GB.</p>
                    <p class="product-price">Q 4,799.99</p>
                    <div class="product-meta">
                        <span>⭐ 4.5 (876 reseñas)</span>
                        <span>🔥 98 vendidos</span>
                    </div>
                    <div class="product-tags">
                        <span class="tag">Electrónica</span>
                        <span class="tag">Nuevo</span>
                    </div>
                    <div class="btn-container">
                        <a href="#" class="btn btn-primary">Comprar</a>
                        <a href="#" class="btn btn-secondary">+ Lista</a>
                    </div>
                </div>
            </div>
            
            <!-- Producto 3 -->
            <div class="product-card">
                <div class="product-image">
                    <span>Imagen del Producto 3</span>
                </div>
                <div class="product-info">
                    <h2 class="product-title">Reloj Inteligente</h2>
                    <p class="product-description">Monitor de salud avanzado con GPS, resistente al agua y hasta 7 días de batería.</p>
                    <p class="product-price">Q 799.99</p>
                    <div class="product-meta">
                        <span>⭐ 4.8 (2,345 reseñas)</span>
                        <span>🔥 320 vendidos</span>
                    </div>
                    <div class="product-tags">
                        <span class="tag">Electrónica</span>
                        <span class="tag">Mejor valor</span>
                    </div>
                    <div class="btn-container">
                        <a href="#" class="btn btn-primary">Comprar</a>
                        <a href="#" class="btn btn-secondary">+ Lista</a>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="pagination">
            <a href="#" class="page active">1</a>
            <a href="#" class="page">2</a>
            <a href="#" class="page">3</a>
            <a href="#" class="page">4</a>
            <a href="#" class="page">5</a>
            <a href="#" class="page">→</a>
        </div>
    </div>
</body>
</html>
```

## 📎 Cheat Sheet del Modelo de Caja

### Componentes del modelo de caja:
- **Contenido**: Área donde se muestra el texto o imagen
- **Relleno (padding)**: Espacio entre contenido y borde
- **Borde (border)**: Línea que rodea el contenido y relleno
- **Márgenes (margin)**: Espacio exterior entre bordes

### Propiedades de márgenes:
```css
margin-top, margin-right, margin-bottom, margin-left
margin: top right bottom left /* forma abreviada */
margin: vertical horizontal
margin: top horizontal bottom
```

### Propiedades de relleno:
```css
padding-top, padding-right, padding-bottom, padding-left
padding: top right bottom left /* forma abreviada */
padding: vertical horizontal
```

### Propiedades de bordes:
```css
border-width: /* Ancho del borde */
border-style: /* solid, dotted, dashed, double */
border-color: /* Color del borde */
border-radius: /* Radio de las esquinas */
border: width style color /* forma abreviada */
```

### Box-sizing:
```css
box-sizing: content-box; /* por defecto */
box-sizing: border-box; /* recomendado */

/* Aplicar a todos los elementos */
* { box-sizing: border-box; }
```

## 🛠️ Herramientas del Navegador

### Acceso:
- **Chrome/Firefox/Edge**: F12 o Ctrl+Shift+I (Windows) / Cmd+Opt+I (Mac)
- **Safari**: Habilitar herramientas de desarrollador en Preferencias > Avanzado

### Inspección del modelo de caja:
1. Abrir herramientas de desarrollo
2. Clic en "Inspeccionar elemento" o Ctrl+Shift+C / Cmd+Shift+C
3. Seleccionar elemento en la página
4. Ver sección del modelo de caja en panel "Elements"/"Inspector"

### Consejos profesionales:
- Usar modo "Layout" en Chrome para overlays de grid/flexbox
- Activar "Box Model" en Firefox para más detalles
- Modificar valores en tiempo real para experimentar
- Usar selector de color integrado

## 💡 Consejos para el Reto

1. **Estructura HTML**: Empieza con la estructura antes de añadir estilos
2. **Box-sizing**: Usa `box-sizing: border-box` en todos los elementos
3. **Consistencia**: Aplica márgenes y rellenos de manera consistente
4. **Responsivo**: Usa grid o flexbox para diseño adaptable
5. **Experimentación**: Prueba diferentes valores para bordes y radios
6. **Compatibilidad**: Asegúrate de que funcione en móviles y escritorio
7. **Animaciones**: Añade efectos sutiles con `:hover` si te sientes cómodo
