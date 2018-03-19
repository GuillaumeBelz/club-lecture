# Résumé

Le but du chapitre est de se familiariser avec le pseudo-code utilisé dans le livre et avec les
notations liées à la complexité algorithmique. Les deux principaux exemples sont :

- le tri par insertion
- le tri fusion

## Tri par insertion

Note à propos du pseudo-code: le but est d'être précis tout en s'abstrayant des détails quand cela
permet de mieux comprendre l'algorithme en lui-même. Par exemple, on peut remplacer certaines
instructions par une phrase en langue naturelle.

Le code peut être trouvé à peu près n'importe où. Il consiste à chaque tour de boucle à
prendre le prochain élément non trié, à faire glisser tous les éléments qui lui sont supérieurs
vers la fin du tableau et finalement l'insérer juste après le premier élément inférieur.

### La notion d'invariant de boucle

Un invariant de boucle est une propriété qui est vraie avant de commencer chaque itération de boucle
(comprenant l'invalidation de la condition de boucle). Trois propriété à montrer:

- vrai à l'initialisation,
- si vrai au rang i, vrai au rang i+1,
- vrai à la terminaison.

### Invariant du tri par insertion

A chaque itération "i", le sous-tableau allant du début à "i-1" (inclus, ou i exclu) correspond
à une permutation triée des éléments qui étaient précédemment présents dans ce sous-tableau.

Intuition de preuve:

- 1) un tableau à un élément est trié
- 2)
  - les éléments du sous-tableau à i sont triés, les faire glisser ne les détrie pas
  - on ajoute l'élément en sous des éléments qu'on a fait glissé,
  - et au dessus du premier élément plus petit
  On maintien le tri
- 3) a la fin, i vaut taille du tableau donc tous les éléments jusqu'à taille du tableau sont triés

### Exercices :

1) appliquer l'algo sur papier
2) changer la condition pour faire glisser (et la preuve reste la même modulo le sens de l'inégalité)
3) linear-search :
  Invariant: pour tout élément avant i, ce n'est pas celui-cherché
  Avec une variable intermédiaire, la preuve est plus directe.
4) Dernier algo, un peu plus compliqué. Je peux le faire éventuellement.

## Analyser des algorithmes

On considère une machine abstraites qui a les instructions communes d'une vraie machine. Cependant,
on évacue les questions de concurrence, parallélisme, caches, etc. On considère des mots de la taille
d'un entier.

Taille de l'entrée: généralement on considère que le nombre d'éléments considérés en entrée est une
bonne entrée. Mais par exemple, dans le cas de l'addition de deux entiers en bit à bit, ce sera le
nombre de bits. Cela doit être précisé pour chaque problème.

Le temps de calcul: nombre de pas primitifs exécutés, ici nous considérerons généralement les
instructions

NOTE: c'est une triche assez commune pour les algos de graphs par exemple, de considérer
      qu'on peut vérifier l'existence d'un élément dans un set en O(1)).

### Runtime du tri par insertion

Meilleur cas: les éléments sont déjà triés (on obtient un O(n))
Pire cas: les éléments sont à l'envers (an²+bn+c ~ O(n²))

On se concentre généralement sur le pire cas. Il donne une borne supérieure et c'est le plus
intéressant en général. Le cas moyen peut être intéressant parfois quand il est facile de l'obtenir
et que les résultats sont très bon sur celui-ci.

### Croissance

On simplifie la vue que l'on a de la complexité en ne gardant que l'élément d'ordre maximal.
Notation: Theta

### Exerices

1) n cube
2)
  - l'algo est en n² (best et worse sont équivalents)
  - l'invariant est sensiblement le même que selection sort,
  - l'élément final est nécessairement supérieur puisque:
    - soit on l'a échangé avec le précédent parce que le précédent était plus grand
    - soit on ne l'a pas échangé par le final était plus grand
3) Dans le meilleur des cas 1
   Dans le pire, tous

4) Vérifier en premier lieu si c'est OK ?

## Designing algorithms

