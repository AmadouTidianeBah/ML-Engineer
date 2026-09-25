# Module 01 — Environnement de travail

> Phase 0 — Python en profondeur · Fichier : `phase-0-python/01-environnement.md`
> Durée estimée : 2 séances de 3 h

---

## 1. Objectifs et prérequis

**À la fin de ce module, tu sauras :**
- Utiliser le terminal pour les opérations de base.
- Installer Python et comprendre **quel** Python tu utilises.
- Créer, activer et comprendre un environnement virtuel (`venv`).
- Installer des bibliothèques avec `pip` et figer tes dépendances (`requirements.txt`).
- Exécuter du Python de trois façons : l'interpréteur interactif, un script, un notebook Jupyter.
- Versionner ton travail avec Git et le publier sur GitHub.
- Vérifier que ta carte graphique NVIDIA est reconnue.

**Prérequis** : aucun. Un PC sous Parrot OS et une connexion internet.

**Pourquoi commencer par là ?** En ML, la moitié des problèmes des débutants ne viennent pas du code mais de l'environnement : « ça marchait hier », « le module est introuvable », « PyTorch ne voit pas le GPU ». Un environnement propre, c'est la base du métier.

---

## 2. Le terminal : le minimum vital

Le terminal est ton outil principal. Voici les commandes à connaître par cœur.

| Commande | Rôle | Exemple |
|----------|------|---------|
| `pwd` | Affiche le dossier courant (*print working directory*) | `pwd` |
| `ls` | Liste le contenu d'un dossier | `ls -la` (tout, y compris les fichiers cachés) |
| `cd` | Change de dossier | `cd ~/ML-Engineer` |
| `mkdir` | Crée un dossier | `mkdir -p a/b/c` (crée aussi les parents) |
| `touch` | Crée un fichier vide | `touch notes.md` |
| `cat` | Affiche un fichier | `cat notes.md` |
| `cp` / `mv` | Copie / déplace ou renomme | `mv ancien.md nouveau.md` |
| `rm` | Supprime (**définitivement**, pas de corbeille) | `rm fichier.txt` |
| `which` | Indique quel programme sera exécuté | `which python3` |
| `echo $PATH` | Affiche la liste des dossiers où le système cherche les programmes | `echo $PATH` |

**Raccourcis utiles**
- `~` = ton dossier personnel (`/home/ton_nom`).
- `.` = le dossier courant, `..` = le dossier parent.
- `Tab` complète automatiquement les noms. Utilise-le tout le temps.
- `Ctrl + C` interrompt une commande en cours.
- Flèche du haut : rappelle la commande précédente.

### Sous le capot : le `PATH`

Quand tu tapes `python3`, le système ne « sait » pas où est ce programme. Il parcourt, dans l'ordre, les dossiers listés dans la variable d'environnement `PATH`, et exécute le **premier** `python3` qu'il trouve. Retiens bien ce mécanisme : c'est exactement ce que l'environnement virtuel va exploiter à la section 4.

---

## 3. Installer et identifier Python

### 3.1 Installation

Parrot OS est basé sur Debian. Python 3 y est déjà installé, car le système lui-même l'utilise. Il faut ajouter les outils de développement :

```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip python3-dev git
```

Vérifie :

```bash
python3 --version
which python3
```

Tu devrais voir une version 3.x et le chemin `/usr/bin/python3`.

### 3.2 Règle d'or : ne jamais toucher au Python du système

Le Python de `/usr/bin/python3` appartient à Parrot OS. Des outils du système en dépendent. Si tu y installes ou mets à jour des bibliothèques, tu risques de casser ton système.

D'ailleurs, essaie :

```bash
pip install numpy
```

