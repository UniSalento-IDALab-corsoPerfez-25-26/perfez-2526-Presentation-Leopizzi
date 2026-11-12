# Report dataset aria — 2024-06-01 → 2024-06-30

Generato il 2026-10-14T14:19:12 da `scripts/aria/genera_dataset_aria.py`. Fonti: ARPA, OpenAQ, EEA, CAMS. Struttura: provincia → distretto → comune → stazione → giorno → fonte → inquinante (v. docs/Regole_dei_dati.md). L'analisi è descrittiva della copertura dei dati, non un'analisi dell'esposizione.

## 1. Sintesi

- **Celle totali:** 206.280
- **Distretti con almeno un valore** (qualunque fonte): **20 su 20**; ARPA: 12; OpenAQ: 11; EEA: 11; CAMS: 20
- **Comuni con almeno un valore:** 145 su 145, di cui **20 con dato misurato** e **125 solo modellato** (v. sezione 10)
- **Distretti senza alcun valore:** 0 — nessuno
- **Inquinanti scoperti nei dati** oltre ai 5 di riferimento della dashboard: C6H6, H2S, IPA, PM10
- **Stazioni/zone fuori dai distretti noti:** 0
- **Errori delle API:** 0

## 2. Celle per fonte e stato

| Fonte | VALORE | NULL | NO_DATA | % VALORE sulle celle di stazioni reali |
|---|---|---|---|---|
| ARPA | 4513 | 1457 | 45600 | 8.8% |
| CAMS | 26100 | 0 | 25470 | 50.6% |
| EEA | 3230 | 190 | 48150 | 6.3% |
| OpenAQ | 1622 | 58 | 49890 | 3.1% |

## 3. Copertura per distretto

Celle con `VALORE` per distretto e fonte (stazione × giorno × inquinante), e stazioni coperte da ciascuna fonte.

| Distretto | Comune sede | ARPA stazioni | ARPA valori | OpenAQ stazioni | OpenAQ valori | EEA stazioni | EEA valori | CAMS stazioni | CAMS valori |
|---|---|---|---|---|---|---|---|---|---|
| BR-01 | Brindisi | 13 | 891 | 6 | 322 | 6 | 621 | 2 | 360 |
| BR-02 | Fasano | 1 | 107 | 1 | 87 | 1 | 107 | 3 | 540 |
| BR-03 | Francavilla Fontana | 2 | 265 | 2 | 129 | 2 | 208 | 6 | 1080 |
| BR-04 | Mesagne | 6 | 522 | 5 | 234 | 5 | 412 | 9 | 1620 |
| LE-51 | Lecce | 5 | 487 | 7 | 205 | 5 | 464 | 10 | 1800 |
| LE-52 | Campi Salentina | 2 | 124 | 2 | 60 | 2 | 132 | 8 | 1440 |
| LE-53 | Nardo' | 0 | 0 | 0 | 0 | 0 | 0 | 6 | 1080 |
| LE-54 | Martano | 0 | 0 | 0 | 0 | 0 | 0 | 10 | 1800 |
| LE-55 | Galatina | 2 | 267 | 1 | 58 | 1 | 148 | 6 | 1080 |
| LE-56 | Gallipoli | 0 | 0 | 0 | 0 | 0 | 0 | 8 | 1440 |
| LE-57 | Maglie | 1 | 164 | 0 | 0 | 0 | 0 | 12 | 2160 |
| LE-58 | Poggiardo | 0 | 0 | 0 | 0 | 0 | 0 | 15 | 2700 |
| LE-59 | Casarano | 0 | 0 | 0 | 0 | 0 | 0 | 7 | 1260 |
| LE-60 | Gagliano Del Capo | 0 | 0 | 0 | 0 | 0 | 0 | 14 | 2520 |
| TA-01 | Ginosa | 0 | 0 | 0 | 0 | 0 | 0 | 4 | 720 |
| TA-02 | Massafra | 3 | 383 | 3 | 173 | 3 | 259 | 4 | 720 |
| TA-05 | Martina Franca | 1 | 86 | 1 | 30 | 1 | 57 | 2 | 360 |
| TA-06 | Grottaglie | 1 | 81 | 1 | 58 | 1 | 87 | 11 | 1980 |
| TA-07 | Manduria | 0 | 0 | 0 | 0 | 0 | 0 | 7 | 1260 |
| TA-08 | Taranto | 6 | 1136 | 4 | 266 | 6 | 735 | 1 | 180 |

## 4. Distretti con almeno un valore, per inquinante

Su 20 distretti.

