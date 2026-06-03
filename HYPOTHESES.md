# Ipotesi falsificabili — MFF Validation

> Ogni ipotesi è formulata in **due livelli**: linguaggio quotidiano (chiunque) e linguaggio tecnico (chi vuole replicare l'analisi).

Tutte le ipotesi sono **preregistrate** su OSF prima della raccolta dati. Vedi [osf.io/9ehgx](https://osf.io/9ehgx/).

---

## H1 — Onestà sull'incertezza

### Versione "nonno"
> *Con MFF l'AI mente di meno quando non sa la risposta.*

### Versione tecnica
> MFF riduce significativamente il tasso di hallucinazioni (affermazioni false presentate come certe) su prompt factuali ambigui rispetto al prompt baseline (vanilla).

### Predizione quantitativa
Tasso hallucination MFF < Tasso hallucination baseline, con **effect size ≥ 0.3** (Cohen's d) su sub-categoria "Fatti incerti".

### Cosa la smentirebbe
Se i giudici della community danno rating "AI mente" altrettanto frequentemente con/senza MFF (delta < 0.1 punti su scala 5), H1 è rigettata.

### Categorie prompt rilevanti
- Fatti generali ambigui
- Domande su eventi recenti (post-knowledge-cutoff)
- Citazioni / fonti richieste

---

## H2 — Calibrazione delle etichette

### Versione "nonno"
> *I bollini colorati 🟢🔵🟡 dell'AI dicono davvero quanto è sicura.*

### Versione tecnica
> Le etichette epistemiche emesse dall'AI sotto MFF (🟢 alta confidenza, 🔵 media, 🟡 bassa, 🔴 incerta) correlano con l'accuracy reale verificata della risposta.

### Predizione quantitativa
- Accuracy media risposte 🟢: ≥ 85%
- Accuracy media risposte 🔵: 60-84%
- Accuracy media risposte 🟡: 30-59%
- Accuracy media risposte 🔴: < 30%

Calibrazione misurata con **Expected Calibration Error (ECE) < 0.15**.

### Cosa la smentirebbe
Se le etichette non discriminano (es. accuracy 🟢 ≈ accuracy 🔴), H2 è rigettata.

### Categorie prompt rilevanti
- Fatti verificabili con ground truth (Wikipedia, dati ufficiali)
- Calcoli con risposta unica
- Date / numeri esatti

---

## H3 — Nessuna regressione

### Versione "nonno"
> *MFF non rallenta o peggiora le cose semplici.*

### Versione tecnica
> Su task baseline (riassumere, tradurre, scrivere, brainstorming) MFF preserva la qualità delle risposte rispetto al prompt vanilla (no degradation > 5% sui rating community).

### Predizione quantitativa
Rating medio MFF ≥ (Rating medio baseline − 0.2) sui prompt di categoria "Creatività" e "Calcoli semplici".

### Cosa la smentirebbe
Se MFF rallenta significativamente o peggiora task semplici (es. -1 stella media su rating), H3 è rigettata.

### Categorie prompt rilevanti
- Creatività (storia breve, idee, brainstorm)
- Calcoli semplici (no ambiguità)
- Traduzione / parafrasi

---

## H4 — Lingua-agnostico

### Versione "nonno"
> *MFF funziona uguale in italiano e in inglese.*

### Versione tecnica
> L'effetto MFF (delta rating MFF − baseline) è statisticamente equivalente in italiano e inglese, con delta cross-lingua < 10% del rating baseline.

### Predizione quantitativa
|delta_IT − delta_EN| / |delta_IT| < 10%

### Cosa la smentirebbe
Se MFF migliora le risposte in IT ma non in EN (o viceversa), H4 è rigettata. Suggerirebbe che il framework dipende da artefatti linguistici specifici (es. tokenizer).

### Categorie prompt rilevanti
- Tutti i prompt sono disponibili sia in IT che EN nel Prompt Bank
- Submission richiede di dichiarare la lingua usata

---

## H5 — AI-agnostico

### Versione "nonno"
> *MFF funziona uguale con AI diverse (Claude, ChatGPT, Gemini, Llama, ecc.)*

### Versione tecnica
> L'effetto MFF è generalizzabile across provider AI (OpenAI, Anthropic, Google, Meta, ecc.) con delta cross-provider < 20% del rating baseline.

### Predizione quantitativa
Per ogni coppia di provider (A, B): |delta_A − delta_B| / mean(delta_A, delta_B) < 20%

### Cosa la smentirebbe
Se MFF funziona solo su Claude e non su GPT/Gemini/Llama, H5 è rigettata. Suggerirebbe che il framework è "Claude-specific" e non un protocollo generale.

### Categorie prompt rilevanti
- Tutti i prompt, con submission che richiede di dichiarare il modello AI usato
- Distribuzione bilanciata via gentle nudge nel form

---

## Statistica e analisi

Vedi [PROTOCOL.md](PROTOCOL.md) per:
- Test statistici usati (Mann-Whitney U per non-parametric, bootstrap CI 95%)
- Correzione multi-comparazione (Bonferroni o FDR)
- Effect size minimo rilevabile dato N
- Power analysis (N=300 → 80% power per d=0.3)

Tutto il codice in [ANALYSIS.ipynb](ANALYSIS.ipynb) è eseguibile da chiunque con Jupyter + pandas + scipy. Riproducibilità garantita.
