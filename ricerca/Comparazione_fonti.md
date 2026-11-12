# Comparazione delle fonti — stato, incroci e confronti per granularità

*Creato il 02/10/2026, aggiornato il 02/10/2026 dopo l'integrazione di CAMS nel report dell'aria e la prima validazione del dato salute. Fotografia dello stato **reale** del repo (codice, file in `data/raw/` e `data/interim/`), non solo di quello pianificato. Va aggiornato a ogni nuova fonte o nuovo confronto.*

Documenti collegati: `Lista_dataset.md` (indice), `aria/Lista_dataset_aria.md`, `salute/Lista_dataset_salute.md`, `calore/Lista_dataset_calore.md`, `Anagrafiche_relazionali.md`, `documentazione/Scelte_Progettuali.md` del repository Presentation.

**Legenda stato:** ✅ integrata nella pipeline (adattatore/client + dati) · 🟡 client scritto o dati scaricati, **non** ancora nella griglia/dataset · 📄 solo documentata · ⛔ scartata/non accessibile.
**Legenda tipo di confronto:** **V** = validazione per ridondanza (stesso fenomeno, fonti diverse: devono tornare) · **E** = confronto esplorativo (fenomeni diversi, mai causale).

---

## 1. Tabella aggiornata delle fonti

### 1.1 Aria

| Fonte | Tipo | Grana nativa | Copertura | Licenza | Stato | Note sullo stato reale |
|---|---|---|---|---|---|---|
| **ARPA Puglia** (RRQA, host `old.arpa.puglia.it`) | misurato | stazione × giorno | 2012 → ieri | CC BY 4.0 (da confermare) | ✅ | 49 stazioni nel Salento (VERSALIS incluse); 12 distretti su 20 coperti. Statistica giornaliera propria (massimo per NO2/O3/SO2/CO, media per PM) |
| ARPA — mirror CKAN `dati-qualita-aria-2023` | misurato | stazione × giorno | solo 2023 | CC BY 4.0 | 🟡 | `data/raw/aria/arpa_puglia/qualita_aria_2023_salento.json`; riscontro indipendente dell'host non documentato, **non** ancora confrontato |
| **OpenAQ** | misurato (origine EEA) | stazione × ora → giorno | 2020-05-06 → oggi | ODC-BY (2 stazioni HabitatMap senza licenza) | ✅ | Orari sfasati 0-2 h rispetto a EEA (non corretti, scelta del 06/11/2026); nuovi id dal 01/06/2026 |
| **EEA** (Air Quality Download Service) | misurato (origine ARPA) | stazione × ora → giorno | 2013-2025 (2014 assente) + 2026 non verificato | CC BY 4.0 | ✅ | 33 stazioni, tutte già in ARPA. Parquet in cache |
| **Copernicus CAMS** (ADS) | **modellato** (0,1° ≈ 10 km) | cella × ora → comune × giorno | 2016 → oggi | CC-BY-4.0 | ✅ | **Nel dataset dal 02/10/2026**: giugno 2024 rigenerato a 4 fonti (207.360 celle, CAMS 21.900 `VALORE`) e confronti CAMS ↔ EEA/OpenAQ nel report, sez. 9.2. Cache: rianalisi validata 2024-01 → 2024-11 per CO, NO2, O3, PM2.5, SO2; **PM10 non ancora scaricato** → celle `NULL`. Il generatore legge solo la cache (`solo_cache`), l'ADS si chiama a parte con `scripts/aria/scarica_cams.py` |

### 1.2 Salute

