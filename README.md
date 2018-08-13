# MOOC FUN : abc du langage C

# Semaine 1 : Les fondamentaux pour écrire en langage C

## S1.3 - Boucles et répétitions
```c
+-----------------------+
| o | X | o | X | o | X |
| X | o | X | o | X | o |
| o | X | o | X | o | X |
| X | o | X | o | X | o |
| o | X | o | X | o | X |
| X | o | X | o | X | o |
+-----------------------+
```
```c
#include <stdio.h>

int main() {
	printf("+");
	for (int i = 0; i < 23; i++)
		printf("-");
	printf("+\n");

	for (int i = 0; i < 3; i++){
		printf("| o | X | o | X | o | X |");
		printf("\n");
		printf("| X | o | X | o | X | o |");
		printf("\n");
	}

	printf("+");

	for (int i = 0; i < 23; i++)
		printf("-");
	printf("+");
	
    return 0;
}
```

## S1.5 - Calcul
### Votre mission
Vous travaillez pour le bureau international des procrastineurs. Ce bureau vous a demandé combien de temps il reste avant la journée de la procrastination (le 25 mars).

La requête ayant été réalisée le 23 mars, nous vous invitons à leur offrir les formats d'affichage suivants :

> Cher procrastineur,
Il vous reste X jours, soit Y minutes donc Z secondes avant de pouvoir procrastiner !
				
Rappel : X est le nombre de jours restants, soit 25-23; Y est le nombre de minutes qu'il y a dans 25-23 jours, soit 60*24*(25-23) minutes, et Z est le nombre de secondes, soit 60*60*24*(25-23) secondes !

Attention ! L'invitation précédente est en réalité une exigence importante, et nous vous demandons de la respecter méticuleusement. Le format doit donc absolument être respecté au caractère près.

```c
#include <stdio.h>
int main()
{
	printf("Cher procrastineur,\n");
	printf("Il vous reste %d jours, ", 25 - 23);
	printf("soit %d minutes ", 2 * 24 * 60);
	printf("donc %d secondes avant de pouvoir procrastiner !\n", 48 * 3600);

	return 0;
}
```	
## S1.6 - Variables et boucles

### Votre mission
Votre camarade a beaucoup de mal avec les tables de multiplication, en particulier celle de 8! En effet, on sait tous que c'est la plus dure à mémoriser. Il vous a donc demandé de lui envoyer la table afin qu'il puisse l'apprendre correctement. Pour cela, vous décidez d'écrire un programme qui affiche les produits par 8 de 0 à 10.

Afin d'accomplir cette tâche, et de réutiliser ce programme pour toutes les autres tables rapidement, vous utiliserez une boucle.
```c	
#include <stdio.h>

int main(){
    int nombre = 0;
    for(int i=0 ; i<11 ; i++){
        printf("%dx8 = %d\n",nombre,nombre*8);
        nombre=nombre+1;
    }
    return 0;
}
```	

## S1.7 - lire les entrées du programme

### Votre mission
Voici enfin votre dernière activité de la semaine, profitez-en pour appliquer tout ce que vous avez appris correctement !
Nous en avons désormais la confirmation, David a besoin d'aide, et vite. Il se trouve que Goliath est beaucoup plus imposant que David le pensait.
Heureusement David n'est pas à court de ressources et il a prévu d'envoyer des robots combattre le géant. Mais avant de lancer l'assaut, il doit évaluer les performances de ces robots.

On vous donne sur la première ligne le nombre de robots puis sur chaque ligne suivante la hauteur, le poids, la puissance des moteurs et un coefficient entier (1,2, ou 3) de résistance de chacun de ces robots, et vous devez calculer la puissance de frappe totale de ses robots.
La puissance de frappe d'un robot est définie comme étant :

> (puissance_moteur+coefficient) * (poids - taille) 

La puissance de frappe de tous les robots est la somme de la puissance de frappe de chacun des robots

Voici un exemple de ce que votre programme doit faire :

Par exemple, si on vous donne l'entrée suivante :
>2
50 60 2 1
43 62 5 2

Vous devez afficher la sortie suivante :
>163

Qui correspond au calcul
>(2+1)*(60-50) + (5+2)*(62-43)

Vous devez utiliser une boucle pour lire chacune des lignes !
Pour rappel, votre programme doit permettre à David de s'adapter à n'importe quelle armée qu'il donne en entrée, et pas seulement celle donnée en exemple

```c
#include <stdio.h>
int main() {
    int nbRobots;
    int poids,taille,puissance,coeff;
    int total = 0;

    scanf("%d", &nbRobots);
    for(int i=0 ; i < nbRobots ; i++){
        scanf("%d %d %d %d",&taille,&poids,&puissance,&coeff);
        total = total + (poids-taille)*(puissance+coeff);
    }
    printf("%d", total);
    return 0;
}
```

