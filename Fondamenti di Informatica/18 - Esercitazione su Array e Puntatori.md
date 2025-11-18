## Introduzione all'Esercitazione su Array e Puntatori

La lezione odierna è una sessione pratica interattiva focalizzata sul consolidamento dei concetti relativi ad array, matrici e puntatori. Verranno affrontati una serie di esercizi volti a fissare le nozioni teoriche e a chiarire eventuali dubbi. In particolare, si esplorerà la creazione di librerie personalizzate tramite compilazione separata e si approfondirà la gestione della memoria tramite puntatori.

## Esercizio 1: Creazione di una Libreria per Vettori Monodimensionali

L'obiettivo di questo esercizio è costruire una libreria per la gestione di array monodimensionali di numeri reali, introducendo un nuovo tipo di dato `vettore`. La libreria dovrà fornire le seguenti funzionalità:

*   Calcolo del valore medio degli elementi dell'array.
*   Calcolo del valore massimo.
*   Calcolo del valore minimo.

L'implementazione seguirà il principio della **compilazione separata**, strutturando il codice in tre file distinti.

### Struttura dei File

Il progetto sarà organizzato come segue:

1.  **`vector.h`**: Il file di intestazione (header) contenente la definizione del nuovo tipo `vettore` e i prototipi delle funzioni della libreria.
2.  **`vector.c`**: Il file di implementazione che contiene il codice sorgente delle funzioni dichiarate nel file `.h`.
3.  **`main.c`**: Il file di test, contenente la funzione `main`, che utilizza la libreria per verificarne il corretto funzionamento.

### File di Intestazione: `vector.h`

Nel file di intestazione si definisce una costante `NMAX` per la dimensione massima degli array e si crea un alias di tipo `vettore` tramite la direttiva `typedef`. Questo approccio, basato sull'allocazione statica, riserva una quantità di memoria fissa per ogni variabile di tipo `vettore`.

```c
#define NMAX 100

typedef double vettore[NMAX];

double media(vettore V, int n);
double massimo(vettore V, int n);
double minimo(vettore V, int n);
```

### File di Implementazione: `vector.c`

Questo file deve includere il corrispondente file di intestazione (`#include "vector.h"`) per poter utilizzare il tipo `vettore` e riconoscere i prototipi delle funzioni da implementare.

#### Implementazione della Funzione `media`
L'algoritmo per il calcolo della media consiste nel sommare tutti gli elementi dell'array e dividere il risultato per il loro numero.

```c
double media(vettore V, int n) {
    double media = 0.0;
    int i;
    for (i = 0; i < n; i++) {
        media += V[i];
    }
    return media / n;
}
```

#### Implementazione della Funzione `massimo`
L'algoritmo di ricerca del massimo inizializza una variabile `massimo` con il primo elemento del vettore. Successivamente, scorre gli `n-1` elementi rimanenti, aggiornando il valore di `massimo` qualora venga trovato un elemento maggiore.

```c
double massimo(vettore V, int n) {
    double massimo = V[0];
    int i;
    // Il ciclo parte da 1 per evitare di confrontare il primo elemento con se stesso.
    for (i = 1; i < n; i++) {
        if (V[i] > massimo) {
            massimo = V[i];
        }
    }
    return massimo;
}
```

#### Implementazione della Funzione `minimo`
L'algoritmo per la ricerca del minimo è duale a quello del massimo. L'unica differenza risiede nell'operatore di confronto, che sarà `<` anziché `>`.

```c
double minimo(vettore V, int n) {
    double minimo = V[0];
    int i;
    for (i = 1; i < n; i++) {
        if (V[i] < minimo) {
            minimo = V[i];
        }
    }
    return minimo;
}
```

### File di Test: `main.c`

Il programma principale include la libreria, dichiara un vettore, acquisisce da tastiera il numero di elementi da inserire e i valori stessi. Infine, invoca le funzioni della libreria e ne stampa i risultati.

```c
#include <stdio.h>
#include "vector.h"

int main() {
    vettore V;
    int n, i;

    printf("Inserisci il numero di elementi: ");
    scanf("%d", &n);

    printf("Inserisci %d numeri reali:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%lf", &V[i]);
    }

    printf("La media dei valori è: %f\n", media(V, n));
    printf("Il valore massimo è: %f\n", massimo(V, n));
    printf("Il valore minimo è: %f\n", minimo(V, n));

    return 0;
}
```

### Compilazione Separata
Per compilare i tre file in un unico eseguibile, si utilizza il seguente comando `gcc`:

