# Basi di Spazi Vettoriali: Riepilogo e Approfondimenti

## Definizione di Base

Torniamo sul concetto fondamentale di **base** di uno [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|spazio vettoriale]], una nozione cruciale per descriverne la struttura intrinseca. Una base può essere pensata come il più piccolo insieme di "mattoni" fondamentali con cui è possibile costruire ogni singolo elemento dello spazio.

Sia $V$ uno spazio vettoriale e $B$ un suo sottoinsieme. Diciamo che $B$ è una **base** di $V$ se soddisfa simultaneamente due proprietà:
1.  $B$ è un **insieme di generatori** per $V$. Questo significa che ogni vettore $v \in V$ può essere scritto come [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|combinazione lineare]] di elementi di $B$. In altre parole, $B$ è "sufficientemente grande" da poter generare l'intero spazio. Matematicamente: $\text{span}(B) = V$.
2.  $B$ è **linearmente indipendente**. Questo garantisce che non ci siano vettori superflui o ridondanti nell'insieme. Ogni vettore in $B$ fornisce un'informazione direzionale unica e insostituibile. In altre parole, $B$ è "sufficientemente piccolo" da essere un insieme efficiente di generatori.

Una delle conseguenze più importanti di questa definizione è che **ogni vettore dello spazio può essere espresso come combinazione lineare dei vettori della base in modo unico**.

L'esempio canonico è la **base standard** (o canonica) dello spazio vettoriale $\mathbb{R}^n$, costituita dai vettori $e_1 = (1, 0, \dots, 0)$, $e_2 = (0, 1, \dots, 0)$, fino a $e_n = (0, 0, \dots, 1)$.

### Esempi di Basi in Altri Spazi Vettoriali

Il concetto di base si estende a tutti gli spazi vettoriali. Consideriamo lo spazio delle matrici $M_{2,2}(\mathbb{R})$, i cui elementi sono della forma:
$$\begin{pmatrix} a & b \\ c & d \end{pmatrix}, \quad a,b,c,d \in \mathbb{R}$$
Una base per questo spazio è data dall'insieme di matrici:
$$B = \left\{ \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}, \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}, \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}, \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} \right\}$$
Questo insieme è una base perché:
- **Genera lo spazio:** Qualsiasi matrice $\begin{pmatrix} a & b \\ c & d \end{pmatrix}$ può essere scritta come combinazione lineare degli elementi di $B$:
$$a \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} + b \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix} + c \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix} + d \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}$$
- **È linearmente indipendente:** Una loro combinazione lineare che dà la matrice nulla implica che tutti i coefficienti devono essere nulli.
$$ \alpha_1 \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} + \alpha_2 \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix} + \alpha_3 \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix} + \alpha_4 \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix} \implies \begin{pmatrix} \alpha_1 & \alpha_2 \\ \alpha_3 & \alpha_4 \end{pmatrix} = \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix} \implies \alpha_1=\alpha_2=\alpha_3=\alpha_4=0$$

Poiché la base è composta da 4 elementi, la **dimensione** di $M_{2,2}(\mathbb{R})$ è 4. Generalizzando, la dimensione dello spazio delle matrici $M_{m,n}(\mathbb{R})$ è $m \times n$.

## Proprietà delle Basi in Spazi di Dimensione Finita

### Corollario: Proprietà Equivalenti per una Base

Sia $V$ uno spazio vettoriale di dimensione finita $\dim(V) = n$, e sia $S = \{s_1, \dots, s_n\}$ un insieme di esattamente $n$ vettori. Le seguenti affermazioni sono equivalenti:
1.  $S$ è linearmente indipendente.
2.  $S$ genera $V$.
3.  $S$ è una base di $V$.

Questo corollario è estremamente utile: se conosciamo la dimensione dello spazio, per verificare se un insieme di $n$ vettori è una base, è sufficiente controllare una sola delle due proprietà (indipendenza lineare o generazione).

**Dimostrazione (2 $\implies$ 3):**
- **Ipotesi:** $\dim(V)=n$, $S=\{s_1, ..., s_n\}$ e $S$ genera $V$.
- **Tesi:** $S$ è una base di $V$.

Per dimostrare che $S$ è una base, dobbiamo solo provare che è linearmente indipendente. Procediamo per [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|assurdo]], supponendo che $S$ sia linearmente dipendente. Per una proposizione precedente, se un insieme di generatori è linearmente dipendente, allora esiste almeno un vettore che può essere scritto come combinazione lineare degli altri. Possiamo rimuovere tale vettore senza alterare lo spazio generato. A meno di riordinare gli elementi, supponiamo che $s_n$ sia combinazione lineare di $\{s_1, \dots, s_{n-1}\}$. Allora, l'insieme $S' = \{s_1, \dots, s_{n-1}\}$ genera ancora $V$.