| Fonte | Cosa dà | Grana nativa | Copertura | Licenza | Stato | Note sullo stato reale |
|---|---|---|---|---|---|---|
| **ISTAT — decessi comunali giornalieri** (canale A) | decessi totali, nessuna causa | **comune × giorno** (classi d'età sommate) | 2011-01-01 → 2026-06-30 (provvisori) | CC BY 4.0 | 🟡 | `api/salute/istat.py` + `data/interim/salute/istat/decessi_giornalieri_salento.csv` (853.224 righe, 146 comuni, stati `VALORE`/`NULL`/`NO_DATA`). **Non** collegato alla griglia del dataset salute |
| **ISTAT — bilancio demografico mensile** (canale D) | morti, nessuna causa | comune × mese | 2019-2024 | CC BY 4.0 | 🟡 | **Client scritto il 02/10/2026** (`api/salute/istat.py`, `scarica_bilancio_mensile` + `leggi_bilancio_mensile`) e **usato come validazione di A** (`scripts/salute/valida_decessi.py`): celle identiche nell'81-97 % per anno. Non entra nel dataset: è un controllo |
| ISTAT — cause di morte (SDMX, canale B) | decessi e tassi **per causa** (European Short List) | provincia × anno | 2003-2023 | CC BY 4.0 | 📄 | Nessun client. Selezione cause ⏳ |
| **Eurostat** `demo_r_mwk3_t` | decessi (stessi dati ISTAT ridistribuiti) | provincia (NUTS 3) × settimana | 2011-W01 → 2026-W27 | CC BY 4.0 | 🟡 | **Client scritto il 02/10/2026** (`api/salute/eurostat.py`, JSON-stat 2.0, nessuna chiave) e usato come validazione di A: **100 % di settimane identiche dal 2011 al 2023**, differenze solo su 2024-2025 (revisioni). Non entra nel dataset: è un controllo |
| **PNE / AGENAS** | ospedalizzazione BPCO, asma, influenza (unica fonte ricoveri) | ASL × anno | edizioni 2022-2025 | ⏳ non dichiarata | 📄 | Nessun client. API non documentata |
| AReSS — open data CKAN | prevalenza BPCO; accessi PS e ricoveri urgenti cerebrovascolari/renali | ASL × anno | 2006-2023 | CC BY 4.0 | 📄 | Client CKAN già nel repo (`dati_puglia_ckan.py`), nessun dataset scaricato |
| **Open Salute Puglia** (CSV scaricati a mano) | incidenza e prevalenza BPCO | **comune × anno** | incidenza 2024 (il file); prevalenza 2011-2024 | ⏳ non dichiarata | 🟡 | `data/interim/salute/open_salute/{incidenza,prevalenza}_BPCO_salento.csv` (filtrati dallo script `filtra_open_salute.py`). **Solo confronto visivo e supporto alle tesi**, non nel dataset (decisione 02/10) |
| AReSS — PugliaStat | mortalità e ricoveri per distretto/comune | distretto / comune | — | non dichiarata | ⛔ | Non accessibile. Unica fonte che darebbe causa **e** distretto |
| ISS, HFA, IPRES, SDO, registri tumori, ReNCaM | — | — | — | — | ⛔ | Eliminate il 01/10/2026 (v. `Lista_dataset_salute.md`) |

### 1.3 Calore (UHRI)

| Fonte | Tipo | Grana nativa | Copertura | Licenza | Stato |
|---|---|---|---|---|---|
| **ERA5-Land** (CDS) | modellato (0,1° ≈ 9 km) | cella × ora → comune × giorno | 1950 → oggi − 6 giorni (latenza misurata il 03/11/2026) | Copernicus (CC-BY) | 📄 — nessun client; `api/calore/` da creare. Riusa `celle_comuni.py` |
| **ARPA meteo** (CKAN) | misurato | stazione × ora | solo 2023-2024 | CC BY 4.0 | 📄 — nessun client; ~13 stazioni nel Salento |
| Tree Cover Density / Imperviousness Density (CLMS) | raster 10 m | pixel → comune (statistica zonale) | edizioni annuali/triennali | Copernicus (da confermare) | 📄 — attributi comunali; serve `rasterio` |
| Landsat C2 L2 (LST) | satellite | 30 m | — | USGS | 🕐 rimandata dopo l'MVP |

### 1.4 Supporto territoriale

| Fonte | Cosa dà | Stato |
|---|---|---|
| Regione Puglia — anagrafe distretti (IODL 2.0) | 20 distretti socio-sanitari del Salento (10 LE, 4 BR, 6 TA) e comuni afferenti | ✅ in `territorio.json` |
| Comuni-Italiani.it / ISTAT | 146 comuni, residenti, superficie | ✅ in `territorio.json` (licenza di Comuni-Italiani da chiarire) |
| Confini comunali GeoJSON (da mockup) | punto → comune, pesi cella → comune | ✅ `comuni_salento.geojson` |

---

## 2. Come incrociamo i dati

### 2.1 Chiavi di join

| Chiave | Dove vive | Collega |
|---|---|---|
| `id_comune` (codice ISTAT a 6 cifre) | `territorio.json` (PK), stazioni (FK), decessi ISTAT, Open Salute, celle CAMS/ERA5 | **tutto**: è l'unità base |
| `id_distretto` (es. `LE-53`) | `territorio.json` | aggrega i comuni; i 20 distretti sono la zona di confronto |
| `id_provincia` (LE, BR, TA) = ASL nel Salento | `territorio.json` | collega le fonti provinciali/ASL (ISTAT SDMX, Eurostat, PNE, AReSS CKAN) |
| `id_stazione` | `stazioni.json` + `stazioni_fonti` | porta le fonti aria (ARPA/OpenAQ/EEA) sotto la **stessa stazione fisica** (abbinamento per coordinate ≤ 250 m, 1 km se il comune è nel nome) |
| `giorno` (UTC+1) | dataset aria, calore, decessi | asse temporale comune; fonti orarie ridotte a un giorno con la stessa regola (media pesata sul tempo, senza soglia di ore, completezza in nota) |
| `inquinante` / `indicatore` | `inquinanti.json` | CO, NO2, O3, PM2.5, SO2 (+ PM10 scoperto) |

### 2.2 Regole d'incrocio (già decise)

1. **Mai medie fra fonti**: per ogni cella si tiene un valore per fonte; le fonti si confrontano, non si fondono.
2. **Stati espliciti**: `VALORE` / `NULL` (la fonte copre ma il valore non è usabile) / `NO_DATA` (la fonte non copre). Il confronto si fa **solo sulle celle in cui entrambe le fonti hanno `VALORE`**.
3. **Dalla stazione al comune** (solo in mappa e analisi): media delle **stazioni fisiche** con `VALORE`; la stazione virtuale `CAMS-<id_comune>` **non** entra nella media. Trattamento di `NULL`/`NO_DATA` nella media: ⏳.
4. **Dalla cella al comune** (CAMS, poi ERA5-Land): media **pesata sull'area** della sovrapposizione cella ∩ confine comunale.
5. **Dal comune al distretto** *(deciso il 02/10/2026)*: **media pesata sui residenti** dei comuni con `VALORE` per le grandezze intensive (concentrazioni, temperature) e **somma** per i conteggi (decessi, ricoveri); la nota porta quanti comuni e quale quota di residenti del distretto hanno contribuito. Implementazione condivisa in `api/comune/aggregazione.py`.
6. **Fonti a grana grossa non si ripartiscono** sulle grane fini (dato provinciale ≠ dato distrettuale senza ipotesi): ogni indicatore resta alla grana della sua fonte.
7. **Confronto aria/calore ↔ salute**: sempre **esplorativo, non causale**; dati sanitari mostrati **almeno a distretto × mese** (privacy, §7).
8. **Grana del confronto fra domini** *(deciso il 02/10/2026)*: aria a **comune × giorno**, salute e calore a **distretto × mese**; il confronto fra i tre si fa alla grana minima comune a tutti, cioè **distretto × mese**.
9. **ARPA si legge a parte** *(deciso il 02/10/2026)*: nei confronti e nelle visualizzazioni ARPA è una serie a sé, mentre OpenAQ, EEA e CAMS — che calcolano tutte la media delle ore del giorno — si possono accorpare. Per NO2, O3, SO2 e CO ARPA pubblica il **massimo**: il confronto con le altre resta leggibile come ordine di grandezza, non come concordanza.
10. **Dato modellato dichiarato** *(deciso il 02/10/2026)*: dove non ci sono stazioni il valore dell'aria è CAMS. Le correlazioni **si calcolano comunque**, ma vanno sempre etichettate come calcolate su dato modellato (report dell'aria, sez. 10).

