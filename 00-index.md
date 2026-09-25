# Programme ML Engineer — Vision médicale & ophtalmologie

> Sommaire du cours. Ce fichier est à la racine du dossier `ML-Engineer/`.
> Il est **fixe** : la progression et les statuts se suivent dans `carnet-de-bord.md`.

**Objectif** : devenir ML Engineer en 13 mois (octobre 2026 → octobre 2027), capable d'entraîner, d'évaluer, d'adapter et de mettre en production des modèles, avec une spécialité en **vision par ordinateur médicale appliquée à l'ophtalmologie** (dépistage de maladies de l'œil à partir d'images de fond d'œil et d'OCT).

**Niveau de départ** : débutant en Python, en maths et en ML. Chaque notion est reprise depuis la base, puis approfondie jusqu'au fonctionnement interne (« sous le capot »).

**Rythme** : 3 h par jour, au moins 5 séances par semaine. Règle des 70 % de pratique et 30 % de théorie.

---

## Comment utiliser ce dossier

1. Je t'envoie le fichier du cours dans le chat.
2. Tu le places dans le dossier de sa phase, sous le nom indiqué dans ce sommaire.
3. Tu étudies le cours et tu fais les exercices (sur papier ou dans ton éditeur).
4. Tu reviens dans le chat. On fait le **récap actif**, la **correction** et le **quiz**.
5. Tu reçois le corrigé (`-corrige.md`) après tes tentatives.
6. Module validé à **80 % au quiz**. En dessous, on retravaille avant d'avancer.
7. Je t'envoie le `carnet-de-bord.md` mis à jour : il remplace l'ancien.

**Structure d'un cours**
1. Objectifs et prérequis
2. Cours : définition, intuition, exemples résolus pas à pas
3. Sous le capot : comment ça marche vraiment
4. Lien avec le ML (et avec l'ophtalmologie quand c'est pertinent)
5. Exercices gradués : échauffement → application → problème
6. Ressources pour approfondir : documentation officielle, lectures, vidéos
7. Devoir pour la séance suivante

**Nommage des fichiers**
- Cours : `NN-nom-du-module.md`
- Corrigé : `NN-nom-du-module-corrige.md`
- Tes réponses : `NN-nom-du-module-reponses.md`

**Règles de la classe**
- Français, termes techniques en anglais.
- Blocage : indices d'abord, solution complète après deux vraies tentatives.
- Devoirs faits avant la séance suivante, sinon pas de nouveau cours.
- Pas de « j'ai compris » sans preuve : réexpliquer avec ses mots ou recoder de mémoire.
- La documentation officielle est la référence. Apprendre à la lire fait partie du programme.

**Nouvelle conversation ?** Joins `00-index.md` et `carnet-de-bord.md` dès ton premier message.

**Lien cassé ?** Signale-le : je te donne la nouvelle adresse.

---

## Structure du dossier

```
ML-Engineer/
├── 00-index.md
├── carnet-de-bord.md
├── phase-0-python/
├── phase-1-fondations/
├── phase-2-deep-learning-vision/
├── phase-3-ophtalmologie/
└── phase-4-production/
```

---

## Ressources transversales (tout le programme)