| Inquinante | Unità | ARPA | OpenAQ | EEA | CAMS | Qualunque fonte | Stato nella lista |
|---|---|---|---|---|---|---|---|
| C6H6 | µg/m³ | 8 | 0 | 0 | 0 | 8 | scoperto il 2026-09-27 |
| CO | mg/m³ | 8 | 0 | 6 | 20 | 20 | riferimento dashboard |
| H2S | µg/m³ | 2 | 0 | 0 | 0 | 2 | scoperto il 2026-09-27 |
| IPA | ng/m³ | 4 | 0 | 0 | 0 | 4 | scoperto il 2026-09-27 |
| NO2 | µg/m³ | 12 | 11 | 11 | 20 | 20 | riferimento dashboard |
| O3 | µg/m³ | 7 | 6 | 6 | 20 | 20 | riferimento dashboard |
| PM10 | µg/m³ | 12 | 2 | 11 | 20 | 20 | scoperto il 2026-09-27 |
| PM2.5 | µg/m³ | 9 | 2 | 7 | 20 | 20 | riferimento dashboard |
| SO2 | µg/m³ | 9 | 7 | 7 | 20 | 20 | riferimento dashboard |

## 5. Inquinanti scoperti nei dati

Inquinanti di riferimento per la dashboard (docs/Regole_dei_dati.md): CO, NO2, O3, PM2.5, SO2. Per la regola di docs/Regole_dei_dati.md ogni altro inquinante restituito da una fonte viene aggiunto alla lista tracciata (`data/dataset/aria/anagrafica/inquinanti.json`); resta da decidere se includerlo fra gli inquinanti di riferimento della dashboard (`RIFERIMENTO_DASHBOARD` in `api/aria/anagrafica_aria.py`).

- **C6H6** (µg/m³) — scoperto nei dati di ARPA, aggiunto il 2026-09-27
- **H2S** (µg/m³) — scoperto nei dati di ARPA, aggiunto il 2026-09-27
- **IPA** (ng/m³) — scoperto nei dati di ARPA, aggiunto il 2026-09-27
- **PM10** (µg/m³) — scoperto nei dati di ARPA, OpenAQ, aggiunto il 2026-09-27

## 6. Stazioni fuori dai distretti noti (zone non elencate)

Stazioni restituite da una fonte ma non riconducibili a nessuno dei 20 distretti del Salento: escluse dalla griglia e segnalate in `data/interim/aria/riepilogo_errori.md` (regola di docs/Regole_dei_dati.md).

Nessuna.

## 7. Stazioni

- **ARPA:** 43 stazioni nel dataset
  - escluse: 100 Cokeria (rete privata ADI ex-ILVA); 101 Tamburi - Via Orsini (rete privata ADI ex-ILVA); 102 Riv1 (rete privata ADI ex-ILVA); 103 Direzione (rete privata ADI ex-ILVA); 104 Meteo Parchi (rete privata ADI ex-ILVA); 105 Portineria C (rete privata ADI ex-ILVA)
  - statistica giornaliera usata: CO=massimo giornaliero della media mobile su 8 ore, NO2=massimo orario del giorno, O3=massimo orario del giorno, PM10=media giornaliera, PM2.5=media giornaliera, SO2=massimo orario del giorno
- **OpenAQ:** 33 stazioni nel dataset
  - escluse: 6387790 Monopoli - Aldo Moro (provincia di Bari, fuori Salento)
  - senza licenza dichiarata (incluse comunque): 5200352 egdp-6 (provider HabitatMap, citizen-science, nessuna licenza dichiarata); 5338026 egdp-7 (provider HabitatMap, citizen-science, nessuna licenza dichiarata)
  - statistica giornaliera usata: CO=media pesata sul tempo delle misure del giorno, NO2=media pesata sul tempo delle misure del giorno, O3=media pesata sul tempo delle misure del giorno, PM10=media pesata sul tempo delle misure del giorno, PM2.5=media pesata sul tempo delle misure del giorno, SO2=media pesata sul tempo delle misure del giorno
- **EEA:** 33 stazioni nel dataset
  - escluse: IT1817A Monopoli - Aldo Moro (provincia di Bari, fuori Salento)
  - dataset usati: E1a 2024-06-01 → 2024-06-30
  - statistica giornaliera usata: CO=media pesata sul tempo delle misure del giorno, NO2=media pesata sul tempo delle misure del giorno, O3=media pesata sul tempo delle misure del giorno, PM10=media pesata sul tempo delle misure del giorno, PM2.5=media pesata sul tempo delle misure del giorno, SO2=media pesata sul tempo delle misure del giorno
- **CAMS:** 145 stazioni nel dataset
  - statistica giornaliera usata: CO=media oraria del giorno, media pesata sull'area delle celle CAMS 0,1° del comune, NO2=media oraria del giorno, media pesata sull'area delle celle CAMS 0,1° del comune, O3=media oraria del giorno, media pesata sull'area delle celle CAMS 0,1° del comune, PM10=media oraria del giorno, media pesata sull'area delle celle CAMS 0,1° del comune, PM2.5=media oraria del giorno, media pesata sull'area delle celle CAMS 0,1° del comune, SO2=media oraria del giorno, media pesata sull'area delle celle CAMS 0,1° del comune
- **Stazioni comuni a più fonti:** 33 su 191

### Abbinamento stazioni OpenAQ → stazioni ARPA

Solo le stazioni con dati nel periodo.

