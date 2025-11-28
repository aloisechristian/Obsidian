# Algoritmi di Ricerca e Ordinamento su Array in C

Questa nota analizza i principali algoritmi per la manipolazione di [[Fondamenti di Informatica/16 - Dichiarazione, Manipolazione e Funzioni degli Array|vettori (array)]], concentrandosi sulle due operazioni più frequenti: la ricerca di un elemento e l'ordinamento della collezione.

## 1. Algoritmi di Ricerca su Array

La ricerca è l'operazione che permette di individuare la presenza e la posizione di un elemento (detto _chiave_) all'interno di un insieme di dati. La scelta dell'algoritmo dipende dalla struttura dei dati (ordinati o meno) e ha un impatto diretto sulla [[Fondamenti di Informatica/08 - Introduzione ad Algoritmi, Complessità e Linguaggi di Programmazione#5. Complessità Computazionale|complessità computazionale]].

### 1.1 Ricerca Sequenziale (Lineare)

La ricerca sequenziale è il metodo più intuitivo e l'unico applicabile quando il vettore **non è ordinato**. L'algoritmo itera su ogni elemento dell'array confrontandolo con il valore cercato.

**Funzionamento:** Si scorre l'array dall'indice $0$ all'indice $N-1$. Se si trova l'elemento, si restituisce la sua posizione (indice); altrimenti, se si raggiunge la fine del vettore, l'elemento non è presente (si restituisce solitamente `-1`).

**Analisi della Complessità:**

- **Caso Migliore:** L'elemento è in prima posizione ($v[0]$). Complessità temporale: $O(1)$.
    
- **Caso Peggiore:** L'elemento è in ultima posizione o non è presente. L'algoritmo esegue $n$ confronti. Complessità temporale: $O(n)$.
    
- **Caso Medio:** Assumendo una distribuzione uniforme, si effettuano mediamente $\frac{n+1}{2}$ confronti. La complessità asintotica rimane lineare: $O(n)$.
    

### 1.2 Ricerca Binaria (Dicotomica)

Se il vettore è **già ordinato**, è possibile utilizzare la ricerca binaria, un algoritmo molto più efficiente che adotta una strategia _divide et impera_.

**Principio di Funzionamento:** Ad ogni passo, si confronta l'elemento cercato con l'elemento centrale dell'intervallo di ricerca. Grazie all'ordinamento, è possibile scartare immediatamente metà dell'array.

1. Si definiscono due indici, `primo` ($0$) e `ultimo` ($N-1$), che delimitano l'area di ricerca.
    
2. Si calcola l'indice centrale: $medio = \lfloor \frac{primo + ultimo}{2} \rfloor$ (divisione intera).
    
3. Si confronta l'elemento cercato $x$ con $v[medio]$:
    
    - Se $v[medio] == x$: Elemento trovato, restituisco `medio`.
        
    - Se $x < v[medio]$: L'elemento, se esiste, deve trovarsi nella metà sinistra (valori minori). Si restringe il campo ponendo `ultimo` = medio - `1`.
        
    - Se $x > v[medio]$: L'elemento deve trovarsi nella metà destra (valori maggiori). Si restringe il campo ponendo `primo = medio + 1`.
        
4. Si ripete finché l'elemento non viene trovato o finché `primo` $\le$ `ultimo`.
    

**Implementazione in C:**

```c
int ricerca_binaria(int v[], int riemp, int x) {
    int primo = 0, ultimo = riemp - 1;
    int medio, pos = -1;

    do {
        medio = (primo + ultimo) / 2;
        if (v[medio] == x) {
            pos = medio; // Trovato
        } else if (v[medio] < x) {
            primo = medio + 1; // Cerca a destra
        } else {
            ultimo = medio - 1; // Cerca a sinistra
        }
    } while (primo <= ultimo && pos == -1);

    return pos;
}
```

**Analisi della Complessità:**

- **Caso Migliore:** L'elemento si trova esattamente al centro al primo passo. Complessità: $O(1)$.
    
- **Caso Peggiore/Medio:** Ad ogni iterazione la dimensione del problema $n$ si dimezza ($n, n/2, n/4, \dots$). Nel caso peggiore (elemento assente o nell'ultima suddivisione possibile), sono necessari circa $\log_2 n$ confronti. Complessità logaritmica: $O(\log_2 n)$.
    

> [!NOTE] Confronto delle prestazioni Per $n = 1.000.000$ (un milione di elementi):
> 
> - **Ricerca Sequenziale:** fino a $1.000.000$ di confronti.
>     
> - **Ricerca Binaria:** circa $\log_2(10^6) \approx 20$ confronti.
>     

## 2. Algoritmi di Ordinamento (Sorting)

L'ordinamento è propedeutico per algoritmi efficienti come la ricerca binaria. Analizziamo algoritmi "in-place" (che non richiedono memoria ausiliaria significativa) di complessità quadratica.

### 2.1 Selection Sort

Il Selection Sort si basa sulla ricerca iterativa del minimo assoluto nel sottovettore non ancora ordinato e sul suo posizionamento nella corretta sequenza.

**Algoritmo:**

1. Si considera l'intero array. Si cerca il valore minimo nell'intervallo $[0, N-1]$ e lo si scambia con l'elemento in posizione $0$. Ora l'elemento in $v[0]$ è ordinato.
    
2. Si considera il sottovettore rimanente $[1, N-1]$. Si cerca il minimo e lo si scambia con $v[1]$.
    
3. Si generalizza: all'iterazione $i$, si cerca il minimo in $[i, N-1]$ e lo si scambia con $v[i]$.
    

**Implementazione Modulare:** L'algoritmo si appoggia tipicamente a due funzioni ausiliarie: `scambia` (per permutare due valori) e `minimo` (per trovare l'indice del valore minimo).

