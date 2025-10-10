# Introduzione ai Numeri Complessi

Il campo dei [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali|numeri reali]] $\mathbb{R}$ è definito da [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^e1bb55|assiomi relativi alle operazioni]], all'[[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^6ced7f|ordinamento]] e alla [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|completezza]]. Tuttavia, questo campo non è algebricamente chiuso, ovvero non è sufficiente per risolvere tutte le equazioni algebriche. Un esempio notevole è l'equazione $x^n = a$ dove $n$ è un numero pari e $a$ è un numero reale negativo. Poiché la [[07 - Funzioni Potenza, Radici e Polinomi di Secondo Grado|funzione potenza]] $f(x) = x^n$ con $n$ pari, definita in $\mathbb{R}$, ha come [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Estensione dei Concetti alle Funzioni Reali|immagine]] l'intervallo $[0, +\infty)$, non esistono soluzioni reali per tale equazione.

Per superare questa limitazione, si introduce un campo numerico più ampio: il **campo dei numeri complessi** $\mathbb{C}$, che si ottiene definendo opportune operazioni sull'insieme $\mathbb{R}^2$.

### 1. Sistemi di Coordinate sul Piano

Prima di definire formalmente i numeri complessi, è utile richiamare i sistemi di coordinate per rappresentare un punto $P$ su un piano.

#### 1.1 Coordinate Cartesiane

