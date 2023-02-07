#s6
8cm
6tp
1cc en salle info
1 devoir à la maison
	R
	1 sujet/personne, si mauvais sujet=0
	25%
Test/qcm en tp 2 4 et 6   



# CM1: principe des tests statistiques, test du x² (chi²)

(enseignante: marine jacquier)

## 1. Principe d'un test statistique

Formulation d'une hypothese statistique nulle H0 (hypothese alternative H1)

Observation des données expérimentales : est ce que les observations sont compatibles avec l'hypothèse nulle?
Si oui on accepte H0, si non on la rejette.

		Moyenne = 10?
		H0= la moyenne est 10
		H1= la moyenne n'est pas 10
		Xbarre = 10,5, probablement H0
		Xbarre = 25 => 7h
		=> statistique de test: moyenne - 10
		 
=> besoin de définir une statistique de test (quantifier à quel point nos données "sont proches" de H0)
H0 doit donc représenter une hypothèse pour laquelle il est facile de faire un calcul (par exemple égalité des moyennes ou des variances)

**Illustration: loi binomiale**
	On lance un dé un certain nombre de fois et on compte le nombre de succès (par exemple avoir un numéro pair)
	Si le jeu n'est pas truqué (le dé est équilibré), combien de succès devrait-on observer?
	Si le nombre de succès observé est trop faible (ou trop élevé), on préfère rejeter H0
	gnégnégné distribution en cloche, si c'est en haut c'est ok si c'est sur les bords c'est pas ok


**Attention**
H0 peut tout de même être vraie, on en est jamasi certain à 100%.
On a regardé seulement un petit échantillon.

**Notion de valeur p (*p-value*)**
Une fois qu'on a la statistique de test on peut la comparer à une distribution théorique => la *p-value* (valeur p)
P value = probabilité d'être au delà de la statistique de test sous la distribution de H0 (dans les zones qu'on veut pas)
Plus elle est faible, plus on est loin, moins on a de chance d'avoir H0
Donc si on a P au dessus d'une certaine valeur -> H0, sinon on acceptera H1.
Cette valeur est appelée **seuil de significativité** ou **risque alpha**
Seuil de significativité (= probabilité de rejeter Hà alors qu'elle est vraie) : souvent $$\alpha= 0,05$$
R calculera automatiquement cette *p-value*, il ne restera plus qu'à conclure sur l'acceptation de H0 en fonction de la p-value et du seuil choisi:
* *p-value* > seuil : on accepte H0
* *p-value* < seuil : on rejette H0 (et donc on accepte H1)


#### Démarche
* 1) question biologique
* 2) choix du test statistique approprié en fonction de la queston biologique et des données disponibles
* 3) application du test statistique et calcul de la valeur *p*
* 4) conclusion du test statistique en fonction de la valeur *p*
* 5) réponse à la question biologique


## 2. Données utilisées

### Tableaux de données

Données biologiques observées chez de nombreux individus

Un tableau de données a en général la structure suivante (data.frame dans R):
- *i* observations sur les lignes
- *j* variables sur les colonnes

### Types de variables

**Deux grandes catégories**
- Variables *quantitatives* 

		ex: taille, poids
- Variables *qualitatives* avec un nombre fini de catégories (les modalités) qui peuvent être ordonnées ou non

		ex: couleur des yeux, saison...

**Attention** : les variables quantitatives discrètes sont parfois utilisées comme des variables qualitatives

## Test du chi²

#### Données
Une ou plusieurs variables **qualitatives** mesurées chez les mêmes individus
On s'intéresse à la répartition des observations entre les différentes modalités qualitatives pour 1 ou plusieurs variables

Deux (principaux) test du chi²
- Test du chi² d'adéquation (1 variable)
- Test du chi² d'homogénéité (2 variables)

#### Table de contingence

Une table de contingence contient le nombre d'occurences de chaque modalité d'une variable qualitative, ou de chaque couple de modalité si on a 2 variables
Tableau de modalité croisée si 2 variables
![[Pasted image 20230118161047.png]]

		Construction de la table de contingence dans r:
		 table(variable1)
		 table(variable1,variable2)

#### Test du chi² d'adéquation

Situation:
- mesure qualitative chez un groupe d'individu
=> la répartition observée est-elle conforme à la répartition attendue?

H0? "la répartition des observations dans les différents groupes est conforme à la répartition attendue"

###### Statistique de test?

**Répartition observée**
| K     | L     | M     |
| ----- | ----- | ----- |
| $O_K$ | $O_L$ | $O_M$ |
-> à comparer aux proportions théoriques $P_K$, $P_L$, $P_M$

| K     | L   | M   |
| ----- | --- | --- |
| $q_K$ | $q_L$    | $q_M$     |
*avec*  $q_{K}= \frac{O_K}{O_K+O_L+O_M}$
vs $P_K,P_L,P_M$
<br>
$(P_K-q_K)^2+(P_L-q_L)^2+(P_M-q_M)^2$

T = $\sum_{j=1}^{J}\frac{(O_j-N.P_j)^2}{N.P_{j}}$
avec:
- N = $O_{K}+ O_{L} + O_M$ = effectif total
- $O_j$ l'effectif observé
- $N.P_j$ l'effectif théorique


