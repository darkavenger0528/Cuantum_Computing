# Cuantum_Computing

Página web educativa de introducción a la **Computación Cuántica**, desarrollada como
proyecto para la Universidad EAN. Explica desde los conceptos básicos (qubit,
superposición, entrelazamiento) hasta la **Transformada Cuántica de Fourier (QFT)**
y sus fórmulas asociadas.

## Estructura del proyecto

```
Cuantum_Computing/
├── index.html          # Introducción
├── conceptos.html       # Conceptos Fundamentales
├── qft.html              # Transformada Cuántica de Fourier
├── comparativa.html     # Comparativa: clásico vs cuántico
├── formulas.html        # Fórmulas (Regla de Born, estado de n qubits, etc.)
├── contacto.html         # Formulario de contacto
├── wireframe.svg         # Wireframe (escritorio / tablet / celular)
├── css/
│   ├── style.css              # Estilos propios + @media queries (responsive)
│   └── fontawesome.min.css    # Font Awesome (cargado localmente)
├── fonts/                  # Archivos .woff2 de Font Awesome (fuentes locales)
├── img/                    # Imágenes del sitio
└── mp3/                    # Audios
```

## Tecnologías

- **HTML5** — 6 páginas independientes, cada una con su propia sección.
- **CSS3** — Flexbox para el layout (menú, barra lateral y contenido).
- **Diseño responsivo** — `@media` queries con 3 puntos de quiebre:
  - Escritorio: > 900px
  - Tablet: 601px – 900px
  - Celular: ≤ 600px
- **Font Awesome 7** — iconos del menú, cargados desde una carpeta local (`fonts/`),
  sin depender de un CDN.

## Wireframe

El archivo `wireframe.svg` muestra la estructura planeada de la página en sus tres
versiones (escritorio, tablet y celular): menú de navegación, barra lateral de
"Datos Clave" y área de contenido.

## Autor

Justin Thomas Moreno Solano — Universidad EAN
