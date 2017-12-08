
# Chapitre 6 - Objets et structures de données

## Abstraction de données

Pour l'auteur, une classe n'est pas simplement un agrégat de données, mais impose également comment utiliser ces données
(lecture valeurs seules, écriture atomique). En cela, il distingue les classes et les structures de données.

Le but de l'encapsulation est de manipuler l’essence des données, sans avoir à en connaître l’implémentation. 
Et donc ne pas exposer les détails de nos données.

La base de ce chapitre est de faire une réflexion sérieuse sur la meilleure manière de représenter les données 
contenues dans un objet

## Antisymétrie données/objet

Les objets cachent leurs données derrière des abstractions et fournissent des fonctions qui manipulent ces données. 
Les structures de données exposent directement leurs données et ne fournissent aucune fonction significative.

Un code procédural (un code qui utilise des structures de données) facilite l’ajout de nouvelles fonctions sans 
modifier les structures de données existantes. Un code orienté objet facilite l’ajout de nouvelles classes sans 
modifier les fonctions existantes.

Un code procédural complexifie l’ajout de nouvelles structures de données car toutes les fonctions doivent être 
modifiées. Un code orienté objet complexifie l’ajout de nouvelles fonctions car toutes les classes doivent être 
modifiées.

Parfois, nous voulons réellement de simples structures de données avec des procédures qui les manipulent.

## Loi de Déméter

Un module ne doit pas connaître les détails internes des objets qu’il manipule.

Une méthode `f` d’une classe `C` ne doit appeler que les méthodes des éléments suivants :

- `C` ;
- un objet créé par `f` ;
- un objet passé en argument à `f` ;
- un objet contenu dans une variable d’instance de `C`.

Voici une exemple de code qui ne respecte pas cette loi :

```
String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath(); 
```

L'auteur qualifié un tel code, qui appel en chaîne plusieurs méthodes, de "catastrophe ferroviaire".

Les structures hybrides commulent le pire des deux monde.

### Cacher la structure

Il faut se poser la question de savoir si la solution est de retourner une structure (donc ne plus avoir de
contraintes d'accès aux membres) ou mettre toutes les methodes dans le classe qui appelle toutes ces fonctions
 en chaîne. Et pour l'auteur, la réponse est non.

Il ne faut pas demander quelque chose concernant ses détails internes, mais laisse la classe le faire. 
Il ne faut pas mélanger différents niveaux de détails (voir les chapitres précedents).

## Objets de transfert de données, DTO, Data Transfer Object

En Java, il est classique de créer des "beans" : ce sont des structures de données, avec ses membres en privée, 
un constructeur public qui prend en paramètre tous ces membres, et proposent des getters sur ces membres.

### Enregistrement actif

contient des methodes comme find ou save. Hybride

## Conclusion

ajouts de classes vs ajouts de fonctions





## Questions

- Method chaining, named parameter idiom, vs catastrophe ferroviere

```
QString("bla bla").arg(123).arg(123)
std::cout << 1 << 123 << std::endl;
```
	
- exemple de structure de donnees ? GPU. Data driven programming

- choix des differents langages ? acces aux private ? Pas d'objects, que des structures de donnees. Tuple/pair = tous les langages sont objects ?

```
struct opaque;

void f(struct opaque* o);
```






# Chapitre 7 - Gestion des erreurs

tâches indispensables dans un programme, entrée anormale, périphériques peuvent échouer
responsables du bon comporte- ment de notre code.
Le traitement des erreurs est important, mais s’il masque la logique il est mauvais.

## Utiliser des exceptions à la place des codes de retour

separation code de gestion des erreurs et le traitement des donnees

## Commencer par écrire l’instruction try-catch-finally

exception = définissent une portée à l’intérieur du programme. try = transactions (bof?)
catch doit laisser le programme dans un état cohérent, quel que soit ce qui s’est produit dans la partie try

code d'exemple = TDD
- creer le test
- creer un stub/bouchon (fonction qui n'est pas implementé, mais qui compile = le test échoue)
- implementation
- refactoring (separation try-catch-finaly)

tester les exceptions

## Employer des exceptions non vérifiées

exception verifiee = liste des throws dans la signature. Pas en C#, C++, python, ruby

violation de OCP : modificaiton de details internes (throw dans la signature) doit etre propagé aux codes appelant. cascade de modifications qui commence aux niveaux inférieurs du logiciel et remonte vers les niveaux les plus élevés

## Fournir un contexte avec les exceptions

déterminer l’origine et l’emplacement de l’erreur

## Définir les classes d’exceptions en fonction des besoins de l’appelant

classifier les erreurs:
- origine
- type
- la manière de les intercepter

creer des "enveloppes" (wrapper) :
- diminue les dependances
- facilite les tests

## Définir le flux normal

séparation entre la logique métier et le traitement des erreurs. Mais déplacer la détection des erreurs à la lisière du programme.

Creer des cas particulier pour conserver le flux normal lisible

## Ne pas retourner null

Retourner un objet "qui ne fait rien"

## Ne pas passer null

## Conclusion


- "nouvelles" methodes de gestion des donnees : retour de fonctions, exception, monades (Maybe), optional

- RAII et exception, equivalent de finally





