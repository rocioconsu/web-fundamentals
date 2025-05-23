# Guía pedagógica: Crear una Masonry Grid totalmente responsive con CSS3

## Introducción

Una **masonry grid** es un diseño visual en el que los elementos se organizan como ladrillos en una pared, apilados verticalmente sin una altura uniforme. Es muy usada en sitios como Pinterest para mostrar contenidos visuales de forma atractiva y flexible.

Esta guía está pensada para que los estudiantes puedan:

- Comprender qué es una _masonry grid_.
- Aplicar dos técnicas modernas usando solo **CSS3** (sin JavaScript).
- Usar buenas prácticas para que el diseño sea 100% responsive.

Incluye:

- Explicaciones teóricas.
- HTML y CSS separados.
- Ejemplo visual con imágenes reales (Unsplash).
- Dos técnicas: `column-count` y `grid-auto-flow: dense`.
- Versiones completas en archivos `.html` para práctica.

---

## Técnica 1: `column-count` (multicolumnas)

### HTML completo (masonry-column.html)

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Galería Masonry con Columnas</title>
    <style>
      body {
        font-family: sans-serif;
        background: #f4f4f4;
        padding: 2rem;
      }

      h1 {
        text-align: center;
        margin-bottom: 2rem;
      }

      .masonry-column {
        column-count: 3;
        column-gap: 1rem;
      }

      .masonry-column img {
        width: 100%;
        margin-bottom: 1rem;
        border-radius: 6px;
        display: block;
        break-inside: avoid;
      }

      @media (max-width: 768px) {
        .masonry-column {
          column-count: 2;
        }
      }

      @media (max-width: 480px) {
        .masonry-column {
          column-count: 1;
        }
      }
    </style>
  </head>
  <body>
    <h1>Galería Masonry (Columnas)</h1>
    <section class="masonry-column">
      <img
        src="https://images.unsplash.com/photo-1517694712202-14dd9538aa97"
        alt="imagen 1"
      />
      <img
        src="https://images.unsplash.com/photo-1526170375885-4d8ecf77b99f"
        alt="imagen 2"
      />
      <img
        src="https://images.unsplash.com/photo-1519985176271-adb1088fa94c"
        alt="imagen 3"
      />
      <img
        src="https://images.unsplash.com/photo-1506744038136-46273834b3fb"
        alt="imagen 4"
      />
      <img
        src="https://images.unsplash.com/photo-1504198458649-3128b932f49b"
        alt="imagen 5"
      />
    </section>
  </body>