| id OpenAQ | nome OpenAQ | chiave nel dataset | distretto | abbinamento |
|---|---|---|---|---|
| 7877 | Filzi | 72 | BR-03 | stazione ARPA 72 (Francavilla Fontana) a 198 m |
| 8063 | TERMINAL PASSEGGERI | 67 | BR-01 | stazione ARPA 67 (Brindisi - Terminal Passeggeri) a 202 m |
| 8154 | taranto SAN VITO | 21 | TA-08 | stazione ARPA 21 (Taranto - San Vito) a 1 m |
| 8378 | LECCE - S. M. Cerrate | 29 | LE-51 | stazione ARPA 29 (Lecce - Cerrate) a 93 m |
| 8379 | GUAGNANO - villa baldassarri | 28 | LE-52 | stazione ARPA 28 (Guagnano - Villa Baldassarri) a 1 m |
| 8384 | STATTE | 18 | TA-02 | stazione ARPA 18 (Statte - Sorgenti) a 0 m |
| 8499 | Ceglie Messapica | 96 | BR-03 | stazione ARPA 96 (Ceglie Messapica) a 0 m |
| 8530 | La Porta | 50 | LE-55 | stazione ARPA 50 (Galatina - I.T.C.  La Porta) a 155 m |
| 8600 | taranto WIND | 40 | TA-02 | stazione ARPA 40 (Statte - Wind) a 0 m |
| 8603 | TALSANO | 38 | TA-08 | stazione ARPA 38 (Taranto - Talsano) a 1 m |
| 8605 | San Pietro Vernotico - Campo sportivo | 26 | BR-04 | stazione ARPA 26 (San Pietro Vernotico) a 56 m |
| 8606 | TORCHIAROLO | 27 | BR-04 | stazione ARPA 27 (Torchiarolo - Don Minzoni) a 33 m |
| 8608 | Mesagne | 23 | BR-04 | stazione ARPA 23 (Mesagne - Via Udine) a 56 m |
| 8609 | Campi Salentina | 51 | LE-52 | stazione ARPA 51 (Campi Salentina) a 817 m, stesso comune nel nome |
| 8610 | Grottaglie - Scuola Pertini | 41 | TA-06 | stazione ARPA 41 (Grottaglie) a 4 m |
| 8611 | Martina Franca | 42 | TA-05 | stazione ARPA 42 (Martina Franca) a 1 m |
| 8612 | ARNESANO - Riesci | 31 | LE-51 | stazione ARPA 31 (Arnesano - Riesci) a 0 m |
| 8613 | brindisi VIA DEI MILLE | 33 | BR-01 | stazione ARPA 33 (Brindisi - Via dei Mille) a 78 m |
| 8614 | brindisi VIA MAGELLANO | 35 | BR-01 | stazione ARPA 35 (Brindisi - Casale) a 121 m |
| 8615 | brindisi SISRI | 36 | BR-01 | stazione ARPA 36 (Brindisi - SISRI) a 557 m, stesso comune nel nome |
| 8620 | GARIGLIANO | 47 | LE-51 | stazione ARPA 47 (Lecce - Garigliano) a 107 m |
| 8622 | Massafra | 75 | TA-02 | stazione ARPA 75 (Massafra) a 215 m |
| 8623 | LIBERTINI | 62 | LE-51 | stazione ARPA 62 (Lecce - Libertini) a 1 m |
| 8626 | PERRINO | 77 | BR-01 | stazione ARPA 77 (Brindisi - Perrino) a 6 m |
| 8628 | Cisternino - Via Croce | 108 | BR-02 | stazione ARPA 108 (Cisternino) a 2 m |
| 8629 | Surbo ENEL | OpenAQ-8629 | LE-51 | nessuna stazione ARPA entro 1000 m (la più vicina a 1020 m); distretto dal comune nel nome (Surbo) |
| 8630 | Torchiarolo ENEL | 93 | BR-04 | stazione ARPA 93 (Torchiarolo - Fanin) a 1 m |
| 2162927 | Taranto - CISI Paolo VI | 37 | TA-08 | stazione ARPA 37 (Taranto - CISI) a 16 m |
| 2162928 | Brindisi VIA TARANTO | 24 | BR-01 | stazione ARPA 24 (Brindisi - Via Taranto) a 1 m |
| 2162929 | San Pancrazio Salentino - Via Deledda | 25 | BR-04 | stazione ARPA 25 (San Pancrazio) a 57 m |
| 2162930 | taranto ADIGE | 22 | TA-08 | stazione ARPA 22 (Taranto - Alto Adige) a 23 m |
| 5200352 | egdp-6 | OpenAQ-5200352 | — | non assegnabile: stazione ARPA più vicina a 2297 m, nessun comune nel nome |
| 5338026 | egdp-7 | OpenAQ-5338026 | — | non assegnabile: stazione ARPA più vicina a 2341 m, nessun comune nel nome |

### Abbinamento stazioni EEA → stazioni ARPA

Solo le stazioni con dati nel periodo.

