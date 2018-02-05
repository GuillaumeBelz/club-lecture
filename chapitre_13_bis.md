
# Annexe A - Concurrence II

## Exemple client/serveur

equilibre usage CPU et reseau

En revanche, si le traitement est limité par les entrées/sorties, la concurrence peut améliorer l’efficacité. 
Pendant qu’une partie du système attend que les entrées/sorties soient disponibles, une autre partie peut en 
profiter pour effectuer une autre opération et ainsi employer plus efficacement le processeur. ???

Ajouter des threads
Observations concernant le serveur

- gestion de la connexion par socket ; 
- traitement du client ;
- stratégie de gestion des threads ;
- stratégie d’arrêt du serveur.

le code traverse allègrement plusieurs niveaux d’abstraction différents > ????
la gestion des threads doit se trouver en quelques endroits parfaitement maîtrisés > ???

A faire a priori ???

## Chemins d’exécution possibles

n = (NT)! / N!^T


