# Il Modello di Esecutore: Il Calcolatore

Un **calcolatore** è una macchina che, in maniera automatica e ad altissima velocità, esegue operazioni elementari dettate da un algoritmo memorizzato. Il suo funzionamento è governato da un programma, che risiede nella sua memoria. Il calcolatore non possiede capacità decisionale o discrezionale autonoma, ma si limita a compiere determinate azioni secondo procedure prestabilite, agendo come un esecutore obbediente. La sua velocità operativa si misura in **MIPS (Milioni di Istruzioni Per Secondo)**.

Le operazioni che un calcolatore può compiere sono in numero limitato. Azioni complesse vengono realizzate attraverso la combinazione di queste operazioni elementari. Affinché il calcolatore possa operare, l'algoritmo e i dati devono essere comunicati in un linguaggio a esso comprensibile, tipicamente una [[Fondamenti di Informatica/02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria|rappresentazione binaria]].

Data la sua natura deterministica, un calcolatore è intrinsecamente affidabile: non commette errori nell'esecuzione di un algoritmo. Eventuali risultati errati sono quasi sempre da attribuire a errori nella logica del programma fornito (errori di programmazione) e non a un malfunzionamento della macchina.

## Cenni Storici sull'Evoluzione dei Calcolatori

### I Primi Calcolatori: L'ENIAC

Uno dei primi e più celebri esempi di computer è l'**ENIAC** (Electronic Numerical Integrator and Computer), realizzato nel 1946. Si trattava di una macchina di dimensioni imponenti, caratterizzata da essere una macchina limitata, quasi priva di memoria e con scarsa elasticità operativa. I programmi non erano memorizzati internamente, ma venivano configurati manualmente dagli operatori attraverso complessi cablaggi fisici, un'interazione diretta con l'hardware senza gli strati di astrazione moderni.

### La Macchina Universale di Turing

Il fondamento teorico del calcolatore moderno fu posto da **Alan Turing** nel 1937 con il suo saggio *"On Computable Numbers, with an Application to the Entscheidungsproblem"*. L'idea rivoluzionaria di Turing era quella di permettere a un computer (l'hardware) di eseguire istruzioni codificate in un programma (il software) inseribile e modificabile dall'esterno. Questo concetto astratto, noto come **Macchina di Turing**, descriveva un dispositivo universale capace di eseguire qualsiasi algoritmo, operando su un nastro di lunghezza infinita (memoria) per mezzo di una testina in grado di leggere e scrivere simboli.

### L'Architettura di Von Neumann e l'EDVAC

Il passo decisivo verso il calcolatore moderno fu compiuto da **John Von Neumann**, che nel 1945 propose un'architettura nel suo documento *"First Draft of a Report on the Edvac"*. Questo modello rappresentò la realizzazione pratica della macchina universale inventata da Turing e portò alla costruzione dell'**EDVAC** (Electronic Discrete Variable Automatic Computer) nel 1949, il primo computer programmabile nel senso moderno del termine, basato sul concetto di **programma memorizzato** (*stored-program computer*).

L'architettura di Von Neumann introduce il principio fondamentale che sia le istruzioni (il programma) sia i dati su cui operare risiedono nella stessa memoria, permettendo alla macchina di trattare le istruzioni come dati e viceversa. Questo modello, sebbene oggi evoluto, costituisce ancora lo schema di principio su cui si basa la maggior parte dei calcolatori.

## L'Architettura di Von Neumann

Il modello di Von Neumann descrive un calcolatore come un sistema composto da tre sottosistemi principali interconnessi:

1.  **CPU (Central Processing Unit):** L'unità centrale di elaborazione, che coordina ed esegue le operazioni fondamentali.
2.  **Memoria:** Il sottosistema che contiene l'algoritmo con le operazioni da eseguire e i dati su cui si opera.
3.  **Unità di Input/Output (I/O):** I dispositivi che consentono l'inserimento di algoritmi e dati in memoria (input) e permettono di presentare i risultati dell'attività della CPU (output).

## La Central Processing Unit (CPU)

La CPU, detta anche **processore**, è il "cervello" del calcolatore. Ha il compito di acquisire, interpretare ed eseguire le istruzioni del programma contenuto in memoria centrale, operando la trasformazione dei dati.

### Struttura della CPU
La CPU è a sua volta composta da tre parti fondamentali:

