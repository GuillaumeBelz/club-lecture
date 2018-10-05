
# Chapitre 8 - 8 Sorting in Linear Time

algos en O(n lg n) :

- merge sort et heapsort dans le pire cas
- quicksort dans le cas moyen

def: comparison sorts = comparaison entre les elements pour trier

Plan :

- 8.1 : prouver que comparaison sorts sont en Omega(n lg n)
- 8.2 : couting sort
- 8.3 : radix sort
- 8.4 : bucket sort

## 8.1 Lower bounds for sorting

compare 2 elements a_i <=> a_j

Postulats:

- tous les elements distincts, a_i = a_j n'est pas utile
- toutes les comparaisons sont inutiles, on utilise a_i <= a_j

### The decision-tree model

def: full binary tree, represente les comparaison entre les elements par un algo
particulier sur une entree de taille donnee

Chaque noeud noté i:j et chaque feuille noté par une permutation <1,2,3>. Branche de gauche = a_i <= a_j, brache de droite = a_i > a_j.
n! permutations possible pour n elements.

Execution = trouver un chemin depuis la racine vers une feuille

### A lower bound for the worst case

worst case = chemin le plus long entre la racine et le plus long chemin

Theorem 8.1: Any comparison sort algorithm requires Omega(n lg n) comparisons in the worst case.

Corollary 8.2: Heapsort and merge sort are asymptotically optimal comparison sorts.

## 8.2 Counting sort






















