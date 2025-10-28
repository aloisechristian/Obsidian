# Topologia, Limiti e Continuità in $\mathbb{R}$

## 1. Topologia della Retta Reale

### 1.1. Definizione di Intorno

Dato un punto $x_0 \in \mathbb{R}$, si definisce **intorno** di $x_0$ un qualsiasi [[03 - Insiemi Numerici, Completezza e Estremo Superiore#Intervalli in R|intervallo aperto]] che contiene $x_0$. Per convenzione, si considerano spesso gli **intorni simmetrici (o circolari, o sferici)**, ovvero intervalli in cui $x_0$ è il punto medio. Un tale intorno è definito da un raggio $\delta > 0$ e si denota come:
$$I(x_0, \delta) = (x_0 - \delta, x_0 + \delta)$$
Un punto $x$ appartiene a questo intorno se e solo se la sua distanza da $x_0$ è minore di $\delta$, condizione che è equivalente alla seguente disuguaglianza con il [[06 - Studio delle Funzioni Valore Assoluto e Potenza|valore assoluto]]:
$$|x - x_0| < \delta$$

Si definiscono inoltre **intorni unilaterali**:
* **Intorno destro** di $x_0$: un intervallo della forma $(x_0, x_0 + \delta)$ o $[x_0, x_0 + \delta)$, con $\delta > 0$.
* **Intorno sinistro** di $x_0$: un intervallo della forma $(x_0 - \delta, x_0)$ o $(x_0 - \delta, x_0]$, con $\delta > 0$.

> [!NOTE] Proprietà di Separazione (Hausdorff)
> Dati due punti distinti $x, y \in \mathbb{R}$ (o $\mathbb{R}$ esteso), esistono sempre un intorno di $x$ e un intorno di $y$ che sono disgiunti (la loro intersezione è l'[[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Esempio 2: L'Insieme Vuoto|insieme vuoto]]).

### 1.2. Intorni di Infinito

La nozione di intorno può essere estesa anche all'insieme dei numeri reali ampliato $\overline{\mathbb{R}} = \mathbb{R} \cup \{ -\infty, +\infty \}$.
* Un **intorno di $+\infty$** è un qualsiasi intervallo illimitato superiormente, della forma $(M, +\infty)$ per un certo $M \in \mathbb{R}$.
* Un **intorno di $-\infty$** è un qualsiasi intervallo illimitato inferiormente, della forma $(-\infty, M)$ per un certo $M \in \mathbb{R}$.

### 1.3. Punti di Accumulazione e Punti Isolati

Sia $X \subseteq \mathbb{R}$ un insieme. Un punto $x_0 \in \overline{\mathbb{R}}$, che non deve necessariamente appartenere a $X$, si dice **punto di accumulazione** per $X$ se in *ogni* intorno di $x_0$ cade almeno un punto di $X$ distinto da $x_0$ stesso. Formalmente:
$$\forall I(x_0) \text{ intorno di } x_0, \quad (I(x_0) \setminus \{x_0\}) \cap X \neq \emptyset$$
L'esistenza di un punto di accumulazione suggerisce che gli elementi dell'insieme $X$ si "addensano" arbitrariamente vicino a $x_0$. Se in ogni intorno cade almeno un punto distinto, allora ne cadono infiniti.

Un punto $x_0 \in X$ che *non* è di accumulazione per $X$ si dice **punto isolato** di $X$. Per un punto isolato, esiste almeno un intorno $I(x_0)$ tale che $I(x_0) \cap X = \{x_0\}$.

### 1.4. Insieme Derivato, Chiusura, Insiemi Chiusi e Compatti

Si definiscono i seguenti insiemi:
* **Insieme derivato**: L'insieme di tutti i punti di accumulazione di $X$, denotato con $D(X)$ o $X'$. Un punto di accumulazione non deve necessariamente appartenere all'insieme $X$.
* **Chiusura di un insieme**: L'unione dell'insieme $X$ con il suo derivato, denotata con $\overline{X} = X \cup D(X)$.
* **Insieme chiuso**: Un insieme $X$ si dice chiuso se contiene tutti i suoi punti di accumulazione, ovvero se $D(X) \subseteq X$, il che implica $\overline{X} = X$.
* **Insieme Compatto**: Un insieme $X \subseteq \mathbb{R}$ si dice **compatto** se è **chiuso e limitato** (Teorema di Heine-Borel).

