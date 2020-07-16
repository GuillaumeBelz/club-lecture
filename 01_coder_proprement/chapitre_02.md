
> Merci à Ksass'Peuk pour ce resumé.

# Chapitre 2 - Noms significatifs

Le but de ce chapitre est d'établir un certain nombre de règles simples pour
avoir un bon nommage des différents éléments d'un programme (variables,
fonctions, classes, etc).

Les différents points abordés par ce chapitre sont :

- noms révélateurs d'intentions
- éviter la désinformation
- faire des distinctions significatives
- choisir des noms prononçables
- choisir des noms compatibles avec une recherche
- éviter la codification
- éviter les associations mentales.
- noms des méthodes
- noms des classes
- ne pas faire le malin
- choisir un mot par concept
- éviter les jeux de mots
- choisir des noms dans le domaine de la solution
- choisir des noms dans le domaine du problème.
- ajouter un contexte significatif
- ne pas ajouter de contexte inutile

## Noms révélateurs d'intentions

Un bon nom doit exprimer, pour l'élément qu'il nomme :

- la raison de son existence,
- son rôle,
- son utilisation.

Typiquement, s'il y a besoin d'un commentaire pour expliquer cela, le nom est
mauvais. Non seulement il est important de trouver un bon nom mais il faut
être prêt à changer quand on en trouve un meilleur.

Une nouvelle fois le point crucial est de révéler les intentions du code.
Le problème n'est généralement pas dans la trop importante simplicité du code
mais plutôt dans la quantité d'informations implicites qu'il renferme, cela
implique du lecteur la connaissance d'informations qui ne sont pas expliquées
par le code.

Exemples typiques :

- signification de valeur numériques en dur dans le code,
- signification d'un indice pour un tableau,
- manière particulière d'utiliser une variable ou une fonction.

## Éviter la désinformation

Le nom ne doit pas risquer de détourner le sens du code. Mieux vaut éviter,
par exemple d'utiliser un mot comme "liste" dans un nom si on ne désigne pas
précisément une liste (qui a un sens particulier en programmation).

Il faut également faire attention à ne pas utiliser des noms trop proches qui
peuvent induire en erreur car l'on ne remarque pas immédiatement les différences
qui peuvent apparaître.

Un bon nom implique que l'on n'a pas la nécessité d'aller voir les commentaires
avant d'auto-compléter un nom (et pas le besoin d'aller voir une liste de
fonctionnalités proposées par exemple).

Caractères prise de tête si mal utilisés:

- "o" majuscule (facilement confondu avec zéro)
- "L" minuscule (facilement condondu avec un)

## Faire des distinctions significatives

Modifier un nom pour le compilateur, c'est aller aux devants de problèmes.
Exemple typique : renommage d'une variable "qui a le même sens" qu'une autre
pour éviter le conflit de nom. Si les variables ne sont pas les mêmes, elles
n'ont nécessairement pas le même sens.

Mauvaises pratiques :

- introduction de faute volontaire dans un mot pour le différencier,
- utilisation de numéros,
- utilisation de mots parasites.

Généralement, on ne provoquera pas de désinformation mais au minimum, on
n'exprime pas clairement les intentions du code.

Le mots comme "info" ou "data" ne sont pas précis. Difficulté par exemple de
différencier correctement "MachinData" et "Machin", rendant difficile le fait
de savoir laquelle des deux on doit utiliser pour obtenir une information
particulière quand on utilise l'une ou l'autre.

Conseil : ne jamais mettre le mot variable dans le nom d'une variable, ou
array dans un tableau, ou string dans une chaîne, etc.

## Choisir des noms prononçables

Besoin dû principalement au fait que notre cerveau est câblé pour mieux
manipuler des choses prononçable. Cela permet entre autre d'avoir une
conversation intelligible avec une autre personne.

## Choisir des noms compatibles avec une recherche

Éviter par exemple les noms d'une seule lettre et ou les constantes numérique,
qui sont difficiles à rechercher dans un texte. Par ailleurs l'inversion de
chiffres dans une grande constante peut rendre cette constante impossible à
détecter.

La longueur d'un nom doit correspondre à la taille de sa portée.

Plus le nom est susceptible d'être recherché à plusieurs endroit, plus il doit
être facile à rechercher.

## Éviter la codification

La codification doit être apprise, ce qui est une charge de travail inacceptable
quand on doit déjà se taper l'apprentissage de la base de code sur laquelle on
arrive. D'autant que les noms codifiés sont souvent imprononçables et sujets
aux erreurs de saisies.

### Notation hongroise

Importante dans l'API C Windows, créée à un moment où la vérification de type
était pour ainsi dire inexistante, et que l'on avait besoin d'un mécanisme
explicite dans le nommage pour mémoriser les types.

Ce n'est plus le cas aujourd'hui, la plupart des langages étant fortement typés
ou inversement, certains langages rendant la distinction de type généralement
inutile.

Bref : la notation hongroise, aujourd'hui, ne sert plus à rien.

### Préfixe des membres

Préfixage "m_" pour les membres inutile : les classes et fonctions doivent être
assez courtes pour qu'une telle disctinction soit inutile. Ce préfixe
représenterait alors un foullis inutile.

### Interfaces et implémentations