In un sistema di riferimento cartesiano ortogonale, un punto $P$ è univocamente identificato da una [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#Definizione per due Insiemi|coppia ordinata]] di numeri reali $(x, y)$, stabilendo una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|corrispondenza biunivoca]] tra i punti del piano e l'insieme $\mathbb{R}^2 = \mathbb{R} \times \mathbb{R}$ (il [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali|prodotto cartesiano]] di $\mathbb{R}$ per se stesso).
- $x$ è l'**ascissa**, ottenuta dalla proiezione ortogonale di $P$ sull'asse delle $x$.
- $y$ è l'**ordinata**, ottenuta dalla proiezione ortogonale di $P$ sull'asse delle $y$.

#### 1.2 Coordinate Polari

Un metodo alternativo per identificare un punto $P$ nel piano è tramite le coordinate polari $(\rho, \theta)$, definite come segue:
- **Modulo (o raggio vettore) $\rho$**: È la distanza del punto $P$ dall'origine $O$. Per definizione, $\rho \ge 0$.
- **Argomento (o anomalia) $\theta$**: È l'angolo, misurato in senso antiorario (positivo), formato dal semiasse positivo delle ascisse e la semiretta passante per $O$ e $P$.

L'argomento $\theta$ non è univocamente determinato. Se $\theta_0$ è un valore valido per l'argomento, lo sono anche tutti gli angoli della forma $\theta_0 + 2k\pi$ con $k \in \mathbb{Z}$. Per garantire l'unicità, si definisce **argomento principale** quel valore di $\theta^*$ tale che $\theta^* \in (-\pi, \pi]$.

### 2. Relazioni tra Coordinate Cartesiane e Polari

È possibile stabilire delle relazioni per convertire le coordinate da un sistema all'altro.

#### 2.1 Da Polari a Cartesiane

Dato un punto $P$ con coordinate polari $(\rho, \theta)$, le sue coordinate cartesiane $(x, y)$ si ottengono tramite le relazioni trigonometriche in un triangolo rettangolo:
$$
\begin{cases}
x = \rho \cos(\theta) \\
y = \rho \sin(\theta)
\end{cases}
$$

#### 2.2 Da Cartesiane a Polari

Dato un punto $P$ con coordinate cartesiane $(x, y)$, le sue coordinate polari $(\rho, \theta)$ si ricavano come segue:
1.  **Modulo $\rho$**: Applicando il teorema di Pitagora, il modulo è dato da:
    $$ \rho = \sqrt{x^2 + y^2} $$ Poiché $\rho$ rappresenta una distanza, si considera solo la radice positiva.
2.  **Argomento $\theta$**: L'argomento si determina risolvendo il sistema di equazioni:
    $$ \begin{cases} \cos(\theta) = \frac{x}{\rho} = \frac{x}{\sqrt{x^2 + y^2}} \\ \sin(\theta) = \frac{y}{\rho} = \frac{y}{\sqrt{x^2 + y^2}} \end{cases} $$

### 3. Costruzione Algebrica dei Numeri Complessi

I numeri complessi vengono definiti formalmente come elementi di $\mathbb{R}^2$, ovvero coppie ordinate di numeri reali $(x, y)$, su cui sono definite le seguenti operazioni di somma e prodotto.

**Definizione (Somma):** Dati due numeri complessi $(x_1, y_1)$ e $(x_2, y_2)$, la loro somma è definita come:
$$ (x_1, y_1) + (x_2, y_2) = (x_1 + x_2, y_1 + y_2) $$

**Definizione (Prodotto):** Dati due numeri complessi $(x_1, y_1)$ e $(x_2, y_2)$, il loro prodotto è definito come:
$$ (x_1, y_1) \cdot (x_2, y_2) = (x_1 x_2 - y_1 y_2, x_1 y_2 + x_2 y_1) $$

Si può verificare che queste operazioni sono commutative, associative e che il prodotto è distributivo rispetto alla somma.

#### 3.1 Elementi Neutri, Opposto e Inverso

- **Elemento neutro della somma**: La coppia $(0, 0)$, poiché $(x, y) + (0, 0) = (x, y)$.
- **Opposto**: Per ogni coppia $(x, y)$, esiste l'opposto $(-x, -y)$ tale che $(x, y) + (-x, -y) = (0, 0)$.
- **Elemento neutro del prodotto**: La coppia $(1, 0)$, poiché $(x, y) \cdot (1, 0) = (x \cdot 1 - y \cdot 0, x \cdot 0 + y \cdot 1) = (x, y)$.
- **Inverso**: Per ogni coppia $(x, y) \neq (0, 0)$, esiste un inverso $(x', y')$ tale che $(x, y) \cdot (x', y') = (1, 0)$. Questa uguaglianza porta al sistema:
  $$
  \begin{cases}
  xx' - yy' = 1 \\
  x'y + xy' = 0
  \end{cases}
  $$
  Risolvendo il sistema si trova:
  $$ (x', y') = \left( \frac{x}{x^2 + y^2}, \frac{-y}{x^2 + y^2} \right) $$

### 4. La Forma Algebrica

#### 4.1 Identificazione con i Numeri Reali

Consideriamo il sottoinsieme dei numeri complessi con la seconda componente nulla, $\mathcal{R} = \{(x, 0) \mid x \in \mathbb{R}\}$. Questo insieme è **stabile** (chiuso) rispetto a somma e prodotto:
- **Somma**: $(x_1, 0) + (x_2, 0) = (x_1 + x_2, 0) \in \mathcal{R}$
- **Prodotto**: $(x_1, 0) \cdot (x_2, 0) = (x_1 x_2 - 0, 0 + 0) = (x_1 x_2, 0) \in \mathcal{R}$

Le operazioni in questo sottoinsieme sono identiche a quelle sui numeri reali. Per convenzione, si identifica la coppia $(x, 0)$ con il numero reale $x$.

#### 4.2 L'Unità Immaginaria

Consideriamo il sottoinsieme degli **immaginari puri**, $\mathcal{I} = \{(0, y) \mid y \in \mathbb{R}\}$. Questo insieme è stabile rispetto alla somma ma non al prodotto.
Definiamo **unità immaginaria** la coppia $(0, 1)$, indicandola con il simbolo $i$. Calcoliamo il suo quadrato:
$$ i^2 = i \cdot i = (0, 1) \cdot (0, 1) = (0 \cdot 0 - 1 \cdot 1, 0 \cdot 1 + 1 \cdot 0) = (-1, 0) $$
Poiché abbiamo identificato la coppia $(-1, 0)$ con il numero reale $-1$, otteniamo la relazione fondamentale:
$$ i^2 = -1 $$
Questo risolve il problema iniziale: abbiamo trovato un numero il cui quadrato è negativo.

#### 4.3 Potenze di $i$
Le potenze successive di $i$ seguono un ciclo di periodo 4:
- $i^0 = (1,0) = 1$
- $i^1 = (0,1) = i$
- $i^2 = (-1,0) = -1$
- $i^3 = i^2 \cdot i = (-1, 0) \cdot (0, 1) = (0, -1) = -i$
- $i^4 = i^2 \cdot i^2 = (-1)(-1) = 1$
- $i^5 = i^4 \cdot i = 1 \cdot i = i$, e così via.

#### 4.4 Dalle Coppie alla Forma Algebrica

Ogni numero complesso $(x, y)$ può essere decomposto come:
$$ (x, y) = (x, 0) + (0, y) $$
Inoltre, si può dimostrare che $(0, y) = (0, 1) \cdot (y, 0)$. Utilizzando le identificazioni $x \leftrightarrow (x,0)$, $y \leftrightarrow (y,0)$ e $i \leftrightarrow (0,1)$, si ottiene:
$$ (x, y) = (x, 0) + (0, 1)(y, 0) = x + i y $$ 
Questa espressione, $z = x + iy$, è chiamata **forma algebrica** del numero complesso $z$. In essa:
- $x = \text{Re}(z)$ è la **parte reale** di $z$.
- $y = \text{Im}(z)$ è il **coefficiente dell'immaginario** di $z$.

### 5. Definizioni e Rappresentazione Geometrica

- **Numero complesso coniugato**: Dato $z = x + iy$, il suo coniugato è $\bar{z} = x - iy$. Geometricamente, il punto che rappresenta $\bar{z}$ è il simmetrico di $z$ rispetto all'asse reale.
- **Modulo**: Dato $z = x + iy$, il suo modulo è il numero reale non negativo $|z| = \sqrt{x^2 + y^2}$, che coincide con il modulo $\rho$ delle coordinate polari. Un numero complesso, il suo opposto e il suo coniugato hanno lo stesso modulo: $|z| = |-z| = |\bar{z}|$.

I numeri complessi possono essere rappresentati come punti su un piano, detto **Piano di Gauss**, dove l'asse delle ascisse è l'**asse reale** (contenente i numeri con parte immaginaria nulla) e l'asse delle ordinate è l'**asse immaginario** (contenente gli immaginari puri).

### 6. Forma Trigonometrica

Sostituendo le formule di conversione da coordinate polari a cartesiane ($x = \rho\cos\theta$, $y = \rho\sin\theta$) nella forma algebrica, si ottiene:
$$ z = x + iy = \rho\cos(\theta) + i(\rho\sin(\theta)) = \rho(\cos(\theta) + i\sin(\theta)) $$
Questa è la **forma trigonometrica** del numero complesso $z$. Spesso viene indicata in modo compatto come $z = [\rho, \theta]$.

#### Esempio 1: Da forma algebrica a trigonometrica

Dato $z = 1+i$, si ha $x=1$ e $y=1$. 
- Calcolo del modulo: $\rho = \sqrt{1^2 + 1^2} = \sqrt{2}$.
- Calcolo dell'argomento: $\cos(\theta) = \frac{1}{\sqrt{2}} = \frac{\sqrt{2}}{2}$ e $\sin(\theta) = \frac{1}{\sqrt{2}} = \frac{\sqrt{2}}{2}$. L'argomento principale è $\theta = \frac{\pi}{4}$.
La forma trigonometrica è $z = \sqrt{2}\left(\cos\left(\frac{\pi}{4}\right) + i\sin\left(\frac{\pi}{4}\right)\right)$.

#### Esempio 2: Da forma trigonometrica a algebrica

Dato un numero complesso con $\rho=1$ e $\theta = \frac{\pi}{2}$.
- Calcolo di $x$: $x = 1 \cdot \cos(\frac{\pi}{2}) = 1 \cdot 0 = 0$.
- Calcolo di $y$: $y = 1 \cdot \sin(\frac{\pi}{2}) = 1 \cdot 1 = 1$.
Il numero in forma algebrica è $z = 0 + i \cdot 1 = i$.

### 7. Operazioni in Forma Trigonometrica

La forma trigonometrica semplifica notevolmente le operazioni di prodotto, quoziente e potenza.

#### 7.1 Prodotto

Dati $z_1 = \rho_1(\cos\theta_1 + i\sin\theta_1)$ e $z_2 = \rho_2(\cos\theta_2 + i\sin\theta_2)$, il loro prodotto è:
$$
\begin{align*}
z_1 z_2 &= \rho_1 \rho_2 (\cos\theta_1 + i\sin\theta_1)(\cos\theta_2 + i\sin\theta_2) \\
&= \rho_1 \rho_2 [(\cos\theta_1\cos\theta_2 - \sin\theta_1\sin\theta_2) + i(\cos\theta_1\sin\theta_2 + \sin\theta_1\cos\theta_2)] \\
&= \rho_1 \rho_2 [\cos(\theta_1+\theta_2) + i\sin(\theta_1+\theta_2)]
\end{align*}
$$
In notazione compatta, $z_1 \cdot z_2 = [\rho_1 \rho_2, \theta_1 + \theta_2]$.
Il modulo del prodotto è il prodotto dei moduli, e l'argomento è la somma degli argomenti.

#### 7.2 Potenza (Formula di De Moivre)

Per ogni intero $n$, dato $z = [\rho, \theta]$, la sua potenza $n$-esima si ottiene applicando ripetutamente la regola del prodotto:
$$ z^n = [\rho^n, n\theta] \implies z^n = \rho^n(\cos(n\theta) + i\sin(n\theta)) $$
Questa formula è nota come **Formula di De Moivre**. Si estende anche a esponenti interi negativi:
$$ z^{-n} = \frac{1}{z^n} = \frac{1}{[\rho^n, n\theta]} = [\rho^{-n}, -n\theta] $$

#### 7.3 Quoziente

Dati $z_1 = [\rho_1, \theta_1]$ e $z_2 = [\rho_2, \theta_2]$ (con $z_2 \neq 0$), il loro quoziente può essere visto come $z_1 \cdot z_2^{-1}$:
$$ \frac{z_1}{z_2} = z_1 \cdot z_2^{-1} = [\rho_1, \theta_1] \cdot [\rho_2^{-1}, -\theta_2] = [\rho_1 \rho_2^{-1}, \theta_1 - \theta_2] $$
In notazione compatta, $\frac{z_1}{z_2} = \left[\frac{\rho_1}{\rho_2}, \theta_1 - \theta_2\right]$.
Il modulo del quoziente è il quoziente dei moduli, e l'argomento è la differenza degli argomenti.