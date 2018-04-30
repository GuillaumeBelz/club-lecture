
# Chapitre 7 - Quicksort

worst-case running time of Theta(n^2)

pas le meilleur dans le plus mauvais cas, mais cas moyen en Theta(n lg n)
avec des constantes faibles. Et tri sur place. Et bon avec environment virtuels.

## 7.1 Description of quicksort

approche divide-and-conquer. Pour trier A[p..r]

- diviser : rearrange en 2 sous tableaux A[p..q-1] et A[q+1..r], avec chaque element: A[p..q-1] <= A[q] <= A[q-1..r]
- conquérir : trier les sous tableau reursivement
- combiner: rien a faire

Algo: 

QUICKSORT(A,p,r):
if p < r
    q = PARTITION(A,p,r)
    QUICKSORT(A,p,q-1)
    QUICKSORT(A,q+1,r)

Pour tout trier : QUICKSORT(A,1,A.length)

### Partitioning the array

PARTITION(A,p,r)
    x = A[r]
    i = p-1
    for j = p to r-1
        if A[j] <= x
            i = i + 1
            swap A[i] et A[j]
    swap A[i+1] et A[r]
    return i+1

Analyse :

- x=A[r] comme pivot
- regroupe les elements inferieurs a x dans A[p,i]
- regroupe les elements superieur a x dans A[i+1,j]

Invariants de boucle :

1. si p <= k <= i (sous tableau de gauche), alors A[k] <= x
2. si i+1 <= k <= j-1 (sous tableau de droite), alors A[k] > x
3. si k = r (pivot), alors A[k] = x

Preuve :

- initialisation : les sous tableaux sont vides, donc les invariants 1 et 2 sont vrais. Et l'initialisation du pivot fait que l'invariant 3 est vrai.
- maintenance : 2 cas, si A[j] est sup ou inf au pivot.
  - si A[j] > x, alors j=j+1. Les invariants restent valides.
  - si A[j] <= x, alors echange + incremantation de i et j. Invariants encore valides.
- terminaison : a la fin, j=r. 

Running time de PARTITION : Theta(n)


## 7.2 Performance of quicksort

proche de merge sort si partitionnement équilibré, proche de insertion sort sinon.

### Worst-case partitioning

Pire cas lorsque un des sous tableaux contient 0 elements. (prouvé dans 7.4.1)

T(n) = T(n-1) + T(0) + Theta(n) 
// sous-tableau de taille n-1, puis sous-table de taille 0, puis merge
T(n) = T(n-1) + Theta(n)
T(n) = Theta(n^2)

Pas meilleur que insertion sort

### Best-case partitioning

Equilibré = 2 sous problème de tailles n/2 et (n/2)-1

T(n) = 2T(n/2) + Theta(n)
T(n) = Theta(n lg n)

similaire merge sort

### Balanced partitioning

Meme si mal equilibré, plus proche du meilleur cas que du plus mauvais cas. (Prouvé dans 7.4)

Par exemple, avec partition 9/10 et 1/10 :

T(n) = T(9n/10) + T(n/10) + c.n 

- log_10(n) = Theta(lg n)
- log_10/9(n) = Theta(lg n)

Donc au final : O(n lg n). Et plus generalement pour toute partition de taille constante.

### Intuition for the average case

Alternative entre bons et mauvais parttion fait que cela s'equilibre et pas trop mauvais au final.


## 7.3 A randomized version of quicksort

En situation reelle, toutes les permutations ne sont pas forcement equivalentes.

Randomisation des entrées comme dans 5.3 possible. Mais plus simple a analyser : random sampling : choix du pivot aleatoire dans A[p..r] et echange avec A[r] au début.

RANDOMIZED-PARTITION(A,p,r):
    i = RANDOM(p,r)
    swap A[r] et A[i]
    return PARTITION(a,p,r)

RANDOMIZED-QUICKSORT(A,p,r):
    if p < r
        q = RANDOMIZED-PARTITION(A,p,r)
        RANDOMIZED-QUICKSORT(A,p,q-1)
        RANDOMIZED-QUICKSORT(A,q+1,r)

## 7.4 Analysis of quicksort

### 7.4.1 Worst-case analysis

montrer que le cas où la partition est 0 vs n-1 est le pire cas.

T(n) = max (T(q) + T(n-q-1)) + Theta(n)  | pour 0 <= q <= n-1

On a au pire : T(n) <= c.n^2, puis faire la substitution.

### 7.4.2 Expected running time


#### Running time and comparisons

Lemma 7.1

Let X be the number of comparisons performed in line 4 of PARTITION over the entire execution of QUICKSORT on an n-element array. Then the running time of QUICKSORT is O.n C X/.

