# Clase 3: Multimedia y Estructura con Divs

## 📌 Objetivos de la Clase
- Aprender a integrar elementos multimedia (audio y video) en una página web
- Entender los atributos esenciales para controlar el comportamiento de multimedia
- Dominar el uso del elemento `<div>` como contenedor principal
- Aprender a estructurar contenido con divs semánticos
- Crear una sección de multimedia funcional para un blog

## 🎧 Integración de Audio en HTML

El elemento `<audio>` se utiliza para reproducir archivos de audio en una página web.

```html
<audio controls>
    <source src="audio/ejemplo.mp3" type="audio/mpeg">
    Tu navegador no soporta el elemento de audio.
</audio>
```

### Atributos esenciales:
- **controls**: Muestra controles para reproducir, pausar y ajustar el volumen
- **autoplay**: Hace que el audio se reproduzca automáticamente al cargarse la página
- **loop**: Hace que el contenido se reproduzca en bucle
- **muted**: Silencia el audio inicialmente

### Formatos compatibles:
- **MP3 (audio/mpeg)**: Ampliamente compatible con la mayoría de navegadores
- **WAV (audio/wav)**: Calidad sin compresión, pero archivos grandes
- **OGG (audio/ogg)**: Formato abierto, compatible con la mayoría de navegadores modernos

### Ejemplo avanzado:
```html
<audio controls autoplay loop>
    <source src="musica.mp3" type="audio/mpeg">
    <source src="musica.ogg" type="audio/ogg">
    Tu navegador no soporta el elemento de audio.
</audio>
```

## 🎥 Integración de Video en HTML

El elemento `<video>` se utiliza para reproducir archivos de video en una página web.

```html
<video controls width="600">
    <source src="video/ejemplo.mp4" type="video/mp4">
    Tu navegador no soporta el elemento de video.
</video>
```

### Atributos esenciales:
- **controls**: Muestra controles para reproducir, pausar y ajustar el volumen
- **width/height**: Define el tamaño del video
- **autoplay**: Reproduce el video automáticamente al cargarse la página
- **loop**: Hace que el video se reproduzca en bucle
- **poster**: Especifica una imagen que se muestra mientras se carga el video
- **muted**: Silencia el video inicialmente

### Formatos compatibles:
- **MP4 (video/mp4)**: Ampliamente compatible (usando codec H.264)
- **WebM (video/webm)**: Formato abierto, compatible con navegadores modernos
- **OGG (video/ogg)**: Menos común pero compatible con algunos navegadores

### Ejemplo avanzado:
```html
<video controls width="800" height="450" poster="portada.jpg">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    Tu navegador no soporta el elemento de video.
</video>
```

## 📦 Elemento `<div>` en HTML

El elemento `<div>` es un contenedor genérico en HTML que se utiliza para agrupar otros elementos y aplicarles estilos o scripts. No tiene un significado específico por sí mismo, pero es muy útil para la estructura y el diseño de las páginas web.

```html
<div class="contenedor-principal">
    <h1>Título de la sección</h1>
    <p>Este es un párrafo dentro de un div.</p>
</div>
```

### Buenas prácticas con `<div>`:
- Nunca usar divs cuando exista una etiqueta semántica más apropiada (como `<header>`, `<footer>`, `<article>`, etc.)
- Siempre añadir clases o IDs descriptivos para facilitar el estilizado
- Evitar anidar demasiados divs (máximo 3-4 niveles de profundidad)
- Mantener la estructura organizada con comentarios HTML

### Ejemplo de estructura con divs:
```html
<div class="blog-post">
    <div class="post-header">
        <h2>Título del Artículo</h2>
        <p class="post-date">Publicado el 15 de mayo de 2024</p>
    </div>
    
    <div class="post-content">
        <p>Contenido del artículo...</p>
        <div class="multimedia">
            <video controls width="100%">
                <source src="video.mp4" type="video/mp4">
                Tu navegador no soporta el elemento de video.
            </video>
        </div>
    </div>
    
    <div class="post-footer">
        <p>Categorías: <a href="#">Tecnología</a>, <a href="#">Web</a></p>
    </div>
</div>
```

## 🌐 Estructurar contenido con divs semánticos

Aunque HTML5 introdujo etiquetas semánticas (`<header>`, `<footer>`, `<article>`, etc.), los `<div>` siguen siendo esenciales para agrupar contenido. La clave está en usarlos de manera inteligente:

