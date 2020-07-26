
# 1. Fundamentals of Quantitative Design and Analysis

Slides : https://www.elsevier.com/__data/assets/powerpoint_doc/0011/559721/CAQA6e_ch1.pptx

## 1.1 Introduction

Amélioration des performances = amélioration des technologies de semi-conducteurs + amélioration des architectures des ordinateurs (RISC)

Démocratisation des ordinateurs (au sens large : mobiles, serveurs, etc) = ensemble de facteurs : plus de puisssance, baisse des coûts (PC, mobiles), 
facilité de fabrication en grande quantité (circuits intégrés, microprocesseurs), langages de programmation haut niveaux (parallèle entre l'augmentation
de puissance, l'évolution des besoins que permet cette évolution de technologie et les moyens de développement pour profiter de cette puissance
et répondre aux besoins).

Fin de l'amélioration des processeurs uniques vers 2004. Puis amélioration du parallélisme des instructions (ILP, plus de progression maintenant, 
implicite contrairement aux autres LP), puis parallélisme des données (DLP) et des threads (TLP), et maintenant paralèllisme des requètes (RLP).

Diminution de l'augmentation des performances due à loi de Moore (doublement de la puissance tous les 18 mois, n'est plus valide), loi d'Amdahl (limitation performances paralélisme).

Futur pour améliorer les coûts énergie-performance : domain-specific architecture

## 1.2 Classes of computers

Selon le prix et les points critiques

- internet of things et embedded computers : prix, énergie, performances spécifique à une application
- personal mobile device (PMD) : coût, énergie, media performance, réactivité
- desktop : prix-performance, énergie, performances graphiques
- serveur : débit, disponibilité, évolutivité, énergie
- clusters/warehouse-scale computers : prix-performances, débit, "energy proportionality"

**Classes of Parallelism and Parallel Architectures**

2 types de parallélisme :

- Data-level parallelism (DLP) 
- Task-level parallelism (TLP)

- Instruction-level parallelism (DLP)
- Vector architectures, graphic processor units (GPUs), and multimedia instruction sets (DLP)
- Thread-level parallelism (DLP et TLP)
- Request-level parallelism (TLP)

Classification Flynn (1996)

- SISD (uniprocessor)
- SIMD (vectorisation, DLP, GPU)
- MISD
- MIMD

## 1.3 Defining Computer Architecture

1. qu'est-ce qui est important ?
2. concevoir le design en tenant compte des performances, l'efficacité énergétique, les coûts, etc

**Instruction set architecture (ISA)**













