
# Chapitre 5 - Probabilistic Analysis and Randomized Algorithms

## The hiring problem

On doit recruter un employé. L'agence envoie chaque jour un employé, on paie
l'agence, et si on recrute : on paie plus cher. Pour avoir toujours le meilleur
on recrute toujours la personne si elle est plus compétente que le précédent
employé.

La question est "combien ça va coûter à peu près ?".

L'algo est simple : avec une entrée en nombre de jour. Chaque jour on regarde
si l'employé est meilleur et on l'embauche si c'est le cas.

Ce qui change par rapport aux autres chapitre et ce que l'on détermine comme
étant le coût qui nous intéresse : ici ce n'est pas le temps d'exécution mais
l'argent dépensé.

La technique est cependant semblable, on regarde combien de fois un certain
coût est cumulé. Avec ci le coût d'interview et ch le coût de recrutement, et n
le nombre de jour et m le nombre de recrutement, on a :

O(ci * n + ch * m).

### Pire cas

On recrute à chaque fois: O(ch * n).
Sauf que le candidat n'est pas toujours meilleur

### Analyse probabiliste

Idée: faire l'analyse par la connaissance de la distribution de l'entrée (ou en
faisant des suppositions son propos). Il faut noter que c'est un cas moyen et
pas un pire cas (qui n'est pas probabiliste en soi).

Naturellement, la loi de probabilité doit être choisie avec attention sinon
l'analyse risque d'être complètement faussée.

Ici, on peut considérer qu'il est possible de trouver un ordre total sur la
qualité des employés et qu'une entrée est une permutation de cet ordre. Ici,
on a une permutation aléatoire et uniforme.

### Algorithmes randomisés

Pour pouvoir utiliser une analyse probabiliste, on a souvent besoin de connaître
quelque chose à propos de la distribution des entrées, ce qui n'est pas toujours
le cas. Dans ce cas, on peut se contenter de "forcer" la distribution à
respecter cette proposition : en mélangeant par exemple.

## Indicator random variables

Variable utilisée pour passer des probabilités aux effets attendus sur l'entrée.
Par exemple, on peut avoir:
Xf la variable nous indiquant "le nombre" de "face" lors d'un lancement de
pièce. Que l'on définit par :

Xf = I{Face}
Xf = | 1 si c'est face
     | 0 si c'est pile

On peut ainsi calculer l'espérance du lancer :

E[Xf] = E[I{Face}]
      = 1 * Pr{Face} + 0 * Pr{Pile}
      = 1/2

Lemme important: Xa = I{a} => E[Xa] = Pr{a}
Preuve simple par généralisation de l'exemple au dessus.
(Les références à l'annexe C pourrissent un peu la vie)

## Example with the hiring problem

Avec X le nombre de fois où l'on recrute.

E[X] = Sum(1, n, x * Pr{X = x})

Mais calculer ça, c'est pas pratique. Alors on utilise une indicator random
variable.

Xi = I{candidat i recruté}
   = | 1 si i est recruté
     | 0 sinon

Et X = X1 + X2 + ... + Xn

Par le lemme, on a :

E[Xi] = Pr{candidat i recruté}

Et on doit regardé la probabilité de recrutement. Le candidat i est recruté
quand il est meilleur que tous les candidats 0 à i-1. Qui ont tous les mêmes
probabilité d'être les meilleurs. Le candidat i a une chance sur i d'être
meilleur.

E[Xi] = 1/i

E[X] = E[ Sum(i: 1, n, Xi) ]
     = Sum(i: 1, n, E[Xi])
     = Sum(i: 1, n, 1/i)
     = ln(n) + O(1) (voir l'annexe A)

Ce qui veut dire que même si l'on interviewe tout le monde, on en recrute
ln n en moyenne.

(Et en multipliant par le coût de recrutement, on arrive au coût global).

## Algorithmes randomisés

Idée : forcer l'entrée à avoir la forme voulue d'un point de vue proba.
Par exemple pour l'algorithme de recrutement : on mélange les arrivants.
Et montrer que la complexité est O(ch ln n) est facile : on a créé la
condition correcte sur l'entrée.

### Permutation aléatoire de tableau

#### Permutation par le tri

On crée aléatoirement des priorités pour chaque valeur et on trie le tableau
d'origine en prenant comme clés les valeurs du tableau de priorités.
(Donc en temps O(n log n)).

Ensuite, on prouve la propriété importante que le résultat a une probabilité
de 1/n!. L'intuition est que la probabilité pour un élément d'être à la case
1 est de 1/n, et son suivant 1/(n-1) -> ... 1/1 soit 1/n!.

Note: montrer que la probabilité pour chaque case est de 1/n est insuffisant.

#### Permutation en place

Pour i de 1 à n swap A[i] avec une case entre i et la fin.

Pour prouver l'algo, on prouve un invariant montrant que le début du tableau
(jusqu'à i) est une (i-1)-permutation du tableau, et qu'en instanciant i à n
(fin de l'exécution), on arrive à une proba 1/n!

## Analyse probabiliste et autres usages des indicator random variables

### The birthday paradox

Combien de personne dans une pièce pour avoir 50% de chance d'avoir un
anniversaire commun ?
Résultat assez connu, l'idée est qu'il faut se pencher sur les chances que les
autres n'aient pas le même anniversaire que soi.

# Annexe C
