# MFF OpenScience Validation

> **Validazione community-driven del MarcoFLY Framework (MFF-EX)** — un progetto Open Science aperto, riproducibile, trasparente.

[![License: CC BY 4.0](https://img.shields.io/badge/Data-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![License: MIT](https://img.shields.io/badge/Code-MIT-blue.svg)](LICENSE-CODE)
[![OSF Preregistration](https://img.shields.io/badge/OSF-9ehgx-336699.svg)](https://osf.io/9ehgx/)
[![Submissions](https://img.shields.io/badge/dynamic/json?label=Submissions&query=$.total_submissions&url=https%3A//marcofly.app/api/validation-stats)](https://marcofly.app/contribute-time)

---

## 🎯 In una frase

Vogliamo capire **se e quanto MFF funziona davvero**, in modo che chiunque possa verificarlo, replicarlo, criticarlo o smentirlo. Senza chiacchiere, con dati.

## ❓ Cosa stiamo testando

Cinque domande semplici. Niente jargon.

| ID | La domanda (versione "nonno") | Versione tecnica |
|---|---|---|
| **H1** | *Con MFF l'AI mente di meno quando non sa la risposta?* | MFF riduce hallucination rate su prompt factuali ambigui |
| **H2** | *I bollini 🟢🔵🟡 dell'AI dicono davvero quanto è sicura?* | Le etichette epistemiche sono calibrate con accuracy reale |
| **H3** | *MFF non rallenta o peggiora le cose semplici?* | MFF preserva instruction-following su task baseline |
| **H4** | *MFF funziona uguale in italiano e in inglese?* | MFF è language-agnostic (IT/EN delta < 10%) |
| **H5** | *MFF funziona uguale con AI diverse (Claude, ChatGPT, Gemini, Llama)?* | MFF è model-agnostic (delta < 20% across providers) |

Sono **falsificabili**: se i dati dicono "no", lo diciamo. Non barare con i numeri è il punto di tutto questo.

## 🤝 Come puoi contribuire (5 minuti)

1. Vai su **[marcofly.app/contribute-time](https://marcofly.app/contribute-time)**
2. Scegli un prompt random dal [Prompt Bank](PROMPT_BANK.md)
3. Copialo in DUE AI a tua scelta — una **senza MFF**, una **con MFF**
4. Incolla i due output nel form, dai un voto da 1 a 5 stelle a ognuno
5. Submit. Ricevi **750 crediti MFF gratis** + badge di Validator 🥉

Email richiesta solo per credit-back + badge. Niente spam, niente profilazione. Vedi [Privacy](https://marcofly.app/privacy).

## 📊 Stato attuale

Vedi [DATA/stats.json](DATA/stats.json) (aggiornato automaticamente ogni 24h via GitHub Action) e la [progress bar live](https://marcofly.app/contribute-time).

**Goal validazione robusta**: 1.000 submission · **Milestone**: 100 → 250 → 500 → 750 → 1.000.

## 🧪 Come è strutturato

| File | Cosa contiene |
|---|---|
| [`PROTOCOL.md`](PROTOCOL.md) | Disegno sperimentale (come si analizza, quali metriche, quali test statistici) |
| [`HYPOTHESES.md`](HYPOTHESES.md) | Le 5 ipotesi H1-H5 in dettaglio (statement, predizione, falsificazione) |
| [`PROMPT_BANK.md`](PROMPT_BANK.md) | 100 prompt curati in 5 categorie (fatti, calcoli, ragionamento, opinione, creatività) |
| [`RUBRIC.md`](RUBRIC.md) | Criteri di valutazione 1-5 stelle (uguali per chiunque) |
| [`ANALYSIS.ipynb`](ANALYSIS.ipynb) | Notebook Jupyter per analisi statistica replicabile (Python + pandas + matplotlib) |
| [`CONTRIBUTORS.md`](CONTRIBUTORS.md) | Lista nominativa supporter attivi (chi ha optato in) |
| [`DATA/`](DATA/) | Dati aggregati pubblici (CSV + JSON) — aggiornato via GH Action |

## 🛡 Privacy e licenze

- **Dati**: [CC BY 4.0](LICENSE) — puoi riusarli, citando MFF OpenScience Validation
- **Codice (notebook, scripts)**: [MIT](LICENSE-CODE) — riutilizzabile liberamente
- **Email submitter**: non pubblicate mai, salvate solo come hash per dedup + accredito crediti (vedi [PROTOCOL.md §Privacy](PROTOCOL.md#privacy))
- **Nickname**: pubblicati solo se hai spuntato esplicitamente l'opt-in nel form

## 🔗 Link essenziali

- 🌐 Sito MFF: [marcofly.app](https://marcofly.app)
- 🤖 PWA per usare MFF: [app.marcofly.app](https://app.marcofly.app)
- 📋 OSF preregistration: [osf.io/9ehgx](https://osf.io/9ehgx/)
- 🧠 ORCID autore: [0009-0001-9118-6183](https://orcid.org/0009-0001-9118-6183)
- 📚 Documentazione framework: [marcofly.app/mff](https://marcofly.app/mff)
- 💬 Discussioni community: [Issues](https://github.com/marcoflyframework/mff-openscience-validation/issues)

## ⚠ Limiti onesti dichiarati

1. **Non è peer review accademica formale.** Possiamo dire *"evidence-informed, community-validated, preregistered"*, non *"peer-reviewed in Nature"*.
2. **Selezione bias**: chi partecipa è già early adopter pro-MFF. Mitighiamo con inviti espliciti a critici + spazio note per disaccordo.
3. **Quality control**: filtri anti-spam (rate limit IP + reCAPTCHA + manual review periodica admin). Submission flag come "sospette" sono escluse dall'analisi finale.
4. **N campione**: con 5 submission/giorno servono ~2 mesi per N=300 (effect size moderato).

Questi limiti li discutiamo apertamente nel report finale.

---

> *MarcoFLY Framework — Find · Leader · In · You*
> *© 2026 Marco Motta · Sito CC BY-NC-ND 4.0 · Framework MFF Proprietary License 1.0*
> *Validation project dati e codice: CC BY 4.0 + MIT.*