### Estructura básica de una página:
```html
<div class="wrapper">
    <div class="header">
        <h1>Mi Sitio Web</h1>
    </div>
    
    <div class="nav">
        <ul>
            <li><a href="#">Inicio</a></li>
            <li><a href="#">Blog</a></li>
            <li><a href="#">Contacto</a></li>
        </ul>
    </div>
    
    <div class="content">
        <div class="main">
            <h2>Contenido Principal</h2>
            <!-- Aquí iría el contenido principal -->
        </div>
        
        <div class="sidebar">
            <h3>Lateral</h3>
            <!-- Aquí iría el contenido lateral -->
        </div>
    </div>
    
    <div class="footer">
        <p>&copy; 2024 Mi Sitio Web</p>
    </div>
</div>
```

### Consejos para estructurar con divs:
- Usar clases descriptivas que indiquen el propósito del div
- Mantener una jerarquía clara con sangría adecuada en el código
- Agregar comentarios para secciones importantes
- Evitar divitis (exceso de divs sin necesidad)

## 🏆 Ejercicio práctico: Crear una sección de multimedia para un blog

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sección Multimedia - Blog de Viajes</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        
        .blog-container {
            max-width: 800px;
            margin: 0 auto;
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0,0,0,0.1);
        }
        
        .post-header {
            text-align: center;
            margin-bottom: 30px;
            border-bottom: 3px solid #3498db;
            padding-bottom: 20px;
        }
        
        .post-header h1 {
            color: #2c3e50;
            font-size: 2.5em;
            margin-bottom: 10px;
        }
        
        .post-date {
            color: #7f8c8d;
            font-style: italic;
        }
        
        .audio-section, .video-section, .description {
            margin-bottom: 40px;
            padding: 20px;
            background-color: #ecf0f1;
            border-radius: 8px;
        }
        
        .section-title {
            margin-bottom: 15px;
            color: #2c3e50;
        }
        
        .video-container {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 Aspect Ratio */
            height: 0;
            overflow: hidden;
        }
        
        .video-container video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
    </style>
</head>
<body>
    <div class="blog-container">
        <div class="post-header">
            <h1>Explorando los Sonidos y Visuales de la Naturaleza</h1>
            <p class="post-date">Publicado el 20 de mayo de 2024</p>
        </div>
        
        <div class="post-content">
            <div class="audio-section">
                <h2 class="section-title">Sonidos de la Selva</h2>
                <p>Escucha los increíbles sonidos de la selva tropical en este audio grabado durante mi viaje a la Amazonía.</p>
                <audio controls style="width: 100%; margin-top: 15px;">
                    <source src="audio/selva.mp3" type="audio/mpeg">
                    Tu navegador no soporta el elemento de audio.
                </audio>
            </div>
            
            <div class="video-section">
                <h2 class="section-title">Puesta de Sol en la Montaña</h2>
                <p>Vive la experiencia de una impresionante puesta de sol desde la cima de la montaña Nevado.</p>
                <div class="video-container">
                    <video controls poster="imagenes/poster.jpg">
                        <source src="video/puesta-de-sol.mp4" type="video/mp4">
                        <source src="video/puesta-de-sol.webm" type="video/webm">
                        Tu navegador no soporta el elemento de video.
                    </video>
                </div>
            </div>
            
            <div class="description">
                <h2 class="section-title">Descripción</h2>
                <p>Esta sección multimedia forma parte de mi serie "Viajes alrededor del mundo", donde comparto experiencias auditivas y visuales de mis viajes. Los sonidos y videos son grabaciones originales que realicé durante mis expediciones.</p>
                <p>Si deseas más contenido similar, ¡no olvides suscribirte a mi canal!</p>
            </div>
        </div>
    </div>
