# Esercitazione e Gestione della Memoria Dinamica

## 1. Esercitazione Pratica: Array di Strutture

### Analisi del Problema

Questa sezione conclude l'analisi pratica sulla gestione di tipi di dati complessi, collegandosi direttamente a quanto visto in [[Fondamenti di Informatica/22 - Strutture, Array, Puntatori e Funzioni|Strutture, Array, Puntatori e Funzioni]]. L'esercizio richiede la gestione di un **array di strutture** con dimensione fisica allocata staticamente:

$$MAX\_STUDENTI = 100$$

La struttura `Studente` è definita dai seguenti campi (vedi [[Fondamenti di Informatica/21 - Sintassi, Memoria e Applicazioni delle Strutture|Sintassi delle Strutture]]):

- Due stringhe per nome e cognome (dimensione $51$ byte per includere il terminatore `\0`).
    
- Un intero (`int`) per l'età.
    
- Un booleano (`bool` da `<stdbool.h>`) per lo status di studente lavoratore.
    
- Un valore reale (`float`) per la media voti.
    

### Implementazione del Filtro

È stata implementata una funzione di ricerca e stampa condizionale. La funzione agisce come un **filtro** sull'array:

$$\text{void stampa\_minori(Studente *elenco, int riempimento, const int soglia\_eta)}$$

L'algoritmo itera sull'array fino al valore di `riempimento` (dimensione logica). La condizione di selezione è:

$$\text{if (elenco[i].eta} < \text{soglia\_eta)}$$

> [!warning] Nota sui Warning 
> Il compilatore può generare _warning_ se i tipi di dato nelle funzioni di I/O non corrispondono esattamente ai specificatori di formato. Un caso critico è l'uso di `scanf` su tipi `bool`: trattare un `bool*` come un `int*` può causare corruzione della memoria, poiché le dimensioni in byte potrebbero differire.

## 2. Organizzazione della Memoria di un Processo

Per comprendere l'allocazione dinamica, è necessario visualizzare lo spazio di indirizzamento virtuale assegnato dal sistema operativo a un processo in esecuzione. Questo si collega al modello architetturale visto in [[Fondamenti di Informatica/07 - Architettura del Calcolatore, Bus, Clock e Memoria|Architettura del Calcolatore]].

La memoria è segmentata in quattro aree logiche:

1. **Text (Codice):** Segmento di sola lettura che contiene le istruzioni macchina del programma compilato.
    