*   **Unità di Controllo (Control Unit - CU):** Interpreta le singole istruzioni del programma e attiva tutti i meccanismi necessari al loro espletamento, generando i segnali di controllo che coordinano le altre parti del calcolatore. In senso stretto, il termine "processore" corrisponde alla CU.
*   **Unità Aritmetico-Logica (ALU - Arithmetic Logic Unit):** Esegue operazioni aritmetiche, di confronto o [[Fondamenti di Informatica/05 - Codifica Digitale di Testo, Media e Logica Booleana#Operatori Logici e Tabelle di Verità|bitwise]] sui dati.
*   **Registri Interni:** Piccole e velocissime unità di memoria interne alla CPU, utilizzate per depositare temporaneamente informazioni durante le elaborazioni.

### Il Ciclo del Processore
L'Unità di Controllo opera in maniera ciclica, controllando che una serie di fasi vengano correttamente eseguite. Questo ciclo è noto come **ciclo del processore**.

1.  **Boot (Avvio):** Operazione iniziale, eseguita all'accensione, che informa la CU dell'indirizzo di memoria contenente la prima istruzione da eseguire.
2.  **Fetch (Prelievo):** Un'istruzione viene prelevata dalla memoria centrale, decodificata e memorizzata in un registro interno. Questa fase è anche detta *Instruction Fetch and Decode*.
3.  **Decode/Operand Assembly (Decodifica/Assemblaggio Operandi):** La CU interpreta il codice operativo dell'istruzione e, se necessario, preleva dalla memoria i dati (operandi) su cui l'istruzione deve agire.
4.  **Execute (Esecuzione):** L'istruzione viene eseguita. La CU invia i segnali appropriati, tipicamente attivando l'ALU per effettuare il calcolo.

Questo ciclo si ripete per ogni istruzione del programma.

### L'Unità Aritmetico-Logica (ALU)
L'ALU è il nucleo computazionale della CPU. È in grado di eseguire:
*   **Operazioni Aritmetiche:** Somma, sottrazione, etc.
*   **Operazioni di Confronto:** Maggiore, minore, uguale.
*   **Operazioni Logiche e Bitwise:** Operazioni booleane come [[Fondamenti di Informatica/05 - Codifica Digitale di Testo, Media e Logica Booleana#Operatori Logici e Tabelle di Verità|AND, OR, NOT]] eseguite bit a bit sugli operandi.

L'esito dei suoi calcoli viene segnalato da appositi bit in un registro chiamato **Condition Code**.

### I Registri Interni della CPU
I registri sono memorie ad altissima velocità, con tempi di accesso inferiori a quelli della memoria centrale, e sono cruciali per le performance. I registri principali includono:

*   **Prossima Istruzione (PI) o Program Counter (PC):** Ricorda alla CU la **posizione** in memoria della successiva istruzione da eseguire. Dopo ogni prelievo di un'istruzione, il suo valore viene aggiornato per puntare alla prossima.
*   **Instruction Register (IR):** Contiene l'**istruzione** prelevata dalla memoria che la CU sta eseguendo.
*   **Accumulatore (ACC):** Serve come **deposito** di dati da parte dell'ALU. Può contenere uno degli operandi prima di un'operazione e, al termine, il risultato calcolato.
*   **Condition Code (CC) o Status Register (SR):** Indica le **condizioni** che si verificano durante l'elaborazione, quali risultato nullo, [[Fondamenti di Informatica/02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria#Condizione di Overflow|overflow]], o il risultato di un'operazione non valido (NaN).
*   **Memory Address Register (MAR):** Contiene l'indirizzo della locazione di memoria a cui si vuole accedere.
*   **Memory Data Register (MDR):** Contiene il dato letto dalla memoria o da scrivere in memoria.

## Il Sottosistema di Memoria

La memoria è un insieme di contenitori fisici di dimensioni finite e fissate, detti **registri**. La memoria centrale di un computer è organizzata come un array di stringhe di bit, dette **[[Fondamenti di Informatica/01 - Introduzione al Corso e Fondamenti dell'Informazione#Byte, Word e Multipli|parole o word]]**.

### Struttura e Organizzazione della Memoria
*   La posizione di un registro nell'insieme si chiama **indirizzo di memoria**. Ogni parola è individuata da un indirizzo univoco, un intero compreso tra $0$ e $N-1$.
*   La dimensione di un registro si misura in numero di bit.
*   L'insieme di tutti gli indirizzi possibili, da $0$ a $N-1$, è detto **spazio di indirizzamento**. Se gli indirizzi sono codificati con $k$ bit, lo spazio di indirizzamento contiene $N = 2^k$ locazioni.

### Operazioni sulla Memoria: Lettura e Scrittura
Le operazioni fondamentali che la CPU può eseguire sulla memoria sono:

*   **Lettura (Read o Load):** Preleva l'informazione contenuta nel registro di memoria senza però distruggerla. L'operazione è **non distruttiva**.
*   **Scrittura (Write o Store):** Inserisce una informazione nel registro di memoria, eliminando quella precedente. L'operazione è **distruttiva**.

Un **buffer** è un'area di transito dei dati dalla CPU alla memoria e viceversa.

### Prestazioni e Tipi di Accesso alla Memoria
Le prestazioni della memoria sono misurate dal **tempo di accesso**. In base a come si accede alle locazioni, le memorie si dividono in:

*   **Memorie ad Accesso Casuale (RAM - Random Access Memory):** Il tempo di accesso non dipende dalla posizione del registro.
*   **Memorie ad Accesso Sequenziale (SAM - Sequential Access Memory):** Il tempo di accesso dipende dalla posizione del registro (es. nastri magnetici).

### Classificazione delle Memorie: Volatilità e Permanenza
*   **Memorie Volatili:** Perdono le informazioni registrate quando il sistema viene spento (es. RAM).
*   **Memorie Permanenti:** Conservano le informazioni anche in assenza di alimentazione (es. memorie magnetiche, ottiche, ROM).

Una **ROM (Read-Only Memory)** è una memoria realizzata in modo che sia possibile una sola scrittura di informazioni. Un esempio critico è il **BIOS (Basic Input-Output System)**, un insieme di programmi su ROM che fornisce funzionalità di base per l'accesso all'hardware.

### Memoria Centrale e Memoria di Massa
Nel modello di Von Neumann si distingue tra:

*   **Memoria Centrale (o Principale):** Memoria con cui la CPU può interagire direttamente. È tipicamente una RAM, quindi veloce ma volatile.
*   **Memoria di Massa (o Ausiliaria):** Memorie ausiliarie caratterizzate da una elevata capacità di archiviazione (es. SSD, Hard Disk), ma con tempi di accesso maggiori.

## Trasferimento dei Dati e Comunicazione tra Componenti

### Interazione tra CPU, Memoria Centrale e Memoria di Massa
A causa della grande differenza di velocità, la CPU non comunica direttamente con la memoria di massa. Il flusso di dati segue una gerarchia:

*   **CPU <-> Memoria Centrale:** Le informazioni possono essere direttamente prelevate dalla CPU.
*   **Memoria di Massa -> CPU:** Le informazioni devono essere dapprima trasferite nella memoria centrale e successivamente elaborate.
*   **CPU -> Memoria di Massa:** Le informazioni prodotte dalla CPU devono essere depositate in memoria centrale per poi essere conservate nelle memorie di massa.

### Le Aree di Buffer
Per ovviare alla differenza di velocità tra i dispositivi, la memoria centrale contiene delle **aree di accumulo (buffer)**. Con i buffer si procede verso una **separazione dei compiti** tra i componenti del modello:

*   **Buffer di Input:** Ha il compito di accumulare dati in memoria ricevendoli da un dispositivo lento prima che la CPU provveda ad elaborarli.
*   **Buffer di Output:** La CPU, molto più veloce, accumula i dati prodotti in un buffer di uscita prima di abilitarne il trasferimento.

## Il Sottosistema di Input/Output
Questo sottosistema raggruppa tutti i dispositivi (periferiche) che consentono la comunicazione tra il calcolatore e l'esterno. Esempi includono:
*   **Unità di Input:** Tastiera, mouse, scanner.
*   **Unità di Output:** Monitor, stampante.

## I Canali di Comunicazione: Il Sistema di Bus
I vari sottosistemi del calcolatore comunicano tra loro attraverso un **canale di comunicazione condiviso** chiamato **bus**. L'utilizzo di un bus favorisce la **modularità** e l'**espandibilità** del calcolatore.

Il bus di sistema permette alla CPU di comunicare con la memoria e con tutti i dispositivi di input ed output. È logicamente suddiviso in tre bus specializzati:

1.  **Bus Indirizzi (Address Bus):** Canale **unidirezionale** su cui la CPU invia l'indirizzo del dispositivo interessato dall'operazione.
2.  **Bus Dati (Data Bus):** Canale **bidirezionale** su cui transitano i dati effettivi, sia dalla CPU verso la memoria/I/O, sia viceversa, per operazioni di STORE e LOAD.
3.  **Bus di Controllo (Control Bus):** Canale **bidirezionale** su cui viaggiano i segnali che sincronizzano e gestiscono le operazioni (es. segnali di *read* e *write*).