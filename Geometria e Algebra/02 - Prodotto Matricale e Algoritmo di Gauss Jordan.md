## Riepilogo delle Lezioni Precedenti: Operazioni tra Matrici

Nelle lezioni precedenti sono state introdotte le nozioni fondamentali relative alle matrici. Di seguito, un breve riepilogo degli argomenti trattati:

1.  **[[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#^1f6aea|Definizione di Matrice]]:** Introduzione al concetto di matrice come tabella rettangolare di numeri.
2.  **[[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Operazioni Elementari con le Matrici|Uguaglianza, Somma e Sottrazione]]:** Operazioni definite per matrici delle stesse dimensioni.
3.  **[[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Proprietà della Somma e della Moltiplicazione Scalare|Trasposizione]]:** Operazione che scambia le righe con le colonne di una matrice.
4.  **[[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Moltiplicazione per uno Scalare|Moltiplicazione per uno Scalare]]:** Prodotto di una matrice per un numero (scalare).

L'ultima operazione introdotta è stata la **moltiplicazione riga per colonna** tra due matrici.

## Il Prodotto Riga per Colonna

### Definizione e Condizioni di Esistenza

Date due matrici, $A$ di dimensioni $m \times n$ e $B$ di dimensioni $p \times q$, il prodotto riga per colonna $A \times B$ è definito solo se il numero di colonne di $A$ è uguale al numero di righe di $B$, ovvero se $n=p$. In tal caso, la matrice prodotto $C = A \times B$ avrà dimensioni $m \times q$.

L'entrata $c_{ik}$ della matrice prodotto $C$, che si trova all'incrocio della $i$-esima riga e della $k$-esima colonna, è calcolata come il prodotto scalare tra la $i$-esima riga di $A$ e la $k$-esima colonna di $B$. Formalmente:

$$c_{ik} = \sum_{j=1}^{n} a_{ij} b_{jk}$$

Questa operazione è detta "riga per colonna" proprio perché ogni elemento della matrice risultato si ottiene combinando una riga della prima matrice con una colonna della seconda.

### La Non Commutatività del Prodotto

Una delle proprietà più importanti e controintuitive del prodotto tra matrici è la sua **non commutatività**. In generale, $A \times B \neq B \times A$.

Analizziamo i diversi scenari:

1.  **Prodotto Definito in un Solo Verso:** Se $A$ è $2 \times 3$ e $B$ è $3 \times 1$, il prodotto $A \times B$ è definito e risulta in una matrice $2 \times 1$. Tuttavia, il prodotto $B \times A$ non è definito, poiché le dimensioni interne non sono compatibili ($B$ è $3 \times 1$ e $A$ è $2 \times 3$, quindi $1 \neq 2$).

2.  **Prodotti Definiti ma di Dimensioni Diverse:** Se $A$ è $2 \times 3$ e $C$ è $3 \times 2$, entrambi i prodotti sono definiti. $A \times C$ è una matrice $2 \times 2$, mentre $C \times A$ è una matrice $3 \times 3$. Essendo di dimensioni diverse, non possono essere uguali.

3.  **Matrici Quadrate della Stessa Dimensione:** Anche quando si moltiplicano due matrici quadrate della stessa dimensione, per cui $A \times B$ e $B \times A$ sono definite e hanno le stesse dimensioni, il risultato non è, in generale, lo stesso. Consideriamo il seguente esempio:
    Siano $D = \begin{pmatrix} 1 & 1 \\ 0 & 0 \end{pmatrix}$ e $E = \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}$.

    $$D \times E = \begin{pmatrix} 1 & 1 \\ 0 & 0 \end{pmatrix} \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}$$

    $$E \times D = \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} \begin{pmatrix} 1 & 1 \\ 0 & 0 \end{pmatrix} = \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}$$

    Come si può osservare, $D \times E \neq E \times D$. La non commutatività è una caratteristica fondamentale dell'algebra delle matrici.

## Proprietà del Prodotto Matricale