| id EEA | nome EEA | chiave nel dataset | distretto | abbinamento |
|---|---|---|---|---|
| IT1607A | Statte - Ponte Wind | 40 | TA-02 | stazione ARPA 40 (Statte - Wind) a 9 m |
| IT1608A | Statte - Via delle Sorgenti | 18 | TA-02 | stazione ARPA 18 (Statte - Sorgenti) a 10 m |
| IT1609A | Taranto - CISI Paolo VI | 37 | TA-08 | stazione ARPA 37 (Taranto - CISI) a 17 m |
| IT1610A | Taranto - San Vito | 21 | TA-08 | stazione ARPA 21 (Taranto - San Vito) a 12 m |
| IT1611A | Taranto - Machiavelli | 20 | TA-08 | stazione ARPA 20 (Taranto - Machiavelli) a 9 m |
| IT1613A | Taranto - Via Alto Adige | 22 | TA-08 | stazione ARPA 22 (Taranto - Alto Adige) a 13 m |
| IT1614A | Taranto - Talsano | 38 | TA-08 | stazione ARPA 38 (Taranto - Talsano) a 14 m |
| IT1617A | San Pancrazio Salentino - Via Deledda | 25 | BR-04 | stazione ARPA 25 (San Pancrazio) a 57 m |
| IT1618A | Brindisi - Via Taranto | 24 | BR-01 | stazione ARPA 24 (Brindisi - Via Taranto) a 11 m |
| IT1657A | San Pietro Vernotico - Campo sportivo | 26 | BR-04 | stazione ARPA 26 (San Pietro Vernotico) a 56 m |
| IT1658A | Torchiarolo - Don Minzoni | 27 | BR-04 | stazione ARPA 27 (Torchiarolo - Don Minzoni) a 40 m |
| IT1660A | Taranto - Archimede | 19 | TA-08 | stazione ARPA 19 (Taranto - Archimede) a 6 m |
| IT1663A | Mesagne - Scuola Borsellino | 23 | BR-04 | stazione ARPA 23 (Mesagne - Via Udine) a 67 m |
| IT1664A | Guagnano - Villa Baldassarre | 28 | LE-52 | stazione ARPA 28 (Guagnano - Villa Baldassarri) a 85 m |
| IT1665A | Lecce - S.M. Cerrate | 29 | LE-51 | stazione ARPA 29 (Lecce - Cerrate) a 81 m |
| IT1666A | Campi Salentina - Scuola "A. Volta" | 51 | LE-52 | stazione ARPA 51 (Campi Salentina) a 67 m |
| IT1679A | Grottaglie - Scuola Pertini | 41 | TA-06 | stazione ARPA 41 (Grottaglie) a 5 m |
| IT1680A | Martina Franca - Stazione | 42 | TA-05 | stazione ARPA 42 (Martina Franca) a 22 m |
| IT1687A | Arnesano - Riesci | 31 | LE-51 | stazione ARPA 31 (Arnesano - Riesci) a 67 m |
| IT1701A | Brindisi - Via dei Mille | 33 | BR-01 | stazione ARPA 33 (Brindisi - Via dei Mille) a 17 m |
| IT1702A | Brindisi - Casale | 35 | BR-01 | stazione ARPA 35 (Brindisi - Casale) a 2 m |
| IT1704A | Brindisi - SISRI | 36 | BR-01 | stazione ARPA 36 (Brindisi - SISRI) a 2 m |
| IT1932A | Lecce - Via Garigliano | 47 | LE-51 | stazione ARPA 47 (Lecce - Garigliano) a 89 m |
| IT1953A | Galatina - La Porta | 50 | LE-55 | stazione ARPA 50 (Galatina - I.T.C.  La Porta) a 26 m |
| IT2018A | Francavilla Fontana - Filzi | 72 | BR-03 | stazione ARPA 72 (Francavilla Fontana) a 39 m |
| IT2021A | Massafra - Via Frappietri | 75 | TA-02 | stazione ARPA 75 (Massafra) a 55 m |
| IT2044A | Lecce - Piazza Libertini | 62 | LE-51 | stazione ARPA 62 (Lecce - Libertini) a 117 m |
| IT2137A | Brindisi - Perrino | 77 | BR-01 | stazione ARPA 77 (Brindisi - Perrino) a 6 m |
| IT2139A | Brindisi - Terminal Passeggeri | 67 | BR-01 | stazione ARPA 67 (Brindisi - Terminal Passeggeri) a 202 m |
| IT2148A | Ceglie Messapica - Via Martina | 96 | BR-03 | stazione ARPA 96 (Ceglie Messapica) a 22 m |
| IT2149A | Cisternino - Via Croce | 108 | BR-02 | stazione ARPA 108 (Cisternino) a 1 m |
| IT2150A | Lecce - Via Croce (ex Surbo) | 95 | LE-51 | stazione ARPA 95 (Surbo - Croce) a 15 m |
| IT2151A | Torchiarolo - Via Fanin | 93 | BR-04 | stazione ARPA 93 (Torchiarolo - Fanin) a 25 m |

