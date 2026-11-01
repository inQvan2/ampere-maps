# ampere-maps

Descargas públicas de [Ampere](https://github.com/inQvan2/ampere): el mapa de Cuba para usar sin conexión y los APK
compilados. No contiene código de la app.

## Cuba sin conexión (mapa y rutas)

Se publican en [Releases](../../releases) como `cuba-AAAA-MM-DD`, generados del mismo extracto de Cuba de
[Geofabrik](https://download.geofabrik.de/central-america/cuba.html):

| Archivo | Qué es |
|---|---|
| `cuba.pmtiles` | El mapa vectorial (esquema OpenMapTiles, zoom 0–14), generado con [Planetiler](https://github.com/onthegomap/planetiler). Sirve para dibujar. |
| `cuba-valhalla.tar.gz` | Los datos de rutas: teselas de [Valhalla](https://github.com/valhalla/valhalla) comprimidas. Sirven para calcular rutas sin conexión. |
| `SHA256SUMS` | La suma de cada archivo. |

En la app es una sola descarga, «Cuba sin conexión», que baja solo las partes que faltan o que cambiaron.

Para regenerarlos: Actions → «Build Cuba data» → Run workflow, eligiendo **qué generar**:
- `both` (por defecto): mapa y rutas del mismo extracto.
- `routing` o `map`: solo esa parte. La otra no se vuelve a publicar y la app no la descarga otra vez; puede quedar de
  un extracto de otra fecha (lo dicen las notas de cada release y `osmDate` en `cuba.json`).

Cada actualización con `both` hace que la app vuelva a bajar unos 137 MB: lánzalo solo cuando haga falta (cada pocos
meses o tras cambios importantes en las calles). Se publica a mano, sin calendario. Con `publish` desmarcado solo
genera y mide, sin publicar.

`cuba.json` apunta a la última versión de cada parte: el mapa en la raíz (`tag`, `url`, `size`, `sha256`,
`osmDate`; las versiones antiguas de la app leen solo los tres primeros) y las rutas en `routing` (`tag`, `url`,
`size`, `unpackedSize`, `sha256`, `osmDate`, `engine`, `formatVersion`). El flujo lo reescribe después de crear la
publicación. La app lo lee de `raw.githubusercontent.com` para saber si hay una versión nueva.

## APK de Ampere

Cada versión se publica en [Releases](../../releases) como `app-vX.Y.Z`, con **un APK por procesador**:

| Archivo | Para |
|---|---|
| `ampere-X.Y.Z-arm64-v8a.apk` | Casi todos los móviles actuales (64 bits). Si dudas, es este. |
| `ampere-X.Y.Z-armeabi-v7a.apk` | Móviles antiguos de 32 bits. |
| `ampere-X.Y.Z-x86_64.apk` | Emuladores y algunas tabletas. |

`SHA256SUMS` lleva la suma de cada uno. Si se instala el que no corresponde, Android lo rechaza.

Se compilan y firman en GitHub, en el repositorio privado de la app, al subir allí una etiqueta `vX.Y.Z`; aquí solo
llega la publicación final. `apk.json` apunta a la última versión (`tag`, `version`, `build` y la `url` y el `size` de
cada APK), igual que `cuba.json` con el mapa.

Los datos son © colaboradores de [OpenStreetMap](https://www.openstreetmap.org/copyright), bajo licencia ODbL.
