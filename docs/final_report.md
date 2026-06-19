# Report Tecnico – Sistema Intelligente di Supporto all'Adozione dei Cani

## Introduzione

L'obiettivo del progetto è sviluppare un sistema intelligente di supporto alle adozioni canine basato su tecniche di Intelligenza Artificiale.

Il punto di partenza è stato lo studio dei fattori che influenzano il successo delle adozioni. Il dataset PetFinder contiene infatti una variabile chiamata `AdoptionSpeed`, che indica quanto rapidamente un animale è stato adottato. Questa informazione è stata  utilizzata come riferimento per comprendere quali caratteristiche dei cani risultino maggiormente associate ad adozioni rapide.

Le conoscenze ottenute da questa analisi sono state successivamente utilizzate per progettare un sistema di matching cane–famiglia, in cui le caratteristiche ritenute più importanti ricevono un peso maggiore nel calcolo della compatibilità.

Per raggiungere questo obiettivo sono state integrate tecniche di Machine Learning, Natural Language Processing (NLP), Computer Vision e Recommendation Systems.

---

## Motivazione del Problema

Ogni anno rifugi e associazioni gestiscono un elevato numero di richieste di adozione. Nella maggior parte dei casi gli adottanti possono consultare gli annunci disponibili e applicare semplici filtri basati su età, sesso o taglia del cane.

Tuttavia il processo di selezione dell'animale più adatto richiede spesso una valutazione più approfondita che tenga conto sia delle caratteristiche del cane sia delle esigenze della famiglia.

L'obiettivo del progetto è fornire uno strumento di supporto decisionale che aiuti a individuare gli abbinamenti più compatibili, riducendo il rischio di adozioni poco adatte e favorendo una maggiore soddisfazione sia per l'animale sia per l'adottante.

---

## Obiettivi del Progetto

Gli obiettivi principali del progetto sono:

* analizzare le caratteristiche associate alla velocità di adozione dei cani;
* individuare quali fattori risultano maggiormente rilevanti nelle adozioni storiche;
* utilizzare tecniche di Machine Learning per studiare il comportamento delle adozioni;
* sfruttare il Natural Language Processing per analizzare le descrizioni degli annunci;
* utilizzare la Computer Vision per estrarre informazioni aggiuntive dalle immagini;
* progettare un sistema di matching cane–famiglia basato su caratteristiche strutturate, testo e immagini;
* generare classifiche personalizzate dei cani maggiormente compatibili con gli adottanti.

---

## Aspetti di Intelligenza Artificiale

Il progetto integra diversi ambiti dell'Intelligenza Artificiale:

### Machine Learning

Utilizzato per analizzare la relazione tra le caratteristiche dei cani e la velocità di adozione tramite modelli Random Forest.

### Natural Language Processing

Utilizzato attraverso BERT per rappresentare semanticamente le descrizioni degli annunci e confrontarle con la descrizione del cane ideale fornita dagli adottanti.

### Computer Vision

Utilizzata tramite ResNet50 per stimare le possibili razze presenti nei cani classificati come Mixed Breed e valorizzarne le caratteristiche all'interno del sistema di matching.

### Recommendation Systems

Utilizzati per generare ranking personalizzati dei cani in base alle preferenze e alle caratteristiche degli adottanti.

---

## Innovatività

La maggior parte dei portali dedicati alle adozioni consente agli utenti di consultare gli annunci disponibili e applicare alcuni filtri di ricerca, ad esempio età, sesso, taglia o razza del cane.

In questi sistemi il ruolo dell'adottante è generalmente limitato alla selezione di alcune caratteristiche desiderate, mentre il processo di valutazione della compatibilità tra cane e famiglia viene svolto successivamente dagli operatori dei rifugi o delle associazioni.

Il sistema sviluppato in questo progetto propone invece un approccio più attivo e personalizzato.

L'adottante non si limita a filtrare i cani disponibili, ma descrive anche le proprie caratteristiche e il proprio contesto familiare, fornendo informazioni quali esperienza con i cani, presenza di bambini, disponibilità di tempo, tipologia di abitazione e presenza di un giardino.

Il sistema utilizza quindi sia le caratteristiche del cane sia quelle della famiglia per calcolare un punteggio di compatibilità e generare una classifica personalizzata dei candidati più adatti.

In particolare:

utilizza dati storici sulle adozioni per comprendere quali caratteristiche risultano maggiormente associate al successo delle adozioni;
integra dati strutturati, descrizioni testuali e immagini;
utilizza le immagini per valorizzare i cani meticci e renderli maggiormente individuabili durante la ricerca;
applica regole ispirate ai processi di adozione reali per evitare raccomandazioni poco realistiche;
genera ranking personalizzati e spiegazioni delle raccomandazioni.

L'obiettivo non è sostituire il lavoro degli operatori, ma fornire uno strumento di supporto che possa guidare adottanti e associazioni nella fase iniziale di selezione, evidenziando in modo automatico gli abbinamenti potenzialmente più compatibili.