1. Calcul des effectifs dans chaque catégorie (table de contingence)
	- tab_sample <- table(sample)
2. Pour tester si la répartition correspond à des proportions théoriques (par exemple (p1,p2,p3))
	- chisqu.test(tab_sample, p=c(p1,p2,p3))

		 tab_lunettes <- table(donnees$lunettes)
		 p1 = 0,4
		 p2 = 0,6
		 chisq.test(tab_lunettes, p=c(p1,p2))
		On a 0,73 en p value donc ca passe pour H0

#### Rédaction 

On réalise un test du x² pour la variable v1
>tab 1 <- table(v1)
>chisq.test(tab1, p=c(p1,p2,...))

On obtient une p-value = pval. Au risque alpha = 0,05, on [peut/ ne peut pas] rejeter l'hypothèse H0, et on conclut donc que la répartition de v1 [correspond/ ne correspond pas] à la répartition attendue

*remarque* : il faudra bien penser à concluer sur la question biologique après la conclusion du test ; le risque alpha peut changer

[mettre photo exercice]
[mettre photo réponse]

#### Test du chi² d'homogénéité / d'indépendance

Situation
- différentes mesures qualitatives chez les mêmes individus
=> deux critères qualitatifs sont-ils indépendant ? 

		Ex: le moyen de transport pour se rendre à l'université est-il lié au port de lunettes?

==[ insérer photo diapo cours]==

H0 ? "les critères qualitatifs considérés sont indépendants"

==[photo diapo cours]==

On calcule : 
	- les effectifs marginaux : Oi = OiL + Oim Oj = Oxj + Oyj
	- l'effectif total : N = OxL + Oxm + OyL + Oym
	- les effectifs théoriques:

$$E_{ij=N.}\frac{O_i}{N}.\frac{O_j}{N} $$



#### Test du chi² sur R

1. Création d'une table de contingence (à deux entrées)
	- tab=table(sample1, sample2)
2. Réalisation du test du chi²


#### Test exact de Fisher

Sur table de contingence 2x2 (en général)
Alternative au test du chi² : contrairement au test du chi², est valide même si certains effectifs sont faibles.
Contrairement au test du chi², on peut calculer la p-value directement "à la main"

Démarche:
1) Créer la table de contingence *tab*
2) Réaliser le test exact de Fisher : 
	fisher.test(tab,alternative = "two.sided") 
Il existe d'autres valeurs pour alternative (dans le CM8)

[[mettre CM2]]

*cm3*

### Exemple de corrélation

[insérer diapo]
mais corrélation =/= causalité, pas forcément lié.

##### Pourquoi ces corrélations?

- facteurs de confusion : A -> B et A -> C, on observe une corrélation entre B et C
- facteurs intermédiaures : A -> B -> C, on observe une corrélation entre A et C
- hasard
- manipulation des données

### Tests de corrélation (linéaire)

#### Coefficient de corrélation

![[Linéaire ou non linéaire IB2]]
Situation : 2 mesures quantitatives chez un groupe d'individus
=> existe-t-il un lien (linéaire) entre ces deux mesures?

Exemple:
La taille et le poids sont-ils liés chez différentes espèces d'oiseaux?

##### Coefficient de corrélation
Le coefficient de corrélation (r) varie entre -1 et 1
- -1 = négativement corrélées (1 augmente l'autre diminue)
- 1 = positivement corrélées
- 0 = pas corrélées
- entre : nuances

$$r = \frac{Cov(X,Y)}{\sigma_x \sigma_y}$$
avec : 
- Cov(X,Y), la covariance des variables X et Y (~écarts des variables par rapport à leurs moyennes respectives)
- $$\sigma_i$$l'écart type de la variable i (~&cart de la variable à sa moyenne)

estimation du coeff r pour deux échantillons X et Y:
[récup diapo]

#### Démarche

1. tester la normalité des échantillons : test de Shapiro
2. Appliquer le test de corrélation approprié
- Si les deux suivent une loi Normale : test de corrélation de Pearson (paramétrique)
	- *cor.test(s1,s2, method = "pearson"*)
- Sinon : test de corrélation de Spearman (non paramétrique)
	- *cor.test(s1,s2, method = "spearman")*
3. Conclusion du test

$$H_{0}~les~échantillons~ne~sont~pas~corrélés~(r = 0 ~donc)$$
##### Test de corrélation de Pearson

Si les deux échantillons (x et y) suivent une loi Normale
- >*cor.test(x,y,method="pearson")*
Il nous donne bcp de trucs dont "cor : (valeur)" et la p-value 

##### Test de corrélation de Spearman

Si les deux échantillons (x et y) suivent une loi Normale
- >*cor.test(x,y,method="spearman")*
Il nous donne bcp de trucs dont "cor : (valeur)" et la p-value 

##### Test de corrélation - rédation

Vu que les échantillons (suivent/ne suivent pas) une loi Normale, on effectue un test de corrélation de (Pearson/Spearman) :
- >*cor.test(s&,s2,methode="pearson/spearman"*
On obtient une p-value=pval. Au risque alpha = 0,05, on (peut/ne peut pas) rejeter l'hypothèse H0, et on conclut donc que les échantillons (sont/ne sont pas) corrélés linéairement.


