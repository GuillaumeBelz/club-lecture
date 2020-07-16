
# Chapitre 6 - Heapsort

note: tri par tas https://fr.wikipedia.org/wiki/Tri_par_tas

- O(n.log n), comme merge sort et contrairement a insertion sort.
- tri sur place, comme insertion sort et contrairement a merge sort

nouvelle technique de conception : utiliser une structure de données (tas)

## 6.1 Heaps

Tas = arbre binaire complet (tout les noeds d'un niveau sont utilisé avant de commencer les noeuds du niveau inferieur)

- A = tableau
- A.length = taille du tableau
- A.heap-size = taille du tas. 0 <= A.heap-size <= A.length

Acces aux parent et enfants, pour A[i] :

- parent = A[i/2]
- enfants = A[2i] et A[2i+1]

implementation en utilisant les bitshift

- max-heap : A[parent(i)] >= A[i]  ----> heapsort
- min-heap : A[parent(i)] <= A[i]

height = nombre de niveau avec la racine. 
Pour un tas de n elements : height = Theta(log n)

procédures :

- MAX-HEAPIFY : O(log n)
- BUILD-MAX-HEAP : linear time
- HEAPSORT : O(n.log n)

## 6.2 Maintaining the heap property

prendre le plus petit des sous noeuds et le descendre. Recusion

## 6.3 Building a heap

applique MAX-HEAPIFY sur chaque noeud qui n'est pas une feuille (neud terminal)

invariant : chaque noeud i+1, i+2,... est la racine d'un max-heap
initialisation : i=[n/2], [n/2]+1, [n/2]+2,... sont des feuilles et donc des racines de max-heap
maintenance : apres chaque iteration, les noeuds sont triés aussi
termination : n=1, tous les noeuds sont triés

BUILD-MAX-HEAP : O(n)

## 6.4 The heapsort algorithm

BUILD-MAX-HEAP puis extraire chaque element avec MAX-HEAPIFY

## 6.5 Priority queues

max-priority queue :

- insert(S,x)
- maximum(S)
- extract-max(S)
increase-kers(S,x,k)