Tu obtiens une erreur `externally-managed-environment`. Ce n'est pas un bug, c'est une **protection** : les distributions récentes de Debian empêchent `pip` de modifier le Python du système (règle définie par la [PEP 668](https://peps.python.org/pep-0668/)). La solution propre, ce n'est pas de forcer, c'est l'environnement virtuel.

> Ne jamais utiliser `--break-system-packages` ni `sudo pip install` sur ta machine. Ce sont les deux erreurs classiques qui cassent un système Linux.

---

## 4. Les environnements virtuels (`venv`)

### 4.1 Le problème

Imagine deux projets :
- Le projet A a besoin de PyTorch 2.1.
- Le projet B a besoin de PyTorch 2.4.

Si toutes tes bibliothèques sont installées au même endroit, tu ne peux avoir qu'une seule version. Un des deux projets casse.

### 4.2 La solution

Un **environnement virtuel** est un dossier qui contient son propre Python et ses propres bibliothèques, isolé du reste. Un projet = un environnement.

```bash
cd ~/ML-Engineer/phase-0-python
mkdir code && cd code
python3 -m venv .venv          # crée l'environnement dans le dossier .venv
source .venv/bin/activate      # l'active
```

Ton invite de commande affiche maintenant `(.venv)`. Vérifie :

```bash
which python
python --version
```

Le chemin pointe maintenant vers `.../code/.venv/bin/python`. Pour sortir de l'environnement :

```bash
deactivate
```

### 4.3 Sous le capot : que fait vraiment `venv` ?

Regarde ce qui a été créé :

```bash
ls .venv
ls .venv/bin
cat .venv/pyvenv.cfg
```

Tu verras :
- `pyvenv.cfg` : un petit fichier qui indique quel Python a servi de base (`home = /usr/bin`).
- `bin/` : contient `python` (un lien vers le Python du système), `pip`, et le script `activate`.
- `lib/python3.x/site-packages/` : le dossier où **tes** bibliothèques seront installées.

Et `source .venv/bin/activate` ? Ce script fait principalement une chose : il **ajoute `.venv/bin` au début de ton `PATH`**. Du coup, quand tu tapes `python`, le système trouve d'abord celui de l'environnement. Voilà tout le « secret » : ce n'est pas une machine virtuelle, c'est un dossier et une modification du `PATH`.

Quand Python démarre depuis `.venv/bin/python`, il lit `pyvenv.cfg` et sait qu'il doit chercher les bibliothèques dans `.venv/lib/.../site-packages`. Tu peux le vérifier :

```bash
python -c "import sys; print(sys.prefix); print(sys.executable)"
```

---

## 5. `pip` : installer des bibliothèques

`pip` télécharge des bibliothèques depuis [PyPI](https://pypi.org/) (le dépôt officiel des paquets Python) et les installe dans le `site-packages` de l'environnement **actif**.

```bash
# environnement activé
pip install --upgrade pip
pip install numpy
pip list                  # ce qui est installé
pip show numpy            # détails : version, emplacement, dépendances
pip uninstall numpy
```

### 5.1 Figer ses dépendances : `requirements.txt`

Pour qu'un projet soit **reproductible** (qu'il marche chez toi dans 6 mois, ou chez quelqu'un d'autre), on note les versions exactes :

```bash
pip freeze > requirements.txt     # enregistre les versions installées
cat requirements.txt
```

Pour recréer le même environnement ailleurs :

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 5.2 Sous le capot : que contient un paquet ?

La plupart des bibliothèques sont distribuées sous forme de **wheels** (fichiers `.whl`) : des archives prêtes à installer, parfois avec du code compilé en C pour la performance. NumPy, par exemple, est écrit en grande partie en C. C'est pour ça qu'il est si rapide, et on y reviendra en phase 1.

### 5.3 Bonne pratique : `python -m pip`

Utilise `python -m pip install ...` plutôt que `pip install ...`. Cela garantit que `pip` travaille pour **le même Python** que celui que tu utilises, et évite des erreurs quand plusieurs Python coexistent.

---

## 6. Trois façons d'exécuter du Python

### 6.1 L'interpréteur interactif (REPL)

```bash
python
```

```python
>>> 2 + 3
5
>>> import sys
>>> sys.version
>>> exit()
```

Idéal pour tester une ligne rapidement. REPL signifie *Read–Eval–Print Loop* : il lit, évalue, affiche, recommence.

### 6.2 Un script

Crée `bonjour.py` :

```python
import sys

print("Bonjour, futur ML Engineer")
print("Python utilisé :", sys.executable)
```

Exécute :

```bash
python bonjour.py
```

Idéal pour du code qu'on réutilise, qu'on teste et qu'on versionne.

### 6.3 Un notebook Jupyter

```bash
python -m pip install jupyterlab
jupyter lab
```

Ton navigateur s'ouvre. Un notebook mélange cellules de code, résultats, graphiques et texte. C'est l'outil standard pour **explorer** des données et **expérimenter** en ML.

**Scripts ou notebooks ?**

| | Notebook | Script |
|---|----------|--------|
| Explorer des données, visualiser | Excellent | Moyen |
| Code réutilisable, testé, versionné | Faible | Excellent |
| Mise en production | À éviter | Standard |

Un ML Engineer utilise les deux : il **explore** en notebook, puis **déplace** le code solide dans des scripts et des modules.

### 6.4 Sous le capot : le kernel

Un notebook n'exécute pas le code lui-même. Il l'envoie à un **kernel**, un processus Python qui tourne en arrière-plan et garde les variables en mémoire entre les cellules. Conséquence : si tu exécutes les cellules dans le désordre, l'état en mémoire ne correspond plus à ce que tu lis à l'écran. Règle : avant de conclure quoi que ce soit, **Restart Kernel and Run All**.

---

## 7. L'éditeur de code

Utilise **VS Code** (ou **VSCodium**, sa version libre, disponible sur Parrot OS) avec l'extension officielle **Python** de Microsoft (et **Jupyter** pour les notebooks).

Configuration essentielle :
1. Ouvre le dossier de travail : `code ~/ML-Engineer/phase-0-python/code`
2. `Ctrl + Shift + P` → **Python: Select Interpreter** → choisis `./.venv/bin/python`.
3. Vérifie en bas de la fenêtre que c'est bien l'environnement `.venv` qui est sélectionné.

Si l'éditeur utilise le mauvais interpréteur, il te signalera des « modules introuvables » alors qu'ils sont installés. C'est l'erreur la plus fréquente chez les débutants.

---

## 8. Git : versionner son travail

### 8.1 Configuration (une seule fois)

```bash
git config --global user.name "Ton Nom"
git config --global user.email "ton.email@exemple.com"
git config --global init.defaultBranch main
```

### 8.2 Le cycle de base

```bash
cd ~/ML-Engineer
git init                     # crée le dépôt
git status                   # que s'est-il passé ?
git add .                    # prépare les changements
git commit -m "Début du programme ML Engineer"
git log --oneline            # historique
```

### 8.3 Le fichier `.gitignore`

Certains fichiers ne doivent **jamais** être versionnés : l'environnement virtuel (lourd, et recréable avec `requirements.txt`), les caches, les données volumineuses. Crée `~/ML-Engineer/.gitignore` :

```
# Environnements virtuels
.venv/

# Caches Python
__pycache__/
*.pyc

# Jupyter
.ipynb_checkpoints/

# Données et modèles (trop lourds pour Git)
data/
*.pt
*.pth
*.ckpt
```

### 8.4 Sous le capot : que contient `.git` ?

Git stocke des **instantanés** (snapshots) de tes fichiers, pas des différences. Chaque commit est identifié par un hash (une empreinte unique, comme `a3f9c2e`), calculé à partir de son contenu et de son commit parent. Tout est dans le dossier caché `.git` : supprime-le, et tout l'historique disparaît.

### 8.5 Publier sur GitHub

1. Crée un compte sur [github.com](https://github.com) si ce n'est pas fait.
2. Crée un dépôt vide nommé `ML-Engineer` (sans README).
3. Relie et envoie :

```bash
git remote add origin https://github.com/TON_PSEUDO/ML-Engineer.git
git push -u origin main
```

GitHub demande un **token** (jeton d'accès) au lieu du mot de passe. Crée-le dans *Settings → Developer settings → Personal access tokens*. Mieux encore, configure une clé SSH (voir [la documentation GitHub](https://docs.github.com/fr/authentication/connecting-to-github-with-ssh)).

Ton GitHub deviendra ton portfolio. Chaque module validé = un commit propre.

---

## 9. Vérifier la carte graphique

Ta RTX 3070 servira à entraîner des modèles en phase 2. Pour l'instant, on vérifie seulement qu'elle est reconnue :

```bash
nvidia-smi
```

- **Si un tableau s'affiche** avec le nom de la carte et une version de pilote (*Driver Version*) et de CUDA : tout va bien. Note ces deux versions dans tes réponses.
- **Si la commande est introuvable** ou renvoie une erreur : le pilote NVIDIA n'est pas installé. **N'essaie pas de l'installer seul maintenant**. Une installation ratée peut empêcher l'affichage graphique de démarrer. On le fera ensemble, pas à pas, avant la phase 2.

---

## 10. Lien avec le ML

- **Reproductibilité** : un résultat de ML qu'on ne peut pas reproduire ne vaut rien. `requirements.txt` + Git = la base de la reproductibilité. En phase 4, tu iras plus loin avec Docker, MLflow et DVC.
- **Conflits de versions** : PyTorch, CUDA et les pilotes doivent être compatibles entre eux. Un environnement par projet évite l'enfer des dépendances.
- **Médical** : en santé, il faut pouvoir prouver avec quel code et quelles versions un modèle a été entraîné. La traçabilité commence ici.

---

## 11. Organisation du code

À partir de maintenant, pour chaque phase :

```
phase-0-python/
├── 01-environnement.md          ← le cours
├── 01-environnement-reponses.md ← tes réponses
└── code/                        ← ton code (avec son .venv)
    ├── .venv/
    ├── requirements.txt
    └── exercices/
```

---

## 12. Exercices

Écris toutes tes réponses dans `01-environnement-reponses.md`. Pour les commandes, copie la commande **et** ce qu'elle a affiché.

### Échauffement

**E1.** Affiche ton dossier courant, puis va dans `~/ML-Engineer` et liste tout son contenu, fichiers cachés compris.

**E2.** Affiche ton `PATH`. Combien de dossiers contient-il ? Lequel est lu en premier ?

**E3.** Quelle est la version de Python du système, et où se trouve-t-il ?

### Application

**E4.** Dans `phase-0-python/code/`, crée un environnement virtuel `.venv`, active-le, et prouve que tu es dedans avec **deux** commandes différentes.

**E5.** Affiche à nouveau ton `PATH` avec l'environnement activé. Qu'est-ce qui a changé ? Explique en une phrase pourquoi `python` pointe maintenant vers l'environnement.

**E6.** Crée le script `bonjour.py` de la section 6.2. Exécute-le **avec** l'environnement activé, puis **après** `deactivate` (avec `python3 bonjour.py`). Compare les deux résultats et explique la différence.

**E7.** Installe `numpy` et `jupyterlab` dans l'environnement. Génère `requirements.txt`. Combien de lignes contient-il ? Pourquoi beaucoup plus que 2 ?

**E8.** Lance Jupyter Lab, crée un notebook `test.ipynb`, et dans une cellule, affiche `sys.executable`. Est-ce le Python de ton environnement ?

### Problème

**E9. Reproductibilité.** Crée un second dossier `code-copie/`, et recrée dedans un environnement **identique** au premier en utilisant uniquement `requirements.txt`. Prouve qu'ils sont identiques (indice : compare deux sorties avec `diff`).

**E10. Git.** Initialise un dépôt dans `~/ML-Engineer`, ajoute le `.gitignore` de la section 8.3, fais ton premier commit, puis publie sur GitHub. Donne le lien de ton dépôt. Vérifie sur GitHub que le dossier `.venv` n'y est **pas**.

**E11. GPU.** Exécute `nvidia-smi` et donne le nom de la carte, la version du pilote et la version de CUDA affichées (ou le message d'erreur).

### Questions de compréhension (avec tes mots, sans copier le cours)

**Q1.** Un ami te dit : « Un environnement virtuel, c'est une petite machine virtuelle. » A-t-il raison ? Explique ce que c'est vraiment.

**Q2.** Pourquoi `pip install numpy` échoue-t-il sur le Python du système de Parrot OS, et pourquoi c'est une bonne chose ?

**Q3.** Pourquoi ne met-on pas `.venv/` dans Git, alors qu'on y met `requirements.txt` ?

**Q4.** Tu as exécuté les cellules d'un notebook dans le désordre, et tu obtiens un résultat surprenant. Que fais-tu avant de conclure ?

---

## 13. Pour approfondir

**Documentation officielle**
- [venv — Création d'environnements virtuels](https://docs.python.org/fr/3/library/venv.html)
- [Installation de modules Python](https://docs.python.org/fr/3/installing/index.html)
- [Tutoriel : environnements virtuels et paquets](https://docs.python.org/fr/3/tutorial/venv.html)
- [Utiliser l'interpréteur Python](https://docs.python.org/fr/3/tutorial/interpreter.html)
- [PEP 668 — Environnements gérés en externe](https://peps.python.org/pep-0668/)
- [Guide de l'utilisateur de pip](https://pip.pypa.io/en/stable/user_guide/)
- [Documentation Jupyter](https://docs.jupyter.org/)
- [Python dans VS Code](https://code.visualstudio.com/docs/python/python-tutorial)

**Git**
- [Pro Git, chapitres 1 à 3 (en français)](https://git-scm.com/book/fr/v2)
- [Connexion à GitHub avec SSH](https://docs.github.com/fr/authentication/connecting-to-github-with-ssh)

**Terminal**
- [The Missing Semester of Your CS Education (MIT)](https://missing.csail.mit.edu/) : leçons 1 (shell) et 6 (Git). En anglais, excellent.

---

## 14. Devoir pour la prochaine séance

1. Faire les exercices E1 à E11 et répondre aux questions Q1 à Q4 dans `01-environnement-reponses.md`.
2. Envoyer ce fichier dans le chat, avec le lien de ton dépôt GitHub.
3. Préparer le récap actif : tu devras expliquer **sans notes** ce que fait `source .venv/bin/activate`.

Ensuite : correction, quiz, puis le module `02-types-modele-objet.md`.
