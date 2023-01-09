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



