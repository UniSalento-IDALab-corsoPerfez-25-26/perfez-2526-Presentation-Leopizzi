# PROGETTO ONEHEALTH — Versione 2

*Qualità dell'aria e mortalità/morbilità respiratoria nel Salento — dashboard di supporto decisionale per presidi medici*

Documento 1 (v2) — Descrizione del Progetto

---

## 1. Informazioni generali

- **Candidato:** Matteo Leopizzi
- **Corso:** Corso di Perfezionamento in Tecnologie Digitali per Ambienti e Sistemi Intelligenti — Università del Salento (IDA Lab)
- **Tipo di elaborato:** Progetto d'esame finale, in collaborazione con azienda partner
- **Azienda partner:** Parsec 3,26 (Lecce) — referente aziendale: Sergio Guglielmi; responsabile risorse umane: Irene Galante
- **Referente accademico IDA Lab:** prof. Luigi Patrono
- **Scadenza:** 17/09/2026 → 24/10/2026 (implementazione tecnica + tesi + presentazione); consegna documentazione finale (tesina, bozza PPT, codice sorgente, Dichiarazione sull'utilizzo dell'IA) entro il 20 novembre 2026 (presentazione finale nella prima settimana di dicembre 2026) —

---

## 2. Perché il cambio di approccio (v1 → v2)

La v1 era centrata su un dispositivo wearable custom (PCB, sensori ambientali/salute/GPS). Il cambio verso un approccio **software-first, senza hardware/sensoristica dedicata**, nasce da due considerazioni:

- **Saturazione dello stato dell'arte hardware:** esistono già prototipi e progetti di riferimento consolidati in quest'area (es. RESPIRO, Univ. Milano-Bicocca) — costruire un ennesimo wearable aggiunge poco valore differenziante.
- **Valore per il destinatario:** una dashboard decisionale, basata su dati pubblici e già esistenti, può supportare più direttamente le scelte di investimento future dei presidi medici/aziende sanitarie e aumentare la consapevolezza dell'utente finale — senza i costi, i tempi e i rischi di sviluppo di un dispositivo fisico.

---

## 3. Obiettivo del progetto

Fornire a **presidi medici e aziende sanitarie pubbliche e private** (chiunque possa usufruire del servizio) uno strumento di supporto al **controllo di gestione**, basato sulla correlazione tra:

- qualità dell'aria in diverse zone del **Salento**, e
- diagnosi/mortalità per patologie respiratorie nelle stesse zone,

per aiutare la pianificazione e le decisioni di investimento sanitario-ambientale. Non è prevista un'interfaccia pubblica separata per il cittadino (decisione 18/09/2026): l'unico output è la dashboard per i presidi medici/aziende sanitarie.

> **Aggiornamento 18/09/2026:** il gap "destinatario finale" è chiuso — target esplicito: presidi medici/aziende sanitarie **pubbliche e private**. Nessuna interfaccia cittadino separata da realizzare.

---

## 4. Architettura del progetto — quattro componenti

### Componente 1 — Acquisizione dati

Raccolta di dati pubblici da fonti istituzionali, senza rilevazione diretta sul campo. Approccio adottato: costruire una lista ampia di archivi/dataset pubblici papabili, poi restringerla con una ricerca dedicata in Fase 2.

**Fonti confermate finora:**
- **ARPA Lecce** — dati ambientali a livello locale/provinciale.
- **ISTAT** — dati su qualità dell'aria e dati sanitari (cause di morte/diagnosi di patologie respiratorie) per zona.
- **OpenAQ**
- **Copernicus/CAMS**
- *(lista aperta — altri archivi pubblici verranno aggiunti durante la ricerca dataset)*

