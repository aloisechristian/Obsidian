# Introduzione agli Algoritmi e alla Complessità Computazionale

Questa lezione introduce i concetti fondamentali di algoritmo, complessità computazionale e la loro relazione con i modelli di calcolo e i linguaggi di programmazione. L'obiettivo è comprendere come un problema viene formalizzato, come si progetta una soluzione algoritmica e come si valuta la sua efficienza prima di tradurla in un programma eseguibile da un calcolatore.

### 1. Definizione di Algoritmo

Un **algoritmo** è definito come una sequenza finita e ordinata di operazioni elementari, non ambigue, che, se eseguite, portano alla soluzione di un problema appartenente a una determinata classe. Ogni passo di questa sequenza è denominato **istruzione**.

L'informatica, come suggerisce l'etimologia francese (*information* + *automatique*), è la scienza del trattamento automatico dell'informazione. In questo contesto, può essere vista come lo studio sistematico degli algoritmi, con un focus sulla loro progettazione, analisi e traduzione in un formato eseguibile da un **esecutore**.

Nel nostro dominio, l'esecutore è il **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann|calcolatore]]** (computer), una macchina elettronica che esegue istruzioni in modo automatico, affidabile, deterministico e ad altissima velocità, misurabile in **MIPS (Milioni di Istruzioni Per Secondo)**.

Il termine "algoritmo" deriva dalla latinizzazione del nome del matematico persiano del IX secolo, Muhammad ibn Musa **al-Khwarizmi**, considerato uno dei primi a formalizzare procedure di calcolo sistematiche.

### 2. Dalla Specifica del Problema al Programma

La risoluzione di un problema inizia con una **specifica**, ovvero una descrizione in linguaggio naturale che definisce:

*   **Dati di input:** Le informazioni fornite al problema.
*   **Dati di output:** Il risultato atteso.

