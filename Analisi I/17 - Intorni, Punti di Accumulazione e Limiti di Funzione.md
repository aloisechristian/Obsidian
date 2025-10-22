# Topologia e Limiti di Funzioni Reali

## 1. Topologia della Retta Reale

Prima di definire i limiti di funzioni, è necessario introdurre alcuni concetti topologici fondamentali relativi ai sottoinsiemi dei [[03 - Insiemi Numerici, Completezza e Estremo Superiore|numeri reali $\mathbb{R}$]].

### 1.1. Intorni di un Punto

Dato un punto $x_0 \in \mathbb{R}$, si definisce **intorno** di $x_0$ un qualsiasi [[03 - Insiemi Numerici, Completezza e Estremo Superiore#Intervalli in R|intervallo aperto]] che contiene $x_0$. Naturalmente, un punto $x_0$ possiede infiniti intorni.

Per convenzione e comodità di calcolo, si considera spesso un **intorno circolare (o simmetrico)** di $x_0$, ovvero un intervallo della forma:
$$(x_0 - \delta, x_0 + \delta) \quad \text{o equivalentemente} \quad ]x_0 - \delta, x_0 + \delta[$$
dove $\delta > 0$ è un numero reale che rappresenta il **raggio** o la **semi-ampiezza** dell'intorno. Un punto $x$ appartiene a tale intorno se e solo se la sua distanza da $x_0$ è minore di $\delta$, cioè se soddisfa la condizione:
$$|x - x_0| < \delta$$
Questa disuguaglianza è equivalente a $- \delta < x - x_0 < \delta$, che a sua volta equivale a $x_0 - \delta < x < x_0 + \delta$.

Si definiscono anche intorni unilaterali:
- **Intorno destro di $x_0$**: un intervallo del tipo $(x_0, x_0 + \delta)$ (o $[x_0, x_0+\delta)$ se semiaperto).
- **Intorno sinistro di $x_0$**: un intervallo del tipo $(x_0 - \delta, x_0)$ (o $(x_0-\delta, x_0]$ se semiaperto).
L'unione di un intorno destro e un intorno sinistro aperti forma un intorno completo di $x_0$.

La nozione di intorno si estende anche a $\mathbb{R}$ ampliato:
- **Intorno di $+\infty$**: un qualsiasi intervallo aperto non limitato superiormente, del tipo $(M, +\infty)$ per un qualsiasi $M \in \mathbb{R}$ (spesso si prende $M>0$). Un punto $x$ appartiene a tale intorno se $x > M$.
- **Intorno di $-\infty$**: un qualsiasi intervallo aperto non limitato inferiormente, del tipo $(-\infty, M)$ per un qualsiasi $M \in \mathbb{R}$ (spesso si prende $M<0$). Un punto $x$ appartiene a tale intorno se $x < M$.

Una proprietà fondamentale (proprietà di separazione di Hausdorff) è che, dati due punti distinti $x, y \in \mathbb{R}$ (o $\mathbb{R}$ ampliato), esistono sempre un intorno di $x$ e un intorno di $y$ che sono disgiunti (la loro intersezione è l'insieme vuoto).

### 1.2. Punti di Accumulazione

Sia $X \subseteq \mathbb{R}$ un insieme e $x_0$ un punto in $\mathbb{R}$ (o $\mathbb{R}$ ampliato), che può appartenere o meno a $X$.

Si dice che **$x_0$ è un punto di accumulazione per l'insieme $X$** se in *ogni* intorno di $x_0$ cade almeno un punto di $X$ distinto da $x_0$ stesso.

Formalmente:
$$\forall I \text{ intorno di } x_0, \quad (I \cap X) \setminus \{x_0\} \neq \emptyset$$

Intuitivamente, un punto è di accumulazione per un insieme se esistono punti dell'insieme "arbitrariamente vicini" ad esso, cioè prossimi a $x_0$ quanto si voglia. Se in ogni intorno di $x_0$ cade almeno un punto di $X$ distinto da $x_0$, allora necessariamente ne cadono infiniti.

Se un punto $x_0 \in X$ non è di accumulazione per $X$, si dice **punto isolato** di X. Per un punto isolato, esiste almeno un intorno che non contiene altri punti di $X$ al di fuori di $x_0$ stesso.

### 1.3. Insieme Derivato, Chiusura e Insiemi Compatti

- **Insieme Derivato**: L'insieme di tutti i punti di accumulazione (al finito) di un insieme $X$ è detto **insieme derivato** di $X$ e si denota con $D(X)$.
- **Chiusura**: La **chiusura** (o aderenza) di un insieme $X$, denotata con $\bar{X}$, è l'unione dell'insieme stesso con il suo derivato: $\bar{X} = X \cup D(X)$. I punti di $\bar{X}$ sono detti **punti aderenti** ad $X$.
- **Insieme Chiuso**: Un insieme $X$ si dice **chiuso** se contiene tutti i suoi punti di accumulazione, ovvero se $D(X) \subseteq X$. Equivalentemente, un insieme è chiuso se coincide con la sua chiusura ($\bar{X} = X$).
- **Insieme Compatto**: Un insieme $X \subseteq \mathbb{R}$ si dice **compatto** se è chiuso e limitato (**Teorema di Heine-Borel**). Una definizione equivalente afferma che un insieme è compatto se da ogni [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche|successione]] di punti dell'insieme è possibile estrarre una sottosuccessione convergente a un punto dell'insieme stesso.

## 2. Esempi di Punti di Accumulazione

Analizziamo i punti di accumulazione per alcuni insiemi notevoli.

- **Intervallo chiuso $A = [a, b]$**: Ogni punto $x_0 \in [a, b]$ è di accumulazione. Infatti, per qualsiasi $x_0$ interno $(a < x_0 < b)$, ogni intorno $(x_0 - \delta, x_0 + \delta)$ con $\delta$ sufficientemente piccolo è contenuto in $A$ e contiene infiniti punti di $A$. Anche gli estremi $a$ e $b$ sono di accumulazione: ogni intorno $(a - \delta, a + \delta)$ interseca $A$ nell'intervallo $[a, a+\delta)$ (se $\delta \le b-a$), che contiene punti di $A$ diversi da $a$. Un ragionamento analogo vale per $b$. L'insieme derivato è $D(A) = [a, b]$. Poiché $D(A) \subseteq A$, l'insieme è chiuso. Essendo anche limitato, è compatto.

- **Intervallo aperto $A = (a, b)$**: Ogni punto $x_0 \in (a, b)$ è di accumulazione. Inoltre, anche gli estremi $a$ e $b$, che *non* appartengono ad $A$, sono punti di accumulazione. Il ragionamento è identico al caso precedente. Pertanto, l'insieme derivato è $D(A) = [a, b]$. Poiché $D(A) \not\subseteq A$, l'insieme non è chiuso. La sua chiusura è $\bar{A} = A \cup D(A) = (a, b) \cup \{a, b\} = [a, b]$.

- **Singleton $A = \{a\}$**: Questo insieme non ha punti di accumulazione. Qualsiasi intorno di $a$, ad esempio $(a-\delta, a+\delta)$, intersecato con $A$ contiene solo $a$ stesso. Non ci sono punti di $A$ *distinti* da $a$ nell'intorno. L'insieme derivato è vuoto, $D(A) = \emptyset$. Il punto $a$ è un punto isolato.

- **Numeri Naturali $A = \mathbb{N} = \{1, 2, 3, \dots\}$**:
    - **Punti finiti**: Non esistono punti di accumulazione al finito. Per ogni $n \in \mathbb{N}$, l'intorno $(n-1/2, n+1/2)$ contiene solo $n$ e nessun altro numero naturale. Tutti i punti di $\mathbb{N}$ sono punti isolati. $D(\mathbb{N}) \cap \mathbb{R} = \emptyset$.
    - **Punti all'infinito**: $+\infty$ è un punto di accumulazione per $\mathbb{N}$. Dobbiamo verificare che in ogni intorno di $+\infty$, cioè in ogni intervallo $(M, +\infty)$, cada almeno un numero naturale. Questo è garantito dalla **[[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali|proprietà Archimedea]]** di $\mathbb{R}$, la quale afferma che per ogni numero reale $M$ esiste un numero naturale $n$ tale che $n > M$. Invece, $-\infty$ non è un punto di accumulazione, poiché $\mathbb{N}$ è limitato inferiormente.

- **Insieme $A = \{\frac{1}{n} \mid n \in \mathbb{N}^*\}$**: $A = \{1, 1/2, 1/3, \dots\}$.
    - L'insieme è limitato, essendo contenuto in $(0, 1]$. Pertanto, non vi sono punti di accumulazione all'infinito.
    - L'unico punto di accumulazione al finito è **0**. Per dimostrarlo, consideriamo un generico intorno di 0, $(-\delta, \delta)$. Dobbiamo verificare se esiste un elemento $1/n \in A$ (distinto da 0, il che è sempre vero) tale che $1/n \in (-\delta, \delta)$. Poiché $1/n > 0$, la condizione si riduce a $0 < 1/n < \delta$, che è equivalente a $n > 1/\delta$. Per la proprietà Archimedea, dato un qualsiasi numero reale $1/\delta$, esiste sempre un numero naturale $n$ che soddisfa tale disuguaglianza. Quindi 0 è un punto di accumulazione. Notare che $0 \notin A$. Tutti gli altri punti $1/n$ sono isolati.

## 3. Limiti di Funzioni Reali

L'analisi del comportamento di una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] $f: X \to \mathbb{R}$ quando la variabile indipendente $x$ si avvicina a un punto $x_0$ (appartenente a $\mathbb{R}$ ampliato) è centrale in analisi matematica. Affinché questo concetto abbia senso, $x_0$ deve essere un **punto di accumulazione** per il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|dominio]] $X$, garantendo così l'esistenza di punti in $X$ (diversi da $x_0$) arbitrariamente vicini a $x_0$.

### 3.1. Definizione di Limite tramite Intorni
Si dice che la funzione $f(x)$ è **convergente** a $L$ in $x_0$, o che il **limite della funzione $f(x)$ per $x$ che tende a $x_0$ è $L$** (con $L \in \mathbb{R}$ ampliato), e si scrive
$$\lim_{x \to x_0} f(x) = L$$
se per ogni intorno $J$ di $L$ è possibile determinare un intorno $I$ di $x_0$ tale che, per ogni $x \in (I \cap X) \setminus \{x_0\}$, la sua immagine $f(x)$ appartiene a $J$. Formalmente:
$$\forall J \text{ intorno di } L, \exists I \text{ intorno di } x_0 \text{ tale che } \forall x \in X, \text{ se } x \in I \setminus \{x_0\} \implies f(x) \in J$$

Nel caso specifico in cui $x_0 \in \mathbb{R}$ e $L \in \mathbb{R}$, questa definizione si traduce nella celebre **formulazione $\epsilon-\delta$**:
$$\forall \epsilon > 0, \exists \delta > 0 \text{ tale che } \forall x \in X, \text{ se } 0 < |x - x_0| < \delta \implies |f(x) - L| < \epsilon$$
dove $J = (L-\epsilon, L+\epsilon)$ e $I = (x_0-\delta, x_0+\delta)$. La condizione $0 < |x-x_0|$ esclude il punto $x_0$ stesso.
Questa definizione si adatta ai casi in cui $x_0$ o $L$ sono infiniti, modificando opportunamente la nozione di intorno (es. $x>k$ per $x_0=+\infty$, $f(x)>M$ per $L=+\infty$).

### 3.2. Definizione di Limite tramite Successioni

Una definizione alternativa, ma equivalente, si basa sul concetto di [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche|successione]].

Si dice che $\lim_{x \to x_0} f(x) = L$ se per **ogni** [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Definizione di Successione|successione]] $(x_n)_{n \in \mathbb{N}}$ di punti del dominio $X \setminus \{x_0\}$ che converge a $x_0$ (cioè $\lim_{n \to \infty} x_n = x_0$), la corrispondente successione delle immagini $(f(x_n))_{n \in \mathbb{N}}$ converge a $L$ (cioè $\lim_{n \to \infty} f(x_n) = L$).

