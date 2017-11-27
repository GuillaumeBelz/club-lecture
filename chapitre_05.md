
# Mise en forme

l’élégance, la cohérence et l’attention portée aux détails

règles simples, les appliquer systématiquement

## Objectif de la mise en forme

important, moyen de communication

"faire en sorte que cela fonctionne" n'est pas la priorité: fonctionnalites changent, lisibiltie du code a un impact sur les modifications, facilite de maintenance et extension du code

etablir un precedent

## Mise en forme verticale

tres variables, quelques dizaines de lignes a plusieurs milliers

taille des fichiers pas forcement en relation avec la taille des projets

Petits fichiers plus simples a comprendre

- Métaphore du journal -> du plus haut niveau vers les details
- Espacement vertical des concepts -> ligne vide pour separer les concepts
- Concentration verticale -> ne pas separer les memes concepts ensemble (commentaires, lignes vides, etc)
- Distance verticale -> regrouper les concepts verticalement, regrouper dans un meme fichier si cela a du sens. Variables protegees a eviter ?

## Déclarations de variables

déclarées au plus près de leur utilisation. 

Rare cas d'exception ?

## Variables d’instance

Java: au debut de la classe. C++: a la fin. 

## Fonctions dépendantes

proches verticalement, appelant avant appellees

## Affinité conceptuelle

appelant/appeleees, functions qui realisent une operation semblable

## Rangement vertical



# Mise en forme horizontale

80 caracteres arbitaires, mais conserver des lignes pas trop longue (100, voire 120)

## Espacement horizontal et densité

espace dans une ligne

operateur d'affectation = 1 espace
appel de fonction = pas d'espace
espace apres virgule
addition et soustraciton = espace, multiplication et division = pas d'espace
==> basé sur les regles typographiques ?

## Alignement horizontal

auteur prefere non aligné

## Indentation

hiérarchisation

permet de lire rapidement par blocs de code

==> python obligatoire

## Rompre l’indentation

auteur ne prefere pas le code sur une ligne

## Portées fictives

preferer des accolades vides plutot qu'un point virgule seul



# Règles d’une équipe

suivre les regles de l'equipe

rester coherent




# questions

> outils de formatage ? clang-format, git hook
> separer commit mise en forme et changement dans le code ?

> est ce que les styles de codage de Lynix sont les pires ou il est possible de faire pire ?

==> C++: meme ordre que interface ? 
==> A qui est destinee la declaration de la classe ? Au l'utilisateur = mettre dans l'ordre public, protected et private
==> Java: pas de separation interface/implementation. Fichier destinee aux utilisateurs et concepteurs de la classe. C++ = separation

==> guides par equipes

