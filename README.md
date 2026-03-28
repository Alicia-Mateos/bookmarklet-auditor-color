# Auditoría de Color

Bookmarklet para analizar los colores que usa cualquier página web: ya sean los fondos, el texto, los bordes, los contornos... Muestra los colores en hex, OKLCH o en el formato que se encuentren y los separa entre colores sólidos y colores con transparencia.

## Requisitos

- Navegador moderno (Chrome, Firefox, Safari, Edge).
- JavaScript activado.
- Para **copiar al portapapeles**, la página debe servirse por HTTPS o ser `localhost` (restricción del navegador). Si falla, el bookmarklet intenta un método alternativo.

## Instalación

1. Abre [`auditor-color.html`](auditor-color.html) en el navegador (doble clic o arrastra el archivo a una pestaña).
2. Arrastra el enlace **«Auditor de color»** a la barra de marcadores (o el menú de marcadores).
3. Opcional: renombra el marcador si quieres otro nombre.

## Uso

1. Visita la página que quieras auditar.
2. Haz clic en el marcador **Auditor de color**.
3. Se abre un cuadro de diálogo centrado con:
   - **Colores sólidos**: opacidad 100 %.
   - **Colores con transparencia**: incluye el porcentaje de opacidad cuando aplica.
4. En cada muestra puedes **Copiar** el valor en hex (mayúsculas).
5. **Copiar todos los hex** exporta la lista de hex únicos (una línea por color).
6. En el caso de que se trate de un OKLCH también se copiará.
7. Cierra con **×** o **Escape**.

## Qué hace el bookmarklet

- Recorre los elementos del DOM y lee estilos computados (`getComputedStyle`): `background-color`, `color`, colores de borde y `outline-color`.
- Ignora valores totalmente transparentes o equivalentes a «sin color» para no llenar la lista de ruido.
- Normaliza a hex y etiqueta con nombres de color HTML cuando coinciden.
- Añade una descripción aproximada del matiz (p. ej. tonos de gris, dominancia RGB) para accesibilidad y contexto.

## Siguientes pasos recomendados (Figma)

Una vez que hayas copiado todos los colores desde el bookmarklet, el siguiente paso es llevarlos a una herramienta de diseño para analizarlos y organizarlos mejor:

1. Abre Figma (por ejemplo) y crea o accede a un archivo de trabajo.
2. Utiliza el plugin Pallete’r (aunque puedes usar cualquier otro plugin similar).
3. Pega todos los códigos hexadecimales en el campo de entrada separados por comas para asegurar que se procesen correctamente.
4. En la sección Variations selecciona No variations para evitar que se generen tonos adicionales automáticamente.
5. En Add ons puedes añadir información extra como RGB, CMYK o HSL si lo necesitas.
6. Haz clic en Create.

De esta forma, se generarán automáticamente cards de color dentro del lienzo de Figma, lo que te permitirá:
- Visualizar todos los colores detectados
- Organizarlos fácilmente
- Empezar a limpiarlos, agruparlos o construir un sistema de color consistente



## Limitaciones

- Solo ve colores aplicados vía **CSS computado** en el DOM; no analiza imágenes, vídeos ni canvas como bitmap.
- Colores definidos solo en hojas de estilo muy dinámicas o en iframes de otro origen pueden no reflejarse igual según políticas del navegador.
- El diálogo inyecta fuentes desde Google Fonts; en entornos sin red las fuentes pueden verse con fallback del sistema.

## Privacidad

El script se ejecuta **solo en tu navegador** en la página donde activas el marcador. No hay servidor propio ni envío de datos a terceros por parte de este proyecto (salvo la carga opcional de fuentes de Google al mostrar el panel).