Présentation de l'approche "diviser pour régner" (divide and conquer).
Généralement des algorithmes récursifs, qui vont:
  - diviser le sous problème en instances réduites
  - résoudre ces sous problèmes récursivement
  - combiner les solutions pour obtenir la solution au problème original.

### Exemple avec tri fusion:

  - on coupe le tableau en deux,
  - on trie chacun des tableaux avec tri fusion
  - on fusionne les deux tableaux triés.

La récursion s'arrête pour les tableaux de taille 1 ou moins: ils sont déjà triés.

NOTE: La sentinelle complique le code plus qu'elle ne le simplifie AMHA.

Invariant du merge: tous les éléments jusqu'au rang "n" de l'algo sont triés, et tous les éléments
restant dans les tableaux sont plus grand que le dernier ajouté.

- init : il n'y a pas d'élément
- n -> n+1 :
  tous les éléments jusqu'à n sont triés et ceux restant sont supérieur,
  on prend le plus petit des deux et on l'ajoute donc :
    - les éléments sont triés à n+1
    - et comme on a pris le plus petit des éléments restant, tous les autres sont plus grands
- fin: quand on arrive à la taille tous les éléments sont triés.

### Analyse d'un algo D&C

On utilise généralement des équations de récurrence. Généralité:

T(n) = | O(1)                   si n <= c
       | aT(n/b) + D(n) + C(n)  sinon

Avec a le nombre de sous problèmes, b la taille des sous problèmes, D le temps de division et
C le temps de combinaison.

Pour merge sort:

La procédure de séparation en deux est en temps constant, la procédure de fusion est linéaire (on
visite chaque élément). Chaque étage de la récursion est donc en temps N (on voit une fois chaque
élément). On a ensuite (log n) récursion (puisqu'on casse en deux à chaque tour) donc

T(n) = | O(1) si n = 1
       | 2T(n/2) + O(n) si n > 1

O(n log n) (à voir dans le chapitre 4)

### Exercices

1) Faire une exécution de merge-sort à la main
2) La même chose sans les sentinelles (plus facile AMHA)
3) Par induction sur k
4) Ça ne change rien, mais on peut construire le raisonnement
5) Si j'ai le temps je mettrai le binary search avec Frama-C quelque part
6) Ça ne change rien au fait qu'il faut shifter les éléments
7) ?

### Problèmes

A voir.

# Questions:

[Q] Preuve de terminaison :

Utilisation de variant de boucle.
Note à propos de la récurrence qui est équivalente à une boucle.

[Q] Exemple d'élémemts qui différencient de la machine RAM :

- Cache pour les mémoire
- Execution out of order

Pertinence de l'analyse:

- Typiquement en rapport à la taille des mots
- Forte complexité -> impact moindre des caches
- Attention à bien regarder tout ce qui se passe et ne pas abstraire les mauvaises idées
- WCET sur du vrai matériel, possible mais très coûteux.

[Q] Tri adaptatif en fonction des entrées
Et de manière générale algo adapté quand l'entrée à des propriétés connues.
Par exemple pour le tri, on peut choisir le bon algorithme en fonction de la taille du
tableau.

[Q] Différence entre bas et haut niveau à la fois sur la preuve et la complexité
A bas niveau, on a souvent des détails supplémentaires qui sont plus ou moins intéressants:
 - pour la complexité, il faut être capable de faire un tri pertinent entre ce qui est
   coûteux et ce qui ne l'est pas
 - pour la preuve, aucun détail ne peut être ignoré généralement (notamment la sûreté des
   accès), mais on peut progressivement s'en abstraire à l'aide de propriété de plus 
   haut niveau.
   
A haut niveau, on a moins de détails et on compose des traitements plus larges, cela 
facilite généralement les raisonnements
  - en complexité il faut faire attention: certains détails des couches inférieures
    pourraient nous permettre d'avoir un calcul plus précis
  - en preuve, tant qu'on prouve qu'on respecte correctement les pré-conditions, on peut 
    raisonner abstraitement et prendre les post-conditions sans réfléchir.
