# Topologia, Limiti e Continuità in $\mathbb{R}$

## 1. Topologia della Retta Reale

### 1.1. Definizione di Intorno
Dato un punto $x_0 \in \mathbb{R}$, si definisce **intorno** di $x_0$ un qualsiasi [[03 - Insiemi Numerici, Completezza e Estremo Superiore#Intervalli in R|intervallo aperto]] che contiene $x_0$. Per convenzione, si considerano spesso gli **intorni simmetrici (o circolari, o sferici)**, ovvero intervalli in cui $x_0$ è il punto medio. Un tale intorno è definito da un raggio $\delta > 0$ e si denota come:
$$I(x_0, \delta) = (x_0 - \delta, x_0 + \delta)$$
Un punto $x$ appartiene a questo intorno se e solo se $x_0 - \delta < x < x_0 + \delta$, condizione che è equivalente alla seguente disuguaglianza con il [[06 - Studio delle Funzioni Valore Assoluto e Potenza|valore assoluto]]:
$$|x - x_0| < \delta$$
Si definiscono inoltre **intorni unilaterali**:
* **Intorno destro** di $x_0$: un intervallo della forma $(x_0, x_0 + \delta)$ o $[x_0, x_0 + \delta)$, con $\delta > 0$.
* **Intorno sinistro** di $x_0$: un intervallo della forma $(x_0 - \delta, x_0)$ o $(x_0 - \delta, x_0]$, con $\delta > 0$.

### 1.2. Intorni di Infinito
La nozione di intorno può essere estesa ai punti all'infinito, introducendo l'**insieme dei numeri reali esteso** $\mathbb{R} \cup \{-\infty, +\infty\}$.
* Un **intorno di $+\infty$** è un qualsiasi intervallo non limitato superiormente, della forma $(M, +\infty)$ per un certo $M \in \mathbb{R}$.
* Un **intorno di $-\infty$** è un qualsiasi intervallo non limitato inferiormente, della forma $(-\infty, M)$ per un certo $M \in \mathbb{R}$.

> [!NOTE] Proprietà di Separazione (Hausdorff)
> Dati due punti distinti $x, y \in \mathbb{R}$ (o $\mathbb{R}$ esteso), esistono sempre un intorno di $x$ e un intorno di $y$ che sono disgiunti (la loro intersezione è l'insieme vuoto).

### 1.3. Punti di Accumulazione e Punti Isolati
Sia $X \subseteq \mathbb{R}$ un insieme. Un punto $x_0 \in \mathbb{R}$ (o $\mathbb{R}$ esteso), che non deve necessariamente appartenere a $X$, si dice **punto di accumulazione** per $X$ se in *ogni* intorno di $x_0$ cade almeno un punto di $X$ distinto da $x_0$. Formalmente:
$$\forall I \text{ intorno di } x_0, \quad (I \cap X) \setminus \{x_0\} \neq \emptyset$$
Intuitivamente, ciò significa che esistono punti di $X$ "arbitrariamente vicini" a $x_0$. Se in ogni intorno cade almeno un punto distinto, allora ne cadono infiniti.

Un punto $x_0 \in X$ che *non* è di accumulazione per $X$ si dice **punto isolato** di $X$. Per un punto isolato, esiste almeno un intorno $I(x_0)$ tale che $I(x_0) \cap X = \{x_0\}$.

### 1.4. Insieme Derivato, Chiusura e Insiemi Compatti
* **Insieme Derivato**: L'insieme di tutti i punti di accumulazione di $X$ è detto **insieme derivato** di $X$ e si indica con $D(X)$ o $X'$.
* **Chiusura**: La **chiusura** di un insieme $X$, indicata con $\bar{X}$, è definita come l'unione dell'insieme stesso con il suo derivato: $\bar{X} = X \cup D(X)$.
* **Insieme Chiuso**: Un insieme $X$ si dice **chiuso** se contiene tutti i suoi punti di accumulazione, ovvero se $D(X) \subseteq X$, che equivale a dire $X = \bar{X}$.
* **Insieme Compatto**: Un insieme $X \subseteq \mathbb{R}$ si dice **compatto** se è **chiuso e limitato** (questo è noto come **Teorema di Heine-Borel**).

#### Esempi
1.  **Intervallo chiuso $[a, b]$**: Ogni punto $x \in [a, b]$ è di accumulazione. $D([a, b]) = [a, b]$. L'insieme è chiuso e, essendo limitato, è anche compatto.
2.  **Intervallo aperto $(a, b)$**: Ogni punto interno è di accumulazione. Anche gli estremi $a$ e $b$ sono punti di accumulazione. $D((a, b)) = [a, b]$. L'insieme non è chiuso. La sua chiusura è $\bar{X} = [a, b]$.
3.  **Insieme finito $\{a\}$**: Non ha punti di accumulazione. $D(\{a\}) = \emptyset$. Il punto $a$ è un punto isolato.
4.  **Insieme $\mathbb{N} = \{1, 2, 3, \dots\}$**: Non ha punti di accumulazione al finito (ogni punto è isolato). $D(\mathbb{N}) \cap \mathbb{R} = \emptyset$. Tuttavia, $+\infty$ è un punto di accumulazione per $\mathbb{N}$, grazie alla [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|proprietà Archimedea]] (per ogni $M$, esiste $n > M$).
5.  **Insieme $A = \{\frac{1}{n} \mid n \in \mathbb{N}, n \ge 1\}$**: L'unico punto di accumulazione è $0$, che non appartiene ad $A$. Questo si dimostra tramite la proprietà Archimedea: $\forall \delta > 0$, $\exists n > 1/\delta$, quindi $0 < 1/n < \delta$.

## 2. Limiti di Funzioni

Il concetto di limite descrive il comportamento di una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] $f(x)$ quando la variabile indipendente $x$ si avvicina a un punto $x_0$ che deve essere **punto di accumulazione** per il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|dominio]] $X$ della funzione.