# Semaine 2 : Vos premiers programmes en langage C
## S2.2 - Nombre à virgule
### Votre mission
Vous décidez de partir pour quelques jours de randonnée à la montagne avec un ami américain. Le problème est que toutes les distances indiquées sur les panneaux sont en kilomètres et non en miles (pour votre ami américain). Vous aimeriez être en mesure de faire les conversions automatiquement pour l'aider à se rendre compte des distances.

Écrivez un programme qui lit un nombre décimal (un nombre à virgule) représentant un nombre de kilomètres et affiche le nombre de miles correspondant, avec 6 chiffres après la virgule. Un kilomètre vaut exactement 0,621371 miles.

> Entrée => Nombre décimal représentant un nombre de kilomètres : 4.8
 
> Sortie => Nombre avec 6 chiffres après la virgule représentant un nombre de miles correspondant : 2.982581

```c
#include <stdio.h>

int main(){
    double km, miles ;
    scanf("%lf", &km);
    miles = km * 0.621371;
    printf("%.6lf",miles);
    return 0;
}
```

## S2.3 - Divisions

### 1. Votre mission : les températures
Après tant de miles parcourus, vous décidez de camper. Il vous faut désormais dîner, mais votre réchaud électrique n'est réglable qu'en degrés Fahrenheit ! Il vous faut donc convertir les températures des degrés Celsius vers les degrés Fahrenheit.

Écrivez un programme qui lit un nombre décimal (un nombre à virgule) représentant une température en degrés Celcius et affiche la température en degrés Fahrenheit avec 1 chiffre après la virgule. Temperature(°F) = Temperature(°C) × 9.0/5.0 + 32.0

> Entrée => Nombre décimal représentant une température en degrés Celcius : 42

> Sortie => Nombre avec 1 chiffre après la virgule représentant une température en degrés Farenheit : 107.6

```c
#include <stdio.h>

int main(){
    double celsius;
    scanf("%lf", &celsius);
    printf("%.1lf" , celsius* 9.0/5.0 + 32.0);
    return 0;
}
```
### 2. Votre mission : ranger des allumettes
Vous avez des allumettes que vous voulez répartir par boîtes. Créez un programme qui calcule combien de boîtes complètement pleines il y aura. Ce programme devra aussi afficher le nombre d'allumettes restantes (ne remplissant pas totalement la dernière boîte).

> Entrée => Votre programme lira dans l’entrée le nombre d’allumettes et la capacité d’une boîte (nombre d’allumettes pour la remplir complètement).
666
13

> Sortie => Il affichera le nombre de boites pleines et le nombres d’allumettes restantes.
51
3

```c
#include <stdio.h>

int main(){
    int nbAllumette, capaciteBoite;
    int nbBoitePleine = 0;
    int nbAllumetteRestante = 0;
    scanf("%d",&nbAllumette);
    scanf("%d",&capaciteBoite);
    printf("%d\n",nbBoitePleine = nbAllumette / capaciteBoite);
    printf("%d",nbAllumetteRestante = nbAllumette % capaciteBoite);
    return 0;
}
```

## S2.4 - Conversion

### 1. Votre mission : calcul de moyenne
Un professeur a tellement de classes qu'il passe trop de temps à calculer les moyennes de ses élèves. Pour l'aider, vous allez devoir écrire un programme qui calcule les moyennes à partir des notes données.

> Entrée => Votre programme doit d'abord lire un premier entier, qui décrit le nombre de notes obtenues. Ensuite, il doit lire chacune de ces notes, qui sont également des nombres entiers.
4
10
8
16
9

> Sortie => Votre programme devra afficher la moyenne avec 2 chiffres après la virgule.

10.75

```c
#include <stdio.h>
int main (){
    int nbNote, note;
    int somme = 0;

    scanf("%d", &nbNote);
    for(int i = 0; i < nbNote ; i++) {
        scanf("%d", &note);
        somme = somme + note;
    }
    double sommeVirgule = (double)somme;
    printf ("%.2lf", sommeVirgule/nbNote);
    return 0;
}
```

### 2. Votre mission : calcul de population
Ces dernières années, la population de votre ville a très fortement augmenté, grâce à un fort taux de natalité. Cela pose cependant un certain nombre de problèmes, notamment une pénurie de logements ! Le maire a décidé de s'occuper du problème et souhaiterait estimer l'évolution future de la population.

