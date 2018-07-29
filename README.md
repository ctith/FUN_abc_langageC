# MOOC FUN : abc du langage C


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

## S2.5 - les Tableaux

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
