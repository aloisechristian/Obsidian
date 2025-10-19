# Spazi Vettoriali

Il corso entra ora nella sua fase centrale, dedicata allo studio degli **spazi vettoriali**. Questa struttura algebrica è fondamentale per comprendere e gestire insiemi di soluzioni, in particolare quando ci si trova di fronte a infinite soluzioni di un sistema lineare. Invece di selezionare arbitrariamente una soluzione tra le infinite disponibili, l'obiettivo è sviluppare strumenti per analizzare e manipolare l'intero insieme delle soluzioni come un unico oggetto geometrico e algebrico.

### La Struttura di Gruppo Commutativo (o Abeliano)

Il punto di partenza per la definizione di uno spazio vettoriale è la nozione di gruppo commutativo. Un **gruppo commutativo** (o **abeliano**) è una coppia $(V, +, 0)$ costituita da un insieme non vuoto $V$ e un'operazione binaria interna, denotata con $+$, che soddisfa le seguenti quattro proprietà:

1.  **Proprietà Associativa**: $\forall u, v, w \in V$, vale la relazione $(u+v)+w = u+(v+w)$. Questa regola garantisce che la somma sia affidabile: possiamo scrivere `u+v+w` senza ambiguità.
2.  **Esistenza dell'Elemento Neutro**: $\exists 0 \in V$ tale che $\forall v \in V$, si ha $0+v = v+0 = v$. L'elemento neutro fornisce un' "origine", un punto di riferimento fondamentale per lo spazio.
3.  **Esistenza dell'Opposto**: $\forall v \in V, \exists v' \in V$ (chiamato opposto di $v$ e denotato con $-v$) tale che $v+v' = v'+v = 0$. Questa proprietà rende la somma **reversibile** e ci permette di definire la sottrazione ($u - v\ come\ u + (-v)$).
4.  **Proprietà Commutativa**: $\forall v, w \in V$, vale la relazione $v+w = w+v$. Geometricamente, significa che il percorso per arrivare da un punto all'altro è indipendente dall'ordine delle operazioni.

Un insieme che soddisfa solo le prime tre proprietà è detto **gruppo**.

**Esempio:** L'insieme delle [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#^1f6aea|matrici]] $M_{m,n}(\mathbb{R})$ con l'operazione di somma e la matrice nulla come elemento neutro, $(M_{m,n}(\mathbb{R}), +, 0)$, è un gruppo commutativo.

### Definizione di Spazio Vettoriale

Uno **spazio vettoriale** su $\mathbb{R}$ è un gruppo commutativo $(V, +, 0)$ su cui è definita un'ulteriore operazione, chiamata **moltiplicazione per uno scalare**. Questa operazione associa a ogni **scalare** $\lambda \in \mathbb{R}$ e a ogni **vettore** $v \in V$ un nuovo vettore $\lambda \cdot v \in V$.

**Cos'è un "vettore"?** Un vettore non ha una forma predefinita: è semplicemente un membro di un insieme che obbedisce a queste regole. Può essere una n-upla $(x, y, z)$, una matrice, un polinomio o una funzione. La lettera $v$ è una rappresentazione astratta per indicare un oggetto generico che si comporta secondo le regole dello spazio vettoriale.

La struttura completa, per essere uno spazio vettoriale, deve soddisfare le seguenti proprietà:

**Proprietà del Gruppo Commutativo (già viste):**
i. **Associatività della somma**: $\forall u,v,w \in V, (u+v)+w = u+(v+w)$
ii. **Esistenza dell'elemento neutro**: $\exists 0 \in V$ t.c. $\forall v \in V, v+0=v$
iii. **Esistenza dell'opposto**: $\forall v \in V, \exists -v \in V$ t.c. $v+(-v)=0$
iv. **Commutatività della somma**: $\forall v,w \in V, v+w=w+v$