</body>
</html>
```

### Pasos para completar el ejercicio:
1. Crea un nuevo archivo en tu editor de código y guárdalo como `seccion-multimedia.html`
2. Copia la estructura básica de HTML
3. Agrega las secciones de audio y video usando los elementos `<audio>` y `<video>`
4. Si no tienes archivos de audio/video reales, usa estos enlaces de ejemplo:
   - **Audio**: https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3
   - **Video**: https://storage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4
   - **Poster**: https://via.placeholder.com/800x450
5. Personaliza los estilos con CSS
6. Guarda el archivo y ábrelo en tu navegador

## 📎 Recurso adicional: Formatos compatibles y mejores prácticas

### Formatos de audio compatibles:
| Formato | Tipo MIME | Compatibilidad |
|---------|-----------|----------------|
| MP3 | audio/mpeg | Excelente (todos los navegadores) |
| WAV | audio/wav | Bueno |
| OGG | audio/ogg | Bueno (excepto en Safari) |

### Formatos de video compatibles:
| Formato | Tipo MIME | Compatibilidad |
|---------|-----------|----------------|
| MP4 (H.264) | video/mp4 | Excelente (todos los navegadores) |
| WebM | video/webm | Bueno (excepto en Safari) |
| OGG | video/ogg | Limitado |

### Mejores prácticas:
- Siempre proporciona múltiples formatos para máxima compatibilidad
- Usa el atributo `poster` en videos para una mejor experiencia de usuario
- Evita `autoplay` con sonido (los navegadores modernos lo bloquean)
- Optimiza el tamaño de los archivos para mejorar el tiempo de carga
- Incluye texto alternativo para usuarios con discapacidad

## 🏆 Reto Adicional: Galería Multimedia de Viajes

¡Felicidades por completar los ejercicios de multimedia y divs! Aquí tienes un reto adicional para que practiques aún más:

### 📚 Descripción del Reto
Crea una página web que simule una galería multimedia de viajes. Debe incluir:

- Un diseño organizado con divs semánticos
- Sección de audio con al menos 2 pistas de sonido de diferentes ubicaciones
- Sección de video con al menos 1 video (usa el atributo `poster`)
- Uso de múltiples formatos para compatibilidad (MP3/OGG para audio, MP4/WebM para video)
- Una galería de imágenes relacionadas con los videos y audios
- Navegación interna para moverse entre secciones

### 📌 Ejemplo de Cómo Debería Verse

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galería Multimedia de Viajes</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        
        header {
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 20px 0;
        }
        
        nav ul {
            list-style-type: none;
            padding: 0;
            background-color: #34495e;
            margin: 0;
            display: flex;
            justify-content: center;
        }
        
        nav ul li {
            margin: 0 20px;
        }
        
        nav ul li a {
            color: white;
            text-decoration: none;
            padding: 15px;
            display: block;
        }
        
        nav ul li a:hover {
            background-color: #3498db;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        section {
            margin-bottom: 50px;
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0,0,0,0.1);
        }
        
        .gallery {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
        }
        
        .gallery img {
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        
        footer {
            background-color: #2c3e50;
            color: white;
            text-align: center;
            padding: 20px 0;
            margin-top: 50px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Galería Multimedia de Viajes</h1>
        <p>Explora el mundo a través de sonidos e imágenes</p>
    </header>
    
    <nav>
        <ul>
            <li><a href="#selva">Selva</a></li>
            <li><a href="#montanas">Montañas</a></li>
            <li><a href="#playas">Playas</a></li>
            <li><a href="#ciudades">Ciudades</a></li>
        </ul>
    </nav>
    
    <div class="container">
        <section id="selva">
            <h2>Selva Amazónica</h2>
            
            <div class="audio-container">
                <h3>Sonidos de la Selva</h3>
                <p>Escucha los sonidos de la selva tropical en su estado natural.</p>
                <audio controls style="width: 100%; margin-top: 10px;">
                    <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
                    <source src="audio/selva.ogg" type="audio/ogg">
                    Tu navegador no soporta el elemento de audio.
                </audio>
            </div>
            
            <div class="video-container">
                <h3>Video de la Selva</h3>
                <p>Vive la experiencia de la selva amazónica.</p>
                <video controls poster="https://via.placeholder.com/800x450?text=Selva+Amazónica" style="width: 100%; margin-top: 10px;">
                    <source src="https://storage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" type="video/mp4">
                    <source src="video/selva.webm" type="video/webm">
                    Tu navegador no soporta el elemento de video.
                </video>
            </div>
            
            <div class="gallery">
                <img src="https://via.placeholder.com/250x150?text=Flora" alt="Flora de la selva">
                <img src="https://via.placeholder.com/250x150?text=Fauna" alt="Fauna de la selva">
                <img src="https://via.placeholder.com/250x150?text=Río" alt="Río en la selva">
                <img src="https://via.placeholder.com/250x150?text=Cascada" alt="Cascada en la selva">
            </div>
        </section>
        
        <section id="montanas">
            <h2>Montañas</h2>
            <!-- Contenido similar para montañas -->
        </section>
        
        <section id="playas">
            <h2>Playas</h2>
            <!-- Contenido similar para playas -->
        </section>
        
        <section id="ciudades">
            <h2>Ciudades</h2>
            <!-- Contenido similar para ciudades -->
        </section>
    </div>
    
    <footer>
        <p>&copy; 2024 Galería Multimedia de Viajes. Todos los derechos reservados.</p>
    </footer>
</body>
</html>
```

### 💡 Consejos para Completar el Reto
- Usa enlaces de placeholder para audio y video si no tienes archivos propios
- Organiza tu código con comentarios para cada sección
- Aplica estilos consistentes usando clases
- Usa el atributo `poster` en tus videos para una mejor experiencia
- Implementa navegación interna con anclas (`#id`)
- Prueba tu página en diferentes navegadores para verificar compatibilidad

### 📅 Entrega
¡Tómate el tiempo que necesites!.

¿Te animas a aceptar el reto? ¡Tu galería multimedia podría ser el inicio de tu portfolio como desarrollador web! 🌍🎧🎥
