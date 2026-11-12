# RICERCA DATASET — Fase 2 (ricognizione fonti pubbliche)

*Documento 3 (v2) — Sintesi della ricognizione svolta il 18/09/2026 su Claude.ai. Le fonti e gli URL provengono da una ricerca web automatica: **verificare ogni link e ogni copertura temporale prima di costruire la pipeline**.*

## Parametri di ricerca confermati da Matteo

- **Territorio:** province di **Lecce, Taranto e Brindisi**, denominate collettivamente **"Salento"**. *(Aggiornamento 18/09/2026: la suddivisione in zone è decisa — v. sotto.)*
- **Zonizzazione (decisa il 18/09/2026):** il Salento è diviso in **distretti socio-sanitari** (non comuni singoli, non cluster arbitrari). I confini di ogni distretto vanno delineati dalle mappe geografiche ASL delle tre province; la forma dei distretti serve anche per la mappa della dashboard.
- **Salute:** **tutte le cause** (non solo respiratorie), per poter rilevare anche incidenze non respiratorie come confronto/controllo.
- **Finestra temporale:** copertura **minima 5 anni** (aggiornamento 18/09/2026); resta un obiettivo restare vicini a ~10 anni (2016-2026) se i dati effettivamente disponibili lo permettono.
- **Categorie:** qualità dell'aria nel tempo, cause di morte, ricoveri ospedalieri (SDO).
- **Fonti dati:** solo fonti pubbliche — nessun dataset fornito dal partner aziendale.
- **Accesso ai dati:** chiamate API dirette alle fonti pubbliche, senza database intermedio persistente (decisione 18/09/2026, v. docs/Regole_dei_dati.md).

## Conclusione principale

**Non esiste un dataset "aria + salute per zona" già pronto: va costruito incrociando fonti separate.** Le granularità sono disallineate: l'aria è **puntuale** (stazione), la salute è **areale** (comune / ASL / provincia).

## Chiarimento su "ESDO"

Nessuna fonte con questo acronimo esiste in Puglia. Con ogni probabilità è un riferimento informale all'**OER Puglia** (Osservatorio Epidemiologico Regionale) e/o alla **S.C. Statistica ed Epidemiologia dell'ASL Taranto**; entrambi si basano sull'archivio **ReNCaM/ReMo** delle schede di morte ISTAT.

> **Aggiornamento 18/09/2026:** Matteo ha chiarito che il nome corretto non è "ESDO" ma **ESDS — European Statistical Data Support**. Questo nome è diverso dall'ipotesi OER/ASL Taranto sopra: la ricerca web non ha trovato un ente sanitario italiano con questo acronimo, quindi **va verificato con Matte Lia/il referente aziendale l'ente esatto e l'URL ufficiale di ESDS** prima di costruire la pipeline su questa fonte. Fino alla verifica, le fonti candidate (OER Puglia, ASL Taranto) restano valide come fallback operativo.

## Categoria 1 — Qualità dell'aria

| Fonte | Contenuto | Granularità | Accesso / formato | Note |
|---|---|---|---|---|
| **ARPA Puglia — RRQA** (fonte primaria) | PM10, PM2.5, NO2, O3, SO2, benzene, CO. Rete di 53 stazioni fisse (41 pubbliche + 12 private) + stazioni di interesse locale | Singola stazione (lat/long) | CSV / JSON / API REST. Portale `dati.puglia.it/ckan/organization/arpa-puglia`; API `dati.arpa.puglia.it/openapi/index.html`; storici `arpa.puglia.it/pagina3139_dati-storici-qualit-dellaria.html` | Copre 2016-2026. Dati recenti provvisori fino a validazione. Copertura spaziale non uniforme: non tutti i comuni hanno una stazione |
| **OpenAQ** | PM2.5, PM10, O3, NO2, SO2, CO | Stazione | API v3 (`docs.openaq.org`), API key gratuita | Aggregatore (origine EEA/ARPA), non fonte primaria. Da verificare quali stazioni salentine siano presenti |
| **Copernicus / CAMS** (fallback) | Reanalisi europea della qualità dell'aria, ensemble di 11 modelli | Griglia **0.1° (~10 km)** | NetCDF/GRIB via Atmosphere Data Store (`ads.atmosphere.copernicus.eu`), registrazione gratuita | Dato **modellato, non misurato**. Utile per zone senza centraline |
| **EEA** | Osservazioni armonizzate UE (AirBase / e-Reporting) | Stazione | European Air Quality Portal (`aqportal.discomap.eea.europa.eu`) | Sono le stesse stazioni ARPA riportate a livello UE |
| **Dataset accademico pulito** | Statistiche giornaliere 2013-2023 su 744 stazioni italiane (da EEA e Copernicus) | Stazione | Zenodo (progetto GRINS). Fusta Moro, Fassò, Rodeschini, *Scientific Data* 2026, DOI 10.1038/s41597-026-07712-3 | Buona base già validata per le stazioni salentine |
| **ISPRA / SNPA** | Emissioni disaggregate per provincia (1990-2023) | Provincia | `emissioni.sina.isprambiente.it` | Complementare, non prioritaria |

## Categoria 2 — Cause di morte