Nonostante la mancanza della proprietà commutativa, il prodotto riga per colonna gode di altre importanti proprietà algebriche. Siano $A, A'$ matrici $m \times n$; $B, B'$ matrici $n \times p$; $C$ matrice $p \times r$ e $\lambda$ uno scalare. Valgono le seguenti proprietà:

*   **Proprietà Associativa:** $(A \times B) \times C = A \times (B \times C)$
*   **Compatibilità con la Moltiplicazione Scalare:** $\lambda (A \times B) = (\lambda A) \times B = A \times (\lambda B)$
*   **Proprietà Distributiva a Sinistra:** $(A + A') \times B = A \times B + A' \times B$
*   **Proprietà Distributiva a Destra:** $A \times (B + B') = A \times B + A \times B'$
*   **Relazione con la Trasposizione:** $(A \times B)^T = B^T \times A^T$. Si noti l'inversione dell'ordine dei fattori, una conseguenza diretta della natura "riga per colonna" del prodotto e dell'operazione di trasposizione.

## Matrice Inversa e Matrice Identità

### Il Concetto di Inverso

In analogia con l'aritmetica dei numeri reali, dove la divisione $a/b$ può essere vista come la moltiplicazione $a \times (1/b)$, dove $1/b$ è l'inverso moltiplicativo di $b$, si cerca di definire un concetto simile per le matrici. Per farlo, è necessario prima identificare un elemento neutro per la moltiplicazione.

### La Matrice Identità come Elemento Neutro

L'elemento neutro esiste solo nel contesto delle matrici quadrate. La **matrice identità** di ordine $n$, denotata con $I_n$, è una matrice quadrata $n \times n$ con tutti 1 sulla diagonale principale e 0 altrove. La matrice identità è un caso particolare di [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Tipologie di Matrici Speciali|matrice diagonale]]. Essa agisce come l'elemento neutro per la moltiplicazione, ovvero per qualsiasi matrice quadrata $A$ di dimensione $n \times n$:

$$A \times I_n = I_n \times A = A$$

### Definizione di Matrice Inversa

Data una matrice quadrata $A$ di dimensione $n \times n$, la sua **matrice inversa**, se esiste, è una matrice $A^{-1}$ tale che:

$$A \times A^{-1} = A^{-1} \times A = I_n$$

### Il Problema dell'Esistenza dell'Inversa

Non tutte le matrici quadrate ammettono un'inversa. L'esistenza dell'inversa è una questione cruciale. Per analogia, se consideriamo solo i numeri interi, l'inverso di 2 (cioè 1/2) non esiste all'interno di quell'insieme. Allo stesso modo, per le matrici, dobbiamo stabilire dei criteri per determinare quando una matrice è invertibile.

## Forme a Scala (Echelon) di una Matrice

Per affrontare il problema dell'invertibilità e per risolvere sistemi di equazioni lineari, si introduce il concetto di forma a scala di una matrice.

### Forma a Scala (Row Echelon Form)

Una matrice (non necessariamente quadrata) è in **forma a scala** se soddisfa due condizioni:

1.  Tutte le righe composte interamente da zeri (righe nulle) si trovano in fondo alla matrice.
2.  In ogni riga non nulla, il primo elemento non nullo da sinistra, detto **pivot**, si trova in una colonna a destra del pivot della riga precedente.

Questo conferisce alla matrice una struttura "a gradoni".

### Forma a Scala Ridotta (Reduced Row Echelon Form)

Una matrice è in **forma a scala ridotta** se, oltre a essere in forma a scala, soddisfa altre due condizioni:

1.  Ogni pivot è l'unico elemento non nullo nella sua colonna.
2.  Tutti i pivot sono uguali a 1.

La forma a scala ridotta è una generalizzazione della matrice identità per matrici rettangolari.

## Sottomatrici

Una **sottomatrice** di una matrice $A$ è una matrice ottenuta selezionando un certo numero di righe e un certo numero di colonne da $A$ e prendendo gli elementi che si trovano alle loro intersezioni. Le righe e le colonne scelte non devono necessariamente essere contigue.

## L'Algoritmo di Eliminazione di Gauss-Jordan

### Scopo del Gioco e Regole: Le Operazioni Elementari di Riga

L'obiettivo fondamentale è trasformare una qualsiasi matrice nella sua forma a scala ridotta. Per fare ciò, sono permesse tre operazioni, dette **operazioni elementari di riga**:

1.  **Scambio:** Scambiare due righe ($R_i \leftrightarrow R_j$).
2.  **Scalatura:** Moltiplicare una riga per uno scalare non nullo ($R_i \to k R_i$, con $k \neq 0$).
3.  **Combinazione Lineare:** Sostituire una riga con la somma di se stessa e un multiplo di un'altra riga ($R_i \to R_i + k R_j$, con $i \neq j$).

### Il Metodo di Eliminazione di Gauss-Jordan

Il metodo di Gauss-Jordan è un algoritmo sistematico che garantisce di poter trasformare qualsiasi matrice nella sua forma a scala ridotta utilizzando esclusivamente le operazioni elementari di riga. L'algoritmo si articola in due fasi principali:

**Fase 1: Eliminazione in Avanti (Forward Elimination)**

Questa fase trasforma la matrice in una forma a scala.

1.  Identificare la prima colonna da sinistra che contiene almeno un elemento non nullo.
2.  Trovare il primo elemento non nullo in questa colonna. Se si trova nella riga $i$, scambiare la riga $i$ con la prima riga della sottomatrice considerata.
3.  Dividere la prima riga per il valore del pivot, in modo che il pivot diventi 1.
4.  Utilizzare il pivot (che ora è 1) per annullare tutti gli altri elementi nella sua colonna al di sotto di esso, sottraendo multipli appropriati della prima riga dalle righe sottostanti.
5.  Ignorare la prima riga e la prima colonna e ripetere il processo sulla sottomatrice rimanente, fino a esaurire le righe o le colonne.

**Fase 2: Sostituzione all'Indietro (Back Substitution)**

Questa fase trasforma la matrice da forma a scala a forma a scala ridotta.

6.  Partendo dall'ultimo pivot (quello più in basso a destra), utilizzarlo per annullare tutti gli elementi sopra di esso nella stessa colonna, aggiungendo o sottraendo multipli appropriati della riga del pivot dalle righe superiori.
7.  Ripetere il processo per ogni pivot, procedendo dal basso verso l'alto, fino a quando tutti i pivot non saranno gli unici elementi non nulli nelle rispettive colonne.

Questo algoritmo è di importanza capitale in algebra lineare, poiché costituisce la base per la risoluzione di sistemi di equazioni lineari da parte dei computer, ed è essenziale per calcolare l'inversa di una matrice.

### Esempio Pratico di Riduzione a Scala

Consideriamo la matrice $A = \begin{pmatrix} 1 & 0 & 2 \\ 1 & 1 & 2 \\ 0 & -1 & -1 \end{pmatrix}$.

1.  Il primo pivot è in posizione (1,1) ed è già 1. Lo usiamo per annullare l'elemento sottostante. Applichiamo l'operazione $R_2 \to R_2 - R_1$:
    $$ \begin{pmatrix} 1 & 0 & 2 \\ 0 & 1 & 0 \\ 0 & -1 & -1 \end{pmatrix} $$
2.  Il secondo pivot è in posizione (2,2) ed è già 1. Lo usiamo per annullare l'elemento sottostante. Applichiamo l'operazione $R_3 \to R_3 + R_2$:
    $$ \begin{pmatrix} 1 & 0 & 2 \\ 0 & 1 & 0 \\ 0 & 0 & -1 \end{pmatrix} $$
3.  La matrice è ora in forma a scala. Per portarla in forma a scala ridotta, normalizziamo il terzo pivot. Applichiamo $R_3 \to -1 \cdot R_3$:
    $$ \begin{pmatrix} 1 & 0 & 2 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} $$
4.  Infine, usiamo il terzo pivot per annullare l'elemento sopra di esso. Applichiamo $R_1 \to R_1 - 2R_3$:
    $$ \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} $$

La matrice ottenuta è la matrice identità, che è la forma a scala ridotta della matrice di partenza.