# Ricognizione dataset pubblici "Qualità dell'aria + Salute" per il Salento (Lecce, Taranto, Brindisi) — Fase 2 OneHealth

## TL;DR
- **Il dataset combinato "aria + salute per zona" NON esiste pronto all'uso: va costruito ex novo incrociando fonti separate.** Le tre categorie richieste sono tutte reperibili da fonti istituzionali, ma con granularità geografiche disallineate (stazione vs. comune vs. ASL/provincia) che il progetto dovrà armonizzare.
- **Le fonti più solide e immediatamente utilizzabili** sono: per l'aria, gli **open data ARPA Puglia** (portale dati.puglia.it + API dati.arpa.puglia.it, dato per singola stazione, serie storiche pluriennali) integrati da **EEA** e **Copernicus/CAMS**; per la mortalità, **ISTAT** (comune/provincia, CSV) e **OER Puglia**; per i ricoveri, gli **open data del Ministero della Salute** e il **Rapporto SDO** annuale.
- **La fonte informalmente citata come "ESDO" non esiste con questo acronimo**: corrisponde con ogni probabilità all'**OER (Osservatorio Epidemiologico Regionale Puglia)** e/o alla **S.C. Statistica ed Epidemiologia della ASL Taranto**, entrambe basate sull'archivio **ReNCaM/ReMo** dei certificati di morte ISTAT. Il **Centro Salute Ambiente (CSA) Puglia** è l'ente che più si avvicina all'obiettivo del progetto (correlazione ambiente-salute su Taranto/Brindisi/Lecce).

## Key Findings

1. **Qualità dell'aria** — ARPA Puglia gestisce la Rete Regionale di Rilevamento della Qualità dell'Aria (RRQA), composta da **53 stazioni fisse (41 pubbliche + 12 private)**, definite dalla D.G.R. Puglia 2420 del 16.12.2013, più altre stazioni di interesse locale e 7 laboratori mobili; sono presenti stazioni in tutte e tre le province salentine (es. Lecce–S.M. Cerrate, Maglie, Galatina, Brindisi, Taranto e le stazioni ex-ILVA/ADI). Dati per singola stazione, frequenza giornaliera/oraria, pubblicati come open data (CSV/API) e come report annuali/mensili. Copernicus/CAMS e EEA forniscono coperture modellistiche/satellitari e osservazioni armonizzate a scala europea.

2. **Cause di morte** — Disponibili a livello comunale e provinciale da ISTAT (serie storiche dal 2003 in poi per causa iniziale ICD/età/sesso; dettaglio comunale su richiesta dal 1980) e dall'OER Puglia (atlanti e tavole di mortalità). Il livello di massimo dettaglio (per singola causa ICD, comune, età) spesso richiede richiesta al Contact Centre ISTAT.

3. **Ricoveri (SDO)** — Il flusso SDO è gestito regionalmente dal sistema **Edotto** (Regione Puglia) e confluisce nel NSIS del Ministero della Salute. Open data aggregati su dati.salute.gov.it; Rapporto SDO annuale nazionale; i microdati per ASL/provincia richiedono richiesta di accesso.

## Details

### CATEGORIA 1 — QUALITÀ DELL'ARIA

**1a. ARPA Puglia — Rete Regionale Qualità Aria (RRQA)** *(fonte primaria consigliata)*
- **Ente**: ARPA Puglia — Centro Regionale Aria (UOC CRA), sede di Bari; validazione dati province BR/LE/TA gestita dagli uffici territoriali.
- **Cosa contiene**: PM10, PM2.5, NO2, O3, SO2, benzene (C6H6), CO e altri inquinanti previsti dal D.Lgs. 155/2010. Secondo il documento ufficiale ARPA Puglia prot. 0078439 del 29/10/2024, «La Rete Regionale di Rilevamento della Qualità dell'Aria (RRQA)… è composta da 53 stazioni fisse (di cui 41 di proprietà pubblica e 12 private)», a cui si aggiungono 9 stazioni di interesse locale e le stazioni ex-ILVA/ADI a Taranto.
- **URL**:
  - Portale open data regionale: https://dati.puglia.it/ckan/organization/arpa-puglia (dataset "Aria - Monitoraggio dati qualità dell'aria", "Aria - Stazioni di monitoraggio delle reti di qualità dell'aria")
  - API: https://dati.arpa.puglia.it/openapi/index.html
  - Dati storici: https://www.arpa.puglia.it/pagina3139_dati-storici-qualit-dellaria.html
  - Report annuali/mensili: https://www.arpa.puglia.it/pagina2873_report-annuali-e-mensili-qualit-dellaria-rrqa.html