```bash
gcc -o vector_test vector.c main.c
```
Questo comando istruisce il compilatore a processare entrambi i file sorgente (`.c`) e a generare un file eseguibile chiamato `vector_test`.

## Esercizio 2: Gestione di Matrici Bidimensionali

Questo esercizio affronta la manipolazione di array bidimensionali (matrici). L'obiettivo è, data una matrice di interi 4x3, calcolare:
1.  La somma di tutti i suoi elementi.
2.  Il valore massimo per ogni riga.

### Implementazione in un Unico File

Per semplicità, l'implementazione sarà contenuta in un unico file sorgente. Vengono definite delle costanti per le dimensioni e un tipo `matrice`.

```c
#include <stdio.h>

#define N 4 // Numero di righe
#define M 3 // Numero di colonne

typedef int matrice[N][M];

int somma(matrice matt, int n, int m);
void massimo_per_riga(matrice matt, int n, int m, int massimi[]);
```

#### Implementazione della Funzione `somma`
Per calcolare la somma totale, è necessario scorrere ogni elemento della matrice tramite due cicli `for` annidati e accumulare i valori in una variabile.

```c
int somma(matrice matt, int n, int m) {
    int i, j;
    int sum = 0;
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            sum += matt[i][j];
        }
    }
    return sum;
}
```

#### Implementazione della Procedura `massimo_per_riga`
Poiché la funzione deve restituire più valori (un massimo per ogni riga), si trasforma in una procedura (`void`) che accetta un array come **parametro di output**. Questo array, passato per riferimento (essendo un array, il suo nome è un puntatore al primo elemento), verrà popolato con i valori massimi di ciascuna riga.

L'algoritmo itera su ogni riga. Per ciascuna riga, inizializza il massimo locale con il primo elemento della riga (`matt[i][0]`) e poi confronta questo valore con gli elementi successivi della stessa riga, aggiornandolo se necessario. Alla fine dell'iterazione su una riga, il massimo trovato viene salvato nell'array di output.

```c
void massimo_per_riga(matrice matt, int n, int m, int massimi[]) {
    int i, j;
    for (i = 0; i < n; i++) {
        int max = matt[i][0];
        for (j = 1; j < m; j++) {
            if (matt[i][j] > max) {
                max = matt[i][j];
            }
        }
        massimi[i] = max;
    }
}
```

## Esercizio 3: Utilizzo Avanzato dei Puntatori con la Funzione `swap`

Questo esercizio analizza l'algoritmo di scambio (`swap`) di valori tra due variabili, implementato in diverse varianti per illustrare l'uso dei puntatori.

### Variante 1: Scambio nel `main` tramite Puntatori
Si definiscono due variabili intere `x` e `y` e due puntatori `px` e `py`. I puntatori vengono inizializzati con gli indirizzi di `x` e `y`. Lo scambio avviene manipolando i valori tramite dereferenziazione (`*`).

```c
int x = 10, y = 5;
int *px, *py;
int temp;

px = &x;
py = &y;

temp = *px;  // Salva il valore di x
*px = *py;   // Assegna a x il valore di y
*py = temp;  // Assegna a y il valore salvato
```

### Variante 2: Procedura `swap` con Parametri di Tipo Puntatore
La logica di scambio viene incapsulata in una procedura che accetta puntatori come parametri. Questo permette di modificare le variabili originali definite nel chiamante (emulazione del passaggio per riferimento).

```c
void swap_pointer(int *x, int *y) {
    int temp;
    temp = *x;
    *x = *y;
    *y = temp;
}
// Chiamata nel main:
// swap_pointer(&x, &y);
```

### Variante 3: Procedura `swap` con Puntatori a Puntatori
Questa variante utilizza puntatori a puntatori (`int **`) e scambia gli indirizzi contenuti nei puntatori originali, non i valori delle variabili a cui puntano.

```c
void swap_ref(int **x, int **y) {
    int *temp;
    temp = *x; // temp (puntatore) salva l'indirizzo contenuto nel primo puntatore
    *x = *y;
    *y = temp;
}
// Chiamata nel main:
// swap_ref(&px, &py);
```
In questo caso, non vengono scambiati i valori `10` e `5` nelle loro locazioni di memoria originali. Vengono invece scambiati gli indirizzi contenuti in `px` e `py`. Di conseguenza, dopo la chiamata, `px` punterà alla variabile `y` e `py` punterà alla variabile `x`.