
# Annexe A - Concurrence II

## Exemple client/serveur

On note que la question immédiate est de savoir si la raison de la lenteur est la vitesse de calcul ou les entrées sorties (dans le premier cas, on est plus rapidement limité en accélération).

equilibre usage CPU et reseau

En revanche, si le traitement est limité par les entrées/sorties, la concurrence peut améliorer l’efficacité. 
Pendant qu’une partie du système attend que les entrées/sorties soient disponibles, une autre partie peut en 
profiter pour effectuer une autre opération et ainsi employer plus efficacement le processeur. ???

Le premier choix est de lancer un thread par client, le choix est discutable parce que cela peut lancer beaucoup de threads, mais surtout parce que l'on a pas de contrôle sur le scheduling et parce que la classe a un gros paquet de responsabilité.

On montre ensuite comment séparer la partie scheduling dans une classe dédiée à laquelle on poste les demandes de connexions, il est ensuite facile de changer le scheduler.

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

Le bytecode généré par le programme en question est surprenant. Il y a beaucoup d'instructions, et certaines paraissent moyennement raisonnables. On a ensuite la présentation du calcul du nombre de chemin qui revient simplement à déterminer le nombre de permutations.

n = (NT)! / N!^T

## Résultat surprenant : deux threads ==> augmentation de 1 seulement.

Ce problème est simplement dû au fait que les lectures et écritures ne sont pas atomiques et donc on peut avoir deux threads qui lisent la même valeur et font leur écriture avec la même valeur à nouveau (car même incrément).

[NOTE]: En réalité la situation peut être bien pire, le langage Java, comme les autres langages un peu raisonnables, autorise les comportements faibles.

# Connaître sa bibliothèque.

[PAS DANS LE LIVRE]
## New-IO

Regarder de plus près.
Basé sur une technique de polling, permet de s'affranchir des threads lorsque l'on fait des IOs.
[FIN]

## Executor

Présentation succincte du framework Executor qui permet de poster un certain nombre de tâches à réaliser dans un pool. Il décharge ensuite les tâches postées (notamment en permettant d'implémenter la notion de futures).

## Non blocking atomic operation

Présentation des opérations comme compare_and_swap ou fetch_and_add qui permettent de réaliser un certain nombre d'opérations atomiques. On peut se référer à compare and swap qui est basiquement : si la variable que je veux set à la valeur recherché, écrire atomiquement la valeur voulue, sinon renvoyer la valeur trouvée.

## Présentation ultra-succintes de quelques collections sûres

Lorsque l'on a besoin d'utiliser des éléments non-sûrs, 

- on peut synchroniser côté client, 
[Note]: ce qui est généralement une bombe à retardement
- faire une classe wrapper
- utiliser une classe safe équivalente
[pas dans le livre] - Possibilité de créer un objet synchronisé à partir d'un objet pas synchronisé.

# Impact des dépendances entre méthodes.

Présentation d'un exemple où de multiples appels provoquent des interférences principalement dus au fait que l'on peut reposer sur une connaissance qui est rapidement invalide.

[Note]: C'est l'invariant de la classe qui ne tient pas trop la route. On ne peut pas reposer sur le fait que la connaissance est toujours valide. 

- Tolérer la panne

Technique de sagouin.

- Verrouillage côté client

On présente l'opération a possibilité d'échec qui devrait en fait être encapsulée.

- Verrouillage côté serveur

On introduit la possibilité d'échouer pour l'opération next. Ici, c'est réalisé à travers un adapteur, qui peut être une bonne manière de transformer un objet non-safe en objet safe.

# Augmenter le débit

Présente simplement une manière d'estimer les gains en multi-thread, mais la technique n'est pas très réaliste. Dans l'idée : on calcule le chevauchement maximum que l'on peut avoir entre IO et calcul et on obtient un temps minimum.

# Interblocage

Condition d'un interblocage :

- exclusion mutuelle : même ressources (en quantité limitée) pour différents threads qui ne peuvent pas être utilisées en même temps,
- détention et attente : on obtient une ressource et on en attend d'autre sans libérer,
- pas de préemption : on ne peut pas piquer une ressource à un thread,
- attente circulaire : T1 a pris R1 et veut R2, T2 a pris R2 et veut R1.

## Briser l'exclusion mutuelles

- ressource simultannées,
- augmenter le nombre de ressources,
- vérifier que tout est libre avant de prendre.

## Briser la détention et l'attente

On peut refuser l'attente, mais on a alors risque de famine ou livelock.

## Briser la préemption

Système de requête pour demander les ressources occupées. On a quasiment les mêmes risques pour avant.

## Briser la circularité

On évite l'interblocage par la mise en place de stratégie qui cassent les cycles. Par exemple en prenant toujours les ressources dans le même ordre.

# Tester du code MT

BOF, beaucoup d'aberrations.

Framework de test permettant de simuler le scheduling.

https://deadlockempire.github.io/

What about Pony ?
