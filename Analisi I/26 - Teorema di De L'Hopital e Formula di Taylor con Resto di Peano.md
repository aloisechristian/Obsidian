# Il Teorema di De L'Hôpital e la Formula di Taylor

## 1. Il Teorema di De L'Hôpital

### 1.1 Enunciato del Teorema
Il **Teorema di De L'Hôpital** è uno strumento fondamentale per la risoluzione di forme indeterminate nel calcolo dei [[Analisi I/19 - Limiti di Funzioni, Continuità e Teoremi Fondamentali|Limiti]]. Consideriamo due funzioni $f$ e $g$ derivabili in un intorno $I$ di un punto $x_0$ (escluso al più $x_0$ stesso).

Affinché il teorema sia applicabile, devono essere soddisfatte le seguenti ipotesi:
1.  Il limite del rapporto si presenta in una forma indeterminata:
    $$\lim_{x \to x_0} \frac{f(x)}{g(x)} = \frac{0}{0} \quad \text{oppure} \quad \frac{\infty}{\infty}$$
2.  La derivata del denominatore non si annulla nell'intorno (eccetto eventualmente in $x_0$):
    $$g'(x) \neq 0 \quad \forall x \in I \setminus \{x_0\}$$
3.  Esiste il limite del rapporto delle loro derivate:
    $$\lim_{x \to x_0} \frac{f'(x)}{g'(x)} = L \quad (\text{con } L \in \mathbb{R} \cup \{\pm \infty\})$$

Se queste condizioni sono verificate, allora vale la tesi:
$$\lim_{x \to x_0} \frac{f(x)}{g(x)} = \lim_{x \to x_0} \frac{f'(x)}{g'(x)}$$

**Note Importanti:**
* Il teorema è applicabile anche per i limiti destro ($x \to x_0^+$) e sinistro ($x \to x_0^-$).
* Il punto $x_0$ può essere un numero reale finito, oppure $\pm \infty$.
* L'utilità del teorema risiede nel fatto che spesso, derivando numeratore e denominatore (vedi [[Analisi I/21 - Derivate e Regole di Derivazione|Regole di Derivazione]]), la forma indeterminata si risolve.