| Fonte | Contenuto | Granularità | Limiti |
|---|---|---|---|
| **ISTAT — decessi e cause di morte** (primaria) | Causa iniziale (European Short List / ICD), serie dal 2003, per età, sesso, ecc. Banca dati: `esploradati.istat.it` | Provincia nella banca dati pubblica; **comune su richiesta** al Contact Centre (per ricerca) | Diffusione con ~2 anni di ritardo; il dettaglio comunale per causa richiede richiesta motivata |
| **ISTAT — Health for All Italia** | ~4.000 indicatori (mortalità per causa, attività ospedaliera per patologia). Ultimo aggiornamento straordinario aprile 2026 | Provincia/regione | Software desktop (solo Windows), non un semplice CSV |
| **ISTAT — mortalità tempestiva** | Decessi totali giornalieri (senza causa), serie dal 2011 | Comune / sesso / classe d'età | Nessun dettaglio per causa |
| **OER Puglia** (candidato "ESDO") | *Atlante delle cause di morte* 2000-2005 (PDF + Excel per comune); sezioni "Tavole mortalità" e "Atlante-Trend tumori" sul portale `sanita.puglia.it/web/oer` | Comune | Atlante pubblico fermo al 2005; copertura delle sezioni attuali **da verificare a mano nel browser**. Funzioni in trasferimento ad AReSS dal 2024 |
| **ASL Taranto — S.C. Statistica ed Epidemiologia** (candidato "ESDO") | Rapporto "Le cause di mortalità in provincia di Taranto" 2012-2021, ICD-10 | Comune (solo provincia di Taranto) | Formato report/PDF, non dataset grezzo |
| **Registro Tumori Puglia** | Incidenza, mortalità, prevalenza tumorale | Provincia | Solo oncologia; report PDF |
| **AReSS Puglia — Open Salute Puglia / PugliaStat** *(aggiunto 22/09/2026)* | Malattie croniche (incl. BPCO), 25+ tipologie tumorali, ospedalizzazioni e decessi | **Provincia / distretto / comune** (PugliaStat) | Portale web (`opensalute.aress.regione.puglia.it`, `aress.regione.puglia.it/.../pugliastat`); formato di export e licenza da verificare manualmente. AReSS ha assorbito le funzioni OER dal 2024 (DGR 1396/2024) |

## Categoria 3 — Ricoveri ospedalieri (SDO)

| Fonte | Contenuto | Granularità | Accesso |
|---|---|---|---|
| **Regione Puglia — flusso SDO / Edotto** | SDO complete (diagnosi ICD-9-CM, DRG, reparto, comune di residenza) | Struttura / ASL / comune di residenza | **Microdati non open**: solo enti SSR; per ricerca serve richiesta formale e autorizzazione |
| **Ministero della Salute — Rapporto annuale SDO** | Analisi descrittive; rapporti 2016-2024 disponibili | Prevalentemente regionale | PDF + Excel |
| **Open data Ministero della Salute** (`dati.salute.gov.it`, tag "SDO") | Dataset aggregati, licenza IODL 2.0 | Struttura / ASL / regione | CSV / JSON / XML |
| **Regione Puglia — Ufficio Statistico** | Rielaborazioni regionali dei dati SDO ministeriali | Regione | Web |

## Strategia di armonizzazione proposta

1. **Unità base = comune di residenza** (massimo comune denominatore tra mortalità, SDO e popolazione).
2. **Aggregazione per distretto socio-sanitario** per le analisi sanitarie — **decisa il 18/09/2026** (non più solo "proposta"): il Salento (Lecce, Brindisi, Taranto) è diviso in distretti socio-sanitari ASL, i cui confini vanno delineati dalle mappe geografiche delle tre province. Riferimento: dataset "Anagrafe distretti socio-sanitari" su `dati.puglia.it`.
3. **Aria:** associare ogni stazione al comune/distretto; per le zone scoperte usare interpolazione o CAMS/EEA.
4. **Soglia di revisione:** se una zona ha meno di ~1 stazione ARPA, usare CAMS/EEA come layer primario per l'aria.
5. **Accesso ai dati:** nessun database intermedio — i dati vengono recuperati via chiamate API dirette alle fonti a ogni aggiornamento (decisione 18/09/2026).

## Piano operativo suggerito dalla ricerca

- **Fase 2a — open data subito:** ARPA (RRQA + anagrafica stazioni) e dataset accademico su Zenodo; ISTAT provinciale per LE/TA/BR e Atlante OER (Excel comunale, storico); Rapporti SDO ministeriali 2016-2024 e `dati.salute.gov.it`.
- **Fase 2b — richieste formali:** ISTAT Contact Centre (decessi per comune/causa/età); OER/AReSS e ASL Taranto (mortalità comunale post-2005, e per validare "ESDO"); Regione Puglia/Edotto (microdati SDO, con autorizzazione).
- **Fase 2c — contatto strategico:** **Centro Salute Ambiente (CSA) Puglia** (`sanita.puglia.it/web/csa`, Progetto Jonico-Salentino). È il precedente più vicino a OneHealth: potrebbe fornire dati già incrociati o metodologia.

## Cautele

- Le richieste formali richiedono tempi che potrebbero non stare dentro la scadenza di ottobre: **per l'MVP conviene basarsi sui soli open data (Fase 2a)** e trattare la Fase 2b come sviluppo futuro documentato in tesi.
- Microdati SDO e mortalità comunale per causa sono **dati sensibili**: non vanno mai committati nel repo.
- Dati CAMS ≠ misure: cautela per analisi sub-comunali.
- Correlazione aria-salute: analisi **esplorativa, non causale** (fumo, età, comorbidità, aria indoor sono confondenti).
