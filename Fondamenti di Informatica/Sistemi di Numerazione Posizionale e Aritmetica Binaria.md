## Informazioni di Servizio e Organizzazione del Corso

Prima di procedere con gli argomenti della lezione, si forniscono alcuni aggiornamenti organizzativi.

### Orario di Ricevimento
L'orario di ricevimento è stato fissato per il **martedì, dalle 14:30 alle 16:30**. Si raccomanda di concordare preventivamente un appuntamento tramite email o messaggio su Microsoft Teams per evitare sovrapposizioni. L'orario è stato aggiornato anche sul sito docenti ufficiale per una facile consultazione.

### Canale Microsoft Teams
È stato creato un canale su Microsoft Teams per le comunicazioni relative al corso. Il codice di accesso è stato inserito nella versione aggiornata delle slide, disponibili per il download sul sito docenti. Per iscriversi:
1.  Accedere a Microsoft Teams con le proprie credenziali istituzionali (disponibili dopo l'immatricolazione).
2.  Navigare alla sezione "Team".
3.  Selezionare l'opzione "Unisciti a un team o creane uno".
4.  Inserire il codice fornito nel campo apposito per inviare la richiesta di partecipazione.

Le slide delle lezioni verranno caricate sia sul sito docenti, preferibilmente prima della lezione per chi desidera prendere appunti digitali, sia sul canale Teams.

## Introduzione ai Sistemi di Numerazione

Un sistema di numerazione è un insieme di simboli (cifre) e di regole utilizzate per rappresentare i numeri. Le regole definiscono come interpretare le sequenze di cifre per associarle a una quantità numerica.

### Sistemi Posizionali e Non Posizionali
I sistemi di numerazione si dividono principalmente in due categorie:

*   **Sistemi Posizionali**: Il valore di ogni cifra dipende dalla sua posizione all'interno del numero. Il sistema decimale, che utilizziamo quotidianamente, ne è l'esempio principale. Nel numero 120, la cifra '1' rappresenta le centinaia, '2' le decine e '0' le unità, in virtù della loro posizione.
*   **Sistemi Non Posizionali**: Il valore di un simbolo è generalmente indipendente dalla sua posizione. Un esempio classico è il sistema di numerazione romano. Il simbolo 'X' rappresenta sempre il valore 10. Sebbene esistano regole specifiche (es. IV per 4, dove la posizione di 'I' indica una sottrazione), il valore intrinseco del simbolo non cambia.

In questo corso ci concentreremo esclusivamente sui sistemi di numerazione posizionali, fondamentali per l'informatica.

### Rappresentazione Polinomiale di un Numero
In un sistema di numerazione posizionale con base $B$, un numero intero $x$, composto da $i$ cifre $C_{i-1}C_{i-2}...C_1C_0$, può essere espresso tramite una forma polinomiale. Il valore di $x$ è dato dalla somma dei prodotti di ogni cifra per la base $B$ elevata a una potenza corrispondente alla posizione della cifra stessa:

$$x = C_{i-1} \cdot B^{i-1} + C_{i-2} \cdot B^{i-2} + \dots + C_1 \cdot B^1 + C_0 \cdot B^0$$

Questa può essere espressa più sinteticamente con una sommatoria:

$$x = \sum_{j=0}^{i-1} C_j \cdot B^j$$

**Esempio (Base 10):** Il numero 120 nel sistema decimale (base $B=10$) si interpreta come:

$$120 = (1 \cdot 10^2) + (2 \cdot 10^1) + (0 \cdot 10^0) = 100 + 20 + 0 = 120$$

Questo concetto si estende anche ai **numeri frazionari**. Un numero con $i$ cifre per la parte intera e $k$ cifre per la parte frazionaria viene rappresentato utilizzando potenze positive (o nulle) della base per la parte intera e potenze negative per la parte frazionaria. Le cifre della parte frazionaria, $C_{-1}, C_{-2}, \dots, C_{-k}$, corrispondono a decimi, centesimi, millesimi nel sistema decimale.

## Sistemi di Numerazione Utilizzati in Informatica

Oltre al sistema decimale (base 10), in informatica sono di particolare interesse altri tre sistemi:

*   **Sistema Binario (Base 2):** Utilizza solo due cifre, 0 e 1. È il sistema fondamentale su cui si basano i calcolatori digitali.
*   **Sistema Ottale (Base 8):** Utilizza le cifre da 0 a 7.
*   **Sistema Esadecimale (Base 16):** Utilizza le cifre da 0 a 9 e le lettere da A a F per rappresentare i valori da 10 a 15.

Le cifre disponibili in una base $B$ vanno sempre da 0 a $B-1$. Per evitare ambiguità, si utilizza la notazione $(N)_B$ per indicare che il numero $N$ è rappresentato in base $B$. Ad esempio, $(101111)_2$ è un numero binario e non va letto come "centounomilacento undici".

## Conversione tra Basi di Numerazione

### Conversione da una Base B a Decimale
Per convertire un numero da una base $B$ qualsiasi al sistema decimale (base 10), si applica la formula della rappresentazione polinomiale vista in precedenza, eseguendo i calcoli in aritmetica decimale.

**Esempio 1: Binario a Decimale**
Convertire $(101111)_2$ in base 10.
$$\begin{aligned}(101111)_2 &= 1 \cdot 2^5 + 0 \cdot 2^4 + 1 \cdot 2^3 + 1 \cdot 2^2 + 1 \cdot 2^1 + 1 \cdot 2^0 \\ &= 32 + 0 + 8 + 4 + 2 + 1 = 47\end{aligned}$$

**Esempio 2: Base 5 a Decimale**
Convertire $(142)_5$ in base 10.
$$(142)_5 = 1 \cdot 5^2 + 4 \cdot 5^1 + 2 \cdot 5^0 = 25 + 20 + 2 = 47$$

Questi esempi dimostrano come la stessa quantità (47) possa avere rappresentazioni molto diverse in basi differenti.

### Conversione da Decimale a Binario
Il processo di conversione da decimale a binario richiede procedure diverse per la parte intera e la parte frazionaria del numero.

1.  **Conversione della Parte Intera:** Si utilizza l'algoritmo delle **divisioni successive**. La parte intera del numero decimale viene divisa ripetutamente per 2. I resti di ogni divisione (che possono essere solo 0 o 1) vengono raccolti. La sequenza dei resti, letta in ordine inverso (dall'ultimo al primo), costituisce la rappresentazione binaria della parte intera.

