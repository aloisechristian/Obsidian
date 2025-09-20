## Introduzione e Richiami

Nelle lezioni precedenti sono stati introdotti i concetti fondamentali di **insieme**, le operazioni insiemistiche (unione, intersezione, differenza) e la definizione di **funzione** come una legge che associa a ogni elemento $x$ di un insieme di partenza $X$ un unico elemento $y$ di un insieme di arrivo $Y$.

La lezione odierna prosegue approfondendo la teoria degli insiemi con l'introduzione del prodotto cartesiano e, successivamente, stabilisce le fondamenta del calcolo infinitesimale attraverso la presentazione della **struttura assiomatica dell'insieme dei numeri reali** $\mathbb{R}$. Gli assiomi sono proposizioni fondamentali accettate come vere senza dimostrazione, dalle quali discendono, tramite deduzione logica, teoremi, lemmi e corollari che costituiscono l'intera teoria matematica.

## Il Prodotto Cartesiano

### Definizione per due Insiemi

Dati due insiemi non vuoti $A$ e $B$, si definisce **prodotto cartesiano** di $A$ per $B$, e si denota con $A \times B$, l'insieme di tutte le **coppie ordinate** $(a, b)$ dove il primo elemento $a$ appartiene ad $A$ e il secondo elemento $b$ appartiene a $B$. Formalmente:

$$ A \times B = \{ (a, b) \mid a \in A \text{ e } b \in B \} $$

L'attributo "ordinata" sottolinea che la posizione degli elementi all'interno della coppia è significativa. Di conseguenza, il prodotto cartesiano non gode della proprietà commutativa, ovvero in generale $A \times B \neq B \times A$.

### Generalizzazione a n-Insiemi

Il concetto di prodotto cartesiano può essere esteso a un numero finito $n$ di insiemi $A_1, A_2, \dots, A_n$. In tal caso, il prodotto $A_1 \times A_2 \times \dots \times A_n$ è l'insieme di tutte le **n-uple ordinate** $(a_1, a_2, \dots, a_n)$, dove ogni elemento $a_i$ appartiene al corrispondente insieme $A_i$ per $i=1, \dots, n$.

Ad esempio, per tre insiemi $A, B, C$, il prodotto cartesiano è l'insieme delle terne ordinate:

$$ A \times B \times C = \{ (a, b, c) \mid a \in A, b \in B, c \in C \} $$

### Notazione Potenziale

Quando si esegue il prodotto cartesiano di un insieme per se stesso, si adotta una notazione potenziale. Ad esempio:

- $A \times A$ si denota con $A^2$.
- $A \times A \times A$ si denota con $A^3$.
- Il prodotto di $A$ per se stesso $n$ volte si denota con $A^n$.

### Esempio Pratico

Siano dati gli insiemi $A = \{1, 3, 7\}$ e $B = \{2, 5\}$. Il loro prodotto cartesiano $A \times B$ è:

$$ A \times B = \{ (1, 2), (1, 5), (3, 2), (3, 5), (7, 2), (7, 5) \} $$

### Il Grafico di una Funzione

Il prodotto cartesiano è fondamentale per definire il **grafico di una funzione**. Data una funzione $f: X \to Y$, il suo grafico è un sottoinsieme del prodotto cartesiano $X \times Y$ costituito da tutte le coppie $(x, y)$ in cui $y$ è l'immagine di $x$ tramite $f$. Formalmente, il grafico $G_f$ è definito come:

$$ G_f = \{ (x, y) \in X \times Y \mid y = f(x) \} = \{ (x, f(x)) \mid x \in X \} $$

In questo caso, la seconda componente della coppia non è scelta arbitrariamente all'interno di $Y$, ma è determinata univocamente dalla prima componente $x$ e dalla funzione $f$.

## La Struttura Assiomatica dei Numeri Reali ($\mathbb{R}$)

L'insieme dei numeri reali, denotato con $\mathbb{R}$, è definito da un sistema di assiomi che ne stabiliscono le proprietà algebriche, di ordinamento e di completezza. Questi assiomi sono suddivisi in tre gruppi.

### 1. Assiomi Relativi alle Operazioni (Assiomi di Campo)

Su $\mathbb{R}$ sono definite due operazioni binarie interne, l'**addizione** (+) e la **moltiplicazione** ($\cdot$), che associano a ogni coppia di numeri reali $(a, b) \in \mathbb{R}^2$ un unico numero reale, rispettivamente $a+b$ e $a \cdot b$. Queste operazioni soddisfano le seguenti proprietà per ogni $a, b, c \in \mathbb{R}$:

1.  **Proprietà Associativa:**
    - $(a+b)+c = a+(b+c)$
    - $(a \cdot b) \cdot c = a \cdot (b \cdot c)$
2.  **Proprietà Commutativa:**
    - $a+b = b+a$
    - $a \cdot b = b \cdot a$
3.  **Proprietà Distributiva:**
    - $a \cdot (b+c) = a \cdot b + a \cdot c$
