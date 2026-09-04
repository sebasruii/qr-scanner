# Escáner por lotes

Escáner de códigos QR / de barras que funciona en el navegador del móvil.
Lee varios códigos seguidos, los acumula en una lista y los exporta a CSV.

- Todo ocurre en el navegador: no se sube ningún dato a ningún servidor.
- Necesita HTTPS para poder abrir la cámara (por eso GitHub Pages, y no abrir el archivo local).
- Los códigos se guardan en el navegador (localStorage), así que sobreviven a una recarga o a que
  iOS descarte la pestaña. Se borran con el botón "Borrar todo".

## Decodificadores

Se prueban dos motores distintos sobre cada frame, porque ZXing rechazaba códigos
que la cámara nativa de iOS sí lee:

1. [jsQR](https://github.com/cozmo/jsQR) con `inversionAttempts: 'attemptBoth'`,
   que cubre los códigos claros sobre fondo oscuro.
2. [zbar-wasm](https://github.com/undecaf/zbar-wasm) si el primero falla: es ZBar
   compilado a WebAssembly, bastante más tolerante con códigos estilizados.

## Uso

Abrir la URL de GitHub Pages en el móvil y dar permiso a la cámara.
En iPhone conviene abrirlo en Safari y usar "Compartir → Añadir a pantalla de inicio".
