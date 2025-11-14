## 1. Il Concetto di Derivata

### 1.1 Definizione di Funzione Derivabile

Una funzione $f(x)$ si definisce **derivabile** in un punto $x$ del suo dominio (che deve essere un [[17 - Intorni, Punti di Accumulazione e Limiti di Funzione|punto di accumulazione]] per il dominio) se esiste ed è finito il limite del suo rapporto incrementale. Tale limite, detto **derivata prima** della funzione in quel punto, è dato da:

$$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$

Questo limite è anche introdotto in [[20 - Infinitesimi, Principio di Sostituzione e Derivata]] e [[21 - Derivate e Regole di Derivazione]].

La derivata prima di una funzione in un punto $x$ si indica con varie notazioni:

- $f'(x)$ (Notazione di Lagrange)
    
- $D[f(x)]$ (Notazione di Cauchy)
    
- $\frac{dy}{dx}$ (Notazione di Leibniz)
    
- $\dot{y}$ (Notazione di Newton, usata in fisica per la derivata rispetto al tempo)
    

### 1.2 Derivate di Ordine Superiore

È possibile derivare una funzione più volte. La derivata della derivata prima, se esiste, è definita come **derivata seconda**, indicata con $f''(x)$ o $D^2[f(x)]$. Analogamente, la derivata della derivata seconda è la **derivata terza**, e così via. In generale, la **derivata n-esima** è il risultato della derivazione della funzione per $n$ volte consecutive, a condizione che la funzione ottenuta a ogni passo sia a sua volta derivabile.

## 2. Relazione tra Derivabilità e Continuità

Ci si può chiedere se tutte le funzioni siano derivabili. Un classico controesempio è la funzione [[06 - Studio delle Funzioni Valore Assoluto e Potenza|valore assoluto]], $f(x) = |x|$, che è [[18 - Limiti, Continuità e Teoremi sulle Funzioni Continue|continua]] nel punto $x=0$ ma non è derivabile in tale punto.

In $x=0$, infatti, le derivate destra e sinistra non coincidono:

- **Derivata destra**: $f'_+(0) = \lim_{h \to 0^+} \frac{|0+h| - |0|}{h} = \lim_{h \to 0^+} \frac{h}{h} = 1$
    
- **Derivata sinistra**: $f'_-(0) = \lim_{h \to 0^-} \frac{|0+h| - |0|}{h} = \lim_{h \to 0^-} \frac{-h}{h} = -1$ Poiché $f'_+(0) \neq f'_-(0)$, la funzione non è derivabile. Il punto $(0,0)$ è un **punto angoloso**, come menzionato in [[21 - Derivate e Regole di Derivazione]].
    

Questo dimostra che la continuità non implica la derivabilità. Tuttavia, vale la relazione inversa, come enunciato dal seguente teorema (presente anche in [[21 - Derivate e Regole di Derivazione]]).

### Teorema: La Derivabilità Implica la Continuità

Se una funzione $f(x)$ è derivabile in un punto $x$, allora è anche continua in quel punto.