4.  **Esistenza degli Elementi Neutri:**
    - Esiste un elemento $0 \in \mathbb{R}$ (zero) tale che $a+0 = a$.
    - Esiste un elemento $1 \in \mathbb{R}$ (uno), con $1 \neq 0$, tale che $a \cdot 1 = a$.
5.  **Esistenza dell'Opposto (Inverso Additivo):**
    - Per ogni $a \in \mathbb{R}$, esiste un elemento $-a \in \mathbb{R}$ (l'opposto di $a$) tale che $a + (-a) = 0$.
6.  **Esistenza dell'Inverso (Inverso Moltiplicativo):**
    - Per ogni $a \in \mathbb{R}$ con $a \neq 0$, esiste un elemento $a^{-1} \in \mathbb{R}$ (l'inverso di $a$) tale che $a \cdot a^{-1} = 1$.

### 2. Assiomi di Ordinamento

In $\mathbb{R}$ è definita una relazione d'ordine totale "minore o uguale" ($\le$) che soddisfa le seguenti proprietà per ogni $a, b, c \in \mathbb{R}$:

7.  **Proprietà di Dicotomia:** Si ha sempre $a \le b$ oppure $b \le a$.
8.  **Proprietà Asimmetrica:** Se $a \le b$ e $b \le a$, allora necessariamente $a=b$.
9.  **Compatibilità con l'Addizione:** Se $a \le b$, allora $a+c \le b+c$ per ogni $c \in \mathbb{R}$. ^84ce53
10. **Compatibilità con la Moltiplicazione (Chiusura dei non-negativi):** Se $a \ge 0$ e $b \ge 0$, allora $a+b \ge 0$ e $a \cdot b \ge 0$.

### 3. Assioma di Completezza

Questo assioma distingue $\mathbb{R}$ dall'insieme dei numeri razionali $\mathbb{Q}$ e garantisce l'assenza di "buchi" sulla retta reale.

- **Definizione di Insiemi Separati:** Due sottoinsiemi non vuoti $A, B \subset \mathbb{R}$ si dicono **separati** se ogni elemento di $A$ è minore o uguale di ogni elemento di $B$, cioè $\forall a \in A, \forall b \in B, a \le b$.
- **Assioma di Completezza:** Dati due sottoinsiemi non vuoti $A, B \subset \mathbb{R}$ separati, esiste almeno un elemento $c \in \mathbb{R}$ (detto **elemento di separazione**) tale che $a \le c \le b$ per ogni $a \in A$ e per ogni $b \in B$.
- **Insiemi Contigui:** Se l'elemento di separazione $c$ è unico, i due insiemi $A$ e $B$ si dicono **contigui**.

***

Dagli assiomi enunciati è possibile dedurre tutte le proprietà algebriche e di ordinamento dei numeri reali.

### Conseguenze degli Assiomi delle Operazioni

- **Regola di Semplificazione per la Somma:** Se $a+b = a+c$, allora $b=c$.
  *Dimostrazione:* Partendo da $b$ e utilizzando l'esistenza dell'elemento neutro (0) e dell'opposto (-a), si ha:
  $b = b+0 = 0+b = (-a+a)+b = -a+(a+b)$.
  Sfruttando l'ipotesi $a+b=a+c$:
  $-a+(a+c) = (-a+a)+c = 0+c = c$. Dunque $b=c$.

- **Regola di Semplificazione per il Prodotto:** Se $a \cdot b = a \cdot c$ e $a \neq 0$, allora $b=c$.
  *Dimostrazione:* Dato che $a \neq 0$, esiste il suo inverso $a^{-1}$. Si ha:
  $b = b \cdot 1 = b \cdot (a \cdot a^{-1}) = (a \cdot b) \cdot a^{-1}$.
  Per ipotesi $a \cdot b = a \cdot c$:
  $(a \cdot c) \cdot a^{-1} = (c \cdot a) \cdot a^{-1} = c \cdot (a \cdot a^{-1}) = c \cdot 1 = c$. Dunque $b=c$.

- **Legge di Annullamento del Prodotto:** $a \cdot b = 0 \iff a=0 \text{ oppure } b=0$.
  *Dimostrazione $(\Leftarrow)$:* Proviamo che $a \cdot 0 = 0$ per ogni numero reale $a$. Consideriamo:
  $a + a \cdot 0 = a \cdot 1 + a \cdot 0 = a \cdot (1+0) = a \cdot 1 = a = a+0$.
  Otteniamo quindi l'uguaglianza $a + a \cdot 0 = a+0$. Per la regola di semplificazione rispetto alla somma, si conclude che $a \cdot 0 = 0$.
  *Dimostrazione $(\Rightarrow)$:* Si supponga $a \cdot b = 0$. Se $a \neq 0$, allora esiste l'inverso $a^{-1}$. Moltiplicando entrambi i membri per $a^{-1}$ si ha:
  $b = b \cdot 1 = b \cdot (a \cdot a^{-1}) = a^{-1} \cdot (a \cdot b) = a^{-1} \cdot 0 = 0$.

- **Inesistenza dell'Inverso di Zero:** Non è possibile definire l'inverso di 0. Se per assurdo esistesse $0^{-1}$, per definizione di inverso si dovrebbe avere $0 \cdot 0^{-1} = 1$. Tuttavia, per la legge di annullamento del prodotto, $0 \cdot 0^{-1} = 0$. Si giungerebbe quindi all'assurdo $1=0$.

- **Unicità dell'Opposto:** L'opposto di un numero reale è unico. Per ogni numero reale $a$ esiste l'opposto $-a$ tale che $a+(-a)=0$. Se supponiamo che esista un altro elemento $b$ tale che $a+b=0$, allora per la legge di semplificazione dell'addizione, partendo da $a+(-a)=a+b$, si ottiene $-a=b$.

- **Unicità dell'Inverso:** L'inverso di un numero reale $a \neq 0$ è unico. Per ogni $a \neq 0$ esiste $a^{-1}$ tale che $a \cdot a^{-1} = 1$. Se supponiamo che esista un altro elemento $b$ tale che $a \cdot b = 1$, allora per la legge di semplificazione del prodotto si ha che $a^{-1}=b$.

- **Opposto dell'opposto:** Per ogni numero reale $a$ vale $-(-a) = a$. Infatti, $-(-a)$ è l'opposto di $-a$, ma anche $a$ è l'opposto di $-a$, poiché $-a+a=0$. Per l'unicità dell'opposto, segue la tesi.

- **Regola dei segni:** Per ogni $a,b \in \mathbb{R}$:
    1.  $(-a) \cdot b = -(a \cdot b)$. Dimostrazione: $(-a) \cdot b + a \cdot b = [(-a)+a] \cdot b = 0 \cdot b = 0$. Questo significa che $(-a) \cdot b$ è l'opposto di $a \cdot b$, cioè $-(a \cdot b)$.
    2.  $(-a) \cdot (-b) = a \cdot b$. Dimostrazione: $(-a) \cdot (-b) = -[a \cdot (-b)] = -[-(a \cdot b)]$. Per la proprietà dell'opposto dell'opposto, si ottiene $a \cdot b$.

### Conseguenze degli Assiomi di Ordinamento

- **Equivalenza della disuguaglianza:** $a \le b \iff b-a \ge 0$.
  *Dimostrazione:* Se $a \le b$, sommando $-a$ a entrambi i membri si ottiene $a-a \le b-a$, ovvero $0 \le b-a$. Viceversa, se $b-a \ge 0$, sommando $a$ a entrambi i membri si ha $(b-a)+a \ge 0+a$, da cui $b \ge a$.

- **Proprietà Transitiva:** Se $a \le b$ e $b \le c$, allora $a \le c$.
  *Dimostrazione:* Da $a \le b$ segue $b-a \ge 0$. Allo stesso modo, da $b \le c$ segue $c-b \ge 0$. Poiché la somma di numeri non negativi è non negativa, si ha $(b-a)+(c-b) \ge 0$. Semplificando si ottiene $c-a \ge 0$, che equivale a $c \ge a$.

- **Segno dell'Opposto:** $a \ge 0 \iff -a \le 0$.
  *Dimostrazione:* Se $a \ge 0$, sommando $-a$ a entrambi i membri si ottiene $a+(-a) \ge 0+(-a)$, ovvero $0 \ge -a$.

- **Moltiplicazione per un Numero Positivo:** Se $a \le b$ e $c \ge 0$, allora $a \cdot c \le b \cdot c$. La disuguaglianza si conserva.
  *Dimostrazione:* Da $a \le b$ segue $b-a \ge 0$. Poiché anche $c \ge 0$, il prodotto $(b-a)c \ge 0$. Per la proprietà distributiva, $bc - ac \ge 0$, da cui $bc \ge ac$.

- **Moltiplicazione per un Numero Negativo:** Se $a \le b$ e $c \le 0$, allora $a \cdot c \ge b \cdot c$. La disuguaglianza si inverte.
  *Dimostrazione:* Se $c \le 0$, allora $-c \ge 0$. Poiché $b-a \ge 0$, si ha $(b-a)(-c) \ge 0$. Svolgendo il prodotto, si ottiene $-bc + ac \ge 0$, da cui $ac \ge bc$.

- **Relazione tra gli Inversi:** Se $0 < a < b$, allora $0 < b^{-1} < a^{-1}$.
  *Dimostrazione:* Poiché $a, b > 0$, anche $a^{-1}, b^{-1} > 0$. Si moltiplica la disuguaglianza $a < b$ per la quantità positiva $a^{-1}b^{-1}$. Si ottiene $a(a^{-1}b^{-1}) < b(a^{-1}b^{-1})$. Semplificando, si arriva a $b^{-1} < a^{-1}$.