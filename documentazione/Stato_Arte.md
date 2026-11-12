# Stato dell'arte — Progetti di correlazione qualità dell'aria / salute (con focus respiratorio)

  *Obiettivo: mappare i riferimenti esistenti — teorici o realizzati, solo software o basati su hardware/wearable — a progetti che mettono in relazione la qualità dell'aria con l'incidenza di patologie (soprattutto respiratorie), per posizionare OneHealth rispetto allo stato dell'arte e citarli in tesi.*

## 1. Criteri di classificazione

Ogni riferimento è classificato su due assi indipendenti:

- **Teorico vs. Implementato** — *teorico*: studio, metodologia o framework pubblicato (paper, rassegna), senza una piattaforma pubblica operativa e mantenuta nel tempo; *implementato*: sistema/dispositivo realmente costruito, distribuito o in uso (anche come pilota/prototipo testato sul campo).
- **Software vs. Hardware/wearable** — *software*: usa dati già esistenti (stazioni pubbliche, registri sanitari, satellite) senza rilevazione fisica dedicata; *hardware/wearable*: introduce un dispositivo di rilevazione (indossabile o portatile) per la misura diretta.

---

## 2. Software — Implementato (piattaforme/programmi realmente operativi)

### 2.1 CDC — National Environmental Public Health Tracking Network (USA)
Rete nazionale statunitense che integra dati ambientali (inclusa qualità dell'aria, misurata e modellata) e dati di salute pubblica in un unico *Data Explorer* con dashboard tematiche. È il precedente istituzionale più maturo e longevo per l'idea di "cruscotto ambiente-salute" su scala nazionale, gestito dai CDC.
- https://ephtracking.cdc.gov/
- https://www.cdc.gov/environmental-health-tracking/php/data-research/air-quality-outdoor.html

CDC works closely with federal partners. These include Environmental Protection Agency (EPA), National Aeronautics and Space Administration (NASA), and National Oceanic and Atmospheric Association (NOAA).
EPA and CDC studies found that modeled predictions of air pollution are very similar to actual data.A However, in some areas, modeled data underestimate or overestimate the air pollutant concentration levels.

### 2.2 EEA — European Environment and Health Atlas / European City Air Quality Viewer (UE)
Atlante interattivo dell'Agenzia Europea per l'Ambiente: mappe di concentrazione di PM2.5/NO2/O3, popolazione esposta, morti premature attribuibili e anni di vita persi, fino al livello di singola città (con classifica comparativa e stima del costo economico dei decessi prematuri). È il riferimento europeo più vicino, in scala, a quanto vuole fare OneHealth su scala di distretto.
- https://www.eea.europa.eu/en/newsroom/news/european-environment-and-health-atlas
- https://www.eea.europa.eu/en/topics/in-depth/air-pollution/european-city-air-quality-viewer

The interactive online tool, a first on such a scale for all of Europe, allows users to visualise how the environment around them affects their health and well-being via set of detailed maps. It covers topics like air quality, noise and quietness, green and blue spaces and climate change throughout the member and collaborating countries of the EEA. 

### 2.3 WHO — AirQ+ (Globale)
Software scaricabile (non un servizio web continuo) sviluppato da OMS/Europa per stimare il carico sanitario attribuibile all'inquinamento atmosferico, a partire da relazioni esposizione-rischio da studi di coorte. Oltre 1000 utenti in 112 paesi, applicato in più di 300 città. Va usato con il supporto di un epidemiologo: è più un motore di calcolo dell'impatto che un cruscotto di monitoraggio continuo, ma è lo standard metodologico di riferimento per tradurre concentrazioni di inquinanti in stime di mortalità/morbilità.
- https://www.who.int/tools/airq

### 2.4 WHO/Europe — ENHIS, Environment and Health Information System (UE, storico)
Database interattivo di indicatori ambiente-salute a livello di paese (55 indicatori, incl. esposizione a PM outdoor), con grafici a linee, barre e mappe. Nato prima dell'Atlante EEA (§2.2), che ne rappresenta di fatto l'evoluzione più recente e granulare. Utile come riferimento storico/metodologico, meno come fonte dati aggiornata.
- https://gateway.euro.who.int/en/datasets/enhis

### 2.5 Atlante Aria Salute (Italia — Ministero della Salute, ISS, ISPRA, Regioni)
**Il precedente italiano più simile a OneHealth nell'impostazione.** Piattaforma web nazionale (con declinazioni regionali) finanziata dal Ministero della Salute (bando CCM), che integra dati ISTAT, ISPRA e Ministero della Salute per rappresentare in modo interattivo l'impatto dell'inquinamento atmosferico sulla salute della popolazione adulta, includendo scenari previsionali e fattori di contesto (socioeconomici, stili di vita). Esiste anche un lavoro di tesi (Politecnico di Milano) sulla visualizzazione narrativa dei dati previsionali di questo atlante. Differenze principali rispetto a OneHealth: scala nazionale/regionale (non distrettuale-locale), nessun modulo LLM/RAG, nessun focus esplicito su presidi/aziende sanitarie come utenza.
- https://www.isprambiente.gov.it/it/progetti/cartella-progetti-in-corso/ambiente-e-salute-1/aria-outdoor-e-salute-un-atlante-integrato-a-supporto-delle-decisioni-e-della-ricerca-per-ambienti-piu-sani-inclusivi-piu-sicuri-resilienti-e-sostenibili
- https://www.regione.piemonte.it/web/temi/sanita/qualita-dellaria-salute-latlante-supporto-delle-decisioni-della-ricerca
- Tesi (Polimi, visualizzazione dati previsionali): https://www.politesi.polimi.it/handle/10589/240955

### 2.6 SENTIERI — Studio Epidemiologico Nazionale dei Territori e degli Insediamenti Esposti a Rischio da Inquinamento (ISS, Italia)
Programma nazionale coordinato dall'Istituto Superiore di Sanità dal 2007, che studia la mortalità (e in parte l'ospedalizzazione) delle popolazioni residenti nei Siti di Interesse Nazionale (SIN) per contaminazione ambientale. **Include specificamente il SIN di Taranto** (ILVA), con eccessi di mortalità documentati per tumori polmonari, mesotelioma e malattie respiratorie nel periodo 2000-2009. Non è un cruscotto interattivo pubblico, ma un programma di sorveglianza epidemiologica con rapporti periodici strutturati (pubblicati su *Epidemiologia & Prevenzione*) — è quindi "implementato" come programma/metodologia ricorrente, non come piattaforma self-service.
- https://epiprev.it/page/sentieri-studio-epidemiologico-nazionale-dei-territori-e-degli-insediamenti-esposti-a-rischio-da-inquinamento
- https://www.epicentro.iss.it/ambiente/IlvaTaranto

