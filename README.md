# lumarp.images

Dépôt d’assets images pour **Luma RP**.

Sous-module du projet principal [`Luma.rp`](https://github.com/Nico-du-34/Luma.rp).

## Structure

| Dossier | Contenu |
| --- | --- |
| `inventory/` | Icônes items ox_inventory (PNG) |
| `vehicles/` | Photos véhicules (dealership / garage) |
| `loading/` | Fonds loading screen + logo |
| `maps/` | Fonds carte admin (satellite / atlas WebP) |

## CDN inventaire

```text
https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/inventory
```

```cfg
setr inventory:imagepath "https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/inventory"
```

```lua
local base = exports.ox_inventory:GetImagePath()
```

## CDN loading

```text
https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/loading
```

Config NUI : `pn-loadingscreen/html/cdn-config.js` (`window.LOADING_IMAGE_BASE`).

Contenu attendu dans `loading/` : `bg_01.jpg`…`bg_XX.jpg`, `Logo.png`, `manifest.json`.

## CDN vehicles

```text
https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/vehicles/{model}.png
```

Utilisé par `jg-dealerships` et `jg-advancedgarages` (NUI). Fallback docs.fivem.net si PNG absent.

Nom de fichier = spawn code / modèle (casse exacte), ex. `adder.png`.

## CDN maps (admin)

```text
https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/maps/satellite.webp
https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/maps/atlas.webp
```

Utilisé par `pn-adminmenu` (Leaflet ImageOverlay, CRS.Simple).

Contenu attendu dans `maps/` :

| Fichier | Description |
| --- | --- |
| `satellite.webp` | Vue satellite pleine carte (~5–6k) |
| `atlas.webp` | Vue atlas / schéma pleine carte |

Source assemblée : tuiles communautaires type CreepPork/Flamm64 (zoom 6 → 5632² WebP). Qualité inférieure au pack MEGA RiceaRaul non disponible ici ; remplacer les WebP si un pack 8k officiel est fourni.

## Checklist de migration

| Dossier | Source sur le serveur | Volume | Statut |
| --- | --- | --- | --- |
| `inventory/` | `ox_inventory/web/images/` | ~963 / ~21 Mo | **migré** |
| `loading/` | `pn-loadingscreen/html/images/` + `Logo.png` | ~28 / ~6.7 Mo | **migré** |
| `vehicles/` | `jg-dealerships/vehicle_images/` | ~935 PNG / ~76 Mo | **migré** |
| `maps/` | fond carte admin (ex-tuiles nikez) | 2 WebP / ~4 Mo | **migré** |

### Hors scope (ne pas dupliquer)

- `ox_inventory-old/web/images` (archive)
- `fivem-greenscreener/images/vehicles` (doublon dealership)
- Packs install jg-mechanic / pn-fishing (déjà dans inventory)
- UI qs-housing
- `pn-loadingscreen/html/music.mp3` (reste local)
- `jg-advancedgarages/vehicle_images/` (dossier vide, fallback CDN)

### Workflow

1. Ajouter le fichier dans le dossier concerné (`inventory/` / `loading/` / `vehicles/` / `maps/`).
2. Commit + push ce dépôt.
3. Attendre le cache jsDelivr (quelques minutes) ou pinner `@<commit>`.