</html>
```

### Ventajas

- Muy fácil de aplicar.
- No requiere cálculos.
- Totalmente responsive.

### Limitaciones

- El orden visual es por columna (no fila).
- Espaciado vertical puede ser desigual.

---

## Técnica 2: `CSS Grid` con `grid-auto-flow: dense`

### HTML completo (masonry-grid.html)

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Galería Masonry con CSS Grid</title>
    <style>
      /* Reset CSS */
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }
      html,
      body {
        background: linear-gradient(45deg, #190f2c, #200b30);
        padding: 15px;
      }

      img {
        max-width: 100%;
        height: auto;
        vertical-align: middle;
        display: inline-block;
      }

      /* Main CSS */
      .grid-wrapper > div {
        display: flex;
        justify-content: center;
        align-items: center;
      }
      .grid-wrapper > div > img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        border-radius: 5px;
      }
      h1 {
        color: white;
      }
      .grid-wrapper {
        display: grid;
        grid-gap: 10px;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-auto-rows: 200px;
        grid-auto-flow: dense;
      }
      .grid-wrapper .wide {
        grid-column: span 2;
      }
      .grid-wrapper .tall {
        grid-row: span 2;
      }
      .grid-wrapper .big {
        grid-column: span 2;
        grid-row: span 2;
      }
    </style>
  </head>
  <body>
    <h1>Galería Masonry (CSS Grid)</h1>
    <div class="grid-wrapper">
      <div>
        <img
          src="https://images.unsplash.com/photo-1541845157-a6d2d100c931?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1588282322673-c31965a75c3e?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1351&amp;q=80"
          alt=""
        />
      </div>
      <div class="tall">
        <img
          src="https://images.unsplash.com/photo-1588117472013-59bb13edafec?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=500&amp;q=60"
          alt=""
        />
      </div>
      <div class="wide">
        <img
          src="https://images.unsplash.com/photo-1587588354456-ae376af71a25?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1350&q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src=" https://images.unsplash.com/photo-1558980663-3685c1d673c4?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1000&amp;q=60"
          alt=""
        />
      </div>
      <div class="tall">
        <img
          src="https://images.unsplash.com/photo-1588499756884-d72584d84df5?ixlib=rb-1.2.1&amp;auto=format&amp;fit=crop&amp;w=2134&amp;q=80"
          alt=""
        />
      </div>
      <div class="big">
        <img
          src="https://images.unsplash.com/photo-1588492885706-b8917f06df77?ixlib=rb-1.2.1&amp;auto=format&amp;fit=crop&amp;w=1951&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1588247866001-68fa8c438dd7?ixlib=rb-1.2.1&amp;auto=format&amp;fit=crop&amp;w=564&amp;q=80"
          alt=""
        />
      </div>
      <div class="wide">
        <img
          src="https://images.unsplash.com/photo-1586521995568-39abaa0c2311?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
      <div class="big">
        <img
          src="https://images.unsplash.com/photo-1572914857229-37bf6ee8101c?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1951&amp;q=80"
          alt=""
        />
      </div>
      <div class="tall">
        <img
          src="https://images.unsplash.com/photo-1588453862014-cd1a9ad06a12?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=634&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1588414734732-660b07304ddb?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=675&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1588224575346-501f5880ef29?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=700&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1574798834926-b39501d8eda2?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=800&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1547234935-80c7145ec969?ixlib=rb-1.2.1&amp;auto=format&amp;fit=crop&amp;w=1353&amp;q=80"
          alt=""
        />
      </div>
      <div class="wide">
        <img
          src="https://images.unsplash.com/photo-1588263823647-ce3546d42bfe?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=675&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1587732608058-5ccfedd3ea63?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1587897773780-fe72528d5081?ixlib=rb-1.2.1&amp;auto=format&amp;fit=crop&amp;w=1489&amp;q=80"
          alt=""
        />
      </div>
      <div class="wide">
        <img
          src="https://images.unsplash.com/photo-1588083949404-c4f1ed1323b3?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1489&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1587572236558-a3751c6d42c0?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
      <div class="wide">
        <img
          src="https://images.unsplash.com/photo-1583542225715-473a32c9b0ef?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
      <div class="big">
        <img
          src="https://images.unsplash.com/photo-1527928159272-7d012024eb74?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1553984840-b8cbc34f5215?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1433446787703-42d5bf446876?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1351&amp;q=80"
          alt=""
        />
      </div>
      <div class="big">
        <img
          src="https://images.unsplash.com/photo-1541187714594-731deadcd16a?ixlib=rb-1.2.1&amp;auto=format&amp;fit=crop&amp;w=700&amp;q=80"
          alt=""
        />
      </div>
      <div class="tall">
        <img
          src="https://images.unsplash.com/photo-1540979388789-6cee28a1cdc9?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=634&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1421930866250-aa0594cea05c?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1355&amp;q=80"
          alt=""
        />
      </div>
      <div>
        <img
          src="https://images.unsplash.com/photo-1493306454986-c8877a09cbeb?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1381&amp;q=80"
          alt=""
        />
      </div>
      <div class="wide">
        <img
          src="https://images.unsplash.com/photo-1536466528142-f752ae7bdd0c?ixlib=rb-1.2.1&amp;ixid=eyJhcHBfaWQiOjEyMDd9&amp;auto=format&amp;fit=crop&amp;w=1350&amp;q=80"
          alt=""
        />
      </div>
    </div>
  </body>
</html>
```

### Ventajas

- Control total de ubicación y flujo.
- `grid-auto-flow: dense` rellena huecos inteligentemente.
- Flexible y fácil de extender.

### Limitaciones

- Si se desea calcular `span` según altura real, se requiere JS (no cubierto aquí).

### Recursos

- [CSS Grid Layout #1: Responsive Masonry](https://codepen.io/iamsaief/pen/jObaoKo)

---

## Conclusiones pedagógicas

- Ambas técnicas permiten resolver el problema de diseño sin necesidad de librerías externas.
- La versión multicolumna es la más fácil para comenzar.
- La versión con CSS Grid y `dense` permite más control y efectos visuales atractivos.

---

## Propuesta de actividad final para el aula

1. Crear una galería con 10 imágenes usando la técnica de `column-count`.
2. Duplicar el proyecto y transformarlo usando `grid-auto-flow: dense`.
3. Agregar una versión con `grid-row: span x` para ajustar manualmente algunas alturas.
4. Compartir el proyecto en GitHub Pages.

---

¡Ahora sí, que empiece la magia del CSS! Sorpréndete viendo cómo tus cuadrículas cobran vida con solo unas líneas de código.
