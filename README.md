# lumarp.images

Dépôt d’assets images pour **Luma RP**.

Sous-module du projet principal [`Luma.rp`](https://github.com/Nico-du-34/Luma.rp).

## Structure

| Dossier | Contenu |
| --- | --- |
| `inventory/` | Icônes items ox_inventory (PNG) |
| `vehicles/` | Photos véhicules (dealership / garage) |
| `loading/` | Fonds loading screen |

## CDN (inventaire)

URL de base (sans slash final) :

```text
https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/inventory
```

Config serveur (`ox.cfg`) :

```cfg
setr inventory:imagepath "https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/inventory"
```

Les scripts ne doivent **pas** hardcoder cette URL. Récupérer le chemin via :

```lua
local base = exports.ox_inventory:GetImagePath()
local url = ('%s/%s.png'):format(base, itemName)
-- NUI : envoyer `base` au front (SendNUIMessage / init)
```

## Checklist de migration

| Dossier | Source sur le serveur | Volume | Statut |
| --- | --- | --- | --- |
| `inventory/` | `Qbox_.../resources/[ox]/ox_inventory/web/images/` | ~963 fichiers / ~21 Mo | **migré** |
| `vehicles/` | `.../[jgscript]/jg-dealerships/vehicle_images/` | ~935 PNG / ~76 Mo | à faire |
| `loading/` | `.../pn-loadingscreen/html/images/` (+ `Logo.png`) | ~28 / ~6.8 Mo | à faire |

### Hors scope (ne pas dupliquer)

- `ox_inventory-old/web/images` (archive)
- `fivem-greenscreener/images/vehicles` (doublon dealership)
- Packs install jg-mechanic / pn-fishing (déjà dans inventory)
- UI qs-housing

### Workflow inventaire

1. Ajouter le PNG dans `inventory/` (nom = nom item, casse exacte).
2. Commit + push ce dépôt.
3. Attendre le cache jsDelivr (quelques minutes) ou pinner `@<commit>`.
4. Déclarer l’item dans `ox_inventory/data/items.lua` si besoin — pas de copie locale sur le serveur.
