
# Histoire du C++ : Thriving in a Crowded and Changing World: C++ 2006–2020 (BJARNE STROUSTRUP)

Resume : livre accessible gratuitement en ligne. Publie en 2020. Histoire du C++. Description des fonctionnalites sur C++11, C++14,
C++17 et C++20. Orientation pour le future.

## Citations et commentaires

### Les principes de base du C++

Qui expliquer pourquoi les fonctionnalites du C++ sont concues telles qu'elles le sont.

> It retains its dual focus on:
> - Direct mapping of language constructs to hardware facilities
> - Zero-overhead abstraction
> This combination is the defining characteristic that sets C++ apart from most languages. "Zero overheadž was explained like this" [Stroustrup 1994]:
> - What you don’t use, you don’t pay for (aka "no distributed fat").
> - What you do use, you couldn’t hand-code any better.

## Pourquoi le C++ evoluent lentement ?

A cause des demandes contradictoires :

> three contradictory demands:
> - Make the language simpler!
> - Add these two essential features now!!
> - Don’t break (any of) my code!!!

## Une definition originale de new et delete

Ces fonctions ne servent pas juste a "creer et detruire un objet", mais creer un contexte (un ensemble ferme, qui contient un etat - ensemble
de valeurs/infos -, et qui communique avec d'autres contexts - au moins le context parent) d'execution pour les variables membres.

Exemple de "contextes" : un logiciel dans un systeme d'exploitation, un module, un layer dans une architecture multi-couche, 
une fonction, un objet, un bloc de code.

> From my 1979 lab book:
> - A "new function" creates the run-time environment for member functions
> - A "delete function" reverses that
