# Feedback Test delle Emozioni

Raccolta dei risultati ottenuti dai tester della web app di profilazione emotiva.
Ogni voce contiene il messaggio copiato dal tester + eventuali note qualitative raccolte a voce.

---

## Tester

<!-- Aggiungere nuovi tester sopra, più recenti in alto -->

### Stefania, 45-60, donna (21/4/2026)

**Aree emerse:** 🌊 Acqua profonda · 💃 Corpo vivo · 🔥 Fuoco sociale

**Spunti valutati (20):**
- 12 mi rappresentano
- 5 indifferenti
- 3 non sono miei

**Spunti rifiutati (senza motivazione):**
- Pioggia
- Nebbia
- Odore della pioggia

**Mi riconosco in generale:** sì, molto

**Manca:** niente segnalato

#### Note qualitative

- **Tripletta "acquatica" rifiutata in blocco** (Pioggia, Nebbia, Odore della pioggia): Stefania ha Acqua profonda come cluster dominante ma rifiuta le 3 ancore atmosferiche/meteo del cluster. Legge il "liquido" come mare/corpo/immersione, non come meteo malinconico. Conferma l'intuizione post-Mattia: i cluster hanno **sotto-ramificazioni** che l'algoritmo non distingue (qui: acqua-elemento vs acqua-meteo).
- **Primo caso di rifiuto coerente per sotto-categoria senza motivazione scritta**: la categoria meteo-grigio ("pioggia", "nebbia") attiva un rifiuto nettissimo (probabile associazione con umore basso o stagione pesante). Ancore candidate a review: valutare se spostare Pioggia/Nebbia/Odore pioggia in un sotto-cluster separato "acqua-atmosferica" opzionale, lasciando in dominante le ancore marine/corporee.
- **Riconoscimento "sì molto"** nonostante i 3 rifiuti: il 60% di match sulle ancore dominanti risulta comunque appagante quando il cluster emotivo di appartenenza è riconosciuto. Segnale che il problema di Mattia (riconoscimento "in parte") non è il tasso di rifiuto in sé, ma il mismatch sulle ancore centrali del cluster.
- **Nessun "manca"**: coerente con il match forte sul vocabolario proposto.

### Mattia, 45-60, uomo (21/4/2026)

**Aree emerse:** 🎨 Creazione viva · 🏔 Anima selvatica · 🔥 Fuoco sociale

**Spunti valutati (20):**
- 12 mi rappresentano
- 4 indifferenti
- 4 non sono miei

**Spunti rifiutati (con motivazione):**
- **Scultura** — "la scultura non mi ha mai generato forti emozioni. È una forma espressiva di arte che non riesco ad apprezzare"
- **Teatro** — "Lo trovo finto. Io amo il reale"
- **Poesia** — "La poesia è una forma di scrittura, che, un po' come il teatro, trovo artefatta"
- **Colori vividi** — "Amo i chiaroscuri, il desaturato, il nero"

**Mi riconosco in generale:** in parte

**Manca:** "il deserto. Nulla come il deserto al tramonto mi genera pace"

#### Note qualitative

- **Primo tester con riconoscimento "in parte"** (non "sì molto" come Chiara ed Elena). Segnale importante: il match rate del 60% (12/20 rappresentative) è inferiore ai precedenti, e lui stesso lo registra come parziale.
- **I 4 rifiuti sono *tutti* ancore del cluster Creazione viva** (Scultura, Teatro, Poesia, Colori vividi). Mattia HA il cluster Creazione viva come dominante, ma **rifiuta 4 delle ancore più caratteristiche di quel cluster**. Paradosso apparente che rivela un pattern interessante:
  - Il cluster "Creazione viva" contiene stili espressivi molto eterogenei (arti figurative, arti performative, scrittura creativa, ecc.)
  - Mattia è creativo ma ama il **reale**, non l'artefatto; ama il **chiaroscuro** non il saturo
  - Non c'è problema di matching cluster → problema di **granularità dentro il cluster**
