# Escáner por lotes

Escáner de códigos QR / de barras que funciona en el navegador del móvil.
Lee varios códigos seguidos, los acumula en una lista y los exporta a CSV.

- Todo ocurre en el navegador: no se sube ningún dato a ningún servidor.
- Necesita HTTPS para poder abrir la cámara (por eso GitHub Pages, y no abrir el archivo local).
- Los códigos se guardan en el navegador (localStorage), así que sobreviven a una recarga o a que
  iOS descarte la pestaña. Se borran con el botón "Borrar todo".

## Uso

Abrir la URL de GitHub Pages en el móvil y dar permiso a la cámara.
En iPhone conviene abrirlo en Safari y usar "Compartir → Añadir a pantalla de inicio".
