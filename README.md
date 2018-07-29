# FUN_abc_langageC


## S2.2 - Nombre à virgule
### Votre mission
Vous décidez de partir pour quelques jours de randonnée à la montagne avec un ami américain. Le problème est que toutes les distances indiquées sur les panneaux sont en kilomètres et non en miles (pour votre ami américain). Vous aimeriez être en mesure de faire les conversions automatiquement pour l'aider à se rendre compte des distances.

Écrivez un programme qui lit un nombre décimal (un nombre à virgule) représentant un nombre de kilomètres et affiche le nombre de miles correspondant, avec 6 chiffres après la virgule. Un kilomètre vaut exactement 0,621371 miles.

Entrée => Nombre décimal représentant un nombre de kilomètres : 4.8
Sortie => Nombre avec 6 chiffres après la virgule représentant un nombre de miles correspondant : 2.982581

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
