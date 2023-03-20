## <u>Initiation aux systèmes d'information géographique</u>

Rappel 

- [ ] Diagnostic environnemental des prairies St Martin

![[Pasted image 20230320140420.png]]

- [ ] Etapes:

1. Planifier le projet sous SIG 
2. Digitaliser les informations cartographiques relevées sur le terrain 
3. Réaliser la symbologie des couches d’information sur la base des typologies choisies
4. Mettre en forme de la carte

- [ ] Rendu demandé

A déposer sur l’ENT (suite au stage terrain, date à recommuniquer) 
Un chapitre Carto (mat-met, carte(s), résultats-discussion, explications du choix de type et de comment on a fait notre carte (rapidement)) dans le rapport final A minima, la carte doit présenter l’occupation du sol et être être mise en forme aux standards présentés


### Qu'est-ce qu'un SIG?

- [ ] Outil informatique de représentation et d'analyse de données géographiques 
- [ ] Il permet de mettre en relation les informations cartographiées afin d'identifier, de structurer et de cartographier des résultats pour visualiser, comprendre et aider à la décision.
- [ ] Concrètement il permet la superposition de **différentes couches d’information** et leur analyse

### Qu'est-ce qu'une couche d'information?

- [ ] Une couche constituée d’un même type d’objet cartographique

![[Pasted image 20230320140731.png]]

### Le référencement dans l'espace des couches d'information

- [ ] Ce référencement se fait en utilisant un Système de projection / de coordonnées (algo mathématique qui calcule des points X/Y(Z parfois))
- [ ] Il définit les règles mathématiques permettant de passer d’un paysage en trois dimensions à une projection sur un plan
- [ ] Il a pour but de **minimiser les erreurs de représentation** par rapport à la réalité, sur une zone donnée
- [ ] En France, <u><b>le système de projection utilisé est le Lambert 93</b></u>

### Représentation de type vecteur vs. raster

![[Pasted image 20230320141016.png]]
*vecteur = dessin, raster = image, photo*

- [ ] Le raster 

Image découpée en cellules (pixel) aux quelles sont affectées une combinaison de chiffres pour définir la couleur.

![[Pasted image 20230320141118.png]]

Les rasters servent souvent en tant que support de la cartographie « terrain », mais ont pas bcp d'infos

- [ ] Le vecteur

Il comprend deux composantes: 

1. une composante cartographique:
	- Des entités ponctuelles (point)
	- Des entités linéaires (ligne)
	- Des entités surfaciques (polygone)

![[Pasted image 20230320141247.png]]

2. une composante attributaire

Un "tableau" associé à la carte:
champs et enregistrements sont des termes **A CONNAITRE**
![[Pasted image 20230320141307.png]]


### Les principales difficultés

- [ ] Il faut que les couches d’information superposées aient <u>le même référentiel de projection (la couche la moins précise impose sa précision)</u>

Aide possible: l’existence des métadonnées qui permettent d’indiquer la limite d’utilisation des données (auteur, précision…ect)


### Les principaux types de fichiers 

![[Pasted image 20230320141619.png]]

<mark style="background: #FF5582A6;">/!\ 2 ENREGISTREMENT DIFFERENTS A FAIRE : DONNEES ET PROJET </mark>
____


## Cartographie du site d'étude

### Planifier son projet SIG

1. Quels éléments figureront sur ma carto ? *-> est ce que cet élément est structurant pour mon diagnostique écologique ?*
- Les parcelles *a minima*
- Les haies *a minima*
- Cours d'eau
- Chemins
- Alignements d'arbres

2. Comment vais-je représenter ces éléments ?
- Les parcelles -> polygones
- Les haies... -> lignes

3. Quel système de projection vais-je utiliser? 
- Lamber 93 (EPSG 2154)

4. Quelles couches d’information SIG seront nécessaires?
![[Pasted image 20230320142052.png]]

5. Quels attributs à ces couches ?
- Occupation du sol : Nom de l’habitat (format texte) / Code habitat (format numérique)


*Dans la mesure du possible, réfléchir et fixer chacun de ces points avant de commencer la digitalisation*

