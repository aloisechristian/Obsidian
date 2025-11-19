# Teorema Fondamentale e Criteri di Diagonalizzabilità

La presente trattazione analizza le condizioni necessarie e sufficienti affinché una [[Geometria e Algebra/01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Tipologie di Matrici Speciali|matrice quadrata]] (o un endomorfismo associato) sia diagonalizzabile. Viene discusso il legame tra diagonalizzabilità e l'esistenza di una [[Geometria e Algebra/08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Definizione di Base|base]] di autovettori, fornendo la dimostrazione formale e introducendo i concetti di molteplicità algebrica e geometrica per definire un criterio operativo.

## 1. Teorema di Caratterizzazione della Diagonalizzabilità

Sia $A$ una matrice quadrata di ordine $N$ a coefficienti in un campo $\mathbb{K}$ (es. $\mathbb{R}$). Siano $\lambda_1, \dots, \lambda_R$ gli autovalori distinti di $A$. Per ogni $i$, sia $\mathcal{B}_i$ una base dell'autospazio $V_{\lambda_i}$ relativo all'autovalore $\lambda_i$. Definiamo $\mathcal{B}$ come l'unione di tutte le basi degli autospazi:
$$\mathcal{B} = \bigcup_{i=1}^R \mathcal{B}_i$$

**Teorema:** La matrice $A$ è diagonalizzabile se e soltanto se l'insieme $\mathcal{B}$ costituisce una **base** per lo [[Geometria e Algebra/06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|spazio vettoriale]] $\mathbb{R}^N$.

