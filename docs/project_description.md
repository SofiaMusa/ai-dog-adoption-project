# Sistema intelligente di supporto all'adozione dei cani

## Descrizione del progetto

L'obiettivo del progetto è sviluppare un sistema intelligente di supporto alle adozioni canine basato su tecniche di Intelligenza Artificiale. Il sistema è progettato per assistere rifugi, associazioni e potenziali adottanti sia nella valutazione dell'adottabilità dei cani sia nell'individuazione degli animali più compatibili con le caratteristiche e le preferenze di una specifica famiglia.

Il progetto utilizza il dataset **PetFinder Adoption Prediction**, contenente informazioni relative a migliaia di animali domestici. In questo lavoro l'analisi è stata limitata ai soli cani e ha sfruttato sia dati strutturati (età, sesso, taglia, stato di salute, vaccinazioni, numero di fotografie, ecc.) sia descrizioni testuali degli annunci di adozione.

Oltre alla previsione della velocità di adozione, il progetto propone un prototipo di sistema di matching cane-famiglia basato sulla combinazione di regole di compatibilità e analisi semantica delle descrizioni testuali.

## Obiettivi

Gli obiettivi principali del progetto sono:

* analizzare le caratteristiche dei cani presenti nel dataset;
* individuare i fattori che influenzano maggiormente la velocità di adozione;
* prevedere la classe di adozione di un cane tramite modelli di Machine Learning;
* sfruttare tecniche di Natural Language Processing per analizzare le descrizioni testuali degli annunci;
* confrontare approcci differenti e valutarne le prestazioni;
* progettare un sistema di matching tra cane e famiglia adottante;
* generare una classifica dei cani maggiormente compatibili con le preferenze espresse dagli adottanti.

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

È stato sviluppato un modello Random Forest basato esclusivamente sulle caratteristiche strutturate del dataset. Il modello migliore ha raggiunto un'accuracy di circa **40.93%**.

L'analisi delle feature importance ha evidenziato che la lunghezza della descrizione, l'età del cane e il numero di fotografie rappresentano alcune delle informazioni più rilevanti per la previsione.

### Modello NLP basato su BERT

Per sfruttare le informazioni contenute nelle descrizioni testuali è stato utilizzato il modello pre-addestrato **BERT (Bidirectional Encoder Representations from Transformers)**. Le descrizioni sono state trasformate in embedding numerici e utilizzate per addestrare un classificatore dedicato.

Il modello basato esclusivamente sulle informazioni testuali ha ottenuto un'accuracy di circa **33.07%**.

### Confronto dei modelli

Le prestazioni dei modelli sono state confrontate per valutare il contributo delle informazioni strutturate e testuali alla previsione della velocità di adozione.

I risultati mostrano che le caratteristiche strutturate rappresentano la fonte informativa più efficace, mentre le descrizioni testuali forniscono informazioni complementari utili a comprendere il profilo dell'animale.

## Sistema di Matching Cane–Famiglia

Per avvicinare il progetto a un reale sistema di supporto alle adozioni è stato progettato un modulo dedicato agli adottanti.

La famiglia compila un questionario contenente informazioni riguardanti:

* età del richiedente;
* presenza di bambini;
* esperienza con i cani;
* tipologia di abitazione;
* disponibilità di un giardino;
* preferenze relative a sesso, età, taglia e lunghezza del pelo del cane;
* tempo disponibile per la cura dell'animale;
* descrizione testuale del cane ideale.

Il sistema calcola quindi uno score di compatibilità utilizzando:

* regole di matching tra preferenze della famiglia e caratteristiche del cane;
* similarità semantica tra la descrizione del cane ideale e la descrizione dell'annuncio, calcolata tramite BERT.

I cani vengono infine ordinati in una classifica che evidenzia gli animali maggiormente compatibili con il profilo dell'adottante.

## Aspetti di Intelligenza Artificiale

Il progetto integra diversi ambiti dell'Intelligenza Artificiale:

* Machine Learning supervisionato per la previsione della velocità di adozione;
* Natural Language Processing (NLP) per l'analisi automatica delle descrizioni testuali;
* Feature Engineering per la costruzione di nuove variabili informative;
* Recommendation Systems per la generazione di classifiche personalizzate;
* Analisi comparativa di modelli differenti.

## Innovatività

La maggior parte dei portali di adozione consente esclusivamente di consultare gli annunci e applicare semplici filtri di ricerca. Il sistema proposto mira invece a supportare attivamente il processo decisionale sfruttando tecniche di Intelligenza Artificiale.

L'approccio combina dati strutturati, descrizioni testuali e informazioni fornite dagli adottanti per costruire un sistema di matching cane-famiglia. In questo modo il progetto non si limita a stimare la probabilità di adozione di un animale, ma fornisce uno strumento in grado di suggerire gli abbinamenti potenzialmente più adatti, contribuendo a rendere le adozioni più consapevoli e sostenibili nel lungo periodo.
