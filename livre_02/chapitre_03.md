
# Chapitre 3 - Growth of Functions

mesure d'efficacite : order of growth of the running time of an algorithm. compare the relative performance of alternative algorithms

input size n (becomes large enough)

- merge sort: Theta(n lg n)  worst-case running time
- insertion sort : Theta(n^2)

analyse asymptotic, aux limites

## 3.1 Asymptotic notation

### Asymptotic notation, functions, and running times

details: a.n^2 + b.n + c (insertion sort)
asymptotic ~ Theta(n2)

which running time ?

Theta(g(n)) = { f(n) } : there exist positive constants c1, c2, and n0 such that 0 

Member d'un ensemble de fonctions = pas une seule fonction f() qui peut etre une borne de g()

Theta = moyen (il existe c1.g(n) et c2.g(n) inf). asymptotically tight bound 
O = meilleur cas (brne inferieure), asymptotic upper bound
omega= plus mauvais cas (borne sup)

### Theta notation

Demonstration que a.n^2 + b.n + c ~ Theta(n^2)
Demontration que 6.n^3 != Theta(n^2)

Theta(1) = Theta(n^0) = constante

### O -notation

asymptotic upper bound

f = Theta(g) => f = O(g)

peut etre deduit directement de l'analyse du code
Par exemple, 2 boucles imbriqués = O(n^2)

la limite O(n^2) sur le plus mauvais cas est egalement O(n^2) sur tous les cas.
Mais pas vrai pour Theta. Par exemple, insertion sort si collection est deja triée est Theta(n)

### omega -notation

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

### petit omega notation

Idem

f/g -> 00, quand n->oo

### Comparing functions

- Transitivity
- Reflexivity
- Symmetry
- Transpose symmetry

Trichotomy


# 3.2 Standard notations and common functions

## Monotonicity

## Floors and ceilings

## Modular arithmetic

## Polynomials

## Exponentials

## Logarithms

## Factorials

## Functional iteration

## The iterated logarithm function

## Fibonacci numbers





question
- revenir sur le "meilleur cas" "plus mauvais cas"
- asymptoic
- ensemble de fonctions. petit o et petit omega
- faire les demos de a.n^2 + b.n + c ~ Theta(n^2)

