# Analisi della Prova Intercorso e Gestione Avanzata delle Stringhe in C

## 1. Revisione Critica della Prova Intercorso

In questa sezione si analizzano gli errori più frequenti emersi durante la prova, collegandoli ai concetti teorici fondamentali dell'architettura dei calcolatori e della rappresentazione dei dati.

### 1.1 Codifica e Rappresentazione: Il vantaggio del Complemento a Due

Una delle questioni teoriche riguardava l'efficienza della rappresentazione in **complemento a due** rispetto ad altre codifiche (come "Modulo e Segno").

- **Risposta Corretta:** Permette di semplificare l'hardware della CPU.
    
- **Approfondimento:**
    
    1. **Unicità dello Zero:** In "Modulo e Segno" esistono $+0$ (`000...0`) e $-0$ (`100...0`). Nel [[03 - Rappresentazione Binaria dei Numeri Interi Relativi|complemento a due]], lo zero ha una sola rappresentazione (`000...0`).
        
    2. **Efficienza dell'ALU:** L'Unità Aritmetico Logica non necessita di circuiti separati per addizione e sottrazione. La sottrazione $A - B$ viene eseguita come $A + (-B)$, dove $-B$ è il complemento a due di $B$. Questo riduce la complessità dei circuiti sommatori.
        
    3. **Range Asimmetrico:** Ricorda che con $N$ bit, l'intervallo rappresentabile è $[-2^{N-1}, +2^{N-1}-1]$.
        

### 1.2 Modello di Esecutore: Timing degli Interrupt

La gestione degli interrupt è cruciale per il multitasking e l'I/O. Il processore verifica la presenza di un segnale di interrupt in un momento specifico del [[06 - Architettura dei Calcolatori, il Modello di Von Neumann|Ciclo di Von Neumann]].

- **Risposta Corretta:** Al termine della fase di _Execute_ (Esecuzione) e prima del _Fetch_ (Prelievo) dell'istruzione successiva.
    
- **Spiegazione Tecnica:** Il ciclo _Fetch-Decode-Execute_ deve essere atomico per la singola istruzione per garantire la coerenza dei registri (come il Program Counter). Se un interrupt viene rilevato:
    
    1. Il processore sospende il flusso normale.
        
    2. Salva il contesto corrente (registri, flag).
        
    3. Salta alla _Interrupt Service Routine_ (ISR).
        

### 1.3 Array in C: Vincoli e Memoria

Gli array in C sono strutture dati statiche e omogenee. È fondamentale distinguere tra la loro definizione e il loro utilizzo.

- **Errore Comune:** Credere che la dimensione possa essere ridefinita a runtime.
    
- **Realtà Implementativa:** Un array dichiarato come `int v[10]` alloca uno spazio contiguo di memoria pari a $10 \times \text{sizeof(int)}$ byte nello _Stack_ (o nel segmento dati, se globale). Questa allocazione è fissa.
    
- **Calcolo degli Indirizzi:** L'accesso a `v[i]` non è altro che un'operazione sui puntatori:
    
    $$\text{Indirizzo}(v[i]) = \text{IndirizzoBase} + (i \times \text{dimensione\_elemento})$$
    
    Questo spiega perché il C non controlla i limiti (bounds checking): calcolare l'indirizzo di `v[-1]` è matematicamente possibile, ma accede a memoria non riservata all'array (Buffer Overflow/Underrun), portando a comportamenti indefiniti descritti in [[16 - Dichiarazione, Manipolazione e Funzioni degli Array]].
    

### 1.4 Analisi Algoritmica: Errori Logici

1. **Shift Errato:** Sovrascrivere `$v[i+1] = v[i]$` all'interno di un ciclo crescente propaga il valore di `$v[i]$` su tutte le posizioni successive ("effetto valanga"), distruggendo i dati originali. Per shiftare elementi, bisogna solitamente iterare in senso inverso o usare una variabile temporanea.
    
2. **Effetti Collaterali nel `printf`:** L'istruzione `printf("%d", i++)` esegue un **post-incremento**.
    
    - _Prima_ stampa il valore corrente di `$i$`.
        
    - _Poi_ incrementa `$i$`. Questo modifica il valore di `$i$` per le istruzioni successive nel blocco (come un eventuale controllo `if` o calcolo matematico), spesso causando loop infiniti o logica errata.
        

## 2. Manipolazione Avanzata di Stringhe (`string.h`)

In C, le stringhe non sono un tipo primitivo, ma array di `char` terminati dal carattere sentinella `\0` (ASCII 0). Per approfondire la relazione tra puntatori e stringhe, vedi [[17 - Puntatori, Array, Stringhe e Gestione della Memoria]].

### 2.1 Funzioni della Libreria Standard