2.  **Conversione della Parte Frazionaria:** Si utilizza l'algoritmo delle **moltiplicazioni successive**. La parte frazionaria viene moltiplicata ripetutamente per 2. Ad ogni passo, la parte intera del risultato (che può essere solo 0 o 1) viene presa come cifra della rappresentazione binaria. La parte frazionaria rimanente viene utilizzata per l'iterazione successiva. Il processo termina quando la parte frazionaria si annulla. In alcuni casi, la rappresentazione binaria può essere periodica e infinita; in tali situazioni, si approssima il risultato a un numero finito di bit.

## Aritmetica Binaria e Operazioni sui Bit

Le operazioni aritmetiche in binario seguono principi logici simili a quelli dell'aritmetica decimale, ma applicati a un sistema con solo due cifre.

### Operazioni di Scorrimento (Shift)
Le operazioni di shift (scorrimento) spostano le cifre di un numero binario a sinistra o a destra di un numero specificato di posizioni.

*   **Shift a Sinistra:** Sposta i bit verso sinistra. I bit più significativi vengono scartati, mentre bit nulli (0) vengono inseriti nelle posizioni meno significative. Uno shift a sinistra di $n$ posizioni equivale a **moltiplicare** il numero per $2^n$.
    *   Esempio: $(101)_2$, che è 5, shiftato a sinistra di 1 posizione diventa $(1010)_2$, che è 10 ($5 \cdot 2^1$).

