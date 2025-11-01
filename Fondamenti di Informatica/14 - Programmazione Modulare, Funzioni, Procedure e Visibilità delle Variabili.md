## Introduzione ai Sottoprogrammi e alle Librerie

La presente lezione introduce i concetti di sottoprogramma e libreria, elementi fondamentali della programmazione strutturata. Verranno analizzati in dettaglio la definizione di sottoprogramma, le distinzioni tra funzioni e procedure, e il concetto di libreria, già incontrato attraverso l'uso di `stdio.h`, `math.h` e `stdlib.h` per la generazione di numeri pseudocasuali.

### Il Principio di Modularità

Alla base dei sottoprogrammi e delle librerie vi è il principio di **modularità**, che consiste nell'organizzare un sistema complesso, come un programma software, in componenti distinti e autonomi, detti moduli. Questo approccio facilita la progettazione, l'implementazione, la comprensione e l'utilizzo del sistema. A livello hardware, un esempio di modularità è l'uso di un [[Fondamenti di Informatica/07 - Architettura del Calcolatore, Bus, Clock e Memoria#1. Il Sistema di Bus|bus di sistema]] per permettere la comunicazione tra componenti diversi.

Applicare la modularità a un programma significa scomporlo in sottocomponenti, ciascuno responsabile di una funzione specifica. Ogni modulo deve possedere un nome, svolgere compiti ben definiti e operare in modo autonomo, senza dipendere da altri moduli. I benefici principali della modularità sono:

- **Riusabilità del codice**: Un modulo può essere utilizzato più volte all'interno dello stesso programma o in programmi diversi, evitando la scrittura di codice ridondante. Ad esempio, la funzione `printf` è un modulo riutilizzabile per la stampa su standard output.
    
- **Gestione della complessità**: Scomporre un problema complesso in sottoproblemi più semplici rende l'[[Fondamenti di Informatica/08 - Introduzione ad Algoritmi, Complessità e Linguaggi di Programmazione#1. Definizione di Algoritmo|algoritmo]] più facile da progettare e implementare.
    
- **Manutenibilità**: Modifiche o correzioni a una specifica funzionalità possono essere isolate all'interno del modulo corrispondente, senza impattare il resto del programma.
    

### Astrazione: Interfaccia e Corpo

Un modulo realizza il concetto di **astrazione**, separando ciò che il modulo _fa_ (l'interfaccia) da _come_ lo fa (il corpo o implementazione).

- **Interfaccia**: È la parte pubblica del modulo, che ne descrive le funzionalità e le modalità d'uso. L'utente di un modulo interagisce solo con la sua interfaccia, senza bisogno di conoscerne i dettagli implementativi. Ad esempio, per usare `printf`, è sufficiente conoscerne la firma e il comportamento, non l'algoritmo interno.
    
- **Corpo**: È l'implementazione effettiva del modulo, contenente il codice che realizza le funzionalità descritte dall'interfaccia. Il corpo è nascosto all'utente esterno, un principio noto come **information hiding**.
    

Esistono due tipi principali di astrazione:

1. **Astrazione sul Controllo**: Si astrae una funzionalità dalla sua implementazione. È il tipo di astrazione trattato in questo corso e si realizza tramite i sottoprogrammi.
    
2. **Astrazione sui Dati**: Si astrae la struttura dei dati e le operazioni consentite su di essi. È tipica dei linguaggi orientati agli oggetti (es. C++) e verrà accennata introducendo i tipi di dato astratto.
    

### Strategie di Progettazione: Top-Down e Bottom-Up

La modularità supporta due approcci complementari alla risoluzione dei problemi:

- **Analisi Top-Down**: Si parte dal problema principale e lo si scompone gerarchicamente in sottoproblemi più semplici. Questo processo di raffinamento continua fino a quando i sottoproblemi diventano abbastanza elementari da essere implementati direttamente. La struttura risultante può essere visualizzata come un albero, dove le foglie rappresentano i moduli software o le istruzioni elementari eseguibili.
    
- **Approccio Bottom-Up**: Si parte da componenti software esistenti e li si combina per costruire una soluzione al problema principale. Questo approccio si basa sulla disponibilità di moduli pre-esistenti e riutilizzabili.
    

## I Sottoprogrammi

Un sottoprogramma è un modulo funzionale definito all'interno di un programma, incaricato di risolvere uno specifico sottoproblema. Può essere attivato (o invocato) zero, una o più volte durante l'esecuzione del programma.

L'invocazione di un sottoprogramma implica un trasferimento del **flusso di controllo**: il programma principale (chiamante) cede temporaneamente il controllo al sottoprogramma (chiamato). Una volta che il sottoprogramma ha terminato la sua esecuzione, il controllo ritorna al chiamante, all'istruzione immediatamente successiva a quella di invocazione. A livello hardware, questo meccanismo è gestito dal `[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Il Ciclo del Processore|ciclo del processore (fetch-decode-execute)]]`, che modifica il registro Program Counter per saltare all'indirizzo di memoria della prima istruzione del sottoprogramma e, al termine, tornare all'istruzione successiva nel chiamante. Questo meccanismo è alla base della programmazione strutturata.

### Scambio di Informazioni: Procedure e Funzioni

Un sottoprogramma può scambiare informazioni con il programma chiamante tramite dati in ingresso (parametri) e dati in uscita (valori di ritorno).

- **Procedura (o Routine)**: Un sottoprogramma che può ricevere dati in ingresso ma non restituisce un valore in uscita. In C, le procedure sono implementate come funzioni con tipo di ritorno `void`.
    
- **Funzione**: Un sottoprogramma che riceve dati in ingresso e restituisce un singolo valore in uscita. Le funzioni sono una specializzazione delle procedure.
    

## Definizione e Invocazione di Sottoprogrammi in C

La definizione di un sottoprogramma in C si compone di due parti:

1. **Intestazione (o Firma o Prototipo)**: Specifica il tipo di valore restituito, il nome del sottoprogramma e l'elenco dei parametri formali (con i rispettivi tipi).
    
2. **Corpo**: Un blocco di codice, racchiuso tra parentesi graffe `{}`, che contiene le dichiarazioni e le istruzioni che implementano la funzionalità del sottoprogramma.
    

La sintassi generale per la **dichiarazione (prototipo)** è:

```c
tipo_ritorno nome_funzione(tipo1 param1, tipo2 param2, ...);
```

Il prototipo informa il compilatore dell'esistenza della funzione prima che essa venga definita o utilizzata.

Anche la funzione `main` rispetta questa struttura: `int main()` è una funzione di nome `main` che restituisce un valore intero.

### Parametri Formali e Parametri Effettivi

- **Parametri Formali**: Sono gli identificatori dichiarati nell'intestazione del sottoprogramma. Agiscono come segnaposto per i valori che verranno forniti durante l'invocazione.
    
- **Parametri Effettivi (o Argomenti)**: Sono i valori o le espressioni passate al sottoprogramma al momento della sua invocazione.
    

Quando un sottoprogramma viene invocato, si verifica un processo di **binding**: il valore di ciascun parametro effettivo viene associato al corrispondente parametro formale. È fondamentale che i parametri effettivi corrispondano a quelli formali per numero, tipo e ordine.

È importante notare che in C il passaggio dei parametri avviene **per valore**: al sottoprogramma viene passata una **copia** del valore del parametro effettivo, non la variabile stessa. Qualsiasi modifica apportata al parametro formale all'interno della funzione non ha effetto sulla variabile originale nel chiamante. Questo è lo stesso motivo per cui la funzione `[[Fondamenti di Informatica/10 - Struttura dei Programmi in C, Input e Output e Variabili#Input: La Funzione scanf|scanf]]` richiede l'indirizzo di una variabile (`&`) per poterla modificare.

### L'Istruzione `return`

L'istruzione `return` ha un duplice scopo:

1. Termina immediatamente l'esecuzione del sottoprogramma.
    
2. Restituisce il controllo al programma chiamante.
    

Nelle funzioni (con tipo di ritorno diverso da `void`), `return` è seguito da un'espressione (costante, variabile o calcolo) il cui valore viene restituito al chiamante. Il tipo di questo valore deve essere compatibile con il tipo di ritorno dichiarato nella firma della funzione. Nelle procedure (`void`), `return;` può essere usato per terminare anticipatamente la funzione, altrimenti la terminazione avviene alla chiusura del blocco `}`.

### Esempio Pratico: La Funzione `minimo`

Consideriamo un programma che calcola il minimo tra due numeri interi, basato sul file `funzione_minimo.c`.

**1. Dichiarazione (Prototipo)** La dichiarazione informa il compilatore dell'esistenza della funzione, della sua firma e del suo tipo di ritorno. Va posta prima del suo primo utilizzo (tipicamente dopo gli `#include`).

```c
#include <stdio.h>

// Prototipo della funzione
int minimo(int a, int b);
```

**2. Programma Principale (`main`) con Invocazione** Il `main` invoca la funzione `minimo` passando dei parametri effettivi (es. `1` e `10`). Il valore restituito dalla funzione può essere usato direttamente, ad esempio in una `printf`, o memorizzato in una variabile.

```c
int main() {
    int risultato = minimo(1, 10); // Invocazione con parametri effettivi costanti
    printf("Il minimo tra 1 e 10 è: %d\n", risultato);
    return 0;
}
```

**3. Definizione della Funzione** La definizione contiene l'implementazione logica. I parametri `a` e `b` sono formali.

```c
// Definizione della funzione
int minimo(int a, int b) {
    if (a < b) {
        return a;
    } else {
        return b;
    }
}
```

Durante l'invocazione `minimo(1, 10)`, al parametro formale `a` viene assegnato il valore `1`, e a `b` il valore `10`. La funzione esegue il confronto e restituisce `a`.

## Visibilità (Scope) e Ciclo di Vita delle Variabili

Lo **scope** (o visibilità) di un identificatore (variabile, funzione) è la porzione di codice in cui esso è accessibile. Il **ciclo di vita** è l'intervallo di tempo durante l'esecuzione in cui una variabile esiste in memoria.

### Identificatori Locali

Un identificatore dichiarato all'interno di un blocco (es. il corpo di una funzione) è **locale** a quel blocco.

- **Visibilità**: Limitata al blocco in cui è dichiarato, dalla dichiarazione fino alla parentesi graffa di chiusura. Non è visibile al chiamante né ad altri sottoprogrammi.
    
- **Ciclo di Vita**: La variabile viene creata in memoria (allocata) quando il flusso di esecuzione entra nel blocco e viene distrutta (deallocata) quando ne esce. Ad ogni invocazione della funzione, le sue variabili locali vengono create _ex novo_.
    

Anche i parametri formali sono considerati locali al sottoprogramma.

### Identificatori Globali

Un identificatore dichiarato al di fuori di qualsiasi blocco (tipicamente all'inizio del file sorgente, dopo gli `#include`) è **globale**.

- **Visibilità**: Si estende dal punto della dichiarazione fino alla fine del file sorgente (`.c`). È accessibile da tutti i sottoprogrammi (definiti in quel file) che seguono la sua dichiarazione.
    
- **Ciclo di Vita**: La variabile esiste per l'intera durata dell'esecuzione del programma.
    

L'uso di variabili globali dovrebbe essere limitato, poiché viola il principio di modularità e di _information hiding_, rendendo il codice più difficile da comprendere, manutenere e testare, dato che qualsiasi funzione può potenzialmente modificarne lo stato.

### Esempio di Visibilità (Locale vs. Globale)

```c
#include <stdio.h>

const float P = 3.14; // Costante globale

float area_cerchio(float raggio) { // 'raggio' è un parametro formale, locale
    float area; // 'area' è una variabile locale
    area = P * raggio * raggio; // 'P' è globale e visibile qui
    return area;
}

int main() {
    float r, A, C; // Variabili locali al main
    // 'area' e 'raggio' della funzione area_cerchio NON sono visibili qui
    // ... il codice che usa le variabili e invoca le funzioni ...
    return 0;
}
```

### Esempio di Variabile Globale (da `variabile_globale.c`)

```c
#include <stdio.h>

// Dichiarazione del prototipo
void stampa_var_globale();

// Definizione della variabile globale
int variabile_globale = 10;

int main() {
    // Il main "vede" la variabile globale e la usa
    stampa_var_globale();
    printf("Il valore della variabile globale nel main è: %d \n", variabile_globale);
    return 0;
}

void stampa_var_globale() {
    // Anche la funzione "vede" la stessa variabile globale
    printf("[STAMPA] Il valore della variabile globale è: %d \n", variabile_globale);
}
```

### Visibilità nei Blocchi di Controllo

La visibilità è legata al blocco più interno che contiene la dichiarazione. Ad esempio, una variabile dichiarata all'interno di un `[[Fondamenti di Informatica/12 - Strutture di Controllo, Sequenza, Selezione, Iterazione#Il Ciclo for: Iterazione a Conteggio|ciclo for]]` è locale solo a quel ciclo.

```c
for (int i = 0; i < 5; i++) {
    int y = i * i; // 'y' è locale a ogni iterazione del ciclo
    printf("%d\n", y);
}
// Qui 'y' non è più visibile e non esiste.
// 'i' non è più visibile (se dichiarata nel for)
```

In questo caso, la variabile `y` viene creata e distrutta ad ogni iterazione del ciclo.

### Mascheramento (Aliasing o Shadowing)

Se un blocco interno dichiara una variabile con lo stesso nome di una variabile dichiarata in un blocco esterno (ad esempio, una variabile globale), la variabile interna **maschera** (o "nasconde") quella esterna. All'interno del blocco, qualsiasi riferimento a quel nome si riferirà alla variabile locale.

```c
#include <stdio.h>

int i = 55; // Globale

int main() {
    int k = -8; // Locale al main

    for (int i = 0; i < 3; i++) { // 'i' locale al for, maschera la 'i' globale
        int k = 100; // 'k' locale al for, maschera la 'k' del main
        printf("Interno: i=%d, k=%d\n", i, k); // Stampa i=0,1,2 e k=100
    }

    printf("Esterno: i=%d, k=%d\n", i, k); // Stampa i=55 (globale) e k=-8 (del main)
    return 0;
}
```

## Le Librerie in C

Una **libreria** è una collezione di sottoprogrammi (funzioni e procedure) e definizioni di dati precompilati, organizzati per fornire un insieme specifico di funzionalità. L'uso delle librerie è un'applicazione fondamentale del principio di modularità e riusabilità.

Quando usiamo `#include <stdio.h>`, stiamo includendo il file di **intestazione (header file)** della libreria standard di Input/Output.

### File di Intestazione (`.h`) e File di Implementazione (`.c`)

Il C gestisce la modularità separando l'interfaccia dall'implementazione:

1. **File di Intestazione (`.h`)**: Contiene le **dichiarazioni** (i prototipi) delle funzioni, le definizioni dei tipi (`typedef`) e le costanti (`#define`) che la libreria "esporta", cioè rende disponibili all'esterno. Non contiene codice eseguibile.
    
2. **File di Implementazione (`.c`)**: Contiene il **corpo** (l'implementazione effettiva) delle funzioni dichiarate nel file `.h`.
    

### Processo di Compilazione e Linking

L'uso delle librerie è reso possibile dal `[[Fondamenti di Informatica/09 - Fondamenti di Programmazione in C, Compilazione ed Errori#Dal Codice Sorgente all'Esecuzione: Il Processo di Compilazione|processo di compilazione]]`:

1. **Preprocessing**: La direttiva `#include <stdio.h>` copia e incolla testualmente il contenuto del file `stdio.h` all'inizio del nostro codice. Questo fornisce al compilatore i prototipi delle funzioni (es. `printf`).
    
2. **Compilazione**: Il compilatore traduce il nostro file `.c` in un file oggetto (`.o`). Quando incontra una chiamata a `printf`, si "fida" del prototipo e genera un riferimento a una funzione `printf` che si aspetta di trovare in seguito.
    
3. **Linking**: Il **linker** è il programma che unisce il nostro file oggetto (`.o`) con il codice precompilato della libreria standard (che contiene l'implementazione di `printf`). Il linker risolve il riferimento e produce l'eseguibile finale.
    

Esistono due tipi di `include`:

- `#include <nome_libreria.h>`: Usato per le librerie di sistema. Il compilatore le cerca in percorsi predefiniti.
    
- `#include "mio_file.h"`: Usato per le librerie definite dall'utente. Il compilatore le cerca prima nella directory corrente.