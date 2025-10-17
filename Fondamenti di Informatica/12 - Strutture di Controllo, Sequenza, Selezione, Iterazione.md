# Guida Approfondita al Controllo del Flusso di Esecuzione in C

## Introduzione: Dall'Astrazione alla Pratica

### Il Paradigma Imperativo e il Modello di Von Neumann

Nella programmazione, il **controllo del flusso di esecuzione** è il meccanismo che determina l'ordine in cui le istruzioni di un programma vengono eseguite. Il testo si concentra sul **paradigma imperativo**, il modello dominante in linguaggi come il C. Un programma imperativo è essenzialmente una ricetta: una sequenza di comandi che modificano lo stato del programma (i dati in memoria) per raggiungere un obiettivo.

Questa sequenza di istruzioni viene processata da un esecutore, che nel nostro modello di riferimento è la **macchina di von Neumann**. Questo modello architetturale, alla base della maggior parte dei computer moderni, prevede un'unità di elaborazione centrale (CPU) che legge ed esegue istruzioni da una memoria in modo sequenziale.

Un programma, quindi, nasce dalla simbiosi di due componenti:

1. **Dati**: Le informazioni grezze (numeri, caratteri, etc.) su cui il programma opera.
    
2. **Flusso di Controllo**: L'ordine logico con cui le istruzioni manipolano tali dati per produrre un risultato.

### I Limiti della Sequenza e la Soluzione di Böhm-Jacopini

La semplice esecuzione di istruzioni una dopo l'altra è intuitiva ma estremamente limitata. Non potremmo, ad esempio, far compiere al programma scelte diverse in base all'input dell'utente o ripetere un'operazione un certo numero di volte. Per superare questi limiti, abbiamo bisogno di strutture di controllo più sofisticate.

Qui entra in gioco il **teorema di Böhm-Jacopini**, una pietra miliare dell'informatica teorica. Il teorema afferma che **qualsiasi algoritmo, per quanto complesso, può essere implementato utilizzando esclusivamente tre strutture di controllo fondamentali**. Questa è una garanzia di completezza: padroneggiando queste tre strutture, si ha il potere di scrivere qualsiasi programma.

Le tre strutture fondamentali sono:

1. **Sequenza**: L'esecuzione lineare di istruzioni.
    
2. **Selezione**: La scelta tra due o più percorsi alternativi.
    
3. **Iterazione**: La ripetizione di un blocco di istruzioni.

Analizziamo ora in dettaglio ciascuna di queste strutture, collegandole a esempi pratici in linguaggio C.

## 1. Strutture di Sequenza: Il Flusso di Default

La sequenza è la struttura più elementare. Le istruzioni vengono eseguite nell'ordine in cui sono scritte, dall'alto verso il basso. In C, il costrutto principale per raggruppare una sequenza di istruzioni è il **blocco di codice**, delimitato da parentesi graffe (`{ ... }`).

Un blocco definisce un ambito (scope) e trasforma più istruzioni in una singola unità logica. Il corpo di ogni funzione, come `main`, è un esempio perfetto di blocco.

```c
#include <stdio.h>

int main() { // Inizio del blocco principale
    // Inizio di una sequenza di istruzioni
    int x;
    int y;
    int sum;

    printf("Inserisci il primo numero: ");
    scanf("%d", &x); // Nota: &x passa l'indirizzo di memoria di x

    printf("Inserisci il secondo numero: ");
    scanf("%d", &y);

    sum = x + y;

    printf("La somma è: %d\n", sum);
    // Fine della sequenza
    
    return 0;
} // Fine del blocco principale
```

In questo esempio, la dichiarazione delle variabili, le chiamate a `printf` e `scanf`, e l'operazione di somma vengono eseguite in modo rigorosamente sequenziale.

## 2. Strutture di Selezione: Prendere Decisioni

