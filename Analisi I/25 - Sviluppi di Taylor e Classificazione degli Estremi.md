## Introduzione alla Derivazione Successiva dei Polinomi

Un polinomio di grado $n$ è una funzione definita dalla forma:
$$P(x) = a_0 + a_1x + a_2x^2 + \dots + a_nx^n = \sum_{k=0}^{n} a_k x^k$$
Essendo composto da somme e prodotti di funzioni potenza, un polinomio è una funzione indefinitamente derivabile su tutto $\mathbb{R}$. È possibile, quindi, calcolare le sue derivate di ordine superiore.

### Calcolo delle Derivate Successive

Applicando le regole di derivazione, otteniamo:

- **Derivata Prima:**
$$P'(x) = a_1 + 2a_2x + 3a_3x^2 + \dots + na_nx^{n-1}$$
Si osserva che la derivata di un polinomio di grado $n$ è un polinomio di grado $n-1$.

- **Derivata Seconda:**
$$P''(x) = 2a_2 + 3 \cdot 2 a_3x + \dots + n(n-1)a_nx^{n-2}$$

- **Derivata Terza:**
$$P'''(x) = 3 \cdot 2 \cdot 1 a_3 + \dots + n(n-1)(n-2)a_nx^{n-3}$$

Questo processo può essere iterato. La derivata $k$-esima del polinomio è data dalla formula generale:
$$P^{(k)}(x) = k! a_k + (k+1)k \dots 2 a_{k+1}x + \dots + n(n-1)\dots(n-k+1)a_nx^{n-k}$$

### Relazione tra Coefficienti e Derivate

Un'osservazione fondamentale emerge quando valutiamo il polinomio e le sue derivate nel punto $x=0$. Tutti i termini contenenti una potenza di $x$ si annullano, lasciando solo il termine noto.

- $P(0) = a_0$
- $P'(0) = a_1$
- $P''(0) = 2a_2 = 2! a_2$
- $P'''(0) = 3 \cdot 2 \cdot 1 a_3 = 3! a_3$

In generale, per la derivata di ordine $k$, si ottiene:
$$P^{(k)}(0) = k! a_k$$

Da questa relazione, è possibile esprimere ogni coefficiente $a_k$ del polinomio in funzione del valore della derivata $k$-esima calcolata in $0$:
$$a_k = \frac{P^{(k)}(0)}{k!}$$

## La Formula di Maclaurin e Taylor per i Polinomi

### La Formula di Maclaurin

Sostituendo l'espressione dei coefficienti $a_k$ nella forma originale del polinomio, si ottiene la **Formula di Maclaurin per i polinomi**:
$$P(x) = P(0) + P'(0)x + \frac{P''(0)}{2!}x^2 + \frac{P'''(0)}{3!}x^3 + \dots + \frac{P^{(n)}(0)}{n!}x^n$$
In forma compatta, utilizzando la notazione di sommatoria:
$$P(x) = \sum_{k=0}^{n} \frac{P^{(k)}(0)}{k!} x^k$$
Questa formula esprime un polinomio in termini dei valori che esso e le sue derivate assumono nel punto $x_0=0$.

### La Formula di Taylor

La formula può essere generalizzata per un punto iniziale generico $x_0$. Attraverso un cambiamento di variabile $t = x - x_0$, si definisce un nuovo polinomio $Q(t) = P(x_0+t)$. Applicando la formula di Maclaurin a $Q(t)$ e utilizzando la regola di derivazione delle funzioni composte, si trova che $Q^{(k)}(0) = P^{(k)}(x_0)$.

Sostituendo nuovamente $t = x-x_0$, si ottiene la **Formula di Taylor per i polinomi** con punto iniziale $x_0$:
$$P(x) = \sum_{k=0}^{n} \frac{P^{(k)}(x_0)}{k!} (x-x_0)^k$$

## Estensione alle Funzioni: La Formula di Taylor con Resto di Peano

L'idea centrale è estendere questo concetto dai polinomi a funzioni più generali. Data una funzione $f(x)$ derivabile $n$ volte in un punto $x_0$, è possibile approssimarla localmente con un polinomio, detto **Polinomio di Taylor** di grado $n$ centrato in $x_0$:
$$T_n(x; x_0) = f(x_0) + f'(x_0)(x-x_0) + \frac{f''(x_0)}{2!}(x-x_0)^2 + \dots + \frac{f^{(n)}(x_0)}{n!}(x-x_0)^n$$

A differenza dei polinomi, una funzione generica $f(x)$ non coincide esattamente con il suo polinomio di Taylor. L'approssimazione introduce un errore, detto **resto**, indicato con $R_n(x)$:
$$f(x) = T_n(x; x_0) + R_n(x)$$

Un teorema fondamentale (la **Formula di Taylor con il resto di Peano**) stabilisce la natura di questo errore. Esso afferma che il resto è un infinitesimo di ordine superiore a $(x-x_0)^n$ per $x \to x_0$:
$$R_n(x) = o((x-x_0)^n)$$
Ciò significa che:
$$\lim_{x \to x_0} \frac{R_n(x)}{(x-x_0)^n} = 0$$
Di conseguenza, la formula di Taylor per una funzione generica si scrive:
$$f(x) = \sum_{k=0}^{n} \frac{f^{(k)}(x_0)}{k!} (x-x_0)^k + o((x-x_0)^n)$$
Se $x_0 = 0$, la formula prende il nome di **Formula di Maclaurin**.

### Esempio: Sviluppo di Maclaurin di $e^x$

