# Come contribuire al MFF OpenScience Validation

Grazie per voler partecipare. Ogni contributo aiuta la community a capire **se e quanto MFF funziona davvero**.

---

## 🎯 Tre modi di partecipare

### 1. Somministra un test (5 minuti, **non serve essere tecnici**)

Il metodo più diretto. Lo può fare chiunque sappia copiare-incollare.

1. Vai su **[marcofly.app/contribute/time](https://marcofly.app/contribute/time)**
2. Ti viene mostrato un **prompt random** dal Prompt Bank
3. Copialo in DUE AI a tua scelta — **una senza MFF, una con MFF**
   - Esempi AI: ChatGPT, Claude, Gemini, Llama (HuggingFace), Mistral chat, Perplexity
   - Per usare MFF: vai su [app.marcofly.app](https://app.marcofly.app), modalità AUTO o MFF-EX
4. Incolla i due output nel form, dai un **voto 1-5 stelle** a ciascuno (vedi [RUBRIC.md](RUBRIC.md))
5. Submit. Dopo la conferma della tua email e la revisione umana ricevi **crediti MFF gratis** — 100 per la prima submission approvata, poi a scaglioni (50 per la 2ª–3ª, 25 per la 4ª–10ª, 10 dalla 11ª; il saldo non scende mai sotto 100) — e il badge Validator. Dettagli in [README — «Cosa ricevi»](README.md#-cosa-ricevi).

**Tu non devi capire la statistica**. Te ne occupi di una sola cosa: copia-incolla onesto + voto onesto.

---

### 2. Proponi un nuovo prompt (10 minuti, **utile a tutti**)

Pensi che manchi una categoria? Un prompt-trabocchetto interessante?

1. Apri una **[Issue tipo "Prompt Suggestion"](https://github.com/marcoflyframework/mff-openscience-validation/issues/new?template=prompt_suggestion.md)**
2. Compila il template:
   - Testo prompt (IT + EN)
   - Categoria proposta
   - Difficoltà stimata
   - Perché secondo te è utile
3. Discuti in commenti
4. Se accettato, viene aggiunto a [PROMPT_BANK.md](PROMPT_BANK.md) con ID univoco

Criteri di accettazione:
- ✅ Comprensibile a qualunque adulto
- ✅ Non duplicato
- ✅ Non offensivo né politicamente faziato
- ✅ Lingua disponibile sia IT che EN
- ✅ Rubrica chiara di valutazione

---

### 3. Replica l'analisi (30 minuti, **tecnico, opzionale**)

Sei a tuo agio con Python? Aiutaci a verificare l'analisi.

1. Clona il repo: `git clone https://github.com/marcoflyframework/mff-openscience-validation.git`
2. Installa: `pip install -r requirements.txt`
3. Apri [`ANALYSIS.ipynb`](ANALYSIS.ipynb) in Jupyter o VSCode
4. Esegui tutte le celle: `jupyter nbconvert --execute --to html ANALYSIS.ipynb`
5. Confronta i tuoi risultati con quelli pubblicati. Se trovi discrepanze, apri **Issue tipo "Analysis Bug"**.

I dati sono in [`DATA/submissions.csv`](DATA/submissions.csv) (pubblicato dal Worker `mff-cron` ogni notte alle 03:00 UTC, solo se qualcosa è cambiato).

---

## 🚫 Cosa NON fare

- ❌ Inviare submission falsificate (copia-incolla finto, voti random). Sono dannose per la community e violano il [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md). Soggette a rejection + ban.
- ❌ Inviare lo stesso prompt 50 volte per accumulare crediti. Rate limit + manual review intercettano. Soggette a credit clawback.
- ❌ Inviare output offensivi/illegali. Filtri automatici li bloccano. In caso eccezionale, contattare `privacy@marcofly.app`.
- ❌ Modificare i file di analisi nel repo senza PR + discussione. La review è importante per evitare cherry-picking.

---

## 🛡 Privacy

- **Email**: salvata solo per dedup e accredito crediti. Non condivisa. Vedi [Privacy MFF](https://marcofly.app/privacy).
- **Nickname**: pubblicato solo se hai spuntato esplicitamente l'opt-in nel form.
- **Output AI**: pubblicato come open data (CC BY 4.0). Anonimizzato: nessun link diretto a te.
- **IP**: hash conservato 30 giorni per anti-spam, mai pubblicato.

GDPR Right to be Forgotten: scrivi a `privacy@marcofly.app` con hash submission per cancellazione completa.

---

## 🏆 Riconoscimento

Tutti i contributor compaiono in [CONTRIBUTORS.md](CONTRIBUTORS.md) se hanno opt-in. Livelli badge:

| Submission valide | Badge |
|---|---|
| 1+ | 🌱 Validatore |
| 3+ | 🥉 Bronzo |
| 10+ | 🥈 Argento |
| 25+ | 🥇 Oro (può fare annotator review per H2) |
| 50+ | 💎 Diamante (mention nel report finale OSF + invito a co-authorship se sostanziale) |

(Scala identica a quella del sito e del pannello: la stessa persona non può avere due gradi diversi.)

---

## 💬 Domande?

- Apri **[Issue](https://github.com/marcoflyframework/mff-openscience-validation/issues)** su GitHub per discussioni pubbliche
- Email: `privacy@marcofly.app` per privacy e questioni sensibili · `info@marcofly.app` per tutto il resto
- Documentation framework: [marcofly.app/mff](https://marcofly.app/mff)

---

> *Validation è un atto di onestà intellettuale. Ti chiediamo solo questo.*
