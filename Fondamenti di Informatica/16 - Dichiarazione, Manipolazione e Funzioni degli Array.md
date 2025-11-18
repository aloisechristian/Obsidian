## Tipi di Dati Strutturati: Introduzione agli Array

### Dati Omogenei e Eterogenei
Il linguaggio C, oltre ai tipi di dato elementari (numerici, caratteri, booleani), offre meccanismi per definire tipi di dato strutturati. Questi si classificano in due categorie principali:
- **Tipi di dato strutturati omogenei**: Contengono elementi tutti dello stesso tipo. L'esempio primario è l'**array** (o vettore).
- **Tipi di dato strutturati eterogenei**: Possono contenere elementi di tipi diversi. Un esempio sono le **strutture** (`struct`).

Questa lezione si concentra sulla prima categoria, analizzando in dettaglio gli array.

### Definizione di Array
Un **array** (o vettore) è una collezione finita e ordinata di elementi dello stesso tipo. Il numero totale di elementi che un array può contenere è definito **dimensione** o **cardinalità**.

## Dichiarazione e Inizializzazione di Array in C

### Sintassi della Dichiarazione
La sintassi per dichiarare un array in C è la seguente:
```c
tipo nome_array[dimensione];
```
- `tipo`: Specifica il tipo di dato di tutti gli elementi dell'array (es. `int`, `float`, `char`).
- `nome_array`: È l'identificatore dell'array, soggetto alle stesse regole dei nomi di variabile.
- `dimensione`: È un valore costante intero che definisce il numero di elementi dell'array. La dimensione deve essere nota al momento della compilazione, in quanto il compilatore deve sapere quanto spazio di memoria allocare.

### Allocazione in Memoria
Quando un array viene dichiarato, il compilatore riserva un blocco di **locazioni di memoria contigue** (consecutive). La dimensione totale dello spazio allocato è data dal prodotto della dimensione dell'array per la dimensione in byte del tipo di dato degli elementi.
$$ 
\text{Spazio Totale} = \text{dimensione} \times \text{sizeof(tipo)}
$$
Ad esempio, per un array `int A[10];`, se un `int` occupa 4 byte, verranno allocati $10 \times 4 = 40$ byte consecutivi.

### Inizializzazione degli Elementi
La sola dichiarazione di un array non inizializza il valore dei suoi elementi; le locazioni di memoria conterranno valori indefiniti ("spazzatura"). È possibile inizializzare un array contestualmente alla sua dichiarazione utilizzando la seguente sintassi:
```c
tipo nome_array[dimensione] = {valore_0, valore_1, ..., valore_N-1};
```
Gli elementi vengono elencati tra parentesi graffe `{}` e separati da virgole.
Esempi:
```c
float numeri[3] = {1.5, -3.0, 4.2};
char lettere[5] = {'a', 'b', 'c', 'd', 'e'};
```

## Accesso agli Elementi di un Array

### La Notazione con Indice
Per accedere a un singolo elemento di un array, si utilizza l'operatore di indicizzazione `[]`:
```c
nome_array[indice]
```
- **Indice (o pedice)**: È un'espressione di tipo intero che specifica la posizione dell'elemento a cui si vuole accedere.
- **Numerazione da zero**: In C, come nella maggior parte dei linguaggi di programmazione, gli indici di un array partono da 0. Pertanto, per un array di dimensione $N$, gli indici validi vanno da $0$ a $N-1$. Il primo elemento è `nome_array[0]`, il secondo `nome_array[1]`, e l'ultimo `nome_array[N-1]`.

L'accesso può avvenire sia in lettura (per ottenere il valore di un elemento) sia in scrittura (per modificarlo):
```c
// Lettura
int valore = mio_array[2];

// Scrittura
mio_array[3] = 100;
```
L'indice può essere una costante, una variabile o un'espressione intera più complessa (es. `vettore[i]`, `vettore[c+3]`).

### Indirizzo di Memoria e Identificatore dell'Array
Un concetto fondamentale in C è che l'identificatore di un array (es. `x`) rappresenta l'**indirizzo di memoria del suo primo elemento** (`&x[0]`). Questo permette al sistema di accedere a qualsiasi altro elemento tramite un'operazione di spiazzamento (offset) calcolata a partire dall'indirizzo base.
$$ 
\text{indirizzo}(x[i]) = \text{indirizzo}(x[0]) + i \times \text{sizeof(tipo)}
$$

### Gestione degli Indici
È responsabilità del programmatore assicurarsi che l'indice utilizzato per accedere a un elemento rientri nell'intervallo valido `[0, N-1]`. L'accesso a un indice non valido (es. `array[N]`) costituisce un errore di **buffer overflow** (o accesso fuori dai limiti), che può portare a comportamenti imprevedibili e crash del programma, poiché si legge o si scrive in aree di memoria non allocate per quell'array.

## Gestione degli Array: Dimensione vs. Riempimento

### Allocazione Statica e Dimensione Massima
Spesso, il numero esatto di elementi da memorizzare non è noto a tempo di compilazione, ma dipende dall'input dell'utente a runtime. In questi casi, si ricorre a una tecnica di **allocazione statica worst-case**. Si dichiara un array con una dimensione massima (`MAX_DIM`), sufficientemente grande da contenere il numero massimo di elementi previsto per il caso peggiore.

