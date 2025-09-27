# Massimi, Minimi, Maggioranti e Minoranti di un Insieme

In questa lezione, si approfondiscono i concetti di massimo, minimo, estremo superiore ed estremo inferiore, prima per gli insiemi numerici e successivamente estendendoli alle funzioni reali di variabile reale.

## Definizioni per Sottoinsiemi di $\mathbb{R}$

Sia $A$ un sottoinsieme non vuoto di [[03 - Insiemi Numerici, Completezza e Estremo Superiore|$\mathbb{R}$]].

### Massimo e Minimo

- **Massimo**: Un elemento $M \in \mathbb{R}$ è definito **massimo** di $A$, e si scrive $M = \max A$, se soddisfa due condizioni:
  1. $M$ è un maggiorante di $A$: $\forall a \in A, M \geq a$.
  2. $M$ appartiene all'insieme $A$: $M \in A$.

- **Minimo**: Analogamente, un elemento $m \in \mathbb{R}$ è definito **minimo** di $A$, e si scrive $m = \min A$, se soddisfa due condizioni:
  1. $m$ è un minorante di $A$: $\forall a \in A, m \leq a$.
  2. $m$ appartiene all'insieme $A$: $m \in A$.

È fondamentale notare che per essere massimo o minimo di un insieme, un elemento deve non solo essere rispettivamente il più grande o il più piccolo tra tutti gli elementi, ma deve anche **appartenere** all'insieme stesso.

**Proposizione:** Se il massimo (o il minimo) di un insieme esiste, esso è unico.
*Dimostrazione (per il massimo):*
Supponiamo per assurdo che esistano due massimi distinti, $M_1$ e $M_2$. Per definizione di massimo:
1.  $M_1$ è un maggiorante di A e $M_1 \in A$.
2.  $M_2$ è un maggiorante di A e $M_2 \in A$.
Poiché $M_1$ è un maggiorante e $M_2 \in A$, deve valere $M_1 \ge M_2$.
Allo stesso modo, poiché $M_2$ è un maggiorante e $M_1 \in A$, deve valere $M_2 \ge M_1$.
Dalla doppia disuguaglianza $M_1 \ge M_2$ e $M_2 \ge M_1$, per la [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^a37a9a|proprietà asimmetrica]] della relazione d'ordine, segue necessariamente che $M_1 = M_2$.

### Maggioranti, Minoranti e Insiemi Limitati

