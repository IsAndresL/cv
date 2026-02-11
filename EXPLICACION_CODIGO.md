# Guía de Estudio: Código del Portafolio "Bento Grid"

Este documento desglosa y explica paso a paso el código fuente de tu página de presentación (Hoja de Vida), tanto la estructura HTML como los estilos CSS. El diseño utiliza una técnica moderna llamada **"Bento Grid"** (inspirada en las cajas bento japonesas), que organiza el contenido en módulos o trajetas cuadrangulares.

---

## 1. Estructura HTML (`index.html`)

El HTML define el _esqueleto_ y el _significado_ del contenido.

### 1.1. Configuración Inicial

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- Vinculación de estilos y fuentes -->
    <link rel="stylesheet" href="styles.css" />
    ...
  </head>
</html>
```

- `lang="es"`: Importante para que los navegadores y lectores de pantalla sepan que el contenido está en español.
- `viewport`: Esta etiqueta es **crucial para el diseño responsivo** (móviles). Asegura que el sitio se escale correctamente en pantallas pequeñas.

### 1.2. El Contenedor Principal (`main`)

```html
<main class="contenedor-principal">
  <!-- Aquí van todas las tarjetas -->
</main>
```

- Usamos la etiqueta semántica `<main>` para indicar que este es el contenido principal de la página.
- La clase `.contenedor-principal` será la encargada de activar la "Rejilla" (Grid) en CSS.

### 1.3. Las Tarjetas (`header`, `section`, `article`)

El diseño se basa en tarjetas independientes. Observa cómo usamos clases genéricas y específicas:

```html
<section id="perfil" class="seccion-tarjeta tarjeta-acerca"></section>
```

- `.seccion-tarjeta`: Esta es una **clase base**. Todas las tarjetas la tienen. Define los estilos comunes (borde, fondo, esquinas redondeadas).
- `.tarjeta-acerca` (o `.tarjeta-perfil`, etc.): Son **clases específicas**. Se usan para darle tamaños o colores únicos a esa tarjeta en particular.

---

## 2. Estilos CSS (`styles.css`)

El CSS define la _apariencia_ y la _distribución_ visual.

### 2.1. Variables CSS (`:root`)

```css
:root {
  --bg-color: #0a0a0a; /* Fondo casi negro */
  --tile-bg: #171717; /* Fondo de las tarjetas (gris oscuro) */
  --accent: #6366f1; /* Color de acento (índigo) */
  --gap: 1.5rem; /* Espacio entre tarjetas */
  --radius: 24px; /* Redondez de las esquinas */
}
```

- **¿Por qué usar variables?** Si mañana quieres cambiar el color azul por rojo, solo cambias `--accent` aquí y se actualiza en toda la página. Es mucho más mantenible.

### 2.2. Diseño de Cuadrícula (The Bento Grid)

Esta es la parte más importante del diseño:

```css
.contenedor-principal {
  display: grid;
  /* La Magia del Responsive: */
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: var(--gap);
  max-width: 1400px;
}
```

- `display: grid`: Activa el modo cuadrícula.
- `repeat(auto-fit, minmax(300px, 1fr))`: Esta línea es muy poderosa. Le dice al navegador: "Crea tantas columnas como quepan. Cada columna debe medir **mínimo 300px**. Si sobra espacio, repártelo equitativamente (`1fr`)". Esto hace que el diseño se adapte automáticamente sin necesidad de muchas "media queries".

### 2.3. Estilo de las Tarjetas

```css
.seccion-tarjeta {
  background-color: var(--tile-bg);
  border-radius: var(--radius);
  border: 1px solid var(--border);
  transition:
    transform 0.3s ease,
    border-color 0.3s ease;
}

.seccion-tarjeta:hover {
  transform: translateY(-5px); /* Mueve la tarjeta un poco hacia arriba */
  border-color: var(--accent); /* Cambia el borde al color de acento */
}
```

- Aquí definimos el aspecto de "vidrio" oscuro y sutil.
- `transition`: Suaviza los cambios (animaciones) cuando pasas el mouse por encima (`:hover`).

### 2.4. Texto con Gradiente (El nombre)

```css
.texto-encabezado h1 {
  background: linear-gradient(90deg, #fff, #a1a1a1);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
}
```

- Esto hace que el texto "Andres Luna" no sea de un color sólido, sino que tenga un degradado de blanco a gris.
- `background-clip: text`: Recorta el fondo (el degradado) para que solo se vea donde hay letras.
- `text-fill-color: transparent`: Hace las letras transparentes para dejar ver el fondo detrás.

### 2.5. Grid Irregular (Haciendo algunas tarjetas más grandes)

Por defecto, todas las tarjetas ocupan 1 columna. Pero queremos que el perfil o los proyectos ocupen 2 columnas si hay espacio:

```css
@media (min-width: 768px) {
  .tarjeta-perfil {
    grid-column: span 2; /* Ocupa 2 espacios de ancho */
  }
}
```

- Usamos `@media` para aplicar esto solo en pantallas medianas o grandes (tablets/PC). En celulares, seguirán ocupando 1 sola columna para que se vean bien verticalmente.

---

## Resumen de Conceptos Clave

1.  **Semantic HTML**: Usar etiquetas con significado (`header`, `main`) ayuda al SEO y accesibilidad.
2.  **CSS Grid**: Es la mejor herramienta para diseños bidimensionales (filas y columnas) como este estilo Bento.
3.  **Variables CSS**: Facilitan cambiar temas de colores rápidamente.
4.  **Mobile First**: El diseño base funciona en móviles (columnas autoadaptables), y luego usamos media queries (`@media`) para mejorarlo en pantallas grandes.