In tal caso, la matrice diagonale $D$ [[Geometria e Algebra/13 - Matrici Associate e Cambiamento di Base#Definizione di Matrici Simili|simile]] ad $A$ avrà sulla diagonale gli autovalori, ripetuti secondo la loro molteplicità, e la matrice di passaggio $P$ (spesso indicata come $B$ nel contesto della dimostrazione) avrà come colonne i vettori della base $\mathcal{B}$.

## 2. Dimostrazione del Teorema

La dimostrazione si articola nelle due implicazioni logiche.

### 2.1 Implicazione Sufficiente ($\Leftarrow$)

**Ipotesi:** $\mathcal{B} = \{\mathbf{b}_1, \dots, \mathbf{b}_N\}$ è una [[Geometria e Algebra/08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Definizione di Base|base]] di $\mathbb{R}^N$ composta da autovettori di $A$.

Poiché ogni colonna $\mathbf{b}_i$ della matrice $B$ è un autovettore, esiste uno scalare $d_i$ (autovalore corrispondente) tale che:
$$A \cdot \mathbf{b}_i = d_i \cdot \mathbf{b}_i$$

Costruiamo il [[Geometria e Algebra/02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Il Prodotto Riga per Colonna|prodotto matriciale]] considerando tutte le colonne contemporaneamente. Sia $B$ la matrice le cui colonne sono i vettori della base $\mathcal{B}$. Il prodotto $A \cdot B$ risulta:
$$\begin{aligned} A \cdot [\mathbf{b}_1 | \dots | \mathbf{b}_N] &= [A\mathbf{b}_1 | \dots | A\mathbf{b}_N] \\ &= [d_1 \mathbf{b}_1 | \dots | d_N \mathbf{b}_N] \\ &= B \cdot D \end{aligned}$$

dove $D = \text{diag}(d_1, \dots, d_N)$. Poiché $B$ è costruita con vettori di una base, essa è **invertibile** (il suo [[Geometria e Algebra/04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#Relazione tra Determinante e Invertibilità|determinante è non nullo]]). Moltiplicando a destra per $B^{-1}$, otteniamo:
$$B^{-1} \cdot A \cdot B = D$$
Questa è la definizione di diagonalizzabilità.

> [!NOTE] Collegamento con il Cambio di Base
> La matrice $B$ funge da [[Geometria e Algebra/13 - Matrici Associate e Cambiamento di Base#Matrici di Cambiamento di Base|matrice di cambiamento di base]] dalla base di autovettori $\mathcal{B}$ alla base canonica. La relazione $D = B^{-1} A B$ rappresenta l'endomorfismo nella nuova base $\mathcal{B}$ dove la matrice associata diventa diagonale.

### 2.2 Implicazione Necessaria ($\Rightarrow$)

**Ipotesi:** $A$ è diagonalizzabile.

Per definizione, esiste una matrice invertibile $B$ e una matrice diagonale $D$ tali che $B^{-1} \cdot A \cdot B = D$. Moltiplicando a sinistra per $B$, si ha $A \cdot B = B \cdot D$.
Sia $\mathbf{b}_i$ l'$i$-esima colonna di $B$ e $d_i$ l'$i$-esimo elemento diagonale di $D$. Uguagliando le colonne corrispondenti nel prodotto matriciale, otteniamo:
$$A \cdot \mathbf{b}_i = d_i \cdot \mathbf{b}_i$$

Questo implica che ogni colonna $\mathbf{b}_i$ è un autovettore di $A$ relativo all'autovalore $d_i$. Poiché la matrice $B$ è invertibile per ipotesi, il suo determinante è non nullo e le sue colonne sono [[Geometria e Algebra/07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Indipendenza Lineare|linearmente indipendenti]]. Essendo $N$ vettori linearmente indipendenti in uno spazio di dimensione $N$, essi formano una [[Geometria e Algebra/08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Corollario Proprietà Equivalenti per una Base|base]] di $\mathbb{R}^N$. Pertanto, esiste una base di autovettori.

## 3. Molteplicità Algebrica e Geometrica

Per applicare il teorema senza calcolare esplicitamente le basi ogni volta, si introducono due definizioni fondamentali per ogni autovalore $\lambda$:

* **Molteplicità Algebrica ($m_\lambda$):** Il numero di volte che $\lambda$ appare come radice del **polinomio caratteristico** $p(\lambda) = \det(A - \lambda I)$. Corrisponde al massimo esponente $k$ tale che $(\lambda - x)^k$ divide $p(x)$. (Vedi [[Geometria e Algebra/04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#1. Richiamo della Definizione di Determinante|Calcolo del Determinante]]).
* **Molteplicità Geometrica ($g_\lambda$):** La [[Geometria e Algebra/08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Definizione di Dimensione|dimensione]] dell'autospazio associato a $\lambda$, che coincide con il [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Nucleo (Kernel)|nucleo]] della matrice singolare $(A - \lambda I)$:
    $$g(\lambda) = \dim(V_\lambda) = \dim(\ker(A - \lambda I)) = N - \text{rg}(A - \lambda I)$$

> [!info] Lemma Fondamentale
> Per ogni autovalore $\lambda$, vale la disuguaglianza:
> $$1 \le g(\lambda) \le m(\lambda)$$

## 4. Criterio Operativo di Diagonalizzabilità

Dal teorema precedente deriva che $A$ è diagonalizzabile se e solo se la somma delle dimensioni degli autospazi (molteplicità geometriche) è pari alla dimensione dello spazio $N$:
$$\sum_{i} g(\lambda_i) = N$$

Considerando le proprietà delle molteplicità, si giunge al seguente **Corollario (Criterio Pratico)**.
Una matrice $A$ di ordine $N$ è diagonalizzabile se e soltanto se sono soddisfatte contemporaneamente le seguenti due condizioni:

1. **Condizione sul Polinomio Caratteristico (Scomponibilità):** Il polinomio caratteristico deve essere interamente scomponibile nel campo di riferimento (tutte le radici devono appartenere a $\mathbb{K}$, es. reali in $\mathbb{R}$), ovvero la somma delle molteplicità algebriche deve essere $N$:
   $$\sum m(\lambda_i) = N$$
2. **Condizione di Regolarità:** Per ogni autovalore $\lambda_i$, la molteplicità geometrica deve coincidere con la molteplicità algebrica:
    $$g(\lambda_i) = m(\lambda_i) \quad \forall i$$

## 5. Note Applicative e Strategie

* **Autovalori Distinti:** Se una matrice $N \times N$ possiede $N$ autovalori distinti, essa è **automaticamente diagonalizzabile**. Infatti, per ogni autovalore si ha $m(\lambda_i)=1$, che implica $g(\lambda_i)=1$. La somma delle geometriche sarà quindi $N$.
* **Autovalori Coincidenti:** In presenza di autovalori con $m(\lambda) > 1$, è necessario verificare che la dimensione del [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Nucleo o Kernel ($\text{Ker}(f)$ o $f^{-1}(0_W)$)|nucleo]] di $(A - \lambda I)$ sia uguale a $m(\lambda)$. Se $g(\lambda) < m(\lambda)$, la matrice non è diagonalizzabile.
* **Invarianza:** Il polinomio caratteristico e le molteplicità sono invarianti per [[Geometria e Algebra/13 - Matrici Associate e Cambiamento di Base#Definizione di Matrici Simili|similitudine]]; pertanto, la scelta della base iniziale non influenza la diagonalizzabilità intrinseca dell'endomorfismo.

> [!example] Perché ci serve in Ingegneria?
> La diagonalizzazione è fondamentale nell'analisi dei sistemi lineari tempo-invarianti (LTI). Se una matrice di stato $A$ è diagonalizzabile, possiamo "disaccoppiare" le equazioni differenziali del sistema. Inoltre, calcolare l'evoluzione temporale $e^{At}$ o le potenze $A^k$ diventa banale:
> $$A^k = P D^k P^{-1} = P \begin{pmatrix} \lambda_1^k & 0 \\ 0 & \lambda_N^k \end{pmatrix} P^{-1}$$