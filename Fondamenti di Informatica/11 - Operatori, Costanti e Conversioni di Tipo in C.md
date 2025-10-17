## Riepilogo degli Operatori e Gestione della Precisione

La lezione riprende il concetto di operatori aritmetici in C (`+`, `-`, `*`, `/`). Un aspetto fondamentale riguarda la gestione della precisione nelle operazioni tra tipi di dati numerici diversi. La regola generale è che il risultato di un'operazione aritmetica assume il tipo con la precisione maggiore tra gli operandi. Di seguito alcuni esempi:

*   `float` + `float` $\implies$ `float`
*   `float` + `int` $\implies$ `float`
*   `double` + `float` $\implies$ `double`
*   `long int` + `short int` $\implies$ `long int`

Per operazioni matematiche più complesse come l'elevamento a potenza, l'arrotondamento per eccesso (`ceiling`) o per difetto (`floor`), il linguaggio C mette a disposizione la libreria standard `math.h`, che può essere inclusa nel programma con la direttiva:

```c
#include <math.h>
```

### Caso di Studio: Divisione tra Interi

Una questione rilevante è il comportamento della divisione tra due interi quando il risultato viene assegnato a una variabile di tipo reale (`float` o `double`). Si consideri il seguente scenario:

```c
int a = 7;
int b = 2;
float c = a / b;
```

In questo caso, il compilatore C esegue prima la divisione tra `a` e `b`. Poiché entrambi sono interi, viene eseguita una **divisione intera**, il cui risultato è `3`. Successivamente, questo valore intero viene convertito implicitamente in `float` e assegnato a `c`. Pertanto, `c` conterrà il valore `3.0`, non `3.5`. Per ottenere il risultato corretto della divisione reale, è necessario effettuare una conversione esplicita di tipo (casting) su almeno uno degli operandi, come verrà discusso in seguito.

## Rappresentazione dei Letterali Numerici

Il C consente di specificare valori numerici (letterali) utilizzando diverse basi e notazioni, identificate da prefissi specifici:

*   **Base Decimale**: Nessun prefisso richiesto (es. `123`).
*   **Notazione Esponenziale**: Utilizzata per numeri reali molto grandi o molto piccoli. La sintassi prevede una parte decimale, il carattere `e` o `E`, e un esponente (es. `3.14e-5`).
*   **Base Ottale (base 8)**: Prefisso `0`. Le cifre valide vanno da `0` a `7` (es. `077`).
*   **Base Esadecimale (base 16)**: Prefisso `0x` o `0X`. Le cifre valide sono `0-9` e `A-F` (maiuscole o minuscole, es. `0xFF`).
*   **Base Binaria (base 2)**: Prefisso `0b` o `0B`. Le cifre valide sono `0` e `1` (es. `0b1011`).

È importante notare che, a differenza degli identificatori di variabili (che sono *case-sensitive*), i caratteri letterali per le basi non decimali (`e`, `x`, `b`, `a-f`) possono essere scritti sia in maiuscolo che in minuscolo.

## Panoramica degli Operatori in C

### Operatori Logici (Booleani)

Gli operatori logici implementano le operazioni dell'algebra di Boole e sono fondamentali per costruire espressioni condizionali.

*   **AND Logico**: `&&`
*   **OR Logico**: `||`
*   **NOT Logico**: `!`

Questi operatori possono essere applicati a qualsiasi tipo di dato, ma il loro uso è semanticamente corretto con i tipi booleani. In C, il tipo `bool` e le costanti `true` e `false` sono state standardizzate a partire dalla versione C99 e richiedono l'inclusione della libreria `stdbool.h`. La convenzione generale è:

*   Il valore `0` è interpretato come `false`.
*   Qualsiasi valore diverso da `0` è interpretato come `true`.

### Operatori Bitwise (Bit a Bit)

Gli operatori bitwise agiscono direttamente sulla rappresentazione binaria dei dati, manipolando i singoli bit.

*   **AND Bitwise**: `&`
*   **OR Bitwise**: `|`
*   **XOR (OR Esclusivo) Bitwise**: `^`. Lo XOR restituisce `1` solo se i due bit di input sono diversi.
*   **Complemento a uno (NOT) Bitwise**: `~`. Inverte ogni bit dell'operando.
*   **Shift a Sinistra**: `<<`. Sposta i bit verso sinistra, inserendo zeri a destra. Uno shift di `n` posizioni equivale a una moltiplicazione per $2^n$.
*   **Shift a Destra**: `>>`. Sposta i bit verso destra. Per i numeri senza segno, inserisce zeri a sinistra. Uno shift di `n` posizioni equivale a una divisione intera per $2^n$.

### Regole di Precedenza per Operatori Logici e Bitwise

L'ordine di valutazione delle espressioni complesse è determinato da regole di precedenza. Per forzare un ordine diverso, si utilizzano le parentesi `()`.