**Proprietà della Moltiplicazione per Scalare:**
v. **Chiusura rispetto alla moltiplicazione per uno scalare**: $\forall \lambda \in \mathbb{R}, \forall v \in V, \lambda \cdot v \in V$. Questa è una proprietà fondamentale: garantisce che le operazioni non ci portino "fuori" dallo spazio.
vi. **Proprietà Distributiva (rispetto alla somma di vettori)**: $\forall \lambda \in \mathbb{R}, \forall v, v' \in V, \lambda(v+v') = \lambda v + \lambda v'$.
vii. **Proprietà Distributiva (rispetto alla somma di scalari)**: $\forall \lambda, \lambda' \in \mathbb{R}, \forall v \in V, (\lambda + \lambda')v = \lambda v + \lambda' v$.
viii. **Proprietà Associativa (mista)**: $\forall \lambda, \lambda' \in \mathbb{R}, \forall v \in V, (\lambda \cdot \lambda')v = \lambda(\lambda'v)$.
ix. **Esistenza dell'elemento neutro per la moltiplicazione**: $\forall v \in V, 1 \cdot v = v$, dove $1$ è l'elemento neutro della moltiplicazione in $\mathbb{R}$.

## Esempi di Spazi Vettoriali

- **I numeri reali $\mathbb{R}$**: L'insieme dei numeri reali $\mathbb{R}$, con le usuali operazioni di addizione e moltiplicazione, forma uno spazio vettoriale su $\mathbb{R}$.
- **I numeri interi $\mathbb{Z}$**: L'insieme dei numeri interi $\mathbb{Z}$ con l'addizione è un gruppo commutativo. Tuttavia, **non è** uno spazio vettoriale su $\mathbb{R}$, poiché non soddisfa la proprietà di chiusura (v). Ad esempio, se si moltiplica l'intero $3$ per lo scalare $\pi \in \mathbb{R}$, si ottiene $3\pi$, che non è un numero intero.
- **Le matrici $M_{m,n}(\mathbb{R})$**: L'insieme delle matrici a $m$ righe e $n$ colonne con coefficienti reali, dotato dell'operazione di somma tra matrici e di moltiplicazione per uno scalare, è uno spazio vettoriale.
- **Lo spazio delle n-uple $\mathbb{R}^n$**: È l'esempio più importante. L'insieme $\mathbb{R}^n$ è definito come l'insieme di tutte le n-uple ordinate di numeri reali: $\mathbb{R}^n = \{(x_1, x_2, \dots, x_n) | x_i \in \mathbb{R} \}$. Le operazioni sono definite componente per componente:
    - **Somma**: $(x_1, \dots, x_n) + (y_1, \dots, y_n) = (x_1+y_1, \dots, x_n+y_n)$.
    - **Moltiplicazione per scalare**: $\lambda(x_1, \dots, x_n) = (\lambda x_1, \dots, \lambda x_n)$.
    Con queste operazioni, $\mathbb{R}^n$ è uno spazio vettoriale. Sebbene formalmente diversi, si noti che $\mathbb{R}^n$ si comporta in modo identico (è *isomorfo*) allo spazio delle matrici riga $M_{1,n}(\mathbb{R})$ e a quello delle matrici colonna $M_{n,1}(\mathbb{R})$.
- **Lo spazio vettoriale banale**: L'insieme contenente solo l'elemento nullo, $\{0\}$, con le operazioni standard, è il più piccolo spazio vettoriale possibile.

## Sottospazi Vettoriali

Un concetto centrale è quello di sottospazio vettoriale: uno "spazio vettoriale contenuto in un altro". Un sottoinsieme non vuoto $W$ di uno spazio vettoriale $V$ è un **sottospazio vettoriale** di $V$ se $W$ stesso è uno spazio vettoriale rispetto alle operazioni di somma e moltiplicazione per scalare ereditate da $V$.
Per verificare se $W$ è un sottospazio, in teoria dovremmo controllare tutte le 9 proprietà di uno spazio vettoriale. Tuttavia, la maggior parte di queste sono **"ereditate" automaticamente** dallo spazio più grande $V$. Proprietà come l'associatività ($(u+v)+w = u+(v+w)$) o la commutatività ($u+v = v+u$) sono "universali": poiché valgono per *tutti* gli elementi di $V$, valgono automaticamente anche per gli elementi di $W$, dato che ogni elemento di $W$ è anche un elemento di $V$.

Le uniche proprietà che non sono ereditate sono quelle di **chiusura**, perché testano se il sottoinsieme $W$ è "stabile" e "autosufficiente". Dobbiamo assicurarci che le operazioni, applicate a elementi di $W$, non producano un risultato che si trovi al di fuori di $W$.
Affinché un sottoinsieme $W \subseteq V$ sia un sottospazio, è sufficiente verificare le due **condizioni di chiusura**:

1.  **Chiusura rispetto alla somma**: $\forall w_1, w_2 \in W$, la loro somma $w_1 + w_2$ appartiene ancora a $W$.
2.  **Chiusura rispetto alla moltiplicazione per scalare**: $\forall \lambda \in \mathbb{R}$ e $\forall w \in W$, il prodotto $\lambda w$ appartiene ancora a $W$.

Queste due condizioni sono molto potenti e implicano che l'elemento neutro $0$ di $V$ appartiene necessariamente a $W$ (scegliendo $\lambda=0$ nella seconda condizione) e che per ogni $w \in W$, anche il suo opposto $-w$ appartiene a $W$ (scegliendo $\lambda=-1$).

Una proposizione equivalente, spesso più rapida per le verifiche, unisce le due condizioni in una:
$W$ è un sottospazio di $V \iff \forall \lambda_1, \lambda_2 \in \mathbb{R}, \forall w_1, w_2 \in W \implies \lambda_1 w_1 + \lambda_2 w_2 \in W$.

**Perché questa proposizione è equivalente?**
L'equivalenza ($\iff$, "se e solo se") significa che le due affermazioni si implicano a vicenda. Dobbiamo dimostrare entrambe le direzioni:

1.  **Dimostrazione che le due condizioni separate implicano quella unica (`⇒`):**
    Assumiamo che $W$ sia chiuso rispetto alla somma e alla moltiplicazione per scalare. Dobbiamo dimostrare che $\lambda_1 w_1 + \lambda_2 w_2 \in W$.
    - Poiché $W$ è chiuso per la moltiplicazione per scalare, se $w_1 \in W$ e $w_2 \in W$, allora anche i vettori $\lambda_1 w_1$ e $\lambda_2 w_2$ devono appartenere a $W$.
    - Ora abbiamo due elementi, $(\lambda_1 w_1)$ e $(\lambda_2 w_2)$, che sono entrambi in $W$.
    - Poiché $W$ è chiuso per la somma, la loro somma $(\lambda_1 w_1) + (\lambda_2 w_2)$ deve appartenere a $W$.
    Questo dimostra la prima implicazione.

2.  **Dimostrazione che la condizione unica implica le due separate (`⇐`):**
    Assumiamo che $\lambda_1 w_1 + \lambda_2 w_2 \in W$ per ogni scelta di scalari e vettori. Questa affermazione universale ci permette di derivare le due condizioni di chiusura scegliendo valori "furbi" per gli scalari:
    - **Per dimostrare la chiusura della somma** ($w_1 + w_2 \in W$):
      Scegliamo $\lambda_1 = 1$ e $\lambda_2 = 1$. La nostra ipotesi garantisce che $(1 \cdot w_1 + 1 \cdot w_2)$ deve essere in $W$. Questo è esattamente $w_1 + w_2$.
    - **Per dimostrare la chiusura della moltiplicazione per scalare** ($\lambda w \in W$):
      Scegliamo $\lambda_1 = \lambda$ (un qualsiasi scalare) e $\lambda_2 = 0$. La nostra ipotesi garantisce che $(\lambda \cdot w_1 + 0 \cdot w_2)$ deve essere in $W$. Questo si semplifica in $\lambda w_1$.
    Questo dimostra l'implicazione inversa.

Avendo provato entrambe le direzioni, l'equivalenza è dimostrata.

### Esempi di Sottospazi

- **Il Nucleo (Kernel) di una Matrice**: L'insieme delle soluzioni $\Sigma_0$ di un sistema lineare omogeneo $A \cdot x = 0$ è un sottospazio vettoriale di $M_{n,1}(\mathbb{R})$. Questo sottospazio è detto **nucleo** o **kernel** della matrice $A$ e si denota con $\Sigma_0 := \ker(A)$.
- **Insiemi di soluzioni di sistemi non omogenei**: L'insieme delle soluzioni di un sistema $A \cdot x = b$ con $b \neq 0$ **non** è un sottospazio vettoriale, poiché non contiene il vettore nullo $0$ (infatti $A \cdot 0 = 0 \neq b$).
- **Sottospazi di $\mathbb{R}^2$**: L'insieme $W = \{(x, 0) | x \in \mathbb{R}\}$ (l'asse x) è un sottospazio di $\mathbb{R}^2$. Infatti, $\forall \lambda_1, \lambda_2 \in \mathbb{R}$ e $\forall (x_1, 0), (x_2, 0) \in W$, si ha:
  $$ \lambda_1(x_1, 0) + \lambda_2(x_2, 0) = (\lambda_1 x_1 + \lambda_2 x_2, 0) \in W $$
  Al contrario, l'insieme $W' = \{(x, 0) | x \ge 0\}$ non è un sottospazio, perché non è chiuso rispetto alla moltiplicazione per scalari negativi (es. $-1 * (1,0) = (-1,0) ∉ W'$).

## Operazioni con i Sottospazi

### Intersezione di Sottospazi

Se $\{W_i\}_{i \in I}$ è una famiglia di sottospazi di $V$, la loro **intersezione** $W = \bigcap_{i \in I} W_i$ è ancora un sottospazio di $V$.
*Dimostrazione:* Siano $\lambda_1, \lambda_2 \in \mathbb{R}$ e $w_1, w_2 \in W$. Per definizione di intersezione, $w_1, w_2 \in W_i$ per ogni $i \in I$. Poiché ogni $W_i$ è un sottospazio, la combinazione lineare $\lambda_1 w_1 + \lambda_2 w_2$ appartiene a ogni $W_i$. Di conseguenza, appartiene anche alla loro intersezione $W$.

### Unione di Sottospazi

L'**unione** $W_1 \cup W_2$ di due sottospazi, in generale, **non è** un sottospazio vettoriale perché non garantisce la chiusura della somma.
*Esempio:* In $\mathbb{R}^2$, si considerino i sottospazi $W_1 = \{(x, 0) | x \in \mathbb{R}\}$ (l'asse x) e $W_2 = \{(0, y) | y \in \mathbb{R}\}$ (l'asse y). Il vettore $v_1 = (1, 0)$ e $v_2 = (0, 1)$ appartengono all'unione. Tuttavia, la loro somma $v_1+v_2 = (1, 1)$ non appartiene all'unione, poiché non si trova su nessuno dei due assi.

### Somma di Sottospazi e Spazio Generato

Per ovviare al problema dell'unione, si introduce il concetto di **spazio generato**.

- Una **combinazione lineare** di elementi di $V$ è una somma finita del tipo $\lambda_1 v_1 + \dots + \lambda_m v_m$ con $\lambda_i \in \mathbb{R}$ e $v_i \in V$.

- Dato un sottoinsieme qualsiasi $S \subseteq V$, il **sottospazio generato da S**, denotato con $\langle S \rangle$, è l'insieme di tutte le possibili combinazioni lineari di elementi di $S$:
$$ \langle S \rangle = \left\{ \sum_{i=1}^m \lambda_i v_i \mid m \in \mathbb{N}, \lambda_i \in \mathbb{R}, v_i \in S \right\} $$
$S$ è l'insieme dei "generatori" (gli ingredienti), mentre $<S>$ è l'insieme di tutto ciò che si può "costruire" con essi. Per costruzione, **$<S>$ è sempre un sottospazio**. Inoltre, è **il più piccolo sottospazio di V che contiene S**.

- La **somma** di due sottospazi $W_1$ e $W_2$ è definita come il sottospazio generato dalla loro unione:
$$ W_1 + W_2 := \langle W_1 \cup W_2 \rangle $$
Questa operazione "ripara" il difetto dell'unione includendo per costruzione tutte le somme incrociate. Si può dimostrare che questo insieme coincide con:
$$ W_1 + W_2 = \{ w_1 + w_2 \ | \ w_1 \in W_1, w_2 \in W_2 \} $$

### Somma Diretta

Se l'intersezione di due sottospazi si riduce al solo vettore nullo, cioè $W_1 \cap W_2 = \{0\}$, allora la loro somma è detta **somma diretta** e si denota con $W_1 \oplus W_2$. L'unicità della scomposizione è la sua proprietà più importante.

**Proposizione:** Un vettore $w \in W_1 \oplus W_2$ si può scrivere in **modo unico** come somma $w = w_1 + w_2$, con $w_1 \in W_1$ e $w_2 \in W_2$.
*Dimostrazione:* Supponiamo per assurdo che esistano due decomposizioni distinte: $w = w_1 + w_2 = u_1 + u_2$.
Riorganizzando, otteniamo $w_1 - u_1 = u_2 - w_2$.
Il membro di sinistra appartiene a $W_1$, quello di destra a $W_2$. L'uguaglianza implica che l'elemento appartiene all'intersezione $W_1 \cap W_2$.
Ma per definizione di somma diretta, l'intersezione contiene solo lo zero, quindi $w_1 - u_1 = 0 \implies w_1 = u_1$. Di conseguenza, anche $u_2 - w_2 = 0 \implies u_2 = w_2$. Le due decomposizioni erano identiche, dimostrando l'unicità.

**Esempio (Somma non diretta):**
Consideriamo in $\mathbb{R}^3$ i sottospazi $W_1 = \langle (1,0,0), (0,1,0) \rangle$ (il piano xy) e $W_2 = \langle (0,1,0), (0,0,1) \rangle$ (il piano yz).
La loro intersezione è $W_1 \cap W_2 = \langle (0,1,0) \rangle$ (l'asse y), che non è `{0}`. La somma non è diretta.
Il vettore $(1,1,1)$ può essere decomposto in infiniti modi, ad esempio:
- $(1,1,1) = (1,1,0) + (0,0,1)$
- $(1,1,1) = (1,0,0) + (0,1,1)$
L'ambiguità deriva dal fatto che l'elemento dell'intersezione (un vettore sull'asse y) può essere "spostato" da una parte all'altra dell'uguaglianza. L'unicità della decomposizione è persa.