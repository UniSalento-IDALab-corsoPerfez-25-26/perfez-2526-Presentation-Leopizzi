# OneHealth — Abstract della proposta progettuale

*Piattaforma territoriale di supporto alle decisioni per la correlazione tra qualità dell'aria ed esiti di salute nel Salento*

**Candidato:** Matteo Leopizzi
**Corso:** Corso di Perfezionamento in Tecnologie Digitali per Ambienti e Sistemi Intelligenti — Università del Salento (IDA Lab)
**Referente accademico:** prof. Luigi Patrono
**Azienda partner:** Parsec 3,26 (Lecce) — referente aziendale: Sergio Guglielmi
**Data:** 19/09/2026

---

## 1. Abstract

Il progetto proposto dall'azienda partner **Parsec 3,26** riguarda il tema **One Health**, cioè la relazione tra fattori ambientali — in particolare la qualità dell'aria — e la salute della popolazione di un territorio. L'impostazione iniziale prevedeva lo sviluppo di un **dispositivo hardware dedicato** (wearable con sensoristica ambientale e di salute, PCB custom, geolocalizzazione) per la rilevazione diretta dei parametri sul campo.

A valle di un confronto con l'azienda, e **di comune accordo con essa**, sono emerse due criticità che rendono poco sostenibile e poco differenziante il percorso hardware:

1. **Tempi incompatibili con il perimetro dell'elaborato.** La finestra di realizzazione del progetto d'esame (**17/09/2026 – 24/10/2026**, con consegna della documentazione finale entro la prima settimana di novembre) è incomprimibile e si somma a un impegno lavorativo full-time del candidato. Un percorso hardware richiede progettazione del circuito, approvvigionamento dei componenti, prototipazione, calibrazione dei sensori e validazione metrologica: attività con tempi di attesa non controllabili (forniture, revisioni di PCB) e con un esito di fine percorso che, realisticamente, sarebbe un prototipo non validato — quindi poco utilizzabile come risultato dimostrabile.
2. **Saturazione dello stato dell'arte.** Prototipi di rilevazione ambientale personale e distribuita su queste tematiche **esistono già**, in ambito sia accademico sia commerciale (tra gli altri, il progetto RESPIRO dell'Università di Milano-Bicocca), così come reti di centraline low-cost e wearable per il monitoraggio dell'esposizione. Il mercato è sostanzialmente saturo e un ulteriore dispositivo aggiungerebbe un contributo marginale, sia scientifico sia industriale.

Alla luce di questo, **si propone — e si chiede l'autorizzazione a procedere in tal senso — un riorientamento del progetto verso una soluzione interamente software**, che l'azienda partner ritiene **più industrializzabile**: un prodotto replicabile su altri territori senza costi di produzione, distribuzione e manutenzione di apparati fisici, basato su dati già esistenti e pubblicamente disponibili, e quindi capace di generare valore in tempi compatibili con il percorso formativo e con una sua eventuale evoluzione commerciale.

Il valore della proposta risiede nel destinatario. Oggi i dati ambientali e i dati sanitari esistono, sono pubblici e sono di buona qualità, ma **vivono in archivi separati, con granularità geografiche e temporali diverse**, e non sono leggibili insieme da chi deve decidere. La soluzione proposta è una **piattaforma territoriale di supporto alle decisioni (DSS)** rivolta a **presidi medici e aziende sanitarie, pubbliche e private**, pensata come strumento di **controllo di gestione**: consente di osservare, distretto per distretto, come si distribuiscono pressione ambientale e carico sanitario, dove si concentra la domanda di prestazioni, come evolvono gli indicatori nel tempo e quindi dove orientare risorse, personale, campagne di prevenzione e investimenti. È un livello di lettura del territorio che oggi manca e che, per essere costruito, non richiede alcuna nuova rilevazione sul campo.

Sul piano metodologico, il sistema correla la **qualità dell'aria** con le **cause di morte** e con le **diagnosi di patologie potenzialmente associate all'esposizione a inquinanti atmosferici**, su un territorio definito come **Salento** (province di Lecce, Taranto e Brindisi), aggregato per **distretti socio-sanitari** delle rispettive ASL e su una finestra temporale di almeno cinque anni. Le correlazioni individuate sono trattate e presentate **come analisi esplorativa e non causale**: fattori confondenti quali fumo, struttura per età della popolazione, comorbidità e qualità dell'aria indoor non sono osservabili nelle fonti pubbliche utilizzate, e questo limite viene dichiarato esplicitamente sia nella tesi sia nell'interfaccia.

