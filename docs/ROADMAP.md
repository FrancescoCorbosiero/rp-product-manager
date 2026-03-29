# ROADMAP — RP Product Manager

## Stato Attuale — v1.0 (Feature-Complete)

Il plugin è completo per il suo scope. Tutte le funzionalità core sono implementate e funzionanti.

### PHP Layer (crud.php + variations.php)
- [x] `rp_get_product()` — lettura completa prodotto + meta Rank Math
- [x] `rp_create_product()` — creazione prodotto simple con tutti i campi
- [x] `rp_update_product()` — update selettivo (solo campi presenti nel payload)
- [x] `rp_delete_product()` — soft delete (cestino) o hard delete (force)
- [x] `rp_search_products()` — ricerca multi-strategia: ID → SKU esatto → fulltext → SKU LIKE
- [x] `rp_get_product_variations()` — legge varianti, estrae taglia, ordina numericamente
- [x] `rp_update_variation()` — aggiorna singola variante + sync prodotto padre
- [x] `rp_bulk_update_variations()` — aggiorna N varianti in una chiamata

### AJAX Layer (ajax.php)
- [x] `rp_ajax_read`
- [x] `rp_ajax_create`
- [x] `rp_ajax_update`
- [x] `rp_ajax_delete`
- [x] `rp_ajax_search`
- [x] `rp_ajax_get_variations`
- [x] `rp_ajax_save_variations`

### Admin UI (admin-page.php)
- [x] Search bar con dropdown (ID / SKU / titolo, 280ms debounce, keyboard nav)
- [x] Product card (stato attivo, nome, SKU, prezzo, status badge)
- [x] Tab: Varianti — tabella inline editabile con dirty tracking visivo
- [x] Tab: Varianti — bulk toolbar (prezzo reg., saldo, stock, clear saldo)
- [x] Tab: Varianti — select/deselect righe + select all
- [x] Tab: Varianti — save con singola AJAX call + refresh automatico
- [x] Tab: Prodotto — form completo (nome, SKU, prezzi, status, stock, descrizione breve, Rank Math)
- [x] Tab: JSON — editor raw + viewer syntax-highlighted affiancati
- [x] Tab: JSON — POST Create / PUT Update / DELETE diretti dall'editor
- [x] Toast notifications (ok / err / inf)
- [x] Dark theme, mobile-aware

---

## Principio Guida

**Non sono previste nuove feature fuori dallo scope del plugin.**
Il lavoro futuro riguarda esclusivamente miglioramenti, bug fix e raffinamenti di ciò che esiste già.

---

## Miglioramenti Futuri (solo su richiesta esplicita)

Queste sono idee catalogate, non impegni. Si affrontano solo quando il developer le richiede.

- [ ] Miglioramenti UX alla UI esistente (accessibility, touch target, responsive edge cases)
- [ ] Ottimizzazioni performance sulle query di ricerca
- [ ] Raffinamenti dirty tracking e gestione errori
- [ ] Miglioramenti al feedback visivo (stati di loading, conferme)

---

## Decisioni Architetturali

| Decisione | Motivazione |
|---|---|
| Nessun Composer | Zero complessità di setup, zero dipendenze esterne |
| Vanilla JS (no build) | Deploy immediato, zero toolchain, compatibilità WP Admin |
| Tutto in un plugin | Semplicità, un solo deploy |
| PHP 8.0 minimo | Sintassi moderna (null-safe, union types, named args) |