Abbiamo quindi trovato un insieme di $n-1$ generatori per $V$. Tuttavia, poiché $\dim(V) = n$, esiste una base di $V$ con $n$ elementi. Per il lemma di Steinitz, il numero di elementi in un insieme di generatori deve essere sempre maggiore o uguale al numero di elementi in un qualsiasi insieme linearmente indipendente (come una base). Questo implicherebbe $n-1 \ge n$, che è un assurdo. L'assurdo deriva dall'aver supposto che $S$ fosse linearmente dipendente. Pertanto, $S$ deve essere linearmente indipendente. Poiché genera già $V$ per ipotesi, $S$ è una base.

### Corollario: Dimensione di un Sottospazio

Sia $V$ uno spazio vettoriale di dimensione $n$ e $W$ un suo sottospazio. Allora:
- $\dim(W) \le \dim(V) = n$.
- $\dim(W) = n \iff W = V$.

In altre parole, un sottospazio proprio ha sempre dimensione strettamente minore dello spazio che lo contiene.

### Proposizione: Completamento a una Base

Mentre da un insieme di generatori si può sempre *estrarre* una base, un insieme linearmente indipendente può essere *completato* a una base.

Sia $V$ uno spazio vettoriale di $\dim(V)=n$ e sia $S = \{v_1, \dots, v_r\}$ un insieme di vettori linearmente indipendenti in $V$ (con $r \le n$). Allora esistono $n-r$ vettori $v_{r+1}, \dots, v_n$ tali che l'insieme $\{v_1, \dots, v_r, v_{r+1}, \dots, v_n\}$ sia una base di $V$.

**Dimostrazione (schizzo):**
1.  Se $r=n$, per il corollario precedente, $S$ è già una base e abbiamo finito.
2.  Se $r < n$, $S$ non può essere una base. Poiché è linearmente indipendente per ipotesi, deve essere la proprietà di generazione a mancare. Dunque, $\text{span}(S) \subsetneq V$.
3.  Ciò significa che esiste un vettore $v_{r+1} \in V$ tale che $v_{r+1} \notin \text{span}(S)$.
4.  L'insieme $S' = S \cup \{v_{r+1}\} = \{v_1, \dots, v_r, v_{r+1}\}$ è ancora linearmente indipendente.
5.  Ora abbiamo un insieme di $r+1$ vettori linearmente indipendenti. Se $r+1=n$, abbiamo finito. Altrimenti, si ripete il procedimento fino a ottenere un insieme di $n$ vettori linearmente indipendenti, che sarà una base per $V$.

## Dimensione, Somma e Intersezione di Sottospazi

### La Formula di Grassmann

Dati due sottospazi $W_1$ e $W_2$ di uno spazio vettoriale $V$, la dimensione della loro somma non è semplicemente la somma delle loro dimensioni. La relazione corretta è data dalla **Formula di Grassmann**:
$$\dim(W_1 + W_2) = \dim(W_1) + \dim(W_2) - \dim(W_1 \cap W_2)$$
Questa formula è analoga al principio di inclusione-esclusione per la cardinalità degli insiemi. Il termine $\dim(W_1 \cap W_2)$ corregge il "doppio conteggio" dei vettori che appartengono a entrambi i sottospazi, che altrimenti verrebbero contati sia nella base di $W_1$ sia in quella di $W_2$.

## Complemento Diretto di un Sottospazio

### Proposizione: Esistenza del Complemento Diretto

Sia $V$ uno spazio vettoriale di dimensione finita e $W$ un suo sottospazio. Allora esiste (almeno) un sottospazio $W'$, detto **complemento** di $W$ in $V$, tale che:
$$V = W \oplus W'$$
Ricordiamo che la [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma Diretta|somma diretta]] $W \oplus W'$ implica due condizioni: $V = W+W'$ e $W \cap W' = \{\vec{0}\}$. Il complemento diretto non è unico.

