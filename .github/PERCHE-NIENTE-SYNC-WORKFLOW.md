# Perché qui non c'è più un workflow di sync

Fino al 3 agosto 2026 c'era `.github/workflows/sync-stats.yml`: ogni notte
scaricava tre endpoint di `marcofly.app` in `DATA/` e faceva un commit.

**Non ha mai funzionato**, in tutta la vita del repo.

## Cosa succedeva

Cloudflare protegge `marcofly.app` e **sfida gli IP di datacenter** — quelli dei
runner GitHub. La risposta al runner era:

```
HTTP/2 403
cf-mitigated: challenge
<title>Just a moment...</title>
```

Un bot non può risolvere quella sfida. Mai.

E non si vedeva, perché ogni fetch finiva con:

```bash
curl -fsSL ... || { echo "::warning::Failed ... Skipping."; exit 0; }
```

`exit 0` fa **passare** lo step. Il job risultava verde ogni notte — 13 secondi,
spunta verde — mentre `DATA/` restava fermo al segnaposto del commit iniziale.
*Un verde che certifica che non è successo niente è peggio di un rosso: un rosso
lo guardi.*

## Perché non basta una regola WAF

Sul piano **Free**, Bot Fight Mode non ha opzioni di configurazione: non esistono
eccezioni per percorso, quindi una regola WAF con azione *Skip* non ha niente da
saltare. Provato: regola creata e attiva, sfida invariata. Le eccezioni per
percorso arrivano con Super Bot Fight Mode, dal piano Pro in su.

## Cosa c'è adesso

**Il verso è invertito.** Non è più GitHub a tirare i dati: è il Worker
`mff-cron` a **spingerli**, alle 03:00 UTC, con una chiamata in *uscita* verso
l'API di GitHub — che nessuna protezione in entrata può fermare.

- codice: `mff-cron/src/openscience-sync.js` (repo privato dell'ecosistema)
- token: fine-grained, **questo solo repo**, permesso `Contents: read & write`.
  Non ha il permesso `workflows`: quel token **non può modificare** ciò che gira
  qui dentro.
- i commit arrivano firmati `chore(data): sync stats da marcofly.app (data)`
- se anche uno solo dei tre endpoint non risponde, **non pubblica niente**: un
  commit con due file nuovi e uno vecchio sarebbe un dataset mai esistito in
  nessun momento
- se i dati non sono cambiati, non committa: niente rumore quotidiano

Primo sync riuscito: `3a2c668`, 3 agosto 2026.
