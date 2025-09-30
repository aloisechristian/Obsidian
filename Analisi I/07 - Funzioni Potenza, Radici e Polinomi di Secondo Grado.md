# La Funzione Potenza e le Funzioni Polinomiali

## Introduzione alla Funzione Potenza con Esponente Naturale

### Definizione e Casi Elementari
Si definisce **funzione potenza** una funzione nella forma:
$$f(x) = x^n$$
dove l'esponente $n$ è un numero naturale ($n \in \mathbb{N}$). Il significato di $x^n$ è la moltiplicazione di $x$ per se stesso $n$ volte.

Analizziamo i casi più semplici:
1.  **Caso $n=0$**: La funzione $f(x) = x^0$ è definita per $x \neq 0$ come $x^0=1$. Si può prolungare nel punto $x=0$ ponendo per convenzione $f(0)=1$. La funzione si identifica quindi con la funzione costante $f(x)=1$, il cui grafico è una retta orizzontale parallela all'asse delle ascisse.
2.  **Caso $n=1$**: La funzione è $f(x) = x$, nota come **funzione identità**. Il suo grafico è la bisettrice del primo e del terzo quadrante. È una funzione [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|biettiva]].

### Distinzione tra Esponente Pari e Dispari
L'andamento e le proprietà della funzione $x^n$ (per $n \ge 2$) dipendono in modo cruciale dalla parità dell'esponente $n$.

*   **Se $n$ è pari**: La funzione è **pari**, poiché $f(-x) = (-x)^n = x^n = f(x)$. Ciò implica che il suo grafico è simmetrico rispetto all'asse delle ordinate (asse y). Il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|dominio]] è l'intero insieme dei numeri reali $\mathbb{R}$, mentre il [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Estensione dei Concetti alle Funzioni Reali|codominio]] (o insieme delle immagini) è l'intervallo $[0, +\infty)$, dato che un numero elevato a una potenza pari è sempre non negativo.
*   **Se $n$ è dispari**: La funzione è **dispari**, poiché $f(-x) = (-x)^n = -x^n = -f(x)$. Il suo grafico è quindi simmetrico rispetto all'origine degli assi. Sia il dominio che il codominio coincidono con l'insieme dei numeri reali $\mathbb{R}$.

### Monotonia e Invertibilità
Per semplificare lo studio, si analizza inizialmente il comportamento della funzione ristretta all'intervallo $[0, +\infty)$. In questo intervallo, la funzione $g: [0, +\infty) \to [0, +\infty)$ definita da $g(x) = x^n$ è **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente crescente]]** per ogni $n \ge 1$.

Essendo strettamente monotona, la funzione $g$ è [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|iniettiva]]. Poiché il suo codominio coincide con l'intervallo di arrivo, è anche [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Suriettiva (o Suriezione)|suriettiva]]. Pertanto, la funzione $g$ è **[[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|invertibile]]**.

L'analisi dell'invertibilità su tutto il dominio $\mathbb{R}$ porta a due scenari distinti:
*   **Caso $n$ dispari**: La funzione è strettamente crescente su tutto $\mathbb{R}$ e suriettiva da $\mathbb{R}$ in $\mathbb{R}$. Di conseguenza, è biettiva e **invertibile su tutto il suo dominio**.
*   **Caso $n$ pari**: La funzione è strettamente decrescente in $(-\infty, 0]$ e strettamente crescente in $[0, +\infty)$. Non essendo globalmente monotona, non è iniettiva su $\mathbb{R}$ (ad esempio, $f(a) = f(-a)$ per $a \neq 0$). Pertanto, **non è invertibile su $\mathbb{R}$**. Per definire un'inversa, è necessario restringere il dominio a un intervallo in cui la funzione sia monotona, tipicamente $[0, +\infty)$.

La funzione inversa della funzione potenza $y=x^n$ (o della sua restrizione) è la **funzione radice n-esima**, denotata come $x = \sqrt[n]{y}$.

## Risoluzione di Equazioni e Disequazioni

### Caso con Esponente $n$ Dispari
Data la sua invertibilità su tutto $\mathbb{R}$, la risoluzione è diretta. La funzione e la sua inversa sono strettamente crescenti, pertanto le disuguaglianze si conservano.

*   **Equazione $x^n = a$**: Per ogni $a \in \mathbb{R}$, esiste un'unica soluzione reale. Applicando la funzione inversa (radice n-esima) a entrambi i membri, si ottiene:
    $$x = \sqrt[n]{a}$$
