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
plot(x,y) puis abline(mod)