### 1.2 Dimostrazione (Caso Particolare $C^1$)
Proponiamo la dimostrazione nel caso semplificato in cui $f$ e $g$ siano funzioni di classe $C^1$ in un intorno di $x_0$.
> [!INFO] Nota sulla Generalizzazione
> La dimostrazione del caso generale (senza l'ipotesi di continuità delle derivate) fa uso del **Teorema di Cauchy**. Puoi approfondire questo aspetto nella nota: [[Analisi I/22 - Teoremi Fondamentali del Calcolo Differenziale e Applicazioni|Teoremi Fondamentali del Calcolo Differenziale]].

**Ipotesi Semplificate:**
1.  $\lim_{x \to x_0} f(x) = 0$ e $\lim_{x \to x_0} g(x) = 0$ (Forma $0/0$).
2.  $f, g \in C^1$ (funzioni continue con derivata continua).

Dalla continuità delle funzioni e dalle ipotesi sui limiti, segue che definiamo (o ridefiniamo per continuità):
$$f(x_0) = 0 \quad \text{e} \quad g(x_0) = 0$$

Possiamo riscrivere il rapporto $f(x)/g(x)$ sottraendo i valori nulli $f(x_0)$ e $g(x_0)$ e dividendo numeratore e denominatore per $(x - x_0)$:
$$\frac{f(x)}{g(x)} = \frac{f(x) - f(x_0)}{g(x) - g(x_0)} = \frac{\frac{f(x) - f(x_0)}{x - x_0}}{\frac{g(x) - g(x_0)}{x - x_0}}$$
Passando al limite per $x \to x_0$, i termini al numeratore e al denominatore rappresentano i rapporti incrementali rispettivamente di $f$ e $g$ centrati in $x_0$. Poiché le funzioni sono derivabili, questi limiti convergono alle derivate valutate nel punto:
$$\lim_{x \to x_0} \frac{\frac{f(x) - f(x_0)}{x - x_0}}{\frac{g(x) - g(x_0)}{x - x_0}} = \frac{f'(x_0)}{g'(x_0)}$$
Sfruttando l'ipotesi che le derivate $f'$ e $g'$ siano **continue** (classe $C^1$), possiamo affermare che:
$$f'(x_0) = \lim_{x \to x_0} f'(x) \quad \text{e} \quad g'(x_0) = \lim_{x \to x_0} g'(x)$$
Sostituendo, otteniamo la tesi:
$$\lim_{x \to x_0} \frac{f(x)}{g(x)} = \lim_{x \to x_0} \frac{f'(x)}{g'(x)}$$

---

## 2. Applicazioni ed Esempi

### Esempio 1: Confronto con i Limiti Notevoli
Calcolare il limite:
$$\lim_{x \to 0} \frac{e^x - 1}{\sin(2x)}$$
**Metodo classico:** Utilizzando i limiti notevoli $\frac{e^x-1}{x} \to 1$ e $\frac{\sin(2x)}{2x} \to 1$, si ottiene $1/2$.
**Metodo De L'Hôpital:** Forma $0/0$. Deriviamo numeratore e denominatore:
* $D[e^x - 1] = e^x$
* $D[\sin(2x)] = 2\cos(2x)$ (regola della catena)
$$\lim_{x \to 0} \frac{e^x}{2\cos(2x)} = \frac{e^0}{2\cos(0)} = \frac{1}{2}$$

### Esempio 2: Forma Indeterminata $0 \cdot \infty$
Calcolare il limite:
$$\lim_{x \to 0^+} x \ln(x)$$
Questa è una forma $0 \cdot (-\infty)$. Per applicare De L'Hôpital, trasformiamo il prodotto in un rapporto per ottenere la forma $\infty / \infty$:
$$\lim_{x \to 0^+} \frac{\ln(x)}{1/x}$$
Deriviamo:
* $D[\ln(x)] = 1/x$
* $D[1/x] = -1/x^2$
$$\lim_{x \to 0^+} \frac{1/x}{-1/x^2} = \lim_{x \to 0^+} \left( \frac{1}{x} \cdot (-x^2) \right) = \lim_{x \to 0^+} (-x) = 0$$

### Esempio 3: Parametri Reali
Calcolare il limite per $x \to 1$ (forma $0/0$):
$$\lim_{x \to 1} \frac{x^\alpha - 1}{x \ln(x)}$$
Applicando De L'Hôpital:
$$\lim_{x \to 1} \frac{\alpha x^{\alpha-1}}{1 \cdot \ln(x) + x \cdot \frac{1}{x}} = \lim_{x \to 1} \frac{\alpha x^{\alpha-1}}{\ln(x) + 1}$$
Sostituendo $x=1$, il denominatore tende a $0+1=1$, quindi il limite è $\alpha$.

---

## 3. Introduzione ai Polinomi di Taylor

In alcuni casi, l'applicazione ripetuta di De L'Hôpital può risultare laboriosa. Un approccio alternativo e generalizzato è l'uso della **Formula di Taylor**.
Per approfondire la teoria e la classificazione degli estremi tramite Taylor, vedi: [[Analisi I/25 - Sviluppi di Taylor e Classificazione degli Estremi|Sviluppi di Taylor]].

### 3.1 Definizione
Il Polinomio di Taylor di grado $n$, $P_n(x)$, centrato in $x_0$, approssima la funzione $f(x)$ tramite le sue derivate:
$$P_n(x) = \sum_{k=0}^n \frac{f^{(k)}(x_0)}{k!} (x - x_0)^k$$

### 3.2 Formula di Mac Laurin (Taylor centrato in $x_0=0$)
Quando $x_0=0$, la formula prende il nome di Mac Laurin. Ecco alcuni sviluppi fondamentali (con Resto di Peano $o(x^n)$):

* **Esponenziale:**
    $$e^x = 1 + x + \frac{x^2}{2} + \frac{x^3}{3!} + \dots + \frac{x^n}{n!} + o(x^n)$$
* **Logaritmo:**
    $$\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} + \dots + (-1)^{n+1}\frac{x^n}{n} + o(x^n)$$
* **Seno:**
    $$\sin(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!} + \dots + (-1)^k \frac{x^{2k+1}}{(2k+1)!} + o(x^{2k+1})$$

### 3.3 Applicazione al Calcolo dei Limiti
Consideriamo il limite:
$$\lim_{x \to 0} \frac{e^x - 1 - x}{x^2}$$
Utilizziamo lo sviluppo di Mac Laurin di $e^x$ arrestato all'ordine 2:
$$e^x = 1 + x + \frac{x^2}{2} + o(x^2)$$
Sostituendo nel limite:
$$\lim_{x \to 0} \frac{\left( 1 + x + \frac{x^2}{2} + o(x^2) \right) - 1 - x}{x^2}$$
Semplificando i termini:
$$\lim_{x \to 0} \frac{\frac{x^2}{2} + o(x^2)}{x^2} = \lim_{x \to 0} \left( \frac{1}{2} + \frac{o(x^2)}{x^2} \right) = \frac{1}{2}$$
Ricorda che per definizione di o-piccolo (vedi [[Analisi I/20 - Infinitesimi, Principio di Sostituzione e Derivata|Infinitesimi]]), $\lim_{x \to 0} \frac{o(x^2)}{x^2} = 0$.