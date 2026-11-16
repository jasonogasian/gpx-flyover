# GPX flyover

Turn any GPX or TCX track (a run, ride, hike or ski tour) into a 3D flyover video over satellite imagery and terrain.

**Use it:** https://jasonogasian.github.io/gpx-flyover/

1. Export a GPX of your activity (Garmin Connect: activity, gear menu, Export to GPX; Strava: activity, ⋯ menu, Export GPX).
2. Drop it on the page, pick the stats, size and camera you like, and press Preview.
3. Press Export MP4. Works in Chrome, Edge and Safari 17+.

Everything runs in your browser. Your GPX file never leaves your computer; the page only downloads map tiles.

## How it works

- [MapLibre GL JS](https://maplibre.org/) draws satellite imagery draped over 3D terrain.
- Terrain: [AWS Terrain Tiles](https://registry.opendata.aws/terrain-tiles/) (Mapzen, open data).
- Imagery: Esri World Imagery by default; MapTiler or Mapbox with your own key (kept only in your browser), Sentinel-2 cloudless (CC BY 4.0), or shaded relief.
- The camera follows a smoothed version of the track, so switchbacks become gentle sweeps.
- Each frame waits for its map tiles, then WebCodecs encodes it to H.264 and [mp4-muxer](https://github.com/Vanilagy/mp4-muxer) writes the MP4, so the video is smooth on any connection.

Stats are in miles and feet, and pace is per mile, which suits running and hiking more than riding.

Imagery providers limit how their imagery may be used in video. That's fine for sharing your own activities; check their terms before any commercial use.
