
> En cours de redaction

# Chapitre 13 - Concurrence

Idée de la concurrence : Stratégie de découplage entre les actions réalisées et le moment où elles sont réalisées. Le fait d'avoir plusieurs piles sémantiques (plusieurs "programmes") avec une part de mémoire partagée permet d'effectuer des tâches différentes potentiellement en même temps. On peut avoir des systèmes ou plusieurs programmes coopèrent à résoudre une tâche plus globale. On peut gagner en organisation ou encore en performances.

"Il est difficile, même très difficile, d’écrire des programmes concurrents propres."

"en apparence, semble parfait, mais qui soit défectueux à un niveau plus profond."

## Raisons de la concurrence

- lien fort entre quoi et comment

### Mythes et idées fausses

Faux :

- La concurrence améliore toujours les performances.
- L’écriture de programmes concurrents n’a pas d’impact sur la conception.
- La compréhension des problèmes liés à la concurrence n’est pas importante lorsqu’on travaille 
avec un conteneur comme un conteneur web ou EJB.

Vrai :

- La concurrence implique un certain surcoût
- Une bonne mise en œuvre de la concurrence est complexe
- Les bogues de concurrence ne sont généralement pas reproductibles
- La concurrence implique souvent un changement fondamental dans la stratégie de conception.

## Se prémunir des problèmes de concurrence

### Principe de responsabilité unique

- Le code lié à la concurrence possède son propre cycle de développement
- Le code lié à la concurrence présente ses propres défis
- Les causes de dysfonctionnement du code concurrent mal écrit suffisent amplement à compliquer son écriture

### Corollaire : limiter la portée des données

Avoir un maximum de localité pour les données évite d'augmenter la quantité de code susceptible de créer des problèmes de concurrence. Les données accessibles à un thread ne doivent être (logiquement) accessibles par personne excepté le thread, sauf pour les structures de données concurrentes qui doivent renforcer une telle encapsulation.

utiliser le mot-clé synchronized pour protéger une section critique du code qui utilise l’objet partagé

risques :

- Vous oublierez de protéger un ou plusieurs de ces endroits
- Vous devrez redoubler d’efforts pour vous assurer que toutes les protections sont bien en place
- Il sera difficile de déterminer les sources de dysfonctionnements

### Corollaire : utiliser des copies des données

A l'entrée des structures concurrentes, forcer la copie permet d'empêcher un thread externe de créer un partage non voulu.

- copies + map-reduce

### Corollaire : les threads doivent être aussi indépendants que possible

## Connaître la bibliothèque

### Collections sûres vis-à-vis des threads

Concurrent Programming in Java [Lea99] et "java.util.concurrent"

autres : ReentrantLock, Semaphore, CountDownLatch

## Connaître les modèles d’exécution

- Ressources bornées
- Exclusion mutuelle 
- famine
- Interblocage (deadlock)
- Interblocage actif (livelock)

### Producteur-consommateur

https://fr.wikipedia.org/wiki/Probl%C3%A8me_des_producteurs_et_des_consommateurs

### Lecteurs-rédacteurs

https://fr.wikipedia.org/wiki/Probl%C3%A8me_des_lecteurs_et_des_r%C3%A9dacteurs

### Dîner des philosophes

https://fr.wikipedia.org/wiki/D%C3%AEner_des_philosophes

## Attention aux dépendances entre des méthodes synchronisées

Recommandation : évitez d’utiliser plusieurs méthodes sur un objet partagé.

- Verrouillage basé sur le client
- Verrouillage basé sur le serveur
- Serveur adapté

## Garder des sections synchronisées courtes

Recommandation : conservez des sections synchronisées les plus courtes possible. Cela permet entre autre d'avoir un code concurrent plus simple (car moins long à lire et comprendre) mais surtout d'éviter de bloquer tout le monde pendant trop longtemps ce qui ruine les performances.

## Écrire du code d’arrêt est difficile

Il existe un risque important qu'un thread soit en attente de quelque chose et qu'il ne reçoive jamais le signale d'arrêt.

## Tester du code multithread

Il est peu réaliste de vouloir prouver que du code est correct. # Kass'peuk

- Considérer les faux dysfonctionnements comme des problèmes potentiellement liés au multithread
- Commencer par rendre le code normal opérationnel
- Faire en sorte que le code multithread soit enfichable
- Faire en sorte que le code multithread soit réglable
- Exécuter le code avec plus de threads que de processeurs
- Exécuter le code sur différentes plates-formes
- Instrumenter le code pour essayer et forcer des échecs, manuel et/ou automatique

## Questions

- lire l'annexe A lundi prochain ?
- alternative a la programmation concurrente ? events, agents, atomic, signaux-slots, etc.
- plus generalement, structures et algos concurrents ?
- concurrence et conception, methodes pour eviter d'avoir a tout repenser ? Framework de concurrence
- copies de donnees : prog fonctionnelle, données non mutable
- depuis Java 5 ? Autres langages
- modèle memoire et concurrence
- tester du code multithread : mais si pas reproductible, a quoi ca sert ? Quoi faire ? Prioritaire ?
- enseignement de la programmation concurrente 
- http://diy.inria.fr/herd/herding-cats-bw.pdf
- http://ceur-ws.org/Vol-1639/paper-04.pdf
- https://en.wikipedia.org/wiki/Bulk_synchronous_parallel
- https://rephrase-eu.weebly.com/

![Java vs C++](http://img.ibxk.com.br/ns/rexposta/2015/03/07/07115101647000.gif)