### 2.7 Centro Salute Ambiente Puglia (CSA) — Progetto Jonico-Salentino
**Il precedente locale più diretto**, già individuato nella ricerca dataset di OneHealth (`03_Ricerca_Dataset_Fase2.md`). Struttura regionale pugliese con sede a Taranto, dedicata proprio alla relazione ambiente-salute sull'asse **Taranto-Brindisi-Lecce** (lo stesso territorio "Salento" di OneHealth). Il Progetto Jonico-Salentino integra dati da centraline di monitoraggio con test tossicologici *in vivo* (membrana corion-allantoidea di embrione di pollo) e *in vitro* (cellule umane esposte a campioni d'aria), per profilare il rischio di esposizione della popolazione. È un ibrido studio scientifico + monitoraggio ambientale, non un cruscotto software consultabile online, ma resta il riferimento istituzionale più pertinente per validare metodologicamente l'approccio di OneHealth in tesi.
- https://www.sanita.puglia.it/web/csa/progetto-jonico-salentino
- https://www.sanita.puglia.it/web/csa/obiettivi

### 2.8 AReSS Puglia — Open Salute Puglia / PugliaStat (Puglia)
Vedi dettaglio in `ricerca/03_Datasets_List.md` del repository Presentation (nuova sezione 2f) e `salute/Lista_dataset_salute.md`. In sintesi: non correla esplicitamente aria e salute, ma è la piattaforma sanitaria regionale di riferimento — **PugliaStat** in particolare offre nativamente la granularità **provinciale/distrettuale/comunale** (la stessa zonizzazione decisa per OneHealth) su ospedalizzazioni e decessi.
- https://opensalute.aress.regione.puglia.it/
- https://aress.regione.puglia.it/en/aree-tematiche/mappe-e-dati-per-la-salute/pugliastat