---

## 3. Matrice di comparazione per granularità

Ogni riga è un livello di aggregazione; ogni colonna dice **quali fonti si possono mettere a confronto** a quel livello. Lo stato indica se il confronto esiste già.

### 3.1 Aria ↔ aria (validazione per ridondanza)

Il report dell'aria divide i confronti in **due blocchi** (sez. 9.2 e 9.3), perché le fonti non si leggono tutte allo stesso modo: OpenAQ, EEA e CAMS usano la stessa statistica giornaliera, ARPA no.

| Livello | Coppie confrontabili | Tipo | Stato | Esito / limite |
|---|---|---|---|---|
| **stazione × giorno** | **OpenAQ ↔ EEA** (blocco 9.2: stessa statistica) | V | ✅ nel report (giugno 2024: 1.532 celle) | è l'**unica coppia pulita** per NO2, O3, SO2 e CO. Concordanza giugno 2024: SO2 94,6 %, PM2.5 71,9 %, NO2 62,9 %, O3 24,7 % — il grosso dello scarto è lo **sfasamento orario di 0-2 h** (⏳), più alcuni **valori anomali di OpenAQ** (PM2.5 443 µg/m³ a Torchiarolo, v. §4) |
| **stazione × giorno** | ARPA ↔ OpenAQ, ARPA ↔ EEA (blocco 9.3: lettura qualitativa) | V solo per il PM | ✅ nel report (giugno 2024: 3.094 celle ARPA↔EEA, 1.452 ARPA↔OpenAQ) | **PM10 e PM2.5: 100 % concordanti** (correlazione 1,000 e 0,998) → validazione vera, perché lì ARPA usa anch'essa la media. **NO2, O3, SO2 e CO**: ARPA usa il **massimo** (per il CO il massimo della media mobile su 8 h), le altre la media → la concordanza **non è misurabile** e la colonna resta vuota; restano differenze sistematiche attese (NO2 −14,9, O3 −23,3 µg/m³) con correlazione 0,85-0,88, cioè stesso andamento, grandezza diversa |
| stazione × giorno | ARPA (host `old`) ↔ mirror CKAN 2023 | V | 🟡 non fatto | dati già in locale; basta uno script di confronto |
| **comune × giorno** | media stazioni fisiche (EEA o OpenAQ) ↔ **CAMS** (blocco 9.2) | V (misurato vs modellato) | ✅ **fatto il 02/10/2026** (giugno 2024: 1.304 celle EEA↔CAMS, 1.036 OpenAQ↔CAMS) | CO 100 % concordante; **NO2 23,5 %** (CAMS sottostima di ~4 µg/m³: cella di 10 km contro punto di traffico), O3 8,3 % con correlazione 0,76 (livello giusto, giorno sbagliato), SO2 e PM2.5 intermedi. Misura la **qualità del modello**, non "validazione" in senso stretto |
| comune × giorno | media stazioni ARPA ↔ CAMS (blocco 9.3) | V solo per il PM | ✅ nel report | ARPA usa il massimo per NO2/O3/SO2/CO: non confrontabile con la media CAMS |
| **distretto × mese** | ARPA / OpenAQ / EEA ↔ CAMS | V | 🟡 derivabile con `api/comune/aggregazione.py` (media pesata sui residenti), non ancora nel report | solo i 12 distretti con stazioni; **gli 8 senza stazioni hanno solo CAMS** → nessun confronto possibile, solo copertura (dichiarata nel report, sez. 10, con la quota di residenti coperta da misura) |

