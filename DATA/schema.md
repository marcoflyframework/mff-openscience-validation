# DATA schema

> Descrizione campi per i dati open pubblicati in questo repository.
>
> Dati spinti dal Worker `mff-cron` ogni notte alle 03:00 UTC da [marcofly.app/api/validation-stats](https://marcofly.app/api/validation-stats) (v. [PERCHE-NIENTE-SYNC-WORKFLOW](../.github/PERCHE-NIENTE-SYNC-WORKFLOW.md)).

---

## `submissions.csv`

Dataset open dei contributi della community. Una riga per submission. Anonimizzato.

| Campo | Tipo | Descrizione | Esempio |
|---|---|---|---|
| `id` | integer | ID submission (auto-increment) | `1234` |
| `submitted_at` | ISO8601 datetime | Quando è stata inviata | `2026-06-15T14:32:21Z` |
| `submitter_hash` | string | SHA-256 dell'email (anonimo, permette dedup senza esporre email) | `a3f2b1...` |
| `prompt_id` | string | ID prompt da PROMPT_BANK | `P042` |
| `prompt_category` | string | Categoria | `ragionamento` |
| `prompt_difficulty` | integer | 1-3 | `2` |
| `language` | string | IT / EN | `IT` |
| `ai_provider_baseline` | string | Provider AI usato per output_baseline | `openai-gpt-4o` |
| `ai_provider_mff` | string | Provider AI usato per output_mff | `anthropic-claude-sonnet-4-5` |
| `output_baseline_length` | integer | Caratteri output baseline | `342` |
| `output_mff_length` | integer | Caratteri output MFF | `418` |
| `output_baseline_text` | string | Testo output baseline (publicato CC BY 4.0) | `"Marco è più alto di..."` |
| `output_mff_text` | string | Testo output MFF (publicato CC BY 4.0) | `"🟢 Marco è più alto di..."` |
| `rating_baseline` | integer | 1-5 stelle | `3` |
| `rating_mff` | integer | 1-5 stelle | `4` |
| `delta` | integer | rating_mff − rating_baseline | `+1` |
| `notes` | string | Note libere submitter (pubblicate) | `"MFF ha aggiunto il bollino correttamente"` |
| `status` | string | `valid` / `flagged` / `rejected` (post manual review) | `valid` |

**Esclusi mai dal CSV** (privacy):
- `submitter_email` (solo hash è pubblico)
- `ip_hash`
- `nickname` (è in `supporters.json`, opt-in)
- `consent_data_publication` (presupposto a TRUE per essere nel CSV)

---

## `stats.json`

Statistiche aggregate per la progress bar + dashboard pubblica.

```json
{
  "generated_at": "2026-06-15T14:32:21Z",
  "total_submissions": 342,
  "valid_submissions": 318,
  "flagged_submissions": 12,
  "rejected_submissions": 12,
  "goal_total": 1000,
  "progress_percent": 31.8,
  "milestones": {
    "100": true,
    "250": true,
    "500": false,
    "750": false,
    "1000": false
  },
  "validators_count": 87,
  "validators_opted_in": 42,

  "by_category": {
    "fatti": 78,
    "calcoli": 65,
    "ragionamento": 72,
    "opinione": 58,
    "creativita": 69
  },
  "by_language": {
    "IT": 198,
    "EN": 144
  },
  "by_provider": [
    { "provider": "openai-gpt-4o", "count": 89 },
    { "provider": "anthropic-claude-sonnet-4-5", "count": 78 },
    { "provider": "google-gemini-2.5-flash", "count": 61 },
    { "provider": "groq-llama-3.3-70b", "count": 45 }
  ],
  "mean_rating_baseline": 3.2,
  "mean_rating_mff": 3.7,
  "mean_delta": 0.5,
  "note": "Statistiche descrittive — analisi statistica con CI/p-value disponibile in ANALYSIS.ipynb dopo milestone 1000."
}
```
Semantica dei due campi (dal 2026-08-04, allineata su tutte le superfici):

- `validators_count` — **persone** distinte (hash) fra le submission non rifiutate, lo stesso denominatore della barra pubblica;
- `validators_opted_in` — **nickname distinti** della Hall (submission valide + consenso + nickname): il numero di VOCI della lista pubblica, identico per costruzione alle entry di `supporters.json` e a «Supporter pubblici» su marcofly.app/contribute/time.


---

## `supporters.json`

Lista Validator opt-in per la Hall pubblica su [marcofly.app/open-review](https://marcofly.app/open-review).

```json
{
  "generated_at": "2026-06-15T14:32:21Z",
  "total_supporters": 42,
  "supporters": [
    {
      "nickname": "Alice_42",
      "submission_count": 27,
      "badge": "🥇",
      "first_submission_at": "2026-06-05T10:11:33Z",
      "last_submission_at": "2026-06-15T09:22:18Z"
    },
    {
      "nickname": "BookLover",
      "submission_count": 8,
      "badge": "🥈",
      "first_submission_at": "2026-06-08T15:44:01Z",
      "last_submission_at": "2026-06-15T11:33:55Z"
    }
  ]
}
```

Ordine sempre **alfabetico per nickname** (case-insensitive).

---

## Note privacy

- Nessun campo esposto consente di risalire all'identità reale del submitter senza accesso al DB privato MFF
- `submitter_hash` è SHA-256 dell'email — permette dedup ma è computazionalmente infattibile invertirlo
- Submitter con opt-out al public dataset (campo `consent_data_publication = false` nel DB privato MFF) NON appaiono nel CSV pubblico, anche se le loro submission contano per le statistiche aggregate

Vedi [PROTOCOL.md §7](../PROTOCOL.md#7-privacy--gdpr).