Consideriamo la funzione $f(x) = e^x$. Tutte le sue derivate sono uguali a $e^x$. Calcolandole nel punto $x_0=0$, si ottiene:
$$f^{(k)}(0) = e^0 = 1, \quad \forall k \ge 0$$
Lo sviluppo di Maclaurin di $e^x$ è quindi:
$$e^x = \sum_{k=0}^{n} \frac{1}{k!} x^k + o(x^n) = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots + \frac{x^n}{n!} + o(x^n)$$
Questo sviluppo può essere utilizzato, ad esempio, per ricalcolare limiti notevoli. Per $n=1$, si ha $e^x = 1+x+o(x)$. Da cui $e^x-1 = x+o(x)$. Dividendo per $x$:
$$\frac{e^x-1}{x} = 1 + \frac{o(x)}{x}$$
Passando al limite per $x \to 0$, si ritrova il limite notevole:
$$\lim_{x \to 0} \frac{e^x-1}{x} = 1$$

## Applicazione: Criterio delle Derivate Successive per la Classificazione dei Punti Critici

La formula di Taylor fornisce un potente strumento per determinare la natura dei punti critici di una funzione (punti in cui la derivata prima si annulla).

**Teorema:** Sia $f$ una funzione derivabile $n$ volte in un intorno di $x_0$ e si abbia $f'(x_0) = f''(x_0) = \dots = f^{(n-1)}(x_0) = 0$, con $f^{(n)}(x_0) \neq 0$.

1.  **Se $n$ è pari:**
    - Se $f^{(n)}(x_0) > 0$, allora $x_0$ è un punto di **minimo relativo**.
    - Se $f^{(n)}(x_0) < 0$, allora $x_0$ è un punto di **massimo relativo**.

2.  **Se $n$ è dispari:**
    - Il punto $x_0$ non è né un minimo né un massimo relativo (è un punto di flesso a tangente orizzontale).

### Dimostrazione del Teorema

Nelle ipotesi date, lo sviluppo di Taylor di $f(x)$ centrato in $x_0$ si semplifica notevolmente, poiché i termini con derivate da 1 a $n-1$ sono nulli:
$$f(x) = f(x_0) + \frac{f^{(n)}(x_0)}{n!}(x-x_0)^n + o((x-x_0)^n)$$
Studiamo il segno dell'incremento $\Delta f = f(x) - f(x_0)$ in un intorno di $x_0$:
$$\Delta f = f(x) - f(x_0) = \frac{f^{(n)}(x_0)}{n!}(x-x_0)^n + o((x-x_0)^n)$$
Per analizzare il segno di $\Delta f$ vicino a $x_0$, studiamo il limite del rapporto tra $\Delta f$ e $(x-x_0)^n$:
$$\lim_{x \to x_0} \frac{f(x) - f(x_0)}{(x-x_0)^n} = \lim_{x \to x_0} \left[ \frac{f^{(n)}(x_0)}{n!} + \frac{o((x-x_0)^n)}{(x-x_0)^n} \right]$$
Per la definizione di $o$-piccolo, il secondo termine tende a zero. Dunque:
$$\lim_{x \to x_0} \frac{f(x) - f(x_0)}{(x-x_0)^n} = \frac{f^{(n)}(x_0)}{n!}$$
Per ipotesi, $f^{(n)}(x_0) \neq 0$ e $n! > 0$, quindi il limite è non nullo. Supponiamo (senza perdita di generalità) che $f^{(n)}(x_0) > 0$, e di conseguenza $\frac{f^{(n)}(x_0)}{n!} > 0$.

Per il **Teorema della permanenza del segno**, poiché il limite è positivo, esiste un intorno $I$ di $x_0$ tale che per ogni $x \in I \setminus \{x_0\}$, la funzione (cioè il rapporto) ha lo stesso segno del limite:
$$\frac{f(x) - f(x_0)}{(x-x_0)^n} > 0$$
In questo intorno, il segno dell'incremento $\Delta f = f(x) - f(x_0)$ dipende esclusivamente dal segno del termine $(x-x_0)^n$.

- **Caso 1: $n$ è pari.**
  Il termine $(x-x_0)^n$ è sempre positivo (per $x \neq x_0$). Poiché il rapporto $\frac{\Delta f}{(x-x_0)^n}$ è positivo e il denominatore $(x-x_0)^n$ è positivo, ne consegue che l'incremento $\Delta f = f(x) - f(x_0)$ deve essere positivo.
  Dunque $f(x) > f(x_0)$ per $x \in I \setminus \{x_0\}$. Questa è la definizione di **minimo relativo**.
  (Se $f^{(n)}(x_0) < 0$, il limite è negativo, il rapporto è negativo e $\Delta f < 0$, implicando un **massimo relativo**).

- **Caso 2: $n$ è dispari.**
  Il termine $(x-x_0)^n$ cambia segno nell'intorno di $x_0$:
  - Se $x > x_0$, $(x-x_0)^n > 0$. Poiché il rapporto $\frac{\Delta f}{(x-x_0)^n}$ è positivo, si ha $\Delta f > 0$ (cioè $f(x) > f(x_0)$).
  - Se $x < x_0$, $(x-x_0)^n < 0$. Poiché il rapporto $\frac{\Delta f}{(x-x_0)^n}$ è positivo, si ha $\Delta f < 0$ (cioè $f(x) < f(x_0)$).
  Poiché la funzione assume valori sia maggiori che minori di $f(x_0)$ in qualsiasi intorno di $x_0$, il punto **non è né un minimo né un massimo** (è un punto di flesso a tangente orizzontale).