*   **Disequazione $x^n < a$**: Poiché la funzione radice n-esima (con $n$ dispari) è strettamente crescente, essa preserva il verso della disuguaglianza:
    $$\sqrt[n]{x^n} < \sqrt[n]{a} \implies x < \sqrt[n]{a}$$
*   **Disequazione $x^n > a$**: Analogamente, si ottiene:
    $$x > \sqrt[n]{a}$$
Per le equazioni e disequazioni che coinvolgono la funzione radice con indice dispari, si applica la sua funzione inversa, ovvero la potenza n-esima, che è anch'essa strettamente crescente. Ad esempio, da $\sqrt[n]{x} = a$ si ricava $x = a^n$.

### Caso con Esponente $n$ Pari
Questo caso richiede maggiore attenzione a causa del codominio e della non-iniettività globale.

*   **Equazione $x^n = a$**: Il codominio di $x^n$ è $[0, +\infty)$.
    *   Se $a < 0$, l'equazione non ha soluzioni reali.
    *   Se $a = 0$, l'equazione ha un'unica soluzione $x=0$.
    *   Se $a > 0$, si inverte la funzione nella sua restrizione a $[0, +\infty)$, trovando la soluzione positiva $x = \sqrt[n]{a}$. A causa della simmetria (funzione pari), esiste anche la soluzione opposta. Le soluzioni sono quindi due:
        $$x = \pm \sqrt[n]{a}$$
*   **Disequazione $x^n < a$**:
    *   Se $a \le 0$, la disequazione non ha soluzioni reali.
    *   Se $a > 0$, la disequazione equivale a $|x|^n < a$, che a sua volta è $|x| < \sqrt[n]{a}$. La soluzione completa è:
        $$-\sqrt[n]{a} < x < \sqrt[n]{a}$$
*   **Disequazione $x^n > a$**:
    *   Se $a < 0$, la disequazione è sempre verificata per ogni $x \in \mathbb{R}$, poiché $x^n \ge 0$.
    *   Se $a \ge 0$, la disequazione equivale a $|x| > \sqrt[n]{a}$. La soluzione completa è:
        $$x < -\sqrt[n]{a} \quad \lor \quad x > \sqrt[n]{a}$$
*   **Disequazione con radice $\sqrt[n]{x} < a$**:
    *   Innanzitutto, si deve imporre la **condizione di esistenza** della radice con indice pari: $x \ge 0$.
    *   Se $a \le 0$, la disequazione non ha soluzioni, poiché la radice è sempre non negativa.
    *   Se $a > 0$, si può elevare alla potenza $n$ entrambi i membri (essendo la funzione potenza crescente per basi non negative): $x < a^n$. Intersecando questa soluzione con la condizione di esistenza, si ottiene:
        $$0 \le x < a^n$$

#### Esempio
Risolvere la disequazione $\sqrt{1-x} < 2$. (Notazione: $\sqrt{}$ indica una radice quadrata, $n=2$)

1.  **Condizione di Esistenza**: L'insieme di definizione richiede che il radicando sia non negativo: $1-x \ge 0 \implies x \le 1$.
2.  **Risoluzione**: Poiché entrambi i membri sono positivi ($2>0$), possiamo elevare al quadrato preservando la disuguaglianza:
    $$(\sqrt{1-x})^2 < 2^2 \implies 1-x < 4 \implies -x < 3 \implies x > -3$$
3.  **Sistema**: Si intersecano le due condizioni per trovare la soluzione finale:
    $$\begin{cases} x \le 1 \\ x > -3 \end{cases}$$
    La soluzione è l'intervallo $(-3, 1]$.

## Estensione a Esponenti Interi Negativi

Consideriamo la funzione $f(x) = x^n$ con $n \in \mathbb{Z}^-$. Sia $n = -m$, con $m$ intero positivo ($m \in \mathbb{N}$). La funzione si scrive come:
$$f(x) = x^{-m} = \frac{1}{x^m}$$
Il **dominio di definizione** esclude i valori che annullano il denominatore. Poiché $x^m = 0 \iff x=0$, il dominio è $\mathbb{R} \setminus \{0\}$.

Le proprietà di simmetria e il codominio sono ereditati dall'esponente $m$:
*   Se $m$ è **pari**, $f(x)$ è una funzione **pari**. Il codominio è $(0, +\infty)$.
*   Se $m$ è **dispari**, $f(x)$ è una funzione **dispari**. Il codominio è $\mathbb{R} \setminus \{0\}$. Se $m$ è dispari, la funzione è strettamente decrescente negli intervalli $(-\infty, 0)$ e $(0, +\infty)$, ma **non è strettamente decrescente su tutto il suo dominio**.

