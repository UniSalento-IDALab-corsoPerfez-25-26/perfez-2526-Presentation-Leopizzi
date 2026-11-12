# Registro citazioni e fonti esterne

Questo file tiene traccia di **tutte le fonti esterne al progetto** (siti istituzionali, portali dati, documentazione API, letteratura scientifica, ecc.) usate per raccogliere informazioni, dati o riferimenti per OneHealth, in modo da poterle citare in modo corretto e uniforme in tesi.

- **Stile di citazione: Chicago** (*Notes-Bibliography*: nota a piè di pagina completa + voce bibliografica), nella variante accademica **Turabian** — stile CSL `chicago-note-bibliography` / `turabian-fullnote-bibliography`.
- **Regola di progetto (01/10/2026):** ogni bibliografia o citazione prodotta per OneHealth, ora e in futuro, usa **sempre Chicago**; nessun altro stile va proposto o usato senza che Matteo lo chieda.
- **Lingua delle voci:** italiano, salvo titoli originali di pagine/fonti in altra lingua (mantenuti come da originale).
- **Relazione con la tesi:** le voci qui raccolte sono la base per popolare `tesi_finale/capitoli/bibliografia.tex`. Diversi capitoli (`introduzione.tex`, `capitolo_1.tex`) contengono già riferimenti `\cite{TODO_...}` o `\cite{...}` non ancora risolti: la colonna **Chiave** propone l'identificativo da usare in LaTeX quando la bibliografia verrà popolata.
- **Aggiornamento:** ogni volta che si usa un nuovo sito, dataset, documento o paper come fonte di informazioni/dati per il progetto, va aggiunta qui una voce, prima di citarlo in un documento `.md` o in tesi.

## Come si usa (promemoria stile Turabian full-note)

Per ogni fonte sono riportate tre forme:

1. **Nota completa** (*full note*): usata alla prima citazione della fonte in un capitolo, in nota a piè di pagina.
2. **Nota breve** (*short note*): usata per le citazioni successive della stessa fonte nello stesso documento.
3. **Voce bibliografica**: usata nell'elenco finale della bibliografia, in ordine alfabetico per autore/ente.

Per le pagine web istituzionali senza una data di pubblicazione/ultima modifica dichiarata (come i casi qui sotto), Turabian richiede di indicare la **data di consultazione**.

---

## Indice fonti

