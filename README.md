# Horae Besançon — Pipeline numérique pour l'étude des livres d'heures bisontins

## Description
Ce projet développe un pipeline numérique pour l'analyse automatisée 
d'un corpus pilote de 14 manuscrits de livres d'heures bisontins du XVe siècle.
Il constitue une preuve de concept destinée à être étendue à un corpus 
de 73 manuscrits dans le cadre d'une recherche postdoctorale.

**Auteure** : Alix Buisseret
**Institution** : Université de Genève 
**Promoteur** : Simon Gabay et Paul Guhennec
**Contexte** : Mini-mémoire, Certificat en humanités numériques, 2025-2026

---

## Question de recherche
Dans quelle mesure les outils numériques actuels permettent-ils de 
reconstituer automatiquement la structure liturgique et le programme 
iconographique d'un corpus de livres d'heures bisontins du XVe siècle, 
et où précisément ces outils atteignent-ils leurs limites face à 
l'expertise du connoisseur ?

---

## Corpus
- **Corpus pilote** : 14 manuscrits actifs (sur 22 identifiés)
- **Manuscrits complets IIIF** (pipeline B) : 8 manuscrits
- **Manuscrits avec enluminures** (pipeline C) : 14 manuscrits
- **Extension possible** : 73 manuscrits (postdoc)

---

## Pipeline

### Étape 1 — Constitution du corpus et collecte des images
Identification des manuscrits bisontins du XVe siècle et récupération 
des images via les APIs IIIF des bibliothèques partenaires ou 
téléchargement manuel quand le IIIF n'est pas disponible.

**Outils** : Python, requests, APIs IIIF (Gallica, ÖNB, SLV, IRHT, Huntington)  
**Input** : URLs de manifestes IIIF  
**Output** : Images téléchargées par manuscrit

### Étape 2 — Transcription HTR (Projet B)
Transcription automatique du texte latin médiéval des manuscrits 
complets via reconnaissance automatique de l'écriture (HTR).

**Outils** : e-Scriptorium, modèles HTR pré-entraînés sur le latin médiéval  
**Input** : Images complètes des manuscrits (8 manuscrits IIIF complets)  
**Output** : Transcriptions textuelles par folio

### Étape 3 — Classification des sections textuelles (Projet B)
Identification et classification automatique des sections liturgiques 
des livres d'heures (Calendrier, Heures de la Vierge, Psaumes 
pénitentiaux, Office des morts, etc.) à partir des transcriptions.

**Outils** : Horae (Simon Gabay)  
**Input** : Transcriptions HTR  
**Output** : Structure textuelle annotée par manuscrit

### Étape 4 — Détection des enluminures (Projet B+C)
Localisation automatique des zones enluminées sur les pages de manuscrits 
pour distinguer texte, décoration et miniatures.

**Outils** : Modèles de détection de layout (dhSegment / LayoutParser)  
**Input** : Images des folios  
**Output** : Coordonnées et crops des enluminures

### Étape 5a — Classification iconographique (Projet C)
Identification automatique des sujets représentés dans les enluminures 
et évaluation critique des outils existants.

**Outils** : CLIP, IconArt, Replica  
**Input** : Images des enluminures (14 manuscrits)  
**Output** : Classifications automatiques + évaluation par l'expert

### Étape 5b — Clustering visuel et connoisseurship computationnel
Regroupement automatique des enluminures par similarité visuelle 
afin d'identifier des proximités formelles entre manuscrits — 
style, composition, traitement des drapés, des visages, des couleurs.
Cette étape constitue une approche computationnelle du connoisseurship :
là où l'expert regroupe des œuvres par reconnaissance stylistique,
l'outil regroupe par distance visuelle dans un espace de features.
La confrontation entre les deux logiques de regroupement est 
l'argument central du projet.

**Outils** : Replica (EPFL), CLIP embeddings + clustering (k-means, UMAP)  
**Input** : Images des enluminures (14 manuscrits)  
**Output** : Clusters visuels, visualisation UMAP, comparaison 
avec attributions expertes

### Étape 6 — Évaluation critique
Confrontation systématique des résultats automatiques avec l'expertise 
en connoisseurship. Identification des limites des outils numériques 
face à l'analyse experte des manuscrits médiévaux.

**Output** : Analyse critique du pipeline et des limites des outils numériques. 

