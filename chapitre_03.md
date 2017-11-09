
# Chapitre 3 - Fonctions



longue, code dupliqué, chaines de caracteres etranges, types de donnees, API, etc = difficile a comprendre
trop d'operations, trop de niveau d'abstraction, plusieurs niveau d'imbrication

# Faire court

"et encore plus que ca"

25l 80c. 100l, 150c.

Moins de 20 lignes. 5 lignes

bloc et indentation : pas plus de 2 niveaux

# Faire une seule chose

"UNE FONCTION DOIT FAIRE UNE SEULE CHOSE. ELLE DOIT LA FAIRE BIEN ET NE FAIRE QU’ELLE."

1 niveau d'abstraction. Creer un nouvelle fonction ne fait que changer le nom

Pas de sections

# Un niveau d’abstraction par fonction

- fonctions de la classe
- fonctiond d'autres classes
- fonction de la lib standard

Lire le code de haut en bas : la règle de décroissance

# Instruction switch

"nous employons évidemment le polymorphisme" -> langage specifique

Fabrique abstraite

# Choisir des noms descriptifs = chapitre 2

principe de Ward : "Vous savez que vous travaillez avec du code propre lorsque chaque 
fonction que vous lisez correspond presque parfaitement à ce que vous attendiez."

nom long > nom court

# Arguments d’une fonction

ideal = 0, 1 ou 2 = ok, plus de 3 = a eviter

preferer passer une variable comme membre, plutot que comme argument <= purete fonctionnelle ?

Difficulite pour tester <= encore plus dur de tester un etat interne ?

prefere retour de fonction plutot que argument de sortie. <= optional, monade, gestion d'erreur

- Formes unaires classiques : retourner un bool ou un objet. Evenement = specifique a java?

- Arguments indicateurs : a eviter

- fonction diadique <= opposition fonction membre ou non, langage specifique

assertEquals(expected, actual) : ordre des parametres ? <= parametres nommé?

- Fonctions triadiques : cumul de problemes

- Objets en argument : concept qui mérite son propre nom

- Listes d’arguments (string.format)

- Verbes et mots-clés

assertExpectedEqualsActual(expected, actual) au lieu de assertEquals(expected, actual)

# Éviter les effets secondaires

fait également d’autres choses cachées dans la classe ou dans les membres <= const, passage par valeur, purete fonctionnelle

couplage temporel

faire une chose ?

- Arguments de sortie : utilisation des membres. A proscrire, utiliser this pour la sortie

# Séparer commandes et demandes

Une fonction doit modifier l’état d’un objet ou retourner des informations concernant cet objet

if (set("nomUtilisateur", "OncleBob"))... <= isSet, tester si un objet est valid. etentre le scope. C++17 declaration dans if. Pointeur C/C++

if (attributeExists("nomUtilisateur")) { 
    setAttribute("nomUtilisateur", "OncleBob"); ...
} <= verbosite


# Préférer les exceptions au retour de codes d’erreur

violation subtile de la séparation des commandes et des demande

- Extraire les blocs try/catch <= séparation élégante ???

- Traiter les erreurs est une chose

- L’aimant à dépendances Error.java. Probleme de dependances

# Ne vous répétez pas

DRY, plus de code = plus d'erreurs

# Programmation structurée

Dijkstra : chaque fonction, et chaque bloc dans une fonction, doit posséder une entrée et une sortie

# Écrire les fonctions de la sorte


# Questions

apprendre de l'experience?

object vs fonctionnel. parametre vs membre. Typage fort