- **Campo "perché" finalmente in azione con motivazioni estetiche**, non solo avversione sensoriale (come i libri/muffa di Chiara). Il dato qualitativo raccolto è *ricchissimo* per il dataset: non "Mattia rifiuta Poesia" ma "Mattia rifiuta Poesia per preferenza per il reale vs artefatto". Conferma definitiva dell'utilità del campo.
- **Manca "il deserto al tramonto"** — terza richiesta consecutiva di scena compound (deserto + tramonto, entrambe già ancore singole). 3/3 tester chiedono scene composte.
- **Messaggio post-test di Mattia:** *"attenzione perché io sono il re delle contraddizioni. Adoro il deserto al tramonto col vento nei capelli, e lo stadio con 90mila persone"*. Analisi:
  - La "contraddizione" che rivendica è in realtà **già catturata dal sistema**: Anima selvatica + Fuoco sociale sono i poli opposti del wheel dei cluster, e lui li ha entrambi nel top 3. Il sistema multi-cluster funziona proprio per questi profili.
  - Sottotesto: **rivendicazione identitaria** tipica degli analitici — *"non ridurmi a una categoria"*. Segnale che alla fine del quiz servirebbe un messaggio UX esplicito che disinneschi preventivamente questa reazione (tipo: *"questo profilo non ti definisce, è solo un vocabolario da cui gli script pescheranno — comprese le tue contraddizioni"*).
  - Anche qui, **entrambi i momenti citati sono scene compound**: "deserto al tramonto col vento nei capelli" (deserto + tramonto + vento) e "stadio con 90mila persone" (concerto in piazza + folla). 4/4 conferme del pattern compound.

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

### Pattern emergenti (aggiornato 21/4/2026, dopo 3 tester reali)

**1. Tutti e 3 i profili naturali hanno dato 3 cluster dominanti.**
- Chiara: contemplativa + spirituale + stupore
- Elena: selvatica + radicante + corpo
- Mattia: creazione + selvatica + sociale

Un test artificioso fatto internamente (forzando risposte "social") ha dato solo 2 cluster → la soglia score ≥3 sta filtrando correttamente. Conferma: **profili umani autentici hanno sempre sfaccettatura sufficiente per restituire 3 cluster**. Se un tester reale dà 2 cluster, annotarlo come caso peculiare (profilo monolitico o compilazione strategica).

