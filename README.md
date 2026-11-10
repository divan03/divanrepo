# Module PoC : Devoir 1 – Ajustement de Plan par Moindres Carrés

Ce dépôt contient le premier livrable du module **Proof of Concept (PoC)** du Master AMSS (ENS Paris-Saclay). L'objectif est de mettre en œuvre une démarche scientifique reproductible : import de données brutes, ajustement matriciel d'un plan par la méthode des moindres carrés, et visualisation tridimensionnelle.

---

## 1. Contexte & Objectif

L'exercice consiste à :
- Charger un nuage de points tridimensionnels $(x_i, y_i, z_i)$ depuis un fichier texte formaté.
- Estimer les paramètres optimaux du plan d'ajustement qui minimise la somme des carrés des résidus selon l'axe vertical $Z$.
- Restituer les résultats sous forme graphique (points mesurés et surface ajustée) dans un environnement reproductible documenté.

---

## 2. Modélisation Mathématique

L'équation cartésienne explicite d'un plan s'écrit :
$$z = c_1 x + c_2 y + c_0$$

Pour un ensemble de $N$ points expérimentaux $(x_i, y_i, z_i)_{i=1,\dots,N}$, on formule le problème sous forme matricielle surdéterminée :
$$A C \approx Z$$

avec :
$$A = \begin{bmatrix} 
x_1 & y_1 & 1 \\ 
x_2 & y_2 & 1 \\ 
\vdots & \vdots & \vdots \\ 
x_N & y_N & 1 
\end{bmatrix}, \quad 
C = \begin{bmatrix} c_1 \\ c_2 \\ c_0 \end{bmatrix}, \quad 
Z = \begin{bmatrix} z_1 \\ z_2 \\ \vdots \\ z_N \end{bmatrix}$$

Le vecteur optimal de paramètres $\hat{C}$ minimisant $\| A C - Z \|_2^2$ est donné par les équations normales :
$$\hat{C} = (A^T A)^{-1} A^T Z$$

Dans l'implémentation, la résolution est effectuée numériquement via `numpy.linalg.lstsq` (décomposition en valeurs singulières, SVD) afin d'assurer la stabilité numérique.

---

## 3. Structure du Répertoire

```text
.
├── README.md              # Description et documentation du projet
├── main.ipynb             # Notebook interactif (code, visualisations, analyses)
├── data/
│   └── points.txt         # Données brutes de coordonnées (x y z)
└── src/                   # Fonctions auxiliaires éventuelles (optionnel)
```

---

## 4. Prérequis et Installation

Le projet repose sur l'écosystème scientifique standard de Python (distribution Anaconda recommandée).

### Dépendances nécessaires :
- Python 3.9+
- `numpy`
- `matplotlib`
- `jupyter` / `notebook`

Pour installer l'ensemble via `pip` ou `conda` :
```bash
pip install numpy matplotlib notebook
```

---

## 5. Exécution

1. Cloner le dépôt :
   ```bash
   git clone <URL_DU_DEPOT>
   cd <NOM_DU_DEPOT>
   ```
2. Lancer l'environnement Jupyter :
   ```bash
   jupyter notebook
   ```
3. Ouvrir et exécuter les cellules du fichier `main.ipynb` dans l'ordre.

---

## 6. Contacts & Enseignants

- **Étudiant :** [Votre Nom / Prénom]
- **Enseignants référents :** Bruno Denis (`bruno2nis`), Kevin Godineau (`kevin-godineau`)