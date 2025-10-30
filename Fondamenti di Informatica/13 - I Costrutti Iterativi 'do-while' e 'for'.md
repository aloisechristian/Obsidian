## Riepilogo delle Strutture di Controllo Iterative

Questa lezione prosegue l'analisi delle strutture di controllo in C, focalizzandosi sui costrutti iterativi. Dopo un breve riepilogo delle strutture di selezione (`if-then-else`, `switch-case`) e del ciclo `while` (trattati in [[12 - Strutture di Controllo, Sequenza, Selezione, Iterazione.md]]), vengono introdotti e analizzati in dettaglio i cicli `do-while` e `for`.

### Il Costrutto `while` (Riepilogo)

Il ciclo `while` è un costrutto iterativo con **controllo della condizione in testa**. Ciò significa che la condizione viene valutata _prima_ di eseguire il corpo del ciclo. Se la condizione risulta falsa fin dalla prima valutazione, il corpo del ciclo non viene eseguito neppure una volta. Non vi è, pertanto, un numero minimo di iterazioni garantite.

```c
while (condizione) {
    // Corpo del ciclo
}
```

## Il Costrutto `do-while`

Il ciclo `do-while` rappresenta un'alternativa al `while`, caratterizzata da un **controllo della condizione in coda**.

La sua sintassi è la seguente:

```c
do {
    // Corpo del ciclo
} while (condizione);
```

La differenza fondamentale risiede nel flusso di esecuzione:

1. Il corpo del ciclo viene eseguito.
    
2. Successivamente, viene valutata la `condizione`.
    
3. Se la condizione è vera, il ciclo riprende dal punto 1. Se è falsa, l'esecuzione prosegue con l'istruzione successiva al blocco `do-while`.
    

Questa struttura garantisce che il corpo del ciclo venga eseguito **almeno una volta**, indipendentemente dal valore iniziale della condizione. È particolarmente utile in scenari dove è necessario compiere un'azione (es. leggere un input) prima di poter verificare se tale azione debba essere ripetuta.

### Esercizio 1: Validazione di Input Numerico

**Problema**: Scrivere un programma che richieda all'utente di inserire un numero intero finché il valore non rientra nell'intervallo `[1, 12]`.

Questo scenario è ideale per un ciclo `do-while`, poiché l'input deve essere acquisito almeno una volta per poter essere validato.

#### Analisi della Condizione Logica

Il ciclo deve continuare a iterare finché il valore inserito **non rientra** nell'intervallo. Definiamo la condizione di _appartenenza_ all'intervallo come:

$$ (numero >= 1) \text{ AND } (numero <= 12) $$

In C, questo si traduce in: numero >= 1 && numero <= 12

La condizione di _permanenza_ nel ciclo è la negazione logica della condizione di appartenenza:

$$ \neg ((numero >= 1) \text{ AND } (numero <= 12)) $$

