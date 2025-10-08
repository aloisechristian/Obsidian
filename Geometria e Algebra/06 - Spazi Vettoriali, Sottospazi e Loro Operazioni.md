# Spazi Vettoriali

Il corso entra ora nella sua fase centrale, dedicata allo studio degli **spazi vettoriali**. Questa struttura algebrica è fondamentale per comprendere e gestire insiemi di soluzioni, in particolare quando ci si trova di fronte a infinite soluzioni di un sistema lineare. Invece di selezionare arbitrariamente una soluzione tra le infinite disponibili, l'obiettivo è sviluppare strumenti per analizzare e manipolare l'intero insieme delle soluzioni.

### La Struttura di Gruppo Commutativo (o Abeliano)

Il punto di partenza per la definizione di uno spazio vettoriale è la nozione di gruppo commutativo. Un **gruppo commutativo** (o **abeliano**) è una coppia $(V, +, 0)$ costituita da un insieme non vuoto $V$ e un'operazione binaria interna, denotata con $+$, che soddisfa le seguenti quattro proprietà:

1.  **Proprietà Associativa**: $\forall u, v, w \in V$, vale la relazione $(u+v)+w = u+(v+w)$.
2.  **Esistenza dell'Elemento Neutro**: $\exists 0 \in V$ tale che $\forall v \in V$, si ha $0+v = v+0 = v$.
3.  **Esistenza dell'Opposto**: $\forall v \in V, \exists v' \in V$ (chiamato opposto di $v$ e denotato con $-v$) tale che $v+v' = v'+v = 0$.
4.  **Proprietà Commutativa**: $\forall v, w \in V$, vale la relazione $v+w = w+v$.

Un insieme che soddisfa solo le prime tre proprietà è detto **gruppo**.

**Esempio:** L'insieme delle [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#^1f6aea|matrici]] $M_{m,n}(\mathbb{R})$ con l'operazione di somma e la matrice nulla come elemento neutro, $(M_{m,n}(\mathbb{R}), +, 0)$, è un gruppo commutativo.

### Definizione di Spazio Vettoriale

Uno **spazio vettoriale** su $\mathbb{R}$ è un gruppo commutativo $(V, +, 0)$ su cui è definita un'ulteriore operazione, chiamata **moltiplicazione per uno scalare**. Questa operazione associa a ogni **scalare** $\lambda \in \mathbb{R}$ e a ogni **vettore** $v \in V$ un nuovo vettore $\lambda \cdot v \in V$. La struttura completa, per essere uno spazio vettoriale, deve soddisfare le seguenti proprietà:

**Proprietà del Gruppo Commutativo (già viste):**
i. **Associatività della somma**: $\forall u,v,w \in V, (u+v)+w = u+(v+w)$
ii. **Esistenza dell'elemento neutro**: $\exists 0 \in V$ t.c. $\forall v \in V, v+0=v$
iii. **Esistenza dell'opposto**: $\forall v \in V, \exists -v \in V$ t.c. $v+(-v)=0$
iv. **Commutatività della somma**: $\forall v,w \in V, v+w=w+v$