### 1.5. Esempi

1.  **Intervallo chiuso $[a, b]$**: Ogni punto $x \in [a, b]$ è di accumulazione. $D([a, b]) = [a, b]$. L'insieme è chiuso e, essendo limitato, è compatto.

2.  **Intervallo aperto $(a, b)$**: Ogni punto interno $x \in (a,b)$ è di accumulazione. Anche gli estremi $a$ e $b$, pur non appartenendo all'insieme, sono punti di accumulazione. $D((a, b)) = [a, b]$. L'insieme non è chiuso. La sua chiusura è $\overline{(a,b)} = [a, b]$.

3.  **Insieme singoletto $A = \{a\}$**: Non ha punti di accumulazione, $D(A) = \emptyset$. Il punto $a$ è un punto isolato.

4.  **Insieme $\mathbb{N} = \{1, 2, 3, \dots\}$**: Non ha punti di accumulazione al finito (ogni punto è isolato), $D(\mathbb{N}) \cap \mathbb{R} = \emptyset$. Tuttavia, $+\infty$ è un punto di accumulazione per $\mathbb{N}$, grazie alla [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|proprietà Archimedea]] (per ogni $M \in \mathbb{R}$, esiste $n \in \mathbb{N}$ tale che $n > M$).

5.  **Insieme $A = \{1/n \mid n \in \mathbb{N}^*\}$**: L'unico punto di accumulazione è 0. Infatti, per ogni intorno $(-\delta, \delta)$ di 0, per la [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|proprietà Archimedea]], esiste $n \in \mathbb{N}^*$ tale che $n > 1/\delta$, da cui $0 < 1/n < \delta$. Quindi, ogni intorno di 0 contiene infiniti punti dell'insieme. Si noti che $0 \notin A$.

## 2. Limiti di Funzioni

Il concetto di limite descrive il comportamento di una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] $f(x)$ quando la variabile indipendente $x$ si avvicina a un punto $x_0$ che deve essere **punto di accumulazione** per il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|dominio]] $X$ della funzione.

### 2.1. Definizione Topologica e $\epsilon-\delta$

**Definizione topologica (generale)**: Sia $f: X \to \mathbb{R}$ e sia $x_0$ un punto di accumulazione per $X$. Si dice che il limite di $f(x)$ per $x$ che tende a $x_0$ è $L$ (con $L \in \overline{\mathbb{R}}$), e si scrive $\lim_{x \to x_0} f(x) = L$, se:
> Per ogni intorno $V$ di $L$ esiste un intorno $U$ di $x_0$ tale che per ogni $x \in U \cap X$, con $x \neq x_0$, si ha $f(x) \in V$.
> $$\forall V \text{ intorno di } L, \exists U \text{ intorno di } x_0 \text{ t.c. } \forall x \in X, \text{ se } x \in U \setminus \{x_0\} \implies f(x) \in V$$

**Definizione $\epsilon-\delta$ (per $x_0, L \in \mathbb{R}$)**: La definizione precedente si specializza nel caso di limiti finiti al finito. Si ha $\lim_{x \to x_0} f(x) = L$ se:
$$\forall \epsilon > 0, \exists \delta > 0 \text{ tale che } \forall x \in X, \text{ se } 0 < |x - x_0| < \delta \text{ allora } |f(x) - L| < \epsilon$$
La condizione $0 < |x-x_0|$ esclude il punto $x_0$ stesso.

### 2.2. Teorema Ponte: Legame tra Limiti di Funzioni e Successioni

