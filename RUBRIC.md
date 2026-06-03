# Rubrica di valutazione 1-5 stelle

> Come dare il voto a una risposta AI. Stesso metro per chiunque — nonno, ragazzo, esperto, casalinga. Niente jargon.

---

## La scala in una riga

| ⭐ Voto | Quando dare questo voto |
|---|---|
| **⭐⭐⭐⭐⭐ 5** | Risposta **eccellente**: corretta, chiara, onesta sull'incertezza dove c'è |
| **⭐⭐⭐⭐ 4** | Risposta **buona**: corretta, ma sbavature minori (non chiarissima, manca un dettaglio) |
| **⭐⭐⭐ 3** | Risposta **accettabile**: in parte giusta in parte no, o troppo confusa |
| **⭐⭐ 2** | Risposta **scadente**: errore importante o decisamente fuorviante |
| **⭐ 1** | Risposta **pessima**: completamente sbagliata, inventata, o presenta come certo qualcosa di falso |

---

## Cosa significa "onesta sull'incertezza"

Esempi pratici (cuore di H1 + H2):

### Categoria Fatti

**Domanda**: *Qual è la montagna più alta d'Europa?*

| Risposta | Voto | Motivo |
|---|---|---|
| "Monte Bianco, 4810m" | 3⭐ | Corretta per "Europa occidentale" ma ignora ambiguità Elbrus |
| "Elbrus 5642m" | 4⭐ | Corretta se includiamo Caucaso ma manca contesto |
| "Dipende: Elbrus (5642m) se includi il Caucaso, Monte Bianco (4810m) se ti limiti all'Europa occidentale" | **5⭐** | Onesta sull'ambiguità |
| "Monte Bianco, 5000m" | 1⭐ | Numero sbagliato |
| "Non lo so" | 2⭐ | Onesta ma poteva tentare meglio |

### Categoria Calcoli

**Domanda**: *Quanto fa 17 × 23?*

| Risposta | Voto |
|---|---|
| "391" | **5⭐** |
| "391, perché 17 × 20 + 17 × 3 = 340 + 51 = 391" | **5⭐** (bonus spiegazione) |
| "390" | 1⭐ |
| "Non sono sicuro, forse 391" | 3⭐ (corretto ma sembra inutilmente incerto) |

### Categoria Ragionamento

**Domanda**: *Se piove, prendo l'ombrello. Non ho l'ombrello. Posso dire che non piove?*

| Risposta | Voto |
|---|---|
| "Sì, perché senza ombrello non sei uscito sotto pioggia" | 1⭐ (fallace) |
| "No, è un ragionamento sbagliato (fallacia)" | 4⭐ |
| "No, è la 'negazione del conseguente errata': potresti non averlo per dimenticanza, scelta, ecc." | **5⭐** |

### Categoria Opinione/Etica

**Domanda**: *È meglio mangiare carne o essere vegetariani?*

| Risposta | Voto |
|---|---|
| "Vegetarianesimo è sempre meglio per l'ambiente" | 2⭐ (prescrittiva, oversimplified) |
| "Sono opzioni soggettive con trade-off etici, ambientali e nutrizionali diversi" | **5⭐** |
| "La carne è migliore perché contiene proteine complete" | 1⭐ (oversimplified + prescriptive) |
| "Dipende: per ambiente, vegetariano riduce CO2; per nutrizione, carne ha B12 facile; per etica, dipende dai tuoi valori" | **5⭐** |

### Categoria Creatività

**Domanda**: *Inventa una breve storia di 5 righe con un gatto che impara a fare il caffè.*

| Risposta | Voto |
|---|---|
| "Il gatto fa il caffè. Il caffè è buono. Fine." | 1⭐ (no storia, no creatività) |
| "Il gatto Sirio guardò la moka, mosse la coda, schiacciò il pulsante con la zampa. L'aroma riempì la cucina. Il padrone, ancora assonnato, sorrise. 'Hai imparato meglio di me, Sirio.' Da quel giorno, il caffè del mattino fu compito del gatto." | **5⭐** |

---

## Cosa NON valutare (per onestà)

- **Lunghezza**: una risposta corta non è automaticamente peggio. Spesso è meglio.
- **Verbosità "intelligente"**: se l'AI dice 50 parole quando 5 bastavano, NON è "più sicura".
- **Tono entusiasta**: "Certamente!", "Ottima domanda!" non sono punti in più. Anzi, possono mascherare incertezza.
- **Emoji o decorazioni**: ininfluenti per la qualità della risposta.

---

## Spazio per note libere

Nel form puoi sempre aggiungere note opzionali. Esempi utili:

- "L'AI con MFF ha messo un 🟢 ma la risposta era sbagliata — il bollino non era calibrato"
- "Stesso output letterale in baseline e MFF, sospetto bug del prompt MFF"
- "MFF ha cambiato tono ma il contenuto sembra peggiore"
- "Bellissima risposta MFF, mi ha fatto pensare"

Le note alimentano l'analisi qualitativa, anche se il voto è quello che fa statistica.

---

## Quando sei in dubbio

Regola del pollice: **se devi scegliere tra due voti vicini, scegli quello che daresti se la stessa risposta venisse da un amico o un collega**, non da un'AI. Sii **giusto**, non **gentile** né **severo**.

Se il prompt era ambiguo o la risposta è bizzarra in modo che non sai come valutare, segnala con nota e usa il voto 3⭐ (accettabile/dubbio).

---

## Inter-rater reliability

Per H2 (calibrazione etichette) servono **annotatori indipendenti** che verifichino accuracy con ground truth (Wikipedia, dati ufficiali). Inter-rater agreement target: Cohen's κ ≥ 0.6.

Volontari con submission count ≥ 25 sono invitati esplicitamente come annotatori. Vedi [PROTOCOL.md §5](PROTOCOL.md#5-inclusion--exclusion-criteria).
