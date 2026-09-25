# Module 01 — Environnement de travail · Corrigé

> Phase 0 — Python en profondeur · Fichier : `phase-0-python/01-environnement-corrige.md`
> À lire **après** tes tentatives. Compare avec tes réponses, ligne par ligne.

---

## Récap actif : que fait `source .venv/bin/activate` ?

Il **ajoute le dossier `.venv/bin` au début du `PATH`**. Quand tu tapes `python` ou `pip`, le système parcourt le `PATH` dans l'ordre et exécute le premier programme trouvé : celui de l'environnement. Le script modifie aussi l'invite (le préfixe `(.venv)`) et définit la fonction `deactivate`, qui remet le `PATH` d'origine.

Réponse attendue en une phrase : *« Il met `.venv/bin` en tête du `PATH`, donc `python` et `pip` désignent ceux de l'environnement. »*

---

## Échauffement

### E1 — Dossier courant et contenu

```bash
pwd
cd ~/ML-Engineer
ls -la
```

`-a` affiche les fichiers cachés (ceux qui commencent par un point : `.git`, `.gitignore`), `-l` affiche le détail (droits, taille, date).

### E2 — Le `PATH`

```bash
echo $PATH
```

Les dossiers sont séparés par `:`. Dans ton cas, il y en a **13**. Astuce pour les compter et les lire un par un :

```bash
echo $PATH | tr ':' '\n'           # un dossier par ligne
echo $PATH | tr ':' '\n' | wc -l   # les compter
```

- **Lu en premier** : `/home/f0rg0t/.opencode/bin` (le plus à gauche).
- **Doublons** : `~/.opencode/bin` et `~/.local/bin` apparaissent deux fois. C'est sans danger (le système s'arrête à la première occurrence), mais c'est le signe que des fichiers de configuration du shell (`~/.zshrc`) ajoutent le même dossier plusieurs fois.

### E3 — Le Python du système

```bash
python3 --version
which python3
```

Résultat attendu : `Python 3.13.5` et `/usr/bin/python3`. Il manquait la commande `which`, vue en section 2 et utilisée en section 3.1.

---

## Application

### E4 — Créer et prouver l'activation

```bash
cd ~/ML-Engineer/phase-0-python/code
python3 -m venv .venv
source .venv/bin/activate
which python                  # preuve 1 : chemin dans .venv
python -c "import sys; print(sys.prefix)"   # preuve 2 : préfixe = dossier .venv
```

Le préfixe `(.venv)` dans l'invite est un indice, pas une preuve : il peut rester affiché à tort.

### E5 — Le `PATH` après activation

`/home/f0rg0t/ML-Engineer/phase-0-python/code/.venv/bin` est apparu **au début** du `PATH`. Le système prend le premier `python` trouvé en parcourant le `PATH` : c'est donc celui de l'environnement.

### E6 — Deux exécutions, deux résultats

- **Environnement activé** : `.venv/bin` est en tête du `PATH`, donc `python` désigne `.venv/bin/python`. `sys.executable` affiche ce chemin.
- **Après `deactivate`** : le `PATH` est restauré, donc `python` désigne `/usr/bin/python`, le Python du système.

`sys.executable` indique toujours **quel interpréteur exécute réellement le script**. C'est le réflexe à avoir dès qu'un « module introuvable » apparaît.

### E7 — `requirements.txt`

```bash
python -m pip install numpy jupyterlab
pip freeze > requirements.txt
wc -l requirements.txt
```

Environ 90 lignes, parce que `pip freeze` liste **tous** les paquets installés, y compris les **dépendances transitives** : jupyterlab dépend de dizaines de paquets (serveur web, gestion des notebooks, etc.), qui ont eux-mêmes des dépendances. Ta réponse était juste.

Pour aller plus loin : `pip install pipdeptree` puis `pipdeptree` affiche l'arbre des dépendances.

### E8 — Jupyter utilise-t-il le bon Python ?

```python
import sys
print(sys.executable)
```

Le chemin doit pointer dans `.venv`. Si ce n'est pas le cas, le kernel du notebook utilise un autre Python : c'est une source classique de « module introuvable » dans Jupyter.

---

## Problème

### E9 — Reproductibilité

