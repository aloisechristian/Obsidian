## Introduzione

La lezione verte sull'introduzione, la definizione e l'utilizzo delle **strutture** (`struct`) nel linguaggio C, analizzando la sintassi, la gestione della memoria e le differenze sostanziali rispetto agli array.

> [!INFO] Prerequisiti Prima di affrontare le strutture, è utile aver chiaro il concetto di [[16 - Dichiarazione, Manipolazione e Funzioni degli Array|array]] e la gestione delle [[20 - Gestione stringe e libreria string.h|stringhe in C]].

## 1. Le Strutture in C: Dati Eterogenei

### 1.1 Definizione e Differenze con gli Array

Le strutture (keyword `struct`) sono collezioni di elementi a cui viene assegnato un nome unico. La differenza fondamentale risiede nella tipologia di dati contenuti:

- **Array**: sono strutture dati **omogenee**, ovvero contengono elementi tutti dello stesso tipo (es. solo interi).
    
- **Strutture**: sono strutture dati **eterogenee**, ovvero possono aggregare variabili di tipi differenti (interi, caratteri, array, float, ecc.) sotto un'unica entità logica.
    

### 1.2 Sintassi di Dichiarazione

La dichiarazione di un tipo struttura fissa il nome e l'elenco dei campi (o membri). La sintassi termina obbligatoriamente con un punto e virgola.

$$\text{struct NomeStruttura } \{ \\ \quad \text{tipo}_1 \text{ nome}_1; \\ \quad \text{tipo}_2 \text{ nome}_2; \\ \quad \dots \\ \};$$

È possibile definire variabili in due momenti distinti:

1. **Contestualmente alla dichiarazione**: inserendo i nomi delle variabili tra la chiusura della graffa e il punto e virgola.
    
2. **Successivamente**: utilizzando il nome della struttura come un nuovo tipo di dato.
    

## 2. Definizione e Inizializzazione delle Variabili

Per definire un'istanza di una struttura separatamente dalla sua dichiarazione: `struct NomeStruttura miaVariabile;`

L'inizializzazione può avvenire in modi diversi:

1. **Stile Array (Posizionale):** Si elencano i valori tra parentesi graffe, rispettando l'ordine di dichiarazione dei campi.
    
    ```c
    struct Data d = {10, "Ottobre", 2023};
    ```
    
2. **Assegnazione Puntuale:** Si inizializzano i campi singolarmente dopo la definizione.
    

## 3. Accesso ai Campi: La _Dot Notation_

L'accesso ai membri di una struttura avviene tramite l'operatore punto (`.`), noto come _dot notation_. Sintassi: `nomeVariabile.nomeCampo`

- **Tipi primitivi**: Assegnazione diretta (es. `s.eta = 20;`).
    
