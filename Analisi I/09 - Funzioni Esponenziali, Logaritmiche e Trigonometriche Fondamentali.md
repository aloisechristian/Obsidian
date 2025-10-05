# Analisi di Funzioni Esponenziali, Logaritmiche e Trigonometriche

## La Funzione Esponenziale

### Definizione e Dominio
La funzione esponenziale è definita come $f(x) = a^x$, dove la base $a$ è una costante fissata e l'esponente $x$ è la variabile indipendente. Per definizione, la base $a$ deve essere un numero reale strettamente maggiore di zero ($a > 0$).

Il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|dominio]] della funzione esponenziale, ovvero l'insieme dei valori che la variabile $x$ può assumere, è l'intero insieme dei numeri reali, $\mathbb{R}$. Il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|codominio]] (o insieme delle immagini) è l'intervallo $(0, +\infty)$. Questo significa che $a^x$ è sempre una quantità strettamente positiva per qualsiasi $x \in \mathbb{R}$.

### Monotonia e Casi Particolari
L'andamento della funzione esponenziale dipende dal valore della base $a$:

1.  **Caso $a=1$**: La funzione diventa $f(x) = 1^x = 1$. Si tratta di una funzione costante, rappresentata graficamente da una retta parallela all'asse delle ascisse di equazione $y=1$. Poiché non è [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|iniettiva]], questo caso non è di interesse per lo studio dell'invertibilità e viene generalmente escluso.

2.  **Caso $a > 1$**: La funzione $f(x) = a^x$ è **strettamente crescente** su tutto il suo dominio. Un caso notevole è la funzione esponenziale con base il numero di Nepero, $e \approx 2.718...$. Poiché $e > 1$, la funzione $f(x) = e^x$ è strettamente crescente. Quando non si specifica la base, per "funzione esponenziale" si intende convenzionalmente quella con base $e$.

3.  **Caso $0 < a < 1$**: La funzione $f(x) = a^x$ è **strettamente decrescente** su tutto il suo dominio. Ad esempio, la funzione $f(x) = (1/2)^x$.

In entrambi i casi $a>1$ e $0<a<1$, il grafico della funzione passa per il punto di coordinate $(0, 1)$, poiché $a^0 = 1$ per ogni $a > 0$.

## La Funzione Logaritmica

### Definizione come Funzione Inversa
Poiché la funzione esponenziale è [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente monotona]] (crescente o decrescente) per $a>0$ e $a \neq 1$, essa è iniettiva e quindi [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|invertibile]]. La sua [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|funzione inversa]] è la **funzione logaritmica** in base $a$, denotata con $\log_a$.

La relazione che lega le due funzioni è:
$$y = a^x \iff x = \log_a(y)$$
Il logaritmo in base $a$ di un numero $y$ è l'esponente che bisogna dare ad $a$ per ottenere $y$.

Il dominio della funzione logaritmica coincide con il codominio della funzione esponenziale, quindi è l'intervallo $(0, +\infty)$. Ciò implica che **l'argomento di un logaritmo deve essere sempre strettamente positivo**. Il codominio della funzione logaritmica è invece l'intero insieme dei numeri reali, $\mathbb{R}$.

La monotonia della funzione logaritmica dipende dalla base $a$, in accordo con quella della sua inversa esponenziale:
- Se $a > 1$, $\log_a(x)$ è **strettamente crescente**.
- Se $0 < a < 1$, $\log_a(x)$ è **strettamente decrescente**.

Il grafico della funzione logaritmica passa per il punto $(1, 0)$, che è il simmetrico del punto $(0, 1)$ del grafico esponenziale rispetto alla bisettrice $y=x$.

### Composizione di Funzioni Inverse
La composizione di una funzione con la sua inversa restituisce l'identità, ma è fondamentale prestare attenzione ai rispettivi domini di definizione:

- $a^{\log_a(x)} = x$: Questa identità è valida **per ogni $x > 0$**, poiché la prima operazione applicata a $x$ è il logaritmo, che richiede un argomento positivo.
- $\log_a(a^x) = x$: Questa identità è valida **per ogni $x \in \mathbb{R}$**, poiché la funzione esponenziale $a^x$ è definita per ogni $x$ reale e produce sempre un risultato positivo, valido come argomento per il logaritmo.

### Proprietà Fondamentali dei Logaritmi
Si dimostrano le seguenti proprietà per $x, x_1, x_2 > 0$, sfruttando le proprietà delle potenze e la definizione di funzione inversa.