Un problema può essere visto formalmente come una [[Analisi I/01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] che mappa un insieme di input a un insieme di output. La natura dei dati, descrivibile tramite la **[[Fondamenti di Informatica/01 - Introduzione al Corso e Fondamenti dell'Informazione#La Tripla Tipo-Attributo-Valore|tripla Tipo-Attributo-Valore]]**, può influenzare l'algoritmo. Ad esempio, sommare due numeri a una cifra in binario può generare un riporto come output aggiuntivo (`1+1=0` con riporto `1`), mentre la somma in colonna di numeri a più cifre gestisce il riporto internamente, producendo un unico risultato numerico.

Un **programma** è la codifica di un algoritmo in un linguaggio specifico, comprensibile all'esecutore. Quando l'esecutore è un calcolatore, tale linguaggio è detto **linguaggio di programmazione**.

## Modelli di Calcolo e Proprietà dei Problemi

### 3. Il Modello Teorico: La Macchina di Turing

Prima dell'architettura di Von Neumann, Alan Turing propose un modello di calcolo astratto noto come **Macchina di Turing**. Sebbene mai costruita fisicamente, è uno strumento fondamentale dell'informatica teorica per studiare le proprietà degli algoritmi, come la calcolabilità e la complessità.

La Macchina di Turing è composta da:

1.  **Nastro infinito:** Una memoria monodimensionale suddivisa in celle, ciascuna delle quali può contenere un simbolo di un alfabeto predefinito.
2.  **Testina di lettura/scrittura:** Un dispositivo che può leggere il simbolo nella cella corrente, scrivere un nuovo simbolo (cancellando il precedente) e spostarsi di una cella a sinistra o a destra.
3.  **Unità di controllo:** Un meccanismo a stati finiti che, in base allo stato corrente e al simbolo letto, determina l'operazione da eseguire e il prossimo stato da assumere.

Il concetto di nastro infinito è un'astrazione potente, ma si scontra con la realtà dei calcolatori moderni, che operano in **[[Fondamenti di Informatica/02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria#Aritmetica a Precisione Finita e Overflow|aritmetica a precisione finita]]** e sono soggetti a limiti di memoria e a fenomeni come l'**[[Fondamenti di Informatica/02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria#Condizione di Overflow|overflow]]**.

### 4. Calcolabilità e Trattabilità

Lo studio dei problemi si concentra su due proprietà cruciali:

*   **Calcolabilità (o Decidibilità):** Riguarda l'esistenza di un algoritmo per risolvere un problema. Un problema è detto **risolvibile** (o decidibile) se esiste una Macchina di Turing in grado di risolverlo terminando in un tempo finito. Questa proprietà è indipendente dall'esecutore specifico.
*   **Trattabilità:** Riguarda l'eseguibilità pratica di un algoritmo. Come sottolineato in ingegneria, non basta risolvere un problema, ma bisogna farlo in un **[[Geometria e Algebra/01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Motivazioni: Dai Sistemi Lineari all'Efficienza Computazionale|tempo utile]]**. Un problema è **trattabile** se esiste un algoritmo che lo risolve impiegando una quantità di risorse (tempo e memoria) "accettabile".

## Analisi della Complessità degli Algoritmi

### 5. Complessità Computazionale

La **complessità computazionale** è la disciplina che studia il costo di esecuzione di un algoritmo, analizzando come le risorse richieste varino al crescere della dimensione del problema (indicata con $N$).

Si distinguono due tipi principali di complessità:

*   **Complessità Spaziale:** Misura la quantità di memoria richiesta. In un calcolatore reale, questa memoria corrisponde alla [[Fondamenti di Informatica/07 - Architettura del Calcolatore, Bus, Clock e Memoria#6. La Gerarchia di Memoria e la Cache|gerarchia di memoria]] (registri, cache, RAM).
*   **Complessità Temporale:** Misura il tempo di esecuzione, strettamente legato alla frequenza del **[[Fondamenti di Informatica/07 - Architettura del Calcolatore, Bus, Clock e Memoria#4. Il Clock di Sistema|clock di sistema]]** (misurata in Hz) e al numero di cicli richiesti per ogni istruzione.

### 6. Complessità Asintotica

Il tempo di esecuzione di un algoritmo è una funzione della dimensione dell'input, $f(N)$. L'analisi della **complessità asintotica** studia il comportamento di $f(N)$ per valori di $N$ sufficientemente grandi (al limite, per $N \to \infty$), trascurando costanti e termini di ordine inferiore.

Per analizzare un algoritmo, si considerano tipicamente tre casi:

*   **Caso Migliore:** La configurazione di input che richiede il minor tempo di esecuzione.
*   **Caso Peggiore:** La configurazione di input che richiede il maggior tempo di esecuzione. Fornisce una garanzia sulla performance massima.
*   **Caso Medio:** La performance attesa su input generici.

Alcune classi comuni di complessità temporale, che corrispondono a famiglie di funzioni matematiche, includono:

*   **Logaritmica:** $O(\log N)$
*   **Lineare:** $O(N)$ (associata alla [[Analisi I/05 - Coordinate Cartesiane e Analisi delle Funzioni Elementari#3.1 La Funzione Lineare: f(x) = mx + q|funzione lineare]])
*   **Polinomiale:** $O(N^k)$, ad esempio quadratica ($O(N^2)$) (associata alla [[Analisi I/07 - Funzioni Potenza, Radici e Polinomi di Secondo Grado#Analisi dei Polinomi di Secondo Grado|funzione polinomiale di secondo grado]]) o cubica ($O(N^3)$).
*   **Esponenziale:** $O(k^N)$ (associata alla [[Analisi I/09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali#La Funzione Esponenziale|funzione esponenziale]])

Un algoritmo con complessità polinomiale è generalmente considerato trattabile, mentre uno con complessità esponenziale diventa rapidamente intrattabile al crescere di $N$.

### 7. Esempi Pratici di Algoritmi

1.  **Ricerca del minimo in un insieme di N numeri:**
    *   **Algoritmo:** Si assume il primo elemento come minimo temporaneo. Si scorrono i restanti $N-1$ elementi, aggiornando il minimo se si incontra un valore più piccolo.
    *   **Complessità:** Vengono eseguiti $N-1$ confronti. La complessità asintotica è **lineare**, $O(N)$.

2.  **Ordinamento (Selection Sort):**
    *   **Algoritmo:** Per $i$ che va da 1 a $N-1$, si cerca il minimo nel sottoinsieme non ordinato e lo si scambia con l'elemento in posizione $i$.
    *   **Complessità:** L'algoritmo esegue la ricerca del minimo $N-1$ volte su sottoinsiemi di dimensione decrescente. Il numero totale di confronti è $\sum_{i=1}^{N-1} i \approx \frac{N^2}{2}$. La complessità asintotica è **quadratica**, $O(N^2)$.

3.  **Procedure sistematiche:** Altri esempi di algoritmi fondamentali includono:
    *   La **[[Fondamenti di Informatica/02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria#Conversione da Decimale a Binario|conversione da decimale a binario]]** tramite divisioni successive.
    *   L'**[[Geometria e Algebra/02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Il Metodo di Eliminazione di Gauss-Jordan|algoritmo di eliminazione di Gauss-Jordan]]** per la riduzione a scala di una matrice.

## Dai Linguaggi di Alto Livello all'Esecuzione

### 8. Linguaggi di Programmazione: Struttura e Livelli

Un linguaggio di programmazione è un linguaggio formale dotato di alfabeto, lessico, sintassi e semantica. Esiste una gerarchia di linguaggi basata sul loro livello di astrazione rispetto all'hardware:

*   **Linguaggio Macchina:** Il linguaggio nativo della **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#La Central Processing Unit (CPU)|CPU]]**, composto da sequenze binarie. Le istruzioni sono interpretate dalla **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Struttura della CPU|Control Unit (CU)]]** ed eseguite dalla **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#L'Unità Aritmetico-Logica (ALU)|ALU]]**. Un'istruzione tipica è composta da un **codice operativo** (opcode) e dagli **operandi**.
*   **Linguaggio Assembly:** Utilizza codici mnemonici (es. `ADD`, `MOV`) per rappresentare le istruzioni macchina.
*   **Linguaggi di Alto Livello (es. C, Python, Java):** Più vicini al linguaggio umano e indipendenti dall'hardware, richiedono una traduzione.

### 9. Il Processo di Traduzione: Compilazione e Interpretazione

Per eseguire un programma di alto livello, è necessario tradurlo in linguaggio macchina. I due approcci principali sono:

1.  **Compilazione:** Un **compilatore** traduce l'intero codice sorgente in un file eseguibile una sola volta (es. C, C++).
2.  **Interpretazione:** Un **interprete** traduce ed esegue il codice sorgente istruzione per istruzione a ogni avvio (es. Python).

### 10. Le Fasi della Compilazione in C

Il processo che trasforma un codice sorgente C in un programma eseguibile si articola in diverse fasi:

1.  **Scrittura del Codice:** Il programmatore scrive il codice sorgente (es. `programma.c`).
2.  **Compilazione:** Il **compilatore** (es. GCC) traduce il codice sorgente in un **file oggetto** (`programma.o`).
3.  **Linking:** Il **linker** collega il file oggetto con le librerie di sistema necessarie, producendo un **file eseguibile**.
4.  **Caricamento:** Il **loader**, una componente del sistema operativo, carica il file eseguibile dalla [[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Memoria Centrale e Memoria di Massa|memoria di massa]] alla [[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Memoria Centrale e Memoria di Massa|memoria centrale (RAM)]].
5.  **Esecuzione:** La CPU inizia ad eseguire il programma tramite il suo **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Il Ciclo del Processore|ciclo fetch-decode-execute]]**. L'**[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#I Registri Interni della CPU|Unità di Controllo (CU)]]** preleva (`fetch`) un'istruzione dalla RAM (il cui indirizzo è nel registro **Program Counter**), la memorizza nell'**Instruction Register (IR)**, la decodifica (`decode`) e infine la esegue (`execute`), coordinando l'ALU e gli altri componenti.