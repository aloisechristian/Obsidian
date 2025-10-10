# Misura degli Angoli in Radianti e Funzioni Circolari

## Definizione di Radiante

In analisi matematica, la misura di un angolo è espressa in **radianti**. Tale misura è definita attraverso la circonferenza goniometrica, ovvero una circonferenza di raggio unitario ($r=1$) centrata nell'origine degli assi cartesiani. Dato un angolo con vertice nell'origine, la sua misura in radianti corrisponde alla lunghezza dell'arco di circonferenza goniometrica sotteso dall'angolo stesso. Il verso di rotazione positivo è, per convenzione, quello antiorario.

Poiché la lunghezza di una circonferenza completa è data dalla formula $C = 2\pi r$, per una circonferenza di raggio 1 la lunghezza è $2\pi$. Di conseguenza:
- Un angolo giro misura $2\pi$ radianti.
- Un angolo piatto misura $\pi$ radianti.
- Un angolo retto misura $\frac{\pi}{2}$ radianti.

### Periodicità degli Angoli

Geometricamente, un angolo di misura $x$ e un angolo di misura $x + 2\pi$ individuano lo stesso punto sulla circonferenza goniometrica. Pertanto, tutti gli angoli della forma $x + 2k\pi$, con $k \in \mathbb{Z}$, sono considerati equivalenti dal punto di vista trigonometrico.

## Le Funzioni Seno e Coseno

### Definizioni e Proprietà Fondamentali

Consideriamo un punto $P$ che si muove sulla circonferenza goniometrica. Sia $x$ la misura in radianti dell'angolo formato dal semiasse positivo delle ascisse e la semiretta OP. Le funzioni seno e coseno sono definite come le coordinate del punto $P$:

-   **Funzione Seno:** $\sin(x)$ è l'**ordinata** del punto $P$. È una funzione $f: \mathbb{R} \to [-1, 1]$.
-   **Funzione Coseno:** $\cos(x)$ è l'**ascissa** del punto $P$. È una funzione $f: \mathbb{R} \to [-1, 1]$.

Da questa definizione seguono alcune proprietà immediate:

1.  **Limitatezza:** Poiché il punto $P$ giace su una circonferenza di raggio 1, le sue coordinate sono necessariamente comprese tra -1 e 1. Quindi:
    $$-1 \le \sin(x) \le 1 \quad \text{e} \quad -1 \le \cos(x) \le 1, \quad \forall x \in \mathbb{R}$$
2.  **Relazione Fondamentale:** Per il Teorema di Pitagora applicato al triangolo rettangolo avente come ipotenusa il raggio unitario e come cateti i valori $|\cos(x)|$ e $|\sin(x)|$, si ottiene la relazione fondamentale della trigonometria:
    $$\sin^2(x) + \cos^2(x) = 1, \quad \forall x \in \mathbb{R}$$
3.  **Periodicità:** Poiché gli angoli $x$ e $x+2k\pi$ individuano lo stesso punto, le funzioni seno e coseno sono **periodiche di periodo $2\pi$**:
    $$\sin(x) = \sin(x+2k\pi) \quad \text{e} \quad \cos(x) = \cos(x+2k\pi), \quad \forall k \in \mathbb{Z}$$
4.  **Simmetrie (Parità/Disparità):**
    - La funzione coseno è una **funzione pari**, in quanto $\cos(-x) = \cos(x)$. Il suo grafico è simmetrico rispetto all'asse delle ordinate.
    - La funzione seno è una **funzione dispari**, in quanto $\sin(-x) = -\sin(x)$. Il suo grafico è simmetrico rispetto all'origine.

## Inversione delle Funzioni Trigonometriche

### Funzione Arcoseno

La funzione $\sin(x)$, essendo periodica, non è [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|iniettiva]] su tutto $\mathbb{R}$ e quindi non è globalmente invertibile. Per definire la sua funzione inversa, si restringe il dominio all'intervallo $[-\pi/2, \pi/2]$, dove la funzione è **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente crescente]]** e assume tutti i valori tra -1 e 1.

La funzione inversa, detta **arcoseno**, è definita come:

$$\arcsin: [-1, 1] \to [-\frac{\pi}{2}, \frac{\pi}{2}]$$

L'arcoseno di $y$ è quell'unico angolo $x$ nell'intervallo $[-\pi/2, \pi/2]$ tale che $\sin(x) = y$.

#### Risoluzione di Equazioni e Disequazioni con il Seno

