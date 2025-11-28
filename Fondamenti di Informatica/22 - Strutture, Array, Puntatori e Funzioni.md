# Strutture Dati in C: Array, Puntatori e Applicazioni Avanzate

Questo documento approfondisce l'utilizzo combinato di **[[Fondamenti di Informatica/21 - Sintassi, Memoria e Applicazioni delle Strutture|strutture (struct)]]**, **[[Fondamenti di Informatica/16 - Dichiarazione, Manipolazione e Funzioni degli Array|array]]** e **[[Fondamenti di Informatica/17 - Puntatori, Array, Stringhe e Gestione della Memoria|puntatori]]** per la gestione di dati complessi.

## Array di Strutture

Analogamente ai tipi di dato primitivi (interi, reali, booleani), è possibile definire array di tipi strutturati. Un array di strutture rappresenta un tipo strutturato **omogeneo** (l'array) in cui ogni locazione di memoria contiene una singola istanza di un tipo **eterogeneo** (la struttura).

### Definizione e Allocazione
La sintassi per la definizione di un array di strutture, se non si utilizza `typedef`, è la seguente:
$$\texttt{struct nome\_struttura nome\_array[dimensione\_fisica];}$$

Se invece si utilizza `typedef` (consigliato per pulizia del codice, vedi [[Fondamenti di Informatica/11 - Operatori, Costanti e Conversioni di Tipo in C#Definizione di Tipi Personalizzati con typedef|typedef]]):
$$\texttt{TipoStruttura nome\_array[dimensione\_fisica];}$$

L'allocazione in memoria avviene in **blocchi contigui**. 
> [!important] Gestione della Dimensione
> Spesso il numero di elementi non è noto a priori. Si adotta il pattern **Dimensione Fisica vs Riempimento** (vedi [[Fondamenti di Informatica/16 - Dichiarazione, Manipolazione e Funzioni degli Array#Gestione degli Array Dimensione vs. Riempimento|Gestione Array]]):
> 1. Si definisce una dimensione massima (es. `MAX_DIM`) per l'allocazione statica (*worst-case*).
> 2. Si utilizza una variabile intera `riempimento` (o `count`) per tenere traccia degli elementi effettivamente significativi.

### Allineamento e Padding in Memoria
La dimensione totale di una struttura in memoria non corrisponde sempre alla somma aritmetica delle dimensioni dei suoi campi (es. calcolata tramite `sizeof`). 

A causa dell'**[[Fondamenti di Informatica/07 - Architettura del Calcolatore, Bus, Clock e Memoria#3. Caratteristiche Fisiche dei Bus e Prestazioni|Architettura Hardware]]**, la CPU accede alla memoria per *word* (parole) di 32 o 64 bit. Per ottimizzare l'accesso, il compilatore inserisce byte riempitivi, detti **padding**, per allineare i dati al limite di parola (*word boundary*).

**Esempio:**
Consideriamo una struttura `impiegato`:
* `int id` (4 byte)
* `char nome[5]` (5 byte)
* `float stipendio` (4 byte)

La somma teorica è $4 + 5 + 4 = 13$ byte. Tuttavia, per garantire l'allineamento (spesso a multipli di 4 o 8 byte), il compilatore potrebbe aggiungere 3 byte di padding dopo l'array di caratteri.
L'operatore `sizeof(struct impiegato)` restituirà quindi la dimensione reale comprensiva del padding (es. 16 byte).

## Puntatori a Strutture

L'utilizzo dei puntatori si estende naturalmente alle strutture. Un puntatore a una `struct` contiene l'**indirizzo di memoria** in cui inizia il primo campo della struttura stessa (vedi [[Fondamenti di Informatica/17 - Puntatori, Array, Stringhe e Gestione della Memoria#Puntatori a Puntatori Doppia Indirezione|Puntatori e Indirizzi]]).

### Sintassi e Accesso ai Campi
Data una struttura `struct elemento` e un puntatore `struct elemento *ptr` inizializzato all'indirizzo di una variabile (`ptr = &variabile;`), esistono due modalità per accedere ai campi:

1.  **Dereferenziazione esplicita:** Si dereferenzia il puntatore e si accede al campo tramite l'operatore punto (`.`). È obbligatorio l'uso delle parentesi tonde a causa della [[Fondamenti di Informatica/11 - Operatori, Costanti e Conversioni di Tipo in C#Precedenza degli Operatori|precedenza degli operatori]] (il `.` ha priorità su `*`):
    $$\texttt{(*ptr).nome\_campo}$$
2.  **Operatore Freccia (**`->`**):** Una notazione sintattica ("zucchero sintattico") più compatta ed elegante che combina dereferenziazione e accesso:
    $$\texttt{ptr->nome\_campo}$$

### Aritmetica dei Puntatori su Strutture
L'[[Fondamenti di Informatica/17 - Puntatori, Array, Stringhe e Gestione della Memoria#Aritmetica dei Puntatori|aritmetica dei puntatori]] si applica anche ai puntatori a strutture. 
Incrementare un puntatore di un'unità ($ptr + 1$) sposta l'indirizzo di una quantità di byte pari a `sizeof(TipoStruttura)`. Questo permette di scorrere agevolmente un array di strutture utilizzando i puntatori invece degli indici.

## Passaggio di Strutture alle Funzioni

Passare strutture come parametri **per valore** comporta la copia dell'intera struttura (tutti i campi) nello [[Fondamenti di Informatica/14 - Programmazione Modulare, Funzioni, Procedure e Visibilità delle Variabili#Visibilità (Scope) e Ciclo di Vita delle Variabili|Stack]]. Per strutture di grandi dimensioni, ciò risulta inefficiente in termini di memoria e tempo.

### Passaggio per Riferimento e Qualificatore `const`
Per ottimizzare le prestazioni, si passa il **puntatore** alla struttura (simulando il passaggio per riferimento). 
Vedi approfondimento: [[Fondamenti di Informatica/15 - Funzioni, Passaggio Parametri e Librerie#Passaggio dei Parametri per Valore|Passaggio Parametri]].

Questo approccio:
1.  Evita la duplicazione dei dati (si copiano solo 4 o 8 byte di indirizzo).
2.  Permette alla funzione di modificare l'originale (parametro di input/output).

Se la struttura deve essere trattata come parametro di **solo input** (sola lettura), si utilizza il qualificatore `const`:
$$\texttt{void funzione(const struct nome\_struttura *ptr)}$$
Ciò garantisce che i campi puntati non vengano modificati, proteggendo l'integrità dei dati pur mantenendo l'efficienza.

### Valori di Ritorno
Le funzioni possono restituire strutture (per valore) o puntatori a strutture. Restituire un puntatore è comune quando si lavora con l'allocazione dinamica o per restituire un riferimento a un elemento esistente in un array.

## Caso di Studio: Gestione Carriera Studente

È stato analizzato un programma per la gestione di un array di strutture `Studente`, contenente campi eterogenei (stringhe per nome/cognome, interi per età, booleani per status lavoratore, reali per media voti).
Vedi esempio correlato in: [[Fondamenti di Informatica/21 - Sintassi, Memoria e Applicazioni delle Strutture#8. Caso di Studio Gestione Studenti|Gestione Studenti]].

### Funzionalità Implementate
1.  **Inserimento e Stringhe:** * Utilizzo di `fgets` per la lettura di stringhe (che accetta anche spazi, a differenza di `scanf %s`).
    * Gestione del carattere *newline* residuo tramite `strcspn` (o sovrascrittura manuale con `\0`). 
    * Utilizzo di `strcpy` per l'assegnazione dei campi stringa (le stringhe non si assegnano con `=`). 
    * Vedi: [[Fondamenti di Informatica/20 - Gestione stringe e libreria string.h|Libreria string.h]].
2.  **Ricerca e Calcolo:** Implementazione di algoritmi per scorrere l'array e filtrare i dati (es. calcolo media voti solo per studenti non lavoratori). Si sfrutta il ciclo `for` fino al valore di `riempimento`.
3.  **Output:** Stampa condizionale basata su criteri specifici (es. stampa dettagli studenti con età $< 25$).

Il codice dimostra l'interazione tra array di strutture, aritmetica dei puntatori e gestione efficiente tramite passaggio di parametri per riferimento costante (`const Studente *s`).