## 4. Teorema Ponte: Equivalenza delle Definizioni

Il **Teorema Ponte** stabilisce l'equivalenza formale tra la definizione di limite tramite intorni ($\epsilon-\delta$) e quella tramite successioni.

**Enunciato:** Sia $f: X \to \mathbb{R}$ una funzione e $x_0$ un punto di accumulazione per $X$. Siano $x_0, L \in \mathbb{R}$. Le seguenti affermazioni sono equivalenti:
1.  Per ogni successione $(x_n)$ in $X \setminus \{x_0\}$ tale che $x_n \to x_0$, risulta $f(x_n) \to L$.
2.  $\forall \epsilon > 0, \exists \delta > 0$ tale che $\forall x \in X$, se $0 < |x - x_0| < \delta \implies |f(x) - L| < \epsilon$.

**Dimostrazione:**

**($2 \implies 1$)**
Assumiamo vera la definizione (2). Prendiamo una qualsiasi successione $x_n \to x_0$ con $x_n \in X \setminus \{x_0\}$ per ogni $n$. Dobbiamo dimostrare che $f(x_n) \to L$.
Per la definizione di [[14 - Definizione e Teoremi dei Limiti di Successioni#Definizione Formale di Limite Finito (Convergenza)|limite di successione]], $\forall \alpha > 0$, $\exists \nu \in \mathbb{N}$ tale che $\forall n > \nu$, $|x_n - x_0| < \alpha$.
Sia $\epsilon > 0$ fissato. Per l'ipotesi (2), in corrispondenza di questo $\epsilon$, esiste un $\delta > 0$ tale che $0 < |x - x_0| < \delta \implies |f(x) - L| < \epsilon$.
Scegliamo $\alpha = \delta$ nella definizione del limite della successione $x_n$. Allora esiste un $\nu$ tale che per $n > \nu$, si ha $|x_n - x_0| < \delta$. Poiché $x_n \neq x_0$ per ipotesi, vale $0 < |x_n - x_0| < \delta$.
Ma se questo è vero, per l'ipotesi (2), deve valere $|f(x_n) - L| < \epsilon$.
Abbiamo quindi dimostrato che $\forall \epsilon > 0, \exists \nu \in \mathbb{N}$ tale che $\forall n > \nu, |f(x_n) - L| < \epsilon$, che è la definizione di $\lim_{n \to \infty} f(x_n) = L$.

**($1 \implies 2$)**
Procediamo per [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|assurdo]]. Assumiamo che la (1) sia vera ma la (2) sia falsa.
La negazione della (2) è:
$$\exists \epsilon_0 > 0 \text{ tale che } \forall \delta > 0, \exists x \in X \setminus \{x_0\} \text{ con } 0 < |x - x_0| < \delta \text{ ma } |f(x) - L| \ge \epsilon_0$$

Poiché questo vale per ogni $\delta > 0$, possiamo scegliere una successione di $\delta_n = 1/n$ per $n \in \mathbb{N}^* = \{1, 2, 3, \dots\}$.
Per ogni $\delta_n = 1/n$, esiste un corrispondente $x_n \in X \setminus \{x_0\}$ tale che:
1.  $0 < |x_n - x_0| < 1/n$
2.  $|f(x_n) - L| \ge \epsilon_0$

Consideriamo la successione $(x_n)$ così costruita. Dalla condizione 1, $0 < |x_n - x_0| < 1/n$. Poiché $\lim_{n \to \infty} 1/n = 0$, per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema dei Carabinieri (o del Confronto)|Teorema dei Carabinieri]] (applicato a $0 < |x_n - x_0| < 1/n$), segue che $\lim_{n \to \infty} |x_n - x_0| = 0$, ovvero $x_n \to x_0$. Inoltre $x_n \neq x_0$ per costruzione.
Essendo vera l'ipotesi (1), se $x_n \to x_0$ con $x_n \in X \setminus \{x_0\}$, allora la successione delle immagini $f(x_n)$ deve convergere a $L$. Questo significa che, per definizione di limite di successione, $\forall \epsilon > 0$ (e in particolare per il nostro $\epsilon_0$), $\exists N \in \mathbb{N}$ tale che $\forall n > N$, $|f(x_n) - L| < \epsilon_0$.
Siamo giunti a una contraddizione: la condizione 2 afferma che $|f(x_n) - L| \ge \epsilon_0$ *per ogni* $n$, mentre l'ipotesi (1) implica che *da un certo indice in poi* deve valere $|f(x_n) - L| < \epsilon_0$. L'assurdo nasce dall'aver negato la (2), che deve quindi essere vera.

