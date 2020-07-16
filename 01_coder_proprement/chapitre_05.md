
# Mise en forme

l’élégance, la cohérence et l’attention portée aux détails

règles simples, les appliquer systématiquement

## Objectif de la mise en forme

important, moyen de communication

"faire en sorte que cela fonctionne" n'est pas la priorité: fonctionnalités changent, lisibilité du code a un impact sur les modifications, facilité de maintenance et extension du code

établir un précédent 

## Mise en forme verticale

très variables, quelques dizaines de lignes a plusieurs milliers

taille des fichiers pas forcément en relation avec la taille des projets

Petits fichiers plus simples à comprendre

- Métaphore du journal -> du plus haut niveau vers les details
- Espacement vertical des concepts -> ligne vide pour séparer les concepts
- Concentration verticale -> ne pas séparer les mêmes concepts ensemble (commentaires, lignes vides, etc)
- Distance verticale -> regrouper les concepts verticalement, regrouper dans un même fichier si cela a du sens. 
Variables protégées a eviter ?

## Déclarations de variables

déclarées au plus près de leur utilisation. 

Rare cas d'exception ?

## Variables d’instance

Java: au début de la classe. C++: a la fin. 

## Fonctions dépendantes

proches verticalement, appellant avant appellées

## Affinité conceptuelle

appelant/appelées, fonctions qui réalisent une opération semblable

## Rangement vertical

# Mise en forme horizontale

80 caractères arbitraires, mais conserver des lignes pas trop longue (100, voire 120)

## Espacement horizontal et densité

espace dans une ligne

- operateur d'affectation = 1 espace
- appel de fonction = pas d'espace
- espace apres virgule
- addition et soustraction = espace, multiplication et division = pas d'espace

## Alignement horizontal

auteur préféré non aligné

## Indentation

hiérarchisation

permet de lire rapidement par blocs de code

==> python obligatoire

## Rompre l’indentation

auteur ne préfère pas le code sur une ligne

## Portées fictives

préférer des accolades vides plutot qu'un point virgule seul

# Règles d’une équipe

suivre les règles de l'equipe

rester coherent

# questions

- outils de formatage ? clang-format, git hook

séparer commit mise en forme et changement dans le code ?

- C++: meme ordre que interface ? 

A qui est destinée la déclaration de la classe ? Au l'utilisateur = mettre dans l'ordre public, protected et private

Java: pas de separation interface/implementation. Fichier destinée aux utilisateurs et concepteurs de la classe. C++ = separation

- guides par equipes 

