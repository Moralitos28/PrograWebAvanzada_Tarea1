# Tarea 1 · Interfaces web adaptables con HTML y CSS

## Identificación

| Campo | Información |
| --- | --- |
| Estudiante | Carlos Israel Morales Rojas |
| Universidad | Universidad CENFOTEC, Escuela de Software |
| Curso | SOFT-12 · Programación web avanzada |
| Sección | SCV2 |
| Periodo | III cuatrimestre de 2026 |
| Docente | Álvaro Cordero Peña |
| Actividad | Tarea 1: Construcción de interfaces web adaptables con HTML y CSS |
| Modalidad | Individual |
| Fecha de entrega | Domingo 20 de setiembre de 2026, 11:55 p. m. |
| Valor | 10 % · 64 puntos, distribuidos en 16 criterios de 4 puntos |
| Repositorio | [PrograWebAvanzada_Tarea1](https://github.com/Moralitos28/PrograWebAvanzada_Tarea1) |

## Descripción del proyecto

Dos interfaces independientes desarrolladas con HTML5 y CSS3 para organizar información según su importancia y el espacio disponible. Cada caso tiene su propio documento, hoja de estilos y recursos locales. No se utiliza JavaScript, frameworks CSS, paquetes de ejecución, backend ni base de datos; tampoco se utilizan tablas HTML para maquetar las interfaces.

Ambos casos presentan contenido académico estático, desarrollado exclusivamente con HTML5 y CSS3 conforme al alcance de la actividad.

### Caso 1: centro de control de una expedición científica

[Ver HTML del caso 1](caso1/index.html) · [Ver CSS](caso1/css/estilos.css)

La expedición Anastacio Alfaro Bosque Nuboso, edición 2026, se ubica en la Estación Biológica Monteverde. El panel reúne información operativa para que la coordinación pueda consultar misiones, equipos y alertas desde un mismo documento.

| Sección | Contenido implementado |
| --- | --- |
| Encabezado | Nombre, ubicación, día 4 de 7 y estado general de la operación. |
| Navegación | Resumen, Misiones, Equipos, Alertas y Agenda, mediante anclas internas. |
| Resumen | 18 investigadores activos, 2 misiones en progreso, 1 completada y 4 alertas pendientes. |
| Misiones | 5 tarjetas con nombre, equipo, ubicación, horario, prioridad y estado. |
| Estados | En progreso, pendiente, suspendida y completada; incluyen texto e iconos. |
| Equipos | Biología, Hidrología, Meteorología y Geología; integrantes, misión, estado y próxima actividad. |
| Alertas | 4 avisos con niveles crítico, alto, medio e informativo. |
| Agenda | 5 actividades ordenadas por hora, con actividad y equipo relacionado. |

### Caso 2: panel público de información de un festival

[Ver HTML del caso 2](caso2/index.html) · [Ver CSS](caso2/css/estilos.css)

Transitarte 2027 representa un festival cultural en el centro de San José. La interfaz facilita la consulta de actividades actuales, próximas presentaciones, escenarios, cambios y servicios, comenzando por una distribución para teléfono.

| Sección | Contenido implementado |
| --- | --- |
| Encabezado | Nombre, sábado 10 de abril de 2027, centro de San José, entrada libre y horario de 11:00 a. m. a 9:00 p. m. |
| Navegación | Ahora, Programación, Escenarios, Servicios e Información. |
| Ahora | 3 actividades con nombre, tipo, escenario, horario y estado «En este momento». |
| Próximas actividades | 6 entradas con hora, nombre, escenario y categoría; utilizan `time` con `datetime`. |
| Escenarios | 5 tarjetas: Parque Nacional, Parque España, Parque Morazán, Teatro Nacional y Paseo de las Damas. |
| Tipos de espacio | Escenario Central, Zona Familiar, Zona Cultural y Teatro. |
| Cambios importantes | Traslado, actualización de horario, cambio de sala y cancelación. |
| Servicios | Alimentación, baños, primeros auxilios, hidratación, información, accesibilidad y estacionamiento. |

## Estructura del repositorio

```text
Tarea1/
├── README.md
├── caso1/
│   ├── index.html
│   ├── css/
│   │   └── estilos.css
│   └── img/                 # Fotografía de Monteverde e iconos SVG
└── caso2/
    ├── index.html
    ├── css/
    │   └── estilos.css
    └── img/                 # Encabezado y fotografías de los escenarios
```

Los iconos del caso 1 se almacenan como archivos SVG. Los del caso 2 están incorporados en el CSS mediante URI `data:image/svg+xml` y máscaras. Las fuentes son del sistema; no hay cargas de fuentes ni bibliotecas desde CDN.

## Cómo abrir los casos

### Apertura directa

1. Descargar o clonar el repositorio conservando la estructura de carpetas.
2. Abrir `caso1/index.html` en un navegador para consultar la expedición.
3. Abrir `caso2/index.html` en un navegador para consultar el festival.
4. Utilizar el menú de cada caso para desplazarse a sus secciones.

Cada caso es independiente y sus rutas CSS e imágenes son relativas. Es necesario conservar sus carpetas `css/` e `img/`.

## Decisiones de diseño

### 1. Etiquetas semánticas

`header` reúne la identidad y contexto; `nav` contiene enlaces internos; `main` delimita el contenido principal; `section` agrupa los temas; `article` representa tarjetas comprensibles como unidades; `aside` agrupa alertas o cambios complementarios; y `footer` presenta información académica. Los `div` se reservan para agrupaciones visuales, como el encabezado fotográfico o contenedores de tarjetas.

La agenda del caso 1 utiliza una lista ordenada para expresar secuencia. La navegación y los servicios utilizan listas; las próximas actividades del caso 2 incorporan `time` para representar horas con una fecha interpretable por software.

### 2. Jerarquía de encabezados

Cada documento tiene un solo `h1`, correspondiente al nombre de la expedición o festival. Los `h2` identifican las secciones y los `h3` nombran indicadores, misiones, equipos, actividades, escenarios o avisos. El tamaño se define con CSS sin cambiar el nivel semántico por razones de apariencia.

### 3. Accesibilidad básica

Ambos documentos declaran `lang="es"`, codificación UTF-8 y configuración de viewport. Las fotografías tienen textos alternativos descriptivos. Los iconos decorativos usan `alt=""` o `aria-hidden="true"` cuando el texto contiguo ya comunica su significado. La navegación tiene `aria-label`, enlaces reales y un estilo de foco visible con `:focus-visible`; el caso 2 también vincula secciones con sus títulos mediante `aria-labelledby`.

Los estados y niveles incluyen texto e indicadores visuales, de modo que su significado no depende exclusivamente del color.

### 4. Modelo de caja

Se aplica `box-sizing: border-box` a todos los elementos y pseudoelementos, incluyendo el relleno y borde en sus dimensiones declaradas. Las tarjetas combinan `padding` interior, bordes y radios; `gap` separa elementos de Flexbox y Grid. El caso 1 elimina márgenes y rellenos iniciales globalmente; el caso 2 elimina el margen del cuerpo y ajusta componentes concretos.

El ancho principal se limita a `75rem` en el caso 1 y, en escritorio, en el caso 2. Las imágenes se ajustan al contenedor. El caso 1 utiliza `minmax(0, 1fr)` en las cuadrículas internas para permitir que las columnas se reduzcan; el caso 2 utiliza `minmax(13rem, 1fr)` para distribuir escenarios en escritorio.

### 5. Posicionamiento y superposición

| Ubicación | Propiedad | Finalidad |
| --- | --- | --- |
| Encabezado fotográfico, ambos casos | `.hero` con `relative`; imagen y `::after` con `absolute` e `inset: 0` | Superponer fotografía y degradado dentro de un contenedor definido. |
| Texto del encabezado, ambos casos | `.hero-content` con `relative` y `z-index: 1` | Mantener el texto por encima del fondo. |
| Navegación, ambos casos | `sticky`, `top: 0`, `z-index: 10` | Aplicar posicionamiento adherente al borde superior dentro de los límites del encabezado y controlar su superposición mediante `z-index`. |
| Indicadores, caso 1 | Tarjeta con `relative`; cifra con `absolute` e `inset: 0`; título con `z-index: 1` | Centrar la cifra y controlar la superposición con el título. La tarjeta reserva una altura mínima de `10rem`. |
| Etiqueta «En este momento», caso 2 | `.actual` con `relative`; `.estado` con `absolute` | Situar la etiqueta en la zona inferior de la tarjeta. Se reserva espacio con `padding-bottom: 3rem`. |

Los demás elementos conservan el posicionamiento normal (`static`) cuando no se declara otra regla. El layout principal depende de Grid y Flexbox.

### 6. Cascada y especificidad

Las hojas comienzan por variables y reglas base, continúan con componentes y terminan con media queries. Las reglas posteriores prevalecen cuando tienen la misma especificidad y afectan a la misma propiedad. Por ejemplo, el `main` del caso 1 pasa a dos columnas desde `48rem` y vuelve a una columna principal desde `64rem`, mientras cambian sus cuadrículas internas.

En el caso 1, selectores como `#alerts .alert--critical` prevalecen sobre reglas generales de `article` por su mayor especificidad. En el caso 2 predominan clases reutilizables, como `.seccion`, `.aviso` y sus variantes. No se utiliza `!important`.

### 7. Flexbox

En ambos casos, `nav ul` usa Flexbox con `flex-wrap`, `justify-content` y `gap`, permitiendo reorganizar enlaces en varias líneas. En el caso 1 también alinea los títulos y prioridades de misiones y agrupa iconos con estados.

En el caso 2 alinea hora y descripción de próximas actividades, icono y texto de avisos, y los servicios en filas que se envuelven. Las tarjetas de escenarios usan `flex-direction: column`; su etiqueta de tipo se coloca al final mediante `order` y margen automático. Flexbox resuelve estas alineaciones en una dirección.

### 8. CSS Grid

El caso 1 utiliza Grid en `main`, resumen, misiones, equipos y alertas. El título de cada grupo ocupa todo el ancho mediante `grid-column: 1 / -1`. Las cuadrículas interiores permiten comparar tarjetas.

El caso 2 usa Grid para las actividades actuales, próximas actividades y escenarios. En escritorio, `main` se transforma en una cuadrícula de dos columnas y escenarios y servicios abarcan ambas. Los escenarios emplean `repeat(auto-fit, minmax(13rem, 1fr))`, ajustando el número de columnas al espacio disponible.

### 9. Adaptación, media queries y breakpoints

El CSS base corresponde a teléfono y las ampliaciones utilizan exclusivamente media queries de tipo `min-width`.

| Caso | Ancho | Distribución implementada |
| --- | --- | --- |
| 1 | Menor que `48rem` | Secciones y tarjetas principalmente en una columna; menú con envoltura. |
| 1 | Desde `48rem` | `main` declara dos columnas, aunque sus secciones abarcan ambas; resumen con 4 indicadores por fila, misiones y equipos con 2 tarjetas por fila. |
| 1 | Desde `64rem` | `main` vuelve a una columna; resumen conserva 4 columnas, misiones pasan a 3 y equipos a 4. Alertas y agenda permanecen apiladas. |
| 2 | Menor que `601px` | Secciones y tarjetas en una columna; «Ahora» aparece primero. |
| 2 | Desde `601px` | Actividades actuales y escenarios pasan a 2 columnas. |
| 2 | Desde `1024px` | `main` usa 2 columnas; «Ahora» tiene 3 tarjetas por fila, escenarios se distribuyen automáticamente y servicios ocupan el ancho completo. |

Los límites del caso 1 equivalen aproximadamente a 768 y 1024 píxeles con un tamaño inicial de fuente de 16 píxeles, y permiten aumentar la densidad de tarjetas. El caso 2 sigue las referencias orientativas de la consigna: 601 y 1024 píxeles; a exactamente 1024 píxeles ya se aplica la distribución de escritorio.

En el festival, el orden del documento es Ahora, Próximas actividades, Escenarios, Cambios importantes y Servicios. La reorganización de escritorio se logra con columnas y secciones que abarcan todo el ancho, sin alterar ese orden semántico. En la expedición, las cuadrículas internas aumentan progresivamente la cantidad de indicadores, misiones y equipos visibles por fila.

### 10. Unidades relativas

Se emplean `rem` para tipografía, espaciado y dimensiones; `%` para ajustar imágenes y contenedores; `fr` para repartir columnas; y `vw` dentro de `clamp()` para escalar los encabezados con límites mínimo y máximo. Los píxeles se reservan, entre otros usos, para bordes y los breakpoints del caso 2. No se depende exclusivamente de dimensiones fijas.

### 11. Variables CSS y propuesta visual

Ambas hojas definen variables en `:root` para colores principales, fondo, texto, espaciado, bordes y radios. Modificar una variable permite actualizar los componentes que la reutilizan.

El caso 1 combina verde bosque, fondos cálidos y acentos dorados para el contexto científico y natural; sus variables incluyen una escala de espaciados y colores de criticidad. El caso 2 combina azul, cian y superficies claras, con colores específicos para los avisos. Comparten recursos de navegación y encabezado, pero presentan agrupaciones y contenidos diferentes: seguimiento operativo frente a consulta de programación cultural.

### 12. Imágenes adaptables

Las fotografías de encabezado utilizan `width: 100%`, `height: 100%` y `object-fit: cover`, llenando el área con posible recorte. En el festival, las imágenes de escenarios usan `aspect-ratio: 4 / 3` y `object-fit: contain`, conservando la imagen completa dentro del marco. Los iconos usan dimensiones relativas.

## Resumen de commits

La tabla presenta el historial de desarrollo en orden cronológico, con fecha, identificador, mensaje original, caso asociado y descripción del cambio.

| # | Fecha | Hash | Mensaje | Caso | Cambio principal |
| --- | --- | --- | --- | --- | --- |
| 1 | 2026-09-19 | `9546296` | Crear esqueleto inicial del repositorio | Ambos | Crea README y archivos iniciales de HTML y CSS para ambos casos. |
| 2 | 2026-09-20 | `2b522f0` | Esqueleto del caso 1 | Caso 1 | Agrega la estructura y contenido inicial del panel científico. |
| 3 | 2026-09-20 | `9ea9a57` | refractor del caso 1 | Caso 1 | Incorpora estilos base, layout adaptable y ajustes de HTML. |
| 4 | 2026-09-20 | `68f8c5e` | anadir imagen de fondo | Caso 1 | Agrega fotografía de Monteverde y composición del encabezado. |
| 5 | 2026-09-20 | `6a242f0` | correcion de render en tabletas y mobiles | Caso 1 | Ajusta cuadrículas y distribución de alertas para tamaños intermedios. |
| 6 | 2026-09-20 | `414e5da` | alertas con colores e icono para criticidad | Caso 1 | Diferencia niveles de alerta con colores e icono de criticidad. |
| 7 | 2026-09-20 | `072058a` | aplicado concepto de prioridad y estado para las misiones | Caso 1 | Incorpora etiquetas de prioridad y estados de las misiones. |
| 8 | 2026-09-20 | `fca26ca` | mejoras en el ribbon de menu | Caso 1 | Ajusta distribución y presentación de enlaces del menú. |
| 9 | 2026-09-20 | `f31aada` | anadir iconos untracked | Caso 1 | Versiona ocho iconos SVG de prioridad, estados y alerta crítica. |
| 10 | 2026-09-20 | `e988752` | Usando de base caso 1 esqueleto para el caso 2 usando el modelo del pasado transitarte | Caso 2 | Crea el panel del festival, estilos y fotografías iniciales. |
| 11 | 2026-09-20 | `2e62594` | anadir imagenes a las tarjetas | Caso 2 | Integra fotografías en las tarjetas de escenarios. |
| 12 | 2026-09-20 | `89ebbd8` | anadir labels segun consigna y teatro para encajar en el esquema | Caso 2 | Agrega tipos de espacio y tarjeta del Teatro Nacional con fotografía. |
| 13 | 2026-09-20 | `2eada84` | Iconos y mejoras en los avisos | Caso 2 | Incorpora iconos y estilos diferenciados para los avisos. |
| 14 | 2026-09-20 | `8efdde3` | Iconos de servicios | Caso 2 | Agrega iconos y alineación a los servicios. |
| 15 | 2026-09-20 | `253e559` | compliance con la consigna | Caso 2 | Ajusta nombres del menú a las opciones solicitadas. |
| 16 | 2026-09-20 | `e722c5b` | centrado del footer | Caso 2 | Centra el contenido del pie de página. |
