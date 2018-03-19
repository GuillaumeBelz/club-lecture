
# chapitre 4 - Divide-and-Conquer

exemple : merge sort

3 etapes: 
- diviser : le probleme en sous problemes plus petit
- conquerir : resoudre le sous probleme, potentiellement en le divisant encore
- combiner : les sous problemes pour resoudre le probleme

def: "recursive case" = sous probleme qui peut etre divisé
def: "bottoms out" = recursion qui se termine
def: "base case" = sous problemes resolvables

autres exemples du chapitre : 
- maximum-subarray problem : sous tableau contigue avec somme la plus grande
- multiplication de matrices, en Theta(n^3) et Theta(n^2.81)

## Recurrences

def: equation ou inegalité definie en fonction d'entrées plus petites

Ex: merge sort, plus mauvais cas: 

T(n) =
> Theta(1), si n=1
> 2.T(n/2)+Theta(n), si n>1

et donc T(n)=Theta(n.log n)

Algo recursif par forcement avec des sous problemes de tailles equilibrés. Par exemple 1/3 et 2/3. Pas forcement non plus avec des tailles constantes. Par exemple un element de moins a chaque recursion : T(n)=T(n-1)+Theta(n).

3 methodes de resolutions de Theta ou O :
- substitution method: remplace un modele math et prouve qu'il est correct
- recursion-tree method: decoupage en arbre
- master method: T(n)=a.T(n/b)+f(n)

Parfois, on ne determine que le plus mauvais cas, et on utilise une inegalité dans ce cas. T(n)<=2.T(n/2)+Theta(n). Dans ce cas, utilisation de O. Idem pour >= avec Omega.

## Technicalities in recurrences

Mettre de coté certains details techniques. Par exemple, merge sort quand nombre impaire : n/2 n'est pas entier, pas possible de diviser en 2 problemes exactement identiques. 

Conditions limites aussi un probleme. Suppose T(n) constant pour n petit.

Plus generalement, mettre de coté les arrondis sup, inf et limites.

# 4.1 The maximum-subarray problem

example de la bourse.

- force brute: toutes les solutions. Arrangement (n 2) en Theta(n^2)
- transformation: tableau des changements plutot que tableau des valeurs. = trouver la suite continue non vide avec la plus grande somme. (maximum subarray). A(n-1 2)=Theta(n^2), pas meilleur.

note: doit contenir des valeurs negatives, sinon le tableau complet est la plus grande somme.

## A solution using divide-and-conquer

Division du tableau en 3 solutions, selon mid
- sous tableau dans [low, mid]
- sous tableau dans [mid, high]
- sous tableau contenant mid

### Recherche d'une somme max dans un sous tableau contenant mid: FIND-MAX-CROSSING-SUBARRAY

- parcourir de mid a low, trouver la somme max
- parcourir de mid a high, trouver la somme max
- retourner somme max = somme max low + somme max height

Algo en Theta(n)

### recherche d'une somme max dans un sous tableau: FIND-MAXIMUM-SUBARRAY

- 1 element = retourner cet element              # conquire
- prendre mid = (low+high)/2
  - FIND-MAXIMUM-SUBARRAY(low, mid)              # divide
  - FIND-MAXIMUM-SUBARRAY(mid+1, high)           # divide
  - FIND-MAX-CROSSING-SUBARRAY(low, mid, high)   # conquire
  - retourner le plus élevé des 3                # combine

### Analyzing the divide-and-conquer algorithm

hypothese simplificatrice : n puissance de 2. Donc division donne tout le temps un nombre entier.

- T(1)=Theta(1)
- Pour chaque sous probleme recursif : T(n/2)
- pour FIND-MAX-CROSSING-SUBARRAY: Theta(n)
- combine: Theta(1)

Donc:

T(n) = Theta(1) + 2.T(n/2) + Theta(n) + Theta(1) = 2.T(n/2) + Theta(n)

Meme solution que merge sort: Theta(n.log n)


# 4.2 Strassen’s algorithm for matrix multiplication

for (i, j, k)
  c_i_j = sum_k(a_i_k * b_k_j)

T(n) = Theta(n^3)

## A simple divide-and-conquer algorithm

hypothese simplificatrice : n puisssance de 2

SQUARE-MATRIX-MULTIPLY-RECURSIVE(A, B)
- pour n=1, c_1_1 = a_1_1 * b_1_1
- sinon, calculer les produits des sous matrices

note: ne pas copier pour creer les sous matrices, mais faire du calcul d'indice. = Theta(1).

- T(1) = Theta(1)
- T(n) = 8.T(n/2)
- combine = Theta(n^2)

## Strassen’s method

Ne calculer que 7 sous matrices par recursion

- diviser A, B et C en matrices n/2 * n/2
- calculer 10 matrices sommes et produits, Theta(n^2)
- calculer 7 matrices produits
- calculer les matrices C


