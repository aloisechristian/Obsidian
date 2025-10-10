# Introduzione ai Fondamenti della Programmazione

La **programmazione** è definita come la capacità di progettare **[[Fondamenti di Informatica/08 - Introduzione ad Algoritmi, Complessità e Linguaggi di Programmazione|algoritmi]]** indipendentemente dal linguaggio specifico, per istruire un esecutore (tipicamente un **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann|calcolatore]]** basato sull'**[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann|architettura di Von Neumann]]**) a risolvere un problema. La complessità di tale attività è direttamente proporzionale alla complessità del problema. A questa si affianca la **codifica**, ovvero il processo di traduzione dell'algoritmo in un linguaggio appropriato per l'esecutore. Nel contesto della programmazione, il linguaggio di destinazione è il **[[Fondamenti di Informatica/08 - Introduzione ad Algoritmi, Complessità e Linguaggi di Programmazione#8. Linguaggi di Programmazione: Struttura e Livelli|linguaggio macchina]]**, l'unico direttamente comprensibile dalla CPU.

La scrittura di un algoritmo in un linguaggio di programmazione produce un **programma**. Un linguaggio di programmazione è una notazione formale caratterizzata da:

*   **Alfabeto**: un insieme di simboli permessi.
*   **Lessico**: le regole che definiscono le "parole" valide del linguaggio.
*   **Sintassi e Grammatica**: le regole per combinare le parole in istruzioni (frasi) ben formate.
*   **Semantica**: il significato associato alle istruzioni.

### Il Linguaggio C e C++

Il corso si focalizzerà sul linguaggio **C**, esteso con alcuni elementi del **C++**. Il C fu sviluppato nel 1972 da **Dennis Ritchie** presso i laboratori AT&T Bell Labs. Successivamente, l'**American National Standards Institute (ANSI)**, già noto per la standardizzazione del codice **[[Fondamenti di Informatica/05 - Codifica Digitale di Testo, Media e Logica Booleana#Gli Standard Storici: ASCII ed Estensioni|ASCII]]**, ne ha definito una versione standardizzata nota come **ANSI C** nel 1989.

Il C è classificato come un linguaggio di **alto livello**, in quanto fornisce un livello di astrazione superiore rispetto al linguaggio macchina, rendendolo più vicino alla comprensione umana e indipendente dall'architettura hardware. Nonostante ciò, il C possiede una notevole potenza espressiva, poiché offre meccanismi di basso livello che consentono un controllo granulare della memoria, fino alla manipolazione dei singoli bit.

All'inizio degli anni '80, **Bjarne Stroustrup** estese il C nel linguaggio **C++**, che introduce i paradigmi della **programmazione orientata agli oggetti (Object-Oriented Programming, OOP)**. Questa estensione, pienamente compatibile con il C, non sarà oggetto di approfondimento in questo corso.

## Dal Codice Sorgente all'Esecuzione: Il Processo di Compilazione

Il linguaggio C è un linguaggio **compilato**. Ciò significa che un programma scritto in C deve attraversare un processo di traduzione articolato in più fasi prima di poter essere eseguito. Tale processo trasforma il codice sorgente in un file eseguibile specifico per un'architettura target.

I passaggi fondamentali sono i seguenti:

1.  **Scrittura del Codice Sorgente**: Il programmatore scrive il codice in un file di testo, convenzionalmente con estensione `.c`, utilizzando un editor.
2.  **Compilazione**: Il **compilatore** analizza il file sorgente, verifica la presenza di errori di sintassi e traduce il codice in un **file oggetto** (con estensione `.o` nei sistemi Unix-like o `.obj` in Windows). Se vengono riscontrati errori, il processo si interrompe.
3.  **Collegamento (Linking)**: Il **linker** prende il file oggetto generato dal compilatore e lo unisce ad altri moduli necessari. Questi possono includere altri file oggetto o **librerie** esterne (es. `lib.a`), che contengono codice precompilato per funzionalità comuni. Il linker risolve i "riferimenti esterni", ovvero le chiamate a funzioni definite al di fuori del file sorgente principale.
4.  **Generazione dell'Eseguibile**: Al termine del collegamento, viene prodotto un **file eseguibile** (es. `prog.out` su sistemi Unix-like o `prog.exe` su Windows). Questo file contiene il codice macchina completo e pronto per l'esecuzione.
5.  **Caricamento (Loading)**: Il **loader**, un componente del sistema operativo, carica il file eseguibile dalla **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Memoria Centrale e Memoria di Massa|memoria di massa]]** alla **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Memoria Centrale e Memoria di Massa|memoria centrale (RAM)]]**.
6.  **Esecuzione**: La **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#La Central Processing Unit (CPU)|CPU]]** inizia a eseguire le istruzioni del programma. L'**[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Struttura della CPU|Unità di Controllo (CU)]]** gestisce il **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Il Ciclo del Processore|ciclo di fetch-decode-execute]]**: preleva (`fetch`) un'istruzione dalla RAM (il cui indirizzo è nel registro **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#I Registri Interni della CPU|Program Counter]]**), la memorizza nell'**[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#I Registri Interni della CPU|Instruction Register]]**, la decodifica (`decode`) e infine la esegue (`execute`), coordinando l'**[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#L'Unità Aritmetico-Logica (ALU)|ALU]]**.

