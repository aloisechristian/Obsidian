## Estremi Relativi: Definizioni e Proprietà

### Definizioni di Massimo e Minimo Relativo
Un punto $x_0$ si definisce **punto di massimo relativo** per una funzione $f(x)$ se esiste un intorno di $x_0$, denotato come $(x_0 - \delta, x_0 + \delta)$ con $\delta > 0$, tale che per ogni $x$ in tale intorno, si verifica la seguente condizione:
$$f(x_0) \ge f(x) \quad \forall x \in (x_0 - \delta, x_0 + \delta)$$
Questa condizione può essere espressa in modo equivalente utilizzando il valore assoluto: $f(x_0) \ge f(x)$ per ogni $x$ tale che $|x - x_0| < \delta$.

Analogamente, un punto $x_0$ è un **punto di minimo relativo** se esiste un intorno di $x_0$ in cui il valore della funzione in $x_0$ è il più piccolo:
$$f(x_0) \le f(x) \quad \forall x \in (x_0 - \delta, x_0 + \delta)$$

### Relazione tra Estremi Assoluti e Relativi
È importante notare la distinzione tra estremi relativi (locali) ed estremi assoluti (globali).
- Un **estremo assoluto** (massimo o minimo) è anche un estremo relativo. Se $f(x_0)$ è il valore massimo della funzione su tutto il suo dominio, a maggior ragione lo sarà in un piccolo intorno di $x_0$.
- Il viceversa non è vero: un **estremo relativo** non è necessariamente un estremo assoluto. La condizione di massimo o minimo è verificata solo localmente.

## Teorema di Fermat
Il Teorema di Fermat stabilisce un legame fondamentale tra i punti di estremo relativo e la derivata della funzione.

**Enunciato:** Sia $f$ una funzione definita in un intervallo e sia $x_0$ un punto interno a tale intervallo. Se $x_0$ è un punto di estremo relativo (massimo o minimo) e la funzione $f$ è derivabile in $x_0$, allora la sua derivata prima in quel punto è nulla:
$$f'(x_0) = 0$$

**Dimostrazione:**
Supponiamo, senza perdita di generalità, che $x_0$ sia un punto di massimo relativo. Per definizione, esiste un $\delta > 0$ tale che $f(x_0) \ge f(x)$ per ogni $x$ con $|x - x_0| < \delta$. Sostituendo $x = x_0 + h$ con $|h| < \delta$, otteniamo:
$$f(x_0) \ge f(x_0 + h) \implies f(x_0 + h) - f(x_0) \le 0$$
Il numeratore del rapporto incrementale è quindi non positivo.

Consideriamo ora il rapporto incrementale $\frac{f(x_0 + h) - f(x_0)}{h}$ e analizziamo il suo segno al variare di $h$:
1.  **Caso $h > 0$:** Il numeratore è $\le 0$ e il denominatore è $> 0$. Pertanto, il rapporto è $\le 0$. Passando al limite per $h \to 0^+$, per il teorema della permanenza del segno, la derivata destra è non positiva:
    $$f'_+(x_0) = \lim_{h \to 0^+} \frac{f(x_0 + h) - f(x_0)}{h} \le 0$$
2.  **Caso $h < 0$:** Il numeratore è $\le 0$ e il denominatore è $< 0$. Pertanto, il rapporto è $\ge 0$. Passando al limite per $h \to 0^-$, la derivata sinistra è non negativa:
    $$f'_-(x_0) = \lim_{h \to 0^-} \frac{f(x_0 + h) - f(x_0)}{h} \ge 0$$

Poiché per ipotesi la funzione $f$ è derivabile in $x_0$, la derivata destra e sinistra devono esistere, essere finite e coincidere: $f'(x_0) = f'_+(x_0) = f'_-(x_0)$. L'unico valore che soddisfa contemporaneamente le condizioni $f'(x_0) \le 0$ e $f'(x_0) \ge 0$ è $0$. Dunque, si conclude che:
$$f'(x_0) = 0$$

## Teorema di Rolle
**Enunciato:** Sia $f$ una funzione che soddisfa le seguenti ipotesi:
1.  Continua nell'intervallo chiuso e limitato $[a, b]$.
2.  Derivabile nell'intervallo aperto $(a, b)$.
3.  Assume valori uguali agli estremi dell'intervallo, cioè $f(a) = f(b)$.
Allora, esiste almeno un punto $c \in (a, b)$ tale che la derivata prima in quel punto è nulla:
$$f'(c) = 0$$

