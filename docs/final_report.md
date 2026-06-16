# Report Tecnico – Sistema Intelligente di Supporto all'Adozione dei Cani

Questo report riassume il progetto sviluppato per il corso di Intelligenza Artificiale.

## Introduzione
L'obiettivo è sviluppare un sistema AI per supportare il processo di adozione dei cani tramite previsione dell'adottabilità e matching cane–famiglia.

## Dataset
Dataset PetFinder Adoption Prediction, filtrato ai soli cani (8132 record).

## EDA e Feature Engineering
Create le feature age_group, description_len, has_description, gender_label, fur_length_label e maturity_size_label.

## Random Forest
Miglior accuracy: 40.93%.
Le feature più importanti sono description_len, Age e PhotoAmt.

## BERT
Le descrizioni sono state trasformate in embedding da 768 dimensioni.
Accuracy ottenuta: 33.07%.

## Matching Cane–Famiglia
Sistema basato su compatibilità strutturata e similarità semantica tramite BERT.

Formula finale:
final_score = 0.7 * structured_score + 0.3 * bert_similarity

## Risultati
Generazione di ranking personalizzati e spiegazioni automatiche delle raccomandazioni.

## Sviluppi Futuri
Modelli multimodali, interfaccia web e validazione con dati reali.