## 8. Perché mancano i valori

Solo celle di stazioni reali (escluse le stazioni fittizie `nessuna_stazione`).

| Fonte | Stato | Motivo | Celle |
|---|---|---|---|
| ARPA | NO_DATA | inquinante non misurato dalla stazione | 5640 |
| ARPA | NO_DATA | stazione non coperta dalla fonte | 39960 |
| ARPA | NULL | valore null dalla fonte | 1457 |
| CAMS | NO_DATA | inquinante non misurato dalla stazione | 13050 |
| CAMS | NO_DATA | stazione non coperta dalla fonte | 12420 |
| EEA | NO_DATA | inquinante non misurato dalla stazione | 5490 |
| EEA | NO_DATA | stazione non coperta dalla fonte | 42660 |
| EEA | NULL | nessuna misura valida nel giorno | 190 |
| OpenAQ | NO_DATA | inquinante non misurato dalla stazione | 7230 |
| OpenAQ | NO_DATA | stazione non coperta dalla fonte | 42660 |
| OpenAQ | NULL | nessun dato dalla fonte per questo giorno | 58 |

## 9. Confronto tra fonti sulle stesse celle (validazione)

ARPA, OpenAQ ed EEA misurano con le stesse stazioni (ARPA trasmette i dati all'EEA, OpenAQ li riprende dall'EEA): la ridondanza è voluta e serve a validare i dati. Sulle celle in cui due fonti hanno entrambe un `VALORE` si confrontano i valori; *concordanti* = differenza entro 1 unità (ARPA pubblica valori interi).

**Le fonti non si leggono tutte allo stesso modo** (decisione del 02/10/2026), quindi il confronto è diviso in due blocchi.

### 9.1 Che cosa è confrontabile con che cosa

| Fonte | Dato | Livello del valore | Statistica giornaliera | Blocco |
|---|---|---|---|---|
| ARPA | misurato | stazione fisica | massimo giornaliero della media mobile su 8 ore: CO; massimo orario del giorno: NO2, O3, SO2; media: PM10, PM2.5 | a parte |
| OpenAQ | misurato | stazione fisica | media (tutti gli inquinanti) | validazione diretta |
| EEA | misurato | stazione fisica | media (tutti gli inquinanti) | validazione diretta |
| CAMS | modellato | comune (stazione virtuale) | media (tutti gli inquinanti) | validazione diretta |

- **Validazione diretta — OpenAQ, EEA, CAMS:** producono tutte il valore giornaliero con la stessa regola (media delle ore del giorno, UTC+1, senza soglia di completezza), quindi si confrontano cella per cella e la quota di celle concordanti **misura la concordanza del dato**. Si accorpano in un unico blocco.
- **A parte — ARPA:** ARPA pubblica un valore già giornaliero con la *sua* statistica (il massimo per NO2, O3, SO2 e CO). Per quegli inquinanti la differenza con le altre fonti è la distanza fra un massimo e una media: **non misura un disaccordo fra fonti** e la colonna *Concordanti* resta vuota. Il confronto si tiene come lettura qualitativa (ordine di grandezza, andamento), non come validazione.
- **CAMS è l'unica fonte modellata** e non ha stazioni: il confronto si fa a **comune × giorno** contro la media delle stazioni fisiche del comune, e misura **quanto il modello somiglia alla misura nel punto** (la cella è ~10 km, la stazione un punto), non la bontà della misura.

### 9.2 Validazione diretta — OpenAQ, EEA, CAMS

Stessa statistica su tutti gli inquinanti: le percentuali di concordanza sono quelle da leggere.

#### OpenAQ ↔ EEA

Livello: stazione × giorno. Celle in cui entrambe hanno un `VALORE`: **1532**.

| Inquinante | Stessa statistica | Celle | Concordanti | Media OpenAQ | Media EEA | Diff. media (EEA−OpenAQ) | Mediana diff. assoluta | Diff. assoluta massima | Correlazione (Pearson) |
|---|---|---|---|---|---|---|---|---|---|
| NO2 | sì | 843 | 62.9% | 10.23 | 10.43 | 0.19 | 0.69 | 21.18 | 0.949 |
| O3 | sì | 263 | 24.7% | 77.3 | 76.68 | -0.62 | 2.22 | 26.84 | 0.937 |
| PM10 | sì | 34 | 26.5% | 21.95 | 22.02 | 0.07 | 2.11 | 15.2 | 0.889 |
| PM2.5 | sì | 57 | 71.9% | 13.59 | 10.47 | -3.12 | 0.47 | 122.19 | 0.228 |
| SO2 | sì | 335 | 94.6% | 3.56 | 3.45 | -0.11 | 0.07 | 27.43 | 0.643 |

Celle più discordanti fra quelle a statistica uguale (prime 10 di 570):

