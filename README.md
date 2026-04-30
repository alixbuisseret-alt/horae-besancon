# horae-besancon
Titre: Classificateur de structure textuelle et localisation des enluminures (B) et Classification iconographique par vision par ordinateur (C)

Description: Peut-on automatiser la structure textelle et la localisation des enluminures dans un manuscrit médiéval et peut-on classifier l'iconographie par vision computationnelle? 

Alix Buisseret, Université de Genève

Pipeline: 
    [1] Manuscrit numérisé (IIIF)
            ↓
    [2] [B1] Transcription HTR (Transkribus)
            ↓
    [3] [B2] Classification des sections textuelles (Horae)
            ↓
    [4] [B3] Détection des régions enluminées (YOLO / layout detection)
            ↓
    [5] [C]  Classification iconographique (CLIP / IconArt / Replica)
            ↓
    [6] Évaluation critique par l'expert (vous)

Découpage détaillé du pipepine: 
     [1] Constitution du corpus image (1-2 semaines)
      Récupérer les manifestes IIIF de vos 22 manuscrits depuis Biblissima. Un script Python simple avec la librairie iiif-prezi ou 
      des requêtes directes aux API suffit. Vous obtenez les URLs de chaque page en haute résolution, téléchargeables
      automatiquement. Simon Gabay a très probablement déjà des scripts pour ça dans l'écosystème Horae.
      [2] Transcription HTR avec Transkribus (2-3 semaines)
      Appliquer un modèle HTR pré-entraîné sur le latin médiéval du XVe siècle. Transkribus propose plusieurs modèles publics
      adaptés, dont certains entraînés précisément sur des livres d'heures. Vous n'entraînez rien from scratch — vous appliquez et
      évaluez. Le résultat est un texte transcrit par page, imparfait mais suffisant pour la classification de sections.
      Point d'attention : la qualité HTR dépend fortement de la résolution des numérisations. Certaines bibliothèques dans votre
      corpus (Melbourne, par exemple) ont des numérisations moins standardisées que la BnF. Il faudra documenter ces disparités —
      c'est déjà un résultat.
      [3] Classification des sections textuelles avec Horae (2-3 semaines)
      C'est là que l'accès à Gabay devient décisif. Horae a été entraîné précisément pour identifier les sections liturgiques des
      livres d'heures en latin. Vous appliquez le modèle sur vos transcriptions et vous obtenez une segmentation automatique : ce
      folio appartient aux Psaumes pénitentiaux, celui-là à l'Office des morts, etc.
      La valeur ajoutée de votre corpus ici est réelle : Horae a été développé et testé principalement sur des manuscrits à usage
      parisien ou romain. Tester ses performances sur un usage bisontin — plus rare, avec des particularités liturgiques régionales —
      est une contribution originale en soi. La question de recherche devient : le modèle Horae généralise-t-il bien à des usages
      liturgiques non parisiens ?
      [4] Détection des régions enluminées (3-4 semaines)
      C'est le pont entre B et C, et l'étape la plus incertaine techniquement. Il s'agit de détecter automatiquement sur chaque page
      numérisée les zones qui contiennent une enluminure, et de les distinguer du texte, des bordures et des initiales décoratives.
      Des approches existent :      
      Modèles de segmentation de layout comme ceux du projet dhSegment (EPFL, compatible avec des documents historiques) ou
      LayoutParser
      Modèles YOLO fine-tunés sur des pages de manuscrits — il en existe quelques-uns dans la littérature, notamment issus des
      compétitions ICDAR
      Annotation manuelle d'un petit jeu d'entraînement sur vos 22 manuscrits puis fine-tuning — faisable mais chronophage
      La question n'est pas seulement où est l'image mais aussi quelle est sa taille relative — grande miniature pleine page vs
      petite miniature vs initiale historiée — ce qui est directement lié à votre problématique de connoisseurship sur le programme
      décoratif.
      [5] Classification iconographique (3-4 semaines)
      Une fois les enluminures détectées et découpées comme patches d'image, vous appliquez les outils de C :
      CLIP : requêtes textuelles en langage naturel ("saint holding a book", "dead body in a shroud", "king praying") sur vos images 
      — sans entraînement, zéro-shot
      IconArt (Gonthier et al.) : modèle entraîné sur ICONCLASS, plus adapté à l'iconographie médiévale mais moins flexible
      Replica (si accessible) : similarité visuelle, utile pour regrouper des enluminures formellement proches entre manuscrits
      L'évaluation critique est le cœur du projet C. Vous comparez systématiquement ce que chaque outil produit avec votre propre
      lecture experte. Les erreurs de la machine sont aussi informatives que ses succès — elles révèlent ce que le connoisseurship
      mobilise que l'IA ne voit pas encore.

Résultats espérés: 
  - Premier test de Horae sur un usage liturgique non parisien — résultat garanti, positif ou négatif
  - Premier pipeline texte+image appliqué à un corpus de livres d'heures bisontins — même incomplet, c'est une démonstration de
  faisabilité documentée
  - Évaluation comparative de CLIP / IconArt / Replica sur l'iconographie des livres d'heures — aucun article ne fait cette
    comparaison sur ce type de corpus précisément
  - Réflexion critique sur ce que le pipeline ne capture pas — c'est votre voix d'expert en connoisseurship, et c'est ce qui fait la
    différence entre un projet technique et un projet en humanités numériques

Outils: 
  - Python
  - Sublime text
  - E-scriptorium
  - Github
  - tableur (Excel)
  - Sur navigateur: Biblissima, COMMA, Horaem Google Clab.
  - Plus tard: YOLO. CLIP, Icon Art et Replica. 
