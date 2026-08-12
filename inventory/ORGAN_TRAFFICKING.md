# Items trafic d'organes

Images requises (nom = id item) pour le CDN jsDelivr :

| Fichier | Item |
| --- | --- |
| `chloroform_rag.png` | Chiffon chloroforme |
| `organ_scalpel.png` | Scalpel |
| `organ_heart.png` | Cœur |
| `organ_kidney.png` | Rein |
| `organ_liver.png` | Foie |
| `organ_lung.png` | Poumon |
| `organ_eye.png` | Œil |

Icônes flat 128×128 (fond transparent) dans ce dossier. Le menu client `organ_sale` résout les icônes via `exports.ox_inventory:GetImagePath()` → `{base}/{name}.png`.

## Déploiement CDN

Les fichiers doivent être **commit + push dans le dépôt `lumarp.images`** (sous-module), pas seulement le parent Luma.rp. Ensuite :

1. Attendre le cache jsDelivr (quelques minutes) **ou** pinner `@<commit>` dans `inventory:imagepath`
2. Vérifier : `https://cdn.jsdelivr.net/gh/Nico-du-34/lumarp.images@main/inventory/organ_heart.png`

Sans push du sous-module, l’inventaire et le menu « Vente organes » continueront d’afficher d’anciennes images / 404.
