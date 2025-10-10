# Struttura Fondamentale di un Programma in C

Un programma scritto in linguaggio C segue una struttura ben definita, essenziale per la sua corretta compilazione ed esecuzione. Gli elementi costitutivi di base includono le direttive per il preprocessore, la funzione principale (`main`), i blocchi di codice e le singole istruzioni.

### Direttive del Preprocessore
All'inizio del file sorgente si trovano le direttive per il preprocessore, comandi che vengono elaborati prima della compilazione vera e propria. Un esempio comune è l'inclusione di librerie esterne, ovvero moduli di codice preesistente che forniscono funzionalità aggiuntive.

La direttiva `#include` permette di includere una libreria. Ad esempio, per utilizzare funzioni di input/output standard come `printf` e `scanf`, è necessario includere la libreria `stdio.h` (Standard Input/Output):
```c  
#include <stdio.h>
```  
  
Le parentesi angolari (`< >`) indicano al preprocessore di cercare la libreria nelle directory di sistema standard.  
  
### La Funzione `main`  
Ogni programma C deve contenere una funzione denominata `main`. Questa funzione rappresenta l'**entry point**, ovvero il punto di partenza da cui inizia l'esecuzione del programma. La sua sintassi tipica è:  
  
```c  
int main() {  
// Corpo della funzione  
return 0;  
}  
```  
  
- **`int`**: Specifica che la funzione `main` restituisce un valore di tipo intero al sistema operativo al termine della sua esecuzione.  
- **`main()`**: È il nome della funzione. Le parentesi tonde `()` sono necessarie e possono contenere eventuali parametri passati al programma all'avvio.  
  
### Blocchi di Codice e Istruzioni  
Il codice eseguibile della funzione `main` (e di qualsiasi altra funzione) è racchiuso all'interno di un **blocco**, delimitato da parentesi graffe (`{ }`). All'interno di questo blocco, le **istruzioni** — le singole frasi che compongono il programma — vengono eseguite in modo sequenziale, dall'alto verso il basso. Ogni istruzione deve obbligatoriamente terminare con un punto e virgola (`;`), che agisce come terminatore.  
  
L'omissione del punto e virgola costituisce un [[Fondamenti di Informatica/09 - Fondamenti di Programmazione in C, Compilazione ed Errori#1. Errori a Tempo di Compilazione (Compile-Time Errors)|errore di sintassi]] che impedisce la compilazione del programma.  
  
### L'Istruzione `return`  
Generalmente, alla fine della funzione `main` si trova l'istruzione `return`, che termina l'esecuzione della funzione e restituisce un valore al sistema operativo. Per convenzione, `return 0;` indica che il programma è terminato con successo.  
  
```c  
return 0;  
```  
  
## Leggibilità e Stile del Codice  
Sebbene non strettamente richiesto dal compilatore C, adottare buone pratiche di scrittura del codice è fondamentale per garantirne la leggibilità, la comprensibilità e la manutenibilità.  
  
### Indentazione e Spaziatura  
L'**indentazione** consiste nell'utilizzare spazi (o caratteri di tabulazione) all'inizio di una riga per rappresentare visivamente la struttura gerarchica del codice. Le istruzioni all'interno di un blocco vengono indentate per indicare la loro appartenenza a quel blocco. L'uso di righe vuote per separare sezioni logiche del codice (es. tra le direttive `#include` e la funzione `main`) migliora ulteriormente la leggibilità.  
  
### Commenti  
I commenti sono porzioni di testo ignorate dal compilatore, destinate esclusivamente al programmatore per documentare il codice. Servono a spiegare la logica di una funzione, il significato di una variabile o il funzionamento di un [[Fondamenti di Informatica/08 - Introduzione ad Algoritmi, Complessità e Linguaggi di Programmazione|algoritmo]] complesso.  
  
Esistono due tipi di commenti in C:  
- **Commenti a linea singola**: Iniziano con `//` e si estendono fino alla fine della riga.  
```c  
// Questo è un commento su una sola riga  
```  
- **Commenti multilinea**: Iniziano con `/*` e terminano con `*/`. Possono estendersi su più righe.  
```c  
/*  
* Questo è un commento  
* che occupa più righe.  
*/  
```  
  
## Istruzioni di Input e Output  
  
Le operazioni di input e output (I/O) consentono al programma di comunicare con l'esterno, ad esempio mostrando dati sullo schermo (output) o leggendo dati dalla tastiera (input). Queste funzionalità sono fornite dalla libreria `stdio.h`.  
  
