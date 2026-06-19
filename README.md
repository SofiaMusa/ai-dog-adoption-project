# Sistema Intelligente di Supporto all'Adozione dei Cani

Progetto sviluppato per il corso di **Intelligenza Artificiale**.

Il sistema utilizza dati strutturati, descrizioni testuali e immagini per supportare il processo di adozione dei cani e suggerire gli animali più compatibili con uno specifico profilo adottante.

---

## Dataset

Dataset utilizzato:

* PetFinder Adoption Prediction

Dati utilizzati:

* informazioni strutturate sui cani;
* descrizioni testuali degli annunci;
* immagini associate agli animali.

Analisi limitata ai soli cani.

---

## Struttura del Progetto

```text
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
│   ├── 06_export_rankings.ipynb
│   ├── 07_visual_breed_prediction.ipynb
│   ├── 08_visual_breed_prediction_all_photos.ipynb
│   ├── 09_matching_with_visual_breeds.ipynb
│   └── 10_case_studies_final.ipynb
│
├── docs
│
└── README.md
```

---

## Notebook

| Notebook | Contenuto                                               |
| -------- | ------------------------------------------------------- |
| 01       | Analisi esplorativa dei dati e feature engineering      |
| 02       | Modello Random Forest basato sui dati strutturati       |
| 03       | Analisi delle descrizioni tramite BERT                  |
| 04       | Primo sistema di matching cane–famiglia                 |
| 05       | Esperimenti con diversi profili adottante               |
| 06       | Esportazione dei ranking in CSV                         |
| 07       | Predizione delle razze a partire dalle immagini         |
| 08       | Aggregazione delle predizioni su tutte le foto del cane |
| 09       | Integrazione delle razze stimate nel matching           |
| 10       | Casi studio finali e dimostrazione del sistema          |

---

## Sistema di Matching

Il sistema combina:

* compatibilità strutturata;
* compatibilità di razza;
* compatibilità semantica tramite BERT.

L'output è una classifica personalizzata dei cani più compatibili con il profilo dell'adottante.

---

## Tecnologie Utilizzate

* Python
* Pandas
* NumPy
* Scikit-Learn
* PyTorch
* Transformers
* TorchVision
* Jupyter Notebook

---

## Autore

**Sofia Musa**

Corso di Laurea Magistrale in Informatica per il Management

Alma Mater Studiorum – Università di Bologna

---

## Licenza

MIT
