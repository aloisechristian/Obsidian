# La Funzione Potenza e le sue Generalizzazioni

## 1. Esponenti Naturali e Interi

La trattazione inizia con la funzione potenza $f(x) = x^n$, con $n \in \mathbb{N}$. Le proprietà di simmetria dipendono in modo cruciale dalla parità dell'esponente:
-   Se $n$ è **pari**, la funzione è **[[06 - Studio delle Funzioni Valore Assoluto e Potenza#Simmetrie delle Funzioni: Pari, Dispari e Periodiche|pari]]**, ovvero $f(-x) = (-x)^n = x^n = f(x)$. Il suo grafico è simmetrico rispetto all'asse delle ordinate.
-   Se $n$ è **dispari**, la funzione è **[[06 - Studio delle Funzioni Valore Assoluto e Potenza#Simmetrie delle Funzioni: Pari, Dispari e Periodiche|dispari]]**, ovvero $f(-x) = (-x)^n = -x^n = -f(x)$. Il suo grafico è simmetrico rispetto all'origine.

L'analisi viene estesa agli esponenti $n \in \mathbb{Z}$, includendo quindi gli interi negativi. Una funzione con esponente intero negativo, $x^{-m}$ (con $m \in \mathbb{N}$), può essere riscritta come:
$$x^{-m} = \frac{1}{x^m}$$
Questa trasformazione introduce una differenza fondamentale nell'**[[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|insieme di definizione]]**. Mentre per $n \in \mathbb{N}$ il dominio è $\mathbb{R}$, per esponenti interi negativi è necessario escludere il valore che annulla il denominatore. L'insieme di definizione diventa quindi $\mathbb{R} \setminus \{0\}$.

Il grafico di queste funzioni presenta un **asintoto verticale** in $x=0$ e un **asintoto orizzontale** in $y=0$. Anche in questo caso, la simmetria della funzione dipende dalla parità dell'esponente:
-   Se l'esponente è **pari e negativo** (es. $m$ pari), la funzione è pari e il suo codominio è $(0, +\infty)$.
-   Se l'esponente è **dispari e negativo** (es. $m$ dispari), la funzione è dispari e il suo codominio è $\mathbb{R} \setminus \{0\}$.

### 2. Esponenti Reali e Razionali

Si considera ora il caso più generale della funzione $f(x) = x^{\alpha}$ con $\alpha \in \mathbb{R}$. Per preservare la validità delle proprietà delle potenze, l'insieme di definizione cambia drasticamente:
-   Se $\alpha > 0$, il dominio è $x \ge 0$.
-   Se $\alpha < 0$, il dominio è $x > 0$.
Il caso $\alpha = 0$ definisce una funzione costante $f(x)=1$ per $x \ne 0$.

Un caso intermedio rilevante è quello degli esponenti **razionali**, $\alpha = \frac{m}{n}$ con $m, n \in \mathbb{Z}$. La funzione $x^{m/n}$ è definita come:
$$x^{m/n} = \sqrt[n]{x^m}$$
Questa identità è valida nel dominio di $x^\alpha$, ovvero per $x \ge 0$ se $\alpha>0$ e $x > 0$ se $\alpha < 0$.

### 3. Funzione Inversa della Funzione Potenza

Data la funzione $f(x) = x^{\alpha}$ con $\alpha \in \mathbb{R}$ e $\alpha > 0$, definita per $x \ge 0$, è possibile determinare la sua [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|funzione inversa]]. Per trovare l'inversa, si risolve l'equazione $y = x^{\alpha}$ rispetto a $x$:
$$
\begin{aligned}
y &= x^{\alpha} \\
(y)^{1/\alpha} &= (x^{\alpha})^{1/\alpha} \\
y^{1/\alpha} &= x^{\alpha \cdot (1/\alpha)} \\
y^{1/\alpha} &= x
\end{aligned}
$$
La funzione inversa è quindi $f^{-1}(y) = y^{1/\alpha}$. Anch'essa è una funzione potenza, con esponente reciproco rispetto a quella di partenza.

### 4. Distinzione tra Radice Aritmetica e Funzione Potenza

Si presenta una distinzione cruciale quando si confrontano la funzione radice e la funzione potenza con esponente razionale, come in $x^{1/3}$.
-   La funzione $f(x) = x^{1/3}$, intesa come funzione potenza con esponente reale, è definita per $x \ge 0$.
-   La funzione $g(x) = \sqrt[3]{x}$, intesa come radice cubica, è definita per ogni $x \in \mathbb{R}$.

Le due funzioni **coincidono** solo nel primo quadrante (per $x \ge 0$). La funzione radice cubica $g(x)$ può essere vista come un **prolungamento** della funzione potenza $f(x)$ al terzo quadrante (per $x < 0$).

Non è possibile scrivere $\sqrt[3]{x} = x^{1/3}$ per $x < 0$ senza incorrere in contraddizioni. Se ciò fosse possibile, si potrebbero applicare le proprietà delle potenze, portando a risultati errati. Ad esempio, per $x<0$:
$$\sqrt[3]{x} = x^{1/3} = x^{2/6} = (x^2)^{1/6} = \sqrt[6]{x^2}$$
Poiché $x^2 > 0$ per $x < 0$, il risultato $\sqrt[6]{x^2}$ sarebbe positivo, mentre $\sqrt[3]{x}$ per $x<0$ è negativo. Questa contraddizione dimostra che l'identità non può essere estesa ai numeri negativi. In sintesi, quando si lavora con esponenti reali non interi, ci si restringe per convenzione al dominio $x \ge 0$ (o $x > 0$) per preservare in modo coerente le proprietà delle potenze.

## Disequazioni Irrazionali

Le disequazioni irrazionali sono del tipo $\sqrt[n]{P(x)} > Q(x)$ o $\sqrt[n]{P(x)} < Q(x)$, dove $P(x)$ e $Q(x)$ sono polinomi. La strategia risolutiva dipende dalla parità dell'indice $n$.

### 1. Caso $n$ Dispari

La funzione $f(t) = t^n$ (con $n$ dispari) e la sua inversa $f^{-1}(t) = \sqrt[n]{t}$ sono **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente crescenti]]** su tutto $\mathbb{R}$. Grazie a questa proprietà, è possibile elevare entrambi i membri della disequazione alla potenza $n$ mantenendo lo stesso verso della disuguaglianza, senza imporre condizioni di esistenza diverse da quelle intrinseche a $P(x)$ e $Q(x)$.

-   Per $\sqrt[n]{P(x)} < Q(x)$, si risolve $P(x) < [Q(x)]^n$.
-   Per $\sqrt[n]{P(x)} > Q(x)$, si risolve $P(x) > [Q(x)]^n$.

**Esempio:** Risolvere $\sqrt[3]{x(x^2-1)} > x-1$.
1.  Poiché l'indice è dispari (3), si eleva al cubo:
    $$x(x^2-1) > (x-1)^3$$
2.  Si sviluppano i termini:
    $$x^3 - x > x^3 - 3x^2 + 3x - 1$$
3.  Si semplifica e si risolve la disequazione di secondo grado:
    $$3x^2 - 4x + 1 > 0$$
4.  Le radici dell'equazione associata $3x^2 - 4x + 1 = 0$ sono $x_1 = 1/3$ e $x_2 = 1$.
5.  La parabola ha concavità verso l'alto ($a=3>0$), quindi la soluzione per valori esterni è $x < 1/3 \lor x > 1$, che può essere scritta come l'intervallo $(-\infty, 1/3) \cup (1, +\infty)$.

### 2. Caso $n$ Pari

La funzione $f(t) = t^n$ con $n$ pari è strettamente crescente solo per $t \ge 0$. Ciò impone una discussione più attenta che richiede la risoluzione di sistemi di disequazioni.

**Caso A: $\sqrt[n]{P(x)} < Q(x)$**

Per poter elevare a potenza entrambi i membri, essi devono essere non negativi. Questo porta a un sistema di tre condizioni che devono valere simultaneamente:
1.  **Esistenza della radice:** $P(x) \ge 0$.
2.  **Positività del secondo membro:** Poiché $\sqrt[n]{P(x)} \ge 0$, deve essere anche $Q(x) > 0$.
3.  **Elevamento a potenza:** Essendo entrambi i membri non negativi, si può elevare alla $n$: $P(x) < [Q(x)]^n$.

La soluzione è data dall'intersezione delle soluzioni delle tre disequazioni:
$$ \begin{cases} P(x) \ge 0 \\ Q(x) > 0 \\ P(x) < [Q(x)]^n \end{cases} $$

**Caso B: $\sqrt[n]{P(x)} > Q(x)$**

Si analizzano due scenari distinti, e la soluzione finale è l'**unione** delle soluzioni dei due casi.

-   **Sistema 1:** Se $Q(x) < 0$, la disequazione è vera purché la radice esista. Una quantità non negativa (la radice) è sempre maggiore di una negativa.
    $$ \begin{cases} P(x) \ge 0 \\ Q(x) < 0 \end{cases} $$
-   **Sistema 2:** Se $Q(x) \ge 0$, entrambi i membri sono non negativi e si può elevare alla potenza $n$ mantenendo il verso.
    $$ \begin{cases} Q(x) \ge 0 \\ P(x) > [Q(x)]^n \end{cases} $$
    (Nota: La condizione $P(x) \ge 0$ è implicitamente soddisfatta dalla seconda disequazione, rendendola superflua in questo sistema).

**Esempio:** Risolvere $\sqrt{2-x^2} > 2x-1$.
-   **Sistema 1:**
    $$ \begin{cases} 2-x^2 \ge 0 \\ 2x-1 < 0 \end{cases} \implies \begin{cases} -\sqrt{2} \le x \le \sqrt{2} \\ x < 1/2 \end{cases} $$
    La soluzione del primo sistema è $S_1 = [-\sqrt{2}, 1/2)$.
-   **Sistema 2:**
    $$ \begin{cases} 2x-1 \ge 0 \\ 2-x^2 > (2x-1)^2 \end{cases} \implies \begin{cases} x \ge 1/2 \\ 5x^2 - 4x - 1 < 0 \end{cases} $$
    La disequazione $5x^2 - 4x - 1 < 0$ ha soluzioni $-1/5 < x < 1$. Intersecandola con $x \ge 1/2$, si ottiene la soluzione del secondo sistema: $S_2 = [1/2, 1)$.
-   **Soluzione finale:** Si uniscono le soluzioni dei due sistemi:
    $$ S = S_1 \cup S_2 = [-\sqrt{2}, 1/2) \cup [1/2, 1) = [-\sqrt{2}, 1) $$

## Funzioni Esponenziali e Logaritmiche

### 1. La Funzione Esponenziale

La funzione esponenziale è definita come $f(x) = a^x$, dove la base $a$ è una costante positiva ($a>0$) e l'esponente $x$ è la variabile. Il caso $a=1$ è banale ($f(x)=1$).
-   **Dominio:** $\mathbb{R}$.
-   **Codominio:** $(0, +\infty)$.
-   **Monotonia:**
    -   Se $a > 1$, la funzione è **strettamente crescente**.
    -   Se $0 < a < 1$, la funzione è **strettamente decrescente**.
-   Il grafico passa sempre per il punto $(0, 1)$, poiché $a^0 = 1$ per ogni $a>0$.

### 2. La Funzione Logaritmo

La funzione logaritmo, $f(x) = \log_a(x)$, è la funzione **inversa** dell'esponenziale. È definita per $a>0$ e $a \ne 1$.
-   **Dominio:** $(0, +\infty)$ (il codominio dell'esponenziale).
-   **Codominio:** $\mathbb{R}$ (il dominio dell'esponenziale).
-   **Monotonia:** La monotonia del logaritmo ricalca quella dell'esponenziale corrispondente:
    -   Se $a > 1$, la funzione è **strettamente crescente**.
    -   Se $0 < a < 1$, la funzione è **strettamente decrescente**.
-   Il grafico passa sempre per il punto $(1, 0)$, poiché $\log_a(1) = 0$.

### 3. Proprietà Fondamentali e Composizione

Essendo l'una l'inversa dell'altra, la loro composizione restituisce l'argomento di partenza, prestando attenzione ai domini:
-   $a^{\log_a(x)} = x$, per ogni $x > 0$.
-   $\log_a(a^x) = x$, per ogni $x \in \mathbb{R}$.

Le principali proprietà dei logaritmi derivano dalle proprietà delle potenze:
1.  **Logaritmo di un prodotto:** $\log_a(x_1 x_2) = \log_a(x_1) + \log_a(x_2)$, per $x_1, x_2 > 0$.
    *Dimostrazione:* Siano $k_1 = \log_a(x_1)$ e $k_2 = \log_a(x_2)$. Per definizione, $x_1 = a^{k_1}$ e $x_2 = a^{k_2}$.
    $$ x_1 x_2 = a^{k_1} a^{k_2} = a^{k_1+k_2} $$
    Applicando il logaritmo a entrambi i membri:
    $$ \log_a(x_1 x_2) = \log_a(a^{k_1+k_2}) = k_1+k_2 = \log_a(x_1) + \log_a(x_2) $$
2.  **Logaritmo di un quoziente:** $\log_a(\frac{x_1}{x_2}) = \log_a(x_1) - \log_a(x_2)$, per $x_1, x_2 > 0$.