Il grafico di queste funzioni presenta un **asintoto verticale** in $x=0$ e un **asintoto orizzontale** in $y=0$.

## Funzioni Polinomiali e Razionali

### Funzione Polinomiale
Dati $n+1$ coefficienti reali $a_0, a_1, \dots, a_n$, con $a_n \neq 0$, una **funzione polinomiale di grado n** è una funzione definita in $\mathbb{R}$:
$$P(x) = a_n x^n + a_{n-1} x^{n-1} + \dots + a_1 x + a_0 = \sum_{k=0}^{n} a_k x^k$$
Il dominio di ogni funzione polinomiale è l'intero insieme dei numeri reali $\mathbb{R}$.

### Funzione Razionale
Una **funzione razionale** è definita come il rapporto tra due funzioni polinomiali, $P_1(x)$ e $P_2(x)$, con $P_2(x)$ non identicamente nullo:
$$f(x) = \frac{P_1(x)}{P_2(x)}$$
Il dominio di una funzione razionale è l'insieme dei numeri reali che non annullano il polinomio al denominatore, ovvero $D = \{x \in \mathbb{R} \mid P_2(x) \neq 0\}$. Se il denominatore è di grado 0 (una costante non nulla), la funzione razionale è a sua volta un polinomio.

## Analisi dei Polinomi di Secondo Grado

Un polinomio di secondo grado ha la forma $f(x) = ax^2 + bx + c$, con $a \neq 0$. Il suo grafico è una parabola.

### Scomposizione tramite Completamento del Quadrato
Per studiare la funzione, è utile riscriverla tramite la tecnica del **completamento del quadrato**:
$$f(x) = a \left[ \left(x + \frac{b}{2a}\right)^2 - \frac{b^2 - 4ac}{4a^2} \right]$$
Definendo il **discriminante** $\Delta = b^2 - 4ac$, la forma finale è:
$$f(x) = a \left[ \left(x + \frac{b}{2a}\right)^2 - \frac{\Delta}{4a^2} \right]$$
Lo studio del segno di $\Delta$ determina la natura delle soluzioni dell'equazione $f(x)=0$.

#### Caso 1: $\Delta > 0$ (Due radici reali e distinte)
L'equazione $f(x)=0$ ammette due soluzioni reali e distinte (le radici del polinomio):
$$x_{1,2} = \frac{-b \pm \sqrt{\Delta}}{2a}$$
Il polinomio può essere scomposto nella forma:
$$f(x) = a(x-x_1)(x-x_2)$$
**Interpretazione grafica**: La parabola interseca l'asse delle ascisse in due punti distinti, $x_1$ e $x_2$. Per risolvere $f(x)>0$: se $a>0$ (concavità verso l'alto), la funzione è positiva per valori esterni alle radici ($x<x_1 \lor x>x_2$); se $a<0$ (concavità verso il basso), è positiva per valori interni ($x_1 < x < x_2$).

#### Caso 2: $\Delta = 0$ (Una radice reale con molteplicità 2)
L'equazione $f(x)=0$ ammette un'unica soluzione reale $x_1 = -\frac{b}{2a}$ (due radici coincidenti). La scomposizione è:
$$f(x) = a \left(x - x_1\right)^2$$
**Interpretazione grafica**: La parabola è tangente all'asse delle ascisse nel suo vertice, il punto di ascissa $x_1$. La funzione $f(x)$ ha segno concorde a quello di $a$ per ogni $x \neq x_1$, e si annulla solo nel vertice.

#### Caso 3: $\Delta < 0$ (Nessuna radice reale)
Il termine $\left(x + \frac{b}{2a}\right)^2 - \frac{\Delta}{4a^2}$ è sempre strettamente positivo, essendo la somma di un quadrato (non negativo) e di un termine positivo ($-\Delta/4a^2 > 0$).
Il segno di $f(x)$ è determinato unicamente dal segno del coefficiente $a$ ed è costante per ogni $x \in \mathbb{R}$.
*   Se $a > 0$, $f(x) > 0$ per ogni $x \in \mathbb{R}$.
*   Se $a < 0$, $f(x) < 0$ per ogni $x \in \mathbb{R}$.
**Interpretazione grafica**: La parabola non interseca mai l'asse delle ascisse. Giace interamente nel semipiano superiore (se $a>0$) o nel semipiano inferiore (se $a<0$).