| stazione | giorno | inquinante | valore_OpenAQ | valore_EEA | diff |
|---|---|---|---|---|---|
| 93 | 2024-06-26 | PM2.5 | 130.64 | 8.45 | -122.19 |
| 93 | 2024-06-25 | PM2.5 | 58.3 | 11.66 | -46.64 |
| 40 | 2024-06-25 | SO2 | 29.28 | 1.85 | -27.43 |
| 67 | 2024-06-22 | O3 | 93.26 | 66.41 | -26.84 |
| 29 | 2024-06-22 | O3 | 85.54 | 59.63 | -25.92 |
| 35 | 2024-06-22 | O3 | 111.02 | 87.17 | -23.85 |
| 67 | 2024-06-30 | NO2 | 30.47 | 9.29 | -21.18 |
| 31 | 2024-06-22 | O3 | 87.13 | 67.89 | -19.24 |
| 31 | 2024-06-30 | O3 | 60.79 | 79.97 | 19.18 |
| 29 | 2024-06-30 | O3 | 54.8 | 72.83 | 18.03 |

#### OpenAQ ↔ CAMS

Livello: comune × giorno (per le fonti con stazioni: media delle stazioni fisiche del comune). Celle in cui entrambe hanno un `VALORE`: **1070**.

| Inquinante | Stessa statistica | Celle | Concordanti | Media OpenAQ | Media CAMS | Diff. media (CAMS−OpenAQ) | Mediana diff. assoluta | Diff. assoluta massima | Correlazione (Pearson) |
|---|---|---|---|---|---|---|---|---|---|
| NO2 | sì | 534 | 25.8% | 9.39 | 5.5 | -3.89 | 2.58 | 38.34 | 0.31 |
| O3 | sì | 206 | 7.8% | 76.78 | 74.88 | -1.9 | 7.19 | 42.73 | 0.755 |
| PM10 | sì | 35 | 17.1% | 21.68 | 22.07 | 0.38 | 2.57 | 11.85 | 0.881 |
| PM2.5 | sì | 59 | 30.5% | 16.98 | 10.88 | -6.11 | 1.28 | 121.38 | 0.181 |
| SO2 | sì | 236 | 41.1% | 4.18 | 2.94 | -1.23 | 1.27 | 63.53 | 0.057 |

Celle più discordanti fra quelle a statistica uguale (prime 10 di 795):

| comune | giorno | inquinante | valore_OpenAQ | valore_CAMS | diff |
|---|---|---|---|---|---|
| 074018 | 2024-06-29 | PM2.5 | 132.34 | 10.97 | -121.38 |
| 074018 | 2024-06-26 | PM2.5 | 130.64 | 10.33 | -120.31 |
| 074018 | 2024-06-30 | PM2.5 | 95.34 | 12.49 | -82.85 |
| 074018 | 2024-06-04 | SO2 | 65.6 | 2.07 | -63.53 |
| 074018 | 2024-06-25 | PM2.5 | 58.3 | 10.71 | -47.58 |
| 074005 | 2024-06-10 | O3 | 115.56 | 72.83 | -42.73 |
| 074018 | 2024-06-10 | SO2 | 45.03 | 2.78 | -42.25 |
| 073013 | 2024-06-19 | NO2 | 45.09 | 6.75 | -38.34 |
| 073013 | 2024-06-22 | NO2 | 44.31 | 7.2 | -37.11 |
| 073013 | 2024-06-18 | NO2 | 41.28 | 4.18 | -37.1 |

#### EEA ↔ CAMS

Livello: comune × giorno (per le fonti con stazioni: media delle stazioni fisiche del comune). Celle in cui entrambe hanno un `VALORE`: **1820**.

| Inquinante | Stessa statistica | Celle | Concordanti | Media EEA | Media CAMS | Diff. media (CAMS−EEA) | Mediana diff. assoluta | Diff. assoluta massima | Correlazione (Pearson) |
|---|---|---|---|---|---|---|---|---|---|
| CO | sì | 177 | 100.0% | 0.29 | 0.18 | -0.11 | 0.09 | 0.52 | -0.098 |
| NO2 | sì | 502 | 23.5% | 9.72 | 5.49 | -4.23 | 3.06 | 37.46 | 0.312 |
| O3 | sì | 205 | 8.3% | 75.91 | 74.87 | -1.04 | 6.1 | 33.34 | 0.829 |
| PM10 | sì | 516 | 27.1% | 24.6 | 23.32 | -1.28 | 1.95 | 89.03 | 0.927 |
| PM2.5 | sì | 200 | 45.5% | 10.19 | 11.07 | 0.89 | 1.1 | 10.15 | 0.901 |
| SO2 | sì | 220 | 46.8% | 3.45 | 2.96 | -0.5 | 1.08 | 8.48 | 0.239 |

Celle più discordanti fra quelle a statistica uguale (prime 10 di 1174):