**Proprietà della Moltiplicazione per Scalare:**
v. **Chiusura rispetto alla moltiplicazione per uno scalare**: $\forall \lambda \in \mathbb{R}, \forall v \in V, \lambda \cdot v \in V$.
vi. **Proprietà Distributiva (rispetto alla somma di vettori)**: $\forall \lambda \in \mathbb{R}, \forall v, v' \in V, \lambda(v+v') = \lambda v + \lambda v'$.
vii. **Proprietà Distributiva (rispetto alla somma di scalari)**: $\forall \lambda, \lambda' \in \mathbb{R}, \forall v \in V, (\lambda + \lambda')v = \lambda v + \lambda' v$.
viii. **Proprietà Associativa (mista)**: $\forall \lambda, \lambda' \in \mathbb{R}, \forall v \in V, (\lambda \cdot \lambda')v = \lambda(\lambda'v)$.
ix. **Esistenza dell'elemento neutro per la moltiplicazione**: $\forall v \in V, 1 \cdot v = v$, dove $1$ è l'elemento neutro della moltiplicazione in $\mathbb{R}$.

## Esempi di Spazi Vettoriali

- **I numeri reali $\mathbb{R}$**: L'insieme dei numeri reali $\mathbb{R}$, con le usuali operazioni di addizione e moltiplicazione, forma uno spazio vettoriale su $\mathbb{R}$.
- **I numeri interi $\mathbb{Z}$**: L'insieme dei numeri interi $\mathbb{Z}$ con l'addizione è un gruppo commutativo. Tuttavia, **non è** uno spazio vettoriale su $\mathbb{R}$, poiché non soddisfa la proprietà di chiusura (v). Ad esempio, se si moltiplica l'intero $3$ per lo scalare $\pi \in \mathbb{R}$, si ottiene $3\pi$, che non è un numero intero.
- **Le matrici $M_{m,n}(\mathbb{R})$**: L'insieme delle matrici a $m$ righe e $n$ colonne con coefficienti reali, dotato dell'operazione di somma tra matrici e di moltiplicazione per uno scalare, è uno spazio vettoriale.
- **Lo spazio delle n-uple $\mathbb{R}^n$**: L'insieme $\mathbb{R}^n$ è definito come l'insieme di tutte le n-uple ordinate di numeri reali: $\mathbb{R}^n = \{(x_1, x_2, \dots, x_n) | x_i \in \mathbb{R} \}$. Le operazioni sono definite componente per componente:
    - **Somma**: $(x_1, \dots, x_n) + (y_1, \dots, y_n) = (x_1+y_1, \dots, x_n+y_n)$.
    - **Moltiplicazione per scalare**: $\lambda(x_1, \dots, x_n) = (\lambda x_1, \dots, \lambda x_n)$.
    Con queste operazioni, $\mathbb{R}^n$ è uno spazio vettoriale. Si noti che $\mathbb{R}^n$ può essere identificato con lo spazio delle matrici riga $M_{1,n}(\mathbb{R})$ o con quello delle matrici colonna $M_{n,1}(\mathbb{R})$.
- **Lo spazio vettoriale banale**: L'insieme contenente solo l'elemento nullo, $\{0\}$, con le operazioni standard, è il più piccolo spazio vettoriale possibile.

## Sottospazi Vettoriali

Un concetto centrale è quello di sottospazio vettoriale. Un sottoinsieme non vuoto $W$ di uno spazio vettoriale $V$ è un **sottospazio vettoriale** di $V$ se $W$ stesso è uno spazio vettoriale rispetto alle operazioni di somma e moltiplicazione per scalare ereditate da $V$ (ovvero la restrizione delle operazioni di $V$ a $W$).

Affinché un sottoinsieme $W \subseteq V$ sia un sottospazio, è sufficiente verificare due condizioni di chiusura:

1.  $\forall w_1, w_2 \in W$, la loro somma $w_1 + w_2$ appartiene ancora a $W$.
2.  $\forall \lambda \in \mathbb{R}$ e $\forall w \in W$, il prodotto $\lambda w$ appartiene ancora a $W$.

Queste due condizioni implicano che l'elemento neutro $0$ di $V$ appartiene necessariamente a $W$ e che per ogni $w \in W$, anche il suo opposto $-w$ appartiene a $W$.

Una proposizione equivalente e molto utile per le verifiche è la seguente:
$W$ è un sottospazio di $V \iff \forall \lambda_1, \lambda_2 \in \mathbb{R}, \forall w_1, w_2 \in W \implies \lambda_1 w_1 + \lambda_2 w_2 \in W$.

### Esempi di Sottospazi

- **Il Nucleo (Kernel) di una Matrice**: L'insieme delle soluzioni $\Sigma_0$ di un sistema lineare omogeneo $A \cdot x = 0$ è un sottospazio vettoriale di $M_{n,1}(\mathbb{R})$. Questo sottospazio è detto **nucleo** o **kernel** della matrice $A$ e si denota con $\Sigma_0 := \ker(A)$.
- **Insiemi di soluzioni di sistemi non omogenei**: L'insieme delle soluzioni di un sistema $A \cdot x = b$ con $b \neq 0$ **non** è un sottospazio vettoriale, poiché non contiene il vettore nullo $0$ (infatti $A \cdot 0 = 0 \neq b$).
- **Sottospazi di $\mathbb{R}^2$**: L'insieme $W = \{(x, 0) | x \in \mathbb{R}\}$ è un sottospazio di $\mathbb{R}^2$. Infatti, $\forall \lambda_1, \lambda_2 \in \mathbb{R}$ e $\forall (x_1, 0), (x_2, 0) \in W$, si ha:
  $$ \lambda_1(x_1, 0) + \lambda_2(x_2, 0) = (\lambda_1 x_1 + \lambda_2 x_2, 0) \in W $$
  Al contrario, l'insieme $W' = \{(x, 0) | x \ge 0\}$ non è un sottospazio, perché non è chiuso rispetto alla moltiplicazione per scalari negativi.

## Operazioni con i Sottospazi

### Intersezione di Sottospazi

Se $\{W_i\}_{i \in I}$ è una famiglia di sottospazi di $V$, la loro **intersezione** $W = \bigcap_{i \in I} W_i$ è ancora un sottospazio di $V$.
*Dimostrazione:* Siano $\lambda_1, \lambda_2 \in \mathbb{R}$ e $w_1, w_2 \in W$. Per definizione di intersezione, $w_1, w_2 \in W_i$ per ogni $i \in I$. Poiché ogni $W_i$ è un sottospazio, la combinazione lineare $\lambda_1 w_1 + \lambda_2 w_2$ appartiene a ogni $W_i$. Di conseguenza, appartiene anche alla loro intersezione $W$.

### Unione di Sottospazi

L'**unione** $W_1 \cup W_2$ di due sottospazi, in generale, **non è** un sottospazio vettoriale.
*Esempio:* In $\mathbb{R}^2$, si considerino i sottospazi $W_1 = \{(x, 0) | x \in \mathbb{R}\}$ (l'asse x) e $W_2 = \{(0, y) | y \in \mathbb{R}\}$ (l'asse y). Il vettore $v_1 = (1, 0)$ appartiene a $W_1$ e il vettore $v_2 = (0, 1)$ appartiene a $W_2$, quindi entrambi appartengono all'unione $W_1 \cup W_2$. Tuttavia, la loro somma $v_1+v_2 = (1, 1)$ non appartiene né a $W_1$ né a $W_2$, e quindi non appartiene all'unione. L'unione non è chiusa rispetto alla somma.

### Somma di Sottospazi

Per ovviare al problema dell'unione, si introduce l'operazione di **somma di sottospazi**.
Una **combinazione lineare** di elementi di $V$ è una somma finita del tipo $\lambda_1 v_1 + \dots + \lambda_m v_m$ con $\lambda_i \in \mathbb{R}$ e $v_i \in V$.

Dato un sottoinsieme $S \subseteq V$, il **sottospazio generato da S**, denotato con $\langle S \rangle$, è l'insieme di tutte le possibili combinazioni lineari di elementi di $S$:
$$ \langle S \rangle = \left\{ \sum_{i=1}^m \lambda_i v_i \mid m \in \mathbb{N}, \lambda_i \in \mathbb{R}, v_i \in S \right\} $$
Questo è il più piccolo sottospazio di $V$ che contiene $S$.

La **somma** di due sottospazi $W_1$ e $W_2$ è definita come il sottospazio generato dalla loro unione:
$$ W_1 + W_2 := \langle W_1 \cup W_2 \rangle $$
Si può dimostrare che questo insieme coincide con l'insieme delle somme di un elemento di $W_1$ e un elemento di $W_2$:
$$ W_1 + W_2 = \{ w_1 + w_2 \ | \ w_1 \in W_1, w_2 \in W_2 \} $$
*Dimostrazione (schizzo):* Ogni elemento di $W_1+W_2$ è una combinazione lineare di elementi di $W_1 \cup W_2$. Raggruppando i termini, questa somma può essere riscritta come la somma di un vettore in $W_1$ e un vettore in $W_2$.

### Somma Diretta

Se l'intersezione di due sottospazi si riduce al solo vettore nullo, cioè $W_1 \cap W_2 = \{0\}$, allora la loro somma è detta **somma diretta** e si denota con $W_1 \oplus W_2$.

La proprietà fondamentale della somma diretta è l'**unicità della decomposizione**:
**Proposizione:** Un vettore $w \in W_1 \oplus W_2$ si può scrivere in **modo unico** come somma $w = w_1 + w_2$, con $w_1 \in W_1$ e $w_2 \in W_2$.
*Dimostrazione:* Supponiamo per assurdo che esistano due decomposizioni distinte: $w = w_1 + w_2 = u_1 + u_2$, con $w_1, u_1 \in W_1$ e $w_2, u_2 \in W_2$.
Riorganizzando i termini, otteniamo $w_1 - u_1 = u_2 - w_2$.
Il membro di sinistra appartiene a $W_1$ (perché è un sottospazio), mentre il membro di destra appartiene a $W_2$. Poiché sono uguali, questo elemento appartiene alla loro intersezione: $w_1 - u_1 \in W_1 \cap W_2$.
Ma per definizione di somma diretta, $W_1 \cap W_2 = \{0\}$, quindi $w_1 - u_1 = 0 \implies w_1 = u_1$. Di conseguenza, anche $u_2 - w_2 = 0 \implies u_2 = w_2$. Le due decomposizioni erano in realtà identiche, il che dimostra l'unicità.

**Esempio (Somma non diretta):**
Consideriamo in $\mathbb{R}^3$ i sottospazi $W_1 = \langle (1,0,0), (0,1,0) \rangle = \{(x,y,0) \mid x,y \in \mathbb{R}\}$ e $W_2 = \langle (0,1,0), (0,0,1) \rangle = \{(0,y,z) \mid y,z \in \mathbb{R}\}$.
La loro intersezione è $W_1 \cap W_2 = \langle (0,1,0) \rangle \neq \{0\}$. La somma non è diretta.
Il vettore $(1,1,1)$ può essere decomposto in più modi:
- $(1,1,1) = (1,1,0) + (0,0,1)$, con $(1,1,0) \in W_1$ e $(0,0,1) \in W_2$.
- $(1,1,1) = (1,0,0) + (0,1,1)$, con $(1,0,0) \in W_1$ e $(0,1,1) \in W_2$.
- $(1,1,1) = (1, 1/2, 0) + (0, 1/2, 1)$, con $(1, 1/2, 0) \in W_1$ e $(0, 1/2, 1) \in W_2$.
L'unicità della decomposizione è persa.