**Dimostrazione:** Per dimostrare la [[18 - Limiti, Continuità e Teoremi sulle Funzioni Continue#3.1. Definizione di Continuità|continuità]] in $x$, dobbiamo verificare che $\lim_{h \to 0} f(x+h) = f(x)$. Consideriamo la differenza $f(x+h) - f(x)$. Possiamo riscriverla in modo da far comparire il rapporto incrementale (per $h \neq 0$):

$$f(x+h) - f(x) = \frac{f(x+h) - f(x)}{h} \cdot h$$

Passando al limite per $h \to 0$ per entrambi i membri, e usando l'[[14 - Definizione e Teoremi dei Limiti di Successioni#Algebra dei Limiti|algebra dei limiti]] (il limite di un prodotto è il prodotto dei limiti, se finiti):

$$\lim_{h \to 0} [f(x+h) - f(x)] = \lim_{h \to 0} \left( \frac{f(x+h) - f(x)}{h} \cdot h \right)$$$$\lim_{h \to 0} [f(x+h) - f(x)] = \left( \lim_{h \to 0} \frac{f(x+h) - f(x)}{h} \right) \cdot \left( \lim_{h \to 0} h \right)$$

Poiché per ipotesi la funzione è derivabile in $x$, il primo limite è $f'(x)$ (un valore finito). Il secondo limite è $0$.

$$\lim_{h \to 0} [f(x+h) - f(x)] = f'(x) \cdot 0 = 0$$

Da cui si deduce:

$$\lim_{h \to 0} f(x+h) = f(x)$$

Questo corrisponde alla definizione di continuità della funzione nel punto $x$. c.v.d.

## 3. Regole di Derivazione e Derivate Notevoli

(Per un riepilogo, vedi anche [[21 - Derivate e Regole di Derivazione]])

### 3.1 Algebra delle Derivate

Date due funzioni derivabili $f(x)$ e $g(x)$, valgono le seguenti regole:

- **Derivata della Somma/Differenza:** $D[f(x) \pm g(x)] = f'(x) \pm g'(x)$
    
- **Derivata del Prodotto (Regola di Leibniz):** $D[f(x) \cdot g(x)] = f'(x)g(x) + f(x)g'(x)$
    
- **Derivata del Quoziente:** $D\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}$, con $g(x) \neq 0$.
    

### 3.2 Derivata della Funzione Composta (Regola della Catena)

Se $g$ è derivabile in $x$ e $f$ è derivabile in $g(x)$, allora la funzione composta $F(x) = f(g(x))$ è derivabile in $x$ e la sua derivata è:

$$F'(x) = f'(g(x)) \cdot g'(x)$$

### 3.3 Derivata della Funzione Inversa

Sia $f$ una funzione continua e strettamente monotona (e quindi [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|invertibile]]) in un intervallo. Se $f$ è derivabile in $x$ con $f'(x) \neq 0$, allora la sua funzione inversa $f^{-1}$ è derivabile nel punto $y = f(x)$ e si ha:

$$(f^{-1})'(y) = \frac{1}{f'(x)} = \frac{1}{f'(f^{-1}(y))}$$

### 3.4 Derivate di Funzioni Elementari

- $D[c] = 0$ (costante)
    
- $D[x^b] = b x^{b-1}$ (Vedi [[07 - Funzioni Potenza, Radici e Polinomi di Secondo Grado|Funzione Potenza]], per ogni $b \in \mathbb{R}$)
    
- $D[a^x] = a^x \ln(a)$. Caso particolare: $D[e^x] = e^x$ (Vedi [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali|Funzione Esponenziale]])
    
- $D[\log_a(x)] = \frac{1}{x} \log_a(e)$. Caso particolare: $D[\ln(x)] = \frac{1}{x}$ (Vedi [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali|Funzione Logaritmica]])
    
- $D[\sin(x)] = \cos(x)$ (Vedi [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali|Funzioni Trigonometriche]])
    
- $D[\cos(x)] = -\sin(x)$
    
- $D[\tan(x)] = \frac{1}{\cos^2(x)} = 1 + \tan^2(x)$ (Vedi [[10 - Funzioni Trigonometriche Inverse e Loro Applicazioni]])
    

## 4. Significato Geometrico della Derivata

La derivata di una funzione in un punto ha un'importante interpretazione geometrica (vedi anche [[21 - Derivate e Regole di Derivazione]] e [[20 - Infinitesimi, Principio di Sostituzione e Derivata]]): essa rappresenta il **coefficiente angolare della retta tangente** al grafico della funzione in quel punto.

### 4.1 Dalla Retta Secante alla Tangente

Consideriamo due punti sul grafico della funzione $f(x)$: $P_0 = (x_0, f(x_0))$ e $P = (x_0+h, f(x_0+h))$. La retta passante per questi due punti è detta **retta secante**. Il suo coefficiente angolare $m_{sec}$ è dato da:

$$m_{sec} = \frac{\Delta y}{\Delta x} = \frac{f(x_0+h) - f(x_0)}{(x_0+h) - x_0} = \frac{f(x_0+h) - f(x_0)}{h}$$

