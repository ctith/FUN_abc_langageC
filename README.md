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

### 1. Votre mission division
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
### 2. Votre mission modulo
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

## S2.4 - 