Votre programme devra lire un entier, la population actuelle de la ville, puis un nombre décimal, la croissance prévue de la population, en pourcentage. Il devra alors afficher la nouvelle population de la ville sous la forme d'un nombre entier. On considérera, par convention, qu'une population de 31,4 habitants signifie qu'il y a 31 habitants, on ne compte donc que les habitants « entiers » !

> Entrée => 456 -5.5

> Sortie => 430

```c


```

### 3. Votre mission : achat de livres
Vous commencez à apprendre une nouvelle langue et décidez d'acheter quelques livres pour vous entraîner. Vous trouvez un vendeur qui propose de nombreux livres à des prix avantageux. Vous disposez d'une certaine somme d'argent et vous vous demandez combien de livres vous pouvez acheter, sachant qu'ils sont tous au même prix.

Votre programme doit commencer par lire la somme d'argent dont vous disposez (nombre à virgule) et lira ensuite le prix d'un livre (nombre à virgule). Il devra ensuite afficher un entier, le plus grand nombre de livres qu'il vous est possible d'acheter avec cette somme d'argent.

> Entrée => 48.0 3.50  

> Sortie => 13

```c
#include <stdio.h>

int main(){
    double argent, prixLivre;
    int nbLivre;
    scanf("%lf %lf", &argent, &prixLivre);
    
    nbLivre = (int) argent / prixLivre;
    printf("%d", nbLivre);
    
    return 0;
}
```

### 4. Votre mission : construction maison
Pour la construction de votre nouvelle maison, vous avez calculé la quantité de ciment nécessaire pour construire les fondations. De nature économe, vous souhaitez acheter exactement la quantité nécessaire mais malheureusement le magasin ne vend le ciment qu'en gros sacs. Vous souhaitez calculer combien tout cela va vous coûter.

Votre programme devra lire un nombre décimal, la quantité de ciment nécessaire pour les fondations de votre nouvelle maison, en kilos. Sachant que le ciment n'est vendu qu'en sacs de 60 kilos et qu’un sac coûte 45 euros, votre programme devra afficher le coût total du ciment.

> Entrée => Votre programme devra lire un nombre décimal, la quantité de ciment nécessaire pour les fondations de votre nouvelle maison, en kilos : 145.8
! On vous garantit que la quantité de ciment nécessaire ne sera JAMAIS un multiple de 60 (pour raison de simplification du programme)

> Sortie => Votre programme devra afficher le coût total du ciment : 135

```c
#include <stdio.h>

int main(){
    double kg = 0.0;
    double sac = 60.0;
    int prix = 45;
    int prixTot = 0;
    
    scanf("%lf", &kg);
    
    for(int i=0; i< kg/sac; i++){
        prixTot += prix;
    }
    
    printf("%d", prixTot);
    return 0;
}
```

## S2.5 - conditions, opérateur de test et logique

## 1. Votre mission : covoiturage
Pour partager les coûts de mon trajet en voiture, je propose une annonce sur un site de covoiturage.

Si j’ai 0 passager, le site de covoiturage ne me facture rien et je vais payer la totalité des coûts.
Si j’ai 1, 2 ou 3 passagers, le site de covoiturage ajoute 1 euro de frais (à ajouter au coût du trajet) et on divise le coût entre nous (moi compris).
Je veux écrire un programme qui calcule le coût qu’il me reste à payer.

> Entrée => En entrée du programme nous aurons d’abord le nombre de passagers (un nombre entier) puis le coût total du trajet (un nombre à virgule) : 0 23.9

> Sortie => En sortie, le coût qu’il me reste à payer (un nombre à virgule) avec 2 chiffres après la virgule : 23.90

```c
#include <stdio.h>

int main(){
    int nbPassager = 0;
    double coutTotal = 0.0;
    double coutReel = 0.0;
    
    scanf("%d %lf", &nbPassager, &coutTotal);
    
    if (nbPassager == 0){
        coutReel = coutTotal;
    } else {
        nbPassager = (double) nbPassager;
        coutReel = (coutTotal + 1) / (nbPassager + 1);
    }
    
    printf("%.2lf", coutReel);
    return 0;
}
```

## 2. Votre mission : tarifs dégressifs
L'auberge dans laquelle vous avez prévu de passer la nuit ce soir propose des tarifs très intéressants, pour peu que l'on n'arrive pas trop tard. En effet, plus on arrive tôt moins on devra payer. Vous essayez de construire un programme vous donnant directement le prix à payer en fonction de votre heure d'arrivée.

Votre programme lira un entier, l'heure d'arrivée, qui sera compris entre 0 et 12 inclus (soit midi à minuit). Le prix de base est de 10 euros plus 5 euros pour toute heure après midi. Il ne peut cependant pas dépasser 53 euros. Votre programme devra afficher le prix à payer correspondant à l'heure d'arrivée donnée.

