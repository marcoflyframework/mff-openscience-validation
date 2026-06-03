# PROTOCOL — MFF OpenScience Validation

> Disegno sperimentale completo, registrato su [OSF 9ehgx](https://osf.io/9ehgx/) prima della raccolta dati. Modifiche al protocollo dopo l'apertura raccolta saranno tracciate come "Protocol Amendments" pubbliche.

---

## 1. Domanda di ricerca

**Il MarcoFLY Framework (MFF-EX) — un protocollo di prompt engineering basato su etichette epistemiche e anti-circolarità — migliora l'accuratezza e l'onestà epistemica delle risposte AI rispetto ai prompt vanilla?**

Sottodomande:
- Le etichette emesse dall'AI sotto MFF sono calibrate con accuracy reale?
- L'effetto è lingua-agnostico (IT/EN)?
- L'effetto è modello-agnostico (Claude/GPT/Gemini/Llama)?
- MFF degrada task semplici (regression check)?

---

## 2. Disegno sperimentale

**Within-subject crowdsourced human evaluation**, due gruppi:
- **Trattamento**: prompt con MFF system prompt iniettato
- **Controllo**: stesso prompt SENZA MFF (vanilla)

Ogni volontario contribuisce con submission: stesso prompt random somministrato a 2 AI a sua scelta (una vanilla, una MFF), valutazione qualitativa 1-5 stelle.

### Variabili indipendenti (manipolate)
- `mff_used`: boolean (true/false)
- `prompt_id`: identificatore prompt (da Prompt Bank, 100 prompt curati in 5 categorie)
- `ai_provider`: stringa (Claude, ChatGPT, Gemini, Llama-based, ecc.)
- `language`: IT / EN (utente sceglie)

### Variabili dipendenti (misurate)
- `rating_baseline`: 1-5 stelle (community judge giudizio risposta SENZA MFF)
- `rating_mff`: 1-5 stelle (community judge giudizio risposta CON MFF)
- `output_baseline`, `output_mff`: testo libero per analisi qualitativa post-hoc

### Variabili derivate
- `delta`: rating_mff − rating_baseline
- `category`: derivata da prompt_id (fatti, calcoli, ragionamento, opinione, creatività)

---

## 3. Power analysis

Assumendo:
- Effect size minimo rilevabile: **Cohen's d = 0.3** (effetto moderato)
- Alpha = 0.05 (two-tailed)
- Power = 0.80

**N richiesto = 175 per H1** (test single-pair).
Per le 5 ipotesi con correzione Bonferroni → **N = 300** per coprire tutte.
Goal sicurezza: **N = 1000** per power sufficiente anche su sottogruppi (modelli singoli, categorie singole).

---

## 4. Analisi statistiche

### Per H1 (riduzione hallucinazioni)
Mann-Whitney U test su rating_baseline vs rating_mff sulla categoria "Fatti incerti".
Effect size: Cohen's d. Bootstrap CI 95%.

### Per H2 (calibrazione etichette)
Estrazione automatica del bollino 🟢/🔵/🟡/🔴 dall'output_mff via regex.
Ground truth verificata da annotatori (almeno 3 indipendenti).
Calcolo Expected Calibration Error (ECE) per bin di confidenza.

### Per H3 (no regression)
Mann-Whitney U su categorie "Creatività" + "Calcoli semplici".
Equivalence testing (TOST) con bound ±0.2 stelle.

### Per H4 (lingua-agnostico)
ANOVA two-way (mff_used × language) sul rating.
Interaction term: se p > 0.05 → no interazione → H4 supportata.

### Per H5 (AI-agnostico)
Linear mixed-effects model con `ai_provider` random effect.
Variance ratio across provider → H5 supportata se < 0.2.

### Correzione multi-comparazione
Benjamini-Hochberg FDR su 5 ipotesi principali + sottoanalisi.
Alpha effettivo per ipotesi: 0.01.

---

## 5. Inclusion / exclusion criteria

### Inclusi nell'analisi
- Submission con email validata (link Resend cliccato)
- Output_baseline e output_mff entrambi ≥ 20 caratteri
- Rating_baseline e rating_mff entrambi forniti (1-5)
- Submission non flaggata come spam dall'admin review

### Esclusi
- Submission da IP con > 50 contributi in 24h (rate limit anti-spam)
- Output_baseline == output_mff letterale (copia-incolla sospetta)
- Output_baseline o output_mff contenenti spam/profanità rilevati da filtri
- Submission con commento "non capivo cosa fare" o equivalente
- Submission dopo data taglio analisi pubblicata

### Annotatori
Per H2 (calibrazione) servono **annotatori indipendenti** (≥ 3) che verifichino accuracy della risposta vs ground truth. Selezione: volontari con submission count ≥ 25 (livello 🥇) invitati esplicitamente. Inter-rater agreement (Cohen's κ ≥ 0.6) richiesto.

---

## 6. Open data e riproducibilità

- **Submissions** pubblicate in `DATA/submissions.csv` (anonymized: hash email, no IP) aggiornate via GH Action ogni 24h
- **Stats aggregate** in `DATA/stats.json`
- **Analysis notebook** [`ANALYSIS.ipynb`](ANALYSIS.ipynb) riproducibile con `pip install -r requirements.txt` + `jupyter nbconvert --execute`
- **OSF deposit**: snapshot CSV + notebook + report ogni milestone (100, 250, 500, 750, 1000) uploadato manualmente

---

## 7. Privacy & GDPR

| Dato | Finalità | Conservazione | Base legale |
|---|---|---|---|
| `submitter_email` | Validazione + accredito crediti + dedup | 12 mesi poi anonymized | Esecuzione contratto (volontariato + reward) |
| `nickname` | Pagina Supporter (solo se opt-in) | Fino a revoca | Consenso esplicito |
| `output_baseline`, `output_mff` | Analisi statistica | Indefinita (pubblicato come open data) | Consenso esplicito + interesse legittimo ricerca |
| `ip_hash` | Anti-spam, rate limit | 30 giorni | Interesse legittimo sicurezza |
| `ai_model`, `category`, `rating_*` | Analisi | Indefinita | Consenso esplicito |

Tutti i submitter devono confermare consenso esplicito al momento della submission. Email verification obbligatoria (link Resend).

GDPR Right to be Forgotten: submission cancellabile su richiesta a `privacy@marcofly.app` con citazione hash submission. Dati già pubblicati in CSV verranno anonimizzati in 30 giorni dalla richiesta.

---

## 8. Quality assurance

### Anti-spam
- reCAPTCHA v3 invisible (score < 0.5 → flag manual review)
- Rate limit IP: max 50/giorno, max 5/ora
- Email verification (link cliccato entro 24h)
- Manual review admin su flag automatici

### Honesty check
- Random spot check da admin: re-eseguire prompt e confrontare con submission
- Disclosure obbligatorio: submitter dichiara di aver effettivamente eseguito i prompt (checkbox + audit log)

### Bias mitigation
- Inviti espliciti a critici via post su social ("Pensi MFF non funzioni? Aiutaci a dimostrarlo!")
- Note libera per disaccordo registrata
- Pre-registration su OSF prima della raccolta dati: niente p-hacking, niente HARKing

---

## 9. Stopping rules

L'analisi finale sarà eseguita e pubblicata quando si raggiunge **N = 1.000 submission valide**.

Analisi parziali intermedie a milestone 100, 250, 500, 750 sono **descrittive** (no test statistici, no claim di significatività). Servono per monitoring e community engagement.

Se dopo 6 mesi N < 300, il progetto viene riconsiderato (eventuale revisione protocollo con pre-registration amendment su OSF).

---

## 10. Reporting

Report finale (pubblicato in `REPORT.md` + uploadato su OSF):
- Tutti i risultati H1-H5 con effect size + CI 95%
- Sub-analisi per modello AI, lingua, categoria prompt
- Discussione limiti (selection bias, sample composition, ecc.)
- Open data + open notebook per replica

In caso di rigetto di una ipotesi: **lo diciamo apertamente**. Non c'è "spin", non c'è "cherry picking". Se MFF non funziona per H1 ma funziona per H3, scriviamo entrambi.

---

## Amendments

Modifiche al protocollo dopo l'apertura della raccolta dati saranno tracciate qui con data e motivazione.

Nessun amendment al 2026-06-03.
