## Introduzione e Annunci

La lezione riprende dopo un'interruzione dovuta alle prove intercorso, annunciando l'assegnazione di due nuove esercitazioni asincrone per recuperare il tempo perso. Entrambe le esercitazioni, incentrate su **funzioni, array e tipi di dato strutturati**, avranno come scadenza la settimana successiva.

Si procede poi con una breve revisione della seconda esercitazione asincrona, il cui svolgimento generale è stato positivo, salvo una piccola imprecisione che verrà discussa. L'obiettivo principale della lezione odierna è consolidare le conoscenze su array e puntatori attraverso esercizi pratici, per poi proseguire con nuovi argomenti.

## Revisione Esercitazione Asincrona 2: Calcoli Geometrici su un Rettangolo

La traccia richiedeva la scrittura di un programma in C per calcolare le proprietà geometriche di un rettangolo e la sua area dopo un'operazione di scalatura. L'esercizio mirava a rafforzare l'uso degli operatori elementari, della libreria matematica (`math.h`) e, in particolare, dell'istruzione `typedef` per la creazione di alias di tipo.

### Definizione di Tipi Personalizzati con `typedef`

Il programma richiedeva la definizione di due nuovi tipi:
- `misura`: un alias per `unsigned int`, destinato a rappresentare la base e l'altezza del rettangolo.
- `scalare`: un alias per `float`, per il fattore di scala.

L'utilizzo di `typedef` migliora la leggibilità e la manutenibilità del codice, associando un nome significativo a un tipo di dato fondamentale.

```c
typedef unsigned int misura;
typedef float scalare;
```

### Svolgimento e Imprecisione Comune

Dopo aver letto i dati di input (base, altezza e fattore di scala), il programma doveva calcolare perimetro, area, diagonale e area scalata. L'unica lieve imprecisione riscontrata in alcuni elaborati riguardava la dichiarazione delle variabili per perimetro e area. Essendo queste grandezze una combinazione lineare di base e altezza (entrambe di tipo `misura`), la soluzione più coerente sarebbe stata dichiarare anche `perimetro` e `area` come tipo `misura`, anziché `int`.

```c
// Dichiarazione delle variabili
misura base, altezza;
scalare fattore_scala;

// Calcoli (soluzione più coerente)
misura perimetro, area;
scalare diagonale, area_scalata;
```

## Esercizi su Vettori e Puntatori: Superare il Passaggio per Valore

La parte centrale della lezione si concentra su esercizi pratici per illustrare come i puntatori permettano di superare la limitazione del **passaggio di parametri per valore**, l'unico meccanismo nativo del linguaggio C. Attraverso i puntatori, una funzione può modificare variabili definite nel contesto del chiamante (e.g., nel `main`), simulando un passaggio per riferimento e permettendo di fatto di "restituire" più di un valore.

## Esercizio 1: Conteggio delle Occorrenze in un Vettore

**Specifica**: Scrivere una funzione che, dati un vettore di interi, la sua dimensione effettiva (riempimento) e un numero, restituisca il numero di volte in cui tale numero è presente nel vettore. L'esercizio viene affrontato in due modalità.

### Versione 1: Funzione con Valore di Ritorno

La prima implementazione utilizza il meccanismo di ritorno standard di una funzione.

- **Prototipo**: `int contaOccorrenze(vettore V, int riemp, int valore);`
- **Logica**: La funzione deve scorrere l'intero vettore per contare tutte le occorrenze, rendendo il ciclo `for` la scelta più adatta. Un ciclo `while`, usato per la ricerca della prima occorrenza, sarebbe inappropriato perché si fermerebbe prematuramente.

```c
int contaOccorrenze(vettore V, int riemp, int valore) {
    int count = 0; // Variabile contatore inizializzata a 0
    for (int i = 0; i < riemp; i++) {
        if (V[i] == valore) {
            count++;
        }
    }
    return count;
}
```

### Versione 2: Procedura con Parametro di Output

La seconda versione trasforma la funzione in una procedura (`void`) che comunica il risultato tramite un **parametro di output**.

- **Prototipo**: `void contaOccorrenze2(vettore V, int riemp, int valore, int *count);`
- **Logica**: Il quarto parametro, `int *count`, è un puntatore a un intero. La funzione non ritorna un valore, ma modifica direttamente la variabile il cui indirizzo viene passato durante la chiamata.