1.  **Logaritmo di un prodotto**:
    $$\log_a(x_1 x_2) = \log_a(x_1) + \log_a(x_2)$$
    *Dimostrazione*: Si esprimono $x_1 = a^{\log_a(x_1)}$ e $x_2 = a^{\log_a(x_2)}$. Il loro prodotto è $x_1 x_2 = a^{\log_a(x_1)} \cdot a^{\log_a(x_2)} = a^{\log_a(x_1) + \log_a(x_2)}$. Applicando $\log_a$ ad entrambi i membri si ottiene $\log_a(x_1 x_2) = \log_a(x_1) + \log_a(x_2)$.

2.  **Logaritmo di un quoziente**:
    $$\log_a \left( \frac{x_1}{x_2} \right) = \log_a(x_1) - \log_a(x_2)$$
    *Dimostrazione*: Si esprimono $x_1 = a^{\log_a(x_1)}$ e $x_2 = a^{\log_a(x_2)}$. Il loro rapporto è $x_1/x_2 = a^{\log_a(x_1)} / a^{\log_a(x_2)} = a^{\log_a(x_1) - \log_a(x_2)}$. Applicando $\log_a$ ad entrambi i membri si ottiene la tesi.

3.  **Logaritmo di una potenza**:
    $$\log_a(x^b) = b \cdot \log_a(x)$$
    *Dimostrazione*: Si pone $x = a^{\log_a(x)}$. Elevando alla $b$ si ha $x^b = (a^{\log_a(x)})^b = a^{b \log_a(x)}$. Applicando $\log_a$ ad entrambi i membri, si ottiene $\log_a(x^b) = \log_a(a^{b \log_a(x)}) = b \log_a(x)$.
    Un caso particolare si ha per $b=-1$: $\log_a\left(\frac{1}{x}\right) = \log_a(x^{-1}) = -\log_a(x)$.

4.  **Formula del cambiamento di base**:
    $$\log_a(x) = \frac{\log_b(x)}{\log_b(a)}$$
    *Dimostrazione*: Partendo da $x = a^{\log_a(x)}$ e applicando il logaritmo in base $b$ ad entrambi i membri, si ha $\log_b(x) = \log_b(a^{\log_a(x)})$. Usando la proprietà della potenza, si ottiene $\log_b(x) = \log_a(x) \cdot \log_b(a)$, da cui si ricava la formula isolando $\log_a(x)$.

### Risoluzione di Equazioni e Disequazioni
Per risolvere equazioni e disequazioni esponenziali o logaritmiche, si utilizza la funzione inversa corrispondente. È cruciale considerare la monotonia della funzione applicata:
- Se la funzione è **crescente** (es. $a^x$ o $\log_a(x)$ con $a>1$), il verso della disuguaglianza **si mantiene**.
- Se la funzione è **decrescente** (es. $a^x$ o $\log_a(x)$ con $0<a<1$), il verso della disuguaglianza **si inverte**.

**Esempi:**
- $2^x \ge 3$: La base è $2 > 1$, quindi la funzione $\log_2$ è crescente. Applicandola, si ottiene $\log_2(2^x) \ge \log_2(3)$, da cui $x \ge \log_2(3) \iff x \in [\log_2 3, +\infty)$.
- $(1/2)^x \ge 3$: La base è $1/2 < 1$, quindi $\log_{1/2}$ è decrescente. Applicandola si inverte il verso: $\log_{1/2}((1/2)^x) \le \log_{1/2}(3)$, da cui $x \le \log_{1/2}(3) \iff x \in (-\infty, \log_{1/2} 3]$.
- $\log_{1/3}(x) \ge 5$: Prima si impone la **condizione di esistenza**: $x > 0$. Poi, si applica la funzione esponenziale con base $1/3 < 1$, che è decrescente, invertendo il verso. Si ottiene $(1/3)^{\log_{1/3}(x)} \le (1/3)^5$, da cui $x \le (1/3)^5$. La soluzione finale è l'intersezione delle due condizioni: $0 < x \le (1/3)^5 \iff x \in (0, 1/3^5]$.

## Le Funzioni Circolari (Trigonometriche)

