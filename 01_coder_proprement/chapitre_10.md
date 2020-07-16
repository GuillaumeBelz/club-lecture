
# les classes

## Organiser une classe

?? ordre de declaration, public puis private, separation declaration implementation
?? protected pour les tests ?
?? outils du langages pour differentier les types de classes ? interface, pod, etc

## De petites classes

pouvoir decrire brievement la classe
SRP = raisons d’être modifié

"Faire en sorte que le logiciel fonctionne et faire en sorte que le logiciel soit propre sont deux activités très différentes"
?? remarque souvent faites au debutants sur les forums. Interet de l'apprentissage du TDD et analyse statique des le debut? 
?? Comment un debutant peut evaluer la maintenabilité du code ? Comment enseigner ca ?

"Faire en sorte que le logiciel fonctionne et faire en sorte que le logiciel soit propre sont deux activités très différentes"
-> "Par conséquent, la question est de savoir si vous voulez que vos outils soient rangés dans des boîtes à outils avec de 
nombreux petits tiroirs contenant des éléments parfaitement définis et étiquetés, ou si vous voulez avoir quelques tiroirs
dans lesquels vous mettez tous vos outils en vrac."

** Cohésion

Maintenir la cohésion mène à de nombreuses petites classes
nombre réduit de variables d’instance, separer en classes

## Organiser en vue du changement

OCP
?? creation de hierarchie pour reutilisation du code?
?? approche tout object, deep hierarchie. ECS ?

Cloisonner le changement
introduire des interfaces et des classes abstraites pour limiter l’influence de ces détails
DIP
