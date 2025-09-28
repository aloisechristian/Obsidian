## Riepilogo delle Proprietà del Determinante

### 1. Richiamo della Definizione di Determinante

Si inizia richiamando la definizione formale di determinante per una [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Tipologie di Matrici Speciali|matrice quadrata]] $A$ di dimensione $n \times n$, con entrate indicate come $a_{ij}$. Il determinante è un valore scalare associato alla matrice, definito come la somma estesa a tutte le possibili [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Introduzione alle Permutazioni|permutazioni]] $\sigma$ dell'insieme di indici $\{1, 2, ..., n\}$:

$$ \det(A) = \sum_{\sigma \in S_n} \text{sgn}(\sigma) \prod_{i=1}^{n} a_{i, \sigma(i)} $$ 

Dove $S_n$ è l'insieme di tutte le $n!$ permutazioni di $n$ elementi e $\text{sgn}(\sigma)$ è il [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Inversioni e Segno di una Permutazione|segno della permutazione]] $\sigma$, che vale $+1$ se la permutazione è pari e $-1$ se è dispari.

### 2. Proprietà Fondamentali del Determinante

Si procede con l'analisi delle proprietà fondamentali del determinante di una matrice quadrata $A$.

1.  **Invarianza per Trasposizione**: Il determinante di una matrice è uguale al determinante della sua trasposta.
    $$ \det(A^T) = \det(A) $$ 
    Questa proprietà è di fondamentale importanza, poiché implica che ogni risultato o proprietà dimostrata per le righe di una matrice è valida, in modo del tutto analogo, anche per le sue colonne.

