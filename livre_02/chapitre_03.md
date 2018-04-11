
# Chapitre 3 - Growth of Functions

La question posée par ce chapitre est de déterminer une mesure d'efficacité : comment le temps d'exécution d'un 
algorithme va grandir, en fonction de ses paramètres. Cette mesure permet de comparer les performances relatives
entre plusieurs alternatives d'algorithmes.

Le paramètre principal est la taille des entrées `n`. On s'interesse aux comportements aux limites (analyse asymptotic),
c'est-à-dire pour `n` suffisament grand.

Les temps d'execution dans le plus mauvais des cases (*worst-case running time*) :

- pour *merge sort* : `Theta(n lg n)`.
- pour *insertion sort* : `Theta(n^2)`

## 3.1 Asymptotic notation

Ce chapitre présente plusieurs démonstrations de calculs des performances des algorithmes. Reproduire ces
calculs dans le résumé n'est pas pertinent. Si cela vous intéresse, il est préférable de lire ces calculs 
directement dans le chapitre.

### Asymptotic notation, functions, and running times

Pour le tri par insertion, le détail des calculs donne des performances qui suivent une forme
polynomiale :

> a.n^2 + b.n + c

Le comportement asymptotique suit donc une loi en `Theta(n^2)`. (Les valeurs de `b.n` et `c` sont négligeables devant
`a.n^2` quand `n` est très grand).

Quel est le temps d'exécution ?

> Theta(g(n)) = { f(n) } : there exist positive constants c1, c2, and n0 such that 0 

Member d'un ensemble de fonctions = pas une seule fonction f() qui peut etre une borne de g()

Theta = moyen (il existe c1.g(n) et c2.g(n) inf). asymptotically tight bound 
O = meilleur cas (brne inferieure), asymptotic upper bound
omega= plus mauvais cas (borne sup)

### Theta notation

Demonstration que a.n^2 + b.n + c ~ Theta(n^2)
Demontration que 6.n^3 != Theta(n^2)

Theta(1) = Theta(n^0) = constante

### O-notation (grand O, la lettre)

asymptotic upper bound

f = Theta(g) => f = O(g)

peut etre deduit directement de l'analyse du code
Par exemple, 2 boucles imbriqués = O(n^2)

la limite O(n^2) sur le plus mauvais cas est egalement O(n^2) sur tous les cas.
Mais pas vrai pour Theta. Par exemple, insertion sort si collection est deja triée est Theta(n)

### grand omega-notation

asymptotic lower bound. best-case running time

> Theorem 3.1
> For any two functions f = Theta si et seulement si f = O et f = Omega

En general, theoreme utilisé pour determiner Theta a partir de O et Omega

## Asymptotic notation in equations and inequalities

a.n^2 + b.n + c = 2.n^2 + Theta(n) = 2.n^2 + f(n), avec f appatient a Theta
a.n^2 + Theta(n) = Theta(n^2) 

### o-notation

Idem O, mais pas Theta

exemple  2n = o(n^2), but 2.n^2 != o(n^2)

f/g -> 0 pour n->oo

### petit omega-notation

Idem

f/g -> 00, quand n->oo

### Comparing functions

- Transitivity
- Reflexivity
- Symmetry
- Transpose symmetry

Trichotomy


# 3.2 Standard notations and common functions





# Discussions



- revenir sur le "meilleur cas" "plus mauvais cas"
- asymptoic
- ensemble de fonctions. petit o et petit omega
- faire les demos de a.n^2 + b.n + c ~ Theta(n^2)

