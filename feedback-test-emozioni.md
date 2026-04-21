# Feedback Test delle Emozioni

Raccolta dei risultati ottenuti dai tester della web app di profilazione emotiva.
Ogni voce contiene il messaggio copiato dal tester + eventuali note qualitative raccolte a voce.

---

## Tester

<!-- Aggiungere nuovi tester sopra, più recenti in alto -->

### Elena — 30-45, donna (21/4/2026)

**Aree emerse:** 🏔 Anima selvatica · 🌿 Terra radicante · 💃 Corpo vivo

**Spunti valutati (20):**
- 14 mi rappresentano
- 6 indifferenti
- 0 non sono miei

**Mi riconosco in generale:** sì, molto

**Manca:** "Corsa su strada in solitaria all'alba con il silenzio della città che ancora dorme"

#### Note qualitative

- **Zero rifiuti** — prima tester con match perfetto sull'intero pool di 20 ancore. Algoritmo ha predetto bene l'intero set per questo profilo.
- **Match rate 70%** (14/20 rappresentative) — superiore a Chiara (50%), indica un profilo molto ben catturato dall'asse selvatica + radicante + corpo (cluster tangibili, "outdoor/grounded").
- **Bug segnalato**: bottone "Copia e incolla su WhatsApp" non copiava nulla sul browser Android di Elena. Fix deployato 21/4/2026: strategia execCommand-first (più compatibile mobile) + feedback visivo sul bottone + `user-select: all` sul box testo come fallback manuale.
- **Manca "Corsa su strada in solitaria all'alba con il silenzio della città che ancora dorme"** — è una scena compound, combina 4-5 ancore esistenti (Corsa + Alba + Città all'alba + Silenzio + la sfumatura della solitudine). Esattamente come Chiara con "Vento forte sul mare". **Secondo caso consecutivo di richiesta compound** → pattern da prendere sul serio.

### Chiara Zennaro — 45-60, donna (20/4/2026)

**Aree emerse:** 🎭 Estetica contemplativa · 🕯 Spiritualità calma · ✨ Stupore

**Spunti valutati (20):**
- 10 mi rappresentano
- 9 indifferenti
- 1 non è per me

**Spunti rifiutati:**
- Odore di vecchi libri

**Mi riconosco in generale:** sì, molto

**Manca:** "Il vento forte sul mare"

#### Note qualitative (raccolte a voce)

- **Rifiuto "Odore di vecchi libri"** — *non è un errore del test*: Chiara ha un olfatto molto sensibile e l'odore dei libri antichi le ricorda la muffa, che trova sgradevole. L'immagine è semanticamente coerente col suo profilo (contemplativa + spirituale), ma viene filtrata da un'avversione sensoriale personale.
  - **Implicazione:** conferma l'utilità del campo "motivo" opzionale sul ❌. Senza quella nota avremmo classificato l'immagine come "da rivedere" nel dataset, mentre il problema è individuale.
- **Manca "Il vento forte sul mare"** — interessante, perché combina due ancore già presenti (`Vento forte` + `Mare aperto`) in un'immagine unica più evocativa. Valutare se aggiungere alcune combinazioni "di scena" al dataset.
- **Riconoscimento "sì, molto"** conferma che per profili coerenti (3 cluster ben definiti) il matching funziona.

---

## Note trasversali

### Pattern emergenti (aggiornato 21/4/2026, dopo 2 tester reali)

**1. Entrambi i profili naturali hanno dato 3 cluster dominanti.**
Chiara (contemplativa + spirituale + stupore) ed Elena (selvatica + radicante + corpo) entrambe con 3 cluster. Un test artificioso fatto internamente (forzando risposte "social") ha dato solo 2 cluster, in corretto funzionamento della soglia score ≥3. Conferma: profili umani autentici hanno sempre sfaccettatura sufficiente per restituire 3 cluster. **Se un tester reale dà 2 cluster, annotarlo come caso peculiare** (profilo monolitico o compilazione strategica).

**2. Ancora mancante: pattern "scena compound" (2/2 tester).**
- Chiara: *"Il vento forte sul mare"* (combina 2 ancore esistenti: vento forte + mare aperto)
- Elena: *"Corsa su strada in solitaria all'alba con il silenzio della città che ancora dorme"* (combina 4-5 ancore: corsa + alba + città all'alba + silenzio)

Gli utenti **non pensano in ancore atomiche** — pensano in **scene narrative** composte. Il dataset attuale ha unità atomiche (mare, vento, alba, corsa); gli utenti chiedono COMBINAZIONI specifiche che evocano un momento preciso.

**Implicazioni:**
- **Breve termine**: alla feature "aggiungi ancora custom" già in roadmap va data priorità alta — gli utenti vogliono esprimere combinazioni personali
- **Medio termine**: valutare se aggiungere 15-20 "scene compound" di alto valore al dataset (es. "mare in tempesta", "bosco all'alba", "città deserta di notte") come nuovo tipo di ancora `type: 'scene'`
- **Lungo termine**: l'AI di generazione script può ricombinare le ancore in scene — ma richiede prompt engineering dedicato

**3. Match rate alto (50-70%) quando il profilo è coerente.**
Nessun tester ha avuto match rate <50%. Conferma che l'algoritmo scoring + top 20 selection funziona bene per profili naturalmente sfaccettati.

**4. Bug copia su Android (21/4/2026 — fixato).**
`navigator.clipboard.writeText()` non funzionava silenziosamente sul browser Android di Elena. Fix: strategia execCommand-first + user-select:all come fallback + feedback bottone "✓ Copiato!" al posto di alert. Da monitorare sui prossimi tester Android/iOS per confermare.