L'attendibilità del dato è affrontata per **ridondanza e incrocio tra fonti indipendenti**: ogni grandezza è, dove possibile, verificata su più archivi prima di entrare nella pipeline. Per la qualità dell'aria, ad esempio, non si utilizza la sola rete ARPA Puglia, ma anche aggregatori indipendenti come OpenAQ e il dato modellato Copernicus/CAMS, come riscontro e come copertura delle zone prive di stazioni fisse; analogamente, il lato sanitario si appoggia a fonti statistiche ufficiali (ISTAT e archivi regionali) confrontate tra loro. Le discordanze tra fonti non vengono nascoste: sono tracciate e riportate come indicatore della qualità del dato di ciascun distretto.

L'intera piattaforma è **self-hosted**: per scelta esplicita del committente Parsec 3,26, tutte le componenti — inclusa quella di intelligenza artificiale — vengono eseguite su infrastruttura locale, senza ricorso a servizi cloud di terze parti. Oltre alla parte descrittiva e di correlazione, il sistema integra un **modello di machine learning per la predizione**, addestrato sulle serie storiche raccolte, per stimare l'andamento atteso degli indicatori ambientali e sanitari per distretto, e un **LLM open-source preaddestrato**, eseguito in locale e vincolato tramite architettura RAG **ai soli dati raccolti ed elaborati dalla piattaforma**, con la funzione di interrogare il dato in linguaggio naturale e produrre sintesi esplorative, senza ricorso a conoscenza esterna al perimetro dei dati di progetto.

---

## 2. La dashboard

L'output del progetto è un'unica applicazione web, eseguita in locale, con interfaccia a tema scuro e impostazione minimale. Il percorso di lettura è organizzato dall'insieme al dettaglio:

- **Indicatori sintetici (KPI):** valori aggregati sull'area e sul periodo selezionato — concentrazioni medie degli inquinanti, superamenti dei limiti di legge, indicatori sanitari e variazione rispetto al periodo precedente.
- **Mappa interattiva (OpenStreetMap):** il Salento rappresentato con i **confini geografici reali dei distretti socio-sanitari** di Lecce, Taranto e Brindisi; ogni distretto è colorato in base all'indicatore selezionato e cliccabile per aprirne il dettaglio.
- **Dettaglio di distretto e confronto:** per il distretto selezionato, valori per singolo inquinante, indicatore sanitario, scostamento dal periodo precedente e **indicazione della qualità del dato** (numero di stazioni di misura che coprono l'area, oppure segnalazione esplicita che il valore proviene da dato modellato anziché misurato).
- **Serie temporali:** andamento degli indicatori ambientali e sanitari nel tempo, con **selettore di periodo** che agisce contemporaneamente su mappa, KPI e grafici, e con la proiezione prodotta dal modello predittivo distinta graficamente dal dato storico.
- **Tabella riassuntiva:** tutti i distretti a confronto, ordinabili per ciascun indicatore, con colonna di variazione, come base per il controllo di gestione.
- **Interrogazione in linguaggio naturale:** pannello di dialogo con l'LLM locale per porre domande sui dati della piattaforma e ottenere sintesi e confronti, con riferimento alle fonti utilizzate per la risposta.

Ogni vista riporta in modo permanente l'avvertenza sulla natura **esplorativa e non causale** delle correlazioni mostrate.

---

## 3. Richieste

1. **Autorizzazione al riorientamento software.** Si chiede conferma che l'impostazione qui descritta — piattaforma software su dati pubblici, senza sviluppo hardware — sia considerata adeguata come progetto d'esame finale, nei termini concordati con l'azienda partner.
2. **Accesso a dataset dell'Università del Salento.** Si chiede se l'Ateneo, l'IDA Lab o gruppi di ricerca afferenti dispongano di **dataset su qualità dell'aria, esposizione ambientale, epidemiologia o mortalità relativi al territorio salentino** che possano essere resi disponibili per il progetto. Dati di questo tipo — in particolare a granularità comunale o sub-provinciale, o relativi a diagnosi e ricoveri — aumenterebbero sensibilmente il valore analitico della piattaforma e rafforzerebbero il processo di validazione incrociata, che oggi si fonda sulle sole fonti aperte nazionali e regionali. Sono graditi anche riferimenti a pubblicazioni o progetti interni all'Ateneo su queste tematiche, utili come base metodologica e come termine di confronto per i risultati.