| comune | giorno | inquinante | valore_EEA | valore_CAMS | diff |
|---|---|---|---|---|---|
| 073008 | 2024-06-21 | PM10 | 163.1 | 74.07 | -89.03 |
| 073029 | 2024-06-23 | PM10 | 88.2 | 20.66 | -67.54 |
| 073008 | 2024-06-22 | PM10 | 137.9 | 78.77 | -59.13 |
| 073013 | 2024-06-18 | NO2 | 41.64 | 4.18 | -37.46 |
| 073013 | 2024-06-19 | NO2 | 43.94 | 6.75 | -37.19 |
| 073013 | 2024-06-22 | NO2 | 43.62 | 7.2 | -36.42 |
| 073008 | 2024-06-12 | O3 | 29.2 | 62.54 | 33.34 |
| 073013 | 2024-06-08 | NO2 | 35.99 | 5.6 | -30.4 |
| 073013 | 2024-06-04 | NO2 | 34.94 | 4.76 | -30.19 |
| 073013 | 2024-06-21 | NO2 | 35.44 | 5.62 | -29.82 |

### 9.3 Confronti con ARPA (statistica diversa: lettura qualitativa)

Da leggere per ordine di grandezza e andamento. Dove *Stessa statistica* è "no" le differenze sono attese e la concordanza non è misurabile; la correlazione resta indicativa.

#### ARPA ↔ OpenAQ

Livello: stazione × giorno. Celle in cui entrambe hanno un `VALORE`: **1452**.

| Inquinante | Stessa statistica | Celle | Concordanti | Media ARPA | Media OpenAQ | Diff. media (OpenAQ−ARPA) | Mediana diff. assoluta | Diff. assoluta massima | Correlazione (Pearson) |
|---|---|---|---|---|---|---|---|---|---|
| NO2 | no | 803 | non misurabile | 24.76 | 10.2 | -14.56 | 10.63 | 82.38 | 0.828 |
| O3 | no | 254 | non misurabile | 100.15 | 77.51 | -22.64 | 22.21 | 48.98 | 0.852 |
| PM10 | sì | 30 | 30.0% | 22.47 | 21.66 | -0.8 | 2.25 | 15.5 | 0.913 |
| PM2.5 | sì | 57 | 71.9% | 10.49 | 13.59 | 3.09 | 0.49 | 122.64 | 0.217 |
| SO2 | no | 308 | non misurabile | 5.46 | 3.41 | -2.06 | 1.36 | 15.11 | 0.658 |

Celle più discordanti fra quelle a statistica uguale (prime 10 di 37):

| stazione | giorno | inquinante | valore_ARPA | valore_OpenAQ | diff |
|---|---|---|---|---|---|
| 93 | 2024-06-26 | PM2.5 | 8 | 130.64 | 122.64 |
| 93 | 2024-06-25 | PM2.5 | 12 | 58.3 | 46.3 |
| 72 | 2024-06-03 | PM10 | 29 | 13.5 | -15.5 |
| 72 | 2024-06-11 | PM10 | 35 | 25.8 | -9.2 |
| 72 | 2024-06-10 | PM10 | 26 | 17.8 | -8.2 |
| 72 | 2024-06-18 | PM10 | 14 | 21.8 | 7.8 |
| 72 | 2024-06-19 | PM10 | 20 | 13.8 | -6.2 |
| 72 | 2024-06-12 | PM10 | 29 | 35.1 | 6.1 |
| 33 | 2024-06-23 | PM10 | 33 | 38.46 | 5.46 |
| 96 | 2024-06-22 | PM2.5 | 23 | 28 | 5 |

#### ARPA ↔ EEA

Livello: stazione × giorno. Celle in cui entrambe hanno un `VALORE`: **3094**.

| Inquinante | Stessa statistica | Celle | Concordanti | Media ARPA | Media EEA | Diff. media (EEA−ARPA) | Mediana diff. assoluta | Diff. assoluta massima | Correlazione (Pearson) |
|---|---|---|---|---|---|---|---|---|---|
| CO | no | 277 | non misurabile | 0.36 | 0.28 | -0.08 | 0.06 | 1.1 | 0.855 |
| NO2 | no | 885 | non misurabile | 25.36 | 10.51 | -14.85 | 10.84 | 85.46 | 0.878 |
| O3 | no | 255 | non misurabile | 100.1 | 76.76 | -23.34 | 22.36 | 72.83 | 0.846 |
| PM10 | sì | 900 | 100.0% | 24.68 | 24.66 | -0.02 | 0.21 | 0.5 | 1 |
| PM2.5 | sì | 399 | 100.0% | 10.32 | 10.26 | -0.05 | 0.28 | 0.5 | 0.998 |
| SO2 | no | 378 | non misurabile | 5.49 | 3.51 | -1.98 | 1.36 | 14.53 | 0.731 |

#### ARPA ↔ CAMS

Livello: comune × giorno (per le fonti con stazioni: media delle stazioni fisiche del comune). Celle in cui entrambe hanno un `VALORE`: **2029**.

