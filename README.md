# MOOC FUN : abc du langage C

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