**Dimostrazione:**
Poiché $f$ è continua su un intervallo chiuso e limitato $[a, b]$, per il [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Teorema di Weierstrass|Teorema di Weierstrass]], essa ammette un massimo assoluto $M$ e un minimo assoluto $m$ in tale intervallo.
Si presentano due casi:
1.  **Almeno uno tra il punto di massimo e il punto di minimo cade all'interno dell'intervallo $(a, b)$:** Sia $c \in (a, b)$ tale punto. Poiché è un estremo assoluto, è anche un estremo relativo. Essendo $f$ derivabile in $(a, b)$, per il [[#Teorema di Fermat|Teorema di Fermat]] si ha che $f'(c) = 0$.
2.  **Sia il punto di massimo che il punto di minimo sono assunti agli estremi dell'intervallo:** In questo caso, il valore massimo della funzione è $M=f(a)$ (o $f(b)$) e il valore minimo è $m=f(a)$ (o $f(b)$). Per l'ipotesi $f(a) = f(b)$, ne consegue che $M=m$. Questo implica che la funzione è costante su tutto l'intervallo $[a, b]$. La derivata di una funzione costante è zero in ogni punto, quindi $f'(x) = 0$ per ogni $x \in (a, b)$.

In entrambi i casi, è dimostrata l'esistenza di almeno un punto $c \in (a, b)$ tale che $f'(c)=0$.

## Teorema di Lagrange (o del Valor Medio)
Il Teorema di Lagrange è una generalizzazione del Teorema di Rolle.

**Enunciato:** Sia $f$ una funzione che soddisfa le seguenti ipotesi:
1.  Continua nell'intervallo chiuso e limitato $[a, b]$.
2.  Derivabile nell'intervallo aperto $(a, b)$.
Allora, esiste almeno un punto $c \in (a, b)$ tale che:
$$f'(c) = \frac{f(b) - f(a)}{b - a}$$
Il termine $\frac{f(b) - f(a)}{b - a}$ rappresenta il coefficiente angolare della retta secante il grafico di $f$ nei punti $(a, f(a))$ e $(b, f(b))$. Il teorema garantisce quindi l'esistenza di un punto $c$ in cui la retta tangente al grafico è parallela alla retta secante.

**Dimostrazione:**
La dimostrazione si basa sulla costruzione di una funzione ausiliaria $g(x)$ alla quale applicare il [[#Teorema di Rolle|Teorema di Rolle]]. Definiamo $g(x)$ come la differenza tra la funzione $f(x)$ e l'equazione della retta secante passante per i punti $(a, f(a))$ e $(b, f(b))$:
$$g(x) = f(x) - \left[ f(a) + \frac{f(b) - f(a)}{b - a}(x - a) \right]$$
Verifichiamo le ipotesi del Teorema di Rolle per $g(x)$:
1.  $g(x)$ è continua in $[a, b]$ perché è somma di $f(x)$ (continua per ipotesi) e di una funzione lineare (continua).
2.  $g(x)$ è derivabile in $(a, b)$ perché è somma di $f(x)$ (derivabile per ipotesi) e di una funzione lineare (derivabile).
3.  Calcoliamo $g(x)$ agli estremi:
    $$g(a) = f(a) - \left[ f(a) + \frac{f(b) - f(a)}{b - a}(a - a) \right] = 0$$
    $$g(b) = f(b) - \left[ f(a) + \frac{f(b) - f(a)}{b - a}(b - a) \right] = f(b) - [f(a) + f(b) - f(a)] = 0$$
Poiché $g(a) = g(b) = 0$, le ipotesi del Teorema di Rolle sono soddisfatte. Esiste quindi un punto $c \in (a, b)$ tale che $g'(c) = 0$.

Calcoliamo la derivata di $g(x)$:
$$g'(x) = f'(x) - \frac{f(b) - f(a)}{b - a}$$
Valutando in $c$ e ponendo la derivata uguale a zero, otteniamo la tesi:
$$g'(c) = 0 \implies f'(c) - \frac{f(b) - f(a)}{b - a} = 0 \implies f'(c) = \frac{f(b) - f(a)}{b - a}$$

## Criterio di Monotonia

### Definizioni di Funzione Monotona
Sia $f$ una funzione definita in un intervallo $I$.
- $f$ si dice **crescente** in $I$ se $\forall x_1, x_2 \in I$ con $x_1 < x_2 \implies f(x_1) \le f(x_2)$.
- $f$ si dice **strettamente crescente** in $I$ se $\forall x_1, x_2 \in I$ con $x_1 < x_2 \implies f(x_1) < f(x_2)$.
- $f$ si dice **decrescente** in $I$ se $\forall x_1, x_2 \in I$ con $x_1 < x_2 \implies f(x_1) \ge f(x_2)$.
- $f$ si dice **strettamente decrescente** in $I$ se $\forall x_1, x_2 \in I$ con $x_1 < x_2 \implies f(x_1) > f(x_2)$.

### Teorema (Criterio di Monotonia)
Sia $f$ una funzione continua in $[a, b]$ e derivabile in $(a, b)$. Allora valgono le seguenti equivalenze:
1.  $f$ è crescente in $[a, b] \iff f'(x) \ge 0$ per ogni $x \in (a, b)$.
2.  $f$ è decrescente in $[a, b] \iff f'(x) \le 0$ per ogni $x \in (a, b)$.

**Dimostrazione dell'equivalenza per funzioni crescenti:**
- **($\impliedby$) $f'(x) \ge 0 \implies f$ è crescente:**
  Siano $x_1, x_2 \in [a, b]$ con $x_1 < x_2$. La funzione $f$ soddisfa le ipotesi del [[#Teorema di Lagrange (o del Valor Medio)|Teorema di Lagrange]] sull'intervallo $[x_1, x_2]$. Esiste quindi un $c \in (x_1, x_2)$ tale che:
  $$f(x_2) - f(x_1) = f'(c)(x_2 - x_1)$$
  Per ipotesi, $f'(c) \ge 0$. Inoltre, poiché $x_1 < x_2$, il fattore $(x_2 - x_1)$ è strettamente positivo. Il prodotto di un numero non negativo per uno positivo è non negativo:
  $$f(x_2) - f(x_1) \ge 0 \implies f(x_2) \ge f(x_1)$$
  Questa è la definizione di funzione crescente.

- **($\implies$) $f$ è crescente $\implies f'(x) \ge 0$:**
  Per definizione, $f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$. Analizziamo il segno del rapporto incrementale:
  - Se $h > 0$, allora $x+h > x$. Poiché $f$ è crescente, $f(x+h) \ge f(x)$, quindi il numeratore è $\ge 0$. Il rapporto $\frac{\ge 0}{> 0}$ è $\ge 0$.
  - Se $h < 0$, allora $x+h < x$. Poiché $f$ è crescente, $f(x+h) \le f(x)$, quindi il numeratore è $\le 0$. Il rapporto $\frac{\le 0}{< 0}$ è $\ge 0$.
  In entrambi i casi il rapporto incrementale è non negativo. Per il teorema della permanenza del segno, anche il suo limite, cioè $f'(x)$, sarà non negativo: $f'(x) \ge 0$.

## Criterio di Stretta Monotonia
**Teorema:** Sia $f$ continua in $[a, b]$ e derivabile in $(a, b)$. Allora:
- $f$ è **strettamente crescente** in $[a, b]$ se e solo se $f'(x) \ge 0$ per ogni $x \in (a, b)$ e $f'$ non si annulla identicamente in alcun intervallo contenuto in $(a,b)$.
- $f$ è **strettamente decrescente** in $[a, b]$ se e solo se $f'(x) \le 0$ per ogni $x \in (a, b)$ e $f'$ non si annulla identicamente in alcun intervallo contenuto in $(a,b)$.

**Commento:** La condizione $f'(x) > 0$ è sufficiente ma non necessaria per la stretta crescenza. Una funzione può essere strettamente crescente anche se la sua derivata si annulla in punti isolati. L'importante è che non si annulli su un intero intervallo, altrimenti la funzione sarebbe costante in quel tratto, violando la stretta crescenza.

**Esempio:** Si consideri la funzione $f(x) = x^3$. La sua derivata è $f'(x) = 3x^2$. Si ha $f'(x) \ge 0$ per ogni $x \in \mathbb{R}$, e $f'(x) = 0$ solo per $x=0$. Poiché la derivata non si annulla su un intervallo, ma solo in un punto, la funzione $f(x) = x^3$ è strettamente crescente su tutto $\mathbb{R}$.

**Dimostrazione (una implicazione per la stretta crescenza):**
- **($\impliedby$) $f'(x) \ge 0$ e $f'$ non nulla su intervalli $\implies f$ è strettamente crescente:**
  Dal [[#Criterio di Monotonia|Criterio di Monotonia]], sappiamo già che $f$ è crescente. Dobbiamo mostrare che è *strettamente* crescente.
  Procediamo per assurdo: supponiamo che $f$ non sia strettamente crescente. Allora esistono $x_1, x_2 \in [a, b]$ con $x_1 < x_2$ tali che $f(x_1) = f(x_2)$. Poiché $f$ è crescente, per ogni $x \in [x_1, x_2]$ deve valere $f(x_1) \le f(x) \le f(x_2)$. Essendo $f(x_1) = f(x_2)$, ne consegue che $f(x) = f(x_1)$ per ogni $x \in [x_1, x_2]$. La funzione è quindi costante sull'intervallo $[x_1, x_2]$. Di conseguenza, la sua derivata deve essere nulla in tutto l'intervallo $(x_1, x_2)$, cioè $f'(x) = 0$ per ogni $x \in (x_1, x_2)$. Questo contraddice l'ipotesi che la derivata non si annulli identicamente su nessun intervallo. Pertanto, la funzione deve essere strettamente crescente.
- **($\implies$) $f$ è strettamente crescente $\implies f'(x) \ge 0$ e $f'$ non nulla su intervalli:**
  Dal [[#Criterio di Monotonia|Criterio di Monotonia]], se $f$ è crescente (e a maggior ragione se strettamente crescente), allora $f'(x) \ge 0$. Inoltre, se $f'$ si annullasse identicamente su un intervallo $[x_1, x_2]$, la funzione $f$ sarebbe costante su tale intervallo, contrariamente all'ipotesi di stretta monotonia.

## Convessità e Concavità

### Definizioni
Sia $f$ una funzione derivabile in un intervallo $I$. L'equazione della retta tangente al grafico di $f$ nel punto $(x_0, f(x_0))$ è:
$$y(x) = f(x_0) + f'(x_0)(x - x_0)$$
- La funzione $f$ si dice **convessa** in $I$ se, per ogni $x_0 \in I$, il suo grafico si trova al di sopra della retta tangente in $x_0$. Matematicamente:
  $$f(x) \ge f(x_0) + f'(x_0)(x - x_0) \quad \forall x, x_0 \in I$$
- La funzione $f$ si dice **concava** in $I$ se, per ogni $x_0 \in I$, il suo grafico si trova al di sotto della retta tangente in $x_0$. Matematicamente:
  $$f(x) \le f(x_0) + f'(x_0)(x - x_0) \quad \forall x, x_0 \in I$$

### Criterio di Convessità
Sia $f$ una funzione derivabile due volte in un intervallo $[a,b]$. Le seguenti proposizioni sono equivalenti:
1.  $f$ è convessa in $[a, b]$.
2.  La sua derivata prima, $f'$, è crescente in $[a, b]$.
3.  La sua derivata seconda, $f''$, è non negativa in $(a, b)$, cioè $f''(x) \ge 0$ per ogni $x \in (a, b)$.

**Dimostrazione:**
- **(2) $\iff$ (3):** Questa equivalenza è un'applicazione diretta del [[#Criterio di Monotonia|Criterio di Monotonia]] alla funzione $g(x) = f'(x)$. La funzione $g=f'$ è crescente se e solo se la sua derivata, $g' = f''$, è non negativa ($g'(x) = f''(x) \ge 0$).

- **(1) $\implies$ (2) ($f$ convessa $\implies f'$ crescente):**
  Per ipotesi, $f$ è convessa. Siano $x_1, x_2 \in [a, b]$ con $x_1 < x_2$. Vogliamo dimostrare che $f'(x_1) \le f'(x_2)$.
  Usiamo la definizione di convessità, scegliendo prima $x_0 = x_1$ e $x = x_2$, e poi $x_0 = x_2$ e $x = x_1$:
  1. $f(x_2) \ge f(x_1) + f'(x_1)(x_2 - x_1)$
  2. $f(x_1) \ge f(x_2) + f'(x_2)(x_1 - x_2)$
  Sommando membro a membro queste due disequazioni otteniamo:
  $$f(x_1) + f(x_2) \ge f(x_1) + f(x_2) + f'(x_1)(x_2 - x_1) + f'(x_2)(x_1 - x_2)$$
  Semplificando, otteniamo:
  $$0 \ge f'(x_1)(x_2 - x_1) - f'(x_2)(x_2 - x_1)$$
  $$0 \ge [f'(x_1) - f'(x_2)](x_2 - x_1)$$
  Poiché $x_1 < x_2$, il termine $(x_2 - x_1)$ è strettamente positivo. Affinché il prodotto sia non positivo, deve essere:
  $$f'(x_1) - f'(x_2) \le 0 \implies f'(x_1) \le f'(x_2)$$
  Questo dimostra che $f'$ è crescente.

- **(2) $\implies$ (1) ($f'$ crescente $\implies f$ convessa):**
  Per ipotesi, $f'$ è crescente. Vogliamo dimostrare che $f(x) \ge f(x_0) + f'(x_0)(x - x_0)$ per ogni $x, x_0 \in [a, b]$.
  Fissiamo $x$ e $x_0$ distinti. Applichiamo il [[#Teorema di Lagrange (o del Valor Medio)|Teorema di Lagrange]] alla funzione $f$ nell'intervallo di estremi $x$ e $x_0$. Esiste un punto $c$ compreso tra $x$ e $x_0$ tale che:
  $$f(x) - f(x_0) = f'(c)(x - x_0)$$
  Analizziamo due casi:
  1. **Caso $x > x_0$:** Allora $x_0 < c < x$. Poiché $f'$ è crescente, $f'(c) \ge f'(x_0)$. Moltiplicando entrambi i membri per $(x - x_0)$ (che è positivo), la disuguaglianza si mantiene:
    $$f'(c)(x - x_0) \ge f'(x_0)(x - x_0)$$
    Sostituendo l'espressione di Lagrange:
    $$f(x) - f(x_0) \ge f'(x_0)(x - x_0) \implies f(x) \ge f(x_0) + f'(x_0)(x - x_0)$$
  2. **Caso $x < x_0$:** Allora $x < c < x_0$. Poiché $f'$ è crescente, $f'(c) \le f'(x_0)$. Moltiplicando entrambi i membri per $(x - x_0)$ (che è negativo), la disuguaglianza si inverte:
    $$f'(c)(x - x_0) \ge f'(x_0)(x - x_0)$$
    Sostituendo l'espressione di Lagrange, otteniamo di nuovo:
    $$f(x) - f(x_0) \ge f'(x_0)(x - x_0) \implies f(x) \ge f(x_0) + f'(x_0)(x - x_0)$$
  In entrambi i casi, abbiamo ritrovato la definizione di funzione convessa.

Analogamente, una funzione $f$ è **concava** se e solo se $f'$ è decrescente, il che è equivalente a $f''(x) \le 0$ per ogni $x \in (a,b)$.

## Punti di Flesso
Un punto $x_0$ (interno al dominio) si definisce **punto di flesso** se la funzione $f$ è continua in $x_0$ e se esiste un intorno $(x_0-\delta, x_0+\delta)$ tale che la funzione cambia concavità in $x_0$.
- Se $f$ è derivabile due volte, una condizione necessaria (ma non sufficiente) affinché $x_0$ sia un punto di flesso è che $f''(x_0)=0$.
- Se $f''(x_0)=0$ e la derivata seconda cambia segno attraversando $x_0$ (cioè $f''(x)$ è negativa prima e positiva dopo, o viceversa), allora $x_0$ è un punto di flesso.

## Punti di Non Derivabilità
Esistono punti in cui la funzione è continua ma non derivabile, che sono critici per lo studio del grafico:
1.  **Flesso a Tangente Verticale:** Si ha quando $f$ è continua in $x_0$ e i limiti destro e sinistro del rapporto incrementale tendono entrambi a $+\infty$ o entrambi a $-\infty$.
    $$\lim_{h \to 0} \frac{f(x_0+h) - f(x_0)}{h} = \pm \infty$$
    In questo caso, la retta tangente è verticale ($x=x_0$) e $x_0$ è un punto di flesso.
2.  **Punto Angoloso:** Si ha quando $f$ è continua in $x_0$ e le derivate destra ($f'_+(x_0)$) e sinistra ($f'_-(x_0)$) esistono, sono diverse tra loro ($f'_+(x_0) \ne f'_-(x_0)$), e almeno una delle due è finita.
    *Esempio: $f(x) = |x|$ in $x_0=0$, dove $f'_-(0)=-1$ e $f'_+(0)=+1$.*
3.  **Cuspide:** Si ha quando $f$ è continua in $x_0$ e le derivate destra e sinistra sono entrambe infinite ma di segno opposto.
    $$\lim_{h \to 0^+} \frac{f(x_0+h) - f(x_0)}{h} = +\infty \quad \text{e} \quad \lim_{h \to 0^-} \frac{f(x_0+h) - f(x_0)}{h} = -\infty$$
    (o viceversa). La tangente è verticale ($x=x_0$) ma la funzione "torna indietro".