# MFF OpenScience Validation

> **Validazione community-driven del MarcoFLY Framework (MFF-EX)** — un progetto Open Science aperto, riproducibile, trasparente.

[![License: CC BY 4.0](https://img.shields.io/badge/Data-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![License: MIT](https://img.shields.io/badge/Code-MIT-blue.svg)](LICENSE-CODE)
[![OSF Preregistration](https://img.shields.io/badge/OSF-9ehgx-336699.svg)](https://osf.io/9ehgx/)
[![Submissions](https://img.shields.io/badge/dynamic/json?label=Submissions&query=$.total_submissions&url=https%3A//raw.githubusercontent.com/marcoflyframework/mff-openscience-validation/main/DATA/stats.json)](https://marcofly.app/contribute/time)

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

1. Vai su **[marcofly.app/contribute/time](https://marcofly.app/contribute/time)**
2. Scegli un prompt random dal [Prompt Bank](PROMPT_BANK.md)
3. Copialo in DUE AI a tua scelta — una **senza MFF**, una **con MFF**
4. Incolla i due output nel form, dai un voto da 1 a 5 stelle a ognuno
5. Submit, poi **conferma l'email** che ti arriva

Email richiesta per la conferma, per l'accredito dei crediti e per il badge. Niente spam, niente profilazione. Vedi [Privacy](https://marcofly.app/privacy).

### 💚 Cosa ricevi

I crediti arrivano **dopo** due passaggi: la conferma della tua email e una **revisione umana** della submission. Non sono automatici, e non lo diciamo per prudenza: è la stessa disciplina con cui trattiamo i dati.

Il valore **scende a scaglioni**, contando le tue submission già accreditate:

| La tua submission valida n° | Crediti |
|---|---|
| 1ª | **100** |
| 2ª – 3ª | 50 |
| 4ª – 10ª | 25 |
| dall'11ª in poi | 10 |

Scende per due ragioni, e le diciamo apertamente. La prima submission costa molto più delle altre a chi la fa: creare l'account, capire il form, lanciare due modelli, confrontare. E per lo studio **dieci giudizi di dieci persone diverse valgono più di dieci della stessa persona** — quello che misuriamo è se MFF migliora le risposte *secondo giudici diversi*, quindi il prezzo segue il valore.

**Non arriva mai a zero**: chi continua a contribuire continua a essere pagato. E se dopo un accredito il tuo saldo resta sotto i 100 crediti, viene **riportato a 100** — chi dona tempo non deve restare senza il necessario per usare la piattaforma.

### 🏅 Badge

Calcolati sulle submission valide. Non si spendono e non scadono.

🌱 Validatore (1) · 🥉 Bronzo (3) · 🥈 Argento (10) · 🥇 Oro (25) · 💎 Diamante (50)

Il tuo **nickname** compare in [`CONTRIBUTORS.md`](CONTRIBUTORS.md) **solo** se hai spuntato l'opt-in nel form. Altrimenti resti l'hash anonimo, anche qui.

## 📊 Stato attuale

Vedi [DATA/stats.json](DATA/stats.json) e la [barra di avanzamento live](https://marcofly.app/contribute/time). I due numeri usano **la stessa regola**: contano le submission non rifiutate.

**Goal validazione robusta**: 1.000 submission · **Milestone**: 100 → 250 → 500 → 750 → 1.000.

I file in `DATA/` sono pubblicati **una volta al giorno alle 03:00 UTC** dall'infrastruttura MFF, e **solo se qualcosa è cambiato**: se non vedi commit, non è un guasto — è che i numeri sono gli stessi. Se invece un dato non fosse recuperabile, la pubblicazione **si ferma del tutto** anziché caricare un aggiornamento parziale: un dataset a metà sembra coerente e non lo è.

## 🧪 Come è strutturato

| File | Cosa contiene |
|---|---|
| [`PROTOCOL.md`](PROTOCOL.md) | Disegno sperimentale (come si analizza, quali metriche, quali test statistici) |
| [`HYPOTHESES.md`](HYPOTHESES.md) | Le 5 ipotesi H1-H5 in dettaglio (statement, predizione, falsificazione) |
| [`PROMPT_BANK.md`](PROMPT_BANK.md) | 100 prompt curati in 5 categorie (fatti, calcoli, ragionamento, opinione, creatività) |
| [`RUBRIC.md`](RUBRIC.md) | Criteri di valutazione 1-5 stelle (uguali per chiunque) |
| [`ANALYSIS.ipynb`](ANALYSIS.ipynb) | Notebook Jupyter per analisi statistica replicabile (Python + pandas + matplotlib) |
| [`CONTRIBUTORS.md`](CONTRIBUTORS.md) | Lista dei supporter che hanno dato il consenso |
| [`DATA/`](DATA/) | I dati pubblici: `submissions.csv` (le submission complete di chi ha acconsentito alla pubblicazione) + `stats.json` e `supporters.json` (aggregati) |
| [`DATA/schema.md`](DATA/schema.md) | Il contratto delle colonne del CSV — il notebook ci fa affidamento |

## 🛡 Privacy e licenze

- **Dati**: [CC BY 4.0](LICENSE) — puoi riusarli, citando MFF OpenScience Validation
- **Codice (notebook, scripts)**: [MIT](LICENSE-CODE) — riutilizzabile liberamente
- **Email submitter**: **mai pubblicata**, qui dentro non compare in nessun file. È conservata nel database MFF, perché serve per tre cose concrete: mandarti il link di conferma, accreditarti i crediti e cancellare i tuoi dati se lo chiedi. Nel dataset pubblico compare solo il suo **hash SHA-256**, che permette di riconoscere due submission della stessa persona senza sapere chi sia. Puoi chiederne la cancellazione in qualsiasi momento (vedi [Privacy](https://marcofly.app/privacy)) — e la cancellazione **toglie anche le tue submission da questo repo**, al primo aggiornamento successivo
- **Testo delle risposte AI**: pubblicato in `submissions.csv` **solo** se hai spuntato il consenso alla pubblicazione. Senza quel consenso la submission conta nelle statistiche ma non finisce nel dataset
- **Nickname**: pubblicato solo con l'opt-in esplicito nel form

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
3. **Quality control**: filtri anti-spam (rate limit + [Cloudflare Turnstile](https://www.cloudflare.com/products/turnstile/) + revisione manuale di ogni submission prima dell'accredito). Le submission marcate come sospette sono escluse dall'analisi finale.
4. **Chi valuta è chi ha scelto i due output.** Il voto 1-5 lo dà la stessa persona che ha lanciato i due modelli, e sa quale dei due è MFF: non è un confronto in cieco. La [`RUBRIC.md`](RUBRIC.md) serve a rendere il criterio uniforme, non a togliere questo limite.
5. **N campione**: con 5 submission/giorno servono ~2 mesi per N=300 (effect size moderato).

Questi limiti li discutiamo apertamente nel report finale.

---

> *MarcoFLY Framework — Find · Leader · In · You*
> *© 2026 Marco Motta · Sito CC BY-NC-ND 4.0 · Framework MFF Proprietary License 1.0*
> *Validation project dati e codice: CC BY 4.0 + MIT.*