| Inquinante | Stessa statistica | Celle | Concordanti | Media ARPA | Media CAMS | Diff. media (CAMS−ARPA) | Mediana diff. assoluta | Diff. assoluta massima | Correlazione (Pearson) |
|---|---|---|---|---|---|---|---|---|---|
| CO | no | 224 | non misurabile | 0.38 | 0.19 | -0.19 | 0.16 | 1.36 | 0.015 |
| NO2 | no | 519 | non misurabile | 21.86 | 5.42 | -16.44 | 12.45 | 89.82 | 0.374 |
| O3 | no | 228 | non misurabile | 99.68 | 75.15 | -24.53 | 23.86 | 68.09 | 0.693 |
| PM10 | sì | 540 | 27.6% | 24.64 | 23.24 | -1.39 | 2 | 88.93 | 0.922 |
| PM2.5 | sì | 251 | 39.8% | 10.08 | 11.15 | 1.07 | 1.24 | 17.55 | 0.853 |
| SO2 | no | 267 | non misurabile | 4.56 | 2.74 | -1.81 | 1.71 | 8.11 | 0.462 |

Celle più discordanti fra quelle a statistica uguale (prime 10 di 542):

| comune | giorno | inquinante | valore_ARPA | valore_CAMS | diff |
|---|---|---|---|---|---|
| 073008 | 2024-06-21 | PM10 | 163 | 74.07 | -88.93 |
| 073029 | 2024-06-23 | PM10 | 88 | 20.66 | -67.34 |
| 073008 | 2024-06-22 | PM10 | 138 | 78.77 | -59.23 |
| 075039 | 2024-06-22 | PM10 | 99 | 55.75 | -43.25 |
| 073027 | 2024-06-20 | PM10 | 85.83 | 58 | -27.84 |
| 075029 | 2024-06-05 | PM10 | 40 | 13.07 | -26.93 |
| 073013 | 2024-06-22 | PM10 | 99 | 72.19 | -26.81 |
| 074016 | 2024-06-09 | PM10 | 44 | 21.72 | -22.28 |
| 075029 | 2024-06-22 | PM10 | 82 | 60.2 | -21.8 |
| 073008 | 2024-06-20 | PM10 | 77 | 55.44 | -21.56 |

## 10. Copertura: dato misurato o dato modellato

Dichiarazione necessaria per ogni analisi e per ogni correlazione che usa questo dataset: dove non ci sono stazioni, l'unico valore disponibile è **modellato** (CAMS, cella ~10 km).

- **Comuni con almeno un valore misurato** (ARPA, OpenAQ, EEA): **20 su 145**
- **Comuni coperti solo da dato modellato** (CAMS): **125**
- **Distretti con almeno un valore misurato:** **12 su 20**
- **Quota di residenti del distretto che vive in un comune con almeno una misura** (media pesata sui residenti, regola del 02/10/2026): v. tabella

**Come va letta una correlazione su questi dati:** i comuni e i distretti senza stazioni entrano nelle analisi con il valore CAMS, quindi la correlazione che li riguarda è calcolata **su dato modellato, non misurato**. La correlazione si calcola comunque — serve a leggere l'andamento dove non esistono stazioni — ma va sempre presentata con questa etichetta, nel report e in dashboard.

| Distretto | Comune sede | Comuni | Comuni con misura | Comuni solo modellati | Residenti coperti da misura | Lettura |
|---|---|---|---|---|---|---|
| BR-01 | Brindisi | 2 | 1 | 1 | 82% | misurato |
| BR-02 | Fasano | 3 | 1 | 2 | 14% | misurato |
| BR-03 | Francavilla Fontana | 6 | 2 | 4 | 54% | misurato |
| BR-04 | Mesagne | 9 | 4 | 5 | 54% | misurato |
| LE-51 | Lecce | 10 | 3 | 7 | 64% | misurato |
| LE-52 | Campi Salentina | 8 | 2 | 6 | 18% | misurato |
| LE-53 | Nardo' | 6 | 0 | 6 | 0% | solo modellato |
| LE-54 | Martano | 10 | 0 | 10 | 0% | solo modellato |
| LE-55 | Galatina | 6 | 1 | 5 | 45% | misurato |
| LE-56 | Gallipoli | 8 | 0 | 8 | 0% | solo modellato |
| LE-57 | Maglie | 12 | 1 | 11 | 26% | misurato |
| LE-58 | Poggiardo | 15 | 0 | 15 | 0% | solo modellato |
| LE-59 | Casarano | 7 | 0 | 7 | 0% | solo modellato |
| LE-60 | Gagliano Del Capo | 14 | 0 | 14 | 0% | solo modellato |
| TA-01 | Ginosa | 4 | 0 | 4 | 0% | solo modellato |
| TA-02 | Massafra | 4 | 2 | 2 | 59% | misurato |
| TA-05 | Martina Franca | 2 | 1 | 1 | 78% | misurato |
| TA-06 | Grottaglie | 11 | 1 | 10 | 32% | misurato |
| TA-07 | Manduria | 7 | 0 | 7 | 0% | solo modellato |
| TA-08 | Taranto | 1 | 1 | 0 | 100% | misurato |

## 11. Errori delle API

Nessun errore.