**Dimostrazione:**
1.  Sia $\dim(V)=n$ e $\dim(W)=r$ (con $r \le n$).
2.  Sia $C=\{v_1, \dots, v_r\}$ una base di $W$.
3.  Per la proposizione sul completamento, possiamo estendere $C$ a una base di $V$ aggiungendo $n-r$ vettori: $B = \{v_1, \dots, v_r, w_1, \dots, w_{n-r}\}$ è una base di $V$.
4.  Definiamo $W' = \text{span}\{w_1, \dots, w_{n-r}\}$. Per costruzione, $W'$ ha dimensione $n-r$.
5.  **Verifichiamo la somma:** $W+W' = \text{span}(C \cup \{w_1, \dots, w_{n-r}\}) = \text{span}(B) = V$.
6.  **Verifichiamo l'intersezione:** Sia $u \in W \cap W'$. Allora $u$ può essere scritto sia come combinazione lineare della base di $W$ sia della base di $W'$:
    $$u = \sum_{i=1}^{r} \lambda_i v_i = \sum_{j=1}^{n-r} \mu_j w_j$$
    Questo porta all'equazione: $\sum_{i=1}^{r} \lambda_i v_i - \sum_{j=1}^{n-r} \mu_j w_j = \vec{0}$.
    Poiché i vettori $\{v_i, w_j\}$ formano la base $B$ di $V$, sono linearmente indipendenti. L'unica combinazione lineare che dà il vettore nullo è quella con tutti i coefficienti nulli. Dunque, tutti i $\lambda_i$ e $\mu_j$ sono zero, il che implica $u = \vec{0}$.
7.  Pertanto, $W \cap W' = \{\vec{0}\}$ e la somma è diretta.

## Rappresentazione dei Sottospazi di $\mathbb{R}^n$

Ci concentriamo ora sugli aspetti pratici della manipolazione dei sottospazi di $\mathbb{R}^n$.

### Rappresentazioni Parametrica e Cartesiana

Un sottospazio $W \subseteq \mathbb{R}^n$ può essere descritto principalmente in due modi:
1.  **Forma Parametrica:** $W$ è descritto come lo spazio generato da un insieme di vettori $\{v_1, \dots, v_r\}$. Se questi vettori sono una base di $W$, ogni vettore $w \in W$ si scrive come $w = c_1 v_1 + \dots + c_r v_r$, dove i $c_i$ sono i parametri. Questa rappresentazione è equivalente a definire $W$ come lo spazio delle righe (row space) di una matrice $B$ le cui righe sono i vettori generatori: $W = \text{row}(B)$.

2.  **Forma Cartesiana:** $W$ è descritto come l'insieme delle soluzioni di un sistema di equazioni lineari omogeneo $Ax=0$. Questa rappresentazione è equivalente a definire $W$ come il [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Esempi di Sottospazi|nucleo (kernel)]] di una matrice $A$: $W = \ker(A)$.

### Dalla Rappresentazione Parametrica a una Base

Se $W$ è dato come $W = \text{span}\{v_1, \dots, v_r\}$, i generatori forniti potrebbero non essere linearmente indipendenti (e quindi non essere una base).

**Procedimento:**
1.  Costruire una matrice $A$ le cui righe sono i vettori generatori $v_1, \dots, v_r$.
2.  Applicare l'[[Algoritmo di Eliminazione di Gauss Jordan]] per ottenere una matrice a scala per righe $A'$.
3.  Le righe non nulle di $A'$ formano una base per $W$.
4.  La dimensione di $W$ è il numero di righe non nulle, che corrisponde al [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]] della matrice $A$: $\dim(W) = \text{rank}(A)$.

### Dalla Rappresentazione Cartesiana a una Base (e alla Forma Parametrica)

Se $W$ è dato in forma cartesiana, $W = \ker(A)$, per trovare una base (e quindi una forma parametrica) si risolve il [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Sistemi Omogenei e Struttura delle Soluzioni|sistema omogeneo]] $Ax=0$.

**Procedimento:**
1.  Risolvere il sistema $Ax=0$, tipicamente tramite l'algoritmo di Gauss-Jordan.
2.  Il [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Il Teorema di Rouché-Capelli|teorema di Rouché-Capelli]] stabilisce che il numero di parametri liberi (variabili non dipendenti dai pivot) è $k = n - \text{rank}(A)$, dove $n$ è il numero di colonne di $A$.
3.  Esprimere la soluzione generica del sistema come una combinazione lineare di $k$ vettori, dove ogni vettore corrisponde alla scelta di un parametro libero uguale a 1 e gli altri a 0.
4.  Questi $k$ vettori formano una base per il $\ker(A)$.
5.  La dimensione di $W$ è il numero di parametri liberi: $\dim(W) = n - \text{rank}(A)$.

### Conversione da Forma Cartesiana a Parametrica

Il passaggio dalla forma cartesiana a quella parametrica è un'applicazione diretta del metodo appena descritto. Data $W = \ker(A)$, si risolve il sistema omogeneo $Ax=0$. La base trovata per lo spazio delle soluzioni fornisce i generatori necessari per la rappresentazione parametrica $W = \text{span}\{w_1, \dots, w_k\}$.