*(Aggiornamento 18/09/2026: la fonte sanitaria indicata a voce come "ESDO" si chiama in realtà **ESDS — European Statistical Data Support**. Nome diverso dall'ipotesi di ricerca (OER Puglia/ASL Taranto): da verificare ente e URL ufficiale prima di costruire la pipeline su questa fonte — v. `03_Ricerca_Dataset_Fase2.md`.)*

**Granularità geografica:** il territorio "Salento" (province di Lecce, Taranto e Brindisi) viene suddiviso in **distretti socio-sanitari** (decisione 18/09/2026, non più "zone" generiche). Per ciascun distretto si registrano il valore/andamento della qualità dell'aria e l'incidenza di patologie respiratorie legate alla qualità dell'aria, per confrontare un distretto con gli altri. I confini di ogni distretto vanno delineati dalle mappe geografiche ASL delle tre province.

**Copertura temporale:** copertura minima **5 anni** (decisione 18/09/2026); resta un obiettivo restare vicini a ~10 anni (2016-2026) se i dati effettivamente disponibili lo permettono.

### Componente 2 — Data engineering e pipeline

- Validazione, pulizia e ottimizzazione dei dati raccolti dalle diverse fonti.
- Ingegnerizzazione della pipeline dati (formati eterogenei da fonti diverse → dataset unificato e coerente per zona geografica).
- Sovrapposizione temporale/geografica tra dati di qualità dell'aria e dati di mortalità/diagnosi respiratoria, per zona del Salento.

### Componente 3 — Mappatura geografica e dashboard

- Mappa interattiva basata su **OpenStreetMap**, con sovrapposizione qualità dell'aria e cause di morte/incidenza respiratoria per zona.
- Dashboard con grafici e visualizzazioni a supporto delle decisioni dei presidi medici (oltre alla mappa: trend, confronti tra zone, indicatori aggregati).

### Componente 4 — Modulo di intelligenza artificiale (LLM locale + RAG)

- LLM open-source **preaddestrato**, eseguito **in locale** su workstation del candidato, senza server aziendale né cloud (decisione 18/09/2026). Nessun training/fine-tuning: il modello risponde solo sulla base dei dataset pubblici raccolti e dei dati elaborati dalla pipeline.
- Architettura **RAG (Retrieval-Augmented Generation)** sui dati raccolti/elaborati (nessun database persistente: accesso dati via chiamate API dirette, v. sezione 6).
- Funzioni previste: rispondere a domande in linguaggio naturale sull'analisi dei dati raccolti; effettuare inferenza sui dati (es. individuare pattern, rispondere a query esplorative) a supporto dell'utente dei presidi medici.
- **Motivazione dell'esecuzione locale (chiusa 18/09/2026):** scelta del committente, l'azienda **Parsec 3,26** — requisito contrattuale/di policy del partner, da argomentare in tesi in questi termini (non solo come obbligo normativo). Modello LLM specifico ancora da scegliere.

---

## 5. Approccio Privacy

Rispetto alla v1 (Privacy by Design su dati wearable individuali — UUID, pseudonimizzazione), la v2 lavora **su dati pubblici e già aggregati** (ISTAT, ARPA), il che riduce alcuni rischi legati al trattamento di dati personali diretti.

*(Aggiornamento 18/09/2026 — chiuso:)*
- la zonizzazione è decisa: **distretti socio-sanitari** (non comuni singoli), il che mitiga in parte il rischio di re-identificazione rispetto a un dettaglio comunale;
- il motivo per cui l'LLM gira in locale è la **scelta del committente** (azienda Parsec 3,26), requisito contrattuale/di policy del partner più che un obbligo normativo puntuale — da argomentare così in tesi.

---

## 6. Cosa esce dallo scope rispetto alla v1

- Dispositivo wearable, PCB custom, sensori ambientali/salute/GPS on-device.
- Sensori fissi su arredo urbano.
- Pipeline time-series in tempo reale da dispositivo (InfluxDB) — **risolto 18/09/2026**: non serve nessun database (né time-series né relazionale/analitico); i dati pubblici periodici vengono recuperati via chiamate API dirette a ogni aggiornamento.
- Validazione hardware/prestazionale del dispositivo (Fase 5 della roadmap v1).

---

## 7. Collegamento con le materie del corso (aggiornato)

- **Python, ML/DL:** modelli di correlazione/predizione su dati di qualità aria e mortalità respiratoria.
- **NLP / LLM:** progettazione del modulo RAG e integrazione con LLM locale.
- **Architetture a microservizi:** pipeline di data engineering (Componente 2).
- **Privacy & GDPR:** gestione dati sanitari aggregati, scelta dell'LLM locale per conformità.
- **Project Management & Business Intelligence:** gestione del progetto e progettazione della dashboard decisionale.
- **Cloud Orchestration:** infrastruttura per pipeline dati e hosting dashboard (il modulo AI resta locale).
- **Backend/Frontend Development:** dashboard e mappa interattiva.
- ~~IoT e Rapid IoT Prototyping~~ — non più rilevante, salvo diversa indicazione.
- ~~Cisco Networking & Cybersecurity~~ — rilevanza ridotta senza dispositivi IoT sul campo; da rivalutare.

---

## 8. Modalità di collaborazione con l'azienda partner

Invariata rispetto alla v1: per limiti di orario legati all'impegno lavorativo full-time di Matteo (fino alle 18, più tempo di rientro), la collaborazione prevede incontri faccia a faccia saltuari con l'azienda, integrati da aggiornamenti più frequenti via email.

*(Aggiornamento 18/09/2026: referente aziendale = Sergio Guglielmi; responsabile risorse umane Parsec 3,26 = Irene Galante. Nessuna risorsa infrastrutturale fornita dall'azienda oltre alla consulenza di un dipendente per dubbi tecnici.)*
