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

Si la pvalue est inférieure au seuil, le coefficient est significativement
différent de 0 et il y a donc une différence par rapport à la modalité de
référence