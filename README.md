# Producteurs consommateurs
## Problème
Deux classes de processus
Les producteurs produisent de l'information et la place dans un
buffer partagé
Les consommateurs traitent de l'information en allant la chercher
dans un buffer partagé

Comment coordonner ces processus ?

```
 _ _ _ _ _ _ _
|_|_|_||_|_|_|

```

```
/**Initialisation **/
Semaphore mutex = 1 ;
Semaphore empty = N ;
Semaphore full = 0 ;

Void producer(void)
{
int item;
while(TRUE)
{
item=produce(item);
down(&empty);
down(&mutex);
insert_item();
up(&mutex);
up(&full);
}
}
```

```
void consumer(void)
{
int item;
while(TRUE)
{
down(&full);
down(&mutex);
item=remove(item);
up(&mutex);
up(&empty);
}
```

Mutex : exclusion mutuelle pour l'accès au buffer
Empty : nombre de places libres dans le buffer
Full : nombre de places occupées dans le buffer

Implémenter dans le langage de votre choix l'algorithme. Les producteurs produisent
toutes les 2 secondes tandis que les consommateurs produisent toutes les 6 secondes.

Vous devez donner le choix à l'utilisateur de saisir au démarrage du programme le
nombre de producteurs, le nombre de consommateurs et le nombres d'élements maximum 
à produire (i.e la taille de la mémoire partagée).

Donner la possibilité d'afficher toutes les secondes le contenu de la mémoire partagée.