*   **Precedenza Operatori Logici**: `!` (massima), `&&`, `||` (minima).
*   **Precedenza Operatori Bitwise**: `~` (massima), `&`, `^`, `|` (minima).

### Operatori Relazionali (di Confronto)

Questi operatori mettono a confronto due valori e restituiscono un risultato booleano (`true` o `false`, rappresentati da `1` o `0`).

*   Uguaglianza: `==`
*   Diversità: `!=`
*   Maggiore di: `>`
*   Minore di: `<`
*   Maggiore o uguale: `>=`
*   Minore o uguale: `<=`

**Attenzione**: È cruciale non confondere l'operatore di confronto `==` con l'operatore di assegnazione `=`. Un errore comune è scrivere `if (a = b)` invece di `if (a == b)`, che causa un comportamento errato (assegna `b` ad `a` invece di confrontarli).

### Operatori di Incremento e Decremento

Gli operatori `++` e `--` incrementano e decrementano, rispettivamente, il valore di una variabile di una unità. Esistono in due forme:

*   **Pre-incremento/decremento** (`++var`, `--var`): La variabile viene prima modificata, e poi il suo nuovo valore viene utilizzato nell'espressione circostante.
*   **Post-incremento/decremento** (`var++`, `var--`): Il valore corrente della variabile viene prima utilizzato nell'espressione, e solo dopo la variabile viene modificata.

Esempio:
`int i = 5;`
`res = i++; // res vale 5, i diventa 6`
`res = ++i; // i diventa 7, res vale 7`

### Operatori Composti

Per semplificare la scrittura di espressioni in cui una variabile viene modificata usando il suo stesso valore (es. `x = x + 5`), il C fornisce operatori composti:

*   `x += 5;` (equivalente a `x = x + 5`)
*   `b *= 4;` (equivalente a `b = b * 4`)

Questi operatori esistono per tutte le principali operazioni aritmetiche e bitwise (`+=`, `-=`, `*=`, `/=`, `%=`, `&=`, `|=`, `^=`, `<<=`, `>>=`).

### Operatore Condizionale (Ternario)

L'operatore `? :` permette di scrivere un'espressione condizionale in modo compatto. La sintassi è:

`condizione ? espressione_se_vera : espressione_se_falsa`

Se `condizione` è vera, l'intera espressione assume il valore di `espressione_se_vera`, altrimenti assume il valore di `espressione_se_falsa`.

Esempio:
`max = (a > b) ? a : b; // Assegna ad 'max' il valore maggiore tra 'a' e 'b'`

## Le Costanti in C

Una costante è un valore fisso che non può essere modificato durante l'esecuzione del programma. Possono essere di tipo numerico (intero, reale) o alfanumerico (carattere, stringa).

### Costanti Carattere e Stringa

*   **Costante Carattere**: Un singolo carattere racchiuso tra apici singoli (es. `'A'`).
*   **Costante Stringa**: Una sequenza di caratteri (anche vuota) racchiusa tra doppi apici (es. `"Hello, World!"`, `""`).

### Sequenze di Escape

Per rappresentare caratteri speciali all'interno di stringhe e costanti carattere, si usa il carattere di escape `\` (backslash).

*   `\n`: Newline (a capo).
*   `\t`: Tabulazione orizzontale.
*   `\'`: Apice singolo.
*   `\"`: Doppio apice.
*   `\\`: Backslash.

È anche possibile rappresentare caratteri tramite il loro codice ottale o esadecimale (es. `\101` o `\x41` per il carattere 'A').

### Metodi per Definire le Costanti

Esistono due modi principali per definire costanti simboliche:

1.  **Direttiva del Preprocessore `#define`**:
    `#define NOME_COSTANTE valore`
    Il preprocessore sostituisce testualmente ogni occorrenza di `NOME_COSTANTE` con `valore` prima della compilazione. Questo metodo non alloca memoria e la costante non è tipizzata.

2.  **Qualificatore `const`**:
    `const tipo nome_costante = valore;`
    Questo metodo dichiara una variabile a tutti gli effetti, il cui valore però non può essere modificato dopo l'inizializzazione. La costante è tipizzata e viene allocata in memoria. Il compilatore segnalerà un errore se si tenta di modificarla.

## Conversione di Tipo (Type Casting)

Il *type casting* è un'operazione che consente di convertire esplicitamente il valore di una variabile o di un'espressione da un tipo di dato a un altro (compatibile). La sintassi preferita è:

`(nuovo_tipo) espressione`

Ad esempio, per risolvere il problema della divisione intera visto in precedenza:

```c
int a = 7, b = 2;
float c = (float)a / b; // c conterrà 3.5
```

In questo caso, `a` viene temporaneamente trattato come un `float` per l'operazione di divisione. Di conseguenza, anche `b` viene promosso a `float` e viene eseguita una divisione reale. La variabile `a` originale rimane di tipo `int`.