# Dichiarazione sull'utilizzo dell'Intelligenza Artificiale

**Progetto:** OneHealth v2: dashboard di supporto decisionale su aria, calore urbano e salute nel Salento
**Autore:** Matteo Leopizzi
**Corso:** Perfezionamento in Tecnologie Digitali per Ambienti e Sistemi Intelligenti, Università del Salento (IDA Lab), A.A. 2025/2026
**Azienda partner:** Parsec 3,26 (Lecce)
**Data:** novembre 2026

Questo documento dichiara se e come sono stati usati strumenti di Intelligenza Artificiale nel lavoro. Distingue gli strumenti usati **per produrre** il progetto, la tesina e il codice (§1-3) dal modello di linguaggio che è invece **un componente del prodotto** (§4).

## 1. Strumenti usati come supporto

| Strumento | Uso |
| --- | --- |
| **Claude Code** (Anthropic), modelli della famiglia Claude | Assistente di programmazione nel repository: scrittura e revisione del codice Python e TypeScript, della documentazione di progetto in `data/`, delle bozze delle sezioni della tesina, dei test e degli script di verifica |
| **Consensus** | Ricerca di articoli scientifici per lo stato dell'arte sulle isole di calore |
| **Perplexity** e **ChatGPT** | Ricerche preliminari per lo stato dell'arte su progetti e piattaforme aria-salute e per l'individuazione dei dataset, riportate poi in `documentazione/Stato_Arte.md` del repository Presentation dopo la verifica delle fonti |
| **Impeccable** (competenza per Claude Code) | Critica e rifinitura dell'interfaccia della dashboard |

## 2. Dove l'IA ha contribuito

- **Codice**: client delle fonti dati, pipeline, server locale, dashboard e modulo dell'assistente. Matteo ha deciso architettura, stack, vincoli e perimetro; l'assistente di programmazione ha scritto e modificato il codice nelle sessioni di lavoro, e il risultato è stato eseguito e provato con i dati reali.
- **Documentazione di progetto**: schede delle fonti, registro delle scelte progettuali, piani e report di validazione, scritti con l'assistente a partire dalle decisioni di Matteo.
- **Tesina**: bozze delle sezioni scritte con l'assistente, poi riviste da Matteo. Ogni documento di progetto è la fonte della tesina, che ne è la stesura accademica.
- **Ricerca bibliografica**: l'IA ha proposto i riferimenti; nella tesina compaiono solo fonti realmente consultate.

## 3. Cosa è rimasto a carico dell'autore

- Le **decisioni di progetto**: obiettivo, destinatari, fonti ammesse, perimetro, vincoli (solo dati pubblici, nessun costo, esecuzione in locale), scelta del modello e delle regole dell'assistente. Ogni scelta aperta è stata posta a Matteo con le alternative e chiusa da lui.
- La **verifica**: esecuzione del codice sui dati reali, controllo dei numeri citati nella tesina rispetto ai dati e ai documenti di progetto, verifica delle fonti e dei riferimenti bibliografici.
- La **responsabilità** del contenuto della tesina, del codice consegnato e di ogni affermazione in essi contenuta.

## 4. Il modello di linguaggio come componente del prodotto

Il prodotto include un assistente in linguaggio naturale, **ONE**, basato sul modello open source **Qwen3.5 4B** (licenza Apache 2.0), preaddestrato e usato senza *fine-tuning*, eseguito in locale con Ollama. Non è uno strumento di supporto alla stesura della tesina: è parte del sistema descritto nel Capitolo 3. Domande, dati e risposte non lasciano il computer.

L'assistente risponde solo entro un elenco chiuso di argomenti e analisi. I numeri vengono calcolati dal codice e non dal modello; ogni numero della risposta è verificato dal codice, e le richieste fuori perimetro ricevono un rifiuto fisso. Il modello non è stato addestrato né adattato con dati del progetto.

## 5. Limiti dichiarati

Un assistente di programmazione e un modello da 4 miliardi di parametri possono produrre errori plausibili. Per questo:
- il codice è stato provato con i dati e la tesina è stata riletta dall'autore;
- le risposte dell'assistente ONE sono accompagnate dai dati usati, perché la verifica automatica controlla i numeri e non le parole.

Matteo Leopizzi
