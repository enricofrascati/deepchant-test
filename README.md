# DeepChant — Test profilazione emotiva

Web app single-file per validare il sistema di cluster emotivi prima dell'integrazione in DeepChant.

## Cos'è

Un quiz di 6 domande che profila l'utente su 10 **cluster emotivi archetipici**, gli propone 20 ancore emotive coerenti con il suo profilo, e raccoglie feedback su quanto quelle ancore lo rappresentano davvero.

Obiettivo: testare il sistema su 30-50 persone prima di cementarlo nell'app.

## Cosa c'è dentro

- `index.html` — **l'intera web app** (HTML + CSS + JS + dataset). Un solo file, zero dipendenze, funziona offline.
- `README.md` — questo documento.

## Test in locale (provare subito)

```bash
cd "/Users/enricof/Dropbox/_02 PERSONALI/_PROGETTI APP/deepchant-test-web"
open index.html
```

Oppure: doppio-click sul file `index.html` dal Finder → si apre nel browser.

## Deploy pubblico

### Opzione 1 — Netlify Drop (più veloce, 30 secondi)

1. Vai su https://app.netlify.com/drop
2. Trascina `index.html` sulla pagina
3. Netlify ti dà un URL tipo `https://random-name-123.netlify.app`
4. Condividi il link via WhatsApp

**Pro:** zero account richiesto per il test iniziale, istantaneo.
**Contro:** URL brutto, temporaneo (sparisce dopo 24h se non hai account).

### Opzione 2 — Netlify con account (permanente)

1. Crea account gratuito su https://netlify.com
2. "Add new site" → "Deploy manually" → trascina `index.html`
3. Rinomina il subdomain in qualcosa tipo `deepchant-test`
4. URL finale: `https://deepchant-test.netlify.app`

### Opzione 3 — GitHub Pages

Se hai già un account GitHub:

```bash
cd "/Users/enricof/Dropbox/_02 PERSONALI/_PROGETTI APP/deepchant-test-web"
git init
git add index.html README.md
git commit -m "DeepChant emotional cluster test v1"
# crea repo vuoto su github.com chiamato "deepchant-test"
git remote add origin https://github.com/enricofrascati/deepchant-test.git
git branch -M main
git push -u origin main
# poi su github.com → Settings → Pages → Source: main branch
```

URL finale: `https://enricofrascati.github.io/deepchant-test`

## Come raccogli i risultati

Il sistema attuale usa **copia-incolla**: quando l'utente finisce il test, clicca "📋 Copia e incolla su WhatsApp" e ti manda il risultato direttamente su chat.

Riceverai un messaggio formattato così:

```
*Test DeepChant — risultati*

Cluster emersi: 🏔 Anima selvatica, 🕯 Spiritualità calma, ✨ Stupore

Ancore: 12 risuonanti · 5 indifferenti · 3 non mie
Riconoscimento: si
Manca: Il profumo di resina quando cammino in montagna

---
DATI COMPLETI (JSON):
```
{ ... JSON strutturato ... }
```
```

I dati completi in JSON li trovi in fondo, li copi e incolli in un file per l'analisi successiva.

### Upgrade futuro — Formspree (raccolta automatica)

Se il test va bene e vuoi raccogliere i dati in automatico senza scocciare il tester:

1. Crea account su https://formspree.io
2. Crea un nuovo form, prendi l'endpoint (tipo `https://formspree.io/f/xabc1234`)
3. Apri `index.html`, cerca la funzione `finalizeResults()` e aggiungi dopo `showScreen('screen-done')`:

```javascript
fetch('https://formspree.io/f/xabc1234', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json', 'Accept': 'application/json' },
  body: JSON.stringify(payload)
}).catch(() => {}); // fail silently
```

4. Rideploya. Da quel momento ogni test ti arriva via email automaticamente.

**Piano gratuito Formspree:** 50 submission/mese. Più che sufficiente per la fase di test.

## Cosa analizzare dai risultati

Per ogni risposta ricevuta guarda:

### Validazione del matching

- Percentuale di ancore "risuonanti" su totale 20 → obiettivo: **>60%** risuonanti
- Percentuale di "non mie" → se >15%, il matching sta scartando male oppure sovraincludendo
- Pattern: ci sono ancore specifiche sempre indifferenti/non mie? Potrebbero essere mal categorizzate

### Riconoscimento cluster

- "I cluster emersi ti rappresentano?" → cerca >70% di Sì o In parte
- Se molte persone dicono No: le domande del quiz non discriminano bene, o i cluster sono sbagliati

### Ancore mancanti

