# lumarp.images

Dépôt d’assets images pour **Luma RP**.

Sous-module du projet principal [`Luma.rp`](https://github.com/Nico-du-34/Luma.rp).

## Structure

| Dossier | Contenu |
| --- | --- |
| `inventory/` | Icônes items ox_inventory (PNG) |
| `vehicles/` | Photos véhicules (dealership / garage) |
| `loading/` | Fonds loading screen + logo |

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

## Checklist de migration

| Dossier | Source sur le serveur | Volume | Statut |
| --- | --- | --- | --- |
| `inventory/` | `ox_inventory/web/images/` | ~963 / ~21 Mo | **migré** |
| `loading/` | `pn-loadingscreen/html/images/` + `Logo.png` | ~28 / ~6.7 Mo | **migré** |
| `vehicles/` | `jg-dealerships/vehicle_images/` | ~935 PNG / ~76 Mo | à faire |

### Hors scope (ne pas dupliquer)

- `ox_inventory-old/web/images` (archive)
- `fivem-greenscreener/images/vehicles` (doublon dealership)
- Packs install jg-mechanic / pn-fishing (déjà dans inventory)
- UI qs-housing
- `pn-loadingscreen/html/music.mp3` (reste local)

### Workflow

1. Ajouter le fichier dans le dossier concerné (`inventory/` / `loading/` / `vehicles/`).
2. Commit + push ce dépôt.
3. Attendre le cache jsDelivr (quelques minutes) ou pinner `@<commit>`.
