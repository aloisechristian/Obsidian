## Richiamo degli Assiomi e Costruzione degli Insiemi Numerici

### 1. Gli Assiomi dei Numeri Reali

Il sistema dei numeri reali, denotato con $\mathbb{R}$, è fondato su un insieme di assiomi che ne definiscono la struttura. Questi assiomi si possono raggruppare in tre categorie principali:

1.  **[[Prodotto Cartesiano e Assiomi dei Numeri Reali#^e1bb55|Assiomi relativi alle operazioni]]:** Definiscono le proprietà delle operazioni di somma (+) e moltiplicazione (·), tra cui:
    *   Proprietà Associativa
    *   Proprietà Commutativa
    *   Proprietà Distributiva
    *   Esistenza degli elementi neutri (0 per la somma, 1 per la moltiplicazione)
    *   Esistenza degli opposti (per ogni numero $a$, esiste $-a$ tale che $a + (-a) = 0$)
    *   Esistenza degli inversi (per ogni numero $a \neq 0$, esiste $a^{-1}$ tale che $a \cdot a^{-1} = 1$)
2.  **[[Prodotto Cartesiano e Assiomi dei Numeri Reali#^6ced7f|Assiomi di Ordinamento]]:** Introducono la relazione d'ordine $\le$ e ne stabiliscono le proprietà di compatibilità con le operazioni algebriche.
3.  **[[Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|Assioma di Completezza]]:** Questo assioma distingue l'insieme dei numeri reali $\mathbb{R}$ dall'insieme dei numeri razionali $\mathbb{Q}$ e garantisce l'assenza di "buchi" sulla retta reale.

### 2. Dagli Assiomi alla Gerarchia degli Insiemi Numerici

A partire dagli assiomi di $\mathbb{R}$, è possibile costruire e caratterizzare i sottoinsiemi numerici fondamentali.

#### 2.1 L'Insieme dei Numeri Naturali ($\mathbb{N}$)
L'elemento neutro della moltiplicazione, $1$, appartiene a $\mathbb{R}$. A partire da esso, possiamo generare un sottoinsieme mediante somme successive:
*   $1 \in \mathbb{R}$
*   $1+1 =: 2 \in \mathbb{R}$
*   $2+1 =: 3 \in \mathbb{R}$
*   ... e così via.

L'insieme così costruito, $\mathbb{N} = \{1, 2, 3, \dots \}$, è l'insieme dei **numeri naturali**. Essendo un sottoinsieme di $\mathbb{R}$, le proprietà associativa, commutativa e distributiva continuano a valere. Tuttavia, $\mathbb{N}$ non soddisfa tutti gli assiomi algebrici:
*   **Manca l'elemento neutro della somma:** $0 \notin \mathbb{N}$. Ciò implica che l'inclusione $\mathbb{N} \subset \mathbb{R}$ è stretta.

#### 2.2 Estensione a $\mathbb{N}_0$ e agli Interi Relativi ($\mathbb{Z}$)
Per ovviare alla mancanza dello 0, possiamo estendere $\mathbb{N}$ includendolo:
$$ \mathbb{N}_0 = \mathbb{N} \cup \{0\} = \{0, 1, 2, 3, \dots \} $$
Ora l'esistenza degli elementi neutri (0 e 1) è soddisfatta. Tuttavia, manca l'esistenza degli opposti: per esempio, per $1 \in \mathbb{N}_0$, non esiste alcun elemento in $\mathbb{N}_0$ che sommato a 1 dia 0. Introduciamo quindi gli opposti di tutti gli elementi non nulli, costruendo l'insieme degli **interi relativi**:
$$ \mathbb{Z} = \{\dots, -3, -2, -1, 0, 1, 2, 3, \dots\} = \{0, \pm 1, \pm 2, \dots \} $$
In $\mathbb{Z}$ sono verificate tutte le proprietà relative alla somma, ma non quelle relative alla moltiplicazione: manca l'esistenza degli inversi per la maggior parte degli elementi (fatta eccezione per 1 e -1).

#### 2.3 L'Insieme dei Numeri Razionali ($\mathbb{Q}$)
Per soddisfare l'assioma dell'esistenza dell'inverso, introduciamo le frazioni. L'insieme dei **numeri razionali** $\mathbb{Q}$ è definito come:
$$ \mathbb{Q} = \left\{ \frac{m}{n} \mid m \in \mathbb{Z}, n \in \mathbb{N} \right\} $$ 
(equivalentemente, $n \in \mathbb{Z} \setminus \{0\}$). Questo insieme soddisfa tutti gli assiomi algebrici e di ordinamento. Abbiamo la seguente catena di inclusioni strette:
$$ \mathbb{N} \subset \mathbb{N}_0 \subset \mathbb{Z} \subset \mathbb{Q} \subseteq \mathbb{R} $$
La questione fondamentale è se l'ultima inclusione sia un'uguaglianza o un'inclusione stretta. La risposta risiede nell'assioma di completezza, che non è soddisfatto da $\mathbb{Q}$.

## L'Incompletezza dell'Insieme dei Numeri Razionali

Per dimostrare che $\mathbb{Q} \neq \mathbb{R}$, è sufficiente mostrare che esiste almeno un numero reale che non è razionale. Un esempio classico è la radice quadrata di 2.

**Proposizione:** Non esiste alcun numero razionale $c \in \mathbb{Q}$ tale che $c^2 = 2$.

Per dimostrare questa proposizione, necessitiamo di alcune definizioni e un lemma preliminare.

### 3.1 Numeri Pari e Dispari
Un numero naturale $n \in \mathbb{N}$ si dice:
*   **Pari**, se è un multiplo di 2, ovvero se esiste $k \in \mathbb{N}$ tale che $n = 2k$.
*   **Dispari**, se non è pari, ovvero se esiste $k \in \mathbb{N}$ tale che $n = 2k-1$ (o $n=2k+1$, a seconda della scelta per il dominio di $k$) (2k-1 è preferibile per includere anche l'uno).

**Lemma:** Se il quadrato di un numero intero $m$, $m^2$, è pari, allora anche $m$ è pari.

*Dimostrazione (per assurdo):*
Supponiamo per assurdo che $m$ sia dispari. Per definizione, esiste un intero $k$ tale che $m = 2k-1$. Calcoliamo il quadrato di $m$:
$$ m^2 = (2k-1)^2 = 4k^2 - 4k + 1 = 2(2k^2 - 2k) + 1 $$ 
Ponendo $K = 2k^2 - 2k$, otteniamo $m^2 = 2K+1$. Questa è la forma di un numero dispari. Ciò contraddice l'ipotesi che $m^2$ sia pari. Pertanto, l'assunzione iniziale che $m$ sia dispari deve essere falsa, e di conseguenza $m$ deve essere pari.

### 3.2 Dimostrazione dell'Irrazionalità di $\sqrt{2}$
Procediamo per assurdo, supponendo che esista un numero razionale $c$ tale che $c^2 = 2$. Se $c \in \mathbb{Q}$, allora può essere scritto come una frazione:
$$ c = \frac{m}{n} $$
con $m \in \mathbb{Z}$ e $n \in \mathbb{N}$. Possiamo assumere, senza perdita di generalità, che la frazione sia ridotta ai minimi termini, ovvero che $m$ e $n$ siano primi tra loro (non abbiano fattori comuni oltre a 1).

Dall'ipotesi $c^2=2$, segue:
$$ \left(\frac{m}{n}\right)^2 = 2 \implies \frac{m^2}{n^2} = 2 \implies m^2 = 2n^2 $$ 
L'ultima equazione mostra che $m^2$ è un numero pari. Per il lemma precedente, se $m^2$ è pari, allora anche $m$ deve essere pari. Possiamo quindi scrivere $m = 2k$ per un qualche intero $k$.

Sostituiamo questa espressione di $m$ nell'equazione $m^2 = 2n^2$:
$$ (2k)^2 = 2n^2 \implies 4k^2 = 2n^2 \implies 2k^2 = n^2 $$ 
Questa nuova equazione mostra che anche $n^2$ è un numero pari, il che implica, sempre per lo stesso lemma, che anche $n$ è pari.

Siamo giunti a una contraddizione: abbiamo dedotto che sia $m$ sia $n$ sono pari. Questo significa che entrambi hanno un fattore comune, 2, il che contraddice la nostra assunzione iniziale che la frazione $\frac{m}{n}$ fosse ridotta ai minimi termini. L'assurdo deriva dall'ipotesi che $c$ sia un numero razionale. Pertanto, **non esiste alcun numero razionale il cui quadrato sia 2**.

Questo dimostra che $\sqrt{2}$ è un numero reale ma non razionale (un **numero irrazionale**), provando che l'inclusione $\mathbb{Q} \subset \mathbb{R}$ è stretta.

## Massimo, Minimo ed Estremi di un Sottoinsieme di $\mathbb{R}$

### 4.1 Massimo e Minimo
Sia $A$ un sottoinsieme di $\mathbb{R}$.
*   Un numero $M \in \mathbb{R}$ è il **massimo** di $A$, denotato con $M = \max A$, se e solo se soddisfa due condizioni:
    1.  $M \ge a$ per ogni $a \in A$ ($M$ è un [[#^857746|maggiorante]]).
    2.  $M \in A$ ($M$ appartiene all'insieme).
*   Un numero $m \in \mathbb{R}$ è il **minimo** di $A$, denotato con $m = \min A$, se e solo se soddisfa due condizioni:
    1.  $m \le a$ per ogni $a \in A$ ($m$ è un [[#^d4db6f|minorante]]).
    2.  $m \in A$ ($m$ appartiene all'insieme).

**Proposizione:** Se il massimo (o il minimo) di un insieme esiste, esso è unico.
*Dimostrazione (per il massimo):*
Supponiamo per assurdo che esistano due massimi distinti, $M_1$ e $M_2$. Per definizione di massimo:
1.  $M_1$ è un maggiorante di A e $M_1 \in A$.
2.  $M_2$ è un maggiorante di A e $M_2 \in A$.
Dato che $M_1$ è un maggiorante e $M_2 \in A$, deve valere $M_1 \ge M_2$.
Dato che $M_2$ è un maggiorante e $M_1 \in A$, deve valere $M_2 \ge M_1$.
Dalla doppia disuguaglianza $M_1 \ge M_2$ e $M_2 \ge M_1$, per la [[Prodotto Cartesiano e Assiomi dei Numeri Reali#^a37a9a|proprietà asimmetrica]], segue necessariamente che $M_1 = M_2$. Ciò dimostra l'unicità.

### 4.2 Maggioranti, Minoranti, Estremo Superiore e Inferiore
*   Un numero $L \in \mathbb{R}$ è un **maggiorante** per $A$ se $L \ge a$ per ogni $a \in A$. ^857746
*   Un numero $l \in \mathbb{R}$ è un **minorante** per $A$ se $l \le a$ per ogni $a \in A$. ^d4db6f

Un insieme si dice **limitato superiormente** se ammette almeno un maggiorante, **limitato inferiormente** se ammette almeno un minorante, e **limitato** se è entrambe le cose.

Una conseguenza fondamentale dell'assioma di completezza è il seguente teorema:
**Teorema:** Ogni sottoinsieme non vuoto e limitato superiormente di $\mathbb{R}$ ammette un **estremo superiore** (sup), che è il minimo dell'insieme dei suoi maggioranti. Analogamente, ogni sottoinsieme non vuoto e limitato inferiormente di $\mathbb{R}$ ammette un **estremo inferiore** (inf), che è il massimo dell'insieme dei suoi minoranti.

L'estremo superiore e inferiore possono essere caratterizzati come segue:
*   $S = \sup A$ se e solo se:
    1.  $S \ge a$ per ogni $a \in A$ ($S$ è un maggiorante).
    2.  Per ogni $\epsilon > 0$, esiste un $a' \in A$ tale che $a' > S - \epsilon$ ($S$ è il più piccolo dei maggioranti).
*   $s = \inf A$ se e solo se:
    1.  $s \le a$ per ogni $a \in A$ ($s$ è un minorante).
    2.  Per ogni $\epsilon > 0$, esiste un $a'' \in A$ tale che $a'' < s + \epsilon$ ($s$ è il più grande dei minoranti).

**Relazione tra Massimo/Minimo e Sup/Inf:**
*   Se un insieme A ammette massimo, allora $\max A = \sup A$.
*   Se un insieme A ammette minimo, allora $\min A = \inf A$.
*   Il viceversa non è sempre vero. Ad esempio, per l'insieme $A = \{x \in \mathbb{R} \mid x > 0\}$, si ha $\inf A = 0$, ma l'insieme non ammette minimo poiché $0 \notin A$.

## Intervalli in $\mathbb{R}$

Siano $a, b \in \mathbb{R}$ con $a < b$. Un **intervallo** è un sottoinsieme di $\mathbb{R}$ che contiene tutti i punti compresi tra due estremi.
*   **Intervallo aperto:** $(a, b) = \{x \in \mathbb{R} \mid a < x < b\}$
*   **Intervallo chiuso:** $[a, b] = \{x \in \mathbb{R} \mid a \le x \le b\}$
*   **Intervalli semiaperti/semichiusi:** $[a, b) = \{x \in \mathbb{R} \mid a \le x < b\}$ e $(a, b] = \{x \in \mathbb{R} \mid a < x \le b\}$

Si definiscono anche **intervalli illimitati**, come ad esempio $[a, +\infty) = \{x \in \mathbb{R} \mid x \ge a\}$.

### Esempi
1.  Sia $A = [2, 3) = \{x \in \mathbb{R} \mid 2 \le x < 3\}$.
    *   $\inf A = 2$. Poiché $2 \in A$, si ha anche $\min A = 2$.
    *   $\sup A = 3$. Poiché $3 \notin A$, l'insieme non ammette massimo.
2.  Sia $B = [-1, 2] \cup \{3\}$.
    *   L'insieme dei minoranti è $(-\infty, -1]$. Il massimo dei minoranti è -1. Poiché $-1 \in B$, si ha $\inf B = \min B = -1$.
    *   L'insieme dei maggioranti è $[3, +\infty)$. Il minimo dei maggioranti è 3. Poiché $3 \in B$, si ha $\sup B = \max B = 3$.