-   **Equazione $\sin(x) = a$ (con $|a| \le 1$):**
    1.  Si trova la soluzione principale nell'intervallo di invertibilità: $x_0 = \arcsin(a)$.
    2.  Si trova la seconda famiglia di soluzioni tramite la relazione $x_1 = \pi - x_0$.
    3.  Le soluzioni generali si ottengono aggiungendo la periodicità:
        $$x = \arcsin(a) + 2k\pi \quad \cup \quad x = \pi - \arcsin(a) + 2k\pi, \quad k \in \mathbb{Z}$$

-   **Disequazione $\sin(x) > a$:** La soluzione è data dai valori compresi tra le due soluzioni trovate nell'intervallo di riferimento:
    $$\arcsin(a) + 2k\pi < x < \pi - \arcsin(a) + 2k\pi, \quad k \in \mathbb{Z}$$

-   **Disequazione $\sin(x) < a$:** La soluzione è data dai valori esterni all'intervallo precedente. Può essere espressa in modo compatto come:
    $$-\pi - \arcsin(a) + 2k\pi < x < \arcsin(a) + 2k\pi, \quad k \in \mathbb{Z}$$

### Funzione Arcocoseno

Analogamente, la funzione $\cos(x)$ viene ristretta all'intervallo $[0, \pi]$, dove è **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente decrescente]]**, per poter essere invertita.

La funzione inversa, detta **arcocoseno**, è definita come:

$$\arccos: [-1, 1] \to [0, \pi]$$

L'arcocoseno di $y$ è quell'unico angolo $x$ nell'intervallo $[0, \pi]$ tale che $\cos(x) = y$.

#### Risoluzione di Equazioni e Disequazioni con il Coseno

-   **Equazione $\cos(x) = a$ (con $|a| \le 1$):**
    1.  Si trova la soluzione principale: $x_0 = \arccos(a) \in [0, \pi]$.
    2.  Sfruttando la parità della funzione coseno ($\cos(-x) = \cos(x)$), la seconda famiglia di soluzioni è $x_1 = -x_0$.
    3.  Le soluzioni generali sono: $x = \pm \arccos(a) + 2k\pi$, con $k \in \mathbb{Z}$.

-   **Caso con valore negativo (es. $\cos(x) = -1/2$):** Si determina prima l'angolo $\bar{x}$ tale che $\cos(\bar{x}) = 1/2$, che è $\bar{x} = \pi/3$. La soluzione principale per $\cos(x) = -1/2$ è data da $x_0 = \pi - \bar{x} = \pi - \pi/3 = 2\pi/3$, grazie all'identità $\cos(\pi - \theta) = -\cos(\theta)$. Le soluzioni generali sono quindi $x = \pm 2\pi/3 + 2k\pi$.

-   **Disequazione $\cos(x) > a$:** La soluzione è data dai valori interni all'intervallo delle radici nell'intervallo di ampiezza $2\pi$:
    $$-\arccos(a) + 2k\pi < x < \arccos(a) + 2k\pi, \quad k \in \mathbb{Z}$$

-   **Disequazione $\cos(x) < a$:** La soluzione è data dai valori esterni:
    $$\arccos(a) + 2k\pi < x < 2\pi - \arccos(a) + 2k\pi, \quad k \in \mathbb{Z}$$

### Funzione Arcotangente

La funzione $\tan(x) = \frac{\sin(x)}{\cos(x)}$ ha dominio $\mathbb{R} \setminus \{\frac{\pi}{2} + k\pi\}$ ed è periodica di periodo $\pi$. Per invertirla, si restringe il dominio all'intervallo aperto $(-\pi/2, \pi/2)$, dove è **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente crescente]]** e il suo codominio è tutto $\mathbb{R}$.

La funzione inversa, detta **arcotangente**, è definita come:

$$\arctan: \mathbb{R} \to (-\frac{\pi}{2}, \frac{\pi}{2})$$

#### Risoluzione di Equazioni e Disequazioni con la Tangente

-   **Equazione $\tan(x) = a$ (con $a \in \mathbb{R}$):**
    1.  Si trova l'unica soluzione nell'intervallo di ampiezza $\pi$: $x_0 = \arctan(a)$.
    2.  Poiché il periodo della funzione coincide con l'ampiezza dell'intervallo di invertibilità, le soluzioni generali si ottengono semplicemente aggiungendo la periodicità:
        $$x = \arctan(a) + k\pi, \quad k \in \mathbb{Z}$$

-   **Disequazione $\tan(x) > a$:** Poiché la funzione è crescente, la soluzione in un periodo è $\arctan(a) < x < \pi/2$. La soluzione generale è:
    $$\arctan(a) + k\pi < x < \frac{\pi}{2} + k\pi, \quad k \in \mathbb{Z}$$

