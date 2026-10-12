# Micro-fusée expérimentale

Ce dépôt rassemble la conception des différents sous-systèmes de la micro-fusée : propulsion, structure et récupération. Le travail en cours porte sur un éjecteur de coiffe compact destiné à libérer le parachute.

![Vue isométrique de l’éjecteur](https://paul-n7-3ea-portfolio.cdkme.chatgpt.site/assets/ejecteur/ejecteur-isometrique.png)

## Problème d’intégration

Le mécanisme doit éjecter la coiffe tout en laissant suffisamment de place au parachute replié. L’espace disponible est très limité : l’enveloppe extérieure du modèle mesure 44 mm de diamètre pour 40 mm de hauteur, avec un passage central de 38,2 mm.

Cette contrainte conduit à placer la transmission autour du passage central plutôt qu’au milieu. Les engrenages et les deux crémaillères utilisent la couronne périphérique, tandis que le ressort travaille suivant l’axe de la fusée.

## Principe retenu

1. Le bas du ressort s’appuie sur une pièce fixe.
2. Le haut du ressort est retenu par un support supérieur, représenté en rouge dans le modèle.
3. Ce support est clipsé entre deux crémaillères opposées.
4. Un servomoteur entraîne un train d’engrenages qui rétracte les crémaillères de manière synchronisée.
5. Lorsque leurs zones d’appui disparaissent, le support supérieur est libéré.
6. Le ressort se détend rapidement et pousse le parachute compacté.
7. Le parachute transmet l’effort à la coiffe, maintenue juste assez pour rester en place avant la commande.

```mermaid
flowchart LR
  S[Servomoteur] --> E[Train d'engrenages]
  E --> C[Deux crémaillères]
  C --> V[Déverrouillage du support supérieur]
  V --> R[Détente du ressort]
  R --> P[Parachute compacté]
  P --> O[Éjection de la coiffe]
```

## Démarche de conception

### 1. Réserver le volume utile

Le diamètre du parachute est traité comme une contrainte de départ. Le mécanisme est ensuite construit autour de ce passage afin que l’ajout de la commande ne réduise pas progressivement le volume disponible.

### 2. Maintenir l’énergie sans pièce transversale encombrante

Le support rouge retient le ressort en position armée. Les deux crémaillères créent deux appuis opposés et compacts. Leur mouvement latéral permet de libérer la pièce sans ajouter un verrou occupant tout le diamètre.

### 3. Synchroniser les deux côtés

Le train d’engrenages transforme la rotation du servomoteur en translations opposées. La symétrie limite le risque qu’un côté soit libéré nettement avant l’autre.

### 4. Préparer la validation réelle

La CAO vérifie l’encombrement et la cinématique nominale, mais le prototype devra encore mesurer :

- les jeux d’impression et le frottement des crémaillères ;
- la course réellement nécessaire au déclipsage ;
- la force du ressort comprimé ;
- le comportement avec le parachute réellement plié ;
- la répétabilité après plusieurs cycles ;
- la tenue de la coiffe avant la commande et sa libération au bon moment.

## Dimensions actuelles du modèle

| Caractéristique | Valeur |
|---|---:|
| Enveloppe extérieure | Ø44 × 40 mm |
| Passage intérieur | Ø38,2 mm |
| Course axiale simulée | 7 mm |
| Course des crémaillères | 1,477 mm |

Ces valeurs décrivent l’état actuel du modèle Fusion. Elles seront révisées après les essais de montage, de friction et de répétabilité.

## État du projet

- architecture générale modélisée ;
- chaîne cinématique définie ;
- vues et synthèse dimensionnelle produites ;
- prototype et choix définitif du ressort à réaliser ;
- essais avec parachute et coiffe à documenter.

Le dossier illustré et les plans sont visibles sur [la page micro-fusée du portfolio](https://paul-n7-3ea-portfolio.cdkme.chatgpt.site/micro-fusee).
