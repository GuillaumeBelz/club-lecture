
# Préface

Chaque chapitre presente un algorithme, une technique de conception,
un domaine d'application, ou un un sujet connexe.

Des solutions aux exercices sont en ligne :
http://mitpress.mit.edu/algorithms/

# Introduction

Résumé des chapitres de la première partie :

- chapitre 1 : vue d'ensemble et definition de ce qu'est une
  algorithme. Quelques exemples, quelques domaines.
- chapitre 2 : premiers algorithmes, sur le tri d'une séquence de n nombres :
  les tri par insertion (*insertion sort*) et tri fusion (*merge
  sort*), et la technique "Diviser pour régner"
  (*divide-and-conquer*).
- chapitre 3 : chapitre sur la complexité : comparaisons asymptotiques de fonctions
- chapitre 4 : Présentation d'un principe général algorithmique : diviser pour mieux régner
- chapitre 5 : introduction à l'analyse probabiliste et aux algorithmes
  aléatoires.
- annexes A à D : compléments mathématiques.

# Chapitre 1 - The Role of Algorithms in Computing.

## Généralités

Definition : procédure de calcul qui reçoit en entrée des valeurs et produit en
sortie des valeurs. Suite d'opérations qui transforme les entrées en
sorties. 

À l'heure actuelle, il n'y a pas de consensus sur la
définition *formelle* de ce qu'est un algorithme. Ce qu'on apelle
*opération* dépend du contexte : on considère très souvent que
l'addition est primitive alors que ce n'est pas forcément le cas pour
les processeurs qui éxécutent l'algorithme.

Outils pour résoudre des problèmes calculatoires, défini en termes
généraux. Contrairement aux algorithme, le problème peut être
formellement défini. Exemple : calculer la moyenne de n entiers par
exemple.

Algorithme correct : étant donné un problème, un algorithme est
correct vis-à-vis de ce problème si pour toute instance d'entrée, il
calcule la sortie attendue. Les algorithmes incorrects ne sont pas
nécessairement inutiles si le taux d'erreur est contrôlé par exemple.

Lorsque le problème est un problème d'optimisation (on chercher à
maximiser ou à minimiser une certaine valeure), les algorithmes ont
souvent beaucoup de solution candidates, trouver la meilleure solution
est très souvent difficile. Les algorithmes généralement ont des
applications pratiques.

Le livre présente quelques structures de données. Il présente
également des techniques d'approximation pour des problèmes où il
n'existe pas de solution exacte ou bien que la solution exacte est
trop longue à calculer en pratique. Il présente également quelques
problèmes NP-difficiles.

## Les algorithmes en tant que technologie

Même avec des machines infiniment rapides, on aurait quand même besoin
d'étudier l'algorithmique, rien que pour montrer qu'un algo fonctionne
(termine, et avec la bonne solution).

Efficacité : pour un problème donné, un algorithme pourra être très
rapide alors qu'un autre sera beaucoup plus lent. On utilise la notion
de complexité, pour *prédire* le comportement de l'algorithme. Cette
complexité dépend d'un paramètre (ou parfois plusieurs
paramètres). Très souvent, ce paramètre sera la *taille* de l'entrée,
par exemple pour un algorithme qui trie un tableau de nombre, le
paramètre pourra être la taille du tableau.

Les algorithmes et les autres technologies : choisir et réaliser des
algorithmes efficaces est aussi important que le choix du hardware par
exemple. De toute façon, même le hardware nécessite des algorithmes.

# Questions

- qu'attendez vous de ce livre ? De ce type de livre ? D'un livre en
  general ?

## NP-difficile vs NP-complet :

En théorie de la complexité, un problème NP-complet est un problème de
décision, c'est à dire dont la réponse peut-être *oui* ou *non*
vérifiant les propriétés suivantes :

- Il est possible de vérifier une solution efficacement (en temps
  polynomial) ; la classe des problèmes vérifiant cette propriété est
  notée NP ;
- Tous les problèmes de la classe NP se ramènent à celui-ci via une
  réduction polynomiale ; cela signifie que le problème est au moins
  aussi difficile que tous les autres problèmes de la classe NP.

Un problème NP-difficile est un problème qui remplit la seconde
condition, et donc peut être dans une classe de problème plus large et
donc plus difficile que la classe NP.

Exemple de problème NP : étant donné un graphe, est-il possible de
parcourir tous les noeuds du graphes sans passer deux fois par le même
noeud ? Ce problème est aussi connu sous le nom de *chemin
hamiltonien*.

## Complexité

Complexité :

- Quid des performances -> bien comprendre que complexité et
  performances sont des notions différentes (théorie vs pratique),
- Importance de la complexité en espace.
- voir les coûts en consommation d'énergie.