Questo è esattamente il rapporto incrementale della funzione $f$ in $x_0$. La **retta tangente** al grafico nel punto $P_0$ è definita come la posizione limite della retta secante quando il punto $P$ si avvicina a $P_0$, ovvero quando $h \to 0$. Di conseguenza, il coefficiente angolare della retta tangente, $m_{tan}$, è il limite del coefficiente angolare della retta secante:

$$m_{tan} = \lim_{h \to 0} m_{sec} = \lim_{h \to 0} \frac{f(x_0+h) - f(x_0)}{h} = f'(x_0)$$

### 4.2 Equazione della Retta Tangente

L'equazione della retta passante per il punto $P_0(x_0, f(x_0))$ con coefficiente angolare $m = f'(x_0)$ è:

$$y - f(x_0) = f'(x_0)(x - x_0)$$

Questa è l'equazione della retta tangente al grafico di $f(x)$ nel punto di ascissa $x_0$.

## 5. Punti di Massimo e Minimo

### 5.1 Estremi Assoluti e Relativi

(Vedi [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Estremo Superiore e Inferiore di una Funzione|Estremi di una Funzione]])

- Un punto $x_1$ è un **punto di massimo assoluto (o globale)** se $f(x_1) \ge f(x)$ per ogni $x$ nel dominio della funzione.
    
- Un punto $x_2$ è un **punto di minimo assoluto (o globale)** se $f(x_2) \le f(x)$ per ogni $x$ nel dominio della funzione.
    

Una nozione più locale è quella di estremo relativo:

- Un punto $x_0$ è un **punto di massimo relativo (o locale)** se esiste un [[17 - Intorni, Punti di Accumulazione e Limiti di Funzione#1.1. Intorni di un Punto|intorno]] di $x_0$ (cioè un intervallo $(x_0-\delta, x_0+\delta)$) tale che $f(x_0) \ge f(x)$ per ogni $x$ in tale intorno.
    
- Un punto $x_0$ è un **punto di minimo relativo (o locale)** se esiste un intorno di $x_0$ tale che $f(x_0) \le f(x)$ per ogni $x$ in tale intorno.
    

Un punto di massimo o minimo assoluto è sempre anche un punto di massimo o minimo relativo. Il viceversa non è generalmente vero.

## 6. Teoremi Fondamentali del Calcolo Differenziale

### 6.1 Teorema di Fermat

**Enunciato:** Sia $f(x)$ una funzione definita in un intervallo $[a,b]$ e sia $x_0$ un punto di estremo relativo interno all'intervallo (cioè $x_0 \in (a,b)$). Se $f$ è derivabile in $x_0$, allora la sua derivata in quel punto è nulla:

$$f'(x_0) = 0$$

**Dimostrazione:** Supponiamo che $x_0$ sia un punto di massimo relativo. Per definizione, esiste un $\delta > 0$ tale che $f(x_0) \ge f(x_0+h)$ per ogni $|h| < \delta$. Questo implica che $f(x_0+h) - f(x_0) \le 0$. Analizziamo il segno del rapporto incrementale:

1. **Caso** $h > 0$**:** Il numeratore è $\le 0$ e il denominatore è $> 0$. Quindi, $\frac{f(x_0+h) - f(x_0)}{h} \le 0$.
    
2. **Caso** $h < 0$**:** Il numeratore è $\le 0$ e il denominatore è $< 0$. Quindi, $\frac{f(x_0+h) - f(x_0)}{h} \ge 0$.
    

Poiché per ipotesi $f$ è derivabile in $x_0$, il limite del rapporto incrementale per $h \to 0$ deve esistere e coincidere da destra e da sinistra. Per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema della Permanenza del Segno|teorema della permanenza del segno]] (applicato ai limiti di funzione, vedi [[19 - Limiti di Funzioni, Continuità e Teoremi Fondamentali]]):

- La derivata destra è: $f'_+(x_0) = \lim_{h \to 0^+} \frac{f(x_0+h) - f(x_0)}{h} \le 0$.
    
- La derivata sinistra è: $f'_-(x_0) = \lim_{h \to 0^-} \frac{f(x_0+h) - f(x_0)}{h} \ge 0$.
    

