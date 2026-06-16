# Sistema Intelligente di Supporto all'Adozione dei Cani

Progetto sviluppato per il corso di **Intelligenza Artificiale (81940)**.

L'obiettivo del progetto è realizzare un sistema basato su tecniche di Intelligenza Artificiale in grado di supportare il processo di adozione dei cani. Il sistema combina modelli di Machine Learning, Natural Language Processing e un modulo di matching cane–famiglia per suggerire gli animali più compatibili con le preferenze degli adottanti.

---

## Dataset

Il progetto utilizza il dataset **PetFinder Adoption Prediction**, contenente informazioni relative a migliaia di animali domestici.

L'analisi è stata limitata ai soli cani, ottenendo:

- 8132 cani
- 24 variabili originali
- caratteristiche strutturate (età, sesso, taglia, salute, vaccinazioni, foto, ecc.)
- descrizioni testuali degli annunci di adozione

---

## Struttura del Progetto

```
.
├── data
│   ├── raw
│   ├── processed
│   └── results
│
├── notebooks
│   ├── 01_eda.ipynb
│   ├── 02_baseline_model.ipynb
│   ├── 03_bert_model.ipynb
│   ├── 04_matching_system.ipynb
│   ├── 05_matching_experiments.ipynb
│   └── 06_export_rankings.ipynb
│
├── docs
│   ├── project_description.md
│   ├── modulo_famiglia.pdf
│   └── matching_system.pdf
│
└── README.md
```

---

## Notebook

### 01 - Exploratory Data Analysis

- selezione dei soli cani
- analisi esplorativa dei dati
- gestione dei valori mancanti
- feature engineering

Nuove feature create:

- age_group
- description_len
- has_description
- gender_label
- fur_length_label
- maturity_size_label

---

### 02 - Baseline Model

Implementazione di modelli Random Forest basati sulle caratteristiche strutturate del dataset.

Risultato migliore:

**Accuracy ≈ 40.93%**

Analisi delle feature importance:

- lunghezza della descrizione
- età del cane
- numero di fotografie

risultano le variabili più influenti.

---

### 03 - BERT Model

Analisi delle descrizioni testuali tramite:

**BERT (bert-base-uncased)**

Le descrizioni vengono convertite in embedding numerici da 768 dimensioni e utilizzate per addestrare un classificatore.

Risultato:

**Accuracy ≈ 33.07%**

---

### 04 - Matching System

Prototipo di sistema di raccomandazione cane–famiglia.

Il sistema utilizza:

- preferenze della famiglia
- caratteristiche strutturate del cane
- descrizioni testuali
- similarità semantica tramite BERT

Output:

- score di compatibilità
- ranking dei cani consigliati
- spiegazioni automatiche delle raccomandazioni

---

### 05 - Matching Experiments

Permette di confrontare differenti profili famiglia.

Profili disponibili:

- famiglia con bambini in appartamento
- persona singola attiva
- richiedente over 60
- famiglia esperta in campagna
- prima adozione senza esperienza

---

### 06 - Export Rankings

Genera file CSV contenenti il ranking completo dei cani per uno specifico profilo famiglia.

Per ogni cane vengono salvati:

- structured_score
- bert_similarity
- final_score

---

## Sistema di Matching

Il sistema combina:

### Compatibilità strutturata

Basata su:

- età
- sesso
- taglia
- lunghezza del pelo
- esperienza con i cani
- presenza di bambini
- disponibilità di un giardino
- tempo disponibile

### Compatibilità semantica

Basata sulla similarità tra:

- descrizione del cane ideale inserita dalla famiglia
- descrizione dell'annuncio di adozione

calcolata tramite BERT.

### Score Finale

```
final_score =
0.7 × structured_score +
0.3 × bert_similarity
```

---

## Risultati Principali

| Modello | Accuracy |
|----------|----------|
| Random Forest | 40.93% |
| BERT | 33.07% |

Il modello Random Forest ha ottenuto le migliori prestazioni nella previsione della velocità di adozione.

BERT è stato utilizzato principalmente per il sistema di matching e per l'analisi semantica delle descrizioni.

---

## Tecnologie Utilizzate

- Python
- Pandas
- NumPy
- Scikit-Learn
- Transformers (Hugging Face)
- PyTorch
- Jupyter Notebook

---

## Autore

**Sofia Musa**

Corso di Laurea Magistrale in Informatica per il Management

Alma Mater Studiorum – Università di Bologna

---

## Licenza

MIT