### 3.2 Calore ↔ calore

| Livello | Coppie | Tipo | Stato | Limite |
|---|---|---|---|---|
| stazione/comune × giorno | **ERA5-Land ↔ ARPA meteo** | V | 📄 non iniziato | solo **2023-2024**, ~13 stazioni su 146 comuni; rianalisi 9 km contro punto: attesa differenza sistematica (quota, costa, effetto urbano) |

### 3.3 Salute ↔ salute (validazione)

| Livello | Coppie | Tipo | Stato | Note |
|---|---|---|---|---|
| comune × mese | ISTAT giornaliero **sommato per mese** ↔ ISTAT bilancio demografico (canale D) | V | ✅ **fatto il 02/10/2026** (`scripts/salute/valida_decessi.py`, 2019-2024) | celle **identiche** nel 73,6-96,6 % per anno (entro ±1: 94-100 %), correlazione ≥ 0,9995. Lo scarto è peggiore sul 2019-2021 (canale A sopra il bilancio) e minimo sul 2022-2024: coerente con la natura provvisoria del canale A |
| provincia × settimana | ISTAT giornaliero sommato per provincia/settimana ISO ↔ **Eurostat** | V | ✅ **fatto il 02/10/2026** (2.424 settimane 2011 → 2026) | **100 % di settimane identiche dal 2011 al 2023** e sul 2026; differenze solo su 2024 (63,5 %) e 2025 (76,3 %), cioè gli anni che Eurostat non ha ancora rivisto. Ha fatto emergere l'errore del **comune fuso** contato due volte (v. §4) |
| **distretto × mese** | canale A ↔ canale D, aggregati alla grana di presentazione | V | ✅ nel report, sez. 4 | 52,1 % di celle identiche, 84 % entro ±1: aggregando, i piccoli scarti comunali si sommano invece di elidersi — va dichiarato quando si mostra il dato mensile per distretto |
| provincia × anno | ISTAT giornaliero sommato per anno ↔ ISTAT SDMX causa `99` (totale) | V | 📄 fattibile 2011-2023 | anni definitivi vs provvisori |
| ASL × anno | **Open Salute** prevalenza BPCO sommata per ASL ↔ AReSS CKAN prevalenza BPCO ↔ PNE (ricoveri BPCO) | V parziale / E | 📄 | prevalenza vs ricoveri sono grandezze diverse: PNE solo come confronto di andamento. Open Salute ha licenza non dichiarata |
| comune × anno | Open Salute incidenza ↔ prevalenza BPCO | coerenza interna | 🟡 file già in locale | utile solo come sanity check |