### La Variabile di Riempimento
Per gestire un array allocato staticamente ma riempito dinamicamente, si introduce una variabile ausiliaria, comunemente chiamata **riempimento** (o `count`, `size`), che tiene traccia del numero di elementi *effettivamente* presenti nell'array in un dato momento.
- **Dimensione**: La capacità fisica dell'array (es. 100).
- **Riempimento**: Il numero di locazioni correntemente utilizzate (es. 10).

### Operazioni di Inserimento e Cancellazione Logica
- **Inserimento in coda**: Per aggiungere un nuovo elemento, lo si inserisce nella prima posizione libera, che corrisponde all'indice `riempimento`. Successivamente, si incrementa la variabile `riempimento`.
    ```c
    v[riempimento] = nuovo_valore;
    riempimento++;
    ```
- **Cancellazione logica**: Per "cancellare" l'ultimo elemento, è sufficiente decrementare il valore di `riempimento`. La locazione di memoria non viene fisicamente svuotata, ma diventa sovrascrivibile da un inserimento successivo. La cancellazione di un elemento in una posizione intermedia è più complessa e richiede lo spostamento (shift) degli elementi successivi per compattare l'array.

## Array e Funzioni

### Passaggio di Array come Parametri
In C, i parametri sono passati alle funzioni **per valore**. Tuttavia, quando si passa un array, ciò che viene copiato nel parametro formale della funzione è l'indirizzo di memoria del primo elemento dell'array. Questo significa che la funzione opera direttamente sulla memoria dell'array originale, non su una sua copia. Qualsiasi modifica apportata all'array all'interno della funzione sarà permanente.

La firma di una funzione che accetta un array come parametro è la seguente:
```c
tipo_ritorno nome_funzione(tipo nome_parametro[], int dimensione);
```
- `tipo nome_parametro[]`: Le parentesi quadre vuote indicano che il parametro è un array.
- `int dimensione`: Poiché la funzione non conosce la dimensione dell'array che le viene passato, è prassi comune passare la dimensione (o il riempimento) come parametro aggiuntivo.

### Esempio Pratico: Funzione di Stampa
```c
// Funzione per stampare un vettore di interi
void stampa_vettore(int v[], int n) {
    for (int i = 0; i < n; i++) {
        printf("v[%d] = %d\\n", i, v[i]);
    }
}

// Chiamata nel main
int main() {
    int mio_array[5] = {10, 20, 30, 40, 50};
    stampa_vettore(mio_array, 5);
    return 0;
}
```

## Tipi di Dato Personalizzati con `typedef`
La direttiva `typedef` permette di creare un alias per un tipo di dato esistente, migliorando la leggibilità del codice. È possibile utilizzarla anche per definire un tipo "vettore".
```c
// Definisce un nuovo tipo 'VettoreInteri' come un array di 10 interi
typedef int VettoreInteri[10];

// Utilizzo del nuovo tipo
int main() {
    VettoreInteri v1; // Dichiara un array di 10 interi
    // ...
    return 0;
}
```

## Esercizio Pratico: Gestione di un Vettore con Menu
La lezione illustra la creazione di un programma interattivo per gestire un array di interi. Il programma utilizza il concetto di riempimento e implementa le seguenti funzionalità: stampa, inserimento, eliminazione e ricerca di un elemento.

### Struttura del Programma
Il programma è strutturato con un menu `switch-case` che invoca funzioni specifiche per ogni operazione. L'array è dichiarato con una dimensione massima e gestito tramite una variabile di riempimento.

### Implementazione della Funzione di Ricerca
La funzione di ricerca ha il compito di trovare la prima occorrenza di un elemento nell'array e restituirne l'indice. Se l'elemento non è presente, restituisce un valore convenzionale (es. -1).
L'algoritmo implementato utilizza un ciclo `while` che si interrompe in due casi:
1. L'elemento viene trovato.
2. Tutti gli elementi dell'array (fino al riempimento) sono stati controllati.

```c
#include <stdbool.h>

int ricerca(int v[], int n, int elemento) {
    int i = 0;
    int pos = -1;
    bool trovato = false;

    while (i < n && !trovato) {
        if (v[i] == elemento) {
            trovato = true;
            pos = i;
        }
        i++;
    }
    return pos;
}
```

### Implementazione della Funzione di Inserimento
La funzione di inserimento (in coda) aggiunge un elemento all'array nella prima posizione disponibile (indicata dal riempimento) e aggiorna il valore del riempimento. Per propagare la modifica al `main`, la funzione restituisce il nuovo valore del riempimento.

```c
int inserisci_elemento(int v[], int n, int elemento) {
    // Si assume che ci sia spazio (n < MAX_DIM)
    v[n] = elemento;
    n++;
    return n;
}
```

### Cenni sulla Funzione di Eliminazione
Per eliminare un elemento, è necessario prima trovarlo. L'algoritmo di eliminazione, pertanto, si avvale della funzione di ricerca. Se l'elemento viene trovato alla posizione `pos`, l'eliminazione effettiva richiede di "compattare" l'array, spostando tutti gli elementi successivi a `pos` di una posizione all'indietro. Infine, il riempimento viene decrementato. Se l'elemento non è presente, non viene eseguita alcuna operazione.