-   **Disequazione $\tan(x) < a$:** Analogamente, la soluzione in un periodo è $-\pi/2 < x < \arctan(a)$. La soluzione generale è:
    $$-\frac{\pi}{2} + k\pi < x < \arctan(a) + k\pi, \quad k \in \mathbb{Z}$$

## Disequazioni con Funzioni Inverse

Per risolvere disequazioni che coinvolgono le funzioni trigonometriche inverse, è fondamentale applicare la funzione diretta corrispondente, prestando massima attenzione alla sua **monotonia** e al **dominio** della funzione inversa.

-   **Disequazioni con $\arcsin(x)$ e $\arctan(x)$ (crescenti):** Quando si applica $\sin()$ o $\tan()$, il verso della disuguaglianza **si mantiene**.
-   **Disequazioni con $\arccos(x)$ (decrescente):** Quando si applica $\cos()$ (nell'intervallo $[0, \pi]$), il verso della disuguaglianza **deve essere invertito**.

In tutti i casi, la soluzione finale deve essere intersecata con il dominio di definizione della funzione inversa (es. $[-1, 1]$ per $\arcsin$ e $\arccos$).

**Esempio:** Risolvere $\arccos(x) < a$.
1.  **Condizioni di esistenza:** $-1 \le x \le 1$. Per avere soluzioni non banali, $a$ deve essere nel codominio $[0, \pi]$, quindi $0 \le a \le \pi$.
2.  **Applicazione dell'inversa:** Si applica la funzione $\cos()$, che è decrescente nell'intervallo $[0, \pi]$. Il verso della disequazione si inverte:
    $$\cos(\arccos(x)) > \cos(a) \implies x > \cos(a)$$
3.  **Intersezione con il dominio:** La soluzione finale è l'intersezione tra $x > \cos(a)$ e $x \le 1$, che risulta in $\cos(a) < x \le 1$.

## Esercizio Svolto: Disequazione Fratta

Risolvere la disequazione:

$$\frac{2\sin(x) - 1}{2\cos(x) - 1} > 0$$

Si studia il segno del numeratore e del denominatore separatamente nell'intervallo di riferimento $[0, 2\pi]$, per poi combinarli in un grafico dei segni.

1.  **Studio del Numeratore: $N(x) > 0$**
    $$2\sin(x) - 1 > 0 \implies \sin(x) > \frac{1}{2}$$
    Le soluzioni dell'equazione associata $\sin(x)=1/2$ in $[0, 2\pi]$ sono $x=\pi/6$ e $x=\pi - \pi/6 = 5\pi/6$.
    La disequazione è soddisfatta per valori interni: $\frac{\pi}{6} < x < \frac{5\pi}{6}$.

2.  **Studio del Denominatore: $D(x) > 0$**
    $$2\cos(x) - 1 > 0 \implies \cos(x) > \frac{1}{2}$$
    Le soluzioni di $\cos(x)=1/2$ sono $x=\pm\pi/3$. Nell'intervallo $[0, 2\pi]$, le soluzioni sono $x=\pi/3$ e $x=2\pi - \pi/3 = 5\pi/3$.
    La disequazione è soddisfatta per $0 \le x < \frac{\pi}{3} \cup \frac{5\pi}{3} < x \le 2\pi$.

3.  **Grafico dei segni in $[0, 2\pi]$**
    Si riportano gli intervalli di positività su un asse per determinare dove il rapporto è positivo (segni concordi).

| Intervallo | $(0, \frac{\pi}{6})$ | $(\frac{\pi}{6}, \frac{\pi}{3})$ | $(\frac{\pi}{3}, \frac{5\pi}{6})$ | $(\frac{5\pi}{6}, \frac{5\pi}{3})$ | $(\frac{5\pi}{3}, 2\pi)$ |
|:---:|:---:|:---:|:---:|:---:|:---:|
| N(x) | - | + | + | - | - |
| D(x) | + | + | - | - | + |
| Frazione | - | + | - | + | - |

La frazione è positiva dove numeratore e denominatore sono concordi:
    -   **Entrambi positivi:** $(\frac{\pi}{6}, \frac{\pi}{3})$
    -   **Entrambi negativi:** $(\frac{5\pi}{6}, \frac{5\pi}{3})$

4.  **Soluzione Generale**
    La soluzione è l'unione dei due intervalli, a cui si aggiunge la periodicità $2k\pi$:
    $$x \in \left(\frac{\pi}{6} + 2k\pi, \frac{\pi}{3} + 2k\pi\right) \cup \left(\frac{5\pi}{6} + 2k\pi, \frac{5\pi}{3} + 2k\pi\right), \quad k \in \mathbb{Z}$$