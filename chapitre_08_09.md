# Limites

Deux types de limites :
  - le code tiers que l'on importe
  - le code pas encore écrit
  
## Le code tiers.

  - pas nécessairement parfaitement adapté à notre tâche
  - n'évolue pas forcément dans le sens que l'on recherche

Idéalement : enfermer le code tiers derrière une API correspondant à 
la tâche que nous souhaitons réaliser. Cela robustifie la conception
aux changements du code tiers.

Par conséquent, on doit écrire des tests pour le code tiers :

  - pour le prendre en main,
  - pour remarquer les moments où il ne fait plus ce que l'on veut.
  
## Le code pas encore écrit.
 
Moment où une partie du logiciel n'est pas encore développée.
  
Définir l'interface que l'on voudrait de ce code. Il sera généralement
assez aisé de l'adapter le jour où elle sera disponible.

# Tests unitaires

Chapitre fortement lié au TDD

## Trois lois

  - pas de code de prod avant le test d'échec,
  - écrire seulement le test unitaire suffisant pour échouer,
  - écrire seulement le code suffisant pour faire réussir le test.

## Objectif

On veut écrire du code qui soit testable parce que l'on a en tête
le test que l'on cherche à valider. Cela évite de ne pas savoir écrire
le test qui correspond à un code que l'on vient d'écrire parce qu'on ne
sait pas comment le tester.

Cela permet virtuellement une couverture parfaite du code.

## Tests propres

Les tests doivent rester propre pour rester utilisable. Si les tests
sont sales, il finit par être difficile de savoir si un problème est dû
aux tests ou au code. Résultat : les tests deviennent un handicap.

Avoir des tests implique d'avoir un filin de sûreté : on n'a pas peur
de modifier le code parce qu'on sait que les tests nous donneront des
informations pertinentes en cas de soucis.

Test propre :

  - LISIBLE,
  - doit montrer les intentions (encore), donc ne doit pas être pollué
    par des détails inutiles,
  - ne répond pas aux mêmes contraintes que le code de prod, notamment
    sur le plan des performances
  - une assertion par test (format prémisses -> conclusion)
  - un seul concept par test (revient à l'absence de pollution)
  
## FIRST

 - Fast : tests rapides,
 - Independent : pas de dépendances entre tests pour éviter les 
   diagnostiques difficiles,
 - Repeatable : si le test n'est pas reproductible, il n'est pas très 
   pertinent
 - Self-validating : résultat = échec ou réussite, sinon l'analyse 
   demande une intervention,
 - Timely : tests écrits juste avant le code qui correspondant
  
  
# Discussion - Limites

Les codes de tests de prise en main :

  - plutôt expérimenter dans un autre projet,
  - besoin dépendant de la taille de la lib,
  - si on dépend d'un framework, c'est très difficile : c'est généralement
    très intrusif.
	
Difficulté à faire évoluer les libs ?

  - Ex : dépendance à .Net
  - dépendance à des APIs REST ? 
    -> la manière de créer l'API à un impact très fortement
	-> distinction forte entre celles que l'on maîtrise et les autres
	
# Discussion - Tests unitaires

Philosophie de l'entreprise : investissement dans les tests.

Conseiller les décideurs :

  - estimer les coûts,
  - estimer les conséquences

Formation technique des décideurs ?

  - parfois difficile de séparer les types de tests entre unitaires, intégration, ...
  - problème de fainéantise des développeurs ?

Outils :

  - design de tests par contrat
      - génération automatique dirigée par le code
	  - génération automatique dirigée par les langages
	
TDD : pas si utilisée ?

Les coûts à long terme doivent être estimés mais c'est parfois difficile.
Les systèmes à longs termes marchent mieux pour les tests et la maintenance ?
On a tendance à tester les cas auxquels on s'attend

Fuzzer et reproductibilité -> écrire le test qui correspond fuzzing.
Reproductibilité : la concurrence peut vraiment poser des problèmes.
  
  - parallélisme
  - réseaux, base de données (mais peut être moins unitaires)