### 3.4 Ambiente ↔ salute (esplorativo, non causale)

| Livello | Coppie | Tipo | Stato | Vincolo |
|---|---|---|---|---|
| **comune × giorno** (interno all'analisi) | aria (media stazioni / CAMS) ↔ decessi ISTAT | E | ✅ dati **entrambi pronti** per giugno-ottobre 2024; nessuno script di confronto | numeri piccolissimi per comune → rischio di re-identificazione: **non esporre** questo livello in dashboard |
| comune × giorno | calore (ERA5-Land) ↔ decessi ISTAT | E | 📄 ERA5-Land da integrare | stessa cautela privacy; effetto caldo di solito ritardato di 0-3 giorni (lag da definire) |
| **distretto × mese** (**grana del confronto e della presentazione**) | aria / calore ↔ decessi | E | 🟡 aggregazione pronta (`api/comune/aggregazione.py`), script del confronto da scrivere | **è la grana decisa il 02/10/2026** per il confronto fra i tre domini: i decessi si sommano, l'aria è media pesata sui residenti dei comuni, ed è anche il minimo consentito in dashboard (§7) |
| distretto × giorno / settimana | aria / calore ↔ decessi | E | 🟡 derivabile, non la grana scelta | più punti e meno rumore della scala mensile, ma sotto il minimo di privacy per i decessi: usabile solo per analisi interne |
| provincia × anno | aria media annua ↔ cause di morte SDMX; ricoveri PNE | E | 📄 | nessuna lettura per distretto: dato solo provinciale/ASL |
| comune × anno | aria media annua ↔ Open Salute (incidenza/prevalenza BPCO) | E, solo visivo | 🟡 file in locale | **non integrare** nel dataset (decisione 02/10); licenza da chiarire con AReSS |

### 3.5 Riepilogo: a quale grana si può confrontare cosa

| Grana | Aria | Calore | Decessi | Cause di morte | Ricoveri | Patologie (Open Salute) |
|---|---|---|---|---|---|---|
| stazione × giorno | ✅ 3 fonti misurate (+ CKAN 2023) | ARPA meteo (2023-24) | — | — | — | — |
| comune × giorno | ✅ **grana minima dell'aria**: media stazioni + CAMS | 📄 ERA5-Land | ✅ ISTAT | — | — | — |
| comune × mese | derivabile | derivabile | ✅ ISTAT + bilancio mensile | — | — | — |
| **distretto × mese** (grana del confronto) | ✅ media pesata sui residenti | 📄 stessa regola, dati mancanti | ✅ somma | — | — | — |
| provincia × settimana | derivabile | derivabile | ✅ Eurostat | — | — | — |
| provincia/ASL × anno | derivabile | derivabile | derivabile | 📄 ISTAT SDMX | 📄 PNE | 📄 AReSS CKAN |
| comune × anno | derivabile | derivabile | derivabile | — | — | 🟡 Open Salute (visivo) |

"Derivabile" = ottenibile aggregando la fonte più fine; non è una fonte indipendente a quella grana.

---

## 4. Lacune e rischi emersi dalla review

1. **Nessun confronto aria ↔ salute esiste ancora**, ma i dati dei due lati ci sono già (aria: giugno 2024 a 4 fonti; decessi: 2011 → 06/2026) e i due blocchi che mancavano sono stati sciolti: l'**aggregazione al distretto** è decisa (media pesata sui residenti / somma) e implementata in `api/comune/aggregazione.py`, la **grana** è decisa (distretto × mese). Resta da scrivere lo script del confronto.
2. ~~Il dataset aria su disco è solo giugno 2024, 3 fonti~~ — **risolto il 02/10/2026**: giugno 2024 rigenerato a **4 fonti** (207.360 celle) e tabelle di validazione CAMS ↔ EEA/OpenAQ prodotte (report, sez. 9.2). Manca il solo **PM10 di CAMS** (non in cache → `NULL`).
3. **La validazione aria ha un limite strutturale**, ora **gestito nella presentazione** (decisione del 02/10): per NO2, O3, SO2 e CO ARPA usa il massimo, EEA/OpenAQ/CAMS la media, quindi ARPA sta in un blocco a sé (report, sez. 9.3, senza percentuale di concordanza) e le tre fonti a media si confrontano fra loro nel blocco di **validazione diretta** (sez. 9.2). Le coppie pulite per quegli inquinanti sono **OpenAQ↔EEA** (sfasamento orario ⏳) e **EEA/OpenAQ ↔ CAMS**; con ARPA restano confrontabili solo PM10 e PM2.5 (100 %).
4. **Copertura**: i comuni con almeno un valore misurato sono **20 su 146**, i distretti 12 su 20; 5 distretti su 20 hanno **0 % di residenti** coperti da una misura. Per gli altri la sola aria è CAMS (modellata). **Dichiarato nel confronto** (report, sez. 10): la correlazione che include i 126 comuni scoperti è calcolata **su dato modellato, non misurato** — la correlazione si calcola comunque, ma con questa etichetta sempre accanto, anche in dashboard.
5. **Valori anomali di OpenAQ** *(nuovo, 02/10/2026)*: a Torchiarolo (stazione ARPA 93, Fanin) OpenAQ dà PM2.5 443,84 µg/m³ il 28/06/2024 contro 8,70 di CAMS e 130,64 contro 8,45 di EEA il 26/06; SO2 65,6 contro 2,07 il 04/06. EEA e CAMS concordano fra loro, quindi l'anomalia è di OpenAQ e non è segnalata dalla fonte: **sporca la media del comune** e abbassa le concordanze di giugno 2024. Da trattare insieme allo sfasamento orario (⏳), senza filtri silenziosi.
6. **Comuni fusi** *(nuovo, 02/10/2026)*: l'anagrafica tiene Presicce e Acquarica del Capo separati, ISTAT pubblica il solo comune fuso (075098) e il client ne ripete il valore sui due componenti: **ogni somma su più comuni lo contava due volte**. Emerso dal confronto con Eurostat (provincia di Lecce all'8,7 % di settimane identiche invece del 94,1 %) e corretto negli aggregati; resta ⏳ come dovrà rappresentarlo l'anagrafica.
7. **Il calore non ha ancora né client né dati.** Il confronto ERA5-Land ↔ ARPA meteo copre solo 2023-2024.
8. **La salute per causa non scende sotto la provincia**: per cause e ricoveri il confronto con l'aria è per forza provincia/ASL × anno (3 punti per anno), quindi poco informativo. Il vero confronto utile è **decessi totali giornalieri**.
9. **Licenze aperte** che toccano i confronti: PNE (non dichiarata), Open Salute (non dichiarata), CLMS (da confermare), ARPA (CC BY 4.0 assunta).