### Misura degli Angoli in Radianti
In analisi matematica, gli angoli si misurano in **radianti**. Dato un angolo con vertice nell'origine, la sua misura in radianti è definita come la lunghezza dell'arco di circonferenza di raggio 1 sotteso dall'angolo stesso.
- Un angolo giro misura $2\pi$ radianti (lunghezza dell'intera circonferenza unitaria).
- Un angolo piatto misura $\pi$ radianti.
- Un angolo retto misura $\pi/2$ radianti.

Un angolo $x$ individua la stessa posizione di un angolo $x + 2k\pi$ per qualsiasi intero $k \in \mathbb{Z}$, a causa della natura ciclica della circonferenza. Il verso di rotazione positivo è convenzionalmente quello antiorario.

### Definizione di Seno e Coseno
Dato un angolo $x$ in radianti, si considera il punto $P$ intercettato sulla circonferenza goniometrica (centro nell'origine e raggio 1). Le coordinate di questo punto definiscono il coseno e il seno dell'angolo:
- **Coseno**: $\cos(x)$ è l'**ascissa** del punto $P$.
- **Seno**: $\sin(x)$ è l'**ordinata** del punto $P$.

Da questa definizione seguono due proprietà fondamentali:
1.  **Limitatezza**: Poiché $P$ si trova sulla circonferenza unitaria, le sue coordinate sono vincolate a variare tra -1 e 1. Dunque:
    $$-1 \le \sin(x) \le 1 \quad \text{e} \quad -1 \le \cos(x) \le 1 \quad \forall x \in \mathbb{R}$$
2.  **Relazione Fondamentale della Trigonometria**: Applicando il teorema di Pitagora al triangolo rettangolo con ipotenusa di lunghezza 1 e cateti di lunghezza $|\cos(x)|$ e $|\sin(x)|$, si ottiene:
    $$\sin^2(x) + \cos^2(x) = 1 \quad \forall x \in \mathbb{R}$$

### La Funzione Seno e la sua Inversa

#### Studio della Funzione Seno
La funzione $f(x) = \sin(x)$ ha come dominio $\mathbb{R}$ e come immagine l'intervallo $[-1, 1]$.
Come osservato, un angolo $x$ e un angolo $x+2k\pi$ individuano lo stesso punto sulla circonferenza goniometrica, e quindi lo stesso valore del seno. Pertanto, la funzione seno è **periodica di periodo $2\pi$**: 
$$\sin(x) = \sin(x+2k\pi) \quad \forall k \in \mathbb{Z}$$
A causa della sua periodicità, la funzione non è iniettiva sull'intero dominio $\mathbb{R}$ e quindi non è globalmente invertibile.

#### L'Arcoseno: Inversione del Seno
Per definire una funzione inversa, si restringe il dominio del seno a un intervallo in cui la funzione sia strettamente monotona. Per convenzione, si sceglie l'intervallo $[-\pi/2, \pi/2]$, dove $\sin(x)$ è strettamente crescente.

La funzione inversa del seno (ristretto a tale intervallo) è chiamata **arcoseno** e si denota con $\arcsin(y) = x$:
- **Dominio**: $y \in [-1, 1]$
- **Codominio**: $x \in [-\pi/2, \pi/2]$

### Risoluzione di Equazioni e Disequazioni con il Seno
Per risolvere un'equazione del tipo $\sin(x) = a$:
- Se $a < -1$ o $a > 1$, non ci sono soluzioni.
- Se $a \in [-1, 1]$, si procede come segue:

1.  **Trovare la soluzione principale**: Si utilizza la funzione arcoseno per trovare l'unica soluzione nell'intervallo $[-\pi/2, \pi/2]$:
    $$x_0 = \arcsin(a)$$
2.  **Trovare la seconda soluzione**: Sulla circonferenza goniometrica, un'altra famiglia di soluzioni si trova nel secondo quadrante (se $x_0>0$) o terzo (se $x_0<0$). Questa è data da:
    $$x_1 = \pi - x_0 = \pi - \arcsin(a)$$
3.  **Generalizzare con la periodicità**: Le soluzioni complete dell'equazione si ottengono aggiungendo i multipli interi del periodo $2\pi$ a entrambe le soluzioni trovate:
    $$\begin{cases} x = x_0 + 2k\pi \\ x = \pi - x_0 + 2k\pi \end{cases} \quad k \in \mathbb{Z}$$

**Esempio:** Risolvere $\sin(x) = 1/2$.
1.  $x_0 = \arcsin(1/2) = \pi/6$.
2.  $x_1 = \pi - \pi/6 = 5\pi/6$.
3.  Le soluzioni generali sono $x = \pi/6 + 2k\pi$ e $x = 5\pi/6 + 2k\pi$, con $k \in \mathbb{Z}$.

La risoluzione di disequazioni come $\sin(x) > a$ o $\sin(x) < a$ si basa sull'individuazione di questi due angoli fondamentali e sull'analisi del grafico della funzione seno o della circonferenza goniometrica per determinare gli intervalli che soddisfano la condizione, tenendo poi conto della periodicità.
### Risoluzione di Equazioni e Disequazioni con il Seno

#### Risoluzione dell'Equazione $\sin(x) = a$
Per risolvere un'equazione del tipo $\sin(x) = a$:
- Se $a < -1$ o $a > 1$, non ci sono soluzioni, poiché il codominio della funzione seno è $[-1, 1]$.
- Se $a \in [-1, 1]$, si procede come segue:

1.  **Trovare la soluzione principale**: Si utilizza la funzione arcoseno per trovare l'unica soluzione nell'intervallo $[-\pi/2, \pi/2]$:
    $$x_0 = \arcsin(a)$$
2.  **Trovare la seconda soluzione**: Sulla circonferenza goniometrica, un'altra famiglia di soluzioni si trova nel secondo quadrante (se $x_0>0$) o terzo (se $x_0<0$). Questa è data da:
    $$x_1 = \pi - x_0 = \pi - \arcsin(a)$$
3.  **Generalizzare con la periodicità**: Le soluzioni complete dell'equazione si ottengono aggiungendo i multipli interi del periodo $2\pi$ a entrambe le soluzioni trovate:
    $$\begin{cases} x = x_0 + 2k\pi \\ x = \pi - x_0 + 2k\pi \end{cases} \quad k \in \mathbb{Z}$$

**Esempio:** Risolvere $\sin(x) = 1/2$.
1.  $x_0 = \arcsin(1/2) = \pi/6$.
2.  $x_1 = \pi - \pi/6 = 5\pi/6$.
3.  Le soluzioni generali sono $x = \pi/6 + 2k\pi$ e $x = 5\pi/6 + 2k\pi$, con $k \in \mathbb{Z}$.

#### Interpretazione Grafica e Risoluzione delle Disequazioni
Per risolvere disequazioni come $\sin(x) > a$ o $\sin(x) < a$, l'approccio più intuitivo è quello grafico. Si analizza il grafico della funzione $y=\sin(x)$ e lo si interseca con la retta orizzontale $y=a$. Le soluzioni dell'equazione associata, $x_0$ e $x_1$, sono le ascisse dei punti di intersezione.

**Caso 1: $\sin(x) > a$**
Risolvere questa disequazione equivale a trovare gli intervalli di $x$ per cui il grafico della funzione seno si trova **al di sopra** della retta $y=a$.
Osservando un periodo, si nota che questo avviene tra le due soluzioni principali $x_0$ e $x_1$.

- Soluzione nell'intervallo di riferimento: $x_0 < x < x_1$.
- Soluzione generale, tenendo conto della periodicità $2\pi$:
  $$x_0 + 2k\pi < x < x_1 + 2k\pi, \quad k \in \mathbb{Z}$$
  Sostituendo le espressioni di $x_0$ e $x_1$:
  $$\arcsin(a) + 2k\pi < x < \pi - \arcsin(a) + 2k\pi, \quad k \in \mathbb{Z}$$

**Caso 2: $\sin(x) < a$**
Questa disequazione è soddisfatta negli intervalli in cui il grafico della funzione seno si trova **al di sotto** della retta $y=a$.
Considerando un periodo, la curva si trova sotto la retta nell'intervallo che va dalla seconda soluzione, $x_1$, fino alla prima soluzione del periodo successivo, ovvero $x_0 + 2\pi$.

- Soluzione nell'intervallo di riferimento: $x_1 < x < x_0 + 2\pi$.
- Soluzione generale, tenendo conto della periodicità:
  $$x_1 + 2k\pi < x < x_0 + 2(k+1)\pi, \quad k \in \mathbb{Z}$$
  Sostituendo le espressioni di $x_0$ e $x_1$:
  $$\pi - \arcsin(a) + 2k\pi < x < \arcsin(a) + 2(k+1)\pi, \quad k \in \mathbb{Z}$$
  Questo rappresenta un unico intervallo che si ripete periodicamente.