```c
void scambia(int *a, int *b) {
    int tmp = *a;
    *a = *b;
    *b = tmp;
}

int minimo(int v[], int inizio, int fine) {
    int min = v[inizio];
    int indice_min = inizio;
    for (int i = inizio + 1; i <= fine; i++) {
        if (v[i] < min) {
            min = v[i];
            indice_min = i;
        }
    }
    return indice_min;
}

void selection_sort(int v[], int dim) {
    for (int i = 0; i < dim - 1; i++) {
        int pos_min = minimo(v, i, dim - 1);
        scambia(&v[i], &v[pos_min]);
    }
}
```

**Complessità:** L'algoritmo esegue sempre due cicli annidati indipendentemente dall'ordine iniziale dei dati. La complessità è sempre quadratica: $O(n^2)$ in tutti i casi (Best, Average, Worst).

### 2.2 Insertion Sort

L'Insertion Sort simula il modo in cui si ordinano le carte da gioco in mano. Mantiene una parte sinistra dell'array ordinata e vi inserisce progressivamente i nuovi elementi presi dalla parte destra.

**Algoritmo:**

1. Si assume che il sottovettore $v[0]$ sia già ordinato.
    
2. Si prende l'elemento $v[i]$ (con $i$ che va da $1$ a $N-1$).
    
3. Si confronta $v[i]$ con gli elementi precedenti ($v[i-1], v[i-2]\dots$) scorrendo all'indietro.
    
4. Finché l'elemento precedente è maggiore di quello da inserire, si "shifta" l'elemento precedente a destra per fare spazio.
    
5. Si inserisce l'elemento nella posizione corretta.
    

**Implementazione:**

```c
void insertion_sort(int v[], int dim) {
    for (int i = 1; i < dim; i++) {
        int temp = v[i]; // Elemento da inserire
        int j = i;
        // Scorro all'indietro e shifto gli elementi maggiori di temp
        while (j > 0 && v[j - 1] > temp) {
            v[j] = v[j - 1];
            j--;
        }
        v[j] = temp; // Inserisco l'elemento
    }
}
```

**Complessità:**

- **Caso Migliore (Array già ordinato):** Il ciclo `while` interno non viene mai eseguito (la condizione è subito falsa). Complessità: $O(n)$.
    
- **Caso Peggiore (Array ordinato al contrario):** Si eseguono tutti gli spostamenti possibili. Complessità: $O(n^2)$.
    

### 2.3 Selection Sort Indiretto (Su Array di Indici)

Quando gli elementi da ordinare sono "pesanti" (es. grandi [[Fondamenti di Informatica/21 - Sintassi, Memoria e Applicazioni delle Strutture|struct]] come record di un database), lo spostamento fisico dei dati in memoria (l'operazione `scambia`) diventa molto costoso. La soluzione è l'**ordinamento indiretto**: non si spostano i dati, ma si riordinano i loro **indici**.

**Procedura:**

1. Si crea un array di indici $I$ tale che inizialmente $I[k] = k$.
    
2. Si applica il Selection Sort su $I$.
    
3. Il criterio di confronto non è su $I[j] < I[min]$, ma sui valori del vettore originale puntati dagli indici: $V[I[j]] < V[I[min]]$.
    
4. Si scambiano solo gli interi nell'array $I$. L'array $V$ rimane intatto.
    

Al termine, scorrendo $I$ in ordine, si può accedere agli elementi di $V$ in ordine crescente: $V[I[0]], V[I[1]], \dots$.

## 3. Implementazione e Generazione Casuale

Per testare questi algoritmi è utile generare vettori di dati pseudo-casuali utilizzando le librerie standard.

- **Librerie necessarie:** `#include <stdlib.h>` (per `rand`, `srand`) e `#include <time.h>` (per `time`).
    
- **Seeding:** Inizializzare il generatore con l'ora corrente per avere sequenze diverse ad ogni esecuzione:
    
    ```c
    srand(time(NULL));
    ```
    
- **Generazione:** Per ottenere un numero nell'intervallo $[0, MAX]$, si usa l'operatore [[Fondamenti di Informatica/11 - Operatori, Costanti e Conversioni di Tipo in C#Operatori Aritmetici|modulo]]:
    
    ```c
    int casuale = rand() % (MAX + 1);
    ```
    

Un'esercitazione tipica prevede:

1. Generazione di un array di dimensione $N$.
    
2. Stampa dell'array disordinato.
    
3. Chiamata a `selection_sort` o `insertion_sort`.
    
4. Stampa dell'array ordinato.
    
5. Input utente di un valore `k` e chiamata a `ricerca_