Mieux vaut éviter de commencer une interface avec "I". Au choix, il est plus
pertinent de signaler une implémentation (par un suffixe "Imp" par exemple).

## Eviter les associations mentales.

C'est le problème des noms qui sont insuffisamment explicites au sens où le
développeur doit faire lui même un effort pour réassocier le nom à un autre nom
plus explicite correspondant au concept réel.

Exemple : initiales de plusieurs mots que le développeur doit lui même réassocier
à ces mots pour finalement atteindre le concept.

## Noms des classes

Nommer les classes par des groupe nominaux (pas de verbe).

Éviter les mots trop généraux comme : Manager, Processor, Data, Info, etc.

## Noms des méthodes

Choisir des mots auquels on s'attend :

- get pour recevoir de l'information,
- is pour exprimer un prédicate,
- etc.

## Ne pas faire le malin

Éviter l'humour lorsque l'on nomme des éléments d'un programme. Si la blague est
oubliée, cela peut porter à confusion. Dites ce que vous pensez, et pensez ce que
vous dites.

## Choisir un mot par concept

Et s'y tenir ! Typiquement éviter de faire cohabiter : fetch, retrieve et get.
Les noms doivent être autonomes et cohérent, si les concepts sont similaires,
les écritures de ces concepts doivent être simulaires, et inversement.

Cela constitue le lexique du programme et il ne doit pas perturber le lecteur.

## Éviter les jeux de mots

Lorsqu'un mot peut avoir deux sens différents, mieux vaut le bannir. Par exemple
lorsque le concept est semblable mais agit de manière sensiblement différente,
mieux vaut choisir un autre mot.

## Choisir des noms dans le domaine de la solution

Le domaine du problème n'est généralement pas le domaine des développeurs du
code. Mieux vaut choisir des mots qui sont dans le domaine de la solution (donc
typiquement des termes informatiques).

## Choisir des noms dans le domaine du problème

Lorsque le concept n'appartient PAS au domaine informatique, ne pas essayer de
simplifier et vulgariser. Mieux vaut utiliser le terme technique exacte du
problème pour pouvoir faire appel à un expert du domaine le cas échéant.

## Ajouter un contexte significatif

La plupart des noms ne sont pas significatifs en l'état. Il faut leur redonner
un contexte à travers des classes, fonctions ou espaces de noms appropriés. Voir
d'ajouter un préfixe en dernier ressort.

## Ne pas ajouter de contexte inutile

Éviter de mettre de l'information redondante (le nom de l'application elle-même
par exemple) ou hors de propos (distinctions adresse postale d'un client ou d'un
fournisseur).

## Mots de la fin

Le choix des noms est difficile et nécessite

- une bonne aptitude à décrire,
- une culture générale partagée,
- un bon enseignement.

Beaucoup de développeurs ont peur du renommage, mais nous ne mémorisons
généralement pas réellement les noms dans un programmes. Nous les traitons et
les oublions quand nous avons fini de travailler sur une zone particulière du
programme.

# Questions abordés pendant les discussion

Nous avons globalement eu moins de discussions pendant cette séance, le chapitre
énonçant finalement des usages qui sont déjà assez fortement présents chez les
développeurs pros.

## Q1: Point de désaccord sur la présence de mots comme "list" dans un nom

Par exemple pour distinguer un élément d'une collection VS une collection
elle-même. D'un côté l'utilisation du pluriel peut parfois être dure à
remarquer. D'un autre côté, l'ajout d'autres mots "parasites" comme "group_of"
ou "bunch_of" conduit à de l'imprécision. Au cas par cas, cette règle peut
sembler un peu forte.

## Q2: Choix des noms prononçables, portage de vieux code

Certains code dans des langages comme Cobol imposent des contraintes fortes
sur le nommage des variables qui ont souvent mené à des dérives comme des
noms composés quasi-exclusivement d'initales et de chiffres. Ces noms
imprononçables sont très généralement source de confusion, lors d'un portage
mieux vaut complètement renommer ces éléments.

## Q3: Point sur la codification VS la création d'un lexique

Ne pas confondre l'utilisation d'un lexique commun et la codification. Si
l'importance du lexique devient telle que l'apprendre et le comprendre n'est
plus triviale alors ce lexique tire vers la codification ce qui est une
mauvaise chose.

## Q3b: notation hongroise

Cette notation a en plus le défaut de ne pas être robuste à la maintenance,
si l'on change légèrement le typage des éléments, on peut se retrouver à
devoir changer le nom de la variable alors que son utilisation et son sens
n'ont pas changé.

## Q4: Contexte de noms : les espaces de noms

Les espaces de noms sont très utiles pour organiser les éléments d'un
programme cependant tous les langages ne possèdent pas la même notion d'espace
de nom (pas le même contexte d'utilisation et pas le même impact sur le code),
et même la présence d'un tel mécanisme ne garantit pas que les développeurs
vont l'utiliser.

Pour comparaison, on peut prendre la notion d'espace de noms à la C++ et la
notion de package à la Java. Java y définit une notion de  visibilité, ce qui
n'est pas le cas de C++, et malgré le fait que cette notion d'espace de nom
permettent de donner plus de sens au code (par la visibilité justement), cette
notion ne semble pas être si utilisée par la communauté Java.