Questo teorema stabilisce un'equivalenza fondamentale tra la nozione di limite di una funzione e quella di [[14 - Definizione e Teoremi dei Limiti di Successioni|limite di una successione]]. Permette di estendere ai limiti di funzioni molte proprietà note per le successioni (unicità del limite, [[14 - Definizione e Teoremi dei Limiti di Successioni#Algebra dei Limiti|algebra dei limiti]], [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema della Permanenza del Segno|permanenza del segno]], [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema dei Carabinieri (o del Confronto)|teorema del confronto]]).

**Enunciato**: Sia $f: X \to \mathbb{R}$ e sia $x_0$ un punto di accumulazione per $X$. Le seguenti affermazioni sono equivalenti:
1.  Per ogni [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Definizione di Successione|successione]] $(x_n)_{n \in \mathbb{N}}$ di punti in $X \setminus \{x_0\}$ tale che $\lim_{n \to \infty} x_n = x_0$, si ha $\lim_{n \to \infty} f(x_n) = L$. (Definizione sequenziale)
2.  $\, \lim_{x \to x_0} f(x) = L$. (Definizione $\epsilon-\delta$ / intorni)

**Dimostrazione**:
* **(2 $\implies$ 1)**: Assumiamo vera la definizione di limite (2). Sia $(x_n)$ una successione in $X \setminus \{x_0\}$ convergente a $x_0$. Fissato $\epsilon > 0$, per la (2) esiste un $\delta > 0$ tale che se $0 < |x - x_0| < \delta$, allora $|f(x) - L| < \epsilon$. Poiché $x_n \to x_0$, per la definizione di limite di successione, in corrispondenza di tale $\delta$ esiste un $\nu \in \mathbb{N}$ tale che per ogni $n > \nu$ si ha $0 < |x_n - x_0| < \delta$. Unendo le due implicazioni, per $n > \nu$ si ha $|f(x_n) - L| < \epsilon$, che è la definizione di $\lim_{n \to \infty} f(x_n) = L$.
* **(1 $\implies$ 2)**: Procediamo per [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|assurdo]], negando la tesi (2). La negazione di (2) è: esiste un $\epsilon_0 > 0$ tale che per ogni $\delta > 0$ esiste almeno un $x \in X$ con $0 < |x - x_0| < \delta$ per cui $|f(x) - L| \ge \epsilon_0$. Scegliamo una successione di $\delta_n = 1/n$ per $n \in \mathbb{N}^*$. Per ogni $n$, possiamo trovare un $x_n \in X \setminus \{x_0\}$ tale che $0 < |x_n - x_0| < 1/n$ e $|f(x_n) - L| \ge \epsilon_0$. La successione $(x_n)$ così costruita converge a $x_0$ per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema dei Carabinieri (o del Confronto)|Teorema dei Carabinieri]]. Per l'ipotesi (1), dovrebbe seguire che $\lim_{n \to \infty} f(x_n) = L$. Tuttavia, per costruzione, $|f(x_n) - L| \ge \epsilon_0 > 0$ per ogni $n$, il che contraddice la convergenza di $f(x_n)$ a $L$. L'assurdo dimostra la tesi (2).

### 2.3. Forme Indeterminate e Limiti Notevoli

Le operazioni sui limiti si estendono alle funzioni. Le **forme indeterminate** sono le stesse delle successioni:
$$\infty - \infty, \quad 0 \cdot \infty, \quad \frac{\infty}{\infty}, \quad \frac{0}{0}, \quad 1^\infty, \quad 0^0, \quad \infty^0$$