### 2.9 IHME — Global Burden of Disease (GBD), Globale
Strumento di visualizzazione dati (GBD Compare / GBD Results Tool) che include l'inquinamento atmosferico tra i fattori di rischio modellati per il carico di malattia (DALY, mortalità) a livello di paese/regione. The GBD study is the largest and most comprehensive effort to quantify health loss across places and over time, so health systems can be improved and disparities eliminated.

- https://www.healthdata.org/research-analysis/gbd

---

## 3. Software — Teorico / di ricerca (studi e metodologie senza piattaforma pubblica)

### 3.1 BEEP — Big data in Environmental and occupational EPidemiology (INAIL, Italia)
Progetto co-finanziato INAIL per integrare dati nazionali (ambientali, meteorologici, di rumore) e studiarne gli effetti sanitari sulla popolazione italiana attraverso tecniche di big data. Infrastruttura di ricerca, non un servizio pubblico consultabile.

### 3.2 Pisan Longitudinal Study — effetti del particolato sull'incidenza di malattie respiratorie (Pisa, Italia)
Studio epidemiologico longitudinale che misura l'associazione tra esposizione a particolato (PM) e incidenza di patologie respiratorie in una coorte residente a Pisa. Riferimento metodologico diretto per l'analisi esplorativa aria-salute di OneHealth.
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7177905/

### 3.3 Studio case-crossover su accessi in Pronto Soccorso e inquinanti (Milano, Italia)
Analizza la correlazione tra livelli di ozono e altri inquinanti e accessi in pronto soccorso per patologie respiratorie (es. asma) a Milano, con un aumento del 78% degli accessi per asma associato a picchi di ozono nella stagione calda. Metodologia case-crossover rilevante per l'analisi esplorativa di OneHealth.
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3511062/

### 3.4 Approccio GIS per l'associazione tra inquinamento e asma (New York State, USA)
Studio metodologico che usa il GIS per mappare la sovrapposizione spaziale tra inquinanti atmosferici e ricoveri per asma, con tecniche di interpolazione (inverse distance weighting, kriging, land-use regression) — le stesse tecniche rilevanti per il problema di OneHealth di associare stazioni ARPA puntuali a distretti socio-sanitari areali.
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4053878/