### Linguaggi Compilati vs. Interpretati

È importante distinguere i linguaggi compilati da quelli **interpretati** (es. Python, Java):

*   **Compilazione**: La traduzione avviene una sola volta, prima dell'esecuzione. L'eseguibile generato può essere avviato più volte senza necessità di ricompilare. Questo processo garantisce tempi di esecuzione più brevi.
*   **Interpretazione**: La traduzione avviene istruzione per istruzione ogni volta che il programma viene eseguito, tramite un software chiamato **interprete**. Non viene generato un file eseguibile separato, il che garantisce maggiore portabilità del codice ma a costo di tempi di esecuzione più lunghi.

## Ambienti di Sviluppo e Leggibilità del Codice

Per facilitare la programmazione, si utilizzano gli **Ambienti di Sviluppo Integrato (IDE - Integrated Development Environment)**. Un IDE è un software che unisce:

*   Un **editor** avanzato per la scrittura del codice.
*   Un **compilatore** per la traduzione in file oggetto.
*   Un **linker** per la generazione dell'eseguibile.
*   Un **debugger** per l'individuazione e la correzione degli errori.

La **formattazione del codice**, come l'**indentazione** (l'uso di rientri per evidenziare la struttura dei blocchi), è cruciale per la **leggibilità**. Un codice ben formattato è più facile da comprendere e manutenere.

Per il corso, si consiglia l'uso di **VS Codium**, un IDE offline. Alternative includono strumenti online come **OnlineGDB** o le funzionalità integrate in piattaforme come **Moodle**.

### Un Primo Esempio: "Hello, World"

Il programma `Hello, World` stampa una stringa sullo schermo.
```  c
// Il primo programma in C  
#include <stdio.h> 
  
int main() {  
printf("Hello, World!\n");  
return 0;  
}  
```  
Componenti principali:  
* `// ...`: **Commento** a linea singola.  
* `#include `: **Direttiva per il preprocessore** che include la libreria standard di input/output.  
* `int`, `return`: **Parole chiave** del linguaggio.  
* `main`, `printf`: **Identificatori** (nomi di funzioni).  
* `()`, `{}`, `;`: **Delimitatori** e simboli speciali.  
* `"Hello, World!\n"`: **Costante stringa**.  
  
## Classificazione degli Errori di Programmazione  
  
Durante lo sviluppo di un programma, possono verificarsi diverse tipologie di errori.  
  
### 1. Errori a Tempo di Compilazione (Compile-Time Errors)  
  
Vengono rilevati dal compilatore e impediscono la creazione del file oggetto. Si dividono in:  
* **Errori Lessicali**: Simili a errori di ortografia, si verificano quando si utilizza una parola non riconosciuta o si scrive male una parola chiave (es. `ret rn` invece di `return`).  
* **Errori Sintattici**: La struttura delle istruzioni viola la grammatica del linguaggio (es. omettere un punto e virgola `;` alla fine di un'istruzione).  
* **Errori Semantici**: Il codice è sintatticamente corretto ma privo di senso logico (es. il tentativo di confrontare una variabile numerica con una stringa di caratteri).  
* **Warning (Avvisi)**: Segnalazioni di problemi meno gravi che non bloccano la compilazione ma indicano potenziali comportamenti anomali.  
  
### 2. Errori a Tempo di Collegamento (Link-Time Errors)  
  
Rilevati dal linker quando non riesce a risolvere un riferimento a un simbolo esterno, ad esempio se si invoca una funzione dichiarata ma mai definita.  
  
### 3. Errori a Tempo di Esecuzione (Run-Time Errors)  
  
Si manifestano solo quando il programma è in esecuzione.  
* **Errori di Caricamento**: Il loader non riesce a caricare il programma in memoria, ad esempio per mancanza di memoria (`out of memory`).  
* **Errori di Esecuzione (Bug o Eccezioni)**: Si verificano a causa di operazioni illecite, come una divisione per zero. Possono causare l'interruzione anomala del programma.  
  
### 4. Errori Logici  
  
Sono gli errori più insidiosi. Il programma compila ed esegue senza bloccarsi, ma produce risultati errati perché l'algoritmo implementato è scorretto. Possono essere scoperti solo attraverso un'attenta fase di **testing**. Un errore logico comune può portare a un **ciclo infinito**, bloccando l'esecuzione.