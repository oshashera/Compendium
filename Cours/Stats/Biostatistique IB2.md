#s6
8cm
6tp
1cc en salle info
1 devoir à la maison
	R
	1 sujet/personne, si mauvais sujet=0
	25%
Test/qcm en tp 2 4 et 6   

### RAPPELS R BQ1

![[Pasted image 20230216124949.png]]

![[Pasted image 20230216125008.png]]

Comparaison de moyennes
![[Pasted image 20230216125024.png]]

![[Pasted image 20230216125038.png]]

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

### Exemples (avec le qcm rempli à l'avance)

- **Les températures idéales à l'intérieur et l'extérieur sont-elles corrélées?**
On vérifie que les échantillons pour la T° ext et int suivent bien une loi Normale -> shapiro.test
On obtient les pvalues 0,006 et 6E-7 au risque alpha = 0,05, on peut donc rejeter H0 et on conclut qu'aucun échantillon ne suit de loi Normale 
On fait un test de spearman (pas de normalité des données)
Pvalue 0,01 à alpha = 0,05 donc on rejette H0 et on conclut que les échantillons sont corrélés. Il existe donc un lien linéaire entre la température idéale à l'intérieur et à l'extérieur.

- **Existe-t-il un lien entre le jour de naissance et le nombre de mails non lus?**
Test de normalité des données -> test de shapiro
Les deux ne suivent pas de loi normale, donc encore un test de spearman à faire.
Test de spearman, pvalue = 0,247 on peut pas rejeter H0 donc on conclut que pas de corrélation.

- **Existe-t-il un lien entre le jour de naissance et la température idéale à l'intérieur et extérieur**
Test de shapiro -> aucun normal
Test de spearman -> 0,359 donc on peut pas rejeter H0 donc pas de corrélation

### Vers les modèles linéaires

#### Régression linéaire - meilleur droite

[insérer diapo]
*alpha0 est l'ordonnée à l'origine et alpha1 c'est la pente*
*alpha 0 + alpha1 = taille*

##### Régression linéaire - démarche

1. Créer la régression linéaire et estimer les coefficients alpha0 et alpha1
- > mod >- lm(y~x) 
*lm = linear model*
*y en fonction de x*
2. Vérifier la validité du modèle (la régression linéaire): tester la normalité des résidus
- > shapiro.test(mod$residuals)
3. Si la régression linéaire est valide : interprêter les coefficents 
- > summary(mod)
4. Utiliser la régression : tracé de la droite de régression, prédictions...

#### Régression linéaire - meilleur droite

- > mod = lm(y~x)
- > plot(x,y)
- > abline(mod)

On défini les résidus (différences entre la droite et les observations)
Ei = yi - y(avec chapeau)i

avec :
- yi l'observation i
- ychapeaui = alpha0 + alpha1xi pour l'observation i

Pour trouver la meilleur droite (estimer les coefficients alpha0 et alpha1) on minimise la somme des carrés des résidus : Méthode des moindres carrés 
$$RSS~(résidual~sum~of~squares)  = \sum(\hat{y}i - y_i)$$

Il faut que la droite soit "au milieu" du nuage de points : on regarde les résidus et on test leur normalité
- > mod$residuals
- > shapiro.test(mod$residuals)

##### Interprétation des coefficients

- >summary(mod)
Donne plein d'infos, certaines utiles, d'autre non.
-> rappelle la formule
-> donne les residuts
->donne les **coefficients** (nous intéresse)
-> residual standard error : nous donne le "multiple R-squared" qui est la p-value qu'on regarde (pas l'autre)

Pour les **coeffs**
- colonne Estimate : intercept est l'ordonnée à l'origine (alpha0)
- colonne Estimate : X = nombre du coeff associé à X (alpha1)
- colonne Pr(>|t|) c'est la p-value

Si x = 0 on aura une forte p-value
Si x est grand, p-value très loin de 0, coeff significatif, et une variable permet donc d'edxpliquer l'autre.

R effectue un test statistique pour comparer la valeur du coefficient à 0, la p-value correspondante est dans la colonne Pr(>|t|) : si la pvalue est inférieure au seuil, le coeff est significativement différent de 0 et il y a donc un lien entre x et y (pas valable pour alpha0)

Une régression linéaire est un cas particulier de modèle linéaire : 
- y est la variable expliquée
- x est la variable explicative

On peut construire des modèles linéaire avec plusieurs variables explicatives (quantitatives ou qualitatives)


#### Retour sur le questionnaire

- **les températures idéales à l'intérieur et l'extérieur sont-elles corrélées?**
y a une droite, pas très penchée, mais existante.

On réalise une régression linéaire pour expliquer la température idéale à l'extérieur en fonction de la température idéale à l'intérieur :
- >mod_temperatures = lm(T_exterieur ~ T_interieur , data = cm3)
*particulier, faut lui préciser le jeu de données, après (data =)*
On vérifie la normalité des résidus pour voir si le modèle est valide:
- > shapiro.test(mod_temperatures$residuals)
On a pas de normalité des données donc on est pas censé regarder le summary (on va quan même le faire):
regardons quand même les caractéristiques du modèle
- > summary(mod_temperatures)
Intersect 7,2 et coeff de 0,77 avec un p value de 0,02 -> proche du seuil, on considère qu'on a un lien entre T° ext et T° int

- **Existe-t-il un lien entre la saison de naissance et la température?**
on voit des différences sur des boites à moustache mais on sait pas.

On réalise une régression linéaire pour expliquer la température idéale à l'intérieur en fonction de la saison de naissance:
- >mod_temp_saison = lm(T_interieur~saison, data=cm3)
On vérifie la normalité des résidus
- >shapiro.test(mod_temp_saison$residuals)
Ca marche, le modèle est valide (normalité)
Donc summary(mod_temp_saison)
Sur le summary y a que 3 saison : la 4 ème, le printemps , est utilisée en intersect (prédiction printemps), et les autres lignes c'est les différences par rapport à la modalité printemps.

La saison printemps n'apparait pas : c'est la modalité de référence du modèle linéaire. Toutes les autres coefficients sont calculés par rapport à la valeur prédite au printemps.
Ici tous les coefficients sont associés à des pvalules>0,05 donc il n'y a pas d'effet de différence de température idéale par rapport au printemps [récup diapo]