### 2.1. Definizione di Limite

**Definizione formale (con intorni):**
Sia $f: X \to \mathbb{R}$ una funzione e $x_0$ un punto di accumulazione per $X$. Si dice che $\lim_{x \to x_0} f(x) = L$ (con $L \in \mathbb{R}$ esteso) se:
> Per ogni intorno $V$ di $L$ esiste un intorno $U$ di $x_0$ tale che per ogni $x \in U \cap X$, con $x \neq x_0$, si ha $f(x) \in V$.
> $$\forall V \text{ intorno di } L, \exists U \text{ intorno di } x_0 \text{ t.c. } \forall x \in X, \text{ se } x \in U \setminus \{x_0\} \implies f(x) \in V$$

**Definizione $\epsilon$-$\delta$ (caso $x_0, L \in \mathbb{R}$):**
La definizione precedente si specializza nel seguente modo quando sia $x_0$ che $L$ sono numeri reali finiti:
$$\forall \epsilon > 0, \exists \delta > 0 \text{ tale che } \forall x \in X, \text{ se } 0 < |x - x_0| < \delta \implies |f(x) - L| < \epsilon$$
La condizione $0 < |x-x_0|$ esclude il punto $x_0$ stesso.

### 2.2. Teorema Ponte: Legame tra Limiti di Funzioni e di Successioni
Il **Teorema Ponte** stabilisce un'equivalenza fondamentale tra i limiti di funzioni e i [[14 - Definizione e Teoremi dei Limiti di Successioni|limiti di successioni]].

**Enunciato:** Sia $f: X \to \mathbb{R}$ e $x_0$ un punto di accumulazione per $X$. Le seguenti affermazioni sono equivalenti:
1.  $\lim_{x \to x_0} f(x) = L$. (Definizione $\epsilon-\delta$ / intorni)
2.  Per ogni [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Definizione di Successione|successione]] $\{x_n\}_{n \in \mathbb{N}}$ di punti in $X \setminus \{x_0\}$ tale che $\lim_{n \to \infty} x_n = x_0$, risulta $\lim_{n \to \infty} f(x_n) = L$. (Definizione sequenziale)

