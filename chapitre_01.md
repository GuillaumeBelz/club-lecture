
"Coder Proprement" est un livre de Robert C. Martin, dît "Oncle Bob". Il est principalement connu pour ses contributions 
à propos de la méthode Agile, de la gestion de projet et des principes SOLID. Ses autres livres sont également intéressants, 
il ne faut pas hésiter à les lire aussi.

Les objectifs généraux de ce livre sont de fournir :

- des guidelines pour la rédaction de code: noms, fonctions, commentaires, mise en forme,
- une certaine connaissance des structures de données,
- la bonne pratique qu'est "tester" le coder.

Avec pour finalité d'être capable :

- de différencier le bon et le mauvais code,
- d'écrire du bon code,
- de transformer du mauvaise code en bon code.


# Chapitre 1 - Code propre

Le but de ce chapitre est de commencer à répondre à la question "qu'est ce qu'un code propre ?", à travers trois 
questions générales:

 - pourquoi aura-t-on toujours besoin de code ?
 - que le coût du désordre ?
 - qu'est-ce qui caractérise un code propre ?

## Il y aura toujours du code :

L'abstraction augmente et l'on semble avoir de moins en moins besoin de coder, mais le code n'est finalement qu'un langage dans lequel on exprime nos exigences et il y aura toujours des exigences à exprimer.

## Le coût du désordre :

### Causes

Les raisons entraînant la création d'un mauvais code sont très souvent reliées à un problème plus général dans tout 
projet : la pression du temps. C'est généralement du code réalisé trop vite pour répondre le plus rapidement possible à 
un besoin sans tenir compte de la maintenance future, on remet "à plus tard" le fait de rendre le code propre, mais 
"plus tard" signifie "jamais".

### Conséquences

Il s'en suit un ralentissement de la productivité à cause de d'un code négligé dans lequel il est difficile d'avancer, 
car il est difficile à comprendre et aucune modification n'est négligeable. Surtout que reprendre à 0 est généralement 
complètement impossible et mène simplement aux mêmes travers.

Produire du bon code est une question de survie professionnelle.

### Fausses causes, attitude

Le relationnel avec les décideurs et les nouveaux développeurs est important. Les développeurs ont une trop forte 
tendance à rejeter la faute sur les décideurs qui les pressent mais il est de leur devoir :

- de dire non lorsque quelque chose est impossible,
- de s'assurer qu'il sera rare de devoir dire non à une demande faisable (avec un bon code).

## Code propre :

Regroupement de plusieurs point de vue à propos de la rédaction de code. Un code propre doit être :

- élégant : un code agréable à lire est plus facile à lire et donc plus facile à écrire.
- simple : il y a une certaine idée de minimalisme (principe KISS), relié au point suivant ...
- efficace : optimal en un certain sens, rien ne permet de l'améliorer de manière évidente,
- explicite : il doit être assez expressif pour ne cacher aucune intention du développeur,
- destiné à être partagé : fait pour être lu par des humains, et le désordre appelle le désordre.
- testé : on assure qu'il fait ce que l'on veut (et les tests ré-expriment les besoins).

Règle du boyscout : le code doit être plus propre que quand on est arrivé. Nous sommes reponsables d'écrire du code 
propre, de le maintenir propre et au besoin de le nettoyer.

# Questions abordées pendant les discussions :

## Q1 : il parle d'un style d'écriture, de manière de concevoir.

Il faut que le code soit conçu pour être compréhensible, mais cela va plus loin que juste la bonne architecture et la 
bonne organisation. On revient sur l'expressivité : le code montre clairement l'intention du développer, il ne cache 
rien, il est limpide.

## Q2 : bonnes pratiques dans les langages à travers des guidelines.

Elles parlent à la fois :

- de style d'écriture,
- de bonne manière de concevoir.

Exemples dans certains langages :

- C++ https://github.com/isocpp/CppCoreGuidelines
- C# https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions
- Python : Python Enhancement Proposals https://www.python.org/dev/peps/
- Google Python Style Guide https://google.github.io/styleguide/pyguide.html

Les designs patterns sont un exemple dans le point sur la conception. Ils peuvent néanmoins aussi aider d'autres 
codeurs à comprendre ce qu'on a voulu exprimer parce que ce sont des schémas connus (sans être figés ! Il sont sujets 
à adaptation). Le principal second intérêt des DP est de comprendre comment on a abouti à leur conception.

L'utilisation des commentaires est un exemple sur le style d'écriture. Les commentaires ne doivent pas servir à 
comprendre l'intention du code. Ils doivent seulement aider à faire comprendre éventuellement des point des détails 
du code qui ne sont pas exprimables par le langage. Lorsqu'un code a besoin de commentaires expliquant le patch d'un 
patch, d'un patch, c'est le signe que l'on travaille sur un mauvais code.

Documenter est délié de la notion de commentaire. Ce n'est pas parce que le langage fournit la documentation par 
l'intermédiaire du commentaire (au sens du langage) que l'on est effectivement en face de commentaires.

## Q3 : Relation avec les décideurs : de la difficulté à être entendu avec les décideurs.

C'est important d'avoir un bon relationnel et être capable :

 - d'expliquer à d'autres,
 - d'apprendre aux autres à gérer ces problématiques.

La méthode AGILE est une tentative de résolution par l'introduction du "business" au niveau de la production du code. 
Les dérives courantes sont l'utilisation de cette méthode pour reconstituer un modèle non agile où les développeurs 
exécutent sans se faire entendre.

Il est important de présenter de manière concrète des fonctionnalités auprès des décideurs mais surtout aux destinataires 
du projet. Idéalement les réunions business et fonctionnalités devraient être complètement séparées pour éviter ce 
type de dérive.

Addedum de discussion : l'UML (ou formalisme équivalent) n'est pas toujours adapté pour la compréhension mais peut aider 
pour le dialogue avec des non-initiés.

## Q4 : Relation avec les apprenants : problème de formation des personnes.

Apprentissage : projet jetable, problème pour acquérir de la compétence sur la maintenance de projet.
Nécessité de formation personnalisées pour former les gens au plus près et ne pas les lâcher complètement dans la nature 
avec un faux sentiment de compréhension.

Problématique de l'enseignement "classique" vs les formations internet : impossible de créer et suivre des 
projets sur le long terme. C'est possible sur les formation internet, mais pas souvent fait.

## Autres questions non abordées :

**Opposition entre code efficace vs premature optimisation**

Certains experts cités dans ce premier chapitre indiquent que pour eux, un code propre est un code efficace.
L'idée est qu'un code qui est déjà optimal n'aura pas besoin d'être modifié et donc demandera moins de maintenance.

Est-ce que cette idée de code optimial ne s'oppose pas au problème de _premature optimisation_ ?

**Choix du langage de programmation**

Deux approches sont possibles pour choisir le langage de programmation (mais on peut étendre cette question a tous 
les choix technologiques sur un projet) :

- utiliser le langage le plus adapté à un problème. Donc potentiellement un langage que l'on ne maîtrise pas.
- utiliser un langage que l'on maitrise, meme s'il n'est pas le plus adapté à un problème. (Dans la limite du raisonnable, 
on ne va pas créer un site web en assembleur).

Quel choix feriez-vous et dans quels contextes ?

## Strawpolls :

Répondus :

- Pensez-vous que votre propre code est propre ? http://www.strawpoll.me/14162994
- Êtes-vous...  http://www.strawpoll.me/14163039
- C'était cool ? http://www.strawpoll.me/14163936

Non proposé :

- Quel(s) langage(s) de programmation utilisez-vous ? http://www.strawpoll.me/14163066
