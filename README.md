# meridian-fleet-ops
Cruise Liner Voyage &amp; Revenue Tracking — an interactive 3D console built with Three.js + WebGL.

## How it works

**Voyage simulation.** Each port carries real latitude/longitude. The [haversine formula](https://en.wikipedia.org/wiki/Haversine_formula) computes leg distances in nautical miles, and the full loop's real-time duration is derived from total distance ÷ cruising speed (19 kn). The sim interpolates the ship's position along the current leg, then back-calculates everything on the dashboard — speed, heading (via a bearing calculation between coordinates), next port, ETA, and nautical miles logged vs. remaining. `LIVE / FAST / WARP` just scale the sim clock.

**Deck-to-data binding.** A single data model defines each deck and its zones, where every zone stores a normalized footprint (`x`, `z`) on the deck. That one object drives *two* things at once: the 3D zone meshes placed on the ship, and the right-panel analytics (KPIs, charts, zone list, and the insight card). So the spatial model and the numbers can never drift apart — they read from the same source.

**Interaction.** Clicking a deck (in the sidebar or directly on the 3D model) renders that deck's analytics; clicking a zone isolates and highlights its floating label on the ship. The camera uses orbit controls (azimuth / polar / distance) with preset ¾, Port Beam, and Aerial views.

**Charts.** All visuals — bar, stacked, and grouped — are hand-built as inline SVG from the data, no charting library.