> Entrée => 7

> Sortie => 45

```c
#include <stdio.h>
int main() {
    int heureArrivee = 0;
    scanf("%d", &heureArrivee);
    int total = 10+5*heureArrivee; // car l'heure d'arrivée est entre midi et minuit dans l'énoncé
    int totalDepasse53 = total > 53;
    if(totalDepasse53){
        printf("53");
    }else{
        printf("%d", total);
    }
    return 0;
}
```

## 3. Votre mission : ponts et taxes
Vous arrivez devant un pont que vous devez absolument emprunter pour arriver avant la nuit au village situé de l'autre côté de la rivière. Cependant, la traversée du pont n'est pas gratuite et le tarif dépend de votre chance au jeu. En effet, le gardien vous demande de lancer deux dés et le prix dépendra des valeurs que vous obtiendrez. Vous décidez d'écrire un programme pour vérifier qu'il applique bien le bon tarif.

Votre programme doit lire deux entiers, compris entre 1 et 6, la valeur de chaque dé. Si la somme est supérieure ou égale à 10, alors vous devez payer une taxe spéciale (36 pièces). Sinon, vous payez deux fois la somme des valeurs des deux dés. Votre programme devra afficher selon le cas le texte « Taxe spéciale ! » ou bien « Taxe régulière », puis la somme à payer (sans indiquer l'unité).

> Entrée => 5 6

> Sortie => Taxe spéciale ! 36

```c
#include <stdio.h>

int main(){
    int de1,de2;
    scanf("%d %d", &de1, &de2);
    
    if (de1+de2 >= 10){
        printf("Taxe spéciale !\n36");
    }else {
        printf("Taxe régulière\n%d", (de1+de2)*2);
    }
    return 0;
}
```

## 4. Votre mission : concours de tir à la corde
Un championnat de tir à la corde est organisé. Vous décidez alors de vous engager dans les paris qui se font sur les deux équipes qui concourent. Les deux équipes vont tirer une corde le plus fort possible, chacune de leur côté; jusqu’à ce qu’une équipe dépasse une ligne délimitée au sol. C’est à ce moment que l’équipe qui a tiré “le moins fort” a perdu, et l’autre a gagné !

Ce championnat oppose deux équipes, contenant chacune autant de joueurs. Pour donner de l'allure et pimenter les paris, au début du championnat, tous les joueurs sont présentés, avec leur poids, avant d'aller tenir leur côté de la corde. Il est d'abord présenté un membre de la première équipe, puis de la deuxième, puis de la première, puis de la deuxième etc. jusqu'à ce que tous les joueurs soient passés. Afin de vous faire un premier pronostic, vous calculez le poids total de chaque équipe, avec votre programme.

Votre programme devra lire un premier entier : le nombre de membres nbMembres qui constituent une équipe. Ensuite, il devra lire les poids (un entier représentant des kilogrammes), au total nbMembres × 2, sachant que le premier poids est celui d'un joueur de la 1re équipe, le deuxième poids celui d'un joueur de la 2e équipe, le troisième la 1re équipe, le quatrième la 2e équipe, etc.
Après avoir calculé le poids total de chaque équipe, vous devrez afficher le texte « L'équipe X a un avantage » (en remplaçant X par la valeur 1 ou 2), en considérant qu'une équipe est avantagée si elle a un poids total supérieur à celui de l'autre.

Vous afficherez ensuite le texte « Poids total pour l'équipe 1 : » suivi du poids de l'équipe 1, puis « Poids total pour l'équipe 2 : » suivi du poids de l'équipe 2 (voir l'exemple ci-dessous).

On vous garantit que les deux équipes n'auront pas le même poids total.

### Exemple
Chaque équipe est composée de trois joueurs. Ceux de la première pèsent 40, 50 et 60 kg, tandis que ceux de la seconde font 80, 50 et 10 kg. Cela fait 150 kg opposés à 140 kg.

> Entrée => 3 40 80 50 50 60 10

> Sortie => L'équipe 1 a un avantage
Poids total pour l'équipe 1 : 150
Poids total pour l'équipe 2 : 140

```c
#include <stdio.h>
int main(){
    int nbMembres;
    int poids1;
    int poids2;
    int sommePoids1 = 0;
    int sommePoids2 = 0;
    
    scanf("%d", &nbMembres);
    
    for(int i=0; i<nbMembres; i++){
    	scanf("%d", &poids1);
    	scanf("%d", &poids2);
    	sommePoids1 = sommePoids1 + poids1;
    	sommePoids2 = sommePoids2 + poids2;
    }
    
    if(sommePoids1>sommePoids2){
        printf("L'équipe 1 a un avantage\n");
    } else {
        printf("L'équipe 2 a un avantage\n");
    }
    printf("Poids total pour l'équipe 1 : %d\n", sommePoids1);
    printf("Poids total pour l'équipe 2 : %d\n", sommePoids2);
    
    return 0;
}
```

### 5. Votre mission : tarif et age
L'auberge dans laquelle vous vous arrêtez pour la nuit adapte ses prix en fonction de l'âge du client et du poids de ses bagages. Les règles ne vous étant pas très claires, vous décidez d'écrire un petit programme qui vous permettra facilement, à vous et à vos compagnons de voyage, de connaître le prix d'une nuit.

Une chambre ne coûte rien si on a 60 ans (l'âge de l'aubergiste !) et 5 euros si on a strictement moins de 10 ans. Pour les autres personnes c'est 30 euros plus un supplément de 10 euros si on a au moins 20 kilos de bagages.

> Entrée => Votre programme doit lire deux entiers, l'âge et le poids des bagages de la personne : 22 25

> Sortie => Votre programme doit afficher le prix, sous la forme d'un entier : 40

```c
#include <stdio.h>

int main(){
    int age, poids, prix;
    scanf("%d %d", &age, &poids);
    
    if (age == 60){
        prix = 0;
    } else if (age < 10){
        prix = 5;
    } else {
        prix = 30;
        if (poids >=20){
            prix = prix + 10;
        }
    }
    printf("%d", prix);
    return 0;
}
```
### 6. Votre mission : dans la forêt
Alors que vous traversez une forêt vous ne pouvez vous empêcher d'admirer la végétation autour de vous et notamment les nombreuses espèces d'arbres. Malgré votre intérêt, vous êtes très mauvais botaniste et avez beaucoup de mal à identifier les différents arbres. Une personne que vous croisez vous donne quelques indications et vous décidez d'écrire un programme qui vous donnera le nom de l'arbre en fonction de ses caractéristiques.

Il existe 4 types d'arbres :

le "Tinuviel" fait moins de 5 mètres de haut et ses feuilles sont composées de plus de 8 folioles
le "Calaelen" fait plus de 10 mètres de haut et ses feuilles sont composées de plus 10 folioles
le "Falarion" fait moins de 8 mètres de haut et ses feuilles sont composées de moins de 5 folioles
le "Dorthonion" fait plus de 12 mètres de haut et ses feuilles sont composées de moins de 7 folioles
Votre programme lira deux entiers, la hauteur et le nombre de folioles de l'arbre, et affichera le nom de l'arbre correspondant. Toutes les inégalités sont à prendre au sens large, c'est-à-dire que "moins" signifie "moins ou égal" ou et "plus" signifie "plus ou égal".

> Entrée => 12 12

> Sortie => Calaelen

```c
#include <stdio.h>

int main(){
    int hauteur, nbfoliole;
    scanf("%d %d", &hauteur, &nbfoliole);
    
    if (hauteur <= 5 && nbfoliole >= 8)
        printf("Tinuviel");
    if (hauteur >= 10 && nbfoliole >= 10)
        printf("Calaelen");
    if (hauteur <= 8 && nbfoliole <= 5)
        printf("Falarion");
    if (hauteur >= 12 && nbfoliole <= 7)
        printf("Dorthonion");
    
    return 0;
}
```

## S2.6 - les Tableaux

## Votre mission : tableau et ingrédients
Vous avez une superbe recette de cuisine avec 10 ingrédients. Mais vous ne vous souvenez jamais quelle quantité de chaque ingrédient il faut mettre pour réussir cette fameuse recette !

Il y a 10 ingrédients dans la recette et les quantités nécessaires pour chacun sont données en entrée (en grammes).

> Entrée => Votre programme doit lire 10 entiers (les quantités nécessaires pour chacun des ingrédients) et les stocker dans un tableau.
Il doit ensuite lire un entier correspondant au numéro d'un ingrédient (compris entre 0 et 9)
500 180 650 25 666 42 421 1 370 211
3


> Sortie => Votre programme doit afficher la quantité associée au numéro de l'ingrédient. Par exemple ici 3 correspondant à la case numérotée 3 du tableau (donc le quatrième ingrédient) : 25

```c
#include <stdio.h>

int main() {
    int tableau[10];
    int valeurLue = 0;
    int numeroDeCase = 0;  

    for(int i = 0 ; i < 10 ; i ++){
        scanf("%d", &valeurLue);
        tableau[numeroDeCase] = valeurLue;
        numeroDeCase = numeroDeCase + 1;
    }
    scanf("%d",&numeroDeCase);
    printf("%d", tableau[numeroDeCase]);
    return 0;
}
```
# Semaine 3 : Les fonctions et les chaînes de caractère
## S3.1 - la boucle FOR et les structures imbriquées

### 1. Votre mission : répartition du poids
Vous êtes responsable d'un convoi de marchandises composé de plusieurs wagons. Vous faites démarrer le train et après seulement quelques minutes vous vous rendez compte que certains wagons sont surchargés et appuient beaucoup trop sur les rails alors que d'autres sont très légers et ont les roues qui volent. Vous décidez donc d'arrêter le train et de mieux répartir le poids, afin que tous les wagons aient exactement le même poids. Pour cela vous écrivez rapidement un programme qui vous aide dans la répartition du poids des wagons.

Vous avez la possibilité de peser chacun des wagons individuellement. Vous aurez donc pour chaque wagon le poids des marchandises qu'il transporte.

Votre programme doit déterminer quel poids ajouter ou retirer à chaque wagon, pour qu'ils transportent toutes ensuite le même poids, et ce sans modifier le poids total transporté par l'ensemble du train.

Entrée : L'entrée commence par un entier nbWagons (nbWagons <= 50) : le nombre de wagons du train. Les nbWagons lignes suivantes décrivent chacunes des wagons par un nombre décimal : le poids transporté initialement.

Sortie : Vous devez afficher nbWagons nombres décimaux (avec 1 chiffre après la virgule) sur la sortie : le poids à ajouter à chaque wagon (ce qui revient à en retirer si ce nombre est négatif), dans le même ordre que celui de l'entrée, avec 1 seul chiffre après la virgule.

### Exemple
Dans cet exemple, on a 5 wagons avec des poids différents. La sortie montre qu'on modifie tous les wagons pour qu'ils transportent chacun un poids de 22.0, soit un total de 110.0 pour le train, comme au départ. On enlève donc 18.0 pour le premier wagon, on ajoute 10.0 pour le deuxième, on ajoute 2.0 pour le troisième etc...

> entrée : 5 40.0 12.0 20.0 5.0 33.0

> sortie : -18.0 10.0 2.0 17.0 -11.0

```c
```

### 2. Votre mission : prix au kilo
Vous partez faire des courses pour une délicieuse recette et voulez prendre l'argent dont vous avez besoin pour acheter les ingrédients. Heureusement vous savez à l'avance le prix au Kg de chaque ingrédient et la quantité exacte dont vous avez besoin pour chaque ingrédient.

Le programme lira dans l'entrée le nombre d'ingrédients (au MAXIMUM 10), puis pour chaque ingrédient le prix au Kg. Enfin, pour chaque ingrédient le poids nécessaire pour la recette.

Votre programme devra calculer le coût total de ces achats, l'afficher avec 6 chiffres après la virgule.

### Exemple
Il y a 4 ingrédients et ils ont tous un prix au kilo différent : 9.90 5.50 12.0 et 15.0. Vous devez prendre 250 grammes du premier, 1.5Kg du deuxième, 300 grammes du troisième et 1Kg du quatrième. Cela va coûter 29.325000 euros exactement.
> entrée : 4
9.90 5.50 12.0 15.0
0.250 1.5 0.300 1.0

> sortie : 29.325000

```c
```

### 3. Votre mission : villes et villages
Vous voulez savoir combien il y a de villes de plus de 10 000 habitants dans une certaine région.

Ce que doit faire votre programme : on vous donne le nombre d'habitants d'un certain nombre de lieux d'une région. Une ville étant un lieu dont la population est strictement supérieure à 10000 habitants, déterminez combien de lieux sont des villes.

> Entrée : Votre programme doit lire un premier entier en entrée: le nombre de lieux de la région. Il doit ensuite lire, pour chaque lieu, un entier donnant le nombre de gens qui y habitent.
6
1000
5000
15000
4780
0
23590

> Sortie : Votre programme doit alors afficher le nombre de villes.
2

```c
```

### 4. Votre missions : boucles imbriquées
Réalisez un programme qui affiche à l'écran un carré de n x n étoiles, l'entier n étant donné en entrée.

> Entrée: 5

> Sortie:
*****
*****
*****
*****
*****

```c
```

## S3.2 - la boucle WHILE

### 1. Votre mission : dépenses d'une université
Une grande partie du travail de l'administration d'une université, en plus de gérer les enseignants, les chercheurs, les étudiants, les cours… est de veiller au bon fonctionnement de l'université et en particulier à ce que les comptes soient bien tenus. Il faut, une fois par an, faire un bilan annuel des dépenses.

Toutes les dépenses de l'année ont été enregistrées et classées dans une multitude de dossiers et il faut maintenant calculer la somme de toutes ces dépenses. Mais personne ne sait exactement combien de dépenses différentes ont été effectuées durant l'année écoulée !

Votre programme devra lire une suite d'entiers positifs et afficher leur somme. On ne sait pas combien il y aura d'entiers, mais la suite se termine toujours par la valeur -1 (qui n'est pas une dépense, juste un marqueur de fin).

> Entrée: 1000 2000 500 -1

> Sortie: 3500

```c
```

### 2. Votre mission : contrôle d'une épidémie
Afin de pouvoir mieux combattre les différentes épidémies, parfois très graves, qui se développent régulièrement dans une région, le département de médecine d'une université a lancé une grande étude. En particulier, les chercheurs s'intéressent à la vitesse de propagation d'une épidémie et donc à la vitesse à laquelle des mesures sanitaires doivent êtres mises en place.

Votre programme doit d'abord lire un entier, la population totale de la région. Sachant qu'une personne était malade au jour 1 et que chaque malade contamine deux nouvelles personnes le jour suivant (et chacun des jours qui suivent), vous devez calculer à partir de quel jour toute la population de la région sera malade.

#### Exemple 1
Pour une population totale de 3 habitants, le jour 1 une personne est malade. Le jour suivant elle contamine 2 nouvelles personnes donc il y a au total 3 contaminés. C'est la totalité de la population donc il faut 2 jours pour contaminer la totalité de la population.

> Entrée: 1000 2000 500 -1

> Sortie: 3500

#### Exemple 2
Pour une population totale de 10. On a 1 malade le premier jour, donc 2 nouveaux malades le second jour, soit un total de 3 malades. On a donc 6 nouveaux malades au troisième jour, soit un total de 9 malades. On a donc 18 nouveaux malades au quatrième jour, soit etc...

> Entrée: 10

> Sortie: 4

```c
```

### 3. Votre mission : c'est plus, c'est moins
Dans une cité commerçante, il est important que les habitants soient forts en calcul mental afin de pouvoir négocier leurs prix et choisir les meilleurs produits sans se faire avoir. Le département de pédagogie de l'université a donc été sollicité afin de mettre au point des exercices stimulants pour les enfants, qui vont les inciter à travailler leur calcul mental.

Les chercheurs vous demandent de mettre au point un programme capable de faire jouer de manière automatisée un enfant au jeu du « c'est plus, c'est moins » : l'enfant doit deviner un nombre secret en faisant des propositions, et on lui répond chaque fois par « c'est plus » ou « c'est moins », jusqu'à ce qu'il ait trouvé le bon nombre.

L'objectif est bien sûr pour les enfants de trouver le bon nombre le plus rapidement possible !

Ce que doit faire votre programme :

Votre programme doit d'abord lire un entier, le nombre que l'enfant devra trouver.

Ensuite, il devra lire les propositions du joueur, et afficher à chaque fois le texte « c'est plus » (l'enfant a proposé un nombre trop petit) ou « c'est moins » (l'enfant a proposé un nombre trop grand) selon les cas, et recommencer tant que l'enfant n'a pas trouvé le bon nombre.

À la fin, il faudra afficher le texte « Nombre d'essais nécessaires : » puis, à la ligne en dessous, le nombre d'essais qui ont été nécessaires.

On vous garantit que l'enfant finira par trouver la bonne valeur !

#### Exemple 1

> Entrée: 5 
1 2 3 4 5

> Sortie: c'est plus
c'est plus
c'est plus
c'est plus
Nombre d'essais nécessaires :
5

#### Exemple 2
> Entrée: -50
-80
-50

> Sortie: c'est plus
Nombre d'essais nécessaires :
2

```c
```

### 4. Votre mission : surveillance d'une expérience de chimie
Les chimistes de l'université ont mis au point un nouveau procédé de fabrication d'un médicament qui permet une cicatrisation très rapide des blessures. Ce procédé est cependant très long et nécessite une surveillance de tous les instants de la préparation en train de chauffer, et ce parfois pendant des heures. Confier cette tâche à un étudiant n'est pas possible, ils s'endorment toujours ou ne font pas attention… et cela risque alors d'exploser !

Un dispositif automatique de surveillance de la préparation serait donc intéressant. Celui-ci surveillerait la température toutes les 15 secondes, et si celle-ci devient anormale alors une alarme devrait sonner, afin de prévenir tout le monde.

Votre programme devra lire deux entiers : la température minimum et maximum autorisées. Les entiers suivants seront les différentes températures relevées au cours du temps. On consière qu'une valeur de -999 veut dire "fin du relevé des températures"

Si les températures relevées restent dans le bon intervalle (elles peuvent être aussi égales aux valeurs min ou max), votre programme devra écrire le texte « Rien à signaler », mais dès que la température n'est pas bonne il doit écrire le texte « Alerte !! » et s'arrêter.

#### Exemple 1
> Entrée: 10 20
15 10 20 0 15 -999

> Sortie: Rien à signaler
Rien à signaler
Rien à signaler
Alerte !!

#### Exemple 2
> Entrée: 0 100
15 50 75 -999

> Sortie: Rien à signaler
Rien à signaler
Rien à signaler

```c
```
## S3.3 - les chaînes de caractères

### 1. Votre mission : surveillance d'une expérience de chimie
Réalisez un programme qui répète un mot. Le nombre de répétitions et le mot seront donnés en entrée du programme.

#### Exemple 1
> Entrée: 2 bonjour

> Sortie: bonjour
bonjour

#### Exemple 2
> Entrée: 4 truc

> Sortie: truc
truc
truc
truc

```c
```

### 2. Votre mission : inversion prénom/nom
Au sein de la bibliothèque municipale, toutes les personnes souhaitant emprunter un livre doivent s'enregistrer en indiquant leurs noms et prénoms sur une fiche individuelle conservée à l'accueil.

L'habitude veut qu'ils écrivent d'abord leur nom puis leur prénom, ce qui permet de classer les fiches par ordre alphabétique et permet de rapidement retrouver la fiche qu'on cherche.

Malheureusement, depuis un mois, dans toutes les nouvelles fiches créées les personnes ont indiqué en premier leur prénom puis leur nom !

- Contraintes: Chaque nom et prénom est au plus de longueur 100 et ne contient pas d'espace.
- Entrée : Sur la première ligne, un entier nbPersonnes : le nombre total de personnes concernées. Sur chacune des nbPersonnes lignes suivantes, un prénom et un nom, séparés par un espace.
- Sortie: Pour chaque personne, vous devez écrire sur la même ligne son nom, puis son prénom, séparés par un espace.

Votre travail consiste à lire ces couples de prénoms et noms et à les afficher dans le bon ordre.

#### Exemple 1
> Entrée: 4
Alan Turing
Ada Lovelace
Donald Knuth
Claude Shannon

> Sortie: Turing Alan 
Lovelace Ada 
Knuth Donald
Shannon Claude

#### Exemple 2
> Entrée: 4 truc

> Sortie: truc
truc
truc
truc

```c
```

### 3. Votre mission : inscription étudiants
Comme chaque année, lors de la rentrée universitaire en spécialité mathématique, de nombreux étudiants viennent s’inscrire à la bibliothèque et une longue file d’attente se forme. Afin d’essayer d'accélérer les choses, les fiches d’inscription de tous les étudiants ont déjà été préparées et ils n’ont plus qu’à les récupérer. On a trouvé une astuce mathématique pour faire deux files d'attente!

Deux personnes sont en charge de distribuer les fiches : la première s’occupe des étudiants dont le nom contient un nombre pair de lettres, la seconde personne des étudiants dont le nom contient un nombre impair de lettres. Cela forme deux files d'attente !

Quand un nouvel étudiant arrive, il donne son nom et il faut lui indiquer quelle personne il doit aller voir.

- Contraintes : Les noms des étudiants font moins de 50 caractères de long.
- Entrée : Un nom d’étudiant.
- Sortie : Un entier, 1 ou 2 selon que l’étudiant doit aller voir la première (nombre de lettre pair) ou la seconde personne (nombre de lettres impair).

#### Exemple 1
> Entrée: Sharrock

> Sortie: 1

#### Exemple 2
> Entrée: Obama

> Sortie: 2

```c
```

### 4. Votre mission : le mot le + long
Vous devez trouver la taille (en nombre de lettres) du plus grand mot dans un texte simplifié. La simplification consiste à enlever tous les caractères spéciaux, les accents et la ponctuation, il ne reste que les mots.

Pour vous aider, vous réalisez un programme qui prend en entrée le nombre de mots du texte, suivi de tous les mots de ce texte. Dans la sortie vous affichez la taille du plus grand mot trouvé !

#### Exemple 1
> Entrée: 17
Ceci est un texte d exemple simplifie
nous devons trouver la taille du mot le plus long

> Sortie: 9

#### Exemple 2
> Entrée: 7
la nuit tous les chats sont gris

> Sortie: 5

```c
```