2. **Data (Dati Statici):** Contiene le [[Fondamenti di Informatica/14 - Programmazione Modulare, Funzioni, Procedure e Visibilità delle Variabili#Identificatori Globali|variabili globali]] e statiche, la cui dimensione è nota a tempo di compilazione.
    
3. **Stack (Pila):** Area LIFO (_Last In, First Out_) dedicata alla gestione delle chiamate di funzione.
    
    - Contiene i **Record di Attivazione** (variabili locali, parametri formali, indirizzi di ritorno).
        
    - La memoria viene allocata e deallocata **automaticamente** seguendo il flusso di esecuzione (scope delle variabili).
        
    - Cresce verso indirizzi di memoria _decrescenti_ (verso il basso).
        
4. **Heap (Mucchio):** Area dedicata all'**allocazione dinamica**.
    
    - La memoria deve essere gestita esplicitamente dal programmatore.
        
    - Cresce verso indirizzi di memoria _crescenti_ (verso l'alto).
        

### Stack Overflow

Poiché Stack e Heap crescono in direzioni opposte all'interno dello spazio libero, se le richieste di memoria sono eccessive (es. ricorsione infinita o allocazione di array enormi nello stack), le due aree possono collidere, causando un errore critico di **Stack Overflow**.

## 3. Allocazione Statica vs Dinamica

|Caratteristica|Allocazione Statica|Allocazione Dinamica|
|---|---|---|
|**Momento**|_Compile-time_ (Compilazione)|_Run-time_ (Esecuzione)|
|**Area di Memoria**|Stack (o Data)|Heap|
|**Visibilità**|Legata allo [[Fondamenti di Informatica/14 - Programmazione Modulare, Funzioni, Procedure e Visibilità delle Variabili#Visibilità (Scope) e Ciclo di Vita delle Variabili|scope]] del blocco|
|**Dimensioni**|Fisse e note a priori|Variabili e definibili dall'utente|
|**Efficienza**|Alta (gestione automatica CPU)|Minore (overhead di gestione)|

L'allocazione dinamica è essenziale quando la quantità di dati da elaborare non è nota a priori (es. lettura di un file di lunghezza arbitraria), superando i limiti degli array a dimensione fissa (VLA o macro `#define`).

## 4. Gestione della Memoria nello Heap (`stdlib.h`)

Il linguaggio C offre primitive per la manipolazione diretta dello Heap tramite la libreria `<stdlib.h>`. Queste funzioni operano tramite **puntatori** (vedi [[Fondamenti di Informatica/17 - Puntatori, Array, Stringhe e Gestione della Memoria|Teoria dei Puntatori]]).

### Funzioni di Allocazione

#### `malloc` (Memory Allocation)

Alloca un blocco contiguo di memoria grezza.

- **Sintassi:** `void* malloc(size_t size);`
    
- **Input:** Dimensione in byte ($size$).
    
- **Output:** Restituisce un puntatore generico (`void*`) al primo byte del blocco allocato. Se l'allocazione fallisce (memoria esaurita), restituisce `NULL`.
    
- **Nota:** Il contenuto della memoria è **indeterminato** (spazzatura).
    

Esempio per allocare un array di $N$ interi:

```c
int *p = (int*)malloc(N * sizeof(int));
if (p == NULL) { /* Gestione errore */ }
```

#### `calloc` (Contiguous Allocation)

Alloca memoria per un array di elementi e la inizializza a zero.

- **Sintassi:** `void* calloc(size_t num, size_t size);`
    
- **Input:** Numero di elementi ($num$) e dimensione di ciascun elemento ($size$).
    
- **Output:** Puntatore all'area allocata, con tutti i bit impostati a $0$.
    

#### `realloc` (Re-Allocation)

Ridimensiona un blocco di memoria precedentemente allocato, preservandone il contenuto (fino al minimo tra vecchia e nuova dimensione).

- **Sintassi:** `void* realloc(void *ptr, size_t new_size);`
    
- **Comportamento:** Può estendere il blocco in loco o, se non c'è spazio contiguo sufficiente, allocare una nuova area, copiare i dati e liberare la vecchia.
    

### Funzione di Deallocazione: `free`

Restituisce il controllo della memoria al sistema operativo.

- **Sintassi:** `void free(void* ptr);`
    
- **Regola:** Per ogni chiamata a `malloc`/`calloc`, deve esistere una corrispondente chiamata a `free` quando il dato non serve più.
    

## 5. Vulnerabilità e Gestione degli Errori

La potenza dell'allocazione dinamica comporta rischi significativi per la stabilità e la sicurezza del software.

### Memory Leak (Perdita di Memoria)

Si verifica quando si perde il riferimento (il puntatore) a un'area di memoria allocata nello Heap senza averla prima liberata con `free()`.

- **Conseguenza:** La memoria rimane occupata ma inaccessibile fino alla terminazione del processo. In programmi a lunga esecuzione (es. server), questo porta all'esaurimento della RAM.
    

### Dangling Pointers e Use After Free

Un puntatore si dice "dangling" (penzolante) se punta a un'area di memoria che è stata deallocata.

- **Use After Free:** È l'errore che si commette accedendo (in lettura o scrittura) a un puntatore dopo aver chiamato `free()` su di esso. Questo può causare corruzione dei dati o vulnerabilità di sicurezza (es. esecuzione di codice arbitrario se l'area viene riallocata per altri scopi).
    

### Double Free

Il tentativo di invocare `free()` due volte sullo stesso indirizzo di memoria.

- **Conseguenza:** Corruzione delle strutture interne che gestiscono lo Heap, portando quasi sempre al crash del programma.