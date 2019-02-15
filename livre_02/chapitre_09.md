# Chapitre 9 - Medians and Order Statistics

- def: statique d'ordre (statistic order) est le i-ème plus petit élément
- def: minimum i=1, max i=n
- def: mediane est le point central, lower median si pair

probleme : determiner l'ordre i-eme (selection problem)

- input: ensemble A d'elements distincts, 1 <= i <= n
- output: element x de A, plus large que exactement i-1 autres elements de A

Approche simple: O(n lg n), en triant l'ensemble, puis en prenant l'element i.

plan:
- 9.1: selection de min et max
- 9.2: algo en O(n) en temp attendu
- 9.3: algo en O(n) dans le pire des cas

## 9.1 - Minimum and maximum

minimum de comparaison nécessaire = n-1

algo:
```
  min = A[1]
  pour chaque x de A:
    si min > x alors min = x
  return x
```

preuve: moins de comparaisons -> au moins 1 element n'est pas testé. Si c'est le mac, alors fails

### Simultaneous minimum and maximum

ex: points 2D, besoin de trouver les limites

algo: 
```
2 comparaison par element
  si n impaire -> prendre le premier element pour initialiser min et max. 3*|n/2| comparaisons
  si n pair -> faire une premiere comparaison pour determiner min et max. 3*|n-2)/2 comparaisons
```

## 9.2 - Selection in expected linear time

temps asymptotique: Theta(n). Par diviser-conquerir, basé sur quicksort

RANDOMIZED-SELECT sur 1 coté de la partition, ce qui fait passer de Theta(n lg n) à Theta(n).

```
RANDOMIZED-SELECT(A ,p, r, i)
  si p==r
    return A[p]
  q = RANDOMIZED-PARTITION(A ,p, r)
  k = q-p+1
  si i == k: // pivot est le resultat
    A[q]
  sinon si i < k:
    return RANDOMIZED-SELECT(A ,p, q-1, i)
  sinon:
    return RANDOMIZED-SELECT(A ,q+1, r, i-k)
```

Worst case: Theta(n^2), puisque partioning prend Theta(n)

demonstration via esperance statistique pour montrer que le cas moyen est en O(n)

## 9.3 Selection in worst-case linear tim

algo:
```
  partitionner en groups de 5 elements
  trouver la mediane de chaque groupe apres insertion sort
  utiliser SELECT pour trouver la mediane
  partitionner a partir de la mediane trouvée
  si i=k, retourner x. Sinon, utiliser SELECT recursivement
```