Applicando il **teorema di De Morgan** (vedi [[05 - Codifica Digitale di Testo, Media e Logica Booleana.md#Logica Booleana|Logica Booleana]]), secondo cui `$\neg(A \land B) \iff (\neg A \lor \neg B)$`, possiamo trasformare l'espressione:

$$ \neg(numero >= 1) \text{ OR } \neg(numero <= 12) $$

Che si semplifica in:

$$ (numero < 1) \text{ OR } (numero > 12) $$

Entrambe le formulazioni sono logicamente equivalenti e possono essere utilizzate nella clausola `while`.

#### Implementazione in C

```c
#include <stdio.h>

int main() {
    int numero;

    do {
        printf("Inserisci un intero nell'intervallo [1-12]: ");
        scanf("%d", &numero);
    } while (numero < 1 || numero > 12);
    // In alternativa: while (!(numero >= 1 && numero <= 12));

    printf("Valore inserito valido: %d\n", numero);

    return 0;
}
```

### Esercizio 2: Validazione di Input Carattere

**Problema**: Scrivere un programma che richieda l'inserimento di un carattere finché questo non è uno dei seguenti: `+`, `-`, `*`, `/`, `%`.

Anche in questo caso, il `do-while` è appropriato. Il programma deve leggere un carattere e poi controllare se corrisponde a uno di quelli consentiti.

#### Analisi della Condizione Logica

Il ciclo deve continuare se il carattere inserito **non è** `+` **E non è** `-` **E non è** `*`, e così via per tutti i caratteri validi. La condizione di permanenza nel ciclo è quindi una congiunzione (`AND`) di confronti di disuguaglianza.

$$ (carattere \neq +) \land (carattere \neq -) \land (carattere \neq *) \land (carattere \neq /) \land (carattere \neq \%) $$

#### Implementazione in C

È importante notare che durante la lettura di caratteri con `scanf`, il carattere di newline (`\n`), inserito quando l'utente preme Invio, rimane nel buffer di input e può essere letto dalla successiva chiamata a `scanf`, causando un comportamento inatteso. Per ovviare a questo, si antepone uno spazio allo specificatore di formato (`" %c"`), che istruisce `scanf` a ignorare eventuali caratteri di spaziatura (incluso `\n`) prima di leggere il carattere effettivo.

```c
#include <stdio.h>

int main() {
    char carattere;

    do {
        printf("Inserisci un operatore (+, -, *, /, %%): ");
        scanf(" %c", &carattere); // Lo spazio è cruciale
    } while (carattere != '+' && carattere != '-' && carattere != '*' && carattere != '/' && carattere != '%');

    printf("Operatore inserito valido: %c\n", carattere);

    return 0;
}
```

## Il Costrutto `for`

Il ciclo `for` è un costrutto iterativo concepito primariamente per situazioni in cui il numero di iterazioni è noto a priori. Viene definito un **ciclo a conteggio**.

La sua sintassi è compatta e include tre parti essenziali, separate da punto e virgola, all'interno delle parentesi:

1. **Inizializzazione**: Eseguita una sola volta prima dell'inizio del ciclo. Tipicamente, qui si dichiara e/o inizializza una variabile contatore (es. `int i = 0`).
    
2. **Condizione**: Valutata prima di ogni iterazione (come nel `while`, è un controllo in testa). Se è vera, il corpo del ciclo viene eseguito; altrimenti, il ciclo termina.
    
3. **Aggiornamento**: Eseguito _al termine_ di ogni iterazione, prima della successiva valutazione della condizione. Solitamente si tratta di un'operazione di incremento o decremento del contatore (es. `i++`).
    

```c
for (inizializzazione; condizione; aggiornamento) {
    // Corpo del ciclo
}
```

### Esercizio 3: Stampa di una Tabellina

**Problema**: Dato un numero in input, stampare la sua tabellina (da 1 a 10).

```c
#include <stdio.h>

int main() {
    int numero;
    printf("Inserisci un numero per la tabellina: ");
    scanf("%d", &numero);

    // 'i' funge da contatore e moltiplicatore
    // 1. Inizializzazione: int i = 1
    // 2. Condizione: i <= 10
    // 3. Aggiornamento: i++ (eseguito dopo il printf)
    for (int i = 1; i <= 10; i++) {
        int prodotto = numero * i;
        printf("%d x %d = %d\n", numero, i, prodotto);
    }

    return 0;
}
```

### Osservazioni sul Costrutto `for`

#### Visibilità (Scope) della Variabile Contatore

La variabile contatore del ciclo `for` (nell'esempio, `i`) può essere dichiarata in due modi:

1. **All'interno dell'istruzione `for`**: `for(int i = 1; ...)`.
    
    - In questo caso, la variabile `i` ha uno **scope di blocco**, ovvero è visibile e utilizzabile solo all'interno del corpo del ciclo `for`. Questo approccio è generalmente preferito perché limita la visibilità della variabile allo stretto necessario (principio del _least privilege_), migliorando la leggibilità e riducendo il rischio di errori.
        
2. **Prima dell'istruzione `for`**: `int i; for(i = 1; ...)`.
    
    - In questo caso, la variabile `i` è visibile in tutto il blocco in cui è stata dichiarata (es. l'intera funzione `main`). Sarà quindi accessibile anche dopo la fine del ciclo `for`, conservando il valore che ha causato la terminazione del ciclo stesso (nell'esempio precedente, `11`).
        

#### Errori "Off-by-One"

È fondamentale prestare attenzione ai limiti nelle espressioni di inizializzazione e condizione. Un errore comune è il cosiddetto "off-by-one" (errore di uno).

Per eseguire un blocco esattamente $N$ volte, i costrutti tipici sono:

- `for (int i = 0; i < N; i++)` (contatore da $0$ a $N-1$)
    
- `for (int i = 1; i <= N; i++)` (contatore da $1$ a $N$)
    

Usare `i <= N` quando si parte da $0$ o `i < N` quando si parte da $1$ porterebbe a $N+1$ o $N-1$ iterazioni, rispettivamente.

#### Flessibilità dell'Aggiornamento

La sezione di aggiornamento non è limitata a un incremento unitario. È possibile usare qualsiasi istruzione valida, ad esempio per passi non unitari: `for (int i = 0; i < N; i = i + 3)`

## Equivalenza `for` e `while`

Sebbene il ciclo `for` sia sintatticamente più comodo per le iterazioni a conteggio, è importante notare che **qualsiasi costrutto `for` è equivalente a un costrutto `while`**.

Il ciclo `for` è, di fatto, "zucchero sintattico" per un `while` strutturato in questo modo:

|Costrutto `for`|Costrutto `while` equivalente|
|---|---|
|`for (iniz; cond; agg) {`<br><br>`corpo;`<br><br>`}`|`iniz;`<br><br>`while (cond) {`<br><br>`corpo;`<br><br>`agg;`<br><br>`}`|

Questa equivalenza chiarisce perché il `for` sia un ciclo a **controllo in testa**: la `cond` viene valutata _prima_ di eseguire `corpo` e `agg`. Se `cond` è falsa all'inizio, né `corpo` né `agg` vengono mai eseguiti.

- **Quando usare `for`**: Preferibile quando il numero di iterazioni è noto a priori o quando c'è una chiara variabile di conteggio.
    
- **Quando usare `while`**: Preferibile quando il numero di iterazioni non è noto a priori e dipende da una condizione che può cambiare in modo non predicibile (es. input dell'utente, lettura da file).
    

## Istruzioni di Salto non Strutturate (`break` e `continue`)

Esistono due istruzioni che permettono di alterare il normale flusso di esecuzione sequenziale all'interno di un ciclo, anche se il loro uso è da limitare per non compromettere la leggibilità (vanno evitate dove possibile, in favore di una migliore strutturazione della logica).

### `break`

L'istruzione `break` **interrompe immediatamente l'esecuzione del costrutto iterativo** (`while`, `do-while`, `for`) o `switch` più interno in cui è contenuta. L'esecuzione riprende dalla prima istruzione _dopo_ il ciclo terminato.

È usata per gestire "uscite di emergenza" o per interrompere un ciclo non appena una condizione specifica è soddisfatta (es. ricerca di un valore in un array).

```c
// Esempio: esce dal ciclo non appena trova il numero 7
int i = 0;
while (1) { // Ciclo potenzialmente infinito
    printf("%d\n", i);
    if (i == 7) {
        break; // Interrompe il 'while'
    }
    i++;
}
// L'esecuzione continua da qui
```

### `continue`

L'istruzione `continue` **interrompe solo l'iterazione corrente** del ciclo (`while`, `do-while`, `for`) più interno in cui è contenuta. Salta tutte le istruzioni successive nel corpo del ciclo e passa direttamente all'iterazione successiva.

- **Nel `while` e `do-while`**: Salta alla valutazione della condizione.
    
- **Nel `for`**: Salta prima all'esecuzione dell'**aggiornamento** e poi alla valutazione della condizione.
    

```c
// Esempio: stampa solo i numeri dispari
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) {
        continue; // Salta il resto del blocco e passa a i++
    }
    // Questa istruzione viene eseguita solo se 'continue' non è stato attivato
    printf("%d\n", i);
}
```