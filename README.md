# Cuantum_Computing

Pagina web educativa de introduccion a la **Computacion Cuantica**, desarrollada como
proyecto para la Universidad EAN. Explica desde los conceptos basicos (qubit,
superposicion, entrelazamiento) hasta la **Transformada Cuantica de Fourier (QFT)**
y sus formulas asociadas.

## Estructura del proyecto

```
Cuantum_Computing/
├── html/
│   ├── index.html            # Introduccion
│   ├── conceptos.html         # Conceptos Fundamentales
│   ├── qft.html                # Transformada Cuantica de Fourier
│   ├── comparativa.html       # Comparativa: clasico vs cuantico
│   ├── procesadores.html      # Procesadores cuanticos (datos via API REST)
│   ├── formulas.html          # Formulas (Regla de Born, estado de n qubits, etc.)
│   └── contacto.html           # Formulario de contacto
├── bootstrap-5.3.8-dist/      # Bootstrap 5.3.8 completo, tal como se descarga
├── fontawesome-free-7.3.1-web/ # Font Awesome 7 completo, tal como se descarga
├── css/
│   └── style.css               # Estilos propios + @media queries (responsive)
├── fonts/                    # Fuentes propias del proyecto (si se agregan)
├── img/                      # Imagenes del sitio
├── mp3/                      # Audios
├── wireframe.svg              # Wireframe (escritorio / tablet / celular)
└── README.md
```

## Tecnologias

- **HTML5** - 6 paginas independientes, cada una con su propia seccion.
- **Bootstrap 5.3.8** (carpeta completa descargada, sin CDN) - usado para el
  `navbar` responsivo con boton hamburguesa (`navbar-toggler` +
  `bootstrap.bundle.min.js`) y el sistema de grillas (`container-fluid`, `row`,
  `col-md-3` / `col-md-9`) que organiza la barra lateral y el contenido.
- **Font Awesome 7** (carpeta completa descargada, sin CDN) - iconos del menu
  de navegacion, cargados desde `fontawesome-free-7.3.1-web/css/all.min.css`.
- **CSS3 propio** (`css/style.css`) - colores, tipografia del tema y
  **`@media` queries** para ajustes finos en tablet (<=900px) y celular
  (<=600px) que complementan el comportamiento responsivo de Bootstrap.
- **API REST (Retool API Generator)** - la pagina `procesadores.html`
  consume, mediante `fetch()` en JavaScript puro, un dataset simulado de
  procesadores cuanticos (`https://retoolapi.dev/pnc4c1/data`). Las columnas
  de la tabla se generan dinamicamente a partir de las claves del JSON
  recibido, por lo que la pagina no rompe si el dataset cambia.

## Diseno responsivo

- **Escritorio** (> 900px): barra lateral y contenido lado a lado (grid de
  Bootstrap), menu horizontal completo.
- **Tablet** (<= 900px): se reduce el padding del contenido y del menu.
- **Celular** (<= 768px, segun el grid de Bootstrap): la barra lateral y el
  contenido se apilan verticalmente, y el menu se colapsa en un boton
  hamburguesa (componente `navbar` de Bootstrap).

## Wireframe

El archivo `wireframe.svg` muestra la estructura planeada de la pagina en sus
tres versiones (escritorio, tablet y celular): menu de navegacion, barra
lateral de "Datos Clave" y area de contenido.

## Autor

Justin Thomas Moreno Solano - Universidad EAN