Le strutture di selezione permettono al programma di deviare dal flusso sequenziale, scegliendo quale codice eseguire in base al risultato di una **condizione logica** (un'espressione che può essere solo `vera` o `falsa`).

### Il Costrutto `if`: La Scelta a una Via

L'`if` è la forma più semplice di selezione. Esegue un blocco di codice _solo se_ la sua condizione è vera.

**Sintassi:**

```c
if (condizione) {
    // Corpo dell'if: eseguito solo se la condizione è vera
}
```

![[Screenshot 2025-10-17 alle 19.18.20.png]]

**Esempio pratico (`selezione_if.c`):** Questo programma legge un numero e stampa un messaggio solo se è maggiore di 10.

```c
#include <stdio.h>

int main() {
    int numero;

    printf("Inserisci un numero intero: \n");
    scanf("%d", &numero);

    // Valuta la condizione: 'numero' è maggiore di 10?
    if (numero > 10) {
        // Questo blocco viene eseguito solo se la condizione è VERA
        printf("Il numero inserito è maggiore di 10 \n");
    }

    // L'esecuzione prosegue sempre da qui
    return 0;
}
```

### Il Costrutto `if-else`: La Scelta a Due Vie

L'`if-else` offre un'alternativa: esegue un blocco se la condizione è vera, e un altro se è falsa. I due blocchi sono **mutuamente esclusivi**.

**Sintassi:**

```c
if (condizione) {
    // Blocco THEN: eseguito se la condizione è VERA
} else {
    // Blocco ELSE: eseguito se la condizione è FALSA
}
```

![[Screenshot 2025-10-17 alle 19.18.58.png]]

**Esempio pratico (`selezione_if_else.c`):**

```c
#include <stdio.h>
#define N 50 // Uso di una costante per una migliore manutenibilità

int main() {
    int numero;

    printf("Inserisci un numero intero: \n");
    scanf("%d", &numero);

    if (numero > N) {
        printf("Il numero inserito è maggiore di %d \n", N);
    } else {
        printf("Il numero inserito è minore o uguale di %d \n", N);
    }

    return 0;
}
```

### Il Costrutto `else if`: Le Scelte a Catena

Per gestire più di due alternative, si può usare la catena `else if`. Le condizioni vengono valutate in ordine; non appena una risulta vera, il blocco corrispondente viene eseguito e l'intera catena viene saltata.

**Esempio pratico (basato su `selezione_if_elseif.c` corretto):** Questo programma determina se un numero è positivo, negativo o nullo.

```c
#include <stdio.h>

int main() {
    int n;
    printf("Inserisci numero intero: \n");
    scanf("%d", &n); // Corretto: '&n' per passare l'indirizzo

    if (n > 0) {
        printf("Inserito numero positivo.\n");
    } else if (n < 0) {
        printf("Inserito numero negativo.\n");
    } else {
        printf("Inserito zero.\n");
    }
    return 0;
}
```

### Il Costrutto `switch-case`: Selezione Multipla su un Valore

Lo `switch` è ideale quando si deve scegliere tra molti casi basati sul valore di una singola variabile (di tipo intero o carattere). È spesso più leggibile di una lunga catena di `if-else if`.

**Caratteristiche chiave:**

- **`case`**: Etichette che rappresentano i possibili valori.
    
- **`break`**: Istruzione fondamentale per uscire dallo `switch` dopo aver eseguito un `case`. Se omesso, si verifica il "fall-through", e l'esecuzione prosegue nel `case` successivo.
    
- **`default`**: Eseguito se nessuno dei `case` corrisponde al valore del selettore.
    

**Esempio pratico (`selezione_switch.c`):** Converte un numero da 1 a 12 nel mese corrispondente.

```c
#include <stdio.h>

int main() {
    int numero;
    printf("Inserisci un numero intero tra 1 e 12: \n");
    scanf("%d", &numero);

    switch(numero) {
        case 1: printf("Il mese scelto è Gennaio"); break;
        case 2: printf("Il mese scelto è Febbraio"); break;
        // ... altri mesi ...
        case 12: printf("Il mese scelto è Dicembre"); break;
        default: printf("L'intero inserito non corrisponde a nessun mese dell'anno");
    }
    return 0;
}
```

## 3. Strutture di Iterazione: Ripetere le Istruzioni

Le strutture iterative, o cicli, eseguono un blocco di codice ripetutamente finché una condizione di controllo rimane vera.

### Il Ciclo `while`: Controllo in Testa (Pre-condizionale)

Il `while` valuta la condizione _prima_ di ogni iterazione. Se la condizione è falsa fin dall'inizio, il corpo del ciclo non viene mai eseguito.

**Sintassi:**

```c
while (condizione) {
    // Corpo del ciclo
    // Qui dentro, qualcosa deve modificare la condizione per evitare un loop infinito!
}
```

![[Screenshot 2025-10-17 alle 19.20.59.png]]

**Esempio pratico (`iterazione_while.c`):** Stampa la tabellina di un numero.

```c
#include <stdio.h>

int main() {
    int numero, moltiplicatore = 1; // Inizializzazione
    printf("Inserisci un numero intero: \n");
    scanf("%d", &numero);

    while(moltiplicatore <= 10) { // Condizione di permanenza
        printf("%d x %d = %d \n", numero, moltiplicatore, numero * moltiplicatore);
        moltiplicatore++; // Aggiornamento ( cruciale per la terminazione)
    }

    return 0;
}
```

### Il Ciclo `do-while`: Controllo in Coda (Post-condizionale)

Il `do-while` valuta la condizione _dopo_ ogni iterazione. Questo garantisce che il corpo del ciclo venga eseguito **almeno una volta**. È perfetto per la validazione dell'input.

**Sintassi:**

```c
do {
    // Corpo del ciclo
} while (condizione);
```

![[Screenshot 2025-10-17 alle 19.21.33.png]]

**Esempio pratico (`iterazione_do_while.c`):** Forza l'utente a inserire un numero nell'intervallo [1, 12].

```c
#include <stdio.h>

int main() {
    int numero;

    do {
        printf("Inserisci un numero intero tra 1 e 12: \n");
        scanf("%d", &numero);
    // Il ciclo continua se il numero è FUORI dall'intervallo [1, 12]
    } while(numero < 1 || numero > 12);

    printf("Numero inserito valido: %d\n", numero);
    return 0;
}
```

### Il Ciclo `for`: Iterazione a Conteggio

Il ciclo `for` è una specializzazione del `while`, ideale per le situazioni in cui il numero di iterazioni è noto a priori. Raggruppa in una sola riga l'inizializzazione, la condizione e l'aggiornamento della variabile contatore, rendendo il codice più compatto e leggibile.

**Sintassi:**

```c
for (inizializzazione; condizione; aggiornamento) {
    // Corpo del ciclo
}
```

Questo è logicamente equivalente a:

```c
inizializzazione;
while (condizione) {
    // Corpo del ciclo
    aggiornamento;
}
```

**Esempio pratico (`iterazione_for.c`):** Riscrive l'esempio della tabellina in modo più conciso.

```c
#include <stdio.h>

int main() {
    int numero;
    printf("Inserisci un numero intero: \n");
    scanf("%d", &numero);

    // i è il contatore, inizializzato a 1.
    // Il ciclo continua finché i <= 10.
    // Dopo ogni iterazione, i viene incrementato.
    for(int i = 1; i <= 10; i++) {
        int prodotto = numero * i;
        printf("%d x %d = %d \n", numero, i, prodotto);
    }

    return 0;
}
```

## Conclusione: La Combinazione delle Strutture

La vera potenza della programmazione emerge quando queste tre strutture vengono combinate. Un programma reale è un intreccio di sequenze, selezioni e iterazioni. Ad esempio, all'interno di un ciclo `for` (iterazione) potremmo avere un costrutto `if-else` (selezione) che esegue una sequenza di operazioni diverse a seconda del valore del contatore.

Padroneggiare la logica e la sintassi di sequenza, selezione e iterazione è il passo fondamentale per trasformare un problema in un algoritmo funzionante e per scrivere codice chiaro, efficiente e corretto in C e in qualsiasi altro linguaggio imperativo.