
> En cours de redaction

# Chapitre 11 - Systèmes

## Construire une ville

- Certaines de ces personnes sont responsables de la vue d’ensemble, tandis que d’autres se focalisent sur les détails.
- niveaux d’abstraction, modularité, composants

## Séparer la construction d’un système de son utilisation

```
public Service getService() { 
  if (service == null)
    service = new MyServiceImpl(...); // Service par défaut suffisant return service; // pour la plupart des cas ?
}
```

- fonction de creation
- La compilation ne peut pas se faire sans résoudre ces dépendances, même si nous n’utilisons jamais un objet 
de ce type à l’exécution !

??? est-une mauvaise chose ? Permet de verifier que le code est valide ?

- Construire dans la fonction main
- Fabriques
- Injection de dépendance
  - JNDI, "mais il résout néanmoins activement la dépendance"
  - "Les objets dépendants réellement employés sont indiqués par l’intermédiaire d’un fichier de configuration ou par programmation dans un module de construction à usage spécial.". framework Spring.
  
## Grandir

- agilité itérative et incrémentale
- "Leur architecture peut évoluer de manière incrémentale, si nous maintenons la séparation adéquate des préoccupations."
- bean entité, EJB

### Préoccupations transversales

programmation orientée aspect (AOP, Aspect-Oriented Programming)

## Proxies Java

Le "bon vieil objet Java tout simple" (POJO, Plain Old Java Object)

## Frameworks AOP en Java pur

## Aspects d’AspectJ

## Piloter l’architecture du système par les tests

BDUF, Big Design Up Front

## Optimiser la prise de décision

## Utiliser les standards judicieusement, lorsqu’ils apportent une valeur démontrable

## Les systèmes ont besoin de langages propres à un domaine

langages propres à un domaine (DSL, Domain-Specific Language)

## Conclusion

## Questions

- ca parle plus de classe que de systemes ?

https://www.amazon.fr/Large-Scale-Software-Design-John-Lakos/dp/0201633620

- separation construction/execution

- aspect ? ancienne methode/nouvelle methode ?
- comment choisir/creer ces abstractions ? Ces modules ?
- JNDI, Spring : fausse independance ?
- faire par defaut ?



