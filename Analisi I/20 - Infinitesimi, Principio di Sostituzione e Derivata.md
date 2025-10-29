# Infinitesimi, Infiniti e Introduzione alle Derivate

## Definizioni di Infinito e Infinitesimo

Nel calcolo dei limiti, si incontrano spesso funzioni con comportamenti particolari in prossimità di un punto di accumulazione. Introduciamo due definizioni fondamentali.

Sia $f(x)$ una funzione e sia $x_0$ un [[17 - Intorni, Punti di Accumulazione e Limiti di Funzione#1.2. Punti di Accumulazione|punto di accumulazione]] per il suo dominio (con $x_0$ che può essere un numero reale, $+\infty$ o $-\infty$).

1.  **Infinito**: La funzione $f(x)$ si dice un **infinito** per $x \to x_0$ se il suo limite è $\pm\infty$.
    $$\lim_{x \to x_0} |f(x)| = +\infty$$

2.  **Infinitesimo**: La funzione $f(x)$ si dice un **infinitesimo** per $x \to x_0$ se il suo limite è uguale a 0.
    $$\lim_{x \to x_0} f(x) = 0$$

Queste definizioni sono cruciali per affrontare le [[14 - Definizione e Teoremi dei Limiti di Successioni#Forme Indeterminate|forme indeterminate]], in particolare quelle del tipo $\frac{0}{0}$ e $\frac{\infty}{\infty}$. Per risolvere tali limiti, è necessario confrontare la "velocità" con cui due funzioni tendono a zero (infinitesimi) o a infinito (infiniti).

## Confronto tra Infinitesimi e Notazione "o-piccolo"

Consideriamo due funzioni $f(x)$ e $g(x)$ entrambe infinitesime per $x \to x_0$. Per confrontarle, si suppone che $f(x)$ e $g(x)$ non si annullino in un opportuno intorno di $x_0$ (con $x \neq x_0$) e si analizza il limite del loro rapporto:

$$\lim_{x \to x_0} \frac{f(x)}{g(x)}$$

A seconda del risultato di questo limite, possiamo classificare la relazione tra i due infinitesimi:

1.  **Infinitesimo di Ordine Superiore**: Se il limite del rapporto è zero,
    $$\lim_{x \to x_0} \frac{f(x)}{g(x)} = 0$$
    significa che $f(x)$ tende a zero "più rapidamente" di $g(x)$. In questo caso, si dice che **$f(x)$ è un infinitesimo di ordine superiore rispetto a $g(x)$** e si utilizza la notazione di Landau, scrivendo:
    $$f(x) = o(g(x)) \quad (\text{si legge: f di x è un o-piccolo di g di x})$$

2.  **Infinitesimi dello Stesso Ordine**: Se il limite del rapporto è un numero finito $L$ diverso da zero,
    $$\lim_{x \to x_0} \frac{f(x)}{g(x)} = L \in \mathbb{R}, \quad L \neq 0$$
    si dice che **$f(x)$ e $g(x)$ sono infinitesimi dello stesso ordine**.
    -   Un caso particolare si ha quando $L=1$. In questa situazione, $f(x)$ e $g(x)$ si dicono **infinitesimi equivalenti**.

3.  **Infinitesimo di Ordine Inferiore**: Se il limite del rapporto è infinito ($\pm\infty$),
    $$\lim_{x \to x_0} \frac{f(x)}{g(x)} = \pm\infty$$
    significa che $g(x)$ tende a zero più rapidamente di $f(x)$. Si dice che **$f(x)$ è un infinitesimo di ordine inferiore rispetto a $g(x)$**.
    Questa condizione è equivalente a dire che $g(x)$ è un infinitesimo di ordine superiore rispetto a $f(x)$, ovvero $g(x) = o(f(x))$, poiché:
    $$\lim_{x \to x_0} \frac{g(x)}{f(x)} = 0$$

Le stesse definizioni (con le dovute attenzioni sui rapporti) si applicano in modo analogo per il **confronto tra infiniti**.

## Algebra degli "o-piccolo"

La notazione "o-piccolo" segue alcune regole algebriche utili nei calcoli.

### 1. Somma di o-piccolo
Se $f_1(x) = o(g(x))$ e $f_2(x) = o(g(x))$, allora anche la loro somma è un o-piccolo di $g(x)$:
$$o(g(x)) + o(g(x)) = o(g(x))$$

*Dimostrazione*: Per ipotesi, sappiamo che:
$$\lim_{x \to x_0} \frac{f_1(x)}{g(x)} = 0 \quad \text{e} \quad \lim_{x \to x_0} \frac{f_2(x)}{g(x)} = 0$$
Per verificare la tesi, calcoliamo il limite del rapporto tra la somma e $g(x)$:
$$\lim_{x \to x_0} \frac{f_1(x) + f_2(x)}{g(x)} = \lim_{x \to x_0} \left( \frac{f_1(x)}{g(x)} + \frac{f_2(x)}{g(x)} \right)$$
Poiché i singoli limiti sono finiti (entrambi 0), il limite della somma è la somma dei limiti:
$$= \left( \lim_{x \to x_0} \frac{f_1(x)}{g(x)} \right) + \left( \lim_{x \to x_0} \frac{f_2(x)}{g(x)} \right) = 0 + 0 = 0$$
Ciò dimostra che $f_1(x) + f_2(x) = o(g(x))$.

### 2. Prodotto di o-piccolo
Se $f_1(x) = o(g_1(x))$ e $f_2(x) = o(g_2(x))$, il loro prodotto è un o-piccolo del prodotto $g_1(x)g_2(x)$:
$$o(g_1(x)) \cdot o(g_2(x)) = o(g_1(x) \cdot g_2(x))$$
Un caso particolare di questa regola è:
$$o(g(x)) \cdot o(g(x)) = o(g(x)^2)$$

*Dimostrazione (caso $o(g(x)^2)$)*: Siano $f_1(x) = o(g(x))$ e $f_2(x) = o(g(x))$. Dobbiamo calcolare il limite del rapporto tra il prodotto $f_1(x) \cdot f_2(x)$ e $g(x)^2$:
$$\lim_{x \to x_0} \frac{f_1(x) \cdot f_2(x)}{g(x)^2} = \lim_{x \to x_0} \left( \frac{f_1(x)}{g(x)} \cdot \frac{f_2(x)}{g(x)} \right)$$
Poiché i limiti dei singoli fattori esistono e sono finiti (entrambi 0), il limite del prodotto è il prodotto dei limiti:
$$= \left( \lim_{x \to x_0} \frac{f_1(x)}{g(x)} \right) \cdot \left( \lim_{x \to x_0} \frac{f_2(x)}{g(x)} \right) = 0 \cdot 0 = 0$$
Questo dimostra che $f_1(x) \cdot f_2(x) = o(g(x)^2)$.

## Ordine di un Infinitesimo

Per quantificare la velocità di convergenza a zero di un infinitesimo, si introduce il concetto di **ordine**. Si utilizza come termine di paragone la funzione "infinitesimo campione":
$$g(x) = |x-x_0|^{\alpha}, \quad \text{con } \alpha > 0$$
Una funzione $f(x)$ si dice **infinitesimo di ordine $\alpha$** per $x \to x_0$ se $f(x)$ e $|x-x_0|^\alpha$ sono infinitesimi dello stesso ordine, ovvero se:
$$\lim_{x \to x_0} \frac{f(x)}{|x-x_0|^{\alpha}} = L \in \mathbb{R}, \quad L \neq 0$$
(Spesso, se $x_0=0$, si usa $x^\alpha$ come campione). L'esponente $\alpha$ rappresenta l'ordine dell'infinitesimo.

## Principio di Sostituzione degli Infinitesimi

Questo principio è uno strumento potente per il calcolo di limiti che si presentano in forma indeterminata $\frac{0}{0}$.

**Teorema**: Siano $f_1, g_1, f_2, g_2$ funzioni infinitesime per $x \to x_0$. Se $g_1$ è un infinitesimo di ordine superiore rispetto a $f_1$ (cioè $g_1 = o(f_1)$) e $g_2$ è un infinitesimo di ordine superiore rispetto a $f_2$ (cioè $g_2 = o(f_2)$), allora i seguenti limiti sono uguali (purché il secondo esista):
$$\lim_{x \to x_0} \frac{f_1(x) + g_1(x)}{f_2(x) + g_2(x)} = \lim_{x \to x_0} \frac{f_1(x)}{f_2(x)}$$
In pratica, gli infinitesimi di ordine superiore (gli "o-piccolo") possono essere trascurati nelle somme al numeratore e al denominatore.

*Dimostrazione*: Si manipola l'espressione mettendo in evidenza $f_1$ al numeratore e $f_2$ al denominatore:
$$\lim_{x \to x_0} \frac{f_1(x) \left(1 + \frac{g_1(x)}{f_1(x)}\right)}{f_2(x) \left(1 + \frac{g_2(x)}{f_2(x)}\right)}$$
Per ipotesi, sappiamo che $\lim_{x \to x_0} \frac{g_1(x)}{f_1(x)} = 0$ e $\lim_{x \to x_0} \frac{g_2(x)}{f_2(x)} = 0$. Passando al limite, le espressioni tra parentesi tendono entrambe a $(1+0) = 1$:
$$= \left( \lim_{x \to x_0} \frac{f_1(x)}{f_2(x)} \right) \cdot \frac{1+0}{1+0} = \lim_{x \to x_0} \frac{f_1(x)}{f_2(x)}$$
Un principio analogo vale per la **sostituzione degli infiniti**, dove nelle somme si trascurano gli infiniti di ordine inferiore.

## Applicazioni ed Esempi

### Esempio 1: Confronto $1-\cos(x)$ e $\sin(x)$
Calcolare $\lim_{x \to 0} \frac{1 - \cos(x)}{\sin(x)}$.
Questo è un confronto tra due infinitesimi. Applichiamo la definizione:
$$
\begin{aligned}
\lim_{x \to 0} \frac{1 - \cos(x)}{\sin(x)} &= \lim_{x \to 0} \frac{1 - \cos(x)}{\sin(x)} \cdot \frac{1 + \cos(x)}{1 + \cos(x)} \\
&= \lim_{x \to 0} \frac{1 - \cos^2(x)}{\sin(x)(1 + \cos(x))} \\
&= \lim_{x \to 0} \frac{\sin^2(x)}{\sin(x)(1 + \cos(x))} \\
&= \lim_{x \to 0} \frac{\sin(x)}{1 + \cos(x)} = \frac{0}{1+1} = 0
\end{aligned}
$$
Poiché il limite è 0, concludiamo che $1 - \cos(x) = o(\sin(x))$ per $x \to 0$.

### Esempio 2: Limiti notevoli e o-piccolo
Dal limite notevole $\lim_{t \to 0} \frac{e^t - 1}{t} = 1$, segue che $\lim_{t \to 0} \left(\frac{e^t - 1}{t} - 1\right) = 0$, ovvero $\lim_{t \to 0} \frac{e^t - 1 - t}{t} = 0$.
Questo significa che $e^t - 1 - t = o(t)$, da cui si ottiene la fondamentale approssimazione:
$$e^t = 1 + t + o(t) \quad \text{per } t \to 0$$
Analogamente, da $\lim_{t \to 0} \frac{\log(1+t)}{t} = 1$, si ricava:
$$\log(1+t) = t + o(t) \quad \text{per } t \to 0$$

### Esempio 3: Calcolo con Principio di Sostituzione
Calcolare $\lim_{x \to 0} \frac{e^{\sin^3(x)} - 1}{\log(1 - x^3)}$.
Utilizziamo le approssimazioni trovate:
- Per il numeratore, usiamo $e^t = 1 + t + o(t)$. Poniamo $t = \sin^3(x)$. Per $x \to 0$, anche $t \to 0$.
  $e^{\sin^3(x)} - 1 = (1 + \sin^3(x) + o(\sin^3(x))) - 1 = \sin^3(x) + o(\sin^3(x))$.
- Per il denominatore, usiamo $\log(1+t) = t + o(t)$. Poniamo $t = -x^3$. Per $x \to 0$, $t \to 0$.
  $\log(1 - x^3) = -x^3 + o(-x^3) = -x^3 + o(x^3)$.

Applichiamo il principio di sostituzione, trascurando gli o-piccolo:
$$\lim_{x \to 0} \frac{\sin^3(x) + o(\sin^3(x))}{-x^3 + o(x^3)} = \lim_{x \to 0} \frac{\sin^3(x)}{-x^3}$$
Poiché $\sin(x)$ e $x$ sono infinitesimi equivalenti per $x \to 0$, anche $\sin^3(x)$ e $x^3$ lo sono.
$$= -\lim_{x \to 0} \left( \frac{\sin(x)}{x} \right)^3 = -(1)^3 = -1$$

---
## Introduzione al Concetto di Derivata

### Definizione di Derivata
Sia $f(x)$ una funzione definita in un intervallo aperto $(a, b)$ e sia $x \in (a, b)$.

La funzione $f$ si dice **derivabile** nel punto $x$ se esiste ed è **finito** il seguente limite, detto **limite del rapporto incrementale**:
$$\lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$
Il valore di tale limite, se esiste ed è finito, è chiamato **derivata prima** di $f$ nel punto $x$ e si indica con uno dei seguenti simboli:
$$f'(x), \quad Df(x), \quad \frac{df}{dx}, \quad y'$$
Si dice che $f$ è derivabile nell'intervallo aperto $(a, b)$ se è derivabile in ogni punto $x \in (a, b)$.

Per i punti agli estremi di un intervallo chiuso $[a, b]$, si definiscono la **derivata destra** in $a$ e la **derivata sinistra** in $b$, considerando rispettivamente il limite per $h \to 0^+$ e $h \to 0^-$.
Una funzione è derivabile in $[a, b]$ se è derivabile in $(a, b)$ e ammette derivata destra finita in $a$ e derivata sinistra finita in $b$.

### Calcolo di Derivate Elementari tramite Definizione

1.  **Funzione Costante**: $f(x) = q$.
    $$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h} = \lim_{h \to 0} \frac{q - q}{h} = \lim_{h \to 0} \frac{0}{h} = 0$$
    La derivata di una costante è zero.

2.  **Funzione Lineare**: $f(x) = mx + q$.
    $$f'(x) = \lim_{h \to 0} \frac{[m(x+h)+q] - [mx+q]}{h} = \lim_{h \to 0} \frac{mx+mh+q-mx-q}{h} = \lim_{h \to 0} \frac{mh}{h} = m$$
    La derivata è il coefficiente angolare della retta.

3.  **Funzione Quadratica**: $f(x) = x^2$.
    $$f'(x) = \lim_{h \to 0} \frac{(x+h)^2 - x^2}{h} = \lim_{h \to 0} \frac{x^2+2xh+h^2 - x^2}{h} = \lim_{h \to 0} \frac{h(2x+h)}{h} = \lim_{h \to 0} (2x+h) = 2x$$

### Esempio di Funzione Non Derivabile

Non tutte le funzioni sono derivabili in ogni punto del loro dominio. Consideriamo la funzione [[06 - Studio delle Funzioni Valore Assoluto e Potenza|valore assoluto]] $f(x) = |x|$ nel punto $x=0$.
Il rapporto incrementale in $x=0$ è:
$$\frac{f(0+h) - f(0)}{h} = \frac{|0+h| - |0|}{h} = \frac{|h|}{h}$$
Calcoliamo il limite destro e sinistro per $h \to 0$:
-   **Limite destro (Derivata destra)**: $\lim_{h \to 0^+} \frac{|h|}{h} = \lim_{h \to 0^+} \frac{h}{h} = 1$
-   **Limite sinistro (Derivata sinistra)**: $\lim_{h \to 0^-} \frac{|h|}{h} = \lim_{h \to 0^-} \frac{-h}{h} = -1$

Poiché il limite destro (1) e sinistro (-1) sono finiti ma **diversi**, il limite del rapporto incrementale per $h \to 0$ non esiste. Pertanto, la funzione $f(x) = |x|$ **non è derivabile** in $x=0$.

### Continuità e Derivabilità

L'esempio $f(x) = |x|$ mostra che una funzione può essere continua in un punto (è continua in $x=0$) ma non derivabile in quel punto.
Vale però il viceversa:

**Teorema:** Se una funzione $f$ è derivabile in un punto $x$, allora $f$ è anche continua in $x$.