- **Formato**: CSV, JSON, API REST; report in PDF.
- **Frequenza**: rilevazione giornaliera/oraria, validazione giornaliera; report mensili e annuali.
- **Granularità**: singola stazione (georeferenziata lat/long). Aggregazione comunale possibile solo dove esistono stazioni; non tutti i comuni sono coperti.
- **Serie storica**: pluriennale (i report annuali coprono almeno l'ultimo decennio; dati giornalieri storici scaricabili dal portale ARPA). Copre pienamente il periodo 2016-2026.
- **Limiti**: dati recenti "provvisori" fino a validazione definitiva; pubblicazione solo nei giorni lavorativi; copertura spaziale non uniforme.
- **Verifica pratica (27/09/2026)**: l'host API documentato (`cloud.arpa.puglia.it`) risulta irraggiungibile; lo stesso contratto è servito da `old.arpa.puglia.it/ARPA_ARIA/` (`dati.jsp`, `centraline.jsp`, `inquinanti.jsp`), non documentato, con dati reali **2012 → ieri**. È la via usata dal progetto — dettagli e avvertenze in `aria/Lista_dataset_aria.md`, client in `api/aria/arpa_puglia.py`.

**1b. OpenAQ** *(API v3 testata e verificata il 27/09/2026 — v. `api/aria/openaq.py`)*
- **Ente**: OpenAQ (non-profit); aggrega dati governativi (in Italia origine EEA/ARPA — le stazioni trovate hanno nomi identici a quelli della rete ARPA Puglia: es. "LECCE - S. M. Cerrate", "Filzi", "STATTE VIA DELLE SORGENTI").
- **Cosa contiene**: PM2.5, PM10, O3, NO2, SO2, CO. OpenAQ espone più `id` di parametro per lo stesso inquinante a seconda dell'unità (mass in µg/m³ vs. concentrazione in ppm/ppb): per confrontare/unire con ARPA (µg/m³) si usano gli id in µg/m³ — `pm10=1, pm25=2, o3=3, co=4, no2=5, so2=6` (v. `PARAMETRI_RIFERIMENTO` in `api/aria/openaq.py`).
- **URL**: https://openaq.org/ ; API v3: https://docs.openaq.org/ ; explorer: https://explore.openaq.org/
- **Autenticazione**: API key gratuita (registrazione su `explore.openaq.org/register`), header `X-API-Key` (non come query param). Rate limit free tier: 60 richieste/minuto, 2.000/ora.
- **Query geografica**: `GET /v3/locations?bbox=minLon,minLat,maxLon,maxLat` (WGS84) oppure `coordinates=lat,lon&radius=<metri, max 25000>` (non combinabili). Bbox usata per il Salento: `16.70,39.75,18.55,40.95` (`BBOX_SALENTO` in `api/aria/openaq.py`).
- **Dati giornalieri**: `GET /v3/sensors/{sensors_id}/days` (un sensore = una stazione + un parametro), con `date_from`/`date_to`.
- **Formato**: API (JSON); richiede API key gratuita.
- **Granularità**: singola stazione (coordinate GPS).
- **Verifica di copertura (27/09/2026, chiave in `.env` gitignored)**:
  - **62 stazioni** trovate nel bbox del Salento, quasi tutte sovrapponibili per nome/coordinate alle stazioni RRQA di ARPA Puglia note (`data/dataset/aria/arpa_puglia/stazioni_di_monitoraggio.json`).
  - **Copertura temporale reale confermata con dati veri** (non solo metadata): es. NO2 orario/giornaliero per Lecce–S.M. Cerrate disponibile per **gennaio 2021** — un anno **non coperto** dal mirror CKAN ARPA (che copre solo il 2023). La maggior parte delle stazioni ha `datetimeFirst` **2020-05-06** e `datetimeLast` fino a **oggi (27/09/2026)**: copre quindi bene proprio i due buchi noti di ARPA (2019 parzialmente escluso-2022, e 2024-oggi).
  - **2019 non coperto** neanche da OpenAQ (la copertura parte dal 2020-05-06 per la quasi totalità delle stazioni).
  - **Split di ID dal 01/06/2026**: le stazioni storiche (es. id `8378` "LECCE - S. M. Cerrate") terminano intorno al 03/06/2026 e vengono sostituite da nuovi id (es. `6387781` "Lecce - S.M. Cerrate", stessa posizione, nomi ripuliti) attivi da allora: **per costruire una serie continua serve riconciliare vecchio/nuovo id per nome+coordinate**, non basta l'id.
  - **Anomalia**: 2 stazioni (`5200352` "egdp-6", `5338026` "egdp-7", solo PM2.5) senza `datetimeFirst`/`datetimeLast` popolati — da chiarire cosa siano prima di usarle.
- **Limiti**: è un aggregatore, non fonte primaria; **non copre il 2019**; richiede riconciliazione vecchio/nuovo id di stazione per serie continue; completezza (`coverage.percentComplete` per riga) va controllata riga per riga, osservato variabile (es. 4%-88% nello stesso mese per la stessa stazione).

**1c. Copernicus / CAMS**
- **Ente**: Copernicus Atmosphere Monitoring Service (ECMWF).
- **Cosa contiene**: CAMS European air quality reanalyses — reanalisi modellistica su griglia **0.1°** (per Copernicus ADS: «CAMS produces annual air quality reanalyses for the European domain at significantly higher spatial resolution (0.1 degrees, approx. 10km)»; ECMWF precisa che la risoluzione reale va «from 3 km (at 72.0°N) to 10 km (at 30°N)», quindi ~10 km alla latitudine del Salento). Ensemble di 11 modelli — per ECMWF Confluence: «CHIMERE (INERIS, FR), EMEP (MET Norway), EURAD-IM (Jülich IEK, DE), LOTOS-EUROS (KNMI/TNO, NL), MATCH (SMHI, SE), MOCAGE (Météo-France), SILAM (FMI, FI), DEHM (Aarhus, DK), GEM-AQ (IEP-NRI, PL), MONARCH (BSC, ES) and MINNI from ENEA (Italy)».
- **URL**: Atmosphere Data Store https://ads.atmosphere.copernicus.eu/datasets/cams-europe-air-quality-reanalyses
- **Formato**: NetCDF/GRIB via ADS (interfaccia web + API Python); richiede registrazione gratuita e accettazione licenza.
- **Granularità**: griglia ~10 km (dato modellistico, non puntuale): utile per coprire i comuni salentini privi di centraline. Copertura temporale pluriennale (reanalisi annuali validate).
- **Limiti**: dato modellato, non misurato; risoluzione 10 km può essere grossolana per analisi intra-comunali; necessita competenze di gestione dati geospaziali.

**1d. EEA — European Environment Agency**
- **Ente**: EEA (dataflow E1a/E2a + storico AirBase / Air Quality e-Reporting).
- **URL**: European Air Quality Portal https://aqportal.discomap.eea.europa.eu/ ; AQ Viewer / download service.
- **Formato**: CSV via download service; accessibile con librerie (R: EEAaq, euroaq; Python: airbase).
- **Granularità**: singola stazione (le stesse stazioni ARPA riportate a livello UE). Serie storiche lunghe (AirBase parte dagli anni '90-2000).
- **Nota utile — dataset accademico già pronto**: **Fusta Moro A., Fassò A. & Rodeschini J. (Univ. di Bergamo), "The Dataset of Daily Air Quality for the Years 2013-2023 in Italy", Scientific Data (2026), DOI 10.1038/s41597-026-07712-3** — «daily statistics… at the locations of the 744 available monitoring stations… retrieved from the European Environmental Agency and Copernicus Programme». Pubblicato open access su Zenodo (progetto GRINS): utilizzabile come base già pulita e validata per le stazioni salentine.

**1e. ISPRA / SNPA**
- **Ente**: ISPRA (sistema InfoAria; inventario nazionale emissioni).
- **URL**: https://www.isprambiente.gov.it/it/banche-dati/banche-dati-folder/aria-ed-emissioni-in-atmosfera ; emissioni: https://emissioni.sina.isprambiente.it/
- **Contenuto**: aggrega i dataset regionali di qualità dell'aria (EoI) + inventario emissioni disaggregato su base provinciale (1990-2023).
- **Granularità**: provinciale (emissioni); stazione (qualità aria, ridondante con EEA/ARPA).

### CATEGORIA 2 — CAUSE DI MORTE

**2a. ISTAT — Indagine su decessi e cause di morte** *(fonte primaria consigliata)*
- **URL banca dati**: https://esploradati.istat.it/databrowser/#/it/dw/categories/IT1,Z0810HEA,1.0/HEA_DEATH ; anche dati.istat.it (DCIS_CMORTE1_RES).
- **Contenuto e copertura**: per il Contact Centre ISTAT, «L'Istat diffonde ogni anno (a circa due anni dall'anno di riferimento) il numero di decessi per causa iniziale di morte (in base alla European Short List)… serie storiche dall'anno 2003… dove possibile arrivano al livello provinciale». Disaggregazione per età, sesso, cittadinanza, istruzione, stato civile.
- **Granularità**: fino al livello provinciale nella banca dati pubblica; su richiesta per finalità di studio/ricerca sono ottenibili «decessi per comune di residenza, sesso e causa - dati annuali dal 1980» e per comune/provincia di evento con dettaglio ICD dal 1969.
- **Formato**: CSV/tabellare online; microdati testuali su richiesta; elaborazioni personalizzate a pagamento.
- **Copertura recente (mortalità totale/tempestiva)**: la pagina ISTAT "Dati di mortalità" pubblica dati provvisori per comune, serie dal 2011, in due varianti — **giornaliera** (`decessi-comunali-giornalieri-provvisori-4.zip`) e **mensile** (`decessi-comunali-mese-provvisori-3.zip`, la stessa che la pagina EN chiama `mortality-data-...-provisional-data.zip`) — per sesso e classi d'età, senza dettaglio di causa.
- **Limiti**: causa di morte al massimo dettaglio comunale richiede richiesta motivata; diffusione a ~2 anni dall'anno di riferimento.

> **Verifica del 01/10/2026 (chiamate reali).** Scheda tecnica completa: `data/dataset/salute/istat/ISTAT.md`. In sintesi: (a) i decessi comunali **giornalieri** arrivano al **30/06/2026** (non 31/03/2026) e sono un ZIP il cui URL **cambia a ogni rilascio** (cartella per mese), non un endpoint stabile — CSV di 827 MB, 5.332.983 righe, tracciato in PDF allegato; (b) le **cause di morte** sono raggiungibili via **API SDMX** (`https://esploradati.istat.it/SDMXWS/rest`, dataflow `IT1,39_494_DF_DCIS_CMORTE1_RES_1,1.0`) con serie **2003-2023**, ma solo **provinciale** (`ITF45`/`ITF44`/`ITF43`), **senza mese** e **senza classi d'età** (le due dimensioni esistono solo con causa = totale).

**2b. ISTAT — Health for All Italia (HFA)**
- **URL**: https://www.istat.it/sistema-informativo-6/health-for-all-italia/
- **Contenuto**: ~4.000 indicatori (Gruppo 2 "Mortalità per causa", Gruppo 9 "Attività ospedaliera per patologia", ecc.), serie storiche.
- **Granularità**: provinciale e regionale.
- **Formato**: software desktop (solo Windows) con dati interrogabili; ultimo aggiornamento straordinario aprile 2026.
- **Limiti**: non è un semplice CSV; dominio minimo provinciale (no comune).

> **Verifica del 01/10/2026 (database scaricato e decodificato).** Scheda tecnica: `data/dataset/salute/istat/ISTAT.md` (canale C). HFA è **la fonte che risolve i ricoveri**: contiene *Tasso e numero di dimissioni ospedaliere per malattie dell'apparato respiratorio* a livello **provinciale, 1999-2024** (indicatori `8550`+), oltre alla mortalità respiratoria 1990-2023 (`1600`+) e alla popolazione provinciale 1982-2024. Il database (`HFA_giugno.zip`, 26 MB) è in formato binario per `HFA.exe`, ma la struttura è stata decodificata (matrici `float32` indicatore × territorio, più i file `.ind`/`.rid`/`.par`; la Puglia è il dataset `11600`): valori di controllo letti per il 2023 → Lecce tasso dimissioni respiratorie 91,47 per 10.000 e tasso di mortalità respiratoria 11,61; Taranto 90,61 e 9,13; Brindisi 99,58 e 9,99. Licenza **CC BY 4.0**.

**2c. OER Puglia — Osservatorio Epidemiologico Regionale** *(candidato "ESDO")*
- **Ente**: OER Puglia (istituito con L.R. 14/1985; protocollo con Univ. di Bari; funzioni in trasferimento ad AReSS Puglia dal 2024, DGR 1396/2024).
- **URL**: portale attuale https://www.sanita.puglia.it/web/oer (sezioni "Mortalità e Cause", "Tavole Mortalità per causa", "Atlante-Trend mortalità tumori"); sito legacy http://www.oerpuglia.org/ ("Atlante delle cause di morte", "Stato di Salute").
- **Contenuto/copertura**: l'**Atlante delle cause di morte in Puglia** copre gli anni **2000-2005**, a livello **comunale per tutta la Puglia**, disponibile come **PDF (mappe) + tabelle Excel per singolo comune**, accesso pubblico/aperto (confermato da ARPA Puglia e LILT Lecce; file "Atlante_causedimorte_2000-05.pdf"). Le sezioni "Tavole Mortalità per causa" e "Atlante-Trend mortalità tumori" sul portale attuale esistono ma la copertura temporale/formato esatti non sono stati verificabili automaticamente (pagine che bloccano il crawling) — **da verificare aprendo le pagine nel browser**.
- **Fonte dati**: **ReNCaM** (Registro Nominativo delle Cause di Morte) basato su scheda di morte ISTAT mod. D4.
- **Limiti**: atlante pubblico fermo al 2005; per dati aggiornati serve interlocuzione con OER/AReSS.

**2d. ASL Taranto — S.C. Statistica ed Epidemiologia** *(altro candidato "ESDO")*
- **Ente**: Struttura Complessa di Statistica ed Epidemiologia, ASL Taranto (Dir. S.A. Minerba); Viale Virgilio 31, Taranto.
- **URL**: https://www.sanita.puglia.it/web/asl-taranto/epidemiologia-e-statistica
- **Contenuto**: "Le cause di mortalità in Provincia di Taranto - Rapporto 2023" (a cura della S.C. Statistica ed Epidemiologia ASL Taranto, PDF ufficiale su sanita.puglia.it) copre gli anni **2012-2021**, a livello **comunale** della provincia di Taranto, pubblicato su Epidemiologia & Prevenzione (DOI: 10.19191/EP24.2.S1.03); fonte: Registro di Mortalità (ReMo/ReNCaM) municipale, codifica ICD-10 (dati fino al 31/12/2022).
- **Limiti**: solo provincia di Taranto; formato report/PDF, non dataset grezzo.

**2e. Registro Tumori Puglia (RTP)**
- **Ente**: RTP, coordinamento presso Istituto Tumori "Giovanni Paolo II" Bari; sezioni provinciali presso ASL LE, TA, BR.
- **URL**: https://sist.sanita.puglia.it/web/rt/rapporti ; rapporto incidenza regionale 2013-2021 (AReSS).
- **Contenuto**: incidenza, mortalità, prevalenza, sopravvivenza tumorali per provincia; rapporti ASL Lecce (2013-2017), Taranto (2015-2019), Brindisi (2015-2019).
- **Granularità**: provinciale (sezioni accreditate AIRTUM: TA e LE dal 2013, BT dal 2014, Brindisi in accreditamento).
- **Limiti**: solo patologie oncologiche; report PDF, microdati su richiesta.

**2f. AReSS Puglia — Open Salute Puglia / PugliaStat** *(aggiunto 22/09/2026)*
- **Ente**: AReSS Puglia (Agenzia Regionale Strategica per la Salute ed il Sociale), Area "Epidemiologia e Care Intelligence" (dir. Lucia Bisceglia); sede a Bari. AReSS ha assorbito le funzioni dell'OER Puglia (§2c) dal 2024 (DGR 1396/2024) ed è quindi anche il naturale punto di contatto per la mortalità comunale aggiornata oltre il 2005 e per chiarire l'ente "ESDS" (v. sopra).
- **Cosa contiene**: due strumenti distinti.
  - **Open Salute Puglia** (opensalute.aress.regione.puglia.it): prevalenza e incidenza di **malattie croniche** (BPCO, diabete tipo 2, ipertensione arteriosa, scompenso cardiaco — la BPCO è direttamente rilevante come indicatore respiratorio) e di oltre 25 tipologie **tumorali** (colon-retto, polmone, mammella, prostata, leucemie, linfomi, ecc.). Sezione "Metodi" con opzione "Consulta e scarica" (formato/API non confermati automaticamente).
  - **PugliaStat**: strumento di analisi su **ospedalizzazioni e decessi della popolazione residente pugliese**, con granularità dichiarata **provinciale, distrettuale e comunale** — la stessa zonizzazione decisa per OneHealth (distretto socio-sanitario). Presentato nel 2015 al Congresso dell'Associazione Italiana di Epidemiologia.
- **URL**:
  - Portale generale: https://aress.regione.puglia.it/
  - Open Salute Puglia: https://opensalute.aress.regione.puglia.it/
  - PugliaStat: https://aress.regione.puglia.it/en/aree-tematiche/mappe-e-dati-per-la-salute/pugliastat
- **Formato**: non confermato con certezza dalla sola ricognizione web (pagine dinamiche); Open Salute Puglia sembra offrire consultazione + download, PugliaStat non dichiara esplicitamente modalità di accesso/export. **Da verificare manualmente nel browser.**
- **Licenza**: non dichiarata esplicitamente nelle pagine consultate — da verificare, eventualmente contattando AReSS.
- **Rilevanza per OneHealth**: PugliaStat è particolarmente interessante perché copre nativamente sia mortalità sia ricoveri (SDO) a livello di **distretto**, evitando parte del lavoro di armonizzazione geografica che il progetto dovrebbe altrimenti fare partendo da fonti a grana provinciale/comunale disallineata. Open Salute Puglia aggiunge un indicatore di patologia respiratoria cronica (BPCO) complementare alla sola mortalità.
- **Limiti**: accesso/formato di export non confermati automaticamente; nessuna API pubblica documentata trovata in questa ricognizione.

> **Verifica del 01/10/2026 (chiamate reali).** Scheda tecnica completa: `data/dataset/salute/aress_puglia/AReSS_Puglia.md`. I due strumenti **non sono accessibili programmaticamente**: **PugliaStat** è un software interno che produce report su richiesta (la pagina non pubblica dati, export né endpoint); **Open Salute Puglia** è un front-end Next.js che incorpora dashboard **Apache Superset** (`superset.aress.regione.puglia.it`), le cui API richiedono un *guest token* (richiesta anonima all'elenco dashboard → `count: 0`). In compenso è emerso un **terzo canale, questo sì usabile**: AReSS pubblica **75 dataset su dati.puglia.it (CKAN, CC BY 4.0)** con datastore attivo (interrogabile anche in SQL) — tra cui *pazienti cronici con BPCO* (2006-2023) e *accessi in PS e ricoveri urgenti* (malattie cerebrovascolari e renali, 2018-2023) — ma con grana **ASL/regione**, mai distretto o comune, e **senza alcun dataset di ricoveri respiratori**.

**Nota correlata — mortalità comunale più recente (IPRES / Regione Puglia)**: durante la ricerca su AReSS è emerso che il portale open data regionale (dati.puglia.it, gruppo "Popolazione e società", a cura di IPRES) pubblica decessi per comune e sesso su base ISTAT per gli anni **2015, 2019, 2021, 2023**, e l'Ufficio Statistico della Regione Puglia pubblica aggiornamenti comunali mensili dei decessi (serie che arriva a dicembre 2025). Questo **aggiorna il limite segnalato in §2c** ("Atlante OER pubblico fermo al 2005"): esiste mortalità comunale più recente, sebbene su un ente diverso da AReSS (IPRES) — **da verificare e valutare come fonte aggiuntiva** in una prossima sessione.

**Sul "ReNCaM/ESDO"**: nessuna fonte con acronimo "ESDO" esiste in Puglia. Il termine è verosimilmente una citazione informale/errata dell'OER o della struttura "Epidemiologia e Statistica" ASL Taranto, entrambe fondate sul ReNCaM/ReMo (certificati di morte ISTAT).

### CATEGORIA 3 — RICOVERI OSPEDALIERI (SDO)

**3a. Regione Puglia — flusso SDO via sistema Edotto** *(fonte regionale primaria)*
- **Ente**: Regione Puglia; sistema informativo sanitario regionale **Edotto** (N-SISR, in esercizio dal 2012, sviluppato da Exprivia); Uffici SDO/Flussi delle ASL.
- **Contenuto**: SDO complete (anagrafica separata + dati clinici: diagnosi/procedure ICD-9-CM, DRG, reparto, struttura, comune di residenza). Cadenza mensile → invio al Ministero entro 45 giorni.
- **URL**: https://www.sanita.puglia.it/edotto/ ; uffici SDO delle ASL (es. https://www.sanita.puglia.it/ricerca_det/-/journal_content/56/36067/).
- **Granularità**: per struttura/ASL/comune di residenza; potenzialmente per provincia.
- **Limiti**: microdati NON open — accesso riservato agli enti SSR; per ricerca serve richiesta formale/autorizzazione (dati sensibili).

**3b. Ministero della Salute — Rapporto annuale attività di ricovero ospedaliero (SDO)** *(fonte nazionale primaria)*
- **URL**: https://www.salute.gov.it/ (sezione documentazione, "Rapporto annuale sull'attività di ricovero ospedaliero"); Rapporti SDO 2016, 2018, 2019, 2020, 2021, 2022, 2023, 2024 tutti disponibili.
- **Contenuto**: analisi descrittive su base NSIS/SDO; tabelle per Regione di ricovero (dimissioni, DRG, degenza media, mobilità).
- **Formato**: PDF + tabelle elettroniche (Excel).
- **Granularità**: prevalentemente regionale nel rapporto pubblico; dettaglio provinciale/ASL non standard nel PDF.
- **Copertura**: annuale, copre l'intero decennio.

**3c. Open data Ministero della Salute — dati.salute.gov.it**
- **URL**: https://www.dati.salute.gov.it/ (tag "SDO", "Ricoveri ospedalieri", "Dimissioni").
- **Formato**: CSV/JSON/XML, licenza IODL 2.0.
- **Granularità**: aggregati (per struttura/ASL/regione a seconda del dataset).
- **Limiti**: dataset aggregati, non microdati paziente.

**3e. PNE — Programma Nazionale Esiti (AGENAS)** *(aggiunto 01/10/2026)*
- **Ente**: AGENAS, per il Ministero della Salute. Fonte dei dati: flusso **SDO** nazionale integrato con l'**Anagrafe Tributaria** per il follow-up della mortalità.
- **URL**: <https://pne.agenas.it/> — **API JSON pubblica non documentata**: `https://pne.agenas.it/pne` (`/edizioni`, `/indicatori`, `/asl`, `/valori/by?...`), nessuna chiave.
- **Contenuto rilevante**: indicatori di **ospedalizzazione dei residenti** per **BPCO** (cod. 56), **asma adulti** (47), **asma pediatrico** (46), **influenza** (44), più ipertensione e scompenso; e indicatori di esito (BPCO riacutizzata: mortalità e riammissioni a 30 giorni). Edizione corrente **2025**, con serie storica per anno.
- **Granularità**: **ASL di residenza** e struttura di ricovero; nessun distretto.
- **Licenza**: **non dichiarata** — da chiarire con AGENAS.
- Scheda tecnica con endpoint, parametri ed esempio verificato (ASL Lecce, BPCO: 1.425 ricoveri, tasso grezzo 2,16‰): `data/dataset/salute/pne_agenas/PNE_AGENAS.md`.

**3f. Eurostat — decessi settimanali per provincia** *(aggiunto 01/10/2026)*
- **URL**: API `https://ec.europa.eu/eurostat/api/dissemination/statistics/1.0/data/demo_r_mwk3_t?format=JSON&geo=ITF45`, licenza **CC BY 4.0**.
- **Contenuto**: decessi **per settimana e provincia (NUTS 3)**, 2011-W01 → 2026-W27 per Lecce/Brindisi/Taranto; cause di morte solo a NUTS 2 (Puglia).
- **Uso previsto**: validazione per ridondanza dei decessi comunali ISTAT. Scheda: `data/dataset/salute/eurostat/Eurostat.md`, che chiarisce anche che **"ESDS" non è una fonte dati** ma il servizio di assistenza di Eurostat.

> **Verifica del 01/10/2026 (chiamate reali).** Sul portale ci sono tre dataset SDO: *dimissioni per azienda sanitaria e tipologia di ricovero per traumatismo o intossicazione* (**solo anno 2022**, per azienda, con i valori piccoli oscurati da `***`), *dimissioni per fasce d'età e sesso* (per istituto) e *dimissioni per istituto e tipologia di dimissione*. Sono CSV statici, **senza diagnosi e senza comune di residenza** → non utilizzabili per correlare i ricoveri con la qualità dell'aria. Il dataset regionale "Assistenza ospedaliera" su dati.puglia.it copre il **solo 2014**. Conclusione: **nessuna fonte pubblica dà i ricoveri per causa respiratoria a grana distretto** (v. `data/dataset/salute/Lista_dataset_salute.md`, punti aperti); da valutare solo PNE/AGENAS, non ancora verificato.

**3d. Regione Puglia — Ufficio Statistico**
- **URL**: https://www.regione.puglia.it/web/ufficio-statistico (es. rielaborazione "Rapporto attività di ricovero ospedaliero. Anno 2019": Puglia 457.648 dimissioni, tasso ospedalizzazione std 114,79/1.000).
- **Contenuto**: rielaborazioni regionali dei dati SDO ministeriali.

### CATEGORIA 4 — CALORE URBANO / UHRI *(aggiunta 01/10/2026; definizione e fonti chiuse lo stesso giorno)*

Terzo parametro del progetto: **UHRI = Urban Heat Island (UHI) Mitigation & Resilience**, la misura delle **isole di calore urbano** per comune, da correlare con mortalità/ricoveri. Non è la sola copertura arborea (prima formulazione, superata): la misura è la **temperatura**, il verde e il suolo impermeabile sono i **fattori di mitigazione**. Dettaglio completo, licenze, limiti e punti aperti in `data/dataset/calore/Lista_dataset_calore.md`.

**4α. Copernicus ERA5-Land** *(fonte primaria dell'esposizione al calore)*
- **Ente**: Copernicus Climate Change Service (CDS).
- **Contenuto**: temperatura dell'aria a 2 m oraria, 0,1° (~9 km), dal 1950 a oggi → media/massima/minima giornaliera per comune.
- **URL**: https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land — licenza CC BY (Copernicus); accesso con `cdsapi`, già dipendenza del progetto.
- **Limiti**: rianalisi (modello), non misura; ~9 km non distingue centro e campagna dentro il comune.

**4β. ARPA Puglia — rete meteo** *(validazione per ridondanza)*
- **Contenuto**: temperatura oraria misurata e validata, 5 stazioni provinciali + 19 co-localizzate con la RRQA; campi e codici di validazione in `data/dataset/calore/arpa_meteo/ARPA_Meteo.md`.
- **URL**: https://dati.puglia.it/ckan/dataset/dati-meteo-rrqa-2024 — licenza CC BY 4.0, datastore SQL.
- **Limiti**: solo 2023-2024 (API storica su `cloud.arpa.puglia.it` irraggiungibile, host legacy senza endpoint meteo).

**4γ. C3S / EEA — UrbClim "UHI intensity"** *(scartata: copertura)*
- **Contenuto**: intensità dell'isola di calore estiva, raster 100 m, da simulazioni UrbClim su ERA5.
- **URL**: https://cds.climate.copernicus.eu/datasets/sis-urban-climate-cities · https://sdi.eea.europa.eu/catalogue/srv/api/records/45b703bb-d4f3-4eaa-8b73-13fde2041f01 — CC BY 4.0.
- **Limite decisivo**: **100 città europee**, in Puglia solo Bari, nessuna nel Salento; dataset CDS **deprecato dal 10/05/2024**. È la ragione per cui l'isola di calore va calcolata da noi.

**4δ. Landsat Collection 2 Level-2 Surface Temperature** *(rimandata dopo l'MVP)*
- **Contenuto**: temperatura superficiale a 30 m dal 1984 → intensità SUHI per comune (urbano − rurale) sulla stagione calda.
- **URL**: https://www.usgs.gov/landsat-missions/landsat-collection-2-level-2-science-products — nessuna restrizione d'uso; accesso STAC senza chiave.
- **Limiti**: ~1 scena ogni 8-16 giorni solo a cielo sereno; raster e dipendenze nuove (`rasterio`/GDAL).

**4a. Copernicus Land Monitoring Service — Tree Cover Density (TCD)** *(fattore di mitigazione: copertura arborea)*
- **Ente**: Copernicus Land Monitoring Service.
- **Contenuto**: % di copertura arborea per pixel, raster 10 m (annuale dal 2018) o 20 m (triennale 2012/2015/2018), copertura pan-europea.
- **URL**: https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover
- **Granularità**: raster — serve statistica zonale sui confini comunali (`data/territorio/confini/comuni_salento.geojson`), stesso problema metodologico già aperto per CAMS.
- **Copertura**: unica fonte trovata con copertura di **tutti i 146 comuni** del Salento (non solo capoluoghi).
- **Limiti**: nessuna API "per comune"; aggiornamento annuale, non quotidiano; licenza Copernicus esatta da confermare.

**4b. ESA WorldCover**
- **Contenuto**: copertura del suolo globale 10 m con classe "Tree cover" (≥10% copertura), edizioni 2020 e 2021.
- **URL**: https://esa-worldcover.org/en — licenza CC BY 4.0.
- **Ruolo proposto**: riscontro indipendente di Copernicus TCD (ridondanza come già fatto per l'aria), non fonte primaria (solo 2 anni, classe binaria non percentuale).

**4c. ISTAT — Dati ambientali nelle città (Verde urbano)**
- **Contenuto**: superficie di verde urbano per comune, dal 2000, dati geografici dal 2019.
- **Limite decisivo**: copre solo i **109 capoluoghi di provincia** → nel Salento solo Lecce, Brindisi, Taranto. Insufficiente come fonte primaria per i 146 comuni; utile solo come riscontro sui tre capoluoghi.

**4d. Copernicus Land Monitoring Service — Imperviousness Density** *(fattore di mitigazione: suolo impermeabile, aggiunta 01/10/2026)*
- **Contenuto**: grado di sigillatura del suolo per pixel (0-100%), raster 10 m e 100 m, edizione 2018, serie triennale.
- **URL**: https://land.copernicus.eu/en/products/high-resolution-layer-imperviousness/imperviousness-density-2018 — licenza Copernicus (testo da confermare).
- **Perché**: il suolo sigillato spiega il calore **notturno**, la chioma arborea quello diurno.

**4e. Mortalità da caldo già aggregata: non esiste per il Salento** — ISS/SiSMG copre 54 città (nel Salento solo Taranto, nessun dato grezzo) e l'indicatore ISPRA "Ondate di calore e mortalità" usa la stessa base. Il caldo si incrocia **per data** con i decessi comunali giornalieri del dataset salute. Alternative valutate e scartate per la grana (Sentinel-3 LST ~1 km, ERA5-HEAT/UTCI 0,25°): v. `data/dataset/calore/Lista_dataset_calore.md`.

### Note su granularità e "zone"
- **Aria**: dato puntuale per stazione → occorre associare ogni stazione a un comune/zona e interpolare (o usare CAMS/EEA per aree scoperte).
- **Salute**: mortalità disponibile fino al comune (ISTAT su richiesta; OER atlante 2000-2005; ASL TA 2012-2021); SDO per struttura/ASL/comune di residenza; Registro Tumori per provincia.
- **Calore/UHRI**: la temperatura ERA5-Land è una **griglia** (~9 km) → serve la regola cella → comune, la stessa da decidere per CAMS; copertura arborea e suolo impermeabile sono **raster** (10 m) → statistica zonale sui confini comunali, aggiornamento annuale/triennale.
- **Riferimento distretti**: dati.puglia.it pubblica l'"Anagrafe distretti socio-sanitari" delle ASL, utile per definire le "zone" su base ASL/distretto.

## Recommendations

**Fase 2a — Acquisizione rapida (open data, subito):**
1. **Aria**: scaricare da dati.puglia.it/API ARPA i dataset RRQA + anagrafica stazioni; in parallelo scaricare il dataset accademico **GRINS_AQCLIM / Fusta Moro-Fassò-Rodeschini 2026** (Zenodo, 2013-2023) come base già pulita e validata per le stazioni salentine.
2. **Mortalità**: estrarre da ISTAT (esploradati/HFA) le serie provinciali per LE/TA/BR; scaricare l'Atlante OER 2000-2005 (Excel comunale) come riferimento storico.
3. **Ricoveri**: scaricare i Rapporti SDO ministeriali (Excel) 2016-2024 e gli open data dati.salute.gov.it.

**Fase 2b — Richieste formali (per il dettaglio fine):**
4. Richiedere a **ISTAT Contact Centre** i decessi per comune/causa ICD/età (finalità ricerca), serie dal 1980/2003.
5. Contattare **OER/AReSS Puglia** e la **S.C. Statistica ed Epidemiologia ASL Taranto** per mortalità comunale aggiornata (post-2005) e per capire se il "ESDO" citato nel progetto coincide con una di queste.
6. Richiedere alla **Regione Puglia (Edotto/ASL)** l'accesso ai microdati SDO per ASL/comune, con la necessaria autorizzazione al trattamento dati.

**Fase 2c — Contatto strategico:**
7. Interpellare il **Centro Salute Ambiente (CSA) Puglia**: è l'unico ente che già integra ambiente e salute su Taranto-Brindisi-Lecce (Progetto Jonico-Salentino, studi di coorte, "Spatial Data Infrastructure Salute e Ambiente"). Potrebbe fornire dati già incrociati o metodologia di riferimento, evitando di ricostruire tutto da zero.

**Criterio di scelta della granularità ("zone"):** raccomando di adottare il **comune di residenza** come unità base (massimo comune denominatore tra mortalità ISTAT/OER, SDO e popolazione), aggregando poi per **distretto socio-sanitario/ASL** per le analisi sanitarie e associando l'aria via stazione più vicina + interpolazione CAMS. **Soglia di revisione**: se la copertura di stazioni ARPA per zona risulta < ~1 stazione, passare obbligatoriamente al dato modellistico CAMS/EEA come layer primario per l'aria.

## Caveats
- **Nessun dataset unico "aria+salute per zona" già pronto**: va costruito incrociando le fonti sopra; il CSA Puglia è il precedente più vicino ma i suoi output sono studi, non dataset aperti riutilizzabili.
- **Disallineamento di granularità e privacy**: l'aria è puntuale (stazione), la salute è areale (comune/ASL); i microdati SDO e la mortalità comunale per causa sono dati sensibili e richiedono autorizzazioni.
- **"ESDO" non confermato**: acronimo non esistente come ente ufficiale; assunzione (OER / ASL TA Epidemiologia e Statistica) da validare con il committente del progetto.
- **Copertura temporale OER incerta** per le tavole sul portale attuale (pagine non ispezionabili automaticamente): da verificare manualmente in browser.
- **Ritardi di pubblicazione**: mortalità ISTAT per causa ~2 anni; Rapporti SDO ministeriali con ritardo pluriennale (SDO 2021 pubblicato feb. 2024); dati aria recenti provvisori fino a validazione definitiva.
- **Dati modellistici (CAMS) ≠ misure**: usarli con cautela per analisi epidemiologiche fini a scala sub-comunale.