- Raccogli tutte le risposte al campo "ancora mancante"
- Se emergono ancore ricorrenti che non hai nel dataset, aggiungile
- Se emergono categorie nuove che non hai nei cluster, rivedi la tassonomia

### Distribuzione cluster

- Quali cluster sono sempre dominanti? Quali mai? Se un cluster non emerge mai, il quiz non lo misura bene
- Su 30 test, se "Creazione viva" non esce mai come top-3, devi potenziare le opzioni che puntano a quel cluster

## Iterazione

1. Raccogli 10-15 risposte
2. Analizza con i criteri sopra
3. Aggiorna `index.html`:
   - Modifica le domande che discriminano male
   - Riassegna ancore male categorizzate
   - Aggiungi ancore mancanti dal feedback
4. Rideploya (su Netlify: trascina di nuovo, su GitHub Pages: push)
5. Raccogli altri 15-20 test sulla nuova versione
6. Confronta se i tassi di "risuonanti" e "riconoscimento" sono migliorati

## Schema dati

Ogni risposta restituisce un JSON come:

```json
{
  "timestamp": "2026-04-17T10:30:00Z",
  "quiz_answers": [
    { "q": 1, "option": "Cima di montagna al tramonto, da solo" },
    { "q": 2, "option": "Camminare in un bosco, respirare" },
    { "q": 3, "option": "Il silenzio: ti siedi, chiudi gli occhi" },
    { "q": 4, "option": "Il cielo stellato, l'immensità" },
    { "q": 5, "option": "Al freddo: aria pulita, neve, alta quota" },
    { "q": 6, "option": "Silenzioso: chiudi gli occhi, senti dentro" }
  ],
  "cluster_scores": {
    "selvatica": 6, "contemplativa": 3, "sociale": 0,
    "acquatica": 0, "spirituale": 6, "radicante": 2,
    "corpo": 0, "domestica": 0, "stupore": 4, "creazione": 0
  },
  "dominant_clusters": ["selvatica", "spirituale", "stupore"],
  "anchor_ratings": [
    { "anchor": "Montagna", "rating": "risuona" },
    { "anchor": "Foresta tropicale", "rating": "indifferente" },
    { "anchor": "Bar con gli amici", "rating": "non_mia" }
  ],
  "self_recognition": "si",
  "missing_anchor": "Il profumo di resina in montagna",
  "age_range": "45-60",
  "gender": "m",
  "version": "test-v1"
}
```

## Note tecniche

- **Vanilla HTML/CSS/JS** — nessun framework, nessun build step
- **~1000 righe** totali nel file unico
- **Mobile-first** — testato concettualmente per iOS/Android browser
- **Offline-capable** — apri il file in locale, funziona
- **Dataset inline** — 10 cluster, ~150 ancore, 6 domande con 36 opzioni totali
- **Niente tracking** — nessun analytics, nessun pixel, nessun cookie
- **Accessibilità base** — tap target 44pt, contrasti WCAG, font scalabile dal browser

## Struttura del codice in `index.html`

| Sezione | Righe | Cosa contiene |
|---|---|---|
| `<style>` | ~130 | Tutto il CSS (tema scuro DeepChant) |
| Schermate HTML | ~140 | 6 `.screen` div (welcome, quiz, result, anchors, feedback, done) |
| `CLUSTERS` | ~15 | Dizionario dei 10 cluster |
| `ANCHORS` | ~160 | Array delle ~150 ancore con i loro cluster |
| `QUIZ` | ~80 | Array delle 6 domande con 36 opzioni |
| Funzioni JS | ~300 | Navigation, scoring, matching, rendering, export |

## Prossimi passi suggeriti

- [ ] Test in locale: apri `index.html`, fai il quiz tu stesso, verifica che funzioni
- [ ] Deploy su Netlify Drop per avere un URL da mandare via WhatsApp
- [ ] Manda il link a 5-10 persone nella tua cerchia stretta (prima iterazione)
- [ ] Analizza i primi risultati (criteri sopra)
- [ ] Aggiusta domande/cluster/ancore in base al feedback
- [ ] Rideploya, manda la v2 a una cerchia più ampia (30-50 persone)
- [ ] Quando il tasso di riconoscimento è >70%, il sistema è pronto per essere integrato in DeepChant
- [ ] Porta `CLUSTERS`, `ANCHORS` e `QUIZ` dentro l'app React Native, sostituendo l'attuale `AnchorSelector`

---

**Versione:** test-v1  
**Data creazione:** 17 aprile 2026  
**Autore:** Enrico Frascati (con Claude)