*   **Shift a Destra:** Sposta i bit verso destra. I bit meno significativi vengono scartati e bit nulli (0) vengono inseriti nelle posizioni più significative (per numeri senza segno). Uno shift a destra di $n$ posizioni equivale a una **divisione intera** del numero per $2^n$.
    *   Esempio: $(101)_2$, che è 5, shiftato a destra di 1 posizione diventa $(10)_2$, che è 2 (il risultato della divisione intera $5/2$).

### Moltiplicazione Binaria
La moltiplicazione tra due numeri binari si basa su semplici regole bit a bit ($0 \cdot 0=0$, $0 \cdot 1=0$, $1 \cdot 1=1$) e segue un algoritmo analogo a quello della moltiplicazione decimale in colonna:
1.  Si generano i prodotti parziali, moltiplicando il primo numero (moltiplicando) per ogni bit del secondo numero (moltiplicatore).
2.  Ogni prodotto parziale viene shiftato a sinistra di una posizione rispetto al precedente.
3.  Infine, si sommano tutti i prodotti parziali per ottenere il risultato finale.

**Esempio:** Calcolare $5 \cdot 3$, ovvero $(101)_2 \cdot (11)_2$.
```
    101  (5)
  x  11  (3)
  -----
    101  (101 * 1)
   101-  (101 * 1, shiftato di 1)
  -----
  1111   (Somma: 8+4+2+1 = 15)
```
Il risultato è $(1111)_2$, che corrisponde a 15 in decimale.

## Aritmetica a Precisione Finita e Overflow

Nei calcolatori, i numeri sono rappresentati utilizzando un **numero finito di bit** (es. 8, 16, 32, 64 bit). Questa limitazione, nota come **precisione finita**, implica che solo un intervallo limitato di numeri può essere rappresentato. Ad esempio, con 4 bit possiamo rappresentare i numeri interi da 0 a 15 ($2^4 - 1$).

### Condizione di Overflow
Si verifica una condizione di **overflow** quando il risultato di un'operazione aritmetica eccede i limiti dell'intervallo rappresentabile. In pratica, si genera un riporto oltre il bit più significativo, che viene perso.

**Esempio (4 bit):** Calcolare $12+4$, ovvero $(1100)_2 + (0100)_2$.
$$\begin{array}{@{}c@{\;}c@{}c@{}c@{}c@{}l} & \stackrel{1}{1} & \stackrel{1}{1} & 0 & 0 & + \\ & 0 & 1 & 0 & 0 & = \\ \hline 1 & 0 & 0 & 0 & 0 & \\ \end{array}$$
Il risultato è 16, che richiede 5 bit per essere rappresentato. Poiché disponiamo solo di 4 bit, il riporto `1` viene perso (overflow) e il risultato memorizzato sarebbe `0000`, che è errato.

### Proprietà Algebriche nell'Aritmetica Finita
L'aritmetica a precisione finita non rispetta sempre le proprietà algebriche standard, come la proprietà associativa e distributiva, a causa dei possibili overflow nei calcoli intermedi.

*   **Proprietà Associativa:** $(A+B)+C = A+(B+C)$ potrebbe non valere. Se $A=900, B=100, C=-600$ e la precisione è di 3 cifre decimali (range [-999, 999]), allora:
    *   $(900+100)-600 \rightarrow 1000-600 \rightarrow$ **Overflow**
    *   $900+(100-600) \rightarrow 900+(-500) = 400 \rightarrow$ **Corretto**

L'ordine delle operazioni diventa cruciale per la correttezza del risultato.

### Limitazioni della Sottrazione con Numeri Naturali
Nel contesto dei numeri naturali (interi senza segno), non è possibile rappresentare valori negativi. Di conseguenza, un'operazione come $2 - 4$ non può essere eseguita, poiché il risultato $(-2)$ non appartiene all'insieme dei numeri rappresentabili. Questo introduce la necessità di sistemi di rappresentazione per i numeri con segno, che verranno trattati successivamente.