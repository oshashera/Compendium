#eco 
___
# Communautés

## I/ Qu’est-ce qu’une communauté ?

Elle correspond à un niveau d’organisation particulier utilisé en écologie. En écologie, on travaille selon des niveaux hiérarchiques d’organisation :

Atome/molécule -> cellule -> individu -> population -> peuplement/communauté -> biocénose -> écosystème -> écocomplexe -> biosphère.

On peut travailler sur les écosystèmes selon n’importe lequel de ces domaines, souvent sur plusieurs en même temps.

La population est définie comme l’ensemble des individus d’une même espèce (on l’assimile à l’espèce). La biocénose correspond à l’ensemble des populations qui occupent un même milieu.

La communauté est définie comme un ensemble plurispécifique plus restreint que la biocénose. Alors comment sont sélectionnées les espèces de la biocénose intégrées dans une communauté ? Et bien en fonction de la question scientifique posée par l’expérimentateur. Ce dernier choisit la communauté étudiée et en précise les limites.

Une guilde caractérise une communauté d’espèces apparentées et utilisant des ressources identiques ex : la guilde des oiseaux granivores.

L’échelle de la communauté amène plusieurs questions en écologies : cet assemblage d’espèces est-il aléatoire ou mis en place grâce à des processus spécifiques ? Y’a-t-il des règles d’assemblage ? Une structure fonctionnelle à respecter, ou une dynamique spatio-temporelle ? Des processus de sélection ou de coévolution impliqués ?

Certains processus contrôlent les assemblages d’espèces. L’identification des règles d’assemblage permet d’étudier le lien entre structure et fonction des communautés dans le cadre du fonctionnement global de l’écosystème, et de comprendre voire prédire leur dynamique. On peut également étudier le rôle des processus évolutifs dans la structure et la dynamique.

## II/ Caractériser la structure d’une communauté

Eléments indispensables de caractérisation :

- Le nombre d’espèces
- Le nombre d’individus ou l’abondance de chaque espèce

Lorsqu’on étudie une communauté, on doit d’abord caractériser sa structure.

On doit donc :

- Déterminer les espèces présentes : le nombre d’espèce est appelé richesse spécifique (S)
- Déterminer l’abondance de chaque espèce : absolue (densité) ou relative (proportions)
- En fonction de la question posée, on peut mesurer des variables additionnelles : taille, biomasse, activité biologique …

L’ensemble des informations récoltées s’appellent les données brutes, elles sont très nombreuses et difficiles à analyser telles quelles. On a besoin d’utiliser un nombre minimum de communautés pour chaque condition testée, pour être sûrs d’avoir des résultats exploitables.

Pour réduire le flux de données brutes, on utilise des paramètres synthétiques pour caractériser les communautés. Par définition, ils permettent l’intégration de plusieurs variables et donc la réduction de la quantité d’information.

L’indice de diversité de Shannon Weaver (H’) est un paramètre synthétique qui est très utilisé en écologie des communautés.

$$H'\space = \space -\sum_{i=1}^{S}[]$$$

