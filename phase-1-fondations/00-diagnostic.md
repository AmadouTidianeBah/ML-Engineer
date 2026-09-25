# Module 00 — Test de diagnostic

> Phase 1 — Fondations · Fichier : `phase-1-fondations/00-diagnostic.md`

## Objectif

Ce test n'est **pas noté**. Il sert à mesurer ton point de départ réel en maths et en Python, pour que je règle le niveau des cours au lieu de deviner.

## Consignes

- **Durée** : 30 minutes maximum. Chronomètre-toi et note ton temps réel.
- **Aucune aide** : pas d'internet, pas d'IA, pas de cours. Papier, crayon et un terminal Python uniquement pour la partie B.
- **« Je ne sais pas » est une bonne réponse.** Une réponse devinée fausse le diagnostic et te fera perdre du temps ensuite.
- **Montre tes calculs** : je note le raisonnement autant que le résultat.
- **Tes réponses** : écris-les dans un fichier `00-diagnostic-reponses.md` (même dossier), puis envoie-le-moi dans le chat, ou colle-les directement dans le chat.

---

## Partie A — Mathématiques (≈ 18 min)

### Algèbre linéaire

**A1.** Soient u = (2, −1, 3) et v = (4, 0, 1). Calcule le produit scalaire u · v.

**A2.** Calcule la norme du vecteur w = (3, 4).

**A3.** Calcule le produit matriciel AB :

```
A = | 1  2 |        B = | 0  1 |
    | 3  4 |            | 1  0 |
```

**A4.** A est une matrice 3 × 2 et B une matrice 2 × 4.
- Quelles sont les dimensions de AB ?
- Peut-on calculer BA ? Pourquoi ?

**A5.** Donne la transposée de :

```
M = | 1  2  3 |
    | 4  5  6 |
```

### Dérivées

**A6.** Soit f(x) = 3x² − 5x + 2.
- Calcule f'(x).
- Pour quelle valeur de x la fonction atteint-elle son minimum ?

**A7.** Dérive les fonctions suivantes :
- g(x) = e^(2x)
- h(x) = ln(x² + 1)

**A8.** Soit f(x, y) = x²y + 3y. Calcule les dérivées partielles ∂f/∂x et ∂f/∂y.

**A9.** Question de compréhension, avec tes mots : si la dérivée de f en un point est positive, dans quelle direction faut-il déplacer x pour faire **diminuer** f ? Pourquoi ?

### Probabilités et notations

**A10.**
- On lance un dé équilibré à 6 faces. Quelle est la probabilité d'obtenir un nombre pair ?
- On lance deux dés. Quelle est la probabilité que la somme fasse 7 ?

**A11.** Une variable aléatoire X prend les valeurs 1, 2 et 3 avec les probabilités 0,2, 0,5 et 0,3. Calcule l'espérance E[X], puis la variance Var(X).

**A12.** Une maladie de l'œil touche 1 % d'une population. Un test de dépistage détecte la maladie chez 90 % des malades, mais donne aussi un résultat positif chez 5 % des personnes saines. Une personne a un test positif : quelle est la probabilité qu'elle soit réellement malade ?

**A13.** Calcule la somme Σ (de i = 1 à 4) de i².

**A14.** Simplifie : ln(a · b) et ln(aⁿ).

---

## Partie B — Python (≈ 10 min)

**B1.** Sans exécuter le code, que va-t-il afficher ?

```python
nums = [3, 1, 4, 1, 5, 9]
print(sorted(nums)[-2:])
print([n ** 2 for n in nums if n % 2 == 1])
```

**B2.** Écris une fonction `moyenne_variance(valeurs)` qui renvoie la moyenne et la variance d'une liste de nombres, **sans aucune bibliothèque**.

**B3.** Écris une fonction `compter_mots(phrase)` qui renvoie un dictionnaire avec le nombre d'apparitions de chaque mot.
Exemple : `compter_mots("le chat et le chien")` renvoie `{"le": 2, "chat": 1, "et": 1, "chien": 1}`.

**B4.** Sans exécuter le code, que va-t-il afficher ? Explique pourquoi.

```python
def ajouter(x, acc=[]):
    acc.append(x)
    return acc

print(ajouter(1))
print(ajouter(2))
```

**B5.** As-tu déjà utilisé NumPy ? Si oui, que valent `a * a` et `a @ a` ?

```python
import numpy as np
a = np.array([[1, 2], [3, 4]])
```

**B6.** Sur Parrot OS, quelles commandes utiliserais-tu pour créer un environnement virtuel Python, l'activer, puis y installer NumPy ?

---

## Partie C — Auto-évaluation (≈ 2 min)

Note ton niveau de 1 (aucune notion) à 5 (très à l'aise) :

| Domaine | Note (1–5) |
|---------|------------|
| Vecteurs et matrices | |
| Dérivées et dérivées partielles | |
| Probabilités | |
| Statistiques | |
| Python (bases) | |
| NumPy | |
| pandas | |
| Git et terminal | |
| Lecture d'anglais technique | |

**Question libre** : quelle partie du programme t'inquiète le plus, et pourquoi ?

---

## Après le test

Reviens dans le chat avec tes réponses et ton temps réel. Je corrige, j'identifie tes points faibles, je mets à jour le carnet de bord, puis je t'envoie le cours `01-algebre-lineaire.md`, ajusté à ton niveau.