- **Chiamata nel `main`**: `contaOccorrenze2(my_vector, N, val, &my_count);` Si utilizza l'operatore `&` per passare l'indirizzo della variabile `my_count`.

- **Implementazione**: Per accedere e modificare il valore puntato, si usa l'operatore di dereferenziazione `*`.

```c
void contaOccorrenze2(vettore V, int riemp, int valore, int *count) {
    *count = 0; // Inizializza a 0 il valore della variabile esterna

    for (int i = 0; i < riemp; i++) {
        if (V[i] == valore) {
            (*count)++; // Incrementa il valore puntato
        }
    }
}
```
È cruciale l'uso delle parentesi `(*count)++` per garantire la corretta precedenza degli operatori: prima si dereferenzia il puntatore con `*count` e poi si incrementa il valore ottenuto. Senza parentesi, `*count++` incrementerebbe l'indirizzo di memoria del puntatore, portando a un comportamento errato.

## Esercizio 2: Inserimento di un Elemento in Coda al Vettore

**Specifica**: Scrivere una funzione che aggiunga un numero in coda a un vettore di interi. La funzione deve modificare il riempimento del vettore e restituire un valore booleano (`true` se l'inserimento ha successo, `false` altrimenti).

- **Prototipo**: `bool inserisciElemento(int V[], int *riemp, int elemento);`
- **Libreria Richiesta**: `#include <stdbool.h>` per il tipo `bool`.

### Parametri di Ingresso-Uscita
Il parametro `riemp` è un esempio di **parametro di ingresso-uscita**: 
1.  **Ingresso**: Il suo valore iniziale è necessario per determinare se c'è spazio nell'array e per calcolare l'indice della prima cella libera (`V[*riemp]`).
2.  **Uscita**: Il suo valore deve essere incrementato e la modifica deve essere visibile al chiamante. Per questo motivo, viene passato come puntatore.

### Implementazione e Gestione dell'Array Pieno
La funzione deve prima verificare se il vettore ha raggiunto la sua capacità massima (`N_MAX`).

```c
bool inserisciElemento(int V[], int N_MAX, int *riemp, int elemento) {
    // 1. Controlla se l'array è pieno
    if (*riemp < N_MAX) {
        // 2. Inserisci l'elemento nella prima posizione libera
        V[*riemp] = elemento;
        // 3. Incrementa il riempimento
        (*riemp)++;
        // 4. Ritorna successo
        return true;
    } else {
        // 5. Ritorna fallimento
        return false;
    }
}
```

## Esercizio 3: Ricerca di un Elemento e della sua Posizione

**Specifica**: Scrivere una funzione di ricerca che restituisca sia un'indicazione della presenza dell'elemento, sia la sua posizione se trovato. Anche questo problema viene risolto in due modi.

### Versione 1: Ricerca con Ritorno Booleano

Una prima versione semplice restituisce solo `true` o `false`.
- **Prototipo**: `bool ricerca(int V[], int riemp, int elemento);`
- **Logica**: Un ciclo `while` con una variabile booleana `trovato` permette di uscire non appena l'elemento viene individuato, ottimizzando la ricerca.

### Versione 2: Ritorno Booleano e Posizione tramite Puntatore

Per restituire anche la posizione, si aggiunge un parametro di output.
- **Prototipo**: `bool ricerca2(int V[], int riemp, int elemento, int *pos);`
- **Logica**: Il parametro `*pos` viene inizializzato a un valore sentinella (es. `-1`) per indicare che l'elemento non è stato ancora trovato. Se l'elemento viene trovato all'indice `i`, `*pos` viene aggiornato a `i`.

```c
bool ricerca2(int V[], int riemp, int elemento, int *pos) {
    bool trovato = false;
    int i = 0;
    *pos = -1; // Inizializzazione a valore sentinella

    while (i < riemp && !trovato) {
        if (V[i] == elemento) {
            trovato = true;
            *pos = i; // Salva la posizione
        } else {
            i++;
        }
    }
    return trovato;
}
```
Nel `main`, si invoca la funzione passando l'indirizzo di una variabile `posizione`: `if (ricerca2(v, N, val, &posizione)) { ... }`. Se la funzione ritorna `true`, la variabile `posizione` conterrà l'indice corretto.