### Output: La Funzione `printf`  
La funzione `printf` (print formatted) invia dati formattati allo **standard output**, che tipicamente è il monitor.  
  
La sua forma base prevede il passaggio di una stringa costante:  
```c  
printf("Hello, World!\n");  
```  
La sequenza `\n` è un carattere speciale (sequenza di escape) che rappresenta un ritorno a capo (newline).  
  
`printf` può anche stampare il valore di variabili. Per fare ciò, si utilizzano degli **specificatori di formato** all'interno della stringa. Questi specificatori sono segnaposto che iniziano con l'operatore `%` e vengono sostituiti dai valori delle variabili passate come argomenti successivi.  
  
**Esempio:**  
```c  
int a = 5;  
float b = 3.14;  
char c = 'K';  
printf("La variabile intera 'a' ha valore: %d\n", a);  
printf("La variabile float 'b' ha valore: %f\n", b);  
printf("La variabile char 'c' ha valore: %c\n", c);  
```  
In questo caso, `%d` è lo specificatore per un intero decimale con segno, `%f` per un float e `%c` per un carattere. La funzione sostituirà ogni specificatore con il valore della variabile corrispondente.  
  
È possibile includere più specificatori, passando un corrispondente numero di variabili:  
```c  
printf("Valore di a: %d, e valore di b: %f\n", a, b);  
```  
  
#### Principali Specificatori di Formato per `printf`  
- `%d`, `%i`: Intero decimale con segno.  
- `%u`: Intero decimale senza segno.  
- `%c`: Singolo carattere.  
- `%s`: Stringa di caratteri.  
- `%f`: Numero in virgola mobile (float/double).  
- `%x`: Intero in formato esadecimale.  
- `%p`: Indirizzo di memoria (puntatore).  
  