---

## 5. Cosa è stato fatto il 02/10/2026 e cosa resta

Fatto:

1. ✅ **Report aria esteso a CAMS**: giugno 2024 rigenerato a 4 fonti e sez. 9 riorganizzata in due blocchi (9.1 cosa è confrontabile, 9.2 validazione diretta OpenAQ/EEA/CAMS, 9.3 confronti con ARPA), più la nuova sez. 10 sulla copertura misurata o modellata.
2. ✅ **Script di validazione salute**: `scripts/salute/valida_decessi.py` → `data/dataset/salute/report/Report_validazione_decessi.md` (canale A ↔ canale D a comune × mese, canale A ↔ Eurostat a provincia × settimana, più il confronto alla grana di presentazione distretto × mese).
3. ✅ **Aggregazione decisa e implementata**: `api/comune/aggregazione.py` (stazione → comune, comune → distretto con media pesata sui residenti o somma, giorno → mese).

Resta, in ordine:

1. **Primo confronto esplorativo aria ↔ decessi** a **distretto × mese** (grana decisa), con l'etichetta "misurato / modellato" accanto a ogni distretto.
2. **PM10 di CAMS** in cache, e CAMS per i mesi che servono al confronto (oggi 2024-01 → 2024-11).
3. **Valori anomali di OpenAQ** e **sfasamento orario**: decidere come trattarli (⏳).
4. Poi: client ERA5-Land e riuso dello stesso schema per il confronto caldo ↔ decessi.