- [Documentation officielle de Python (en français)](https://docs.python.org/fr/3/) : la référence absolue
- [Python Tutor](https://pythontutor.com/) : visualise l'exécution du code ligne par ligne, idéal pour comprendre les références et la mémoire
- [Pro Git (en français)](https://git-scm.com/book/fr/v2) : le livre officiel de Git
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/) (Jake VanderPlas) : NumPy, pandas, matplotlib, scikit-learn, gratuit en ligne
- [Mathematics for Machine Learning](https://mml-book.github.io/) (Deisenroth, Faisal, Ong) : gratuit en PDF
- [Dive into Deep Learning](https://d2l.ai/) : livre interactif avec code PyTorch
- *Hands-On Machine Learning* (Aurélien Géron) et [ses notebooks](https://github.com/ageron/handson-ml3)

---

## Phase 0 — Python en profondeur (oct. 2026, ≈ 4 semaines)

Dossier : `phase-0-python/`

| N° | Module | Fichier |
|----|--------|---------|
| 00 | Test de diagnostic (maths et Python) | `00-diagnostic.md` |
| 01 | Environnement de travail : Python, venv, pip, éditeur, Jupyter, Git (Parrot OS) | `01-environnement.md` |
| 02 | Types, variables et modèle objet : tout est objet, références, mutabilité | `02-types-modele-objet.md` |
| 03 | Contrôle du flux et fonctions : portée, arguments, `*args`, `**kwargs` | `03-controle-fonctions.md` |
| 04 | Structures de données : list, tuple, dict, set, compréhensions, complexité | `04-structures-donnees.md` |
| 05 | Chaînes, fichiers, exceptions et context managers | `05-fichiers-exceptions.md` |
| 06 | Modules, packages, imports et bibliothèque standard | `06-modules-stdlib.md` |
| 07 | Programmation orientée objet : classes, méthodes spéciales, héritage, dataclasses | `07-poo.md` |
| 08 | Python avancé : itérateurs, générateurs, décorateurs, type hints | `08-python-avance.md` |
| 09 | Code professionnel : PEP 8, tests avec pytest, debugging, logging | `09-code-pro.md` |
| 10 | **Projet de phase** : un outil en ligne de commande complet et testé | `10-projet-phase-0.md` |

### Ressources par module

- **01** — [venv](https://docs.python.org/fr/3/library/venv.html) · [Installer des paquets](https://packaging.python.org/fr/latest/tutorials/installing-packages/) · [Jupyter](https://docs.jupyter.org/) · [Python dans VS Code](https://code.visualstudio.com/docs/python/python-tutorial) · [Pro Git, chapitres 1 à 3](https://git-scm.com/book/fr/v2)
- **02** — [Tutoriel officiel, introduction](https://docs.python.org/fr/3/tutorial/introduction.html) · [Types natifs](https://docs.python.org/fr/3/library/stdtypes.html) · [Modèle de données](https://docs.python.org/fr/3/reference/datamodel.html)
- **03** — [Contrôle du flux et fonctions](https://docs.python.org/fr/3/tutorial/controlflow.html) · [Portée et espaces de noms](https://docs.python.org/fr/3/tutorial/classes.html#python-scopes-and-namespaces)
- **04** — [Structures de données](https://docs.python.org/fr/3/tutorial/datastructures.html) · [Complexité des opérations](https://wiki.python.org/moin/TimeComplexity) · [collections](https://docs.python.org/fr/3/library/collections.html)
- **05** — [Entrées et sorties](https://docs.python.org/fr/3/tutorial/inputoutput.html) · [Erreurs et exceptions](https://docs.python.org/fr/3/tutorial/errors.html) · [pathlib](https://docs.python.org/fr/3/library/pathlib.html) · [Instruction with](https://docs.python.org/fr/3/reference/compound_stmts.html#the-with-statement)
- **06** — [Modules](https://docs.python.org/fr/3/tutorial/modules.html) · [Système d'import](https://docs.python.org/fr/3/reference/import.html) · [itertools](https://docs.python.org/fr/3/library/itertools.html) · [json](https://docs.python.org/fr/3/library/json.html)
- **07** — [Classes](https://docs.python.org/fr/3/tutorial/classes.html) · [Méthodes spéciales](https://docs.python.org/fr/3/reference/datamodel.html#special-method-names) · [dataclasses](https://docs.python.org/fr/3/library/dataclasses.html)
- **08** — [Programmation fonctionnelle (HOWTO)](https://docs.python.org/fr/3/howto/functional.html) · [typing](https://docs.python.org/fr/3/library/typing.html) · [Glossaire : décorateur, générateur](https://docs.python.org/fr/3/glossary.html)
- **09** — [PEP 8](https://peps.python.org/pep-0008/) · [pytest](https://docs.pytest.org/) · [pdb](https://docs.python.org/fr/3/library/pdb.html) · [Logging (HOWTO)](https://docs.python.org/fr/3/howto/logging.html)
- **Pour aller plus loin** — *Fluent Python* (Luciano Ramalho), le livre de référence pour maîtriser Python en profondeur

---

## Phase 1 — Fondations (nov. 2026 → janv. 2027)

Dossier : `phase-1-fondations/`

| N° | Module | Fichier |
|----|--------|---------|
| 01 | Algèbre linéaire pour le ML (vecteurs, matrices, produit matriciel) | `01-algebre-lineaire.md` |
| 02 | Calcul différentiel, gradient et descente de gradient | `02-gradient.md` |
| 03 | Probabilités (variables aléatoires, lois, espérance, variance) | `03-probabilites.md` |
| 04 | Statistiques et maximum de vraisemblance | `04-statistiques.md` |
| 05 | Python scientifique : NumPy et vectorisation | `05-numpy.md` |
| 06 | Données : pandas et visualisation | `06-pandas-visualisation.md` |
| 07 | Régression linéaire from scratch | `07-regression-lineaire.md` |
| 08 | Régression logistique et classification | `08-regression-logistique.md` |
| 09 | Évaluation : train/val/test, métriques, overfitting, data leakage | `09-evaluation.md` |
| 10 | Arbres, random forests, gradient boosting | `10-arbres-ensembles.md` |
| 11 | Non supervisé : k-means et PCA | `11-non-supervise.md` |
| 12 | **Projet de phase** : projet ML classique complet | `12-projet-phase-1.md` |

### Ressources par module

- **01** — [3Blue1Brown : Essence of Linear Algebra](https://www.3blue1brown.com/topics/linear-algebra) · [Khan Academy (fr)](https://fr.khanacademy.org/) · [MML, chapitres 2 et 3](https://mml-book.github.io/)
- **02** — [3Blue1Brown : Essence of Calculus](https://www.3blue1brown.com/topics/calculus) · [MML, chapitre 5](https://mml-book.github.io/) · [3Blue1Brown : Neural Networks](https://www.3blue1brown.com/topics/neural-networks)
- **03** — [Seeing Theory](https://seeing-theory.brown.edu/) (probabilités visuelles) · [MML, chapitre 6](https://mml-book.github.io/) · [StatQuest](https://www.youtube.com/@statquest)
- **04** — [Think Stats](https://greenteapress.com/wp/think-stats-2e/) (Allen Downey, gratuit) · [StatQuest : maximum de vraisemblance](https://www.youtube.com/@statquest)
- **05** — [NumPy pour débutants absolus](https://numpy.org/doc/stable/user/absolute_beginners.html) · [Guide utilisateur NumPy](https://numpy.org/doc/stable/user/index.html) · [Broadcasting](https://numpy.org/doc/stable/user/basics.broadcasting.html) · [Scientific Python Lectures](https://lectures.scientific-python.org/)
- **06** — [Guide utilisateur pandas](https://pandas.pydata.org/docs/user_guide/index.html) · [matplotlib](https://matplotlib.org/stable/users/index.html) · [Python Data Science Handbook, chapitres 3 et 4](https://jakevdp.github.io/PythonDataScienceHandbook/)
- **07** — [scikit-learn : modèles linéaires](https://scikit-learn.org/stable/modules/linear_model.html) · Géron, chapitre 4
- **08** — [scikit-learn : régression logistique](https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression) · Géron, chapitres 3 et 4
- **09** — [Validation croisée](https://scikit-learn.org/stable/modules/cross_validation.html) · [Métriques](https://scikit-learn.org/stable/modules/model_evaluation.html) · [Pièges courants](https://scikit-learn.org/stable/common_pitfalls.html)
- **10** — [Arbres de décision](https://scikit-learn.org/stable/modules/tree.html) · [Méthodes d'ensemble](https://scikit-learn.org/stable/modules/ensemble.html) · Géron, chapitres 6 et 7
- **11** — [Clustering](https://scikit-learn.org/stable/modules/clustering.html) · [PCA](https://scikit-learn.org/stable/modules/decomposition.html#pca) · Géron, chapitres 8 et 9
- **Référence générale** — [Guide utilisateur scikit-learn](https://scikit-learn.org/stable/user_guide.html)

---

## Phase 2 — Deep learning pour la vision (févr. → avr. 2027)

Dossier : `phase-2-deep-learning-vision/`

| N° | Module | Fichier |
|----|--------|---------|
| 01 | Réseaux de neurones et backpropagation (micrograd) | `01-reseaux-neurones.md` |
| 02 | PyTorch : tenseurs, autograd, boucle d'entraînement, GPU | `02-pytorch.md` |
| 03 | Bien entraîner : optimiseurs, régularisation, diagnostic | `03-entrainement.md` |
| 04 | Images et réseaux convolutifs (CNN) | `04-cnn.md` |
| 05 | Architectures modernes (ResNet, EfficientNet) et transfer learning | `05-transfer-learning.md` |
| 06 | Attention, transformers et Vision Transformers (ViT) | `06-vision-transformers.md` |
| 07 | Augmentation de données et fine-tuning (timm, Hugging Face) | `07-augmentation-finetuning.md` |
| 08 | **Projet de phase** : classifieur d'images médicales par transfer learning | `08-projet-phase-2.md` |

### Ressources par module

- **01** — [Karpathy : Neural Networks, Zero to Hero](https://karpathy.ai/zero-to-hero.html) · [micrograd](https://github.com/karpathy/micrograd) · [D2L, chapitre MLP](https://d2l.ai/)
- **02** — [Tutoriels PyTorch](https://pytorch.org/tutorials/) · [Documentation PyTorch](https://pytorch.org/docs/stable/index.html) · [Autograd](https://pytorch.org/tutorials/beginner/blitz/autograd_tutorial.html)
- **03** — [Karpathy : A Recipe for Training Neural Networks](http://karpathy.github.io/2019/04/25/recipe/) · [Papier Adam](https://arxiv.org/abs/1412.6980) · [torch.optim](https://pytorch.org/docs/stable/optim.html)
- **04** — [Stanford CS231n](https://cs231n.github.io/) · [D2L : CNN](https://d2l.ai/)
- **05** — [Papier ResNet](https://arxiv.org/abs/1512.03385) · [Papier EfficientNet](https://arxiv.org/abs/1905.11946) · [Transfer learning (PyTorch)](https://pytorch.org/tutorials/beginner/transfer_learning_tutorial.html)
- **06** — [Attention Is All You Need](https://arxiv.org/abs/1706.03762) · [Papier ViT](https://arxiv.org/abs/2010.11929) · [D2L : attention et transformers](https://d2l.ai/)
- **07** — [timm](https://huggingface.co/docs/timm/index) · [Hugging Face Transformers](https://huggingface.co/docs/transformers/index) · [Albumentations](https://albumentations.ai/docs/)
- **Cours complémentaire** — [fast.ai : Practical Deep Learning for Coders](https://course.fast.ai/)

---

## Phase 3 — IA pour l'ophtalmologie (mai → août 2027)

Dossier : `phase-3-ophtalmologie/`

| N° | Module | Fichier |
|----|--------|---------|
| 01 | L'œil et son imagerie : fond d'œil, OCT, principales pathologies | `01-oeil-imagerie.md` |
| 02 | Données médicales : prétraitement, qualité d'image, déséquilibre des classes, fuites par patient | `02-donnees-medicales.md` |
| 03 | Classification et gradation (rétinopathie diabétique, kappa quadratique) | `03-classification-gradation.md` |
| 04 | Segmentation : U-Net, vaisseaux rétiniens, disque optique | `04-segmentation.md` |
| 05 | Évaluation clinique : sensibilité, spécificité, AUC, calibration, biais | `05-evaluation-clinique.md` |
| 06 | Explicabilité (Grad-CAM) et estimation de l'incertitude | `06-explicabilite.md` |
| 07 | Éthique, réglementation et travail avec des ophtalmologues | `07-ethique-reglementation.md` |
| 08 | **Projet phare** : dépistage de la rétinopathie diabétique sur fond d'œil | `08-projet-phare.md` |

### Ressources par module

- **01** — [OMS : World report on vision](https://www.who.int/publications/i/item/9789241516570)
- **02** — [Kaggle : APTOS 2019 Blindness Detection](https://www.kaggle.com/c/aptos2019-blindness-detection) · [Kaggle : Diabetic Retinopathy Detection (EyePACS)](https://www.kaggle.com/c/diabetic-retinopathy-detection) · [OCT : jeu de données Kermany 2018](https://www.kaggle.com/datasets/paultimothymooney/kermany2018)
- **03** — [Gulshan et al. 2016, JAMA](https://doi.org/10.1001/jama.2016.17216) (rétinopathie diabétique par deep learning) · [cohen_kappa_score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.cohen_kappa_score.html)
- **04** — [Papier U-Net](https://arxiv.org/abs/1505.04597) · [DRIVE (segmentation des vaisseaux)](https://drive.grand-challenge.org/) · [IDRiD](https://idrid.grand-challenge.org/)
- **05** — [Calibration (scikit-learn)](https://scikit-learn.org/stable/modules/calibration.html) · [De Fauw et al. 2018, Nature Medicine](https://doi.org/10.1038/s41591-018-0107-6) (OCT)
- **06** — [Papier Grad-CAM](https://arxiv.org/abs/1610.02391)
- **07** — [Abràmoff et al. 2018, npj Digital Medicine](https://doi.org/10.1038/s41746-018-0040-6) (premier système autonome de dépistage autorisé)

---

## Phase 4 — Mise en production (sept. → oct. 2027)

Dossier : `phase-4-production/`

| N° | Module | Fichier |
|----|--------|---------|
| 01 | Servir un modèle : FastAPI et Docker | `01-fastapi-docker.md` |
| 02 | Optimiser l'inférence : quantification et ONNX | `02-optimisation-inference.md` |
| 03 | Suivi d'expériences et versioning (MLflow, DVC) | `03-mlflow-dvc.md` |
| 04 | Monitoring, dérive des données et réentraînement | `04-monitoring.md` |
| 05 | Tests et CI pour le ML | `05-tests-ci.md` |
| 06 | **Projet final** : outil de dépistage déployé avec interface web | `06-projet-final.md` |

### Ressources par module

- **01** — [FastAPI](https://fastapi.tiangolo.com/) · [Docker : Get started](https://docs.docker.com/get-started/)
- **02** — [ONNX Runtime](https://onnxruntime.ai/docs/) · [Quantification PyTorch](https://pytorch.org/docs/stable/quantization.html)
- **03** — [MLflow](https://mlflow.org/docs/latest/index.html) · [DVC](https://dvc.org/doc)
- **04** — [Evidently](https://docs.evidentlyai.com/)
- **05** — [GitHub Actions](https://docs.github.com/actions) · [pytest](https://docs.pytest.org/)
- **Référence générale** — [Made With ML](https://madewithml.com/) · [Full Stack Deep Learning](https://fullstackdeeplearning.com/) · *Designing Machine Learning Systems* (Chip Huyen)
