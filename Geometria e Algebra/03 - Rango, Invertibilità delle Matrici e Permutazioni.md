## Introduzione e Obiettivi della Lezione

Nelle lezioni precedenti, la necessità di risolvere sistemi di equazioni lineari in modo efficiente ha motivato l'introduzione delle [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#^1f6aea|matrici]] e delle relative operazioni: trasposizione, somma, prodotto per uno scalare e prodotto righe per colonna. Mentre per le prime operazioni è semplice identificare un'inversa, il concetto di invertibilità rispetto al prodotto righe per colonna è una questione più complessa e fondamentale.

L'obiettivo di questa lezione è stabilire un criterio rigoroso per determinare se una matrice quadrata $A$ sia invertibile e, in caso affermativo, calcolarne la matrice inversa $A^{-1}$. Lo strumento introdotto a tale scopo è stato l'[[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#L'Algoritmo di Eliminazione di Gauss-Jordan|algoritmo di eliminazione di Gauss-Jordan]], che permette di trasformare una qualsiasi matrice nella sua forma a scala ridotta (reduced row echelon form).

---

## Il Rango di una Matrice

Per formalizzare il criterio di invertibilità, introduciamo una delle nozioni più importanti dell'algebra lineare: il **rango** di una matrice.

### Definizione di Rango
Data una matrice $A$ di dimensioni $M \times N$, si definisce **rango** di $A$, denotato con $Rk(A)$ o $rg(A)$, il numero di **pivot** presenti in una sua qualsiasi forma a scala (echelon form). Poiché il passaggio da una forma a scala a una forma a scala ridotta (mediante il passo di Jordan) non altera il numero di pivot, la definizione è consistente.

### Proprietà Fondamentali del Rango
1.  **Limiti del Rango:** Il rango di una matrice $A_{M \times N}$ è sempre un numero intero non negativo compreso tra 0 e il minimo delle sue dimensioni:
    $$0 \le Rk(A) \le \min(M, N)$$
    Questo perché, per definizione di forma a scala, ogni riga e ogni colonna possono contenere al massimo un pivot.

2.  **Rango Nullo:** Il rango di una matrice è zero se e solo se la matrice è la matrice nulla (contenente solo zeri).
    $$Rk(A) = 0 \iff A = O$$

3.  **Rango Massimale:** Una matrice $A$ si dice avere **rango massimale** se il suo rango è uguale al massimo valore possibile, ovvero $Rk(A) = \min(M, N)$.

### Teorema sulla Buona Definizione del Rango
Una potenziale ambiguità nella definizione di rango risiede nel fatto che una matrice può avere diverse forme a scala, a seconda della sequenza di operazioni elementari scelte. Il seguente teorema, che enunciamo senza dimostrazione, risolve questo problema.

**Teorema:**
1.  Il rango di una matrice $A$ è **ben definito**, ovvero non dipende dalla specifica forma a scala a cui si perviene. Tutte le forme a scala di $A$ hanno lo stesso numero di pivot.
2.  Il rango di una matrice è uguale al rango della sua trasposta:
    $$Rk(A) = Rk(A^T)$$

### Esempio di Calcolo del Rango
Si consideri la matrice:
$$A = \begin{pmatrix} 2 & 2 & 4 & 0 \\ 1 & 1 & 1 & 1 \\ 0 & 0 & 1 & 1 \end{pmatrix}$$
Per calcolarne il rango, la riduciamo a una forma a scala:
1.  $R_1 \to \frac{1}{2}R_1$:
    $\begin{pmatrix} 1 & 1 & 2 & 0 \\ 1 & 1 & 1 & 1 \\ 0 & 0 & 1 & 1 \end{pmatrix}$
2.  $R_2 \to R_2 - R_1$:
    $\begin{pmatrix} 1 & 1 & 2 & 0 \\ 0 & 0 & -1 & 1 \\ 0 & 0 & 1 & 1 \end{pmatrix}$
3.  $R_2 \to -R_2$:
    $\begin{pmatrix} 1 & 1 & 2 & 0 \\ 0 & 0 & 1 & -1 \\ 0 & 0 & 1 & 1 \end{pmatrix}$
4.  $R_3 \to R_3 - R_2$:
    $\begin{pmatrix} 1 & 1 & 2 & 0 \\ 0 & 0 & 1 & -1 \\ 0 & 0 & 0 & 2 \end{pmatrix}$
La matrice è ora in forma a scala. I pivot sono gli elementi in posizione (1,1), (2,3) e (3,4). Il loro numero è 3. Pertanto, $Rk(A) = 3$. Poiché le dimensioni della matrice sono $3 \times 4$ e $\min(3, 4) = 3$, la matrice ha **rango massimale**.

---

## Algoritmo per il Calcolo della Matrice Inversa

Il concetto di rango è direttamente collegato all'invertibilità di una matrice quadrata.

**Teorema:** Sia $A$ una matrice quadrata di ordine $N$. Si costruisca la matrice aumentata $[A | I_N]$ di dimensioni $N \times 2N$, dove $I_N$ è la matrice identità di ordine $N$. Sia $[A' | B]$ la forma a scala **ridotta** di $[A | I_N]$ ottenuta tramite l'algoritmo di Gauss-Jordan.
- Se $A' = I_N$, allora $A$ è invertibile e la sua inversa è $A^{-1} = B$.
- Se $A' \neq I_N$, allora $A$ non è invertibile.

### Criterio di Invertibilità basato sul Rango
Dal teorema precedente discende un criterio fondamentale.

**Corollario:** Una matrice quadrata $A$ di ordine $N$ è invertibile se e solo se ha rango massimale, cioè $Rk(A) = N$.

*Dimostrazione intuitiva:* La matrice $A'$ nel teorema è una forma a scala ridotta di $A$. Se $Rk(A) = N$, la sua unica forma a scala ridotta è la matrice identità $I_N$. Pertanto $A' = I_N$ e $A$ è invertibile. Viceversa, se $A$ è invertibile, allora la sua forma ridotta è $A' = I_N$, che ha $N$ pivot, implicando che $Rk(A) = N$.

### Esempi di Calcolo dell'Inversa

**1. Matrice Invertibile**
Calcolare l'inversa di $A = \begin{pmatrix} 2 & 1 \\ 1 & 3 \end{pmatrix}$.
$$[A | I_2] = \left( \begin{array}{cc|cc} 2 & 1 & 1 & 0 \\ 1 & 3 & 0 & 1 \end{array} \right) \xrightarrow{R_1 \leftrightarrow R_2} \left( \begin{array}{cc|cc} 1 & 3 & 0 & 1 \\ 2 & 1 & 1 & 0 \end{array} \right) \xrightarrow{R_2 \to R_2 - 2R_1} \left( \begin{array}{cc|cc} 1 & 3 & 0 & 1 \\ 0 & -5 & 1 & -2 \end{array} \right)$$
A questo punto, la matrice a sinistra è a scala con 2 pivot. Sappiamo che $Rk(A) = 2$ e quindi la matrice è invertibile. Completiamo l'algoritmo:
$$\xrightarrow{R_2 \to -\frac{1}{5}R_2} \left( \begin{array}{cc|cc} 1 & 3 & 0 & 1 \\ 0 & 1 & -\frac{1}{5} & \frac{2}{5} \end{array} \right) \xrightarrow{R_1 \to R_1 - 3R_2} \left( \begin{array}{cc|cc} 1 & 0 & \frac{3}{5} & -\frac{1}{5} \\ 0 & 1 & -\frac{1}{5} & \frac{2}{5} \end{array} \right)$$
La parte sinistra è $I_2$, quindi l'inversa è $A^{-1} = \begin{pmatrix} \frac{3}{5} & -\frac{1}{5} \\ -\frac{1}{5} & \frac{2}{5} \end{pmatrix}$.

**2. Matrice Non Invertibile**
Verificare l'invertibilità di $A = \begin{pmatrix} 1 & 2 \\ 3 & 6 \end{pmatrix}$.
$$[A | I_2] = \left( \begin{array}{cc|cc} 1 & 2 & 1 & 0 \\ 3 & 6 & 0 & 1 \end{array} \right) \xrightarrow{R_2 \to R_2 - 3R_1} \left( \begin{array}{cc|cc} 1 & 2 & 1 & 0 \\ 0 & 0 & -3 & 1 \end{array} \right)$$
La matrice a sinistra è in forma a scala e ha un solo pivot. Il suo rango è 1, che è minore di 2. Pertanto, la matrice $A$ **non è invertibile**.

---

## Verso un Metodo più Efficiente: Il Determinante

Sebbene l'algoritmo di Gauss-Jordan sia un metodo completo, può risultare computazionalmente oneroso. Emerge la necessità di uno strumento più agile per determinare l'invertibilità di una matrice: il **determinante**. La sua definizione formale richiede l'introduzione del concetto di permutazione.

### Introduzione alle Permutazioni

Sia $S = \{1, 2, \dots, n\}$ un insieme finito. Una **permutazione** di $S$ è una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|funzione biettiva]] $\sigma: S \to S$.

- **Notazione:** Una permutazione $\sigma$ si rappresenta con la sequenza delle immagini $(\sigma(1), \sigma(2), \dots, \sigma(n))$. L'insieme di tutte le permutazioni di $n$ elementi si denota con $S_n$.
- **Cardinalità:** Il numero di permutazioni di $n$ elementi è $\#S_n = n!$.
- **Operazioni:** La composizione di due permutazioni è una permutazione, e ogni permutazione ammette un'inversa.

#### Inversioni e Segno di una Permutazione
- **Inversione:** Data $\sigma \in S_n$, una **inversione** è una coppia di indici $(i, j)$ tali che $i < j$ ma $\sigma(i) > \sigma(j)$. Il numero totale di inversioni si indica con $i(\sigma)$.
- **Segno:** Il **segno** di $\sigma$ è $sgn(\sigma) = (-1)^{i(\sigma)}$. Se $sgn(\sigma) = +1$, la permutazione è **pari**; se $sgn(\sigma) = -1$, è **dispari**.
- **Proprietà del Segno:** Per ogni $\sigma, \tau \in S_n$, vale $sgn(\sigma \circ \tau) = sgn(\sigma) \cdot sgn(\tau)$.

### Il Determinante e le Operazioni Elementari
Il determinante è un numero associato a ogni matrice quadrata che ne riassume molte proprietà. La sua utilità nel contesto di Gauss-Jordan deriva dalle seguenti proprietà.
Sia $A$ una matrice quadrata e $A'$ la matrice ottenuta da $A$ tramite un'operazione elementare:
1.  **Scambio di righe ($R_i \leftrightarrow R_j$):** $\det(A') = -\det(A)$.
2.  **Moltiplicazione per scalare ($R_i \to k R_i$):** $\det(A') = k \cdot \det(A)$.
3.  **Combinazione lineare ($R_i \to R_i + k R_j$):** $\det(A') = \det(A)$.

Queste relazioni, che verranno approfondite nella prossima lezione, collegano l'algoritmo di riduzione a scala al calcolo del determinante, fornendo un potente strumento di analisi.