- **Stringhe (Array di char)**: Non supportano l'assegnazione diretta (`=`). È necessario usare la funzione `strcpy` dalla libreria `string.h`.
    
    > [!WARNING] Attenzione alle Stringhe
    > 
    > ```
    > // Errato: mioContatto.nome = "Vittorio";
    > strcpy(mioContatto.nome, "Vittorio"); // Corretto
    > ```
    > 
    > Vedi [[20 - Gestione stringe e libreria string.h#2.1 Funzioni della Libreria Standard|funzioni string.h]] per dettagli.
    

### 3.1 Indirizzo della Struttura

L'operatore `&` applicato a una variabile di tipo struttura restituisce l'indirizzo del suo **primo campo**. `&s1` è numericamente equivalente a `&(s1.campo1)`, anche se semanticamente riferiscono a tipi diversi.

## 4. Gestione della Memoria: Allineamento e _Padding_

La dimensione totale di una struttura (`sizeof(struct ...)` ) è spesso maggiore della somma delle dimensioni dei singoli campi. Questo fenomeno è dovuto al **Data Alignment** (allineamento dei dati).

### 4.1 Il concetto di Word e Padding

La CPU accede alla memoria in unità chiamate _word_ (tipicamente 4 byte su 32-bit, 8 byte su 64-bit). Per ottimizzare l'accesso, il compilatore inserisce byte vuoti (**padding**) per allineare i campi ai multipli della word.

**Esempio di calcolo della dimensione:** Consideriamo la seguente struttura su una macchina a 32-bit (word 4 byte):

```c
struct employee {
    int id;         // 4 byte
    char name[5];   // 5 byte
    float salary;   // 4 byte
};
```

Calcolo teorico: $4 + 5 + 4 = 13$ byte. Calcolo reale (con padding):

1. `id` (4 byte) $\rightarrow$ OK.
    
2. `name` (5 byte) $\rightarrow$ Occupa 1 word intera (4 byte) + 1 byte della successiva.
    
3. Per allineare il successivo `float` (che richiede 4 byte allineati), il compilatore aggiunge **3 byte di padding** dopo `name`.
    
4. `salary` (4 byte) $\rightarrow$ inizia all'indirizzo allineato.
    

$$\text{Size Totale} = 4 (\text{id}) + 5 (\text{name}) + \mathbf{3 (\text{padding})} + 4 (\text{salary}) = 16 \text{ byte}$$

> [!TIP] Strumenti di Analisi Su sistemi Linux, è possibile usare il tool `pahole` per visualizzare esattamente dove il compilatore inserisce i "buchi" di padding.

Vedi [[17 - Puntatori, Array, Stringhe e Gestione della Memoria#Dimensione e Architettura]] per approfondimenti sull'architettura.

## 5. L'uso di `typedef`

`typedef` permette di creare un alias per il tipo struttura, evitando di ripetere la keyword `struct` ogni volta.

**Definizione combinata:**

```c
typedef struct {
    int giorno;
    char mese[15];
    int anno;
} Data; // 'Data' è ora il nome del tipo
```

Utilizzo: `Data data_esame;` (invece di `struct NomeStruttura data_esame;`).

## 6. Operazioni e Vincoli

- **Assegnazione (`=`)**: È permessa tra strutture dello stesso tipo (`s1 = s2`).
    
    - Effettua una **copia bit a bit** (shallow copy).
        
    - ⚠️ **Attenzione**: Se la struttura contiene puntatori, viene copiato solo l'indirizzo, non l'area puntata (aliasing involontario).
        
- **Confronto (`==`, `!=`)**: **NON** è supportato nativamente sugli oggetti struct interi. Bisogna implementare una funzione che confronti i campi uno per uno.
    
- **Input/Output**: Non si può fare `scanf` o `printf` dell'intera struttura. Bisogna operare sui singoli campi.
    

## 7. Array di Strutture

È possibile creare array i cui elementi sono strutture. Questo è fondamentale per creare database in memoria (es. una rubrica, un registro classe).

**Dichiarazione:**

```c
struct persona info_utenti[100];
```

In questo caso, `info_utenti` è un array omogeneo dove ogni cella (es. `info_utenti[0]`) è una struttura di tipo `persona`.

**Accesso combinato:**

$$\text{vettore}[i].\text{campo}$$

Esempio: `info_utenti[3].eta = 25;`

> [!NOTE] Gestione Dinamica: Come per gli array di primitivi, se il numero di elementi non è noto a priori, si usa una dimensione massima e una variabile **riempimento** per tenere traccia degli elementi effettivi. Vedi [[16 - Dichiarazione, Manipolazione e Funzioni degli Array#La Variabile di Riempimento]].

## 8. Caso di Studio: Gestione Studenti

Esempio di programma per gestire un elenco di studenti, verificando omonimie e confrontando le medie.

```c
#include <stdio.h>
#include <string.h>
#include <stdbool.h>

#define NVOTI 3

typedef struct {
    char nome[50];
    char cognome[50];
    int eta;
    int voti[NVOTI]; 
} Studente;

// Funzione per verificare l'omonimia
bool sono_omonimi(Studente s1, Studente s2) {
    // strcmp restituisce 0 se le stringhe sono uguali
    if (strcmp(s1.nome, s2.nome) == 0 && strcmp(s1.cognome, s2.cognome) == 0) {
        return true;
    }
    return false;
}

// Funzione per confrontare le medie
// Output: -1 se s1 > s2, 1 se s2 > s1, 0 se uguali
int confronta_media(Studente s1, Studente s2) {
    float media1 = 0, media2 = 0;
    for(int i=0; i<NVOTI; i++) {
        media1 += s1.voti[i];
        media2 += s2.voti[i];
    }
    // Non serve dividere per NVOTI per il confronto, ma per correttezza formale:
    media1 /= NVOTI;
    media2 /= NVOTI;

    if (media1 > media2) return -1;
    if (media2 > media1) return 1;
    return 0;
}
```