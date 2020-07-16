
Séance du 15 juillet 2020

Points importants :

- plusieurs caracteristiques essentielle : temps de reponse, latence, nombre de cores, synchronisation, parallelisme
- pas de meilleure algo et structure de donnees dans l'absolue, cela depend de quelle partie de l'ordi le code est 
  effectivement executé (un core du CPU, le SIMD du CPU, le GPU, les memoires caches, les registres, le GPU, etc)
- en premiere intention, faire confience au compilo. Puis mesurer. Si on trouve des problemes d'algos et structures de données,
  corriger cela et laisser le compilo optimiser ce qu'il peut. Puis mesurer. Et si on trouve encore des optis pertinentes (ie
  avec un gain significatif), alors seulement, on peut passer a des optis manuelles
  
Chapitres :

- 01 : les fondamenteux de l'analyse et du design, qu'est-ce que l'on va mesurer (performances, couts, puissance consommée, etc).
- 02 : les hiérarchies de mémoire. Plusieurs types de mémoires, que l'on peut classer en fonction de leur temps d'accès et leur débits.
- 03 : le paralélisme des instructions. Dans un processeur moderne, les instructions prennent du temps à être executée, donc plusieurs
  instructions sont executé en même temps (un peu en décalées) pour gagner du temps.
- 04 : le parallélisme des données, pour optimiser lorsqu'on doit réaliser le même calcul plusieurs fois sur des données différentes.
- 05 : le parallélisme des threads. Quand plusieurs cores doivent travailler sur des données partagées, utilisation des mémoires caches.
- 06 : les fermes d'ordinateurs, pour le calcul distribué, le cloud, internet, etc.
- 07 : les architectures spécifiques à un domaine, qui permet de concevoir une architecture optimisées pour réaliser une tâche en particulier,
  plutôt que pouvoir réaliser n'importe quelle tâche généraliste.
  
Les annexes seront probablement lues en même temps que les chapitres correspondants. Annexes :
  
  - A : les jeux d'instructions, pour faire l'intermédiaire entre le code que l'on écrit et le matériel.
  - B : Vue d'ensemble des hiérarchie de mémoire.
  - C : le concept de pipeline.

Les annexes suivantes ne sont pas dans le livre, mais uniquement en pdf. Vous pouvez les télécharger sur le site de l'éditeur :
https://www.elsevier.com/books-and-journals/book-companion/9780128119051
