# Catalog Structure — ResellPiacenza

> **Nota:** I file catalogo non sono ancora nel repo. La struttura descritta qui è provvisoria
> e verrà aggiornata quando i file reali saranno forniti dal developer.

---

## File Catalogo (da aggiungere)

| File | Descrizione |
|---|---|
| `catalogo.csv` | Catalogo principale |
| `catalog_corteiz.csv` | Sub-catalogo brand Corteiz |
| `catalog.json` | Versione JSON del catalogo |

---

## SKU Convention

**Prodotto padre:** `BRAND-MODEL-DETAIL`
```
NK-DL-BLK-LIME    → Nike Dunk Low Black Lime Glow
NK-AM90-OG        → Nike Air Max 90 OG
AJ4-BLACKCAT-2025 → Air Jordan 4 Black Cat 2025
```

**Variante (taglia):** `SKU-PADRE-T{TAGLIA}`
```
NK-DL-BLK-LIME-T40
NK-DL-BLK-LIME-T40.5
NK-DL-BLK-LIME-T41
```

---

## Tipo Prodotto WooCommerce

Tutti i prodotti con varianti taglia → `variable`
Prodotti senza taglie (accessori, ecc.) → `simple`

---

## Attributo Taglia

Termine WooCommerce: `pa_taglia`
Slug: `taglia`

```php
// Come viene cercato in rp_get_product_variations():
preg_match('/(taglia|size|misura|eu|uk|us|fr|cm)/i', $attribute_key)
```

Se il negozio usa un nome attributo diverso (es. `pa_size`, `pa_eu`), aggiornare la regex in `variations.php`.