**Dimostrazione:**
* **($1 \implies 2$)**: Si assume valida la definizione (1) ($\epsilon-\delta$). Si prende una qualsiasi successione $x_n \to x_0$ con $x_n \in X \setminus \{x_0\}$. Fissato $\epsilon > 0$, per la (1) esiste un $\delta > 0$ corrispondente. Poiché $x_n \to x_0$, per la [[14 - Definizione e Teoremi dei Limiti di Successioni#Definizione Formale di Limite Finito (Convergenza)|definizione di limite di successione]], esiste un indice $\nu$ tale che per $n > \nu$ si ha $|x_n - x_0| < \delta$ (e $x_n \neq x_0$, quindi $0 < |x_n - x_0| < \delta$). Per l'ipotesi (1), questo implica $|f(x_n) - L| < \epsilon$, che è la definizione di $\lim_{n \to \infty} f(x_n) = L$.

* **($2 \implies 1$)**: Si procede per [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|assurdo]]. Si assume vera la (2) e si nega la (1).
    Negare la (1) (definizione $\epsilon-\delta$) significa:
    $$\exists \epsilon_0 > 0 \text{ t.c. } \forall \delta > 0, \exists x \in X \setminus \{x_0\} \text{ con } 0 < |x - x_0| < \delta \text{ ma } |f(x) - L| \ge \epsilon_0$$
    Poiché questo vale per ogni $\delta > 0$, possiamo scegliere una successione di $\delta_n = 1/n \to 0$. Per ogni $\delta_n$, esiste un $x_n \in X \setminus \{x_0\}$ tale che:
    1.  $0 < |x_n - x_0| < 1/n$
    2.  $|f(x_n) - L| \ge \epsilon_0$
    Dalla condizione 1, per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema dei Carabinieri (o del Confronto)|Teorema dei Carabinieri]], si ha $x_n \to x_0$ (e $x_n \neq x_0$).
    Per l'ipotesi (2), se $x_n \to x_0$, allora *deve* risultare $f(x_n) \to L$. Questo implicherebbe che $\forall \epsilon$ (incluso $\epsilon_0$), $|f(x_n) - L| < \epsilon_0$ definitivamente.
    Questo è in netta contraddizione con la condizione 2, che afferma $|f(x_n) - L| \ge \epsilon_0$ per ogni $n$. L'assurdo prova che la (1) deve essere vera.

### 2.3. Applicazioni e Proprietà dei Limiti

Il Teorema Ponte permette di estendere ai limiti di funzioni tutte le proprietà viste per i limiti di successioni (unicità, algebra dei limiti, permanenza del segno, confronto).

**Esempio (Non Esistenza di un Limite):**
Dimostriamo che $\lim_{x \to +\infty} \sin(x)$ non esiste. Usiamo la definizione sequenziale (Teorema Ponte). Se il limite esistesse e fosse $L$, *ogni* successione $x_n \to +\infty$ dovrebbe dare $f(x_n) \to L$.
1.  Sia $x_n = 2n\pi$. Chiaramente $x_n \to +\infty$.
    $\lim_{n \to \infty} \sin(x_n) = \lim_{n \to \infty} \sin(2n\pi) = \lim_{n \to \infty} 0 = 0$.
