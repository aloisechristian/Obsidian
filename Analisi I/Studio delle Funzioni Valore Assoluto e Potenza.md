# La Funzione Valore Assoluto, Simmetrie e Funzioni Potenza

## 3.2 La Funzione Valore Assoluto

### Definizione e Dominio
La funzione **valore assoluto** (o **modulo**) di $x \in \mathbb{R}$ è una funzione definita come:

$$|x| = \begin{cases} x & \text{se } x \ge 0 \\ -x & \text{se } x < 0 \end{cases}$$

*   **[[Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|Dominio]]**: $\mathbb{R}$.
*   **[[Estremi Superiori e Inferiori per Insiemi e Funzioni#Estensione dei Concetti alle Funzioni Reali|Codominio (o insieme delle immagini)]]**: L'[[Insiemi Numerici, Completezza e Estremo Superiore#Intervalli in R|intervallo]] dei numeri reali non negativi, $[0, +\infty)$.

### Proprietà Fondamentali
Per ogni $x, x_1, x_2 \in \mathbb{R}$ valgono le seguenti proprietà cruciali:
1.  **Non-negatività:** $|x| \ge 0$.
2.  **Legge di annullamento:** $|x| = 0 \iff x=0$.
3.  **Parità (Simmetria):** $|-x| = |x|$. La funzione valore assoluto è una funzione pari.
4.  **Moltiplicatività:** $|x_1 \cdot x_2| = |x_1| \cdot |x_2|$.
5.  **Quoziente:** $|\frac{x_1}{x_2}| = \frac{|x_1|}{|x_2|}$, se $x_2 \ne 0$.

### Iniettività e Suriettività
-   La funzione **non è [[Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|iniettiva]]**. Questo segue direttamente dalla proprietà di parità: per ogni $a \ne 0$, si ha $a \ne -a$ ma $f(a) = f(-a) = |a|$. Elementi distinti del dominio hanno la stessa immagine.
-   La funzione **non è [[Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Suriettiva (o Suriezione)|suriettiva]]** se considerata come $f: \mathbb{R} \to \mathbb{R}$. Nessun valore negativo $y < 0$ ha una controimmagine. Tuttavia, è **suriettiva** se considerata come $f: \mathbb{R} \to [0, +\infty)$, poiché il suo insieme delle immagini coincide con questo intervallo.

### Disequazioni con il Valore Assoluto
Sia $R \ge 0$. Valgono le seguenti equivalenze fondamentali:
1.  $|x| \le R \iff -R \le x \le R$
2.  $|x| \ge R \iff x \le -R \lor x \ge R$

**Dimostrazione della prima equivalenza:** Si analizzano i due casi della definizione di modulo.
*   **Caso A ($x \ge 0$)**: La disequazione $|x| \le R$ diventa $x \le R$. L'intersezione con la condizione del caso, $\{x \mid x \ge 0\} \cap \{x \mid x \le R\}$, fornisce la soluzione $\{x \mid 0 \le x \le R\}$.
*   **Caso B ($x < 0$)**: La disequazione $|x| \le R$ diventa $-x \le R$, che, moltiplicando per $-1$, equivale a $x \ge -R$. L'intersezione con la condizione del caso, $\{x \mid x < 0\} \cap \{x \mid x \ge -R\}$, fornisce la soluzione $\{x \mid -R \le x < 0\}$.

L'[[Fondamenti di Teoria degli Insiemi e Funzioni#Operazioni Fondamentali tra Insiemi|unione]] delle soluzioni dei due casi, $[-R, 0) \cup [0, R]$, fornisce la soluzione completa $-R \le x \le R$.

### Interpretazione Grafica
Il [[Prodotto Cartesiano e Assiomi dei Numeri Reali#Il Grafico di una Funzione|grafico]] della funzione $y=|x|$ è composto da due semirette:
-   La bisettrice del primo quadrante, $y=x$, per $x \ge 0$.
-   La bisettrice del secondo quadrante, $y=-x$, per $x < 0$.

L'interpretazione grafica delle disequazioni conferma i risultati analitici:
-   Risolvere $|x| \le R$ equivale a trovare le ascisse $x$ per cui il grafico si trova al di sotto o sulla retta $y=R$.
-   Risolvere $|x| > R$ equivale a trovare le ascisse $x$ per cui il grafico si trova al di sopra della retta $y=R$.

### La Disuguaglianza Triangolare
Per ogni $x_1, x_2 \in \mathbb{R}$, vale la seguente importante disuguaglianza:
$$|x_1 + x_2| \le |x_1| + |x_2|$$

**Dimostrazione:**
Dalla proprietà $|x| \le R \iff -R \le x \le R$, ponendo $R=|x|$, segue che per ogni numero reale vale $-|x| \le x \le |x|$. Applichiamo questa relazione a $x_1$ e $x_2$:
$$-|x_1| \le x_1 \le |x_1|$$
$$-|x_2| \le x_2 \le |x_2|$$
Sommando membro a membro le due disuguaglianze, si ottiene:
$$-|x_1| - |x_2| \le x_1 + x_2 \le |x_1| + |x_2|$$
Che può essere riscritta come:
$$-(|x_1| + |x_2|) \le x_1 + x_2 \le |x_1| + |x_2|$$
Questa espressione è nella forma $-R \le X \le R$, con $X = x_1 + x_2$ e $R = |x_1| + |x_2|$. Per la proposizione iniziale, si conclude che $|X| \le R$, ovvero:
$$|x_1 + x_2| \le |x_1| + |x_2|$$

### Esempio di Risoluzione
Consideriamo la disequazione $|x+3| - 2 > 0$, che equivale a $|x+3| > 2$. Utilizzando l'equivalenza $|f(x)| > R \iff f(x) < -R \lor f(x) > R$, con $f(x)=x+3$ e $R=2$, otteniamo:
$$x+3 < -2 \quad \lor \quad x+3 > 2$$
Le cui soluzioni sono:
$$x < -5 \quad \lor \quad x > -1$$
L'insieme delle soluzioni è quindi $(-\infty, -5) \cup (-1, +\infty)$.

## Simmetrie delle Funzioni: Pari, Dispari e Periodiche

### Definizioni
-   Una funzione $f$ definita in un insieme $X$ si dice **pari** se:
    1.  L'opposto di ogni elemento di $X$ appartiene a $X$.
    2.  $\forall x \in X$ si ha $f(-x) = f(x)$.
    Il grafico di una funzione pari è simmetrico rispetto all'asse delle ordinate.

-   Una funzione $f$ definita in un insieme $X$ si dice **dispari** se:
    1.  L'opposto di ogni elemento di $X$ appartiene a $X$.
    2.  $\forall x \in X$ si ha $f(-x) = -f(x)$.
    Il grafico di una funzione dispari è simmetrico rispetto all'origine.

-   Una funzione $f$ si dice **periodica** di periodo $\tau > 0$ se:
    1.  Per ogni $x \in X$, anche i punti $x+k\tau$ appartengono a $X$, con $k \in \mathbb{Z}$.
    2.  Per ogni $x \in X$ si ha $f(x) = f(x+k\tau)$.

## La Funzione Potenza $f(x) = x^n$

Analizziamo la funzione $f(x) = x^n$ con $n \in \mathbb{N}$.

-   **Caso $n=0$**: La funzione $f(x) = x^0$ è definita per $x \neq 0$ come $x^0=1$. Si prolunga nel punto $x=0$ ponendo $f(0)=1$. La funzione si identifica quindi con la funzione costante $f(x)=1$. Non è né iniettiva né suriettiva su $\mathbb{R}$.
-   **Caso $n=1$**: La funzione $f(x) = x$ è la funzione identità. Il suo grafico è la bisettrice del I e III quadrante. È una funzione [[Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|biettiva]].

### Parità della Funzione Potenza
-   Se **$n$ è pari**, la funzione $f(x)=x^n$ è **pari**: $f(-x) = (-x)^n = x^n = f(x)$.
-   Se **$n$ è dispari**, la funzione $f(x)=x^n$ è **dispari**: $f(-x) = (-x)^n = -x^n = -f(x)$.

### Analisi della Monotonia e Invertibilità

Per studiare la funzione, ne consideriamo la restrizione $g$ all'intervallo $[0, +\infty)$.
-   **Studio su $[0, +\infty)$**: La funzione $g: [0, +\infty) \to [0, +\infty)$ definita da $g(x) = x^n$ è **[[Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente crescente]]**. È anche suriettiva su tale intervallo. Di conseguenza, $g$ è invertibile e la sua [[Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|funzione inversa]] è la **radice n-esima**, $g^{-1}(y) = \sqrt[n]{y}$.

Ora estendiamo l'analisi a tutto $\mathbb{R}$, distinguendo i due casi.

#### Caso 1: $n$ è dispari
-   **Dominio e Codominio**: $f: \mathbb{R} \to \mathbb{R}$.
-   **Monotonia**: È **strettamente crescente** su tutto $\mathbb{R}$.
-   **Invertibilità**: Essendo strettamente monotona, è iniettiva. È anche suriettiva, quindi è **biettiva e invertibile su tutto $\mathbb{R}$**. La sua inversa è $f^{-1}(y) = \sqrt[n]{y}$.
-   **Risoluzione di equazioni e disequazioni**: Poiché la funzione e la sua inversa sono strettamente crescenti, le disuguaglianze si conservano.
    -   $x^n = a \iff x = \sqrt[n]{a}$ (soluzione unica).
    -   $x^n < a \iff x < \sqrt[n]{a}$.
    -   $x^n > a \iff x > \sqrt[n]{a}$.

#### Caso 2: $n$ è pari
-   **Dominio e Codominio**: $f: \mathbb{R} \to [0, +\infty)$.
-   **Monotonia**: La funzione è **strettamente decrescente** in $(-\infty, 0]$ e **strettamente crescente** in $[0, +\infty)$.
-   **Invertibilità**: Essendo pari, **non è iniettiva** e quindi **non è invertibile su $\mathbb{R}$**.
-   **Risoluzione di equazioni**: Per risolvere $x^n=a$:
    -   Se $a < 0$: l'equazione non ha soluzioni reali.
    -   Se $a = 0$: l'equazione ha un'unica soluzione $x=0$.
    -   Se $a > 0$: l'equazione ha **due soluzioni reali opposte**: $x = \pm\sqrt[n]{a}$.
-   **Risoluzione di disequazioni**: Per risolvere $x^n < a$ con $a>0$:
    - La disequazione equivale a $|x|^n < a$, che a sua volta è $|x| < \sqrt[n]{a}$.
    - La soluzione è $-\sqrt[n]{a} < x < \sqrt[n]{a}$.
-   Per risolvere $x^n > a$ con $a \ge 0$:
    - La soluzione è $x < -\sqrt[n]{a} \lor x > \sqrt[n]{a}$.