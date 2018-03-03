
**Introduction to Algorithms (Third Edition)**

# Preface

Chaque chapitre presente un algorithme, une technique de conception, un domaine d'application, ou un un sujet connexe.

Des solutions aux exercices sont en ligne : http://mitpress.mit.edu/algorithms/

# Introduction

Résumé des chapitres de la première partie :

- 01 : vue d'ensemble et definition de ce qu'est une algorithme. Quelques exemples, quelques domaines.
- 02 : premiers algorithmes, sur le tri d'une séquence de n nombres : les tri par insertion (*insertion sort*) et tri fusion (*merge sort*), et la technique "Diviser pour régner" (*divide-and-conquer*).
- 03 : 
- 04 : 
- 05 : introduction à l'analyse probabiliste et aux algorithmes aléatoires. 
- annexes A à D : compléments mathématiques.

# Les algorithmes

## Généralités

Procédure formelle de calcul qui reçoit en entrée des valeurs et produit
en sortie des valeurs. Suite d'opération qui transforme les entrées en 
sorties.

Outils pour résoudre des problèmes de calcul, défini en termes généraux
NOTE: le problème peut être formellement défini aussi.

Algorithme correct : pour toute instance d'entrée, il donne la sortie
attendue. Les algorithmes incorrects ne sont pas nécessairement inutiles
si le taux d'erreur est contrôlé par exemple.

Les algorithmes ont souvent beaucoup de solution candidates, trouver la
bonne ou la meilleure est peut être difficile. Les algorithmes ont des
applications pratiques.

Le livre présente quelques structures de données. Il présente également
des techniques de résolution pour les cas où les algorithmes n'existent 
pas (en même temps si ça existe, on n'a pas vraiment besoin d'un dev).
Il présente également quelques problèmes NP-difficiles.

## Les algorithmes en tant que technologie

Même avec des machines infiniment rapides, on aurait quand même besoin 
d'étudier l'algorithmique, rien que pour montrer qu'un algo fonctionne
(termine, et avec la bonne solution).

Efficacité : des algorithmes différents pour un même problème peuvent
avoir une efficacité très différente. Ce que l'on mesure grâce à la 
notion de complexité, qui informe du comportement de l'algorithme en 
fonction de la taille de l'instance d'entrée.

Les algorithmes et les autres technologies: choisir et réaliser des
algorithmes efficaces est aussi important que le choix du hardware par
exemple. De toute façon, même le hardware nécessite des algorithmes.

# Questions

- qu'attendez vous de ce livre ? De ce type de livre ? D'un livre en general ?

## NP-Hard vs NP-Complete :

En théorie de la complexité, un problème NP-complet est un problème de 
décision vérifiant les propriétés suivantes :

- Il est possible de vérifier une solution efficacement (en temps 
  polynomial) ; la classe des problèmes vérifiant cette propriété est 
  notée NP ;
- Tous les problèmes de la classe NP se ramènent à celui-ci via une 
  réduction polynomiale ; cela signifie que le problème est au moins 
  aussi difficile que tous les autres problèmes de la classe NP.

Un problème NP-difficile est un problème qui remplit la seconde condition,
et donc peut être dans une classe de problème plus large et donc plus 
difficile que la classe NP.

## Complexité

Complexité :

- Quid des performances -> bien comprendre que complexité et performances sont des notions différentes,
- Importance de la complexité en espace.
- voir les coûts en consommation d'énergie.