![](file:///C:/Users/tomha/AppData/Local/Temp/lu929246kmhy.tmp/lu929246kmi1_tmp_af61b594c70c0333.png)

Il peut être nécessaire de transformer cette formule pour les calculs : log2(pi) = ln(pi)/ln2

H’ intègre 2 types de paramètres quantifiés dans la communauté : l’abondance de chaque espèce et la richesse spécifique. La valeur minimum qu’il peut prendre est 0, et il n’a pas de valeur maximale chiffrée. Quand H’=0, il n’y a pas de diversité dans la communauté, il n’y a qu’une seule espèce. Donc plus H’ augmente, plus la diversité augmente.

Donc, pour chaque espèce, j’applique la formule de H’ en calculant pi*log2(pi), et j’additionne ces produits.

![](file:///C:/Users/tomha/AppData/Local/Temp/lu929246kmhy.tmp/lu929246kmi1_tmp_f33ce1d1d48cc274.png)

La différence de diversité existante n’est pas liée à la richesse spécifique, mais à l’abondance relative des espèces dans chaque communauté.

Une répartition homogène de l’abondance des espèces dans la communauté fait augmenter H’, donc la diversité. H’ est maximal quand toutes les espèces ont la même abondance relative.

Pour des espèces à répartition équivalente : pi = p1+p2+…+ps = 1/S, et H’ = log2(S).

On peut également calculer l’indice de diversité relative H’/H’max = H’/log2(S). Cela permet de s’affranchir du nombre d’espèce et baser l’interprétation d’une différence d’indice sur les proportions relatives des espèces dans chacune des communautés.

**III/ Influence de la niche écologique dans la structuration des communautés**

La niche écologique correspond aux conditions de milieu dans lesquelles une espèce peut vivre et prospérer, elle est définie par une multiplicité de dimensions issues des paramètres qui la contrôle, et la niche réalisée et plus petite que la niche fondamentale.

2 espèces entrent en compétition quand leurs niches sont chevauchantes. La compétition stipule une exploitation similaire du milieu spatial et du milieu trophique.

Plus le nombre d’espèces présentes est élevé, plus leurs niches sont restreintes : les espèces sont donc plutôt spécialistes.

Quand deux espèces entrent en compétition, on observe chez l’espèce peu compétitive une baisse de croissance, de survie, de reproduction, et de production de descendants. C’est l’inverse chez les espèces compétitives.

La compétition va influencer la structure de la communauté car la baisse de survie des individus et leur faible production de descendants va modifier l’abondance relative des espèces, et la compétition peut aboutir à l’élimination d’une ou de plusieurs espèces par exclusion compétitive, ce qui va modifier la richesse spécifique de la communauté.

**IV/ Rôle de la prédation sur la structuration des communautés**

La prédation influence l’abondance relative des espèces dans la communauté de proies, mais aussi la richesse spécifique.

Etude de cas : effet de l’introduction d’un prédateur sur une communauté de proies

On voit que :

- L’amplitude des tailles peut changer
    
- Les tailles peuvent changer (les proies deviennent toutes plus petites par rapport à leur taille sans présence de prédateur) : changement des abondances relatives dans chaque classe de taille
    
- La fréquence de chaque taille peut changer (moins de classe de tailles, effet sur la richesse spécifique)
    

Donc, la prédation élimine les classes grandes tailles et favorise l’abondance des classes petites tailles.

En présence du prédateur qui se spécifie sur les organismes de grande taille, ainsi, la prédation des proies de grande taille sur celle de petite taille diminue (= augmentation des proies de petite taille). De plus, la prédation modifie la compétition : les organismes de grandes et de petites tailles présentent des niches qui se chevauchent.

**V/ La dynamique des communautés**

Les assemblages d’espèces évoluent au cours du temps, c’est un phénomène qui peut s’appliquer au processus de succession écologique.

La succession est un processus qui commence par une étape de colonisation du biotope et qui présente ensuite des changements de communautés d’espèces au cours du temps. Elle se caractérise par des stades marquants présentant des assemblages particuliers d’espèces. Plus on avance dans la succession, plus le recyclage de la matière est efficace, et plus les communautés produisent de biomasse.

  
  

  
  

  
  

  
  

Exemple de la succession végétale du Massif Central :

![](file:///C:/Users/tomha/AppData/Local/Temp/lu929246kmhy.tmp/lu929246kmi1_tmp_4eea7d4fb3dd101b.png)

On peut retracer la présence de végétation dans l’ordre chronologique : plus le pollen est abondant, plus la végétation était dominante à l’époque, et plus il est enfoui, plus il est vieux.

Ici : Chênaie -> Hêtraie sapinière -> Prairie/Culture -> Pinède

On passe de chênaie à hêtraie par refroidissement climatique, de hêtraie à prairie/culture par l’activité humaine, et de prairie/culture à pinède par activité humaine.

On peut donc interpréter ces successions pour reconstituer l’histoire phytologique du milieu.