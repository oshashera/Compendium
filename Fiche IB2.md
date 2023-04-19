pvalue > seuil : on accepte H0
pvalue < seuil : on rejette H0 (et donc on accepte H1)
- variables quantitatives (par exemple : la taille, le poids, ...)
- variables qualitatives (par exemple : la couleur des yeux, la
saison,...), avec un nombre fini de catégories (les modalités) qui
peuvent être ordonnées ou non

Deux (principaux) tests du X² : QUALITATIF(S)
- Test du X2 d'adéquation (1 variable)
- Test du X2 d'homogénéité (2 variables)

Une table de contingence contient le nombre d'occurences de chaque
modalité d'une variable qualitative, ou de chaque couple de modalités si on a 2 variables.
> table(variable1)
> table(variable1, variable2)

X2 adéquation : 
> tab = table(sample)
> chisq.test(tab_sample,p=c(p1,p2,p3)) (ordre alphabétique)
H0 = la répartition des observations dans les diérents groupes est
conforme à la répartition attendue

X2 homogénéité/indé
> tab = table(samp1,samp2), puis chisq.test(tab)
H0 = les critères qualitatifs considérés sont indépendants

Shapiro = normal
Fisher = même variance
![[Pasted image 20230419120945.png]]

Corrélation : facteurs confusion A-> B et A -> C corr entre B et C
facteurs intermédiaires : A -> B -> C corrélation A et C
hasard ; manip données

Tester normalité into test corrélation:
> cor.test(s1,s2, method = "pearson") normal
> cor.test(s1,s2, method = "spearman") pas normal
H0 = les échantillons ne sont pas corrélés

modèle linéaires : représentation simplifiée de la réalité
Une variable expliquée (quantitative) et une/plusieurs variables explicatives quanti ou quali

mod = lm(y~x) ou lm(y~x1+x2)
test normalité des **résidus** : shapiro.test(mod$residuals) 
summary(mod) et mod$coefficients pour avoir la régression et les coeffs
a0 correspond à la ligne (Intercept), a1 ligne x -> a0+a1x
plot(x,y) puis abline(mod)

si on veut comparer deux modèles il faut qu'ils soient emboités et que leurs résidus soient normaux

modèle sans facteur : > mod0 = lm(y ~ 1)
Comparaison modèles linéaires:
H0 : "les modèles sont équivalents en terme de prédiction"
- si on rejette l'hypothèse nulle, cela veut dire que l'un des modèles est meilleur pour expliquer les données : celui qui a le RSS le plus faible
- si on accepte l'hypothèse nulle, les modèles sont "similairement bons", on choisira donc le modèle le plus simple : celui qui a le moins de coefficients

> anova(mod1, mod2) 


si explicatif = qualitatif on pourra prédire une valeur pour chaque modalité de la variable qualitative
dans les coeffs : la prédiction pour la modalité de référence (absent) correspond à la ligne (Intercept)
la différence entre cette modalité et la deuxième correspond à la ligne suivante... etc etc tt est comparé à la modalité de ref.

Si la pvalue est inférieure au seuil, le coefficient est significativement différent de 0 et il y a donc une différence par rapport à la modalité de référence


Comparaison moyennes pour plus de 2 groupes.
boxplot(Taille ~ Antibiotique, data = donnees, main = "titre gnégnégné",xlab = "Concentration en antibiotique", ylab = "Taille des bactéries", col = rainbow(3))
- séparer tt les échantillons par modalités dans des vecteurs
- vérifier leur normalité avec shapiro
- si tous normaux : bartlett.test(y~x)  H0=même variance
- si normalité et homodéasticité : > aov(y~x) ; sinon kruskal.test(y~x)  H0 = même moyenne
mod= aov(y~x)
- si on trouve un effet et anova : TukeyHSD(mod), et faut voir pvalue inf à alpha = diff signif. 


- si kruskal : test mann-whitney avec correction bonferroni (seuil alpha/nb comparaison) : wilcox.test(x1,y1). etc etc 
	si pval inf a alpha diff de moyenne
![[Pasted image 20230419123613.png]]

VE = variance expliquée (entre moy groupe et moy globale)
K = nb variables?
![[Pasted image 20230419123819.png]]
VNE =  variance non-expliquée (entre observations individuelles et moyenne du groupe)
![[Pasted image 20230419123828.png]]
Statistique de test de l'Anova : F =VE/VNE

prendre une variable en fonction d'une autre:
note_oui <- cm4$ Note.IB2[cm4 $ Master == "Oui"]






ACP :
On cherche à réduire la dimension en projetant sur des axes principaux
(qui maximisent l'inertie projetée)
=> réduire la redondance et le nombre de variables = méthode de représentation!!!! pas test

charger ade4 : library(ade4)

<mark style="background: #FF8500A6;">sur données normées</mark>
pca.olympic = dudi.pca(olympic$tab,scale=T,scannf=F,nf=2)
crée l'ACP

scatter(pca.olympic, posieig = "bottomright")
*scatter de tt les observations selon les 2 axes conservés+ valeurs graphs en basà droite*

individus = lignes : pca.olympic$li
variables = colonnes : pca.olympic$co

cercle corrélation : s.cocircle(pca.olympic.co)
*90° = indé, aigu = cor+, obtu = cor-*

graph des valeurs propres : pca.olympic$eig
barplot(pca.olympic$eig, xlab = "axe", ylab = "inertie projetée")
*inertie de chaque axe, son importance*

<mark style="background: #FF8500A6;">sur données brutes</mark>
pca.olympic.2 = dudi.pca(olympic$tab,scale=F,scannf=F,nf=2)
scatter(pca.olympic.2)


<mark style="background: #FF8500A6;">acp centrée</mark>
music = dudi.pca(cm6, scale = F, center =T, scannf = F, nf = 2)
Interprétation des deux premiers axes (51% inertie)
**Axe 1** déterminé principalement par la note de Classique, Jazz, chanson française, country. À gauche les individus en dessus de la moyenne pour ces musiques, à droite ceux au dessus
**Axe 2** Opposition Metal en haut et RnB/Hip Hop/Rap en bas 

covariances entre musiques : cov(cm6$Jazz, cm6 $classique)

indivs au centre : 
colMeans(cm6[c(59, 55, 17, 21),]) (regarder le scatter)
colMeans(cm6) 



classification/clustering:
Séparer un ensemble de données en groupes (cluster ) homogènes avec : une faible inertie intra-groupe une forte inertie inter-groupes

dist(pca.olympic$co)
donne distance entre les colonnes 

distance euclidiennes entre les individus : > d = dist(donnees)
relie indiv proches sous forme dendogramme 
h = hclust(d, method = ...) puis plot(h)
ex avec athlètes :
> d = dist(pca.olympic$co)
> indiv <- hclust(d, method = "ward.D2")
> plot(indiv, hang = -0.1, xlab = 'athletes', sub ='')