- Un numero reale $L$ è detto **[[03 - Insiemi Numerici, Completezza e Estremo Superiore#^857746|maggiorante]]** di $A$ se $L \geq a$ per ogni $a \in A$.
- Un numero reale $l$ è detto **[[03 - Insiemi Numerici, Completezza e Estremo Superiore#^d4db6f|minorante]]** di $A$ se $l \leq a$ per ogni $a \in A$.

- Un insieme $A$ si dice **limitato superiormente** se ammette almeno un maggiorante.
- Un insieme $A$ si dice **limitato inferiormente** se ammette almeno un minorante.
- Un insieme si dice **limitato** se è sia limitato superiormente che inferiormente.

### Estremo Superiore (Sup) e Estremo Inferiore (Inf)

#### Ruolo dell'Assioma di Completezza
L'**[[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|assioma di completezza]]** è la proprietà che distingue $\mathbb{R}$ da $\mathbb{Q}$. Una sua conseguenza fondamentale è il seguente teorema:

**Teorema:** Ogni sottoinsieme non vuoto e limitato superiormente di $\mathbb{R}$ ammette un **estremo superiore** (sup), che è il minimo dell'insieme dei suoi maggioranti. Analogamente, ogni sottoinsieme non vuoto e limitato inferiormente di $\mathbb{R}$ ammette un **estremo inferiore** (inf), che è il massimo dell'insieme dei suoi minoranti.

#### Definizione Formale di Estremo Superiore (Sup)
L'estremo superiore di un insieme $A$, denotato con $S = \sup A$, è il **minimo dei maggioranti**. Formalmente, $S$ è caratterizzato da due proprietà:
1. $S$ è un maggiorante di $A$: $\forall a \in A, S \geq a$.
2. Per ogni $\epsilon > 0$, esiste un elemento $a' \in A$ tale che $a' > S - \epsilon$.
   Questa seconda condizione implica che qualsiasi numero più piccolo di $S$ non può essere un maggiorante di $A$, confermando che $S$ è il più piccolo tra tutti i maggioranti.

#### Definizione Formale di Estremo Inferiore (Inf)
L'estremo inferiore di un insieme $A$, denotato con $s = \inf A$, è il **massimo dei minoranti**. Formalmente, $s$ è caratterizzato da due proprietà:
1. $s$ è un minorante di $A$: $\forall a \in A, s \leq a$.
2. Per ogni $\epsilon > 0$, esiste un elemento $a'' \in A$ tale che $a'' < s + \epsilon$.
   Questa seconda condizione implica che qualsiasi numero più grande di $s$ non può essere un minorante di $A$, confermando che $s$ è il più grande tra tutti i minoranti.

### Relazione tra Minimo/Massimo e Infimo/Supremo
- Se un insieme $A$ ammette minimo, allora il suo minimo coincide con il suo estremo inferiore: $\min A = \inf A$.
- Se un insieme $A$ ammette massimo, allora il suo massimo coincide con il suo estremo superiore: $\max A = \sup A$.

Il viceversa non è sempre vero. Un insieme può avere estremo inferiore o superiore senza avere minimo o massimo. Ciò accade quando l'estremo non appartiene all'insieme stesso.

#### Esempi Illustrativi
1.  **Intervallo semiaperto:** Sia $A = [2, 3) = \{x \in \mathbb{R} \mid 2 \le x < 3\}$.
    -   $\inf A = 2$. Poiché $2 \in A$, si ha anche $\min A = 2$.
    -   $\sup A = 3$. Poiché $3 \notin A$, l'insieme non ammette massimo.

2.  **Unione di insiemi:** Sia $B = [-1, 2] \cup \{3\}$.
    -   L'insieme dei minoranti è $(-\infty, -1]$. Il massimo dei minoranti è $-1$. Poiché $-1 \in B$, si ha $\inf B = \min B = -1$.
    -   L'insieme dei maggioranti è $[3, +\infty)$. Il minimo dei maggioranti è $3$. Poiché $3 \in B$, si ha $\sup B = \max B = 3$.

## Estensione dei Concetti alle Funzioni Reali

Poiché il **[[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|codominio]]** (o insieme delle immagini) di una funzione reale $f(X)$ è un insieme numerico, ad esso possono essere applicate tutte le nozioni di limitatezza, massimo, minimo, estremo superiore e inferiore.

Sia $f: X \to Y$ una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]], con $X, Y \subseteq \mathbb{R}$.

### Funzioni Limitate e Illimitate
- Una funzione $f$ si dice **limitata superiormente** se il suo codominio $f(X)$ è un insieme limitato superiormente.
- Una funzione $f$ si dice **non limitata superiormente** se non esistono maggioranti del suo codominio. Formalmente:
  $$ \forall L \in \mathbb{R}, \exists x_k \in X \mid f(x_k) \ge L $$
  In questo caso, per convenzione, si scrive $\sup f = +\infty$.

Analoghe definizioni valgono per una funzione **limitata inferiormente** e **non limitata inferiormente** ($\inf f = -\infty$). Una funzione è **limitata** se è limitata sia superiormente che inferiormente.

### Estremo Superiore e Inferiore di una Funzione

- L'**estremo superiore** di $f$ su $X$ è definito come $M = \sup_{x \in X} f(x) = \sup(f(X))$. Le due proprietà caratteristiche diventano:
  1. $\forall x \in X, f(x) \leq M$.
  2. $\forall \epsilon > 0, \exists x' \in X$ tale che $f(x') > M - \epsilon$.

- L'**estremo inferiore** di $f$ su $X$ è definito come $m = \inf_{x \in X} f(x) = \inf(f(X))$. Le due proprietà caratteristiche diventano:
  1. $\forall x \in X, f(x) \geq m$.
  2. $\forall \epsilon > 0, \exists x'' \in X$ tale che $f(x'') < m + \epsilon$.

### Massimo e Minimo di una Funzione

- Una funzione $f$ è **dotata di massimo** se il suo codominio $f(X)$ ammette massimo. Ciò significa che l'estremo superiore è un valore effettivamente assunto dalla funzione. L'elemento del dominio in cui tale valore viene assunto è detto **punto di massimo**. Formalmente:
  $$ \exists x_{max} \in X \text{ tale che } f(x_{max}) = \sup f $$
  In tal caso, $\max f = f(x_{max})$.

- Una funzione $f$ è **dotata di minimo** se il suo codominio $f(X)$ ammette minimo. L'elemento del dominio in cui tale valore viene assunto è detto **punto di minimo**. Formalmente:
  $$ \exists x_{min} \in X \text{ tale che } f(x_{min}) = \inf f $$
  In tal caso, $\min f = f(x_{min})$.

## Monotonia delle Funzioni

Si definisce il comportamento di una funzione rispetto alla relazione d'ordine nel suo dominio e codominio.
Siano $x_1, x_2 \in X$.

- **Crescente**: $f$ si dice crescente se $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) \leq f(x_2)$.
- **Decrescente**: $f$ si dice decrescente se $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) \geq f(x_2)$.
- **Strettamente Crescente**: $f$ si dice strettamente crescente se $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) < f(x_2)$.
- **Strettamente Decrescente**: $f$ si dice strettamente decrescente se $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) > f(x_2)$.

Una funzione si dice **monotona** se è crescente oppure decrescente. Si dice **strettamente monotona** se è strettamente crescente o strettamente decrescente.