## Procedure di Prenotazione alla Prova Intercorso

La lezione inizia con una dettagliata spiegazione delle procedure amministrative necessarie per la prenotazione alla prova intercorso. Prima di compilare il modulo di prenotazione, il cui link sarà pubblicato sulla piattaforma Teams, gli studenti devono completare una serie di passaggi preliminari per verificare il corretto funzionamento delle proprie credenziali e l'accesso ai servizi di ateneo.

### Prerequisiti Tecnici e Amministrativi

1. **Iscrizione al Corso su Moodle**: È necessario effettuare l'accesso alla piattaforma Moodle di Ateneo (`moodle.unina.it`) tramite le credenziali istituzionali, utilizzando l'opzione **Open ID Connect**. Una volta autenticati, gli studenti devono navigare fino alla pagina del corso (tramite la sezione Dipartimento di Ingegneria Elettrica e delle Tecnologie dell'Informazione e cercando il cognome del docente) e iscriversi utilizzando la chiave di iscrizione: `fondamenti2025` (tutto minuscolo). Eventuali problemi di accesso devono essere segnalati alla segreteria o al CSI, poiché non sono di competenza del docente.
    
2. **Recupero del PIN**: Ogni studente deve essere in possesso del proprio PIN, reperibile sulla piattaforma Segrepass. Il PIN è indispensabile per la verbalizzazione di tutti gli esami futuri.
    
3. **Generazione del PUK**: Il PUK è un codice necessario, tra le altre cose, per il reset della password dell'account istituzionale. Per generarlo, è necessario:
    
    - Accedere al portale OpenAM di Ateneo.
        
    - Seguire il percorso `Attiva/Resetta Password > Cambio Password Dipendenti Studenti`.
        
    - Se non si possiede il PUK, cliccare su "Nuovo PUK".
        
    - La procedura richiede l'utilizzo dell'**app IO**, sulla quale verrà notificato il nuovo PUK. Si consiglia di verificare preventivamente sull'app IO se il PUK sia già stato inviato al momento dell'immatricolazione.
        
    - È fondamentale annotare e conservare in un luogo sicuro sia il PIN che il PUK.
        
4. **Installazione di Microsoft Authenticator**: L'app Microsoft Authenticator deve essere installata e configurata sul proprio smartphone. Sarà utilizzata per l'autenticazione a due fattori durante la prova, specialmente accedendo ai computer del laboratorio.
    
5. **Consegna delle Esercitazioni**: Un requisito interno al corso è aver consegnato tutte le esercitazioni asincrone prima della prova.
    

Le prenotazioni rimarranno aperte per una settimana, fino al giovedì successivo. Questo permetterà di definire il numero di partecipanti e organizzare i turni, che verranno comunicati su Teams.

## Visibilità degli Identificatori (Scope)

La seconda parte della lezione riprende i concetti di programmazione in C, focalizzandosi sulla **visibilità** (o _scope_) degli identificatori, un concetto introdotto in [[14 - Programmazione Modulare, Funzioni, Procedure e Visibilità delle Variabili.md|lezioni precedenti]]. Lo scope definisce la regione di codice sorgente in cui un identificatore (come una variabile o una funzione) è riconosciuto e utilizzabile.

Al concetto di scope è strettamente legato il **tempo di vita** (_lifetime_) di una variabile, ovvero l'intervallo di tempo durante l'esecuzione del programma in cui la variabile esiste e occupa memoria.

### Variabili Locali e Globali

- **Variabili Locali**: Sono dichiarate all'interno di un blocco di codice (delimitato da parentesi graffe `{}`), come il corpo di una funzione, un ciclo o un blocco $if$.
    
    - **Visibilità**: Limitata esclusivamente al blocco in cui sono definite (scope di blocco).
        
    - **Tempo di Vita**: Generalmente hanno una _durata di memorizzazione automatica_ (automatic storage duration). Vengono create (allocate nello _stack_) quando il flusso di esecuzione entra nel blocco e distrutte (deallocate) quando il flusso ne esce.
        
    - Anche i parametri formali di una funzione sono considerati variabili locali al corpo della funzione stessa.
        
- **Variabili Globali**: Sono dichiarate al di fuori di qualsiasi funzione, solitamente all'inizio del file sorgente.
    
    - **Visibilità**: Visibili in tutto il file sorgente (l'unità di compilazione) a partire dal punto in cui vengono dichiarate (scope di file).
        
    - **Tempo di Vita**: Hanno una _durata di memorizzazione statica_ (static storage duration). Esistono per l'intera durata dell'esecuzione del programma.
        

L'uso di identificatori identici per variabili in ambiti di visibilità differenti (es. una variabile $area$ nel $main$ e una variabile $area$ nella funzione $area\_cerchio$) è lecito e non genera conflitti, proprio perché si tratta di entità distinte con scope locale.

### Il Fenomeno dello Shadowing (Mascheramento)

Lo _shadowing_ si verifica quando una variabile dichiarata in un blocco interno (es. un ciclo $for$) ha lo stesso nome di una variabile dichiarata in un blocco esterno (es. la funzione $main$).

All'interno del blocco interno, l'identificatore si riferirà **sempre** alla variabile più interna (quella locale), "mascherando" o "nascondendo" quella esterna. La variabile esterna rimane inalterata dalle operazioni eseguite sulla variabile interna e torna ad essere visibile non appena il flusso esce dal blocco interno.

Esempio tipico è un [[13 - I Costrutti Iterativi 'do-while' e 'for'.md|Costrutto for]] (secondo lo standard C99 o successivi):

```c
int i = 80; // Variabile esterna
printf("Valore di i prima del ciclo: %d\n", i);

for (int i = 0; i < 3; i++) { // Nuova variabile 'i' locale al ciclo
    // Qui 'i' si riferisce alla variabile locale del ciclo
    printf("Ciclo (i locale): %d\n", i);
}
// Fine dello scope della 'i' locale

// Qui 'i' si riferisce di nuovo alla variabile esterna
printf("Valore di i dopo il ciclo: %d\n", i); // Stamperà 80
```

_Nota: Nello standard C89 (ANSI C), non era possibile dichiarare la variabile contatore all'interno dell'intestazione del ciclo_ $for$_._

## Passaggio dei Parametri per Valore

In linguaggio C, i parametri alle funzioni vengono passati **sempre e solo per valore** (_pass-by-value_).

Questo meccanismo, discusso in [[14 - Programmazione Modulare, Funzioni, Procedure e Visibilità delle Variabili.md|Programmazione Modulare]], implica che:

1. Quando una funzione viene chiamata, il valore di ogni _parametro attuale_ (l'argomento nella chiamata) viene calcolato.
    
2. Viene creata una copia di ciascun valore.
    
3. Queste copie vengono assegnate ai _parametri formali_ della funzione (le variabili locali definite nella sua segnatura).

La funzione opera esclusivamente su queste copie locali.

La conseguenza fondamentale è che **qualsiasi modifica apportata ai parametri formali all'interno della funzione non ha alcun effetto sulle variabili originali nel chiamante**. Questo protegge le variabili del chiamante da modifiche indesiderate.

Questo concetto è stato dimostrato con una funzione $swap$ che tenta, senza successo, di scambiare i valori di due variabili passate dal $main$:

```c
// Funzione 'swap' errata
void swap(int a, int b) {
    // 'a' e 'b' sono copie locali di 'x' e 'y'
    int temp = a;
    a = b;
    b = temp;
    // Le modifiche avvengono solo sulle copie locali.
    // Queste variabili cessano di esistere alla fine della funzione.
}

int main() {
    int x = 5, y = 10;
    printf("Prima: x = %d, y = %d\n", x, y);
    swap(x, y);
    printf("Dopo: x = %d, y = %d\n", x, y); // x e y mantengono 5 e 10
    return 0;
}
```

Per permettere a una funzione di modificare variabili esterne, non si deve passare il loro valore, ma il loro **indirizzo di memoria**, utilizzando i **puntatori**.

## La Funzione `main` e le Librerie

### Ruolo della Funzione `main`

La funzione $main$ è il cuore di ogni [[10 - Struttura dei Programmi in C, Input e Output e Variabili.md|Struttura di un programma C]]:

- **Entry Point**: È la funzione da cui inizia l'esecuzione di ogni programma C.
    
- **Unicità**: Un programma C deve contenere una e una sola funzione $main$.
    
- **Segnatura Standard**: Le segnature più comuni sono:
    
    - `int main(void)`: Se il programma non riceve parametri dalla riga di comando.
        
    - `int main(int argc, char *argv[])`: Se il programma deve leggere argomenti dalla riga di comando ($argc$ è il conteggio, $argv$ è l'array di stringhe).
        
- **Valore di Ritorno**: La dichiarazione $int main()$ implica che la funzione deve restituire un valore intero ($int$). Per convenzione, `return 0;` (o la costante $EXIT\_SUCCESS$ da $<stdlib.h>$) segnala al sistema operativo che il programma è terminato correttamente. Valori diversi da zero (o $EXIT\_FAILURE$) indicano tipicamente un errore.
    

### Inclusione di Librerie

Una libreria è una raccolta di sottoprogrammi (funzioni, costanti, tipi). Per utilizzarle si usa la direttiva del preprocessore $#include$.

- `#include <nome_libreria.h>`: Usata per le librerie di sistema (es. $stdio.h$, $math.h$). Il compilatore cerca i file in percorsi predefiniti (le _include path_ di sistema).
    
- `#include "percorso_libreria.h"`: Usata per librerie personalizzate (file header creati dall'utente). Il compilatore cerca prima il file nel percorso specificato (spesso la directory corrente), e _poi_ nei percorsi di sistema.
    

## Compilazione Separata

Per progetti complessi, è buona norma suddividere il codice in più file, separando l'**interfaccia** (cosa fa un modulo) dall'**implementazione** (come lo fa). Questo processo è noto come **compilazione separata** ed è fondamentale per la modularità, la manutenibilità e il riutilizzo del codice.

Si basa sull'uso di tre tipi di file:

1. **File Header (`.h`)**: Contiene le **dichiarazioni** (l'interfaccia pubblica o "contratto" della libreria).
    
    - Prototipi delle funzioni (es. `int somma(int a, int b);`).
        
    - Definizioni di tipi (`typedef`).
        
    - Costanti globali (`#define`) o variabili $extern$.
        
    - _Non_ deve contenere l'implementazione (il corpo) delle funzioni.
        
2. **File di Implementazione (`.c`)**: Contiene le **definizioni** (l'implementazione) delle funzioni dichiarate nel file header.
    
    - Deve includere il proprio file header (es. `#include "mia_libreria.h"`) per permettere al compilatore di verificare la coerenza tra dichiarazioni e definizioni.
        
3. **File Client o di Test (`.c`)**: Un file $main.c$ che utilizza le funzionalità esposte dalla libreria.
    
    - Contiene la funzione $main$.
        
    - Deve includere il file header della libreria che intende usare (es. `#include "mia_libreria.h"`).
        

### Processo di Compilazione

Il [[09 - Fondamenti di Programmazione in C, Compilazione ed Errori.md|Processo di Compilazione]] di un progetto multi-file (come evidenziato nel file `12_Lesson_FI_Sottoprogrammi e Librerie.pdf`) avviene in due fasi:

1. **Compilazione (Creazione dei File Oggetto)**: Ogni file sorgente `.c` viene compilato _separatamente_ per generare un file oggetto (`.o`) corrispondente. Questo è codice macchina quasi completo, ma mancano i riferimenti alle funzioni definite altrove.
    
    - Il flag `$gcc -c$` indica al compilatore di "compilare solo, non linkare".
        
    
    ```
    # Compila main.c e produce main.o
    gcc -c main.c
    # Compila lib.c e produce lib.o
    gcc -c lib.c
    ```
    
2. **Linking**: Il _linker_ (l'ultima fase del processo) prende tutti i file oggetto (`.o`) e li "collega" insieme, risolvendo i riferimenti incrociati (es. la chiamata a $somma$ in $main.o$ viene collegata alla sua definizione in $lib.o$). Collega anche le librerie di sistema necessarie (es. $stdio$ per $printf$).
    
    - Il flag `-o` specifica il nome del file eseguibile finale.
        
    
    ```
    # Collega main.o e lib.o per creare l'eseguibile 'programma'
    gcc -o programma main.o lib.o
    ```
    

In alternativa, si può eseguire tutto con un unico comando (il compilatore gestirà internamente i passaggi):

```
gcc -o programma main.c lib.c
```

### Include Guards (Direttive di Inclusione Condizionale)

Un file header potrebbe essere incluso più volte nella stessa unità di compilazione (ad esempio, se $main.c$ include $libA.h$ e $libB.h$, e $libB.h$ a sua volta include $libA.h$). Questo causerebbe errori di "ridefinizione" da parte del compilatore.

Per evitare questo, si utilizzano le **include guards**, delle direttive per il preprocessore:

```c
// All'inizio del file "mia_libreria.h"
#ifndef MIA_LIBRERIA_H
#define MIA_LIBRERIA_H

// ----- Contenuto del file header -----
// (prototipi, typedef, etc.)

int somma(int a, int b);
// ...

// ----- Fine contenuto -----

#endif // MIA_LIBRERIA_H
```

_Come funziona:_

1. La prima volta che il file viene incluso, $MIA\_LIBRERIA\_H$ non è definito.
    
2. `#ifndef` (if not defined) è vera.
    
3. `#define MIA_LHBRERIA_H` definisce la macro.
    
4. Il contenuto dell'header viene letto.
    
5. Alle inclusioni successive _nello stesso file_ $.c$, $MIA\_LIBRERIA\_H$ è ormai definito.
    
6. `#ifndef` è falsa, e il preprocessore salta tutto il contenuto fino a `#endif`, evitando la ridefinizione.
    

_Nota: Molti compilatori moderni supportano anche la direttiva non standard `#pragma once`, che ha lo stesso scopo ma va inserita solo come prima riga del file header._