| Chiave (LaTeX) | Ente/Autore | Titolo pagina | Categoria | Data consultazione |
|---|---|---|---|---|
| `distretti_asl_lecce` | ASL Lecce | Distretti Socio-Sanitari | Territorio | 27 settembre 2026 |
| `distretti_asl_brindisi` | ASL Brindisi | Distretti Socio-Sanitari | Territorio | 27 settembre 2026 |
| `distretti_asl_taranto` | ASL Taranto | Distretti Socio-Sanitari | Territorio | 27 settembre 2026 |
| `arpa_puglia_sito` | ARPA Puglia | Sito istituzionale | Dati ambientali | 27 settembre 2026 |
| `arpa_puglia_api` | Cazzati, Liotino (ARPA Puglia) | Linea guida per la interoperabilità ai servizi API | Dati ambientali | — (documento datato 09/10/2023) |
| `eea_aqds` | European Environment Agency | Air Quality Download Service | Dati ambientali | 28 settembre 2026 |
| `openaq` | OpenAQ | Piattaforma e API v3 | Dati ambientali | 1 ottobre 2026 |
| `cams_reanalisi` | Copernicus Atmosphere Monitoring Service | CAMS European air quality reanalyses | Dati ambientali | 28 settembre 2026 |
| `cams_previsioni` | Copernicus Atmosphere Monitoring Service | CAMS European air quality forecasts (tipo `analysis`) | Dati ambientali | 28 settembre 2026 |
| `dlgs_155_2010` | Repubblica Italiana | D.Lgs. 13 agosto 2010, n. 155 (qualità dell'aria) | Normativa aria | — (GU 15/09/2010) |
| `who_aqg_2021` | World Health Organization | WHO Global Air Quality Guidelines (2021) | Normativa aria | 11 ottobre 2026 |
| `dir_ue_2024_2881` | Parlamento europeo e Consiglio | Direttiva (UE) 2024/2881 (qualità dell'aria) | Normativa aria | 11 ottobre 2026 |
| `istat_dati_mortalita` | ISTAT | Dati di mortalità: cosa produce l'Istat | Dati sanitari | 1 ottobre 2026 |
| `istat_cause_morte` | ISTAT | Decessi e cause di morte (banca dati / API SDMX) | Dati sanitari | 1 ottobre 2026 |
| `aress_pugliastat` | AReSS Puglia | PugliaStat | Dati sanitari | 1 ottobre 2026 |
| `chieti_pugliastat_2015` | Chieti, Nannavecchia, Bisceglia | Lo stato di salute pugliese on demand: un nuovo strumento informativo | Dati sanitari | — (comunicazione a congresso, 2015) |
| `aress_opensalute` | AReSS Puglia | Open Salute Puglia | Dati sanitari | 1 ottobre 2026 |
| `aress_opendata` | AReSS Puglia | Open data su dati.puglia.it | Dati sanitari | 1 ottobre 2026 |
| `istat_hfa` | ISTAT | Health for All - Italia | Dati sanitari | 1 ottobre 2026 |
| `pne_agenas` | AGENAS | Programma Nazionale Esiti (PNE) | Dati sanitari | 1 ottobre 2026 |
| `eurostat_decessi_settimanali` | Eurostat | Deaths by week and NUTS 3 region (demo_r_mwk3_t) | Dati sanitari | 1 ottobre 2026 |
| `istat_esds` | ISTAT | European data support (ESDS) | Dati sanitari | 1 ottobre 2026 |
| `istat_bilancio_mensile` | ISTAT | Bilancio demografico mensile (demo.istat.it) | Dati sanitari | 1 ottobre 2026 |
| `istat_verde_urbano` | ISTAT | Ambiente urbano - Verde urbano (esploradati, `609_1_DF_DCCV_URBANENV_18`) | Dati calore (confronto) | 18 ottobre 2026 |
| `sismg_ministero` | Ministero della Salute | Sistema di sorveglianza della mortalità giornaliera (SiSMG) | Dati sanitari | 1 ottobre 2026 |
| `iss_profilidisalute` | Istituto Superiore di Sanità | profilidisalute.it | Dati sanitari | 1 ottobre 2026 |
| `iss_indirizzario_rencam` | Istituto Superiore di Sanità | Indirizzario dei registri di mortalità (ReNCaM) | Dati sanitari | 1 ottobre 2026 |
| `iss_respivirnet` | Istituto Superiore di Sanità | Sorveglianza delle infezioni respiratorie acute (RespiVirNet) | Dati sanitari | 1 ottobre 2026 |
| `rtp_incidenza_2024` | AReSS Puglia / Registro Tumori Puglia | I tumori in Regione Puglia. Dati di incidenza 2013-2021 | Dati sanitari | 1 ottobre 2026 |
| `asl_lecce_registro_tumori` | ASL Lecce | Registro Tumori | Dati sanitari | 1 ottobre 2026 |
| `iungman2023` | Iungman et al. | Cooling cities through urban green infrastructure | Calore / UHI | — (articolo, 2023) |
| `huang2023` | Huang et al. | Economic valuation of temperature-related mortality attributed to urban heat islands | Calore / UHI | — (articolo, 2023) |
| `cuerdo2023` | Cuerdo-Vilches et al. | Impact of urban heat islands on morbidity and mortality in heat waves (Spain) | Calore / UHI | — (articolo, 2023) |
| `pappaccogli_uhi_lecce_2024` | Pappaccogli, Giangrande, Esposito, Donateo, Lionello, Buccolieri | Dynamics of urban heat island intensity in Lecce, Italy | Calore / UHI | — (articolo, 2024) |
| `scarinzi_epiair2_2013` | Scarinzi et al. | Inquinamento atmosferico e ricoveri ospedalieri urgenti in 25 città italiane (EpiAir2) | Simulazione salute | — (articolo, 2013) |
| `michelozzi_phewe_2009` | Michelozzi et al. | High temperature and hospitalizations for cardiovascular and respiratory causes in 12 European cities | Simulazione salute | — (articolo, 2009) |
| `campagna_adi_ps_2021` | Campagna et al. | Determinants associated with the risk of emergency department visits among patients receiving integrated home care services | Simulazione salute | 25 ottobre 2026 |
| `qs_annuario_ssn_2023` | Quotidiano Sanità (dati Annuario statistico SSN 2023) | Accessi al pronto soccorso 2013-2023 | Simulazione salute | 25 ottobre 2026 |
| `italpress_adi_2023` | Italpress | Assistenza domiciliare integrata agli over 65, 2023 | Simulazione salute | 25 ottobre 2026 |
| `era5_land` | Copernicus Climate Change Service | ERA5-Land hourly data from 1950 to present | Calore / UHI | 1 ottobre 2026 |
| `arpa_meteo_rrqa` | ARPA Puglia | Dati di monitoraggio meteorologico RRQA (dati.puglia.it) | Calore / UHI | 1 ottobre 2026 |
| `c3s_urban_climate_cities` | Copernicus Climate Change Service / VITO | Climate variables for cities in Europe from 2008 to 2017 | Calore / UHI | 1 ottobre 2026 |
| `eea_uhi_intensity` | European Environment Agency | Urban Heat Island (UHI) intensity modelling, Jan. 2020 | Calore / UHI | 1 ottobre 2026 |
| `copernicus_tcd` | Copernicus Land Monitoring Service | Tree Cover Density 2018-present (raster 10 m) | Calore / UHI | 1 ottobre 2026 |
| `copernicus_imperviousness` | Copernicus Land Monitoring Service | Imperviousness Density 2018 (raster 10 m e 100 m) | Calore / UHI | 1 ottobre 2026 |
| `landsat_c2_st` | U.S. Geological Survey | Landsat Collection 2 Level-2 Science Products (Surface Temperature) | Calore / UHI | 1 ottobre 2026 |
| `esa_worldcover` | European Space Agency | ESA WorldCover | Calore / UHI | 1 ottobre 2026 |
| `openbmb_minicpm` | OpenBMB | MiniCPM (repository GitHub) | Modulo AI | 27 ottobre 2026 |
| `openbmb_minicpm5_2b` | OpenBMB | MiniCPM5-2B (scheda del modello, Hugging Face) | Modulo AI | 27 ottobre 2026 |
| `aa_minicpm5_2b` | Artificial Analysis | OpenBMB releases MiniCPM5-2B | Modulo AI | 27 ottobre 2026 |
| `qwen35_4b` | Qwen Team (Alibaba Cloud) | Qwen3.5-4B (scheda del modello, Hugging Face) | Modulo AI | 27 ottobre 2026 |
| `ollama` | Ollama | Ollama (repository GitHub) | Modulo AI | 1 novembre 2026 |
| `lewis_rag_2020` | Lewis et al. | Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks | Modulo AI | — (articolo, 2020) |
| `piano_cronicita_2016` | Ministero della Salute | Piano nazionale della cronicità (Accordo Stato-Regioni 15/09/2016) | Medicina di iniziativa | 10 novembre 2026 |
| `dm_77_2022` | Ministero della Salute | DM 23 maggio 2022, n. 77 — assistenza territoriale | Medicina di iniziativa | 10 novembre 2026 |

---

## Territorio — Distretti socio-sanitari

Fonti usate per la zonizzazione del Salento in distretti socio-sanitari (v. `Regole_dei_dati.md` del repository Backend e `data/territorio/`).

### ASL Lecce

- **Nota completa:** Azienda Sanitaria Locale di Lecce, "Distretti Socio-Sanitari," Sanità Puglia, consultato il 27 settembre 2026, https://www.sanita.puglia.it/web/asl-lecce/distretti-socio-sanitari.
- **Nota breve:** ASL Lecce, "Distretti Socio-Sanitari."
- **Voce bibliografica:** Azienda Sanitaria Locale di Lecce. "Distretti Socio-Sanitari." Sanità Puglia. Consultato il 27 settembre 2026. https://www.sanita.puglia.it/web/asl-lecce/distretti-socio-sanitari.

### ASL Brindisi

- **Nota completa:** Azienda Sanitaria Locale di Brindisi, "Distretti Socio-Sanitari," Sanità Puglia, consultato il 27 settembre 2026, https://www.sanita.puglia.it/web/asl-brindisi/distretti-socio-sanitari.
- **Nota breve:** ASL Brindisi, "Distretti Socio-Sanitari."
- **Voce bibliografica:** Azienda Sanitaria Locale di Brindisi. "Distretti Socio-Sanitari." Sanità Puglia. Consultato il 27 settembre 2026. https://www.sanita.puglia.it/web/asl-brindisi/distretti-socio-sanitari.

### ASL Taranto

- **Nota completa:** Azienda Sanitaria Locale di Taranto, "Distretti Socio-Sanitari," Sanità Puglia, consultato il 27 settembre 2026, https://www.sanita.puglia.it/web/asl-taranto/distretti-socio-sanitari.
- **Nota breve:** ASL Taranto, "Distretti Socio-Sanitari."
- **Voce bibliografica:** Azienda Sanitaria Locale di Taranto. "Distretti Socio-Sanitari." Sanità Puglia. Consultato il 27 settembre 2026. https://www.sanita.puglia.it/web/asl-taranto/distretti-socio-sanitari.

> Nota: le tre pagine ASL sono usate insieme come fonte per l'elenco/i confini dei distretti socio-sanitari; in tesi possono essere citate cumulativamente, es. `\cite{distretti_asl_lecce,distretti_asl_brindisi,distretti_asl_taranto}`, al posto del placeholder attuale `TODO_distretti_asl` (v. `tesi_finale/capitoli/introduzione.tex:20`).

---

## Dati ambientali — Qualità dell'aria

### ARPA Puglia (sito istituzionale)

- **Nota completa:** ARPA Puglia (Agenzia Regionale per la Prevenzione e la Protezione dell'Ambiente), "Home," sito istituzionale, consultato il 27 settembre 2026, https://www.arpa.puglia.it/.
- **Nota breve:** ARPA Puglia, sito istituzionale.
- **Voce bibliografica:** ARPA Puglia (Agenzia Regionale per la Prevenzione e la Protezione dell'Ambiente). Sito istituzionale. Consultato il 27 settembre 2026. https://www.arpa.puglia.it/.

> Nota: questa voce copre il sito ARPA Puglia in generale. Le pagine specifiche già usate come fonte dati (dati storici qualità aria, report RRQA, API) sono elencate con URL puntuali in `data/dataset/aria/Lista_dataset_aria.md` e `ricerca/03_Datasets_List.md` del repository Presentation; se citate singolarmente in tesi andranno aggiunte qui come voci separate (es. `arpa_puglia_rrqa`, `arpa_puglia_api`). Sostituisce/risolve il placeholder `TODO_arpa_puglia` usato in `tesi_finale/capitoli/introduzione.tex:64`.

### ARPA Puglia — Linea guida API (qualità dell'aria)

Documento che definisce il contratto dei dati di qualità dell'aria usati dal progetto (campi, parametri, servizi `QualitaAria`, `Stations`, `Pollutants`). Copia locale: `data/dataset/aria/arpa_puglia/API_ARPA.pdf`.

- **Nota completa:** Pietro Cazzati e Isa Liotino, *Servizio di interoperabilità Open Data Arpa Puglia: Linea guida per la interoperabilità ai servizi API*, Rev_01 (Bari: ARPA Puglia, UOS Sistemi Informativi, 9 ottobre 2023).
- **Nota breve:** Cazzati e Liotino, *Linea guida per la interoperabilità ai servizi API*.
- **Voce bibliografica:** Cazzati, Pietro, e Isa Liotino. *Servizio di interoperabilità Open Data Arpa Puglia: Linea guida per la interoperabilità ai servizi API*. Rev_01. Bari: ARPA Puglia, UOS Sistemi Informativi, 9 ottobre 2023.

> Nota: la guida documenta l'host `cloud.arpa.puglia.it`, irraggiungibile al 27/09/2026; il progetto interroga lo stesso contratto su `old.arpa.puglia.it` (v. `data/dataset/aria/Lista_dataset_aria.md`). In tesi citare questa guida per la struttura dei dati e dichiarare a parte l'host effettivamente usato. Il PDF risulta pubblicato anche tra le risorse dei dataset ARPA su dati.puglia.it (es. `dati-qualita-aria`): se si vuole un URL pubblico nella citazione, verificare prima che quella copia coincida con la Rev_01 locale.

### EEA — Air Quality Download Service

Servizio da cui si prelevano i parquet orari delle stazioni del Salento (E1a verificato, E2a non verificato), con la lista di URL. Licenza CC BY 4.0 (politica di riuso EEA: citare sempre EEA come fonte). Scheda: `data/dataset/aria/eea/EEA.md`.

- **Nota completa:** European Environment Agency, "Air Quality Download Service," catalogo SDI dell'EEA, consultato il 28 settembre 2026, https://sdi.eea.europa.eu/catalogue/srv/eng/catalog.search#/metadata/778ef9f5-6293-4846-badd-56a29c70880d.
- **Nota breve:** EEA, "Air Quality Download Service."
- **Voce bibliografica:** European Environment Agency. "Air Quality Download Service." Catalogo SDI dell'EEA. Consultato il 28 settembre 2026. https://sdi.eea.europa.eu/catalogue/srv/eng/catalog.search#/metadata/778ef9f5-6293-4846-badd-56a29c70880d.

> Chiave LaTeX: `eea_aqds`.

### OpenAQ — Piattaforma e API v3

Aggregatore di misure orarie (per il Salento riprende i dati EEA). Licenza dei dati ODC-BY, da citare con il suo nome. Scheda: `data/dataset/aria/openaq/OpenAQ.md`.

- **Nota completa:** OpenAQ, "OpenAQ," piattaforma e documentazione API v3, consultato il 1° ottobre 2026, https://openaq.org/.
- **Nota breve:** OpenAQ.
- **Voce bibliografica:** OpenAQ. Piattaforma e documentazione API v3. Consultato il 1° ottobre 2026. https://openaq.org/; https://docs.openaq.org/.

> Chiave LaTeX: `openaq`.

### Copernicus CAMS — Rianalisi e analisi europee della qualità dell'aria

Due dataset dell'Atmosphere Data Store, licenza CC BY 4.0: la rianalisi (validata e interim) per gli anni consegnati, l'analisi (`type=analysis` del dataset delle previsioni) per l'anno in corso. Scheda: `data/dataset/aria/copernicus_cams/Copernicus_CAMS.md`. ⏳ Confrontare con la dicitura di citazione delle pagine dei dataset.

- **Nota completa:** Copernicus Atmosphere Monitoring Service, "CAMS European Air Quality Reanalyses," Atmosphere Data Store, consultato il 28 settembre 2026, https://doi.org/10.24381/7cc0465a.
- **Voce bibliografica:** Copernicus Atmosphere Monitoring Service. "CAMS European Air Quality Reanalyses." Atmosphere Data Store. Consultato il 28 settembre 2026. https://doi.org/10.24381/7cc0465a.
- **Voce bibliografica:** Copernicus Atmosphere Monitoring Service. "CAMS European Air Quality Forecasts." Atmosphere Data Store. Consultato il 28 settembre 2026. https://doi.org/10.24381/a4005cee.

> Chiavi LaTeX: `cams_reanalisi`, `cams_previsioni`.

---

## Normativa — Valori di riferimento per la qualità dell'aria

Le tre basi normative e sanitarie usate per l'**indice di salubrità** della dashboard (v. `data/dataset/aria/Valori_Riferimento_Normativi.md`), con cui si confronta ogni inquinante. Valori verificati l'11/10/2026.

### D.Lgs. 155/2010 — qualità dell'aria (norma italiana in vigore)

- **Nota completa:** Repubblica Italiana, *Decreto legislativo 13 agosto 2010, n. 155, Attuazione della direttiva 2008/50/CE relativa alla qualità dell'aria ambiente e per un'aria più pulita in Europa*, Gazzetta Ufficiale della Repubblica Italiana n. 216 del 15 settembre 2010, Supplemento Ordinario n. 217.
- **Nota breve:** D.Lgs. 155/2010.
- **Voce bibliografica:** Repubblica Italiana. *Decreto legislativo 13 agosto 2010, n. 155, Attuazione della direttiva 2008/50/CE relativa alla qualità dell'aria ambiente e per un'aria più pulita in Europa*. Gazzetta Ufficiale della Repubblica Italiana n. 216 del 15 settembre 2010, Supplemento Ordinario n. 217.

> Valori limite negli Allegati VII (O3), XI (SO2, NO2, PM10, PM2.5, CO, benzene) e XII (soglie di informazione e allarme). Recepisce la direttiva 2008/50/CE.

### OMS — WHO Global Air Quality Guidelines (2021)

- **Nota completa:** World Health Organization, *WHO Global Air Quality Guidelines: Particulate Matter (PM2.5 and PM10), Ozone, Nitrogen Dioxide, Sulfur Dioxide and Carbon Monoxide* (Geneva: World Health Organization, 2021), https://iris.who.int/handle/10665/345329.
- **Nota breve:** WHO, *Global Air Quality Guidelines*.
- **Voce bibliografica:** World Health Organization. *WHO Global Air Quality Guidelines: Particulate Matter (PM2.5 and PM10), Ozone, Nitrogen Dioxide, Sulfur Dioxide and Carbon Monoxide*. Geneva: World Health Organization, 2021. https://iris.who.int/handle/10665/345329.

> Linee guida sanitarie (non vincolanti), le più severe. Valori chiave verificati l'11/10/2026 via sintesi IQAir (*New WHO air quality guidelines*, https://www.iqair.com/newsroom/2021-who-air-quality-guidelines); prima della citazione definitiva confrontare con la pubblicazione OMS su IRIS.

### Direttiva (UE) 2024/2881 — qualità dell'aria (rifusione, limiti dal 2030)

- **Nota completa:** Parlamento europeo e Consiglio dell'Unione europea, *Direttiva (UE) 2024/2881 del 23 ottobre 2024 relativa alla qualità dell'aria ambiente e per un'aria più pulita in Europa (rifusione)*, Gazzetta ufficiale dell'Unione europea, serie L, 20 novembre 2024, http://data.europa.eu/eli/dir/2024/2881/oj.
- **Nota breve:** Direttiva (UE) 2024/2881.
- **Voce bibliografica:** Parlamento europeo e Consiglio dell'Unione europea. *Direttiva (UE) 2024/2881 del 23 ottobre 2024 relativa alla qualità dell'aria ambiente e per un'aria più pulita in Europa (rifusione)*. Gazzetta ufficiale dell'Unione europea, serie L, 20 novembre 2024. http://data.europa.eu/eli/dir/2024/2881/oj.

> Valori limite da attenere entro il 1° gennaio 2030, Allegato I. Tabella dei valori verificata l'11/10/2026 sulla *Benchmark analysis* dell'EEA (https://www.eea.europa.eu/en/analysis/publications/air-quality-status-report-2025/benchmark-analysis-against-the-standards-in-the-revised-directive-eu-2024-2881); i valori delle soglie di informazione/allarme dei gas restano da riprendere puntualmente dal testo EUR-Lex prima della citazione.

---

## Dati sanitari — Mortalità, ricoveri e patologie

Fonti del dataset salute, verificate con chiamate reali il 1° ottobre 2026 (v. `data/dataset/salute/istat/ISTAT.md` e `data/dataset/salute/aress_puglia/AReSS_Puglia.md`).

### ISTAT — Dati di mortalità (decessi comunali giornalieri e mensili)

Pagina da cui si prelevano i decessi per comune di residenza, giorno/mese, sesso e classe di età (serie dal 2011, dati provvisori). I file sono ZIP rigenerati a ogni rilascio: in tesi va indicato **quale rilascio** si è usato, oltre alla data di consultazione.

- **Nota completa:** Istituto nazionale di statistica, "Dati di mortalità: cosa produce l'Istat," consultato il 1° ottobre 2026, https://www.istat.it/notizia/dati-di-mortalita-cosa-produce-listat/.
- **Nota breve:** ISTAT, "Dati di mortalità."
- **Voce bibliografica:** Istituto nazionale di statistica. "Dati di mortalità: cosa produce l'Istat." Consultato il 1° ottobre 2026. https://www.istat.it/notizia/dati-di-mortalita-cosa-produce-listat/.

> Licenza: **CC BY 4.0** (note legali ISTAT, https://www.istat.it/note-legali/). Rilascio usato nella verifica: giugno 2026, file `decessi-comunali-giornalieri-provvisori-4.zip` (copertura 01/01/2011-30/06/2026).

### ISTAT — Decessi e cause di morte (banca dati e API SDMX)

Serie provinciali di decessi per causa iniziale secondo la European Short List (2003-2023), prelevate via web service SDMX.

- **Nota completa:** Istituto nazionale di statistica, "Decessi e cause di morte," IstatData, dataflow `IT1,39_494_DF_DCIS_CMORTE1_RES_1,1.0`, consultato il 1° ottobre 2026, https://esploradati.istat.it/databrowser/#/it/dw/categories/IT1,Z0810HEA,1.0/HEA_DEATH.
- **Nota breve:** ISTAT, "Decessi e cause di morte."
- **Voce bibliografica:** Istituto nazionale di statistica. "Decessi e cause di morte." IstatData. Consultato il 1° ottobre 2026. https://esploradati.istat.it/databrowser/#/it/dw/categories/IT1,Z0810HEA,1.0/HEA_DEATH.

> Licenza: **CC BY 4.0**. Endpoint effettivamente usato: `https://esploradati.istat.it/SDMXWS/rest`.

### AReSS Puglia — PugliaStat

- **Nota completa:** Agenzia Regionale Strategica per la Salute ed il Sociale (AReSS Puglia), "PugliaStat," consultato il 1° ottobre 2026, https://aress.regione.puglia.it/en/aree-tematiche/mappe-e-dati-per-la-salute/pugliastat.
- **Nota breve:** AReSS Puglia, "PugliaStat."
- **Voce bibliografica:** Agenzia Regionale Strategica per la Salute ed il Sociale (AReSS Puglia). "PugliaStat." Consultato il 1° ottobre 2026. https://aress.regione.puglia.it/en/aree-tematiche/mappe-e-dati-per-la-salute/pugliastat.

> In tesi questa voce serve a documentare che lo strumento con grana **distrettuale** esiste ma **non è pubblicamente accessibile** (nessun dato, export o API): è il limite che costringe a ricostruire la grana distretto dai dati comunali ISTAT.

### Chieti, Nannavecchia, Bisceglia — presentazione di PugliaStat (2015)

- **Nota completa:** Antonio Chieti, Anna Maria Nannavecchia e Lucia Bisceglia, "Lo stato di salute pugliese on demand: un nuovo strumento informativo" (comunicazione al XXXIX Congresso dell'Associazione Italiana di Epidemiologia, Milano, 27-30 ottobre 2015).
- **Nota breve:** Chieti, Nannavecchia e Bisceglia, "Lo stato di salute pugliese on demand."
- **Voce bibliografica:** Chieti, Antonio, Anna Maria Nannavecchia, e Lucia Bisceglia. "Lo stato di salute pugliese on demand: un nuovo strumento informativo." Comunicazione al XXXIX Congresso dell'Associazione Italiana di Epidemiologia, Milano, 27-30 ottobre 2015.

> Riferimento citato dalla pagina AReSS su PugliaStat; **non verificato** sugli atti del congresso.

### AReSS Puglia — Open Salute Puglia

- **Nota completa:** Agenzia Regionale Strategica per la Salute ed il Sociale (AReSS Puglia), "Open Salute Puglia," consultato il 1° ottobre 2026, https://opensalute.aress.regione.puglia.it/.
- **Nota breve:** AReSS Puglia, "Open Salute Puglia."
- **Voce bibliografica:** Agenzia Regionale Strategica per la Salute ed il Sociale (AReSS Puglia). "Open Salute Puglia." Consultato il 1° ottobre 2026. https://opensalute.aress.regione.puglia.it/.

> Licenza non dichiarata. Dashboard Apache Superset incorporate: consultabili nel browser, non interrogabili via API senza *guest token*.

### AReSS Puglia — Open data su dati.puglia.it

Dataset effettivamente utilizzabili (prevalenza di pazienti cronici con BPCO, accessi in PS e ricoveri urgenti per patologia), a grana ASL.

- **Nota completa:** Agenzia Regionale Strategica per la Salute ed il Sociale (AReSS Puglia), "Pazienti cronici affetti da broncopneumopatia cronica ostruttiva," dati.puglia.it, consultato il 1° ottobre 2026, https://dati.puglia.it/ckan/dataset/pazienti-cronici-affetti-da-broncopneumopatia-cronica-ostruttiva-2023.
- **Nota breve:** AReSS Puglia, "Pazienti cronici affetti da BPCO."
- **Voce bibliografica:** Agenzia Regionale Strategica per la Salute ed il Sociale (AReSS Puglia). "Pazienti cronici affetti da broncopneumopatia cronica ostruttiva." dati.puglia.it. Consultato il 1° ottobre 2026. https://dati.puglia.it/ckan/dataset/pazienti-cronici-affetti-da-broncopneumopatia-cronica-ostruttiva-2023.

> Licenza: **CC BY 4.0**. Gli altri dataset AReSS citati nel progetto (diabete, ipertensione, scompenso, accessi in PS per malattie cerebrovascolari e renali) seguono la stessa forma, cambiando titolo e URL del dataset.

### ISTAT — Health for All - Italia

Database di ~4.000 indicatori provinciali su sanità e salute; da qui vengono le **dimissioni ospedaliere per malattie dell'apparato respiratorio per provincia (1999-2024)**, unica fonte pubblica trovata per i ricoveri respiratori sul territorio.

- **Nota completa:** Istituto nazionale di statistica, *Health for All - Italia: sistema informativo territoriale su sanità e salute*, versione di giugno 2026, consultato il 1° ottobre 2026, https://www.istat.it/sistema-informativo-6/health-for-all-italia/.
- **Nota breve:** ISTAT, *Health for All - Italia*.
- **Voce bibliografica:** Istituto nazionale di statistica. *Health for All - Italia: sistema informativo territoriale su sanità e salute*. Versione di giugno 2026. Consultato il 1° ottobre 2026. https://www.istat.it/sistema-informativo-6/health-for-all-italia/.

> Licenza: **CC BY 4.0**. In tesi va dichiarato che i dati sono stati letti **decodificando il formato binario** del database distribuito per il software `HFA.exe` (v. `data/dataset/salute/istat/ISTAT.md`, canale C), indicando la versione del rilascio usato.
>
> ⛔ **Fonte scartata il 01/10/2026** (decisione di Matteo): non alimenta il dataset. Citabile solo se la tesi parla della ricognizione delle fonti e del perché i ricoveri sono rimasti fuori dall'MVP.

### AGENAS — Programma Nazionale Esiti (PNE)

- **Nota completa:** Agenzia nazionale per i servizi sanitari regionali (AGENAS), *Programma Nazionale Esiti (PNE)*, edizione 2025, consultato il 1° ottobre 2026, https://pne.agenas.it/.
- **Nota breve:** AGENAS, *Programma Nazionale Esiti*.
- **Voce bibliografica:** Agenzia nazionale per i servizi sanitari regionali (AGENAS). *Programma Nazionale Esiti (PNE)*. Edizione 2025. Consultato il 1° ottobre 2026. https://pne.agenas.it/.

> **Licenza non dichiarata** (⏳ da chiarire con AGENAS prima di citare i dati in tesi). I dati provengono dal flusso SDO integrato con l'Anagrafe Tributaria (documento *Fonti Informative e criteri di record Linkage*, pubblicato sul sito del PNE). L'API usata (`https://pne.agenas.it/pne`) non è documentata ufficialmente.

### Eurostat — Deaths by week and NUTS 3 region

- **Nota completa:** Eurostat, "Deaths by week and NUTS 3 region," dataset `demo_r_mwk3_t`, aggiornato al 16 settembre 2026, consultato il 1° ottobre 2026, https://ec.europa.eu/eurostat/databrowser/view/demo_r_mwk3_t.
- **Nota breve:** Eurostat, "Deaths by week and NUTS 3 region."
- **Voce bibliografica:** Eurostat. "Deaths by week and NUTS 3 region." Dataset `demo_r_mwk3_t`. Aggiornato al 16 settembre 2026. Consultato il 1° ottobre 2026. https://ec.europa.eu/eurostat/databrowser/view/demo_r_mwk3_t.

> Licenza: **CC BY 4.0** secondo la politica di riuso Eurostat (citare Eurostat come fonte); la dicitura esatta va copiata dalla pagina del dataset. API usata: `https://ec.europa.eu/eurostat/api/dissemination/statistics/1.0/data/demo_r_mwk3_t`.

### ISTAT — European data support (ESDS)

Voce che serve a **documentare un chiarimento**, non una fonte di dati: la pagina spiega che ESDS è il servizio di assistenza del network coordinato da Eurostat, non un produttore di statistiche (v. `Regole_dei_dati.md` del repository Backend e `data/dataset/salute/eurostat/Eurostat.md`).

- **Nota completa:** Istituto nazionale di statistica, "European data support," consultato il 1° ottobre 2026, https://www.istat.it/attivita-e-servizi-per-tipo-di-utenti/tutti/european-data-support/.
- **Nota breve:** ISTAT, "European data support."
- **Voce bibliografica:** Istituto nazionale di statistica. "European data support." Consultato il 1° ottobre 2026. https://www.istat.it/attivita-e-servizi-per-tipo-di-utenti/tutti/european-data-support/.

### ISTAT — Bilancio demografico mensile (demo.istat.it)

Morti, nati e popolazione per comune, mese e sesso (2019-2024), scaricati come CSV zippato da un URL stabile; usati come fonte indipendente e come validazione dei decessi giornalieri (v. `data/dataset/salute/istat/ISTAT.md`, canale D).

- **Nota completa:** Istituto nazionale di statistica, "Bilancio demografico mensile e popolazione residente per sesso," Demo — Demografia in cifre, consultato il 1° ottobre 2026, https://demo.istat.it/app/?i=D7B.
- **Nota breve:** ISTAT, "Bilancio demografico mensile."
- **Voce bibliografica:** Istituto nazionale di statistica. "Bilancio demografico mensile e popolazione residente per sesso." Demo — Demografia in cifre. Consultato il 1° ottobre 2026. https://demo.istat.it/app/?i=D7B.

> Licenza: **CC BY 4.0** (note legali ISTAT). File usati nella verifica: `https://demo.istat.it/data/d7b/D7B2024.csv.zip` (anni disponibili 2019-2024).

### Ministero della Salute — Sistema di sorveglianza della mortalità giornaliera (SiSMG)

Sorveglianza dei decessi giornalieri negli over-65 in 54 città, coordinata dal Dipartimento di Epidemiologia del SSR Lazio (ASL Roma 1). Citata per documentare che **nel Salento copre solo Taranto** e che non pubblica dati grezzi (v. `data/dataset/salute/iss/ISS.md`).

- **Nota completa:** Ministero della Salute, "Sistema di sorveglianza mortalità giornaliera," consultato il 1° ottobre 2026, https://www.salute.gov.it/new/it/tema/ondate-di-calore/sistema-di-sorveglianza-mortalita-giornaliera/.
- **Nota breve:** Ministero della Salute, "Sorveglianza mortalità giornaliera."
- **Voce bibliografica:** Ministero della Salute. "Sistema di sorveglianza mortalità giornaliera." Consultato il 1° ottobre 2026. https://www.salute.gov.it/new/it/tema/ondate-di-calore/sistema-di-sorveglianza-mortalita-giornaliera/.

> Licenza: non dichiarata.

### Istituto Superiore di Sanità — profilidisalute.it

Profili di salute (mortalità per 37 cause e ospedalizzazione) a livello nazionale e regionale in chiaro, per ASL solo in area riservata agli operatori sanitari.

- **Nota completa:** Istituto Superiore di Sanità, "Profili di salute," consultato il 1° ottobre 2026, https://www.profilidisalute.it/.
- **Nota breve:** ISS, "Profili di salute."
- **Voce bibliografica:** Istituto Superiore di Sanità. "Profili di salute." Consultato il 1° ottobre 2026. https://www.profilidisalute.it/.

> Licenza: non dichiarata. Scheda tecnica sulla mortalità: https://www.profilidisalute.it/download/ProSa_ST_MRT.pdf.

### Istituto Superiore di Sanità — Indirizzario dei registri di mortalità (ReNCaM)

Elenco dei registri nominativi delle cause di morte e dei loro referenti, compresi quelli delle ASL di Lecce, Brindisi e Taranto: era la via istituzionale per chiedere il dato comunale per causa. ⛔ **Strada scartata il 01/10/2026** (richiesta formale troppo lenta): la voce serve solo a documentare in tesi che il dato esiste ma non è accessibile.

- **Nota completa:** Istituto Superiore di Sanità, "Indirizzario dei Registri di mortalità," EpiCentro, consultato il 1° ottobre 2026, https://www.epicentro.iss.it/mortalita/indirizzario.
- **Nota breve:** ISS, "Indirizzario dei Registri di mortalità."
- **Voce bibliografica:** Istituto Superiore di Sanità. "Indirizzario dei Registri di mortalità." EpiCentro. Consultato il 1° ottobre 2026. https://www.epicentro.iss.it/mortalita/indirizzario.

### Istituto Superiore di Sanità — Sorveglianza delle infezioni respiratorie acute (RespiVirNet)

Incidenza settimanale regionale delle sindromi respiratorie; citata per documentarne la grana regionale e la **sospensione dei flussi dal 6 marzo 2026**.

- **Nota completa:** Istituto Superiore di Sanità, "Sorveglianza delle infezioni respiratorie acute," EpiCentro, consultato il 1° ottobre 2026, https://www.epicentro.iss.it/sorveglianza-infezioni-respiratorie-acute/.
- **Nota breve:** ISS, "Sorveglianza delle infezioni respiratorie acute."
- **Voce bibliografica:** Istituto Superiore di Sanità. "Sorveglianza delle infezioni respiratorie acute." EpiCentro. Consultato il 1° ottobre 2026. https://www.epicentro.iss.it/sorveglianza-infezioni-respiratorie-acute/.

### AReSS Puglia / Registro Tumori Puglia — Dati di incidenza 2013-2021

Rapporto regionale sull'incidenza dei tumori per sede e provincia di diagnosi (dicembre 2024), unico output pubblico del Registro Tumori Puglia.

- **Nota completa:** Agenzia Regionale Strategica per la Salute ed il Sociale della Puglia, *I tumori in Regione Puglia: dati di incidenza nel periodo 2013-2021* (Bari: AReSS Puglia, 2024), consultato il 1° ottobre 2026, https://aress.regione.puglia.it/en/-/rapporto-tumori-2024.
- **Nota breve:** AReSS Puglia, *I tumori in Regione Puglia*.
- **Voce bibliografica:** Agenzia Regionale Strategica per la Salute ed il Sociale della Puglia. *I tumori in Regione Puglia: dati di incidenza nel periodo 2013-2021*. Bari: AReSS Puglia, 2024. https://aress.regione.puglia.it/en/-/rapporto-tumori-2024.

> Licenza: non dichiarata. La dashboard PugliaCan Live (http://rtp.sanita.regione.puglia.it/pclive2) risulta non raggiungibile dall'esterno al 1° ottobre 2026.
>
> ⛔ **Filone scartato il 01/10/2026** (decisione di Matteo): i registri tumori **non sono una fonte del dataset** (passo annuale, latenza biologica di 10-30 anni). La voce resta solo per un eventuale riferimento di contesto nella tesi; la scheda tecnica è stata rimossa dal repo.

### ASL Lecce — Registro Tumori

Rapporti del registro tumori provinciale, con approfondimento dell'incidenza per singoli comuni e distretti socio-sanitari (dati 2013-2017).

- **Nota completa:** Azienda Sanitaria Locale di Lecce, "Registro Tumori," Sanità Puglia, consultato il 1° ottobre 2026, https://www.sanita.puglia.it/en/web/asl-lecce/registro-tumori.
- **Nota breve:** ASL Lecce, "Registro Tumori."
- **Voce bibliografica:** Azienda Sanitaria Locale di Lecce. "Registro Tumori." Sanità Puglia. Consultato il 1° ottobre 2026. https://www.sanita.puglia.it/en/web/asl-lecce/registro-tumori.

> Licenza: non dichiarata. ⛔ Come la voce precedente: **fonte di contesto, non del dataset** (scartata il 01/10/2026).

---

## Calore / isole di calore urbane

Fonti usate per il terzo parametro del progetto, l'**UHRI** (misura delle isole di calore urbano, v. `data/dataset/calore/Lista_dataset_calore.md`).

### Zhang et al. — Indici ETCCDI di temperature estreme (2011)

Definizione degli indici *summer days* (T max > 25 °C) e *tropical nights* (T min > 20 °C), base delle soglie di caldo (v. `data/dataset/calore/Soglie_Caldo.md`).

- **Nota completa:** Xuebin Zhang et al., "Indices for Monitoring Changes in Extremes Based on Daily Temperature and Precipitation Data," *WIREs Climate Change* 2, n. 6 (2011): 851–70, https://doi.org/10.1002/wcc.147.
- **Nota breve:** Zhang et al., "Indices for Monitoring Changes in Extremes."
- **Voce bibliografica:** Zhang, Xuebin, Lisa Alexander, Gabriele C. Hegerl, Philip Jones, Albert Klein Tank, Thomas C. Peterson, Blair Trewin, e Francis W. Zwiers. "Indices for Monitoring Changes in Extremes Based on Daily Temperature and Precipitation Data." *WIREs Climate Change* 2, n. 6 (2011): 851–70. https://doi.org/10.1002/wcc.147.

> Elenco autori e pagine **da verificare sul DOI** prima della citazione definitiva (scritti a memoria).

### Pappaccogli et al. — Isola di calore urbana di Lecce (2024)

Studio sull'intensità dell'isola di calore di **Lecce**: variazione stagionale, ciclo diurno e influenza delle ondate di calore. È il riferimento di letteratura più vicino al progetto — stesso territorio, stesso fenomeno — e il termine di paragone per i valori che il progetto calcolerà.

- **Nota completa:** Gianluca Pappaccogli et al., "Dynamics of Urban Heat Island Intensity in Lecce, Italy: Seasonal, Diurnal and Heat Wave Influence," *Bulletin of Atmospheric Science and Technology* 5 (2024), https://doi.org/10.1007/s42865-024-00072-z.
- **Nota breve:** Pappaccogli et al., "Dynamics of Urban Heat Island Intensity in Lecce."
- **Voce bibliografica:** Pappaccogli, Gianluca, Francesco Giangrande, Antonio Esposito, A. Donateo, P. Lionello, e Riccardo Buccolieri. "Dynamics of Urban Heat Island Intensity in Lecce, Italy: Seasonal, Diurnal and Heat Wave Influence." *Bulletin of Atmospheric Science and Technology* 5 (2024). https://doi.org/10.1007/s42865-024-00072-z.

### Iungman et al. — Raffrescamento urbano e mortalità da isola di calore (2023)

Studio di *health impact assessment* su 93 città europee (estate 2015): stima la mortalità estiva attribuibile all'isola di calore urbana e la quota di decessi evitabili portando la copertura arborea al 30%. È il riferimento che collega direttamente i due fattori del calore del progetto — temperatura e copertura arborea — alla mortalità, su scala europea.

- **Nota completa:** Tamara Iungman et al., "Cooling Cities through Urban Green Infrastructure: A Health Impact Assessment of European Cities," *The Lancet* 401, n. 10376 (2023): 577-589, https://doi.org/10.1016/S0140-6736(22)02585-5.
- **Nota breve:** Iungman et al., "Cooling Cities through Urban Green Infrastructure."
- **Voce bibliografica:** Iungman, Tamara, Marta Cirach, Federica Marando, Evelise Pereira Barboza, Sasha Khomenko, Pedro Masselot, Marcos Quijal-Zamorano, Natalie Mueller, Antonio Gasparrini, Joan Ballester, et al. "Cooling Cities through Urban Green Infrastructure: A Health Impact Assessment of European Cities." *The Lancet* 401, n. 10376 (2023): 577-589. https://doi.org/10.1016/S0140-6736(22)02585-5.

> Chiave LaTeX: `iungman2023`. Risultato chiave: ~4,33% dei decessi estivi nelle città attribuibili all'UHI; ~1,84% evitabili con il 30% di copertura arborea.

### Huang et al. — Valutazione economica della mortalità da isola di calore (2023)

Valutazione a 500 m di risoluzione del rischio di mortalità legato all'isola di calore urbana in 85 città europee (2015-2017), con stima dei costi economici associati. Riferimento europeo recente sul nesso UHI-mortalità alla scala sub-urbana.

- **Nota completa:** Wan Ting Katty Huang et al., "Economic Valuation of Temperature-Related Mortality Attributed to Urban Heat Islands in European Cities," *Nature Communications* 14 (2023): 7438, https://doi.org/10.1038/s41467-023-43135-z.
- **Nota breve:** Huang et al., "Economic Valuation of Temperature-Related Mortality."
- **Voce bibliografica:** Huang, Wan Ting Katty, Pierre Masselot, Elie Bou-Zeid, Simone Fatichi, Athanasios Paschalis, Ting Sun, Antonio Gasparrini, e Gabriele Manoli. "Economic Valuation of Temperature-Related Mortality Attributed to Urban Heat Islands in European Cities." *Nature Communications* 14 (2023): 7438. https://doi.org/10.1038/s41467-023-43135-z.

> Chiave LaTeX: `huang2023`. Licenza: Open Access CC BY 4.0.

### Cuerdo-Vilches et al. — Isola di calore, morbilità e mortalità in città spagnole (2023)

Analisi di serie storiche sull'effetto dell'isola di calore su mortalità e ricoveri d'urgenza durante le ondate di calore in cinque città spagnole (2014-2018). Rilevante per il progetto perché mostra che l'effetto UHI è più marcato nelle città costiere (via la temperatura minima) e che **non si possono fare generalizzazioni**: servono studi a scala locale, la stessa indicazione che motiva l'approccio distrettuale di OneHealth.

- **Nota completa:** Teresa Cuerdo-Vilches et al., "Impact of Urban Heat Islands on Morbidity and Mortality in Heat Waves: Observational Time Series Analysis of Spain's Five Cities," *Science of the Total Environment* 872 (2023): 162086, https://doi.org/10.1016/j.scitotenv.2023.162086.
- **Nota breve:** Cuerdo-Vilches et al., "Impact of Urban Heat Islands on Morbidity and Mortality."
- **Voce bibliografica:** Cuerdo-Vilches, Teresa, Julio Díaz, José Antonio López-Bueno, Miguel Ángel Navas, Isidro Juan Mirón, e Cristina Linares. "Impact of Urban Heat Islands on Morbidity and Mortality in Heat Waves: Observational Time Series Analysis of Spain's Five Cities." *Science of the Total Environment* 872 (2023): 162086. https://doi.org/10.1016/j.scitotenv.2023.162086.

> Chiave LaTeX: `cuerdo2023`.

### Copernicus C3S — ERA5-Land (fonte primaria del calore)

Rianalisi climatica oraria a 0,1° (~9 km), dal 1950 a oggi: fonte della serie di temperatura giornaliera per comune (v. `data/dataset/calore/era5_land/ERA5_Land.md`).

- **Nota completa:** Copernicus Climate Change Service, "ERA5-Land Hourly Data from 1950 to Present," Climate Data Store, consultato il 1° ottobre 2026, https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land.
- **Nota breve:** C3S, "ERA5-Land Hourly Data."
- **Voce bibliografica:** Copernicus Climate Change Service. "ERA5-Land Hourly Data from 1950 to Present." Climate Data Store. Consultato il 1° ottobre 2026. https://cds.climate.copernicus.eu/datasets/reanalysis-era5-land.

> Licenza: CC BY (licenza Copernicus). Prima della citazione definitiva in tesi, copiare la dicitura di attribuzione dalla pagina del dataset.

### ARPA Puglia — Dati di monitoraggio meteorologico (rete RRQA)

Temperatura oraria misurata dalle stazioni meteo ARPA, usata per validare ERA5-Land su 2023-2024 (v. `data/dataset/calore/arpa_meteo/ARPA_Meteo.md`).

- **Nota completa:** ARPA Puglia, "Meteo — Monitoraggio dati meteo RRQA," Open Data Regione Puglia, consultato il 1° ottobre 2026, https://dati.puglia.it/ckan/dataset/dati-meteo-rrqa-2024.
- **Nota breve:** ARPA Puglia, "Monitoraggio dati meteo RRQA."
- **Voce bibliografica:** ARPA Puglia. "Meteo — Monitoraggio dati meteo RRQA." Open Data Regione Puglia. Consultato il 1° ottobre 2026. https://dati.puglia.it/ckan/dataset/dati-meteo-rrqa-2024.

> Licenza: CC BY 4.0 (dichiarata nei metadati CKAN).

### Copernicus C3S / VITO — Climate variables for cities in Europe (UrbClim)

Simulazioni UrbClim a 100 m per 100 città europee (2008-2017): **nel Salento nessuna città** (in Puglia solo Bari), dataset deprecato dal 10/05/2024. Citata per documentare **perché** un dato UHI già pronto non è utilizzabile per il progetto.

- **Nota completa:** Copernicus Climate Change Service, "Climate Variables for Cities in Europe from 2008 to 2017," Climate Data Store, consultato il 1° ottobre 2026, https://cds.climate.copernicus.eu/datasets/sis-urban-climate-cities.
- **Nota breve:** C3S, "Climate Variables for Cities in Europe."
- **Voce bibliografica:** Copernicus Climate Change Service. "Climate Variables for Cities in Europe from 2008 to 2017." Climate Data Store. Consultato il 1° ottobre 2026. https://cds.climate.copernicus.eu/datasets/sis-urban-climate-cities.

### EEA — Urban Heat Island (UHI) intensity modelling

Intensità UHI estiva (raster 100 m, EPSG:3035) derivata dalle stesse simulazioni UrbClim, con lo stesso limite di copertura.

- **Nota completa:** European Environment Agency, "Urban Heat Island (UHI) Intensity Modelling, Jan. 2020," EEA Geospatial Data Catalogue, consultato il 1° ottobre 2026, https://sdi.eea.europa.eu/catalogue/srv/api/records/45b703bb-d4f3-4eaa-8b73-13fde2041f01.
- **Nota breve:** EEA, "Urban Heat Island (UHI) Intensity Modelling."
- **Voce bibliografica:** European Environment Agency. "Urban Heat Island (UHI) Intensity Modelling, Jan. 2020." EEA Geospatial Data Catalogue. Consultato il 1° ottobre 2026. https://sdi.eea.europa.eu/catalogue/srv/api/records/45b703bb-d4f3-4eaa-8b73-13fde2041f01.

> Licenza: CC BY 4.0 (EEA / Copernicus Climate Change Service).

### Copernicus Land Monitoring Service — Tree Cover Density e Imperviousness Density

I due fattori di mitigazione dell'UHRI: copertura arborea e suolo impermeabile per comune (raster 10 m, statistica zonale sui confini comunali).

- **Nota completa:** Copernicus Land Monitoring Service, "Tree Cover Density 2018-Present (Raster 10 m), Europe, Yearly," consultato il 1° ottobre 2026, https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover/tree-cover-density-2018-present-raster-10-m-europe-yearly; Copernicus Land Monitoring Service, "Imperviousness Density 2018 (Raster 10 m and 100 m), Europe, 3-Yearly," consultato il 1° ottobre 2026, https://land.copernicus.eu/en/products/high-resolution-layer-imperviousness/imperviousness-density-2018.
- **Nota breve:** CLMS, "Tree Cover Density"; CLMS, "Imperviousness Density 2018."
- **Voce bibliografica:** Copernicus Land Monitoring Service. "Tree Cover Density 2018-Present (Raster 10 m), Europe, Yearly." Consultato il 1° ottobre 2026. https://land.copernicus.eu/en/products/high-resolution-layer-forests-and-tree-cover/tree-cover-density-2018-present-raster-10-m-europe-yearly.
- **Voce bibliografica:** Copernicus Land Monitoring Service. "Imperviousness Density 2018 (Raster 10 m and 100 m), Europe, 3-Yearly." Consultato il 1° ottobre 2026. https://land.copernicus.eu/en/products/high-resolution-layer-imperviousness/imperviousness-density-2018.

> Licenza: accesso pieno, libero e gratuito (Reg. delegato UE n. 1159/2013), con obbligo di citare la fonte e dichiarare le modifiche — confermata il 15 ottobre 2026 dai record del catalogo EEA. Edizioni **realmente usate** (16 ottobre 2026): Tree Cover Density **2024** (la pagina «2018-present» qui sopra, aggiungendo «Edizione 2024» alla voce) e Imperviousness Density **2018** (pagina qui sopra). Voci complete in `data/dataset/calore/clms/CLMS.md` §7.

### USGS — Landsat Collection 2 Level-2 (Surface Temperature) ed ESA WorldCover

Fonti per gli sviluppi successivi all'MVP: temperatura superficiale a 30 m per l'intensità SUHI (Landsat) e riscontro indipendente della copertura arborea (WorldCover).

- **Nota completa:** U.S. Geological Survey, "Landsat Collection 2 Level-2 Science Products," consultato il 1° ottobre 2026, https://www.usgs.gov/landsat-missions/landsat-collection-2-level-2-science-products; European Space Agency, "ESA WorldCover," consultato il 1° ottobre 2026, https://esa-worldcover.org/en.
- **Nota breve:** USGS, "Landsat Collection 2 Level-2"; ESA, "WorldCover."
- **Voce bibliografica:** U.S. Geological Survey. "Landsat Collection 2 Level-2 Science Products." Consultato il 1° ottobre 2026. https://www.usgs.gov/landsat-missions/landsat-collection-2-level-2-science-products.
- **Voce bibliografica:** European Space Agency. "ESA WorldCover." Consultato il 1° ottobre 2026. https://esa-worldcover.org/en.

> Licenze: Landsat senza restrizioni d'uso (USGS); ESA WorldCover CC BY 4.0.

---

## Simulazione dei dati sanitari

Fonti dei parametri della simulazione (`api/salute/simulazione.py`, `data/dataset/salute/simulati/Dati_Simulati.md`, 25/10/2026). Si citano per **giustificare le ipotesi** del generatore, non come risultati del progetto.

### Scarinzi et al. — EpiAir2, inquinamento e ricoveri urgenti in 25 città italiane (2013)

Metanalisi su 2.246.448 ricoveri urgenti 2006-2010 in 25 città italiane, **Brindisi e Taranto comprese**. Dà i coefficienti dello scenario «letteratura»: ricoveri respiratori +0,75% per 10 µg/m³ di PM10 (lag 0-5), ricoveri cardiaci +0,57% per 10 µg/m³ di NO2 (lag 0); nessuna associazione positiva per l'ozono. Valori verificati sull'abstract (PDF ospitato da ISPRA).

- **Nota completa:** Cecilia Scarinzi et al., "Inquinamento atmosferico e ricoveri ospedalieri urgenti in 25 città italiane: risultati del progetto EpiAir2," *Epidemiologia & Prevenzione* 37, no. 4-5 (2013): 230-41.
- **Nota breve:** Scarinzi et al., "Inquinamento atmosferico e ricoveri ospedalieri urgenti."
- **Voce bibliografica:** Scarinzi, Cecilia, Ester Rita Alessandrini, Monica Chiusolo, Claudia Galassi, Marco Baldini, Maria Serinelli, Paolo Pandolfi, et al. "Inquinamento atmosferico e ricoveri ospedalieri urgenti in 25 città italiane: risultati del progetto EpiAir2." *Epidemiologia & Prevenzione* 37, no. 4-5 (2013): 230-41. https://www.isprambiente.gov.it/files/temi/ambiente-salute-e-societa/EP45_230_art3.pdf.

### Michelozzi et al. — Alte temperature e ricoveri in 12 città europee (PHEWE, 2009)

Progetto PHEWE, aprile-settembre: ricoveri respiratori nei 75+ **+4,5% per °C** di temperatura apparente massima oltre la soglia nelle città mediterranee (IC95% 1,9-7,3), nessun effetto significativo sui ricoveri cardiovascolari e cerebrovascolari. Dà l'effetto del caldo dello scenario «letteratura». Valori verificati sull'abstract PubMed (PMID 19060232).

- **Nota completa:** Paola Michelozzi et al., "High Temperature and Hospitalizations for Cardiovascular and Respiratory Causes in 12 European Cities," *American Journal of Respiratory and Critical Care Medicine* 179, no. 5 (2009): 383-89.
- **Nota breve:** Michelozzi et al., "High Temperature and Hospitalizations."
- **Voce bibliografica:** Michelozzi, Paola, Gabriele Accetta, Manuela De Sario, Daniela D'Ippoliti, Claudia Marino, Michela Baccini, Annibale Biggeri, et al. "High Temperature and Hospitalizations for Cardiovascular and Respiratory Causes in 12 European Cities." *American Journal of Respiratory and Critical Care Medicine* 179, no. 5 (2009): 383-89. https://pubmed.ncbi.nlm.nih.gov/19060232/.
- ⏳ Elenco degli autori oltre il primo da riscontrare sull'articolo prima della bibliografia LaTeX.

### Campagna et al. — Accessi in PS dei pazienti in assistenza domiciliare integrata (2021)

Studio retrospettivo sul Piemonte (66.433 episodi di ADI): 0,66 accessi in PS per paziente (DS 1,34), 44% degli episodi con almeno un accesso, **60,1% degli accessi a bassa urgenza**. Dà tasso, dispersione e quota a bassa urgenza degli assistiti ADI simulati.

- **Nota completa:** Sara Campagna et al., "Determinants Associated With the Risk of Emergency Department Visits Among Patients Receiving Integrated Home Care Services: A 6-Year Retrospective Observational Study in a Large Italian Region," *International Journal of Health Policy and Management* 10, no. 10 (2021): 605-12, https://pmc.ncbi.nlm.nih.gov/articles/PMC9278539/.
- **Nota breve:** Campagna et al., "Determinants Associated With the Risk of Emergency Department Visits."
- **Voce bibliografica:** Campagna, Sara, Alberto Borraccino, Gianfranco Politano, et al. "Determinants Associated With the Risk of Emergency Department Visits Among Patients Receiving Integrated Home Care Services: A 6-Year Retrospective Observational Study in a Large Italian Region." *International Journal of Health Policy and Management* 10, no. 10 (2021): 605-12. https://pmc.ncbi.nlm.nih.gov/articles/PMC9278539/.
- ⏳ Nomi propri degli autori e DOI da riscontrare sull'articolo.

### Quotidiano Sanità — Accessi al pronto soccorso (dati Annuario statistico SSN 2023)

Articolo che riporta i dati dell'Annuario statistico del SSN: **18,35 milioni di accessi al PS nel 2023, 311 ogni 1.000 abitanti** (338 nel 2013). Dà il tasso di accesso al PS simulato. Fonte secondaria: va sostituita con la tavola dell'Annuario del Ministero della Salute (dato per la Puglia), consultata il 25/10/2026.

- **Nota completa:** Quotidiano Sanità, "La crisi del pronto soccorso: meno accessi ma in dieci anni tagliate le strutture," accesso 25 ottobre 2026, https://www.quotidianosanita.it/studi-e-analisi/la-crisi-del-pronto-soccorso-meno-accessi-ma-in-dieci-anni-tagliate-il-delle-strutture-dieta-anche-per-ambulanze-e-centri-di-rianimazione-ecco-come-sono-cambiati-i-servizi-di-emergenza/.
- ⏳ Titolo esatto e data dell'articolo da copiare dalla pagina.

### Italpress — Over 65 in assistenza domiciliare integrata (2023)

Riporta circa il **4% degli over 65 in ADI nel 2023** (obiettivo PNRR: 10%); il Ministero della Salute dichiara invece oltre l'8% con un altro denominatore. Dà la quota di assistiti ADI simulata, come ipotesi. Da sostituire con il dato SIAD/AGENAS per la Puglia, consultata il 25/10/2026.

- **Nota completa:** Italpress, articolo sull'assistenza domiciliare integrata agli over 65, accesso 25 ottobre 2026, https://www.italpress.com/?p=519170.
- ⏳ Titolo e data da copiare dalla pagina.

---

## Medicina di iniziativa — scopo dell'assistente ONE

Fonti del documento `localhost/rag/documenti/medicina_iniziativa.md` (10/11/2026), da cui ONE prende le leve organizzative per ridurre l'ospedalizzazione evitabile. Estremi verificati il 10/11/2026.

### Ministero della Salute — Piano nazionale della cronicità (2016)

- **Nota completa:** Ministero della Salute, *Piano nazionale della cronicità*, Accordo tra lo Stato, le Regioni e le Province autonome di Trento e di Bolzano del 15 settembre 2016 (Rep. Atti n. 160/CSR) (Roma: Ministero della Salute, 2016), https://www.salute.gov.it/imgs/C_17_pubblicazioni_2584_allegato.pdf.
- **Nota breve:** Ministero della Salute, *Piano nazionale della cronicità*.
- **Voce bibliografica:** Ministero della Salute. *Piano nazionale della cronicità*. Accordo tra lo Stato, le Regioni e le Province autonome di Trento e di Bolzano del 15 settembre 2016 (Rep. Atti n. 160/CSR). Roma: Ministero della Salute, 2016. https://www.salute.gov.it/imgs/C_17_pubblicazioni_2584_allegato.pdf.

> La medicina d'iniziativa e la stratificazione della popolazione sono fra i fondamenti del piano, previsto dal Patto per la Salute 2014-2016. Usato per la definizione di medicina di iniziativa.

### DM 23 maggio 2022, n. 77 — modelli e standard dell'assistenza territoriale

- **Nota completa:** Ministero della Salute, *Decreto 23 maggio 2022, n. 77, Regolamento recante la definizione di modelli e standard per lo sviluppo dell'assistenza territoriale nel Servizio sanitario nazionale*, Gazzetta Ufficiale della Repubblica Italiana, Serie Generale n. 144 del 22 giugno 2022, https://www.gazzettaufficiale.it/eli/id/2022/06/22/22G00085/sg.
- **Nota breve:** DM 77/2022.
- **Voce bibliografica:** Ministero della Salute. *Decreto 23 maggio 2022, n. 77, Regolamento recante la definizione di modelli e standard per lo sviluppo dell'assistenza territoriale nel Servizio sanitario nazionale*. Gazzetta Ufficiale della Repubblica Italiana, Serie Generale n. 144 del 22 giugno 2022. https://www.gazzettaufficiale.it/eli/id/2022/06/22/22G00085/sg.

> In vigore dal 7 luglio 2022. Casa della Comunità, infermiere di famiglia e di comunità (uno ogni 3000 abitanti), Centrale operativa territoriale (una ogni 100.000 abitanti), assistenza domiciliare. ⏳ Gli standard numerici citati da ONE vanno riscontrati sul testo del decreto (allegato 1).

L'obiettivo PNRR del **10% degli over 65 in ADI**, citato da ONE, viene dalla voce *Italpress* della sezione «Simulazione dei dati sanitari».

## Design dell'interfaccia

### Impeccable — skill di design e catalogo dei segnali «AI slop»

Usato per l'audit della dashboard (19/10/2026): catalogo degli anti-pattern e rilevatore `npx impeccable detect`.

- **Nota completa:** Paul Bakaus, "Impeccable," repository GitHub, consultato il 19 ottobre 2026, https://github.com/pbakaus/impeccable; Impeccable, "The Visible Tells of AI Design," consultato il 19 ottobre 2026, https://www.impeccable.style/slop.
- **Nota breve:** Bakaus, "Impeccable"; Impeccable, "Visible Tells."
- **Voce bibliografica:** Bakaus, Paul. "Impeccable." Repository GitHub. Consultato il 19 ottobre 2026. https://github.com/pbakaus/impeccable.
- **Voce bibliografica:** Impeccable. "The Visible Tells of AI Design." Consultato il 19 ottobre 2026. https://www.impeccable.style/slop.

> Licenza: Apache-2.0.

### Anthropic — skill *frontend-design*

- **Nota completa:** Anthropic, "frontend-design," in *anthropics/skills*, repository GitHub, consultato il 19 ottobre 2026, https://github.com/anthropics/skills/tree/main/skills/frontend-design.
- **Nota breve:** Anthropic, "frontend-design."
- **Voce bibliografica:** Anthropic. "frontend-design." In *anthropics/skills*. Repository GitHub. Consultato il 19 ottobre 2026. https://github.com/anthropics/skills/tree/main/skills/frontend-design.

> Licenza: Apache-2.0.

### pixelslop — catalogo dei pattern «AI slop»

- **Nota completa:** "pixelslop," versione 0.3.8, pacchetto npm, consultato il 19 ottobre 2026, https://cdn.jsdelivr.net/npm/pixelslop@0.3.8/dist/skill/resources/ai-slop-patterns.md.
- **Nota breve:** "pixelslop."
- **Voce bibliografica:** "pixelslop." Versione 0.3.8. Pacchetto npm. Consultato il 19 ottobre 2026. https://cdn.jsdelivr.net/npm/pixelslop@0.3.8/dist/skill/resources/ai-slop-patterns.md.

> Licenza: Apache-2.0 (dal badge del README; file LICENSE da verificare).

---

## Modulo AI — modelli di linguaggio locali

Fonti della valutazione di fattibilità del 27/10/2026. Le schede dei modelli cambiano a ogni rilascio: prima di citarle in tesi ricontrollare versione e data.

### OpenBMB — MiniCPM (repository)

- **Nota completa:** OpenBMB, "MiniCPM," repository GitHub, consultato il 27 ottobre 2026, https://github.com/OpenBMB/MiniCPM.
- **Nota breve:** OpenBMB, "MiniCPM."
- **Voce bibliografica:** OpenBMB. "MiniCPM." Repository GitHub. Consultato il 27 ottobre 2026. https://github.com/OpenBMB/MiniCPM.

> Licenza: Apache-2.0 per il repository e i modelli («This repository and MiniCPM models are released under the Apache-2.0 License»).

### OpenBMB — MiniCPM5-2B (scheda del modello)

- **Nota completa:** OpenBMB, "MiniCPM5-2B," scheda del modello, Hugging Face, consultato il 27 ottobre 2026, https://huggingface.co/openbmb/MiniCPM5-2B.
- **Nota breve:** OpenBMB, "MiniCPM5-2B."
- **Voce bibliografica:** OpenBMB. "MiniCPM5-2B." Scheda del modello. Hugging Face. Consultato il 27 ottobre 2026. https://huggingface.co/openbmb/MiniCPM5-2B.

> Licenza: Apache-2.0. Lingue dichiarate: inglese e cinese. Risultati (IFEval 86,7 e altri) dichiarati dall'editore.

### Artificial Analysis — valutazione indipendente di MiniCPM5-2B

- **Nota completa:** Artificial Analysis, "OpenBMB Releases MiniCPM5-2B," consultato il 27 ottobre 2026, https://artificialanalysis.ai/articles/openbmb-releases-minicpm5-2b.
- **Nota breve:** Artificial Analysis, "MiniCPM5-2B."
- **Voce bibliografica:** Artificial Analysis. "OpenBMB Releases MiniCPM5-2B." Consultato il 27 ottobre 2026. https://artificialanalysis.ai/articles/openbmb-releases-minicpm5-2b.

> Usata per il comportamento di astensione (AA-Omniscience) e per il confronto con i modelli sotto i 10 B parametri.

### Qwen Team — Qwen3.5-4B (scheda del modello)

- **Nota completa:** Qwen Team, "Qwen3.5-4B," scheda del modello, Hugging Face, consultato il 27 ottobre 2026, https://huggingface.co/Qwen/Qwen3.5-4B.
- **Nota breve:** Qwen Team, "Qwen3.5-4B."
- **Voce bibliografica:** Qwen Team. "Qwen3.5-4B." Scheda del modello. Hugging Face. Consultato il 27 ottobre 2026. https://huggingface.co/Qwen/Qwen3.5-4B.

> Licenza: Apache-2.0; 201 lingue e dialetti dichiarati. La licenza del 9B non è ancora verificata.

### Ollama (runtime del modello)

- **Nota completa:** Ollama, *Ollama*, repository del software, GitHub, consultato il 1° novembre 2026, https://github.com/ollama/ollama.
- **Nota breve:** Ollama, *Ollama*.
- **Voce bibliografica:** Ollama. *Ollama*. Repository del software. GitHub. Consultato il 1° novembre 2026. https://github.com/ollama/ollama.

> Licenza: MIT. Esegue il modello in locale su `127.0.0.1:11434`.

### Lewis et al. — Retrieval-Augmented Generation

- **Nota completa:** Patrick Lewis et al., "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks," *Advances in Neural Information Processing Systems* 33 (2020): 9459–9474, https://arxiv.org/abs/2005.11401.
- **Nota breve:** Lewis et al., "Retrieval-Augmented Generation."
- **Voce bibliografica:** Lewis, Patrick, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich Küttler, Mike Lewis, Wen-tau Yih, Tim Rocktäschel, Sebastian Riedel, e Douwe Kiela. "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks." *Advances in Neural Information Processing Systems* 33 (2020): 9459–9474. https://arxiv.org/abs/2005.11401.

> Riferimento del metodo RAG (introduzione e capitolo 3). Il progetto ne usa solo l'idea del recupero prima della generazione: la scelta delle sezioni è per argomento e per parole, senza modello di embedding.

---

## Fonti da aggiungere (elenco aperto)

- **Google — Gemma 4** (27/10/2026): licenza Apache-2.0 e 140+ lingue riportate solo da fonti secondarie, con taglie della famiglia discordi. Prima di citarla serve la pagina ufficiale Google o la scheda Hugging Face del modello scelto.

*25/10/2026: CAMS, EEA e OpenAQ registrati nella sezione Qualità dell'aria (chiavi `cams_reanalisi`, `cams_previsioni`, `eea_aqds`, `openaq`).*

Fonti dati già usate nel codice ma non ancora registrate qui (serve verificare titolo e data esatti delle pagine prima di scrivere la voce):

- **Copernicus Atmosphere Data Store (CAMS)** — portale e guida API (https://ads.atmosphere.copernicus.eu/, https://ads.atmosphere.copernicus.eu/how-to-api); dataset *CAMS European air quality reanalyses* (DOI 10.24381/7cc0465a) e *CAMS European air quality forecasts* (DOI 10.24381/a4005cee), licenza **CC-BY-4.0**; consultati il 28/09/2026 (v. `data/dataset/aria/copernicus_cams/Copernicus_CAMS.md`). Prima di citarli copiare la dicitura di citazione dalla pagina di ciascun dataset.
- **EEA — Air Quality Download Service** — record di catalogo *Air Quality download service* (https://sdi.eea.europa.eu/catalogue/srv/eng/catalog.search#/metadata/778ef9f5-6293-4846-badd-56a29c70880d), API (https://eeadmz1-downloads-api-appservice.azurewebsites.net/swagger/index.html), guida *How to use Air Quality Downloads* v. 1.2 (05/05/2026) e vocabolari Eionet; licenza **CC BY 4.0** (politica di riuso EEA, https://www.eea.europa.eu/en/legal-notice: citare sempre EEA come fonte); consultati il 28/09/2026 (v. `data/dataset/aria/eea/EEA.md`).
- **OpenAQ** — piattaforma e documentazione API v3 (https://openaq.org/, https://docs.openaq.org/); licenza dei dati **ODC-BY**, da citare con il suo nome (v. `data/dataset/aria/openaq/OpenAQ.md`).
- **dati.puglia.it** — dataset ARPA `inquinanti-qualita-aria`, `dati-qualita-aria-2023`, `stazioni-qualita-aria`; dataset Regione Puglia `anagrafe-distretti-socio-sanitari` (IODL 2.0).
- **ISS — SENTIERI** (monografie di *Epidemiologia & Prevenzione*): già citato nel capitolo di stato dell'arte; va consolidata la voce con autori, numero e anno della monografia usata (v. `data/dataset/salute/iss/ISS.md` §3).
- **ARPA Puglia / ASL / AReSS — Rapporti di Valutazione del Danno Sanitario (VDS)** per le aree di Taranto e Brindisi (L.R. Puglia 21/2012): mortalità e ospedalizzazione a grana comunale e di quartiere, da citare come riscontro (v. `data/dataset/salute/Lista_dataset_salute.md`, fonti di riscontro).

Il capitolo di stato dell'arte (`tesi_finale/capitoli/capitolo_1.tex`) e l'introduzione (`tesi_finale/capitoli/introduzione.tex`) citano già numerose fonti (CDC Tracking, EEA Atlas, WHO AirQ+, SENTIERI, ISTAT, Copernicus/CAMS, OpenStreetMap, studi accademici, ecc.) con chiavi `\cite{...}` non ancora presenti in questo registro né in `tesi_finale/capitoli/bibliografia.tex`. Vanno aggiunte qui via via che si consolidano le fonti definitive, per poi confluire nella bibliografia LaTeX finale.

---

## Introduzione — quadro generale (aggiunte il 03/11/2026)

### One Health High-Level Expert Panel — definizione di One Health (2022)

Definizione operativa di One Health concordata da FAO, WOAH, UNEP e OMS tramite il panel di esperti OHHLEP (costituito nel maggio 2021).

- **Nota completa:** One Health High-Level Expert Panel (OHHLEP), Wiku B. Adisasmito et al., "One Health: A New Definition for a Sustainable and Healthy Future," *PLoS Pathogens* 18, n. 6 (2022): e1010537, https://doi.org/10.1371/journal.ppat.1010537.
- **Nota breve:** OHHLEP, "One Health: A New Definition."
- **Voce bibliografica:** One Health High-Level Expert Panel (OHHLEP), Wiku B. Adisasmito, Salama Almuhairi, Casey Barton Behravesh, et al. "One Health: A New Definition for a Sustainable and Healthy Future." *PLoS Pathogens* 18, n. 6 (2022): e1010537. https://doi.org/10.1371/journal.ppat.1010537.

> Chiave LaTeX: `ohhlep2022`. Verificata via ricerca web (PMC9223325); il testo della definizione non è stato riletto per intero.

### Bernasconi et al. — esposizione personale con sensori indossabili (2025)

Studio pilota (JMIR mHealth and uHealth) che confronta un sistema di sensori indossabili con la stima da stazione fissa e ventilazione tabulata: la dose inalata di PM2.5 stimata dal sistema indossabile è del 22,3% più alta, differenza al limite della significatività (IC 95% da −6,55 a 0,63; P = 0,05). In tesi sostiene il limite «le centraline stimano l'esposizione della popolazione, non quella individuale», da citare **come studio pilota**.

- **Nota completa:** Sara Bernasconi et al., "A New Wearable System for Personal Air Pollution Exposure Estimation: Pilot Observational Study," *JMIR mHealth and uHealth* 13 (2025): e60426, https://mhealth.jmir.org/2025/1/e60426.
- **Nota breve:** Bernasconi et al., "A New Wearable System."
- **Voce bibliografica:** Bernasconi, Sara, Alessandra Angelucci, Andrea Rossi, e Andrea Aliverti. "A New Wearable System for Personal Air Pollution Exposure Estimation: Pilot Observational Study." *JMIR mHealth and uHealth* 13 (2025): e60426. https://mhealth.jmir.org/2025/1/e60426.

> Chiave LaTeX: `bernasconi2025`. Il DOI non è stato verificato: si usa l'URL della rivista.

### OpenStreetMap — copyright e licenza

Dati della carta di base (tile OSM), licenza Open Database License (ODbL) della OpenStreetMap Foundation; l'attribuzione «OpenStreetMap contributors» è obbligatoria.

- **Nota completa:** OpenStreetMap contributors, "Copyright and License," OpenStreetMap Foundation, consultato il 3 novembre 2026, https://www.openstreetmap.org/copyright.
- **Nota breve:** OpenStreetMap contributors, "Copyright and License."
- **Voce bibliografica:** OpenStreetMap contributors. "Copyright and License." OpenStreetMap Foundation. Consultato il 3 novembre 2026. https://www.openstreetmap.org/copyright.

> Chiave LaTeX: `osm_copyright`.