```bash
cd ~/ML-Engineer/phase-0-python

# 1. Liste des paquets du premier environnement
source code/.venv/bin/activate
pip freeze > freeze-1.txt
deactivate

# 2. Nouvel environnement à partir de requirements.txt
mkdir code-copie && cd code-copie
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r ../code/requirements.txt
pip freeze > ../freeze-2.txt
deactivate
cd ..

# 3. Comparaison
diff freeze-1.txt freeze-2.txt
echo $?
```

- **`diff` n'affiche rien** : les deux fichiers sont identiques, donc les deux environnements contiennent exactement les mêmes paquets aux mêmes versions.
- **`echo $?`** affiche le **code de sortie** de la dernière commande : `0` pour « identiques », `1` pour « différents ». Les scripts automatiques (et plus tard ta CI en phase 4) utilisent ce code.

Ensuite, supprime les fichiers de test : `rm -r code-copie freeze-1.txt freeze-2.txt`.

### E10 — Git et GitHub

Dépôt vérifié : le `.gitignore` est présent et `.venv` est absent. Reste à corriger :
- le dossier `phase-1-fondations/` visible sur GitHub. Git ne versionne pas les dossiers vides : il contient donc un fichier (probablement l'ancien diagnostic). Supprime-le avec `git rm`, puis fais un commit ;
- l'habitude de faire un commit à la fin de chaque séance.

### E11 — Carte graphique

Résultat : le pilote NVIDIA ne répond pas. Le diagnostic complémentaire montre :
- **graphiques hybrides** : Intel UHD 730 (affichage) + RTX 3070 Mobile ;
- pilote libre **`nouveau`** chargé pour la NVIDIA : il ne gère pas CUDA ;
- démarrage **UEFI**, **Secure Boot désactivé**.

Action : installation du pilote propriétaire NVIDIA avec un guide dédié, avant la phase 2.

---

## Questions de compréhension

### Q1 — Un environnement virtuel est-il une machine virtuelle ?

**Non.** Une machine virtuelle simule un ordinateur complet, avec son propre système d'exploitation. Un environnement virtuel est un simple **dossier** qui contient :
- un lien vers le Python du système (`ls -l .venv/bin/python`) ;
- son propre `site-packages` pour les bibliothèques ;
- un script `activate` qui modifie le `PATH`.

Seules les **bibliothèques Python** sont isolées. Le système, les fichiers et les processus sont partagés.

### Q2 — Pourquoi `pip install` échoue sur le Python du système ?

Parce que Parrot OS (basé sur Debian) protège son Python avec la règle de la PEP 668 : des outils du système en dépendent, et installer ou mettre à jour des paquets pourrait les casser. C'est une protection, pas un bug. Ta réponse était juste.

### Q3 — Pourquoi pas `.venv/` dans Git, mais `requirements.txt` oui ?

1. `.venv` est **lourd** (des centaines de Mo).
2. Il est **recréable** en une commande à partir de `requirements.txt`.
3. Il n'est **pas portable** : il contient des chemins absolus et des liens propres à ta machine. Copié sur un autre PC, il ne fonctionnerait probablement pas.

`requirements.txt`, lui, est léger, lisible, et décrit exactement ce qu'il faut installer.

### Q4 — Résultat surprenant après des cellules exécutées dans le désordre

**Kernel → Restart Kernel and Run All Cells.** Le kernel repart d'une mémoire vide et exécute toutes les cellules dans l'ordre. Ce n'est qu'après que l'on peut faire confiance au résultat.

Ne pas confondre :

| Notion | Ce que c'est | Rôle |
|--------|--------------|------|
| Environnement virtuel | Un dossier (`.venv`) | Choisir quel Python et quelles bibliothèques |
| Kernel | Un processus Python en cours d'exécution | Exécuter les cellules et garder les variables en mémoire |

Désactiver l'environnement n'a aucun effet sur un kernel qui tourne déjà.

---

## Leçons à retenir de ce module

1. **Lis le message d'erreur en entier** : `command not found: desactivate` contenait la réponse (la commande est `deactivate`).
2. **Relis le cours avant de dire « je ne sais pas »** : E3 et E6 y étaient expliqués.
3. **Environnement, interpréteur, kernel** : trois notions distinctes. Savoir laquelle est en cause, c'est la moitié du débogage.
