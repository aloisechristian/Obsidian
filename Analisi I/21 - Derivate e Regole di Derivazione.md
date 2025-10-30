## Definizione di Derivata e Derivabilità

### Il Rapporto Incrementale e la Derivata in un Punto
Una funzione $f(x)$ si dice **derivabile** in un punto $x$ del suo dominio (che deve essere un [[17 - Intorni, Punti di Accumulazione e Limiti di Funzione#^01501c|punto di accumulazione]] per il dominio) se esiste ed è finito il seguente limite, detto **limite del rapporto incrementale**:

$$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$

Il valore finito di questo limite è chiamato **derivata prima** della funzione $f$ nel punto $x$. L'incremento $h$ rappresenta una piccola variazione (positiva o negativa) della variabile indipendente $x$.

### Significato Geometrico: Retta Tangente
Il [[20 - Infinitesimi, Principio di Sostituzione e Derivata#^a8f0e5|significato geometrico della derivata]] è fondamentale:
Il rapporto incrementale $\frac{f(x+h) - f(x)}{h}$ rappresenta il **coefficiente angolare della retta secante** il grafico della funzione nei punti $(x, f(x))$ e $(x+h, f(x+h))$.

Quando $h \to 0$, la retta secante tende a diventare la **retta tangente** al grafico della funzione nel punto $(x, f(x))$.
Pertanto, **la derivata $f'(x)$ è il coefficiente angolare della retta tangente** al grafico di $f$ nel punto $x$.

L'equazione della retta tangente al grafico di $f(x)$ nel punto $(x_0, f(x_0))$ è:
$$y - f(x_0) = f'(x_0)(x - x_0)$$

### Notazioni per la Derivata
La derivata prima di una funzione $f$ in un punto $x$ può essere indicata con diverse notazioni. Le più comuni sono:
- $f'(x)$ (Notazione di Lagrange)
- $D[f(x)]$ (Notazione di Cauchy)
- $\frac{dy}{dx}$ (Notazione di Leibniz, molto usata in fisica e ingegneria per la sua espressività)
- $\dot{y}$ (Notazione di Newton, usata prevalentemente in fisica per indicare la derivata rispetto al tempo)

### Derivabilità su Intervalli e Derivate Destra/Sinistra
- **Intervallo Aperto**: Una funzione è derivabile in un intervallo aperto $(a, b)$ se è derivabile in ogni singolo punto appartenente a tale intervallo.
- **Intervallo Chiuso**: Per definire la derivabilità su un intervallo chiuso $[a, b]$, è necessario introdurre il concetto di derivata destra e sinistra agli estremi. La **derivata destra** in $a$ è definita come:
  $$f'_+(a) = \lim_{h \to 0^+} \frac{f(a+h) - f(a)}{h}$$
  La **derivata sinistra** in $b$ è definita come:
  $$f'_-(b) = \lim_{h \to 0^-} \frac{f(b+h) - f(b)}{h}$$

Il concetto di derivata destra e sinistra può essere esteso a qualsiasi punto interno di un intervallo. Una funzione è derivabile in un punto $x$ se e solo se la derivata destra e la derivata sinistra in $x$ esistono, sono finite e coincidono ($f'_+(x) = f'_-(x)$).

Se le derivate destra e sinistra esistono ma sono diverse, il punto si dice **punto angoloso** (come vedremo per il valore assoluto).

## Primi Esempi di Calcolo di Derivate

### Derivata di una Funzione Costante
Sia $f(x) = q$, con $q$ costante. Il suo grafico è una retta orizzontale (coefficiente angolare nullo). Il rapporto incrementale è:
$$\frac{f(x+h) - f(x)}{h} = \frac{q - q}{h} = \frac{0}{h} = 0$$
Poiché il numeratore è esattamente zero (non una quantità che tende a zero), il limite del rapporto incrementale è zero.
$$D[q] = 0$$

### Derivata di una Funzione Lineare
Sia $f(x) = mx + q$. Il grafico è una retta con coefficiente angolare $m$. Applicando la definizione:
$$\lim_{h \to 0} \frac{(m(x+h) + q) - (mx + q)}{h} = \lim_{h \to 0} \frac{mx + mh + q - mx - q}{h} = \lim_{h \to 0} \frac{mh}{h} = m$$
La derivata di una funzione lineare è il suo coefficiente angolare $m$, confermando il significato geometrico.
$$D[mx+q] = m$$

### Derivata della Funzione Quadratica
Sia $f(x) = x^2$. Il calcolo del rapporto incrementale porta a:
$$\lim_{h \to 0} \frac{(x+h)^2 - x^2}{h} = \lim_{h \to 0} \frac{x^2 + 2xh + h^2 - x^2}{h} = \lim_{h \to 0} \frac{h(2x + h)}{h} = \lim_{h \to 0} (2x + h) = 2x$$
$$D[x^2] = 2x$$
Questo risultato anticipa una regola generale per le potenze.

## Relazione tra Continuità e Derivabilità

### Un Controesempio: La Funzione Valore Assoluto
Non tutte le funzioni [[18 - Limiti, Continuità e Teoremi sulle Funzioni Continue#^1e01f5|continue]] sono derivabili. Consideriamo la funzione $f(x) = |x|$ (vedi [[06 - Studio delle Funzioni Valore Assoluto e Potenza]]). Nel punto $x=0$, la funzione è continua, poiché $\lim_{x \to 0} |x| = 0 = |0|$.
Tuttavia, le derivate destra e sinistra in $x=0$ non coincidono:
- **Derivata destra**: $f'_+(0) = \lim_{h \to 0^+} \frac{|0+h| - |0|}{h} = \lim_{h \to 0^+} \frac{h}{h} = 1$
- **Derivata sinistra**: $f'_-(0) = \lim_{h \to 0^-} \frac{|0+h| - |0|}{h} = \lim_{h \to 0^-} \frac{-h}{h} = -1$
Poiché $f'_+(0) \neq f'_-(0)$, la funzione non è derivabile in $x=0$. Il punto $(0,0)$ è un **punto angoloso**. Questo dimostra che **la continuità non implica la derivabilità**.

### Teorema: La Derivabilità Implica la Continuità
Si vuole dimostrare che se una funzione $f$ è derivabile in un punto $x$, allora è anche continua in $x$.

**Ipotesi**: $f$ è derivabile in $x$. Ciò significa che esiste ed è finito il limite:
$$\lim_{h \to 0} \frac{f(x+h) - f(x)}{h} = f'(x)$$

**Tesi**: $f$ è continua in $x$. Dobbiamo dimostrare che:
$$\lim_{h \to 0} f(x+h) = f(x)$$
(che è equivalente a $\lim_{h \to 0} [f(x+h) - f(x)] = 0$)

**Dimostrazione**:
Partiamo dall'espressione $f(x+h) - f(x)$ e manipoliamola algebricamente per far comparire il rapporto incrementale.
$$\begin{aligned}
\lim_{h \to 0} [f(x+h) - f(x)] &= \lim_{h \to 0} \left[ \frac{f(x+h) - f(x)}{h} \cdot h \right] \\
\end{aligned}$$
Utilizzando l'algebra dei limiti (il limite di un prodotto è il prodotto dei limiti), e notando che non si generano forme indeterminate ($f'(x)$ è finito per ipotesi):
$$\begin{aligned}
&= \left( \lim_{h \to 0} \frac{f(x+h) - f(x)}{h} \right) \cdot \left( \lim_{h \to 0} h \right) \\
&= f'(x) \cdot 0 \\
&= 0
\end{aligned}$$
Abbiamo quindi dimostrato che $\lim_{h \to 0} [f(x+h) - f(x)] = 0$, ovvero la tesi.
**Se una funzione è derivabile in un punto, allora è necessariamente continua in quel punto**.

## Derivate di Ordine Superiore
Se la funzione derivata prima, $f'(x)$, è a sua volta derivabile, è possibile calcolarne la derivata. Il risultato è la **derivata seconda** di $f(x)$, indicata con $f''(x)$, $D^2[f(x)]$ o $\frac{d^2y}{dx^2}$.
Questo processo può essere iterato. Derivando la funzione $n$ volte si ottiene la **derivata n-esima**, indicata con $f^{(n)}(x)$.

## Algebra delle Derivate: Regole di Derivazione

### Regola della Somma (Linearità)
Se $f$ e $g$ sono due funzioni derivabili in $x$, e $c \in \mathbb{R}$ è una costante, allora:
1.  **Somma/Differenza**: $D[f(x) \pm g(x)] = f'(x) \pm g'(x)$
2.  **Prodotto per scalare**: $D[c \cdot f(x)] = c \cdot f'(x)$

La combinazione di queste due regole costituisce la **proprietà di linearità** dell'operatore di derivazione.

**Dimostrazione (Somma)**:
Applicando la definizione al rapporto incrementale della funzione somma:
$$\begin{aligned}
D[f(x) + g(x)] &= \lim_{h \to 0} \frac{[f(x+h)+g(x+h)] - [f(x)+g(x)]}{h} \\
&= \lim_{h \to 0} \frac{[f(x+h) - f(x)] + [g(x+h) - g(x)]}{h} \\
&= \lim_{h \to 0} \left( \frac{f(x+h) - f(x)}{h} \right) + \lim_{h \to 0} \left( \frac{g(x+h) - g(x)}{h} \right) \\
&= f'(x) + g'(x)
\end{aligned}$$

### Regola del Prodotto (Regola di Leibniz)
Se $f$ e $g$ sono derivabili in $x$, allora anche il loro prodotto $(f \cdot g)$ è derivabile in $x$ e vale:
$$D[f(x) g(x)] = f'(x)g(x) + f(x)g'(x)$$
**Dimostrazione**:
Consideriamo il rapporto incrementale del prodotto. Con un artificio algebrico (sommando e sottraendo $f(x)g(x+h)$ al numeratore):
$$\begin{aligned}
&\lim_{h \to 0} \frac{f(x+h)g(x+h) - f(x)g(x)}{h} \\
= &\lim_{h \to 0} \frac{f(x+h)g(x+h) - f(x)g(x+h) + f(x)g(x+h) - f(x)g(x)}{h} \\
= &\lim_{h \to 0} \left[ \frac{f(x+h) - f(x)}{h} \cdot g(x+h) + f(x) \cdot \frac{g(x+h) - g(x)}{h} \right]
\end{aligned}$$
Poiché $g$ è derivabile, è anche continua (per il teorema precedente), quindi $\lim_{h \to 0} g(x+h) = g(x)$. Passando al limite:
$$= f'(x) \cdot g(x) + f(x) \cdot g'(x)$$

### Regola della Catena (Derivata della Funzione Composta)
Questa è una delle regole più importanti. Se $g$ è derivabile in $x$ e $f$ è derivabile in $g(x)$, allora la funzione composta $F(x) = f(g(x))$ è derivabile in $x$ e vale:
$$F'(x) = D[f(g(x))] = f'(g(x)) \cdot g'(x)$$
In notazione di Leibniz, se $y = f(z)$ e $z = g(x)$, allora $y = f(g(x))$ e:
$$\frac{dy}{dx} = \frac{dy}{dz} \cdot \frac{dz}{dx}$$

### Teorema di Derivazione della Funzione Inversa
Sia $f$ una funzione continua e strettamente monotona su un intervallo $I$, e sia $y=f(x)$. Sia $x = f^{-1}(y)$ la sua funzione inversa. Se $f$ è derivabile in $x \in I$ e $f'(x) \neq 0$, allora la funzione inversa $f^{-1}$ è derivabile in $y = f(x)$ e la sua derivata è:
$$(f^{-1})'(y) = \frac{1}{f'(x)} = \frac{1}{f'(f^{-1}(y))}$$

### Regola del Quoziente
Se $f$ e $g$ sono derivabili in $x$ e $g(x) \neq 0$, allora il loro quoziente $(f/g)$ è derivabile in $x$ e vale:
$$D\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}$$
**Dimostrazione (schizzo)**: Si può dimostrare applicando la regola del prodotto e la regola della catena alla scrittura $f(x) \cdot [g(x)]^{-1}$.

## Derivate delle Funzioni Elementari

### Regola della Potenza: $D[x^k]$
Per ogni $k \in \mathbb{R}$, la derivata di $f(x) = x^k$ (nel suo dominio) è:
$$D[x^k] = kx^{k-1}$$

**Dimostrazione per $n \in \mathbb{N}$ (per Induzione)**:
- **Base ($n=1$):** $D[x^1] = 1 \cdot x^{1-1} = 1$, che è corretto (derivata di $f(x)=x$).
- **Passo Induttivo:** Supponiamo la formula vera per $n$ (ipotesi induttiva $D[x^n] = nx^{n-1}$) e dimostriamola per $n+1$. Scriviamo $x^{n+1} = x^n \cdot x$ e usiamo la regola del prodotto:
$$\begin{aligned}
D[x^{n+1}] &= D[x^n \cdot x] \\
&= D[x^n] \cdot x + x^n \cdot D[x] \\
&= (nx^{n-1}) \cdot x + x^n \cdot 1 \quad \text{(per ip. induttiva e base)} \\
&= nx^n + x^n = (n+1)x^n
\end{aligned}$$
La formula è valida per ogni $n \in \mathbb{N}$.

**Dimostrazione per $k \in \mathbb{R}$ (per $x>0$)**:
Si usa la Regola della Catena scrivendo $x^k = e^{\ln(x^k)} = e^{k \ln(x)}$.
$$D[x^k] = D[e^{k \ln(x)}]$$
Poniamo $f(z) = e^z$ e $g(x) = k \ln(x)$. Avremo $f'(z) = e^z$ e $g'(x) = k \cdot \frac{1}{x}$.
$$D[x^k] = f'(g(x)) \cdot g'(x) = e^{k \ln(x)} \cdot \left( \frac{k}{x} \right) = x^k \cdot \frac{k}{x} = k x^{k-1}$$

### Derivata della Funzione Logaritmica: $D[\log_a(x)]$
(Vedi [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali]])
$$D[\log_a(x)] = \frac{1}{x} \log_a(e)$$
**Dimostrazione**:
$$\begin{aligned}
&\lim_{h \to 0} \frac{\log_a(x+h) - \log_a(x)}{h} = \lim_{h \to 0} \frac{1}{h} \log_a\left(\frac{x+h}{x}\right) \\
= &\lim_{h \to 0} \log_a\left[\left(1 + \frac{h}{x}\right)^{\frac{1}{h}}\right] = \lim_{h \to 0} \log_a\left[\left(1 + \frac{h}{x}\right)^{\frac{x}{h} \cdot \frac{1}{x}}\right] \\
= &\lim_{h \to 0} \frac{1}{x} \log_a\left[\left(1 + \frac{h}{x}\right)^{\frac{x}{h}}\right]
\end{aligned}$$
Poiché la funzione logaritmo è continua, possiamo portare il limite all'interno dell'argomento. Riconoscendo il [[19 - Limiti di Funzioni, Continuità e Teoremi Fondamentali#^16315c|limite notevole di Nepero]]:
$$= \frac{1}{x} \log_a\left[\lim_{h \to 0} \left(1 + \frac{h}{x}\right)^{\frac{x}{h}}\right] = \frac{1}{x} \log_a(e)$$
Un caso notevole si ha per il logaritmo naturale (base $e$):
$$D[\ln(x)] = \frac{1}{x} \log_e(e) = \frac{1}{x}$$

### Derivata della Funzione Esponenziale: $D[e^x]$ e $D[a^x]$
(Vedi [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali]])
- La derivata di $f(x)=e^x$ si ottiene usando il teorema della funzione inversa, sapendo che è l'inversa di $g(y) = \ln(y)$.
  $$D[e^x] = \frac{1}{D[\ln(y)]|_{y=e^x}} = \frac{1}{1/y|_{y=e^x}} = y|_{y=e^x} = e^x$$
  $$D[e^x] = e^x$$
  La funzione $e^x$ è l'unica (a meno di costanti moltiplicative) ad essere uguale alla propria derivata.
- Per la base generica $a > 0, a \neq 1$, si scrive $a^x = e^{\ln(a^x)} = e^{x\ln(a)}$ e si applica la **Regola della Catena**:
  $$D[a^x] = D[e^{x\ln(a)}] = e^{x\ln(a)} \cdot D[x\ln(a)] = a^x \cdot \ln(a)$$
  $$D[a^x] = a^x \ln(a)$$

### Derivate delle Funzioni Trigonometriche
(Vedi [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali]])
- **Derivata di $\sin(x)$**
  $$D[\sin(x)] = \cos(x)$$
  **Dimostrazione**: Usando le formule di addizione del seno e i limiti notevoli $\lim_{h \to 0} \frac{\sin(h)}{h} = 1$ e $\lim_{h \to 0} \frac{\cos(h)-1}{h} = 0$.
  $$\begin{aligned}
  &\lim_{h \to 0} \frac{\sin(x+h) - \sin(x)}{h} = \lim_{h \to 0} \frac{\sin(x)\cos(h) + \cos(x)\sin(h) - \sin(x)}{h} \\
  = &\lim_{h \to 0} \left[ \sin(x) \frac{\cos(h)-1}{h} + \cos(x) \frac{\sin(h)}{h} \right] \\
  = &\sin(x) \cdot 0 + \cos(x) \cdot 1 = \cos(x)
  \end{aligned}$$
- **Derivata di $\cos(x)$**
  $$D[\cos(x)] = -\sin(x)$$
  **Dimostrazione**: Analoga, usando le formule di addizione del coseno.
  $$\begin{aligned}
  &\lim_{h \to 0} \frac{\cos(x+h) - \cos(x)}{h} = \lim_{h \to 0} \frac{\cos(x)\cos(h) - \sin(x)\sin(h) - \cos(x)}{h} \\
  = &\lim_{h \to 0} \left[ \cos(x) \frac{\cos(h)-1}{h} - \sin(x) \frac{\sin(h)}{h} \right] \\
  = &\cos(x) \cdot 0 - \sin(x) \cdot 1 = -\sin(x)
  \end{aligned}$$
- **Derivata di $\tan(x)$**
  $$D[\tan(x)] = \frac{1}{\cos^2(x)} = 1 + \tan^2(x)$$
  **Dimostrazione**: Usando la regola del quoziente per $\tan(x) = \frac{\sin(x)}{\cos(x)}$.
  $$\begin{aligned}
  D\left[\frac{\sin(x)}{\cos(x)}\right] &= \frac{D[\sin(x)]\cos(x) - \sin(x)D[\cos(x)]}{\cos^2(x)} \\
  &= \frac{\cos(x)\cos(x) - \sin(x)(-\sin(x))}{\cos^2(x)} \\
  &= \frac{\cos^2(x) + \sin^2(x)}{\cos^2(x)} = \frac{1}{\cos^2(x)}
  \end{aligned}$$

### Derivate delle Funzioni Trigonometriche Inverse
(Vedi [[10 - Funzioni Trigonometriche Inverse e Loro Applicazioni]])
Applicando il teorema di derivazione della funzione inversa si ottiene:
- **Derivata di $\arcsin(x)$**
  $$D[\arcsin(x)] = \frac{1}{\sqrt{1-x^2}} \quad \text{per } x \in (-1, 1)$$
- **Derivata di $\arccos(x)$**
  $$D[\arccos(x)] = -\frac{1}{\sqrt{1-x^2}} \quad \text{per } x \in (-1, 1)$$
- **Derivata di $\arctan(x)$**
  $$D[\arctan(x)] = \frac{1}{1+x^2} \quad \text{per } x \in \mathbb{R}$$