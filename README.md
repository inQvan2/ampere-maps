# ampere-maps

Descargas públicas de [Ampere](https://github.com/inQvan2/ampere): el mapa de Cuba para usar sin conexión y los APK
compilados. No contiene código de la app.

## Mapa de Cuba

`cuba.pmtiles` se publica en [Releases](../../releases). Es un mapa vectorial en esquema OpenMapTiles (zoom 0–14)
generado con [Planetiler](https://github.com/onthegomap/planetiler) a partir del extracto de Cuba de
[Geofabrik](https://download.geofabrik.de/central-america/cuba.html).

Para regenerarlo: Actions → «Build Cuba map» → Run workflow. Se publica a mano, sin calendario.

`cuba.json` apunta a la última publicación (`tag`, `url`, `size`); el flujo lo actualiza después de crear la
publicación. La app lo lee de `raw.githubusercontent.com` para saber si hay una versión nueva.

## APK de Ampere

Cada versión se publica en [Releases](../../releases) como `app-vX.Y.Z`, con **un APK por procesador**:

| Archivo | Para |
|---|---|
| `ampere-X.Y.Z-arm64-v8a.apk` | Casi todos los móviles actuales (64 bits). Si dudas, es este. |
| `ampere-X.Y.Z-armeabi-v7a.apk` | Móviles antiguos de 32 bits. |
| `ampere-X.Y.Z-x86_64.apk` | Emuladores y algunas tabletas. |

`SHA256SUMS` lleva la suma de cada uno. Si se instala el que no corresponde, Android lo rechaza.

Se compilan enteros en GitHub (Actions → «Build APK») a partir del código privado de la app: al subir una etiqueta
`vX.Y.Z` en `ampere`, su flujo «Release APK» lanza este. También se puede lanzar a mano con una etiqueta o una rama
(una rama solo deja los APK como artefacto, sin publicar). `apk.json` apunta a la última versión (`tag`, `version`,
`build` y la `url` y el `size` de cada APK), igual que `cuba.json` con el mapa.

Los datos son © colaboradores de [OpenStreetMap](https://www.openstreetmap.org/copyright), bajo licencia ODbL.