---

## Dataset

Il progetto utilizza il dataset **PetFinder Adoption Prediction**, contenente informazioni relative a migliaia di animali domestici.

L'analisi è stata limitata ai soli cani, ottenendo un dataset finale composto da circa **8132 record**.

Le informazioni disponibili comprendono:

* età;
* sesso;
* taglia;
* lunghezza del pelo;
* stato di salute;
* vaccinazioni;
* numero di fotografie;
* descrizioni testuali degli annunci;
* immagini associate ai cani.

---

## Analisi Esplorativa e Feature Engineering

La prima fase del progetto ha previsto una Exploratory Data Analysis (EDA) finalizzata alla comprensione delle caratteristiche del dataset.

Durante questa fase sono state create diverse feature derivate:

* `age_group`
* `description_len`
* `has_description`
* `gender_label`
* `fur_length_label`
* `maturity_size_label`

L'analisi ha evidenziato che fattori come età del cane, presenza di fotografie e qualità delle descrizioni sembrano influenzare significativamente la velocità di adozione.

---

## Modello Baseline – Random Forest

Come primo approccio è stato sviluppato un modello di classificazione basato su Random Forest utilizzando esclusivamente le caratteristiche strutturate del dataset.

L'obiettivo non era solamente prevedere la classe `AdoptionSpeed`, ma soprattutto comprendere quali fattori risultassero maggiormente collegati alla velocità di adozione.

Il modello migliore ha raggiunto un'accuracy di circa:

**40.9%**

L'analisi delle feature importance ha evidenziato che le variabili più rilevanti sono:

* lunghezza della descrizione;
* età del cane;
* numero di fotografie;
* taglia;
* stato di sterilizzazione.

Questi risultati sono stati particolarmente importanti perché hanno fornito indicazioni utili per la progettazione del sistema di matching. Le caratteristiche che si sono dimostrate più influenti nelle adozioni storiche sono infatti diventate elementi centrali nella valutazione della compatibilità tra cane e famiglia.

---

## Modello NLP – BERT

Per sfruttare il contenuto informativo delle descrizioni testuali è stato utilizzato il modello pre-addestrato:

**BERT (bert-base-uncased)**

Le descrizioni sono state trasformate in embedding numerici da 768 dimensioni e successivamente utilizzate per addestrare un classificatore.

Accuracy ottenuta:

**33.1%**

Pur ottenendo prestazioni inferiori rispetto al modello Random Forest, l'analisi ha mostrato che le descrizioni contengono informazioni utili sul carattere e sul profilo dei cani.

Per questo motivo gli embedding generati da BERT non sono stati utilizzati soltanto per l'analisi predittiva, ma sono stati successivamente integrati nel sistema di matching per confrontare semanticamente il cane ideale descritto dall'adottante con i cani presenti nel dataset.

---

## Computer Vision e Predizione delle Razze

Una delle estensioni più importanti del progetto ha riguardato l'utilizzo delle immagini dei cani.

Nel dataset molti animali sono classificati semplicemente come **Mixed Breed**, senza informazioni dettagliate sulle razze presenti nell'incrocio. Questo limita la possibilità di individuare cani che potrebbero possedere caratteristiche tipiche di razze particolarmente ricercate dagli adottanti.

Per affrontare questo problema è stato utilizzato un modello **ResNet50** pre-addestrato in grado di riconoscere numerose razze canine a partire dalle fotografie.

Per ogni immagine vengono generate:

* le tre razze più probabili;
* le relative probabilità.

Successivamente le predizioni ottenute dalle diverse fotografie dello stesso cane vengono aggregate per ottenere una stima finale delle razze visivamente più presenti nell'animale.

L'obiettivo non è sostituire le informazioni ufficiali del dataset, ma arricchirle. Un cane registrato come Mixed Breed potrebbe infatti mostrare caratteristiche molto simili a quelle di razze come Labrador Retriever, Golden Retriever o Husky.

Questa informazione viene utilizzata per aumentare la visibilità dei cani meticci. Se un adottante esprime una preferenza per una determinata razza, è plausibile che stia cercando alcune caratteristiche fisiche o comportamentali associate a quella razza. Anche un incrocio può possedere tali caratteristiche e risultare quindi compatibile con le aspettative dell'adottante.

Le razze stimate dalle immagini vengono pertanto utilizzate come informazione aggiuntiva nel sistema di matching, con un peso inferiore rispetto alle razze ufficialmente presenti nel dataset.

---

## Sistema di Matching Cane–Famiglia

La componente principale del progetto è rappresentata dal sistema di raccomandazione cane–famiglia.

Il sistema non è stato progettato indipendentemente dall'analisi precedente, ma sfrutta le conoscenze ottenute studiando i fattori associati al successo delle adozioni.

L'adottante compila un profilo contenente:

* età;
* esperienza con i cani;
* presenza di bambini;
* tipologia di abitazione;
* disponibilità di giardino;
* tempo disponibile;
* preferenze relative a sesso, età, taglia e pelo;
* eventuali razze preferite;
* descrizione testuale del cane ideale.

Il sistema confronta queste informazioni con le caratteristiche dei cani presenti nel dataset e genera una classifica personalizzata.

Particolare attenzione è stata data alle caratteristiche che, durante l'analisi di `AdoptionSpeed`, si sono dimostrate maggiormente associate alle adozioni rapide. In questo modo il sistema non suggerisce semplicemente cani compatibili con le preferenze espresse, ma cerca di proporre abbinamenti che risultino realistici e sostenibili nel lungo periodo.

---

## Compatibilità Strutturata

La compatibilità strutturata considera:

* sesso;
* fascia di età;
* taglia;
* lunghezza del pelo;
* esperienza dell'adottante;
* presenza di bambini;
* disponibilità di giardino;
* tempo disponibile;
* preferenze sulle razze.

Oltre alle semplici preferenze sono state introdotte regole ispirate ai criteri normalmente utilizzati nei processi di adozione reali.

Ad esempio:

* cani di taglia extra-large non vengono consigliati a famiglie prive di giardino;
* cani di taglia extra-large non vengono consigliati ad adottanti senza esperienza;
* gli adottanti anziani vengono orientati preferibilmente verso cani adulti o senior piuttosto che verso cuccioli molto impegnativi;
* la disponibilità di tempo influenza la compatibilità con cani particolarmente giovani o energici;
* le preferenze sulle razze influenzano il ranking, ma non escludono automaticamente cani compatibili appartenenti ad altre razze.

Queste regole consentono di evitare raccomandazioni poco realistiche e migliorano la qualità complessiva del matching.

---

## Compatibilità Semantica

La compatibilità semantica viene calcolata confrontando:

* la descrizione del cane ideale inserita dall'adottante;
* la descrizione dell'annuncio del cane.

Per effettuare questo confronto vengono utilizzati gli embedding generati da BERT e la similarità coseno.

---

## Calcolo dello Score Finale

Il punteggio finale combina la componente strutturata e quella semantica:

```text
final_score =
0.7 × structured_score +
0.3 × bert_similarity
```

Questo approccio permette di bilanciare le preferenze esplicite dell'adottante con le informazioni contenute nelle descrizioni testuali.

---

## Risultati

Il sistema sviluppato è in grado di:

* analizzare le caratteristiche associate alla velocità di adozione;
* individuare i fattori più rilevanti per le adozioni;
* integrare informazioni strutturate, testuali e visive;
* generare ranking personalizzati dei cani;
* fornire spiegazioni delle raccomandazioni;
* supportare differenti profili di adottanti tramite casi studio simulati.

L'analisi ha mostrato che le caratteristiche strutturate rappresentano la fonte informativa più importante per comprendere il comportamento delle adozioni, mentre descrizioni e immagini forniscono informazioni complementari utili per personalizzare il matching.

---

## Conclusioni

Il progetto dimostra come sia possibile utilizzare dati storici sulle adozioni non soltanto per costruire modelli predittivi, ma anche per progettare sistemi di raccomandazione più consapevoli.

L'analisi della variabile `AdoptionSpeed` ha permesso di identificare quali caratteristiche risultano maggiormente associate al successo delle adozioni. Queste informazioni sono state successivamente incorporate nel sistema di matching cane–famiglia, creando un collegamento diretto tra la fase di analisi dei dati e la fase di raccomandazione.

Un ulteriore contributo del progetto è rappresentato dall'integrazione delle immagini. Attraverso la stima delle razze visivamente presenti nei cani classificati come Mixed Breed, il sistema riesce a valorizzare animali che altrimenti risulterebbero difficili da individuare tramite semplici filtri basati sulla razza. Questo permette di aumentare la visibilità dei meticci e di proporli ad adottanti che potrebbero essere interessati alle caratteristiche tipiche delle razze presenti nei loro incroci.

L'approccio sviluppato combina:

* Machine Learning supervisionato;
* Natural Language Processing;
* Computer Vision;
* Recommendation Systems.

Il risultato finale è un sistema di supporto decisionale che integra dati strutturati, testo e immagini per suggerire gli abbinamenti più compatibili tra cane e famiglia adottante.

---

## Sviluppi Futuri

Possibili estensioni future includono:

* sviluppo di una web application per l'utilizzo del sistema da parte di rifugi, associazioni e potenziali adottanti;
* raccolta di dati reali sulle adozioni per validare empiricamente il sistema e valutare l'efficacia delle raccomandazioni prodotte;
* collaborazione con educatori e comportamentalisti cinofili per integrare informazioni più approfondite sul comportamento dei cani e rendere il matching maggiormente aderente alle procedure adottate nelle adozioni reali.
