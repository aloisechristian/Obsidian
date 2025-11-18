## Introduzione ai Puntatori in C

Un puntatore è una variabile speciale il cui valore non è un dato diretto (come un intero o un carattere), ma l'indirizzo di un'altra variabile in memoria. Essi costituiscono uno strumento fondamentale nel linguaggio C per la gestione diretta della memoria, l'implementazione di strutture dati complesse e l'ottimizzazione delle performance.

I puntatori vengono utilizzati per una molteplicità di scopi:
* Riferimento a liste di variabili dinamiche.
* Riferimento a funzioni.
* Manipolazione di array e stringhe.
* Passaggio di parametri per riferimento (alternativa allo scambio per valore).
* Accesso a locazioni specifiche di memoria (es. registri di I/O hardware).

### Dimensione e Architettura
La dimensione di una variabile puntatore non è fissa, ma è strettamente collegata all'architettura del processore e del suo bus indirizzi.
* In un'architettura a **32 bit**, un indirizzo (e quindi un puntatore) occupa generalmente 32 bit (4 byte).
* In un'architettura a **64 bit**, un indirizzo occupa 64 bit (8 byte).
> [!INFO] Collegamento Consigliato
> Vedi [[07 - Architettura del Calcolatore, Bus, Clock e Memoria]] per dettagli sul bus indirizzi.

### Tipizzazione e Casting
Un puntatore in C è **strettamente tipizzato**. Ciò significa che a un puntatore di tipo `int*` possono essere assegnati solo indirizzi di variabili `int`.
Per assegnare l'indirizzo di un tipo diverso, è obbligatorio utilizzare l'operatore di **cast** esplicito:

```c
float reale = 3.14;
float *p_reale = &reale;
int *p_intero;

// p_intero = p_reale; // Errore o Warning del compilatore
p_intero = (int *) p_reale; // Lecito con cast esplicito [cite: 465]
````

> [!NOTE] Vedi [[11 - Operatori, Costanti e Conversioni di Tipo in C]] per approfondire il casting.

### Operatori di Riferimento e Dereferenziazione

Per lavorare con i puntatori, si utilizzano due operatori fondamentali :

1. **Operatore di Riferimento (`&`):** Noto anche come "address-of", restituisce l'indirizzo di memoria (locazione) in cui una variabile è memorizzata.
    
2. **Operatore di Dereferenziazione (`*`):** Noto anche come "indirection operator", agisce su una variabile puntatore e permette di accedere o modificare il valore contenuto nella locazione puntata.
    

## Utilizzo Pratico dei Puntatori

### Dichiarazione e Assegnazione

La dichiarazione avviene specificando il tipo puntato seguito dall'asterisco:

```c
int *punt; // Dichiarazione di puntatore a int [cite: 459]
```

Successivamente, è possibile assegnare a questo puntatore l'indirizzo di una variabile:
```c
int x = 4;
int *punt;
punt = &x; // Ora 'punt' contiene l'indirizzo di 'x' [cite: 478]
```

### Aliasing dei Puntatori

È possibile assegnare il valore di un puntatore a un altro puntatore dello stesso tipo.
```c
int *px = &x;
int *py;
py = px; // py e px contengono lo stesso indirizzo
```

In questo caso, `px` e `py` diventano **alias**: puntano alla stessa locazione di memoria. Modificare `*py` comporterà una modifica visibile anche dereferenziando `*px` (e ovviamente in `x`) .

### Accesso e Modifica dei Dati

Se `punt` punta a `x`:

- **Lettura:** `*punt` restituisce il valore di `x`.
    
- **Scrittura:** `*punt = 15;` modifica il valore di `x` a 15. Esistono quindi due modi equivalenti per accedere a `x`: direttamente (`x`) o tramite puntatore (`*punt`).
    

### Puntatori a Puntatori (Doppia Indirezione)

È possibile definire puntatori che puntano ad altri puntatori.
```c
int x = 100;
int *px = &x;
int **py = &px; // py punta all'indirizzo di px [cite: 530]
```

Dereferenziando:

- `*py` restituisce il contenuto di `px` (l'indirizzo di `x`).
    
- `**py` restituisce il contenuto di `x` (il valore 100).
    

### Relazione Inversa tra `*` e `&`

Gli operatori `*` e `&` sono inversi tra loro. L'espressione `*&x` è logicamente equivalente a `x`.

### Puntatori Nulli

Per indicare che un puntatore non punta a nulla, si assegna il valore `0` o la costante `NULL` (definita in `<stddef.h>`) .

## Aritmetica dei Puntatori

Sui puntatori è possibile eseguire operazioni aritmetiche (somma, differenza, incremento) gestite dal compilatore in base alla dimensione del tipo puntato (`sizeof(T)`).

Se `p` è un puntatore di tipo `T*`:

- `p + 1`: Punta alla locazione di memoria immediatamente successiva, spostandosi di `sizeof(T)` byte.
    
- `p + i`: Punta all'elemento `i` posizioni dopo `p`.
    

Questa tecnica è essenziale per scorrere gli array in modo efficiente.

#### Ordine di Precedenza ed Esempi

- `*(p++)`: Restituisce il valore puntato e _poi_ incrementa il puntatore all'elemento successivo.
    
- `(*p)++`: Incrementa il _valore_ dell'oggetto puntato (non l'indirizzo).
    

## Puntatori e Tipi di Dati Strutturati

### Puntatori e Array Monodimensionali

In C, il nome di un array è un puntatore costante al suo primo elemento. Se `v` è un array:

- `v` equivale a `&v[0]`.
    
- `v[i]` equivale a `*(v + i)`.
    

> [!INFO] Vedi [[16 - Dichiarazione, Manipolazione e Funzioni degli Array]] per dettagli sugli array.

### Puntatori e Array Multidimensionali (Matrici)

Anche gli array multidimensionali sono allocati in locazioni contigue. L'accesso `mat[i][j]` è syntactic sugar per: $$ \text{mat}[i][j] \equiv _(_( \text{mat} + i) + j) $$ Dove `mat` punta all'inizio della matrice, `mat + i` seleziona la riga `i`, e `+ j` sposta l'offset sulla colonna .

### Stringhe come Array di Caratteri

Le stringhe sono array di `char` terminati dal carattere `\0` (ASCII NULL) .

#### Inizializzazione

```c
char s[] = "ciao"; // Dimensione automatica: 5 byte ('c','i','a','o','\0')
```

#### La Libreria `string.h`

Include funzioni per la manipolazione che restituiscono spesso un puntatore alla stringa di destinazione, permettendo l'uso concatenato (nested calls).

Principali funzioni:

- `strlen(s)`: Restituisce la lunghezza (tipo `size_t`, escluso `\0`).
    
- `strcpy(dest, src)`: Copia `src` in `dest`. Ritorna `dest`.
    
- `strcat(dest, src)`: Accoda `src` a `dest`. Ritorna `dest`.
    
- `strcmp(s1, s2)`: Compara due stringhe.
    

Esempio di concatenazione funzionale:
```c
// Concatena s3 a s2, e il risultato a s1
strcat(s1, strcat(s2, s3));
```

## Puntatori come Parametri di Funzione

Passare un puntatore a una funzione permette di simulare il **passaggio per riferimento**, consentendo alla funzione di modificare le variabili del chiamante.

> [!INFO] Vedi [[15 - Funzioni, Passaggio Parametri e Librerie]] per il passaggio dei parametri.

### La Parola Chiave `const`

Si usa `const` per proteggere i dati puntati da modifiche indesiderate quando il puntatore è usato solo per input (es. `const char *str` in `strlen`).