* **Funzione esponenziale**: Analogamente alle successioni (vedi [[15 - Teoremi Fondamentali dei Limiti di Successioni#Limite della Successione Geometrica an|limite della successione geometrica]]), si ha:
    $$\lim_{x \to +\infty} a^x = \begin{cases} +\infty & \text{se } a > 1 \\ 0 & \text{se } 0 < a < 1 \end{cases}$$
* **Limite notevole goniometrico**: Grazie al Teorema Ponte, si estende il risultato noto per le successioni ([[16 - Criteri di Convergenza e Proprietà delle Successioni#Limiti Trigonometrici|limiti trigonometrici notevoli]]):
    $$\lim_{x \to 0} \frac{\sin(x)}{x} = 1$$
* **Non esistenza di limiti**: Le funzioni $\sin(x)$ e $\cos(x)$ non ammettono limite per $x \to \pm\infty$. La dimostrazione usa il Teorema Ponte trovando due successioni $x_n, x'_n \to +\infty$ tali che $f(x_n)$ e $f(x'_n)$ convergono a limiti diversi (es. $x_n = 2n\pi$ e $x'_n = \frac{\pi}{2} + 2n\pi$ per $\sin(x)$).
* **Calcolo di un limite**: Per calcolare $\lim_{x \to 0} \frac{1-\cos(x)}{x^2}$ (forma $\frac{0}{0}$), si può utilizzare il limite notevole del seno:
    $$\begin{aligned} \lim_{x \to 0} \frac{1-\cos(x)}{x^2} &= \lim_{x \to 0} \frac{1-\cos(x)}{x^2} \cdot \frac{1+\cos(x)}{1+\cos(x)} \\ &= \lim_{x \to 0} \frac{1-\cos^2(x)}{x^2(1+\cos(x))} \\ &= \lim_{x \to 0} \frac{\sin^2(x)}{x^2} \cdot \frac{1}{1+\cos(x)} \\ &= \left( \lim_{x \to 0} \frac{\sin(x)}{x} \right)^2 \cdot \lim_{x \to 0} \frac{1}{1+\cos(x)} \\ &= 1^2 \cdot \frac{1}{1+1} = \frac{1}{2} \end{aligned}$$

## 3. Funzioni Continue

### 3.1. Definizione di Continuità

Una funzione $f: X \to \mathbb{R}$ si dice **continua** in un punto $x_0 \in X$ se si verifica una delle seguenti condizioni:
1.  $x_0$ è un **punto isolato** di $X$.
2.  $x_0$ è un **punto di accumulazione** per $X$ e si verifica che:
    $$\lim_{x \to x_0} f(x) = f(x_0)$$
In altre parole, nel caso (2), il valore del limite coincide con il valore che la funzione assume nel punto.

Una formulazione equivalente per il caso (2), utile in contesti come le derivate, si ottiene ponendo $h = x - x_0$. Poiché $x \to x_0$ è equivalente a $h \to 0$, la condizione di continuità diventa:
$$\lim_{h \to 0} f(x_0 + h) = f(x_0)$$

Una funzione è **continua su un intervallo** $[a, b]$ se è continua in ogni punto interno $(a, b)$ e se valgono i limiti destro e sinistro agli estremi:
$$\lim_{x \to a^+} f(x) = f(a) \quad \text{e} \quad \lim_{x \to b^-} f(x) = f(b)$$

Le [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali|funzioni elementari]] (polinomi, esponenziali, logaritmi, funzioni goniometriche) sono continue nei loro domini.

### 3.2. Proprietà delle Funzioni Continue
L'[[14 - Definizione e Teoremi dei Limiti di Successioni#Algebra dei Limiti|algebra dei limiti]] si traduce direttamente in proprietà per le funzioni continue. Se $f$ e $g$ sono continue in $x_0$, allora sono continue in $x_0$ anche:
* La somma: $f+g$
* La differenza: $f-g$
* Il prodotto: $f \cdot g$
* Il quoziente: $f/g$, purché $g(x_0) \neq 0$.
Anche la composizione di funzioni continue, $g \circ f$, è una funzione continua.

### 3.3. Esempio: Continuità della Funzione Seno
Dimostriamo che $f(x) = \sin(x)$ è continua per ogni $x_0 \in \mathbb{R}$. Utilizziamo la formula di addizione del seno e i limiti notevoli:
$$\begin{aligned} \lim_{h \to 0} \sin(x_0 + h) &= \lim_{h \to 0} (\sin(x_0)\cos(h) + \cos(x_0)\sin(h)) \\ &= \sin(x_0) \cdot \left( \lim_{h \to 0} \cos(h) \right) + \cos(x_0) \cdot \left( \lim_{h \to 0} \sin(h) \right) \\ &= \sin(x_0) \cdot 1 + \cos(x_0) \cdot 0 \\ &= \sin(x_0) = f(x_0) \end{aligned}$$
La funzione è dunque continua su tutto $\mathbb{R}$.

## 4. Classificazione dei Punti di Discontinuità

Un punto $x_0$ in cui una funzione non è continua è detto punto di discontinuità. Essi si classificano in tre tipi.

### 4.1. Discontinuità Eliminabile (o di Terza Specie)
Si verifica quando il limite $\lim_{x \to x_0} f(x) = L$ esiste ed è finito, ma $L \neq f(x_0)$ oppure $f(x_0)$ non è definita.
* **Esempio**: $f(x) = \frac{\sin(x)}{x}$. La funzione non è definita in $x_0=0$. Tuttavia, $\lim_{x \to 0} \frac{\sin(x)}{x} = 1$. La discontinuità può essere "eliminata" definendo una nuova funzione (prolungamento per continuità):
    $$\tilde{f}(x) = \begin{cases} \frac{\sin(x)}{x} & \text{se } x \neq 0 \\ 1 & \text{se } x = 0 \end{cases}$$
    La funzione $\tilde{f}(x)$ è continua in $x=0$.

### 4.2. Discontinuità di Prima Specie (a Salto)
Si verifica quando i limiti destro e sinistro in $x_0$ esistono e sono finiti, ma diversi tra loro: $\lim_{x \to x_0^-} f(x) = L_1 \neq L_2 = \lim_{x \to x_0^+} f(x)$. La differenza $|L_2 - L_1|$ è detta "salto" della funzione.
* **Esempio**: $f(x) = \frac{|x|}{x}$. Per $x > 0$, $f(x) = 1$; per $x < 0$, $f(x) = -1$. In $x_0=0$ si ha:
    $$\lim_{x \to 0^-} f(x) = -1 \quad \text{e} \quad \lim_{x \to 0^+} f(x) = 1$$
    La discontinuità non è eliminabile.

### 4.3. Discontinuità di Seconda Specie
Si verifica quando almeno uno dei due limiti, destro o sinistro, in $x_0$ non esiste o è infinito.
* **Esempio**: $f(x) = \tan(x)$ in $x_0 = \frac{\pi}{2}$. Si ha:
    $$\lim_{x \to (\pi/2)^-} \tan(x) = +\infty \quad \text{e} \quad \lim_{x \to (\pi/2)^+} \tan(x) = -\infty$$

## 5. Teoremi Fondamentali sulle Funzioni Continue

Questi teoremi evidenziano proprietà cruciali delle funzioni continue definite su intervalli chiusi e limitati (insiemi compatti).

### 5.1. Teorema della Permanenza del Segno
Se una funzione $f$ è continua in $x_0$ e $f(x_0) \neq 0$ (cioè $f(x_0) > 0$ o $f(x_0) < 0$), allora esiste un intorno $I(x_0)$ di $x_0$ tale che $f(x)$ ha lo stesso segno di $f(x_0)$ per ogni $x \in I(x_0) \cap X$.
*Dimostrazione (idea):* Deriva dalla definizione di limite. Scegliendo $\epsilon = |f(x_0)|/2 > 0$, esiste un $\delta > 0$ tale che se $|x-x_0|<\delta$, allora $|f(x)-f(x_0)| < |f(x_0)|/2$. Questo implica che $f(x)$ deve trovarsi nell'intervallo $(f(x_0)/2, 3f(x_0)/2)$ se $f(x_0)>0$, o $(-3|f(x_0)|/2, -|f(x_0)|/2)$ se $f(x_0)<0$, mantenendo in entrambi i casi il segno di $f(x_0)$. Vedi anche [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema della Permanenza del Segno]].

### 5.2. Teorema di Esistenza degli Zeri (o di Bolzano)
**Enunciato**: Sia $f$ una funzione continua su un intervallo chiuso e limitato $[a, b]$. Se $f$ assume valori di segno discorde agli estremi, cioè $f(a) \cdot f(b) < 0$, allora esiste almeno un punto $c \in (a, b)$ tale che $f(c) = 0$.

* **Interpretazione geometrica**: Se il grafico di una funzione continua congiunge un punto sotto l'asse delle $x$ con un punto sopra l'asse delle $x$, deve necessariamente intersecare l'asse $x$ almeno una volta.
* **Idea della dimostrazione ([[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative|Metodo di Bisezione]])**: Si costruisce una successione di intervalli incapsulati $[a_n, b_n]$ dimezzando ad ogni passo l'intervallo precedente e scegliendo la metà in cui la funzione mantiene segni discordi agli estremi. L'ampiezza $b_n - a_n \to 0$. Le successioni $(a_n)$ e $(b_n)$ convergono (per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema di Regolarità delle Successioni Monotone|teorema sulle successioni monotone]]) a un punto comune $c$. Sfruttando la continuità di $f$ e la permanenza del segno, si mostra che $f(c)=0$.

### 5.3. Teorema dei Valori Intermedi
**Enunciato**: Sia $f$ una funzione continua su un intervallo chiuso e limitato $[a, b]$. Allora $f$ assume tutti i valori compresi tra $f(a)$ e $f(b)$.

* **Dimostrazione**: È una conseguenza del Teorema degli Zeri. Si considera $g(x) = f(x) - k$, dove $k$ è un valore compreso tra $f(a)$ e $f(b)$. $g(x)$ è continua e assume segni discordi in $a$ e $b$. Per Bolzano, esiste $c \in (a, b)$ tale che $g(c)=0$, ovvero $f(c)=k$.

### 5.4. Teorema di Weierstrass
**Enunciato**: Sia $f$ una funzione continua su un intervallo chiuso e limitato $[a, b]$ (un insieme [[#1.4. Insieme Derivato, Chiusura, Insiemi Chiusi e Compatti|compatto]]). Allora $f$ ammette **massimo** e **minimo** assoluti in $[a, b]$. Cioè, esistono $x_{min}, x_{max} \in [a, b]$ tali che:
$$f(x_{min}) \le f(x) \le f(x_{max}) \quad \forall x \in [a, b]$$
Il valore $m = f(x_{min})$ è il minimo assoluto e $M = f(x_{max})$ è il massimo assoluto della funzione sull'intervallo.

* **Importanza**: Questo teorema garantisce l'esistenza di massimi e minimi per funzioni continue su compatti, un risultato fondamentale in ottimizzazione. L'ipotesi che l'intervallo sia chiuso e limitato è essenziale.
* **Idea della dimostrazione (per il massimo)**:
    1.  Si considera l'[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Estremo Superiore e Inferiore di una Funzione|estremo superiore]] $M = \sup \{f(x) \mid x \in [a, b]\}$. Si deve dimostrare che $M$ è finito e che esiste $x_{max} \in [a, b]$ tale che $f(x_{max})=M$.
    2.  Per le proprietà del sup, esiste una successione $(x_n)$ in $[a, b]$ tale che $\lim_{n \to \infty} f(x_n) = M$.
    3.  Poiché $[a, b]$ è compatto, per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema di Bolzano-Weierstrass|Teorema di Bolzano-Weierstrass]], esiste una sottosuccessione $(x_{n_k})$ convergente a un punto $x_{max} \in [a, b]$.
    4.  Essendo $f$ continua in $x_{max}$, si ha $\lim_{k \to \infty} f(x_{n_k}) = f(x_{max})$.
    5.  Poiché $(f(x_{n_k}))$ è una sottosuccessione di $(f(x_n))$ che converge a $M$, anche la sottosuccessione deve convergere a $M$.
    6.  Per l'unicità del limite, si conclude che $f(x_{max}) = M$. Questo prova che l'estremo superiore è un massimo (è finito ed è assunto). La dimostrazione per il minimo è analoga partendo dall'estremo inferiore.