Le operazioni sulle stringhe richiedono la libreria `<string.h>`.

| Funzione               | Descrizione e Note                                                                                                                                      |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`strlen(s)`**        | Calcola la lunghezza escludendo `\0`. Complessità $O(N)$.                                                                                               |
| **`strcpy(dst, src)`** | Copia $src$ in `$dst$`. ⚠️ **Pericolo:** Se `$dst$` è più piccolo di `$src$`, si verifica un buffer overflow.                                           |
| **`strcat(dst, src)`** | Concatena `$src$` alla fine di `$dst$`. Cerca il `\0` di `$dst` e inizia a copiare lì.                                                                  |
| **`strcmp(s1, s2)`**   | Confronto lessicografico (basato su ASCII).<br><br>- `0`: uguali.<br><br>- `<0`: `$s1$` viene prima di `$s2$`.<br><br>- `>0`: `$s1$` viene dopo `$s2$`. |

### 2.2 Ricerca e Sottostringhe

- **`strchr(s, c)`:** Restituisce un **puntatore** alla prima occorrenza del carattere `$c$` in `$s`, oppure `NULL`.
    
- **`strstr(s1, s2)`:** Restituisce un puntatore alla prima occorrenza della _sottostringa_ `$s2$` in `$s1`.
    

## 3. Input/Output Robusto: `scanf` vs `fgets`

La gestione dell'input testuale è una fonte comune di bug. Vedi [[10 - Struttura dei Programmi in C, Input e Output e Variabili]] per le basi dell'I/O.

### 3.1 Il problema di `scanf`

La funzione `scanf("%s", str)` legge fino al primo _whitespace_ (spazio, tabulazione, invio).

- _Input:_ "Mario Rossi"
    
- _Memorizzato:_ "Mario"
    
- _Buffer:_ " Rossi" rimane in attesa per la prossima lettura.
    

### 3.2 La soluzione `fgets`

La funzione `fgets` è progettata per leggere righe intere, rispettando i limiti del buffer per evitare overflow.

```
char buffer[100];
fgets(buffer, 100, stdin);
```

**Gestione del Newline:** `fgets` include il carattere `\n` nella stringa se c'è spazio. Questo è spesso indesiderato per i confronti (es. `strcmp`). _Tecnica di rimozione:_

```
// Cerca il \n e lo sostituisce con il terminatore \0
buffer[strcspn(buffer, "\n")] = '\0';
```

### 3.3 Pulizia del Buffer (Input Flushing)

Quando si mescolano `scanf` (lettura formattata) e `fgets` (lettura di riga), il carattere `\n` lasciato dalla `scanf` viene letto erroneamente dalla `fgets` successiva come una riga vuota.

**Soluzione Portabile:** Poiché `fflush(stdin)` non è standard ANSI C per gli stream di input (funziona solo su alcuni compilatori come MSVC, ma non su GCC/Linux), si deve usare un ciclo di consumazione:

```
void flush_input_buffer() {
    int c;
    // Legge caratteri finché non trova un newline o la fine del file
    while ((c = getchar()) != '\n' && c != EOF);
}
```

Questa funzione va chiamata _dopo_ una `scanf` e _prima_ di una `fgets`.

## 4. Algoritmo di Filtraggio (Esercizio Pratico)

Obiettivo: Separare vocali e consonanti da una stringa in input.

**Logica e Gestione della Memoria:** L'algoritmo richiede un singolo passaggio (complessità $O(N)$) sulla stringa originale.

```
#include <stdio.h>
#include <ctype.h> // Utile per tolower() e isalpha()
#include <string.h>

void separa_caratteri(const char *src, char *vocali, char *consonanti) {
    int j = 0; // Indice per array vocali
    int k = 0; // Indice per array consonanti
    
    for (int i = 0; src[i] != '\0'; i++) {
        char c = src[i];
        
        // Controllo se è una lettera dell'alfabeto
        if (isalpha(c)) {
            char lower_c = tolower(c); // Normalizzo per il controllo
            
            if (lower_c == 'a' || lower_c == 'e' || lower_c == 'i' || 
                lower_c == 'o' || lower_c == 'u') {
                vocali[j++] = c;
            } else {
                consonanti[k++] = c;
            }
        }
    }
    
    // FONDAMENTALE: Chiudere le stringhe manualmente
    vocali[j] = '\0';
    consonanti[k] = '\0';
}
```

**Note Importanti:**

1. **Terminatore:** Dimenticare `vocali[j] = '\0'` lascerebbe la stringa "aperta", causando la stampa di caratteri spazzatura (_garbage_) presenti in memoria dopo l'ultimo carattere valido.
    
2. **Indici Indipendenti:** L'uso di `$i$`, `$j$` e `$k$` permette di riempire i tre array a velocità diverse senza lasciare "buchi".