# Journal de bord — Horae Besançon

## 2026-04-30 — Séance 1
- Constitution du corpus pilote : 22 manuscrits
- Vérification IIIF : ~10-12 manuscrits accessibles
- Installation Python 3.14 sur Windows
- Création du repo GitHub horae-besancon

## 2026-04-30 — Séance 2
- Morgan M. 293 et M. 287: accès partiel via ICA (folios peints seulement) - MS M.293 : 19 peintures (uniquement) ✅ ; MS M.287 : 31 peintures (uniquement) ✅
- Châlons-en-Champagne, Bibliothèque municipale, ms. 1329: seulement deux iages téléchargées à la main. 
- Notebook sauvegardé sur GitHub dans notebooks/ ✅
- Vienne ÖNB Cod. 1881 : HMML bloque téléchargement auto
  → 12 images récupérées manuellement
  → Images directes supprimées du serveur HMML
  → Pas de numérisation ÖNB disponible
- New Zealand, Alexander Turnbull Library — images:
  Système DPS (Ex Libris) — pas de IIIF, pas d'URL image directe
  12 miniatures téléchargées manuellement
  Même situation que Vienne HMML
- J'ai laissé de côté tous les manuscrits qui n'ont pas d'images du tout et pas de lien en ligne dans la liste des 22 manuscrits, comme ceux qui sont en collection privée. 
  ### pour prochaine séance: 
  - finaliser le téléchargement: New York, Public Library, ms. 41 	Des IIIF, mais seulement quelques peintures (6) enregistrées via Python, voir dossier Cours/hum num
  - ajouter le iiif sur le tableur: Vesoul, Bibliothèque municipal, ms. 110.
  - check si je ne peux pas trouver quelque chose pour Melbourne. 
  - montrer à claude ce que j'ai pour le corpus et lui demander si ca fera l'affaire ou si je dois trouver d'autres manuscrits plus complets avec iiif pour que ca fasse plus
    de sens pour la partie textuelle et pas uniquement icono. Et si je dois trouver d'autres liens, si c'est ok pour le projet B e C de ne pas utiliser les mêmes manuscrits
    forcément.
    
## 2026-05-1 — Séance 3  
  - téléchargée New York, Public Library, ms. 41 à la main seulement quelques peintures dispo sur le site.
  - Melbourne: j'ai trouvé le manifest entier, et téléchargé via Python
    ### Etape 1 ✅
    Corpus:
    1. Projet B (HTR + structure textuelle) : 8 manuscrits complets IIIF
    2. Projet C (iconographie) : 14 manuscrits avec enluminures (dont 8 manuscrits complets et 6 manuscurits partiels, dont uniquement les peintures sont numérisées, que j'ai
    téléchargé à la main ou avec python)
    3. Corpus total de référence : 14 manuscrits actifs.
    TARGET: Démontrer le pipeline, évaluer les outils HTR et iconographie. Démontrer que le pipeline fonctionne sur 14 manuscrits, identifier les limites, et proposer une
    extension à 73 — c'est exactement la structure d'un article de humanités numériques convaincant.

    ### à faire: Acra Initiale indispo, ajouter sur le Excel plus tard...
    
  ## 2026-05-4 — Séance 4
  - J'attaque étape 2: état de l'art pour le segmentation des pages.
    - outils de segm: pixel classification [Capobianco et al., 2018], as in Kraken [Kiessling, 2019]; object detection with tools like YOLO [Jiang et al., 2022] used by Prasad et al. [2020] for table detection or YALTAi [Clérice, 2023] for page segmentation; multi-modal methods that perform jointly the segmentation and the transcription process [Liu et al., 2019, Xu et al., 2021]).
    - voc: Horae projec (paleo et DH dirigé par Dominique Stutzmann; Hazem et al, 2020); Voculaire codicologique (codico tradi; Muzerelle 1985 - sur Codicologia et en version SKOS, voir Geoffroy et al 2021)); SegmOnto (voc. pour segmentation, utile pour tout type d'écriture y compris scrolls, avantage: "GraphicZone* pour les illustrations ou ornementations; Gabay et al. 2024)
    - Proposition: La segmentation du layout suit le vocabulaire contrôlé SegmOnto (Gabay et al. 2024), implémenté via YALTAi/LaDaS (Clérice et al. 2023, 2024) pour la détection automatique des zones textuelles et décoratives. La classification des sections liturgiques s'appuie ensuite sur le projet Horae (Hazem et al. 2020), spécifiquement développé pour les livres d'heures médiévaux.

    ### Conversation avec Paul Guhennec - Retour à étape 1, élargissement du corpus à tous les manuscrits (collecte d'un max de données) + pour ce qui est de l'analyse des images: voir ce que Iconclass donne sur mes images (step1), puis en fonction ajouter des niveaux d'analyse (step2) et projeter différents niveaux de cluster (step3).
  
     ### à faire: Acra Initiale indispo, ajouter sur le Excel plus tard...