### 3.5 Rassegne sistematiche — inquinamento atmosferico e COVID-19 / patologie respiratorie in Europa
Diverse rassegne sistematiche (es. impatto dell'inquinamento su incidenza/gravità/mortalità COVID-19 in Europa e Nord America; aggiornamento generale su inquinamento outdoor e malattie respiratorie con prospettiva italiana) sintetizzano lo stato della letteratura epidemiologica, confermando l'associazione ma **sempre con l'avvertenza sui fattori confondenti** (fumo, età, comorbidità) — lo stesso framing "esplorativo, non causale" adottato da OneHealth.
- https://pmc.ncbi.nlm.nih.gov/articles/PMC9420033/
- https://journalpulmonology.org/en-issue-1-update-on-articulo-S2531043722000113

### 3.6 Rassegna satellite + GIS per sorveglianza dell'inquinamento e delle malattie respiratorie
Rassegna che descrive l'uso combinato di telerilevamento satellitare, GIS e machine learning (kriging spazio-temporale, land-use regression) per stimare l'esposizione e sorvegliare le malattie respiratorie — utile come riferimento per l'eventuale estensione futura di OneHealth a dati satellitari/CAMS oltre alle sole stazioni ARPA.
- https://zenodo.org/records/20714468

### 3.7 Studio GIS/kriging su PM2.5 e rischio respiratorio-cardiovascolare a Baghdad (Iraq)
*Aggiunto 24/09/2026 (verificato, da ricerca Perplexity).* Qasim et al., "Estimating Respiratory and Cardiovascular Health Risks Associated with PM2.5 Concentration in Major Populated Areas of Iraq with Examining Its Correlation to COVID-19", *Iraqi Geological Journal*, 58(1B), 2025, pp. 180-192. Usa Ordinary Kriging e dati satellitari (AOD/MODIS) per mappare la distribuzione spaziale di PM2.5/PM10 a Baghdad e correlarla con il rischio di malattie respiratorie/cardiovascolari. Esempio pratico — non italiano, ma metodologicamente vicino — di interpolazione spaziale da dati puntuali/modellati a rischio sanitario per area, applicabile al problema di OneHealth di derivare un valore di qualità dell'aria per distretto socio-sanitario a partire da stazioni ARPA puntuali.
- https://igj-iraq.org/igj/index.php/igj/article/view/2587

### 3.8 Framework di Explainable AI per la correlazione inquinanti-malattie su scala globale (Thapar Institute)
*Aggiunto 24/09/2026 (contenuto confermato via motore di ricerca, ma URL della pagina esatta non identificato — verificare manualmente nel repository prima di citarlo in tesi).* Tesi (Thapar Institute of Engineering and Technology, TIET Digital Repository) che integra inventari di emissioni EDGAR v8.1 con indicatori sanitari WHO Global Health Observatory su 177 paesi, 9 inquinanti e 6 categorie di malattia (2010-2019), proponendo due architetture deep learning (RBN-BiLSTM, T-RBN-BiLSTM) con attribuzione SHAP per patologia. Rilevante come esempio di superamento della correlazione lineare semplice tramite AI spiegabile, ma a scala globale/nazionale, non locale come OneHealth.
- Repository: https://tudr.thapar.edu/ (titolo/autore esatti e URL diretto della tesi da verificare manualmente prima della citazione in tesi)

---

## 4. Hardware / wearable — Implementato (dispositivi realmente sviluppati o in pilota)

### 4.1 RESPIRO — Università di Milano-Bicocca (Italia)
**Già citato nell'abstract di progetto (`06_Abstract_Proposta_Progetto.md`) come precedente che ha motivato l'abbandono della via hardware.** Dispositivo indossabile low-cost (agganciabile a zaino/borsa/giacca) sviluppato da Unimib con ROAD – Rome Advanced District e XearPro srl, che rileva CO2, CO, polveri sottili/ultrafini, temperatura, umidità e pressione in tempo reale, con GPS, display LED e app Bluetooth con notifiche di rischio. In uso in campagne di rilevamento con volontari/studenti a Milano (coordinamento: Centro di Ricerca POLARIS). Conferma che il segmento "wearable per qualità dell'aria personale" è già presidiato da un ateneo italiano con un prodotto maturo.
- https://www.unimib.it/comunicati/respiro-monitoraggio-della-qualita-dellaria-diventa-indossabile-tempo-reale-e-alla-portata-tutti
- https://polaris.unimib.it/en/2025/05/19/respiro-en/

### 4.2 SOCIO-BEE (Horizon Europe, UE — incl. pilota Ancona, Italia)
Nodo sensore indossabile wireless sviluppato nell'ambito del progetto Horizon Europe SOCIO-BEE, che misura NO2, O3 e PM2.5 tramite citizen science. Tre campagne pilota (Ancona/Italia, Maroussi/Grecia, Zaragoza/Spagna) con gruppi di utenti diversi (anziani, pendolari, studenti); buona correlazione con dati ufficiali (R²=0.75). È il precedente più recente e più vicino geograficamente (pilota italiano, 2025) a un wearable per qualità dell'aria con validazione scientifica pubblicata.
- https://www.mdpi.com/1424-8220/25/12/3739
- https://pmc.ncbi.nlm.nih.gov/articles/PMC12197209/

### 4.3 hackAIR (Horizon 2020, UE)
Piattaforma di citizen science che integra dati da stazioni ufficiali, sensori DIY (statici e portatili via Bluetooth) e stime da foto del cielo, per colmare le lacune spaziali della rete ufficiale e aumentare la consapevolezza pubblica sulla qualità dell'aria. Ibrido hardware (sensori a basso costo) + software (piattaforma di aggregazione). Focus su awareness, non su esiti sanitari.
- https://www.hackair.eu/
- https://cordis.europa.eu/article/id/314290-new-technology-platform-harnesses-citizen-science-to-monitor-air-pollution

### 4.4 CAPTOR (Horizon 2020, UE)
Rete di sensori low-cost per l'ozono troposferico, gestita da comunità locali in tre testbed europei, guidata dall'Universitat Politècnica de Catalunya. Citizen science hardware-based, focalizzata su un singolo inquinante (ozono).
- https://www.captor-project.eu/

### 4.5 AirPredict — piattaforma eHealth per la gestione dell'asma
Piattaforma che combina sensori indossabili, diario digitale del paziente e monitoraggio della qualità dell'aria per ottimizzare la gestione clinica dell'asma, con tracciamento individualizzato dell'esposizione e degli esiti di salute in tempo reale. Ibrido wearable + software clinico, in fase di validazione/pilota.
- https://www.frontiersin.org/journals/digital-health/articles/10.3389/fdgth.2025.1573342/full
- https://pmc.ncbi.nlm.nih.gov/articles/PMC12179981/

### 4.6 Wearable commerciali (mercato, cenno)
Prodotti di mercato consolidati per il monitoraggio personale della qualità dell'aria (es. AirBeam, Flow di Plume Labs, Atmotube) — non progetti di ricerca, ma confermano ulteriormente la saturazione del segmento hardware/wearable "qualità dell'aria personale" già rilevata nell'abstract di progetto.

### 4.7 AIR-DT / RESPIRA-DT — Digital Twin per la qualità dell'aria indoor e l'asma (Birmingham City University, UK)
*Aggiunto 24/09/2026 (verificato, da ricerca Perplexity).* Khosh Amadi et al., "Development of a spatially contextualised and AI-enabled digital twin for asthma specific indoor air quality management", *Journal of Building Engineering*, dicembre 2025; sviluppato ulteriormente nella tesi di dottorato "An Asthma Occupant Focused Digital Twin for Indoor Air Quality in Residential Environments" (Birmingham City University, 2026) e in un lavoro correlato del 2026, "RESPIRA-DT: A digital twin framework for proactive IAQ management in asthma-sensitive residential buildings". Il framework (AIR-DT) integra sensori IoT indoor (PM2.5, PM10, CO2, TVOC, temperatura, umidità, apertura finestre), previsione a breve termine e alert personalizzati; è stato pilotato con famiglie reali a Walsall (UK) su bambini asmatici. Non è un wearable ma un **Digital Twin a scala di edificio/paziente**: utile a OneHealth non per la tecnologia in sé, ma per il framework concettuale (monitoraggio → predizione → intervento) e come termine di paragone per posizionare OneHealth come un "Digital Twin di distretto sanitario" anziché di singolo edificio/paziente (v. §7).
- Tesi: https://www.open-access.bcu.ac.uk/16970/
- Paper: https://pureportal.bcu.ac.uk/en/publications/development-of-a-spatially-contextualised-and-ai-enabled-digital-/
- RESPIRA-DT (2026): https://www.sciencedirect.com/science/article/abs/pii/S2352710226017316
- Pilota Walsall (comunicato BCU): https://www.bcu.ac.uk/news-events/news/bcu-created-digital-twin-gives-kids-a-breath-of-fresh-air

### 4.8 Wearable Body Sensor Network per l'esposizione personale — Politecnico di Milano
*Aggiunto 24/09/2026 (verificato, da ricerca Perplexity).* Bernasconi et al., "A New Wearable System for Personal Air Pollution Exposure Estimation: Pilot Observational Study", *JMIR mHealth and uHealth*, 2025. Sistema indossabile (Body Sensor Network) che stima l'esposizione personale a PM1/PM2.5/PM10 combinando dati ambientali e fisiologici (frequenza cardiaca e respiratoria, ventilazione minuto) su 20 volontari a Milano. Risultato chiave: l'esposizione personale a PM2.5 stimata dal wearable è risultata **in media 2,96 µg/m³ (+22,3%) superiore** a quella stimata dalla sola centralina fissa più vicina. **Rilevante per il posizionamento di OneHealth**: conferma quantitativamente il limite intrinseco di un approccio a stazioni fisse (sottostima dell'esposizione individuale reale), che OneHealth accetta consapevolmente in cambio di scalabilità a costo zero su scala di popolazione/distretto — un compromesso da esplicitare in tesi.
- https://mhealth.jmir.org/2025/1/e60426
- https://pmc.ncbi.nlm.nih.gov/articles/PMC12248256/

---

## 5. Hardware / wearable — Teorico / prototipale (ricerca non oltre il prototipo/laboratorio)

### 5.1 Dispositivo indossabile standalone per performance polmonare + qualità dell'aria (IEEE)
Prototipo di ricerca che integra spirometro (peak flow meter), sensori di NO2/SO2/O3/particolato, temperatura, microprocessore e GPS in un unico dispositivo per pazienti con patologie respiratorie croniche.
- https://ieeexplore.ieee.org/document/9842228/

### 5.2 Wearable da polso a basso costo per i trigger dell'asma
Prototipo accademico (peso 64g, componenti commerciali <150$) che misura ozono, COV, temperatura, umidità e livello di attività per identificare i fattori scatenanti dell'asma.

### 5.3 Personal Exposure Monitor low-cost a sensori metal-oxide
Prototipo di monitor indossabile a basso costo basato su sensori a ossido di metallo, sviluppato specificamente per lo studio delle malattie respiratorie.
- https://pmc.ncbi.nlm.nih.gov/articles/PMC8318339/

### 5.4 Rete di sensori AI-IoT low-cost per pazienti con problemi respiratori
Prototipo di rete di sensori a basso costo con intelligenza artificiale integrata, pensato per assistere cittadini con patologie respiratorie tramite monitoraggio dell'inquinamento.
- https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10708678/

### 5.5 AERION — framework IoT per spirometria e qualità dell'aria (prototipo accademico)
*Aggiunto 24/09/2026 (verificato, da ricerca Perplexity).* Prototipo di ricerca (Mar Baselios College of Engineering and Technology, pubblicato su *International Journal of Engineering Research & Technology*, aprile 2026) basato su microcontrollore ESP32 che integra spirometro portatile (FVC, FEV1, PEF) e sensori di qualità dell'aria, con storico e analisi predittiva su cloud (Next.js/Firebase). Ulteriore conferma della saturazione del segmento hardware a scala di singolo paziente, con focus clinico individuale (non di popolazione/distretto come OneHealth).
- https://www.ijert.org/aerion-an-iot-framework-for-combined-respiratory-and-environment-health-ijertv15is040219

---

## 6. Tabella riepilogativa

| Progetto | Teorico / Implementato | Software / Hardware | Ambito | Rilevanza per OneHealth |
|---|---|---|---|---|
| CDC Tracking Network | Implementato | Software | USA, nazionale | Precedente istituzionale di riferimento (cruscotto ambiente-salute) |
| EEA Environment & Health Atlas | Implementato | Software | UE, fino a città | Scala più vicina a OneHealth (mortalità PM2.5/NO2/O3 per area) |
| WHO AirQ+ | Implementato | Software | Globale | Standard metodologico per stima impatto sanitario |
| ENHIS (WHO Europe) | Implementato (storico) | Software | UE | Precedente storico, superato dall'Atlante EEA |
| Atlante Aria Salute | Implementato | Software | Italia | **Precedente italiano più simile** (dati ISTAT/ISPRA/Min. Salute) |
| SENTIERI (ISS) | Implementato (programma) | Software/statistico | Italia, incl. Taranto SIN | Copre direttamente il territorio Taranto |
| CSA Puglia — Progetto Jonico-Salentino | Implementato | Ibrido (monitoraggio+studi) | Puglia (TA-BR-LE) | **Precedente locale più diretto** |
| AReSS — Open Salute Puglia / PugliaStat | Implementato | Software | Puglia | Granularità distrettuale nativa su mortalità/ricoveri |
| GBD / IHME | Implementato | Software | Globale | Framework standard rischio ambientale → carico di malattia |
| BEEP (INAIL) | Teorico/ricerca | Software | Italia | Metodologia big data ambiente-salute |
| Pisan Longitudinal Study | Teorico/ricerca | Software | Italia (Pisa) | Metodologia PM → incidenza respiratoria |
| Case-crossover Milano | Teorico/ricerca | Software | Italia (Milano) | Metodologia O3 → accessi PS |
| GIS asma New York | Teorico/ricerca | Software | USA | Metodologia interpolazione stazione→area |
| Rassegne COVID/respiratorio | Teorico/ricerca | Software | Europa/Nord America | Framing "esplorativo non causale" |
| Rassegna satellite+GIS | Teorico/ricerca | Software | Globale | Estensione futura a dati satellitari |
| GIS/kriging Baghdad | Teorico/ricerca | Software | Iraq | Metodologia interpolazione spaziale PM→rischio |
| XAI EDGAR-WHO (Thapar) | Teorico/ricerca (URL da verificare) | Software | Globale (177 paesi) | AI spiegabile oltre la correlazione lineare, scala globale |
| RESPIRO (Unimib) | Implementato | Hardware/wearable | Italia (Milano) | Motivo dell'abbandono dell'hardware (già citato in abstract) |
| SOCIO-BEE | Implementato (pilota) | Hardware/wearable | UE, incl. Ancona | Wearable più recente/vicino, validato scientificamente |
| hackAIR | Implementato | Ibrido HW/SW | UE | Citizen science, awareness |
| CAPTOR | Implementato | Hardware/wearable | UE | Citizen science, solo ozono |
| AirPredict | Implementato (pilota clinico) | Ibrido HW/SW | Clinico (asma) | Wearable + software clinico |
| Wearable commerciali | Implementato | Hardware | Globale, mercato | Conferma saturazione mercato |
| AIR-DT / RESPIRA-DT (BCU) | Implementato (pilota) | Ibrido IoT indoor+AI | UK (Walsall) | Digital Twin di edificio/paziente — contrasto con DT di distretto di OneHealth |
| Wearable BSN (Polimi) | Implementato (pilota) | Hardware/wearable | Italia (Milano) | Quantifica il limite delle stazioni fisse (+22,3% esposizione reale) |
| AERION | Teorico/prototipo | Ibrido HW/SW | Accademico (India) | Prototipo clinico individuale, conferma saturazione scala paziente |
| Wearable IEEE lung+air | Teorico/prototipo | Hardware | Accademico | Prototipo di laboratorio |
| Wrist-worn asthma triggers | Teorico/prototipo | Hardware | Accademico | Prototipo di laboratorio |
| PEM metal-oxide low-cost | Teorico/prototipo | Hardware | Accademico | Prototipo di laboratorio |
| AI-IoT sensor network | Teorico/prototipo | Hardware | Accademico | Prototipo di laboratorio |

---

## 7. Osservazioni per il posizionamento di OneHealth

- **Nessuno dei precedenti individuati combina tutti gli elementi distintivi di OneHealth**: (a) approccio interamente software su dati pubblici, senza hardware; (b) granularità di **distretto socio-sanitario** come unità di decisione; (c) utenza esplicita = presidi medici/aziende sanitarie per il controllo di gestione, non cittadini o soli ricercatori; (d) modulo **LLM locale + RAG** per l'interrogazione in linguaggio naturale dei dati raccolti. L'Atlante Aria Salute (§2.5) è il più vicino sul lato "software nazionale decisionale", ma a scala più ampia e senza componente conversazionale.
- **Il lato hardware/wearable è saturo**, e la ricerca conferma quanto già scritto nell'abstract di progetto: RESPIRO (Unimib, 2025) e SOCIO-BEE (Horizon Europe, pilota Ancona 2025) sono precedenti recenti, italiani/europei, con validazione scientifica pubblicata — un ulteriore dispositivo aggiungerebbe poco. Questi progetti, però, si concentrano sull'**esposizione personale in tempo reale**, non sul supporto decisionale territoriale/gestionale: è un obiettivo diverso da quello di OneHealth, non sovrapposto.
- **Il precedente locale più rilevante da citare e possibilmente contattare è il Centro Salute Ambiente Puglia (Progetto Jonico-Salentino, §2.7)**: stesso territorio (TA-BR-LE), stesso obiettivo concettuale (profilo di rischio ambiente-salute), già segnalato nella ricerca dataset di fase 2 come possibile interlocutore.
- **SENTIERI (§2.6)** è la fonte più autorevole per dati/evidenze storiche su Taranto, utile sia come riferimento in tesi sia come possibile validazione esterna dei risultati di OneHealth sul distretto tarantino.
- Il framing **"correlazione esplorativa, non causale"** adottato da OneHealth (`Regole_dei_dati.md` del repository Backend) è coerente con l'intera letteratura epidemiologica esaminata (§3.5): nessuno studio individuato dichiara causalità diretta senza controllare (o dichiarare esplicitamente di non controllare) per fumo, età e comorbidità.
- **OneHealth come "Digital Twin di distretto sanitario".** L'integrazione del 24/09/2026 (§4.7) ha individuato un filone di ricerca 2025-2026 sui Digital Twin per la qualità dell'aria indoor (AIR-DT/RESPIRA-DT, Birmingham City University), che condivide con OneHealth il framework concettuale *monitoraggio → predizione → intervento*, ma a scala di singolo edificio/paziente asmatico. Questo permette una distinzione concettuale utile per la tesi: OneHealth può essere descritto come un Digital Twin **di distretto socio-sanitario** (scala di popolazione/gestione), non di edificio o paziente — una nicchia scala non coperta dai precedenti individuati finora.
- **Il compromesso "stazioni fisse vs. esposizione personale" è ora quantificato.** Lo studio del Politecnico di Milano (§4.8, Bernasconi et al. 2025) mostra che un wearable stima l'esposizione personale a PM2.5 in media il 22,3% più alta di quella derivata dalla centralina fissa più vicina. Questo non invalida l'approccio di OneHealth (che stima il rischio a livello di popolazione/distretto, non l'esposizione del singolo individuo), ma è un limite da dichiarare esplicitamente in tesi quando si discute la scelta di usare solo dati di stazioni pubbliche.

## 8. Limiti di questa ricognizione

- Ricerca svolta con query in inglese e italiano su motori generalisti: possibile aver mancato letteratura in altre lingue o pubblicata su riviste non indicizzate nei risultati di ricerca standard.
- Non è stata verificata l'effettiva disponibilità/formato dei dati di ciascuna piattaforma citata (alcune pagine sono dinamiche/JS e non completamente ispezionabili automaticamente) — da fare manualmente se una fonte diventa rilevante per la pipeline.
- Da approfondire in una fase successiva: letteratura specifica su "digital twin"/DSS sanitari territoriali (non solo aria-salute) e su LLM/RAG applicati a dati sanitari pubblici, per posizionare meglio il modulo AI di OneHealth.
- **Integrazione 24/09/2026 — riferimenti scartati.** Matteo ha condotto la stessa ricerca in parallelo su Perplexity e ChatGPT. Il contenuto di ChatGPT si è rivelato in larga parte ridondante con questa ricognizione (nessun riferimento nuovo, utile come triangolazione/conferma). Da Perplexity sono stati integrati solo i riferimenti verificati con ricerca mirata (§3.7, §3.8, §4.7, §4.8, §5.5); sono stati **scartati** perché non verificabili: una presunta tesi "Assessment of Air Quality Index (AQI) Trends and Public Health Impacts (2024-2026)" (titolo generico, non rintracciabile, citata con un URL — salute.gov.it — non pertinente al contenuto), lo studio Politecnico di Milano citato solo tramite un blog di terze parti (airoasis.com) invece della fonte primaria (poi ritrovata e usata correttamente in §4.8), e un riferimento su Environment International (2026) citato solo tramite un blog (b2slab.upc.edu) senza che la ricerca mirata ne confermasse l'esistenza come articolo primario. In generale, diversi marcatori di nota nel report di Perplexity risultavano abbinati a contenuti non pertinenti (segno di citazioni generate automaticamente e non affidabili) — criterio adottato: includere solo ciò che una ricerca web indipendente ha confermato con fonte primaria identificabile.
