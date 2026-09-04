# Escáner por lotes

Escáner de códigos QR / de barras que funciona en el navegador del móvil.
Lee varios códigos seguidos, los acumula en una lista y los exporta a CSV.

- Todo ocurre en el navegador: no se sube ningún dato a ningún servidor.
- Sin dependencias de CDN: las librerías están en `lib/` y se sirven desde el propio
  repositorio, así que la página no hace ni una petición a terceros.
- Una CSP en el `<meta>` bloquea toda salida de red (`connect-src 'none'`), de modo que
  ni siquiera un script comprometido podría enviar los códigos a ningún sitio.
- Comprobable: activa el modo avión después de cargarla y seguirá escaneando igual.
- Necesita HTTPS para poder abrir la cámara (por eso GitHub Pages, y no abrir el archivo local).
- Los códigos se guardan en el navegador (localStorage), así que sobreviven a una recarga o a que
  iOS descarte la pestaña. Se borran con el botón "Borrar todo".

## Decodificadores

Se prueban dos motores distintos sobre cada frame, porque ZXing rechazaba códigos
que la cámara nativa de iOS sí lee:

1. [jsQR](https://github.com/cozmo/jsQR) 1.4.0 con `inversionAttempts: 'attemptBoth'`,
   que cubre los códigos claros sobre fondo oscuro.
2. [zbar-wasm](https://github.com/undecaf/zbar-wasm) 0.11.0 si el primero falla: es ZBar
   compilado a WebAssembly, bastante más tolerante con códigos estilizados.

Ambas viven en `lib/`, copiadas tal cual desde jsDelivr. Para actualizarlas hay que
volver a descargarlas a mano, que es justo lo que hace auditable lo que se ejecuta.

## Uso

Abrir la URL de GitHub Pages en el móvil y dar permiso a la cámara.
En iPhone conviene abrirlo en Safari y usar "Compartir → Añadir a pantalla de inicio".
