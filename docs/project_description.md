# Sistema intelligente di supporto all'adozione dei cani

## Descrizione del progetto

L'obiettivo del progetto è sviluppare un sistema intelligente in grado di supportare il processo di adozione dei cani attraverso l'utilizzo di tecniche di Intelligenza Artificiale. Il sistema analizza le caratteristiche degli animali disponibili per l'adozione e stima la probabilità con cui un cane verrà adottato, fornendo informazioni utili a rifugi, associazioni e potenziali adottanti.

Il progetto si basa sul dataset **PetFinder Adoption Prediction**, contenente informazioni relative a migliaia di animali domestici. In questo lavoro l'analisi è stata limitata ai soli cani, utilizzando sia dati strutturati (età, sesso, taglia, stato di salute, vaccinazioni, numero di fotografie, ecc.) sia descrizioni testuali degli annunci di adozione.

## Obiettivi

Gli obiettivi principali del progetto sono:

* analizzare le caratteristiche dei cani presenti nel dataset;
* individuare i fattori che influenzano maggiormente la velocità di adozione;
* prevedere la classe di adozione di un cane tramite modelli di Machine Learning;
* sfruttare tecniche di Natural Language Processing per analizzare le descrizioni testuali degli annunci;
* confrontare approcci differenti e valutarne le prestazioni;
* gettare le basi per un futuro sistema di raccomandazione in grado di suggerire i cani più adatti a una famiglia.

## Dataset e Preprocessing

Il dataset originale contiene informazioni relative sia a cani sia a gatti. La prima fase del progetto ha previsto:

* selezione dei soli cani;
* analisi esplorativa dei dati (EDA);
* gestione dei valori mancanti;
* creazione di nuove feature derivate, tra cui:

  * fascia di età del cane;
  * lunghezza della descrizione;
  * presenza o assenza della descrizione;
  * etichette leggibili per genere, lunghezza del pelo e taglia.

Sono inoltre state analizzate le relazioni tra le diverse caratteristiche e la velocità di adozione.

## Modelli sviluppati

### Random Forest

È stato sviluppato un modello Random Forest basato esclusivamente sulle caratteristiche strutturate del dataset. L'analisi delle feature importance ha evidenziato che la lunghezza della descrizione, l'età del cane e il numero di fotografie rappresentano alcune delle informazioni più rilevanti per la previsione.

### Modello NLP basato su BERT

Per sfruttare le informazioni contenute nelle descrizioni testuali è stato utilizzato il modello pre-addestrato **BERT (Bidirectional Encoder Representations from Transformers)**. Le descrizioni sono state trasformate in embedding numerici e utilizzate per addestrare un classificatore dedicato.

### Confronto dei modelli

Le prestazioni dei modelli sono state confrontate per valutare il contributo delle informazioni strutturate e testuali alla previsione della velocità di adozione.

## Aspetti di Intelligenza Artificiale

Il progetto integra diversi ambiti dell'Intelligenza Artificiale:

* Machine Learning supervisionato per la previsione della velocità di adozione;
* Natural Language Processing (NLP) per l'analisi automatica delle descrizioni testuali;
* Feature Engineering per la costruzione di nuove variabili informative;
* Analisi comparativa di modelli differenti.

## Innovatività

La maggior parte dei portali di adozione consente solamente di consultare gli annunci e applicare semplici filtri di ricerca. Il sistema proposto mira invece a sfruttare tecniche di Intelligenza Artificiale per comprendere quali caratteristiche rendono un cane più facilmente adottabile e per supportare il processo decisionale.

L'approccio combina informazioni strutturate e descrizioni testuali, permettendo di analizzare non solo le caratteristiche fisiche dell'animale, ma anche il modo in cui viene presentato nell'annuncio. I risultati ottenuti potranno costituire la base per futuri sistemi di raccomandazione personalizzata capaci di migliorare l'incontro tra cani e famiglie adottanti.