#### Sequenze di Escape  
Le sequenze di escape permettono di inserire caratteri speciali all'interno di una stringa. Iniziano con un backslash (`\`).  
- `\n`: Newline (ritorno a capo).  
- `\t`: Tabulazione orizzontale.  
- `\"`: Doppio apice (per stampare il carattere `"`).  
- `\'`: Apice singolo.  
- `\\`: Backslash (per stampare il carattere `\`).  
- `\nnn`: Carattere ASCII con valore ottale `nnn`.  
- `\xhh`: Carattere ASCII con valore esadecimale `hh`.  
  
### Input: La Funzione `scanf`  
La funzione `scanf` è duale a `printf` e serve per leggere dati formattati dallo **standard input** (tipicamente la tastiera). Anch'essa utilizza specificatori di formato per interpretare correttamente i dati inseriti dall'utente.  
  
La sintassi richiede una stringa di formato e l'indirizzo di memoria della variabile in cui salvare il dato letto. Per ottenere l'indirizzo di una variabile si utilizza l'operatore **address-of** (`&`).  
  
**Esempio:**  
```c  
int numero;  
printf("Inserisci un numero: ");  
scanf("%d", &numero);  
printf("Numero inserito: %d\n", numero);  
```  
1. `int numero;` dichiara una variabile intera.  
2. `scanf("%d", &numero);` attende che l'utente digiti un numero intero e prema Invio.  
3. Il valore inserito viene interpretato come intero (`%d`) e memorizzato all'indirizzo della variabile `numero` (`&numero`).  
  
Durante l'esecuzione di `scanf`, il programma si interrompe temporaneamente, in attesa dell'input dell'utente. L'operazione di lettura termina quando viene premuto il tasto Invio.  
  
## Dichiarazioni e Istruzioni Elementari  
  
Un programma è composto da frasi che possono essere classificate in diverse categorie.  
1. **Dichiarazioni**: Istruzioni dirette al [[Fondamenti di Informatica/09 - Fondamenti di Programmazione in C, Compilazione ed Errori#Dal Codice Sorgente all'Esecuzione: Il Processo di Compilazione|compilatore]] che introducono nuovi elementi, come le variabili. Non vengono tradotte in istruzioni macchina eseguibili, ma servono a guidare il processo di traduzione (es. riservare spazio in memoria).  
2. **Istruzioni**: Comandi che specificano operazioni da eseguire (calcolo, assegnazione) e che vengono tradotti in [[Fondamenti di Informatica/08 - Introduzione ad Algoritmi, Complessità e Linguaggi di Programmazione#8. Linguaggi di Programmazione: Struttura e Livelli|linguaggio macchina]].  
3. **Strutture di controllo**: Costrutti che alterano il flusso sequenziale di esecuzione (es. cicli `for`/`while`, condizionali `if`/`else`).  
4. **Commenti**: Frasi in linguaggio naturale ignorate dal compilatore.  
  
### Identificatori  
Un **identificatore** è un nome utilizzato per riferirsi a entità come variabili, costanti, funzioni e tipi di dati definiti dall'utente. Gli identificatori devono seguire regole precise:  
- Devono iniziare con una lettera (maiuscola o minuscola) o con un trattino basso (`_`).  
- I caratteri successivi possono essere lettere, numeri o trattini bassi.  
- Non possono contenere spazi o altri caratteri speciali (es. `?`, `!`, `-`, `+`).  
- Non possono coincidere con le **parole chiave** (keyword) del linguaggio (es. `int`, `return`, `if`).  
- Il linguaggio C è **case-sensitive**: `minimo` e `Minimo` sono due identificatori distinti.  
- Non esistono limitazioni sulla lunghezza.  
  
È buona norma utilizzare nomi significativi ed espressivi per migliorare la comprensibilità del codice (es. `valoreMinimo` invece di `vm`).  
  
**Esempi:**  
- `pi_greco`, `alpha1`, `eq2grado`: Validi  
- `2alpha`, `ax?yeq`, `2grado`: Non validi  
  
### Variabili: Dichiarazione, Definizione e Inizializzazione  
Una **variabile** è un contenitore di dati, ovvero una porzione di [[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Il Sottosistema di Memoria|memoria]] a cui è associato un identificatore. Ogni variabile ha un tipo, che ne definisce la natura, le operazioni consentite e lo spazio occupato in memoria.  
  
#### Dichiarazione e Definizione  
Prima di poter essere utilizzata, una variabile deve essere **dichiarata**. La dichiarazione specifica il tipo e il nome della variabile. In C, la dichiarazione è anche una **definizione**, in quanto il compilatore alloca contestualmente un'apposita area di memoria per la variabile.  
  
**Sintassi:**  
```c  
tipo identificatore;  
```  
  
**Esempio:**  
```c  
int numero;  
char carattere_scelto;  
```  
Questa dichiarazione istruisce il compilatore a riservare in memoria lo spazio necessario per un `int` e un `char`, associandoli agli identificatori `numero` e `carattere_scelto`. La sola dichiarazione non assegna un valore iniziale alla variabile; il suo contenuto è indefinito (o "sporco").  
  
È possibile dichiarare più variabili dello stesso tipo su una singola riga, separandole con una virgola:  
```c  
int var1, var2, var3;  
```  
  
#### Assegnazione e Inizializzazione  
L'**assegnazione** è l'operazione che attribuisce un valore a una variabile. Si utilizza l'operatore di assegnazione (`=`).  
  
**Sintassi:**  
```c  
variabile = espressione;  
```  
L'**inizializzazione** è il termine specifico per la prima assegnazione di un valore a una variabile. È possibile combinare dichiarazione e inizializzazione in un'unica istruzione:  
  
```c  
int a = 5; // Dichiarazione e inizializzazione  
```  
Questa istruzione non solo dichiara la variabile `a`, ma le assegna anche il valore iniziale 5. A differenza della sola dichiarazione, questa operazione viene tradotta in un'istruzione in linguaggio macchina che scrive il valore `5` nella locazione di memoria riservata per `a`.  
  
**Regole Fondamentali:**  
1. Una variabile **non può** essere usata prima di essere stata **definita**.  
2. Una variabile **non deve** essere usata (letta) prima di essere stata **inizializzata**, per evitare di lavorare con valori imprevedibili.  
  
```c  
int a, b;  
a = 1; // Inizializzazione di a  
b = a + 1; // Uso (lettura) di a per assegnare un valore a b  
```  
  
## Tipi di Dati in C  
  
I tipi delle variabili in C si dividono in due categorie principali.  
  
### Tipi Semplici (o Atomici)  
Sono i tipi di dati fondamentali, non suddivisibili.  
- **`int`**: per i numeri interi.  
- **`char`**: per i singoli caratteri (ma internamente è un tipo intero a 8 bit).  
- **`float`**: per i numeri reali in [[Fondamenti di Informatica/04 - Rappresentazione dei Numeri Reali in Virgola Mobile#Formato a Precisione Singola (32 bit)|precisione singola]].  
- **`double`**: per i numeri reali in [[Fondamenti di Informatica/04 - Rappresentazione dei Numeri Reali in Virgola Mobile#Formato a Doppia Precisione (64 bit)|doppia precisione]].  
- **`bool`**: tipo booleano (logico), che può assumere i valori `true` o `false`.  
  
#### Modificatori di Tipo  
Questi modificatori alterano la dimensione o il range dei tipi semplici:  
- **`short`**, **`long`**, **`long long`**: Modificano la dimensione degli interi. Lo standard garantisce che `sizeof(short int) <= sizeof(int) <= sizeof(long int)`.  
- **`unsigned`**: Specifica che il tipo intero può rappresentare solo valori non negativi, raddoppiandone il range positivo.  
  
L'occupazione di memoria di ogni tipo dipende dall'architettura e dal compilatore. Per conoscere la dimensione esatta in byte di un tipo o di una variabile, si usa l'operatore `sizeof()`:  
```c  
printf("Dimensione di un int: %zu byte\n", sizeof(int));  
printf("Dimensione di un double: %zu byte\n", sizeof(double));  
```  
I valori limite (minimo e massimo) per ciascun tipo sono definiti come macro nella libreria `limits.h`.  
  
### Tipi Strutturati  
Sono tipi composti da più tipi semplici o da altri tipi strutturati.  
- **`array`**: Collezione omogenea di elementi dello stesso tipo.  
- **`struct`**: Collezione eterogenea di elementi di tipi diversi (record).  
  
### Definizione di Tipi Personalizzati con `typedef`  
Il C permette di assegnare un nuovo nome (un alias) a un tipo esistente tramite la parola chiave `typedef`. Questo non crea un nuovo tipo, ma migliora la leggibilità del codice.  
```c  
typedef unsigned long int ulong;  
ulong contatore = 100000; // 'contatore' è di tipo unsigned long int  
```  
Le dichiarazioni di tipo con `typedef` non comportano occupazione di memoria.  
  
## Costanti e Letterali  
Le **costanti** sono valori fissi che non possono essere alterati durante l'esecuzione del programma.  
  
### Letterali  
Un **letterale** è la rappresentazione di un valore costante direttamente nel codice.  
- **Interi**: `10`, `-5`, `123`. Possono avere un suffisso per specificarne il tipo: `12u` (unsigned int), `25L` (long int), `50ULL` (unsigned long long).  
- **Reali**: `3.14` (virgola fissa), `1.2E-3` (virgola mobile, notazione scientifica).  
- **Caratteri**: Un singolo carattere racchiuso tra apici singoli, es: `'A'`, `'?'`.  
- **Stringhe**: Una sequenza di caratteri racchiusa tra doppi apici, es: `"Hello, World!"`.  
  
È possibile specificare letterali numerici in basi diverse:  
- **Ottale (base 8)**: prefisso `0`, es. `045`.  
- **Esadecimale (base 16)**: prefisso `0x` o `0X`, es. `0x1B`.  
- **Binario (base 2)**: prefisso `0b` o `0B`, es. `0b101`.  
  
### Costanti Simboliche  
Per migliorare leggibilità e manutenibilità, è buona pratica dare un nome a una costante. Ci sono due modi principali:  
1. **Direttiva `#define`**: Sostituisce testualmente il nome della costante con il suo valore prima della compilazione. Non viene allocata memoria.  
```c  
#define PI_GRECO 3.14159  
```  
2. **Parola chiave `const`**: Dichiara una costante "tipizzata", a cui viene allocata memoria ma il cui valore non può essere modificato dopo l'inizializzazione.  
```c  
const float pi_greco = 3.14159;  
```  
  
## Operatori in C  
  
Gli operatori sono simboli che specificano un'operazione da eseguire.  
  
### Operatori Aritmetici  
Eseguono calcoli matematici.  
- `+` (addizione), `-` (sottrazione), `*` (moltiplicazione).  
- `/` (divisione): Se entrambi gli operandi sono interi, esegue una **divisione intera** (tronca la parte decimale). Per ottenere una divisione reale, almeno uno degli operandi deve essere di tipo `float` o `double`.  
- `%` (modulo): Restituisce il resto della divisione intera.  
  
Per operazioni matematiche più complesse (potenza, radice, funzioni trigonometriche) è necessario includere la libreria `math.h` e usare funzioni come `pow()`, `sqrt()`, `sin()`.  
  
### Operatori di Assegnazione  
- `=` (assegnazione semplice): Assegna il valore a destra alla variabile a sinistra.  
- **Operatori composti** (`+=`, `-=`, `*=`, `/=`, `%=`): Combinano un'operazione aritmetica con un'assegnazione.  
```c  
x += 5; // Equivalente a x = x + 5;  
```  
  
### Operatori di Incremento e Decremento  
- `++` (incremento unitario): Aumenta il valore di una variabile di 1.  
- `--` (decremento unitario): Diminuisce il valore di una variabile di 1.  
Esistono in forma **prefissa** e **postfissa**:  
- **Prefissa (`++i`, `--i`)**: Incrementa/decrementa il valore e *poi* restituisce il nuovo valore.  
- **Postfissa (`i++`, `i--`)**: Restituisce il valore originale e *poi* lo incrementa/decrementa.  
```c  
int i = 5;  
int a = ++i; // a vale 6, i vale 6  
int j = 5;  
int b = j++; // b vale 5, j vale 6  
```  
  
### Operatori Relazionali e Logici  
- **Relazionali**: Confrontano due valori e restituiscono un risultato booleano (`true` o `false`).  
`==` (uguale a), `!=` (diverso da), `>` (maggiore di), `<` (minore di), `>=` (maggiore o uguale), `<=` (minore o uguale).  
**Attenzione a non confondere `==` (confronto) con `=` (assegnazione).**  
  
- **Logici**: Combinano espressioni booleane.  
`&&` (AND logico), `||` (OR logico), `!` (NOT logico).  
  
### Operatori Bitwise  
Operano direttamente sulla [[Fondamenti di Informatica/02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria|rappresentazione binaria]] dei numeri.  
- `&` (AND bit a bit), `|` (OR bit a bit), `^` (XOR bit a bit), `~` (complemento a 1).  
- `<<` (shift a sinistra), `>>` (shift a destra).  
  
### Operatore Condizionale (Ternario)  
Fornisce una scorciatoia per un'istruzione `if-else`.  
```c  
condizione ? espressione_se_vera : espressione_se_falsa;  
```  
**Esempio:**  
```c  
int a = 10, b = 20;  
int max = (a > b) ? a : b; // max sarà 20  
```  
  
### Precedenza degli Operatori  
Le espressioni complesse vengono valutate secondo regole di precedenza ben definite. Ad esempio, gli operatori moltiplicativi (`*`, `/`, `%`) hanno precedenza su quelli additivi (`+`, `-`). È buona pratica usare le parentesi `()` per forzare un ordine di valutazione e migliorare la leggibilità.  
  
| Priorità | Operatore | Descrizione |  
|:---:|:---:|---|  
| 1 | `++`, `--` | Incremento/decremento postfisso |  
| 2 | `++`, `--`, `!`, `~` | Operatori unari (prefissi), NOT |  
| 3 | `*`, `/`, `%` | Moltiplicativi |  
| 4 | `+`, `-` | Additivi |  
| 5 | `<<`, `>>` | Shift |  
| 6 | `<`, `<=`, `>`, `>=` | Relazionali |  
| 7 | `==`, `!=` | Uguaglianza |  
| ... | ... | ... |  
| 11| `&&` | AND logico |  
| 12| `||` | OR logico |  
| 13| `?:` | Condizionale |  
| 14| `=` e composti | Assegnazione |  
  
  
## Conversione di Tipo (Casting)  
Il C può eseguire conversioni di tipo automatiche (implicite) o forzate (esplicite).  
- **Conversione implicita**: Avviene quando si combinano tipi diversi in un'espressione. Il compilatore "promuove" il tipo di dato meno capiente a quello più capiente (es. `int` a `float`).  
- **Conversione esplicita (casting)**: Forza la conversione di un'espressione a un tipo specifico. È anche detta coercizione.  
```c  
(tipo) espressione;  
```  
**Esempio:** Forzare una divisione reale tra due interi.  
```c  
int a = 5, b = 2;  
float risultato = (float)a / b; // risultato = 2.5  
// Senza cast, a / b darebbe 2, e il risultato sarebbe 2.0  
```  
  
## Esempio Pratico: Scambio di Variabili (Swap)  
Un problema classico per mettere in pratica questi concetti è lo scambio del valore di due variabili.  
```c  
#include  
  
int main() {  
	int x = 10;  
	int y = 20;  
	int temp; // Variabile di appoggio  
  
	printf("Prima dello scambio: x = %d, y = %d\n", x, y);  
  
	// Algoritmo di swap  
	temp = x; // 1. Salvo il valore di x in temp  
	x = y; // 2. Copio il valore di y in x (sovrascrivendolo)  
	y = temp; // 3. Copio il valore originale di x (salvato in temp) in y  
  
	printf("Dopo lo scambio: x = %d, y = %d\n", x, y);  
  
return 0;  
}  
```  
Questo esempio illustra la dichiarazione, inizializzazione, assegnazione e l'uso di una variabile temporanea per risolvere un problema logico comune.  