**2. Ancora mancante: pattern "scena compound" CONFERMATO su 3/3 tester.**
- Chiara: *"Il vento forte sul mare"* (vento forte + mare aperto)
- Elena: *"Corsa su strada in solitaria all'alba con il silenzio della città che ancora dorme"* (corsa + alba + città all'alba + silenzio)
- Mattia: *"Il deserto al tramonto"* (deserto + tramonto)

Pattern *solidissimo* ora. Gli utenti **non pensano in ancore atomiche** — pensano in **scene narrative** composte. Il dataset atomico non raccoglie questo livello di specificità emotiva.

**Implicazioni (priorità alzata):**
- **Urgente**: priorità massima alla feature "aggiungi ancora custom" — 3 tester su 3 l'avrebbero usata
- **Breve termine**: valutare se aggiungere 20-30 "scene compound" di alto valore al dataset (es. "mare in tempesta", "bosco all'alba", "città deserta di notte", "deserto al tramonto", "corsa all'alba") come nuovo tipo di ancora `type: 'scene'`
- **Medio termine**: il prompt di generazione AI può essere istruito a ricombinare ancore atomiche in scene — ma richiede prompt engineering dedicato

**3. Match rate variabile (50-70%), correlato al riconoscimento soggettivo.**
- Elena: 70% + "sì, molto"
- Chiara: 50% + "sì, molto"
- Mattia: 60% + "in parte"

Interessante: il match rate in sé non predice il riconoscimento. Mattia ha un match rate intermedio (60%) ma si riconosce solo "in parte" — segnale che non è il numero delle ancore che contano, ma la **qualità semantica** del match.

**4. Nuovo pattern: granularità insufficiente dentro alcuni cluster (emerso da Mattia).**
Mattia ha il cluster **Creazione viva** come dominante MA rifiuta 4 delle sue ancore più caratteristiche (Scultura, Teatro, Poesia, Colori vividi) con motivazioni estetiche esplicite ("amo il reale, non l'artefatto"; "amo i chiaroscuri, non il saturo").

Il cluster Creazione viva raggruppa stili espressivi **troppo eterogenei** — include arti figurative realistiche e stilizzate, arti performative, scrittura creativa, colori. Un utente può essere creativo ma avere una forte preferenza per un sotto-tipo di creazione e rifiutare le altre.

**Ipotesi:** servirebbe una sotto-dimensione (realistico vs artefatto, minimale vs esuberante) che oggi non è catturata. Da approfondire se emerge in altri tester.

**5. Il campo "perché" sui rifiuti è uno strumento potentissimo di analisi (confermato 2/3 tester hanno motivato).**
- Chiara: avversione sensoriale personale (olfatto → muffa)
- Mattia: preferenze estetiche dichiarate (reale vs artefatto, chiaroscuro vs saturo)

Queste due classi di rifiuto sono **completamente diverse**:
- **Personali non generalizzabili** → l'ancora è OK nel dataset, problema individuale
- **Estetiche dichiarate** → potrebbero rivelare un gap nella tassonomia dei cluster

Senza il campo "perché" avremmo solo dati quantitativi binari (rifiuta/non rifiuta); con, abbiamo i *livelli* di rifiuto.

**6. Bug copia su Android Chrome (Elena, 21/4 — fixato).**
`navigator.clipboard.writeText()` non funzionava silenziosamente. Fix: strategia execCommand-first + user-select:all come fallback + feedback bottone "✓ Copiato!" al posto di alert. Da monitorare sui prossimi tester Android/iOS.

**7. Rivendicazione identitaria post-test (da Mattia, 21/4).**
Dopo aver ricevuto il profilo, Mattia ha scritto *"attenzione perché io sono il re delle contraddizioni"*. È un pattern prevedibile tra utenti analitici e auto-consapevoli: la reazione al risultato è "non ridurmi a categoria".

Ironicamente, la contraddizione che rivendica (deserto solitario + stadio con folla) **è proprio ciò che il sistema ha catturato** (Selvatica + Sociale, poli opposti nel top 3). Il problema non è la profilazione, è la **comunicazione del risultato**.

**Implicazione UX (da implementare in futuro):** alla fine del quiz, messaggio esplicito che disinneschi preventivamente questa reazione. Esempio:

> *"Questo profilo non ti definisce: è un vocabolario di immagini da cui gli script pescheranno per risuonare con te. Puoi essere contemplativo e ribelle, solitario e sociale, analitico e sensuale — le tue contraddizioni fanno parte del profilo, non lo rompono."*

Questa comunicazione educa il tester a vedere il risultato come **strumento non etichetta**, riducendo la reazione di auto-difesa identitaria che è più probabile in utenti analitici.

### Ancore candidate a review (dopo più tester)

Queste ancore hanno ricevuto almeno 1 rifiuto con motivazione estetica/semantica (non solo avversione personale). Non sono ancora da rimuovere, ma **da tenere d'occhio**:

| Ancora | Tester | Motivazione | Tipo |
|---|---|---|---|
| Odore di vecchi libri | Chiara | Ricorda muffa | personale (no action) |
| Scultura | Mattia | Non emoziona | estetica (osservare) |
| Teatro | Mattia | Artefatta | estetica (osservare) |
| Poesia | Mattia | Artefatta | estetica (osservare) |
| Colori vividi | Mattia | Preferenza chiaroscuro | estetica (osservare) |

Se emergono pattern simili su 3+ tester diversi, considerare revisione del cluster Creazione viva.
