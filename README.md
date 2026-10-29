# ampere-maps

Descargas públicas de [Ampere](https://github.com/inQvan2/ampere): el mapa de Cuba para usar sin conexión y, más
adelante, los APK compilados. No contiene código de la app.

## Mapa de Cuba

`cuba.pmtiles` se publica en [Releases](../../releases). Es un mapa vectorial en esquema OpenMapTiles (zoom 0–14)
generado con [Planetiler](https://github.com/onthegomap/planetiler) a partir del extracto de Cuba de
[Geofabrik](https://download.geofabrik.de/central-america/cuba.html).

Para regenerarlo: Actions → «Build Cuba map» → Run workflow. Se publica a mano, sin calendario.

`cuba.json` apunta a la última publicación (`tag`, `url`, `size`); el flujo lo actualiza después de crear la
publicación. La app lo lee de `raw.githubusercontent.com` para saber si hay una versión nueva.

Los datos son © colaboradores de [OpenStreetMap](https://www.openstreetmap.org/copyright), bajo licencia ODbL.