Dato che $f'(x_0) = f'_+(x_0) = f'_-(x_0)$, l'unica possibilità per cui una quantità sia contemporaneamente $\le 0$ e $\ge 0$ è che sia uguale a zero. Pertanto, $f'(x_0) = 0$. La dimostrazione è analoga per un punto di minimo relativo. c.v.d.

### 6.2 Teorema di Rolle

**Enunciato:** Sia $f(x)$ una funzione che soddisfa le seguenti ipotesi:

1. È [[18 - Limiti, Continuità e Teoremi sulle Funzioni Continue|continua]] nell'intervallo chiuso e limitato $[a,b]$.
    
2. È derivabile nell'intervallo aperto $(a,b)$.
    
3. Assume valori uguali agli estremi dell'intervallo: $f(a) = f(b)$.
    

Allora esiste almeno un punto $x_0 \in (a,b)$ tale che $f'(x_0) = 0$.

**Dimostrazione:** Per il [[19 - Limiti di Funzioni, Continuità e Teoremi Fondamentali#5.4. Teorema di Weierstrass|Teorema di Weierstrass]], essendo $f$ continua in $[a,b]$, essa ammette un punto di massimo assoluto $x_{max}$ e un punto di minimo assoluto $x_{min}$ in $[a,b]$. Si presentano due casi:

1. **Almeno uno dei due punti di estremo è interno all'intervallo** $(a,b)$**.** Chiamiamo tale punto $x_0$. Poiché $x_0$ è un punto di estremo interno e per ipotesi la funzione è derivabile in $(a,b)$, possiamo applicare il [[#6.1 Teorema di Fermat|Teorema di Fermat]]. Ne consegue che $f'(x_0) = 0$.
    
2. **Entrambi i punti di estremo si trovano agli estremi dell'intervallo, cioè sono** $a$ **e** $b$**.** Poiché per ipotesi $f(a) = f(b)$, il valore massimo della funzione $f(x_{max})$ coincide con il valore minimo $f(x_{min})$. Questo implica che la funzione è costante su tutto l'intervallo $[a,b]$. La derivata di una funzione costante è zero in ogni punto, quindi $f'(x) = 0$ per ogni $x \in (a,b)$. Anche in questo caso, la tesi è verificata. c.v.d.
    

### 6.3 Teorema di Lagrange (o del Valor Medio)

**Enunciato:** Sia $f(x)$ una funzione che soddisfa le seguenti ipotesi:

1. È [[18 - Limiti, Continuità e Teoremi sulle Funzioni Continue|continua]] nell'intervallo chiuso e limitato $[a,b]$.
    
2. È derivabile nell'intervallo aperto $(a,b)$.
    

Allora esiste almeno un punto $x_0 \in (a,b)$ tale che:

$$f'(x_0) = \frac{f(b) - f(a)}{b - a}$$

Geometricamente, questo significa che esiste almeno un punto in cui la retta tangente al grafico è parallela alla retta secante che congiunge gli estremi $(a, f(a))$ e $(b, f(b))$.

**Dimostrazione:** Si costruisce una **funzione ausiliaria** $g(x)$ come la differenza tra la funzione $f(x)$ e la retta passante per i punti $(a, f(a))$ e $(b, f(b))$. L'equazione di tale retta è $y(x) = f(a) + \frac{f(b) - f(a)}{b - a}(x - a)$. La funzione ausiliaria è:

$$g(x) = f(x) - \left[ f(a) + \frac{f(b) - f(a)}{b - a}(x - a) \right]$$

Questa funzione $g(x)$ soddisfa le ipotesi del [[#6.2 Teorema di Rolle|Teorema di Rolle]]:

1. È continua in $[a,b]$ perché è somma di funzioni continue.
    
2. È derivabile in $(a,b)$ perché è somma di funzioni derivabili.
    
3. Agli estremi assume lo stesso valore: $g(a) = f(a) - [ f(a) + 0 ] = 0$ e $g(b) = f(b) - [ f(a) + \frac{f(b) - f(a)}{b - a}(b - a) ] = f(b) - [f(a) + f(b) - f(a)] = 0$. Quindi $g(a) = g(b) = 0$.
    

Applicando il Teorema di Rolle a $g(x)$, esiste un punto $x_0 \in (a,b)$ tale che $g'(x_0) = 0$. Calcoliamo la derivata di $g(x)$:

$$g'(x) = f'(x) - \frac{f(b) - f(a)}{b - a}$$

Valutandola in $x_0$ e ponendola uguale a zero:

$$0 = g'(x_0) = f'(x_0) - \frac{f(b) - f(a)}{b - a}$$

Da cui si ottiene la tesi: $f'(x_0) = \frac{f(b) - f(a)}{b - a}$. c.v.d.

> [!NOTE] Nota sulla Tecnica Dimostrativa: La dimostrazione del Teorema di Lagrange è un classico esempio di applicazione del Teorema di Rolle a una funzione ausiliaria costruita ad hoc. Questa tecnica è molto comune in analisi. 

## 7. Conseguenze del Teorema di Lagrange

### 7.1 Funzioni con Derivata Nulla

Se $f'(x)=0$ per ogni $x$ in un intervallo $(a,b)$, allora la funzione $f(x)$ è costante in tale intervallo.

**Dimostrazione:** Presi due punti qualsiasi $x_1, x_2$ nell'intervallo, con $x_1 < x_2$. La funzione $f$ è continua e derivabile nell'intervallo $[x_1, x_2]$. Per il Teorema di Lagrange, esiste un $x_0 \in (x_1, x_2)$ tale che $\frac{f(x_2)-f(x_1)}{x_2-x_1} = f'(x_0)$. Poiché per ipotesi $f'(x_0)=0$, si ha $\frac{f(x_2)-f(x_1)}{x_2-x_1} = 0$. Essendo $x_2-x_1 \neq 0$, questo implica $f(x_2)-f(x_1)=0$, cioè $f(x_2)=f(x_1)$. Essendo $x_1$ e $x_2$ arbitrari, la funzione è costante.

**Corollario:** Se due funzioni $f(x)$ e $g(x)$ hanno la stessa derivata in un intervallo ($f'(x) = g'(x)$), allora la loro differenza è una costante: $f(x) = g(x) + c$. _Dimostrazione:_ Si applica il teorema precedente alla funzione $h(x) = f(x) - g(x)$, la cui derivata $h'(x) = f'(x) - g'(x) = 0$.

### 7.2 Criterio di Monotonia

Sia $f$ una funzione continua in $[a,b]$ e derivabile in $(a,b)$. Il segno della derivata prima determina la monotonia della funzione (vedi [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|Funzioni Monotone]]).

- Se $f'(x) > 0$ per ogni $x \in (a,b)$, allora $f$ è **strettamente crescente** in $[a,b]$.
    
- Se $f'(x) < 0$ per ogni $x \in (a,b)$, allora $f$ è **strettamente decrescente** in $[a,b]$.
    
- Se $f'(x) \ge 0$ per ogni $x \in (a,b)$, allora $f$ è **crescente** in $[a,b]$.
    
- Se $f'(x) \le 0$ per ogni $x \in (a,b)$, allora $f$ è **decrescente** in $[a,b]$.
    

**Dimostrazione (caso** $f'(x)>0$**):** Siano $x_1, x_2 \in [a,b]$ con $x_1 < x_2$. Per il Teorema di Lagrange sull'intervallo $[x_1, x_2]$, esiste un $x_0 \in (x_1, x_2)$ tale che $\frac{f(x_2)-f(x_1)}{x_2-x_1} = f'(x_0)$. Per ipotesi, $f'(x_0) > 0$. Inoltre, $x_2-x_1 > 0$. Pertanto, $f(x_2)-f(x_1) = f'(x_0) \cdot (x_2-x_1) > 0$, da cui $f(x_2) > f(x_1)$. Questo dimostra che la funzione è strettamente crescente.

**Nota:** L'implicazione inversa richiede cautela. Se una funzione è strettamente crescente, la sua derivata sarà $f'(x) \ge 0$. Non è garantito che sia strettamente positiva. Ad esempio, $f(x) = x^3$ è strettamente crescente, ma la sua derivata $f'(x) = 3x^2$ si annulla in $x=0$.