## 5. Applicazioni e Proprietà dei Limiti

Il Teorema Ponte è molto utile perché permette di trasferire molti risultati noti per i limiti di [[14 - Definizione e Teoremi dei Limiti di Successioni|successioni]] ai limiti di funzioni.

### 5.1. Esempio di Non Esistenza di un Limite

Dimostriamo che $\lim_{x \to +\infty} \sin(x)$ non esiste. Utilizziamo la definizione sequenziale. Se il limite esistesse e fosse $L$, allora *ogni* successione $x_n \to +\infty$ dovrebbe produrre una successione $\sin(x_n)$ convergente allo stesso valore $L$. Troviamo due successioni $x_n \to +\infty$ e $x'_n \to +\infty$ tali che $\lim \sin(x_n) \neq \lim \sin(x'_n)$.
1.  Sia $x_n = 2n\pi$ per $n \in \mathbb{N}$. Chiaramente, $x_n \to +\infty$. Calcoliamo il limite delle immagini:
    $$\lim_{n \to \infty} \sin(x_n) = \lim_{n \to \infty} \sin(2n\pi) = \lim_{n \to \infty} 0 = 0$$
   
2.  Sia $x'_n = \frac{\pi}{2} + 2n\pi$ per $n \in \mathbb{N}$. Anche $x'_n \to +\infty$. Calcoliamo il limite delle immagini:
    $$\lim_{n \to \infty} \sin(x'_n) = \lim_{n \to \infty} \sin\left(\frac{\pi}{2} + 2n\pi\right) = \lim_{n \to \infty} 1 = 1$$
   
Poiché abbiamo trovato due successioni tendenti a $+\infty$ le cui immagini convergono a limiti diversi (0 e 1), il limite della funzione per $x \to +\infty$ non può esistere.

### 5.2. Operazioni sui Limiti e Forme Indeterminate

Le operazioni algebriche (somma, differenza, prodotto, quoziente) valide per i limiti di successioni si estendono ai limiti di funzioni, grazie al Teorema Ponte. Il limite della somma, differenza, prodotto o quoziente di funzioni è uguale alla rispettiva operazione sui limiti, a patto che l'operazione sia definita (es. denominatore non nullo per il quoziente) e non risulti in una forma indeterminata.
Le **forme indeterminate** sono le stesse viste per le successioni:
$$\infty - \infty, \quad 0 \cdot \infty, \quad \frac{\infty}{\infty}, \quad \frac{0}{0}$$
(e le forme esponenziali $1^\infty, 0^0, \infty^0$).

### 5.3. Esempio di Calcolo di un Limite

Calcoliamo il limite notevole: $$\lim_{x \to 0} \frac{1 - \cos(x)}{x^2}$$
Sostituendo $x=0$, otteniamo $\frac{1-\cos(0)}{0^2} = \frac{1-1}{0} = \frac{0}{0}$, una forma indeterminata. Per risolverla, moltiplichiamo numeratore e denominatore per $1 + \cos(x)$:
$$\begin{aligned} \lim_{x \to 0} \frac{1 - \cos(x)}{x^2} &= \lim_{x \to 0} \frac{(1 - \cos(x))(1 + \cos(x))}{x^2(1 + \cos(x))} \\ &= \lim_{x \to 0} \frac{1 - \cos^2(x)}{x^2(1 + \cos(x))} \\ &= \lim_{x \to 0} \frac{\sin^2(x)}{x^2(1 + \cos(x))} \quad (\text{poiché } \sin^2 x + \cos^2 x = 1) \\ &= \lim_{x \to 0} \left( \frac{\sin(x)}{x} \right)^2 \cdot \frac{1}{1 + \cos(x)} \end{aligned}$$

Utilizzando i limiti notevoli $\lim_{x \to 0} \frac{\sin(x)}{x} = 1$ e $\lim_{x \to 0} \cos(x) = 1$, e applicando il teorema sul limite del prodotto e del quoziente, il limite diventa:
$$\left(\lim_{x \to 0} \frac{\sin(x)}{x}\right)^2 \cdot \frac{1}{1 + \lim_{x \to 0} \cos(x)} = 1^2 \cdot \frac{1}{1+1} = \frac{1}{2}$$


## 6. Funzioni Continue

Una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] $f$ definita in $X$ si dice **continua** in un punto $x_0 \in X$ se $x_0$ è un punto isolato di $X$ oppure se $x_0$ è un punto di accumulazione per $X$ e il valore del limite della funzione in quel punto coincide con il valore della funzione nel punto stesso. Formalmente, se $x_0$ è di accumulazione per $X$ e $x_0 \in X$:
$$\lim_{x \to x_0} f(x) = f(x_0)$$

Ad esempio, le funzioni $\sin(x)$ e $\cos(x)$ sono continue in $x=0$ poiché $\lim_{x \to 0} \sin(x) = 0 = \sin(0)$ e $\lim_{x \to 0} \cos(x) = 1 = \cos(0)$. Si può dimostrare che sono continue su tutto $\mathbb{R}$.

Una funzione è **continua in un intervallo** $[a, b]$ se è continua in ogni punto $x_0 \in (a,b)$ e se è continua da destra in $a$ ($\lim_{x \to a^+} f(x) = f(a)$) e continua da sinistra in $b$ ($\lim_{x \to b^-} f(x) = f(b)$).

Le operazioni algebriche tra funzioni continue (somma, differenza, prodotto, quoziente con denominatore non nullo) preservano la continuità. Anche la composizione di funzioni continue è una funzione continua. Molte funzioni elementari (polinomi, esponenziali, logaritmi, funzioni trigonometriche nel loro dominio) sono continue.