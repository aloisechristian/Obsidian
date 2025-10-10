# Introduzione ai Sistemi di Coordinate e ai Numeri Complessi

## 1. Sistemi di Coordinate sul Piano

Per rappresentare un punto $P$ su un piano, si utilizzano principalmente due sistemi di coordinate.

### 1.1 Coordinate Cartesiane

Un punto $P$ è univocamente identificato da una [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#Definizione per due Insiemi|coppia ordinata]] di numeri reali $(x, y)$, stabilendo una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|corrispondenza biunivoca]] tra i punti del piano e l'insieme $\mathbb{R}^2$, definito come il [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali|prodotto cartesiano]] di $\mathbb{R}$ per se stesso.
- $x$ è l'**ascissa**, la proiezione ortogonale di $P$ sull'asse delle $x$.
- $y$ è l'**ordinata**, la proiezione ortogonale di $P$ sull'asse delle $y$.

### 1.2 Coordinate Polari

Un metodo alternativo per individuare un punto $P$ è tramite le coordinate polari $(\rho, \theta)$:
1.  **Modulo $\rho$**: È la distanza del punto $P$ dall'origine $O$. Essendo una distanza, $\rho \ge 0$.
2.  **Argomento $\theta$**: È l'angolo, misurato in verso antiorario (positivo), formato dal semiasse positivo delle ascisse e la semiretta uscente dall'origine $O$ e passante per $P$.

Mentre una coppia $(\rho, \theta)$ determina un unico punto, il viceversa non è vero. Un punto $P$ non determina un angolo $\theta$ in modo univoco, poiché rotazioni complete di $2\pi$ riportano la semiretta nella stessa posizione. Pertanto, tutti gli angoli nella forma $\theta + 2k\pi$ con $k \in \mathbb{Z}$ individuano lo stesso punto. L'angolo compreso nell'intervallo $(-\pi, \pi]$ è detto **argomento principale**.

## 2. Relazione tra Coordinate Cartesiane e Polari

Le relazioni per convertire le coordinate da un sistema all'altro si deducono da un triangolo rettangolo con ipotenusa $\rho$ e cateti $x$ e $y$.

-   **Da Polari a Cartesiane:**
    $$x = \rho \cos(\theta)$$
    $$y = \rho \sin(\theta)$$
-   **Da Cartesiane a Polari:**
    Applicando il teorema di Pitagora, $\rho^2 = x^2 + y^2$, da cui si ottiene il modulo (considerando la radice positiva poiché $\rho$ è una distanza):
    $$\rho = \sqrt{x^2 + y^2}$$
    L'angolo $\theta$ si determina risolvendo il sistema:
    $$ \begin{cases} \cos(\theta) = \frac{x}{\rho} = \frac{x}{\sqrt{x^2 + y^2}} \\ \sin(\theta) = \frac{y}{\rho} = \frac{y}{\sqrt{x^2 + y^2}} \end{cases} $$

## 3. Introduzione ai Numeri Complessi

### 3.1 Motivazione e Definizione Formale
Nel campo dei numeri reali $\mathbb{R}$, equazioni come la [[07 - Funzioni Potenza, Radici e Polinomi di Secondo Grado|funzione potenza]] $x^n = a$ non ammettono soluzioni se $n$ è pari e $a < 0$. Per superare questa limitazione, si introduce il **campo dei numeri complessi** $\mathbb{C}$, definito come l'insieme delle coppie ordinate di numeri reali $\mathbb{R}^2 = \{(x, y) \mid x, y \in \mathbb{R}\}$.

### 3.2 Operazioni con i Numeri Complessi
Su $\mathbb{C}$ si definiscono due operazioni binarie interne, la somma e il prodotto. Dati due numeri complessi $(x_1, y_1)$ e $(x_2, y_2)$:

-   **Somma:**
    $$(x_1, y_1) + (x_2, y_2) = (x_1 + x_2, y_1 + y_2)$$
-   **Prodotto:**
    $$(x_1, y_1) \cdot (x_2, y_2) = (x_1 x_2 - y_1 y_2, x_1 y_2 + x_2 y_1)$$

### 3.3 Proprietà Algebriche e Elementi Speciali
Le operazioni godono delle proprietà commutativa, associativa e distributiva.
- **Elemento neutro della somma:** La coppia $(0,0)$.
- **Opposto:** Per ogni coppia $(x, y)$, l'opposto è $(-x, -y)$.
- **Elemento neutro del prodotto:** La coppia $(1,0)$.
- **Inverso:** Per ogni coppia $(x, y) \neq (0,0)$, esiste l'inverso. Per trovarlo, poniamo $(x,y) \cdot (x',y') = (1,0)$, che porta al sistema:
  $$ \begin{cases} xx' - yy' = 1 \\ x'y + xy' = 0 \end{cases} $$
  Risolvendo, si ottiene l'inverso:
    $$(x,y)^{-1} = \left( \frac{x}{x^2+y^2}, \frac{-y}{x^2+y^2} \right)$$

## 4. Forma Algebrica e Unità Immaginaria

### 4.1 Identificazione dei Numeri Reali
Il sottoinsieme dei numeri complessi con seconda componente nulla, $\mathcal{R} = \{(x, 0) \mid x \in \mathbb{R}\}$, è stabile (chiuso) rispetto a somma e prodotto. Le operazioni in $\mathcal{R}$ sono identiche a quelle sui numeri reali. Si identifica quindi la coppia $(x,0)$ con il numero reale $x$. Geometricamente, questo insieme corrisponde all'**asse reale** del piano, i cui punti hanno argomento $\theta=0$ (per $x>0$) o $\theta=\pi$ (per $x<0$).

### 4.2 L'Asse Immaginario e l'Unità Immaginaria $i$
Il sottoinsieme $\mathcal{I} = \{(0, y) \mid y \in \mathbb{R}\}$ corrisponde all'**asse immaginario**. Questo insieme è stabile per la somma, ma non per il prodotto.
La coppia $(0,1)$ è chiamata **unità immaginaria** e si denota con $i$. Il suo quadrato è:
$$i^2 = i \cdot i = (0,1) \cdot (0,1) = (0 \cdot 0 - 1 \cdot 1, 0 \cdot 1 + 1 \cdot 0) = (-1, 0)$$
Identificando $(-1,0)$ con il numero reale $-1$, si ottiene la relazione fondamentale $i^2 = -1$. Questo risolve il problema iniziale. Geometricamente, gli immaginari puri hanno argomento $\theta=\pm\frac{\pi}{2}$.

Le potenze di $i$ seguono un ciclo di periodo 4:
- $i^0 = 1$
- $i^1 = i$
- $i^2 = -1$
- $i^3 = -i$
- $i^4 = 1$

### 4.3 La Forma Algebrica $z = x + iy$
Ogni numero complesso $z = (x, y)$ può essere decomposto come:
$$z = (x,y) = (x,0) + (0,y)$$
Poiché $(0,y) = (y,0) \cdot (0,1)$, usando le identificazioni si ha:
$$z = (x,0) + (y,0) \cdot (0,1) = x + y \cdot i = x + iy$$
Questa è la **forma algebrica** di $z$, dove:
- $x = \text{Re}(z)$ è la **parte reale**.
- $y = \text{Im}(z)$ è il **coefficiente dell'immaginario**.

## 5. Coniugato, Modulo e Piano di Gauss

### 5.1 Numero Complesso Coniugato
Dato $z = x+iy$, il suo **coniugato** $\bar{z}$ è $\bar{z} = x - iy$. Geometricamente, $\bar{z}$ è il simmetrico di $z$ rispetto all'asse reale. Il prodotto di un numero per il suo coniugato è un numero reale non negativo:
$$z \cdot \bar{z} = (x+iy)(x-iy) = x^2 - (iy)^2 = x^2 - i^2y^2 = x^2+y^2$$

### 5.2 Modulo di un Numero Complesso
Il **modulo** di $z=x+iy$, denotato con $|z|$, è la distanza del punto $(x,y)$ dall'origine. Coincide con il parametro $\rho$ delle coordinate polari:
$$|z| = \rho = \sqrt{x^2+y^2} = \sqrt{z \cdot \bar{z}}$$
Vale la relazione $|z| = |-z| = |\bar{z}|$.

### 5.3 Il Piano Complesso (o di Gauss)
I numeri complessi si rappresentano come punti sul **piano di Gauss**, dove l'asse delle ascisse è l'**asse reale** e l'asse delle ordinate è l'**asse immaginario**.

## 6. Forma Trigonometrica dei Numeri Complessi

### 6.1 Dalla Forma Algebrica alla Trigonometrica
Sostituendo $x = \rho \cos(\theta)$ e $y = \rho \sin(\theta)$ nella forma algebrica, si ottiene la **forma trigonometrica** di $z$:
$$z = \rho \cos(\theta) + i \rho \sin(\theta) = \rho(\cos(\theta) + i\sin(\theta))$$
Una notazione compatta è $z=[\rho, \theta]$.

### 6.2 Calcolo dell'Argomento tramite Arcotangente
Dividendo $y = \rho \sin(\theta)$ per $x = \rho \cos(\theta)$, si ottiene $\frac{y}{x} = \tan(\theta)$. L'angolo $\theta$ si può ricavare con la funzione arcotangente, prestando attenzione al quadrante:
$$ \theta = \begin{cases} \arctan\left(\frac{y}{x}\right) & \text{se } x > 0 \\ \arctan\left(\frac{y}{x}\right) + \pi & \text{se } x < 0 \\ \frac{\pi}{2} & \text{se } x=0, y>0 \\ -\frac{\pi}{2} & \text{se } x=0, y<0 \end{cases} $$

## 7. Operazioni in Forma Trigonometrica

### 7.1 Prodotto di Numeri Complessi
Dati $z_1 = \rho_1(\cos\theta_1 + i\sin\theta_1)$ e $z_2 = \rho_2(\cos\theta_2 + i\sin\theta_2)$, il loro prodotto è:
$$
\begin{align*}
z_1 z_2 &= \rho_1 \rho_2 [(\cos\theta_1\cos\theta_2 - \sin\theta_1\sin\theta_2) + i(\cos\theta_1\sin\theta_2 + \sin\theta_1\cos\theta_2)] \\
&= \rho_1 \rho_2 [\cos(\theta_1+\theta_2) + i\sin(\theta_1+\theta_2)]
\end{align*}
$$
In notazione compatta: $z_1 z_2 = [\rho_1 \rho_2, \theta_1 + \theta_2]$.
Il modulo del prodotto è il prodotto dei moduli, e l'argomento è la somma degli argomenti.

### 7.2 Potenza (Formula di De Moivre)
Per ogni intero $n$, la potenza $n$-esima di $z = [\rho, \theta]$ è data dalla **formula di De Moivre**:
$$ z^n = [\rho^n, n\theta] \implies z^n = \rho^n(\cos(n\theta) + i\sin(n\theta)) $$

### 7.3 Quoziente di Numeri Complessi
Il quoziente può essere visto come $z_1 \cdot z_2^{-1}$. Sapendo che $z_2^{-1} = [\rho_2^{-1}, -\theta_2]$, si ottiene:
$$\frac{z_1}{z_2} = [\frac{\rho_1}{\rho_2}, \theta_1 - \theta_2]$$
Il modulo del quoziente è il quoziente dei moduli, e l'argomento è la differenza degli argomenti.

## 8. Radici n-esime di un Numero Complesso

### 8.1 Derivazione della Formula
Si cercano i numeri $\omega = [r, \phi]$ tali che $\omega^n = z$, dove $z = [\rho, \theta]$ è noto. Per De Moivre, $\omega^n = [r^n, n\phi]$. Uguagliando a $z$:
1.  **Moduli**: $r^n = \rho \implies r = \sqrt[n]{\rho}$
2.  **Argomenti**: $n\phi = \theta + 2k\pi \implies \phi = \frac{\theta + 2k\pi}{n}$ con $k \in \mathbb{Z}$.

Le $n$ radici $n$-esime di $z$ sono date dalla formula:
$$\omega_k = \left[ \sqrt[n]{\rho}, \frac{\theta + 2k\pi}{n} \right]$$

### 8.2 Determinazione delle Soluzioni Distinte
Si ottengono solo $n$ radici distinte. Due radici $\omega_{k_1}$ e $\omega_{k_2}$ coincidono se e solo se $k_1 - k_2$ è un multiplo di $n$. Per ottenere tutte le radici distinte, è sufficiente far variare $k$ in un insieme di $n$ interi consecutivi, tipicamente $k = 0, 1, 2, \dots, n-1$.

### 8.3 Interpretazione Geometrica
Le $n$ radici $n$-esime di $z$ hanno tutte lo stesso modulo $\sqrt[n]{\rho}$ e giacciono su una circonferenza di tale raggio. I loro argomenti sono equispaziati di $2\pi/n$. Geometricamente, esse rappresentano i vertici di un **poligono regolare di $n$ lati** inscritto in tale circonferenza.

## 9. Esempi Applicativi

### Esempio 1: Calcolo di una potenza
Calcolare $(1+i)^8$.
$z = 1+i \implies \rho = \sqrt{2}, \theta = \pi/4$.
$$(1+i)^8 = [(\sqrt{2})^8, 8 \cdot \frac{\pi}{4}] = [2^4, 2\pi] = 16(\cos(2\pi) + i\sin(2\pi)) = 16$$

### Esempio 2: Radici cubiche di 1
Trovare le radici cubiche di $z=1 = [1, 0]$. ($n=3$)
$$\omega_k = \left[ 1, \frac{2k\pi}{3} \right] \quad \text{per } k = 0, 1, 2$$
- **k=0:** $\omega_0 = [1, 0] = 1$
- **k=1:** $\omega_1 = [1, 2\pi/3] = -\frac{1}{2} + i\frac{\sqrt{3}}{2}$
- **k=2:** $\omega_2 = [1, 4\pi/3] = -\frac{1}{2} - i\frac{\sqrt{3}}{2}$

### Esempio 3: Soluzioni di $w^3 + 2 = 0$
Risolvere $w^3 = -2$. Si cercano le radici cubiche di $z=-2 = [2, \pi]$.
$$\omega_k = \left[ \sqrt[3]{2}, \frac{\pi + 2k\pi}{3} \right] \quad \text{per } k = 0, 1, 2$$
- **k=0:** $\omega_0 = [\sqrt[3]{2}, \pi/3] = \sqrt[3]{2}(\frac{1}{2} + i\frac{\sqrt{3}}{2})$
- **k=1:** $\omega_1 = [\sqrt[3]{2}, \pi] = -\sqrt[3]{2}$
- **k=2:** $\omega_2 = [\sqrt[3]{2}, 5\pi/3] = \sqrt[3]{2}(\frac{1}{2} - i\frac{\sqrt{3}}{2})$
Si noti che $\omega_2 = \overline{\omega_0}$.

### Esempio 4: Operazioni complesse e calcolo di radici
Calcolare le radici cubiche di $z = \frac{(1-i)^8 (\sqrt{3}+i\sqrt{3})^4}{5(\sqrt{3}+i)^3}$.
1.  **Convertire ogni fattore in forma trigonometrica:**
    - $z_1 = (1-i) = [\sqrt{2}, -\pi/4]$
    - $z_2 = (\sqrt{3}+i\sqrt{3}) = [\sqrt{6}, \pi/4]$
    - $z_3 = 5 = [5, 0]$
    - $z_4 = (\sqrt{3}+i) = [2, \pi/6]$
2.  **Calcolare le potenze con De Moivre:**
    - $z_1^8 = [(\sqrt{2})^8, 8(-\pi/4)] = [16, -2\pi] = [16, 0]$
    - $z_2^4 = [(\sqrt{6})^4, 4(\pi/4)] = [36, \pi]$
    - $z_4^3 = [2^3, 3(\pi/6)] = [8, \pi/2]$
3.  **Calcolare il numeratore (prodotto):**
    - $N = z_1^8 \cdot z_2^4 = [16 \cdot 36, 0+\pi] = [576, \pi]$
4.  **Calcolare il denominatore (prodotto):**
    - $D = z_3 \cdot z_4^3 = [5 \cdot 8, 0+\pi/2] = [40, \pi/2]$
5.  **Calcolare $z$ (quoziente):**
    - $z = \frac{N}{D} = [\frac{576}{40}, \pi - \frac{\pi}{2}] = [\frac{72}{5}, \frac{\pi}{2}]$
6.  **Calcolare le radici cubiche di $z$:**
    $$\omega_k = \left[ \sqrt[3]{\frac{72}{5}}, \frac{\frac{\pi}{2} + 2k\pi}{3} \right] \quad \text{per } k = 0, 1, 2$$