2.  Sia $x'_n = \frac{\pi}{2} + 2n\pi$. Anche $x'_n \to +\infty$.
    $\lim_{n \to \infty} \sin(x'_n) = \lim_{n \to \infty} \sin\left(\frac{\pi}{2} + 2n\pi\right) = \lim_{n \to \infty} 1 = 1$.
Avendo trovato due successioni tendenti a $+\infty$ le cui immagini convergono a limiti diversi (0 e 1), il limite della funzione non può esistere.

**Operazioni e Forme Indeterminate:**
Le [[14 - Definizione e Teoremi dei Limiti di Successioni#Algebra dei Limiti|operazioni sui limiti]] (somma, prodotto, quoziente) si estendono alle funzioni. Le **forme indeterminate** sono le stesse:
$$\infty - \infty, \quad 0 \cdot \infty, \quad \frac{\infty}{\infty}, \quad \frac{0}{0}, \quad 1^\infty, \quad 0^0, \quad \infty^0$$

**Esempio (Calcolo di un Limite Notevole):**
Calcoliamo $\lim_{x \to 0} \frac{1 - \cos(x)}{x^2}$ (forma $\frac{0}{0}$).
$$\begin{aligned}
\lim_{x \to 0} \frac{1 - \cos(x)}{x^2} &= \lim_{x \to 0} \frac{(1 - \cos(x))(1 + \cos(x))}{x^2(1 + \cos(x))} \\
&= \lim_{x \to 0} \frac{1 - \cos^2(x)}{x^2(1 + \cos(x))} \\
&= \lim_{x \to 0} \frac{\sin^2(x)}{x^2(1 + \cos(x))} \\
&= \lim_{x \to 0} \left( \frac{\sin(x)}{x} \right)^2 \cdot \frac{1}{1 + \cos(x)} \\
&= \left(\lim_{x \to 0} \frac{\sin(x)}{x}\right)^2 \cdot \frac{1}{1 + \lim_{x \to 0} \cos(x)} \\
&= 1^2 \cdot \frac{1}{1+1} = \frac{1}{2}
\end{aligned}$$

## 3. Funzioni Continue

### 3.1. Definizione di Continuità
Una funzione $f: X \to \mathbb{R}$ si dice **continua** in un punto $x_0 \in X$ se si verifica una delle seguenti condizioni:
1.  $x_0$ è un **punto isolato** di $X$.
2.  $x_0$ è un **punto di accumulazione** per $X$ e si verifica che:
    $$\lim_{x \to x_0} f(x) = f(x_0)$$
In altre parole, nel caso (2), il valore del limite coincide con il valore che la funzione assume nel punto.

Una formulazione equivalente, utile in molti contesti, si ottiene ponendo $h = x - x_0$. La continuità in $x_0$ (se di accumulazione) è allora espressa da:
$$\lim_{h \to 0} f(x_0 + h) = f(x_0)$$

Una funzione si dice **continua in un intervallo** $[a, b]$ se è continua in ogni punto interno $(a, b)$ e inoltre:
* È continua da destra in $a$: $\lim_{x \to a^+} f(x) = f(a)$.
* È continua da sinistra in $b$: $\lim_{x \to b^-} f(x) = f(b)$.

Le [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali|funzioni elementari]] (polinomi, esponenziali, logaritmi, trigonometriche) sono continue nel loro dominio. Somma, prodotto, quoziente (den. $\neq 0$) e composizione di funzioni continue sono ancora funzioni continue.

### 3.2. Punti di Discontinuità
Un punto in cui una funzione non è continua è detto **punto di discontinuità**.
1.  **Discontinuità eliminabile (o di terza specie)**: Esiste finito il limite $\lim_{x \to x_0} f(x) = L$, ma $L \neq f(x_0)$ oppure $f(x_0)$ non è definita. Si può "eliminare" ridefinendo $f(x_0) = L$. Esempio: $f(x) = \frac{\sin(x)}{x}$ in $x_0 = 0$.
2.  **Discontinuità di prima specie (o a salto)**: Esistono finiti i limiti destro e sinistro, ma sono diversi: $\lim_{x \to x_0^+} f(x) \neq \lim_{x \to x_0^-} f(x)$. Esempio: $f(x) = \frac{|x|}{x}$ in $x_0 = 0$.
3.  **Discontinuità di seconda specie**: Almeno uno tra il limite destro e il limite sinistro non esiste o è infinito. Esempio: $f(x) = \tan(x)$ in $x_0 = \frac{\pi}{2}$.

## 4. Teoremi Fondamentali sulle Funzioni Continue

### 4.1. Teorema della Permanenza del Segno
Sia $f$ una funzione continua in $x_0$. Se $f(x_0) > 0$ (o $f(x_0) < 0$), allora esiste un intorno $I(x_0, \delta)$ di $x_0$ in cui la funzione mantiene lo stesso segno.
*Dimostrazione:* Dalla definizione di continuità $\lim_{x \to x_0} f(x) = f(x_0)$, scegliendo $\epsilon = \frac{|f(x_0)|}{2} > 0$, esiste $\delta > 0$ t.c. $\forall x \in I(x_0, \delta) \cap X$ vale $|f(x) - f(x_0)| < \epsilon$. Se $f(x_0) > 0$, questo implica $f(x) > f(x_0) - \epsilon = f(x_0) - \frac{f(x_0)}{2} = \frac{f(x_0)}{2} > 0$.

### 4.2. Teorema di Esistenza degli Zeri (o di Bolzano)
Sia $f$ una funzione continua in un intervallo chiuso e limitato $[a, b]$. Se la funzione assume valori di segno discorde agli estremi ($f(a) \cdot f(b) < 0$), allora esiste almeno un punto $x_0 \in (a, b)$ tale che $f(x_0) = 0$.
*Dimostrazione:* La dimostrazione si basa sul **[[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative|metodo di bisezione]]**. Si costruisce una successione di intervalli incapsulati $[a_n, b_n]$ partendo da $[a_0, b_0] = [a, b]$. Ad ogni passo $n$, si calcola il punto medio $c_n = \frac{a_n + b_n}{2}$.
* Se $f(c_n) = 0$, $x_0 = c_n$ e il teorema è dimostrato.
* Se $f(c_n)$ ha lo stesso segno di $f(a_n)$, si pone $[a_{n+1}, b_{n+1}] = [c_n, b_n]$.
* Se $f(c_n)$ ha lo stesso segno di $f(b_n)$, si pone $[a_{n+1}, b_{n+1}] = [a_n, c_n]$.
In questo modo, $f(a_n)$ e $f(b_n)$ hanno sempre segno discorde. L'ampiezza $b_n - a_n = \frac{b-a}{2^n} \to 0$. Le successioni $\{a_n\}$ (crescente) e $\{b_n\}$ (decrescente) sono limitate e quindi convergono (per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema di Regolarità delle Successioni Monotone|teorema sulle successioni monotone]]) allo stesso limite $x_0$.
Per la continuità di $f$ e la [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema della Permanenza del Segno|permanenza del segno nelle successioni]]:
* $f(a_n) \le 0 \implies f(x_0) = \lim_{n \to \infty} f(a_n) \le 0$
* $f(b_n) \ge 0 \implies f(x_0) = \lim_{n \to \infty} f(b_n) \ge 0$
Dovendo essere $f(x_0) \le 0$ e $f(x_0) \ge 0$, l'unica possibilità è $f(x_0) = 0$.

### 4.3. Teorema dei Valori Intermedi
Sia $f$ una funzione continua in un intervallo chiuso e limitato $[a, b]$. Allora la funzione assume tutti i valori compresi tra $f(a)$ e $f(b)$.
Formalmente, per ogni $y_0$ compreso tra $f(a)$ e $f(b)$, esiste almeno un $x_0 \in [a, b]$ tale che $f(x_0) = y_0$.
*Dimostrazione:* È una conseguenza diretta del Teorema degli Zeri. Si considera un $y_0$ tra $f(a)$ e $f(b)$ e si applica il Teorema degli Zeri alla funzione ausiliaria $g(x) = f(x) - y_0$. $g(x)$ è continua in $[a, b]$ e $g(a) \cdot g(b) < 0$ (poiché $g(a)$ e $g(b)$ hanno segni discordi). Esiste quindi $x_0 \in (a, b)$ tale che $g(x_0) = 0$, ovvero $f(x_0) - y_0 = 0$, da cui $f(x_0) = y_0$.