2.  **Permutazione delle Righe**: Se una matrice $A'$ è ottenuta da $A$ permutando le sue righe secondo una permutazione $\tau$, il determinante di $A'$ è legato a quello di $A$ dal segno della permutazione.
    $$ \det(A') = \text{sgn}(\tau) \cdot \det(A) $$ 
    Un caso particolare e molto comune di questa proprietà è lo **scambio di due righe**. Se $A'$ è ottenuta scambiando due righe di $A$, la permutazione è un singolo scambio (una trasposizione) il cui segno è $-1$. Pertanto:
    $$ \det(A') = -\det(A) $$ 

3.  **Multilinearità rispetto alle Righe**: Il determinante è una funzione lineare rispetto a ciascuna delle sue righe. Se l'i-esima riga $R_i$ di una matrice $A$ è espressa come combinazione lineare di due vettori riga $R$ e $R'$, ovvero $R_i = \alpha R + \alpha' R'$, allora il determinante di $A$ può essere scomposto come segue:
    $$ \det(A) = \alpha \cdot \det(B) + \alpha' \cdot \det(C) $$ 
    dove $B$ è la matrice ottenuta da $A$ sostituendo la riga $R_i$ con $R$, e $C$ è la matrice ottenuta da $A$ sostituendo la riga $R_i$ con $R'$.

### 3. Corollari delle Proprietà Fondamentali

Dalle proprietà precedenti derivano alcuni importanti corollari:

*   **Riga Nulla**: Se una matrice $A$ ha una riga (o una colonna) interamente composta da zeri, il suo determinante è nullo. Questo segue dalla proprietà di multilinearità, scrivendo la riga nulla come $R_i = 0 \cdot R_i$. Di conseguenza $\det(A) = 0 \cdot \det(A) = 0$.
    $$ \det(A) = 0 $$ 
*   **Righe Uguali**: Se una matrice $A$ ha due righe (o due colonne) identiche, il suo determinante è nullo. Infatti, scambiando le due righe identiche, la matrice $A$ non cambia, quindi $\det(A') = \det(A)$. D'altra parte, per la proprietà dello scambio di righe, si ha $\det(A') = -\det(A)$. L'unico numero che è uguale al suo opposto è lo zero, quindi:
    $$ \det(A) = 0 $$ 

### 4. Determinante e Operazioni Elementari di Gauss-Jordan

Le proprietà del determinante permettono di analizzare come esso varia in seguito all'applicazione delle tre [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Scopo del Gioco e Regole: Le Operazioni Elementari di Riga|operazioni elementari di riga]]:

1.  **Scambio di righe ($R_i \leftrightarrow R_j$)**: Il determinante cambia segno: $\det(A') = -\det(A)$.
2.  **Moltiplicazione di una riga per uno scalare non nullo ($R_i \to kR_i$)**: Il determinante viene moltiplicato per lo stesso scalare $k$: $\det(A') = k \cdot \det(A)$.
3.  **Combinazione lineare ($R_i \to R_i + kR_j$)**: Il determinante rimane invariato. Questo si dimostra usando la multilinearità, che scompone il determinante in $\det(A) + k \cdot \det(A'')$, dove $A''$ è una matrice con due righe uguali (la riga $R_j$ appare sia alla posizione $i$ che alla posizione $j$), e quindi il suo determinante è nullo.
    $$ \det(A') = \det(A) $$ 

Queste relazioni forniscono una strategia di calcolo: è possibile utilizzare l'[[Geometria e Algebra/Algoritmo di Eliminazione di Gauss Jordan|algoritmo di Gauss-Jordan]] per ridurre una matrice a una forma a scala (quindi [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Tipologie di Matrici Speciali|matrice triangolare]]), tenendo traccia delle variazioni del determinante a ogni operazione. Poiché il determinante di una matrice triangolare è semplicemente il prodotto degli elementi sulla sua diagonale principale, si può risalire facilmente al determinante della matrice originale.

### 5. Teorema di Binet

Il teorema di Binet stabilisce la relazione fondamentale tra il determinante e il [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Il Prodotto Riga per Colonna|prodotto di matrici]]. Date due matrici quadrate $A$ e $B$ della stessa dimensione, il determinante del loro prodotto è uguale al prodotto dei loro determinanti.

$$ \det(A \cdot B) = \det(A) \cdot \det(B) $$ 

La dimostrazione di questo teorema si basa sulla scomposizione delle righe della matrice prodotto $A \cdot B$ e sull'applicazione iterativa della proprietà di multilinearità. Le righe della matrice $A \cdot B$ sono combinazioni lineari delle righe di $B$, con coefficienti dati dalle entrate di $A$. Scomponendo il determinante riga per riga, si ottiene una complessa somma di determinanti. Molti termini di questa somma si annullano (quelli in cui una riga di $B$ compare più volte). I termini non nulli corrispondono esattamente alle permutazioni delle righe di $B$, portando alla formula del determinante di $A$ moltiplicato per il determinante di $B$.

### 6. Relazione tra Determinante e Invertibilità

Il teorema di Binet è lo strumento chiave per stabilire il più importante criterio di invertibilità per le matrici quadrate.
Se una matrice $A$ è [[03 - Rango, Invertibilità delle Matrici e Permutazioni|invertibile]], esiste la sua [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Algoritmo per il Calcolo della Matrice Inversa|inversa $A^{-1}$]] tale che $A \cdot A^{-1} = I$, dove $I$ è la [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#La Matrice Identità come Elemento Neutro|matrice identità]].

Applicando il teorema di Binet, si ha:
$$ \det(A \cdot A^{-1}) = \det(A) \cdot \det(A^{-1}) $$ 
Poiché $\det(I) = 1$, si ottiene la relazione:
$$ \det(A) \cdot \det(A^{-1}) = 1 $$ 

Da questa equazione si deducono due risultati cruciali:
1.  Se una matrice $A$ è invertibile, il suo determinante deve essere **diverso da zero**: $\det(A) \neq 0$.
2.  Il determinante della matrice inversa è il **reciproco** del determinante della matrice originale: $\det(A^{-1}) = \frac{1}{\det(A)} = (\det(A))^{-1}$.

Questo porta al seguente corollario che unifica i concetti di rango, determinante e invertibilità:

**Teorema di equivalenza:** Per una matrice quadrata $A$ di ordine $n$, le seguenti tre affermazioni sono equivalenti:
1.  $A$ è [[03 - Rango, Invertibilità delle Matrici e Permutazioni|invertibile]].
2.  Il [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango di $A$]] è massimale, ovvero $Rk(A) = n$.
3.  Il determinante di $A$ è non nullo, ovvero $\det(A) \neq 0$.

## Teorema di Laplace per il Calcolo del Determinante

Mentre la definizione formale è computazionalmente impraticabile per matrici più grandi di $3 \times 3$, il teorema di Laplace fornisce un metodo ricorsivo ed efficiente in molti casi pratici.

### 1. Sottomatrici, Minori e Cofattori

Data una matrice quadrata $A$ di dimensione $n \times n$:
- Si definisce **[[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Sottomatrici|sottomatrice]]** $A_{ij}$ la matrice di dimensione $(n-1) \times (n-1)$ ottenuta da $A$ eliminando l'i-esima riga e la j-esima colonna.
- Si definisce **minore** di $A$ relativo agli indici $(i, j)$, denotato con $m_{ij}(A)$ o $|A_{ij}|$, il determinante della sottomatrice $A_{ij}$.
- Si definisce **cofattore** (o complemento algebrico) dell'elemento $a_{ij}$, denotato con $a_{ij}^*$, il minore con il suo segno di posizione:
  $$ a_{ij}^* = (-1)^{i+j} m_{ij} = (-1)^{i+j} |A_{ij}| $$

### 2. Enunciato del Teorema

Il teorema di Laplace, o **sviluppo di Laplace**, afferma che il determinante di una matrice può essere calcolato come la somma dei prodotti degli elementi di una qualsiasi riga (o colonna) per i rispettivi cofattori.

*   **Sviluppo lungo la riga i-esima**: Fissata una qualsiasi riga $i$ (con $1 \le i \le n$), il determinante di $A$ è dato da:
    $$ \det(A) = \sum_{j=1}^{n} a_{ij} \cdot a_{ij}^* = \sum_{j=1}^{n} a_{ij} \cdot (-1)^{i+j} \cdot |A_{ij}| $$ 
*   **Sviluppo lungo la colonna j-esima**: Fissata una qualsiasi colonna $j$ (con $1 \le i \le n$), il determinante di $A$ è dato da:
    $$ \det(A) = \sum_{i=1}^{n} a_{ij} \cdot a_{ij}^* = \sum_{i=1}^{n} a_{ij} \cdot (-1)^{i+j} \cdot |A_{ij}| $$ 

### 3. Applicazione Pratica e Matrice Aggiunta

Il teorema di Laplace è particolarmente potente quando una matrice ha una riga o una colonna con molti zeri. Scegliendo di sviluppare lungo quella linea, molti termini della sommatoria si annullano, semplificando drasticamente il calcolo.

I cofattori sono anche alla base della costruzione di una matrice molto importante:
- La **matrice dei cofattori** di $A$ è la matrice che ha come entrate i cofattori $a_{ij}^*$.
- La **[[Matrice Aggiunta|matrice aggiunta]]** di $A$, denotata con $A^*$ o $\text{adj}(A)$, è definita come la **trasposta** della matrice dei cofattori:
  $$ A^* = \text{adj}(A) = (a_{ij}^*)^t $$

Usando lo sviluppo di Laplace si può dimostrare la seguente proposizione fondamentale:
$$ A \cdot A^* = \det(A) \cdot I_n $$

Da questa relazione, se $\det(A) \neq 0$, si ricava una formula esplicita per calcolare la matrice inversa:
$$ A^{-1} = \frac{1}{\det(A)} A^* $$
Questa formula, sebbene computazionalmente onerosa per matrici di grandi dimensioni, è di grande importanza teorica e molto utile per matrici piccole (es. $2 \times 2$ o $3 \times 3$).