# L'Integrale di Riemann e l'Integrabilità delle Funzioni Continue

## 1. Definizione e Costruzione dell'Integrale di Riemann

### 1.1 Funzioni Limitate e Partizioni
Per introdurre il concetto di integrale, si consideri una funzione $f: [a, b] \to \mathbb{R}$ limitata. La limitatezza è una condizione essenziale che garantisce l'esistenza dell'estremo superiore e inferiore di $f$ nell'intervallo $[a, b]$ e in ogni suo sottointervallo (vedi [[Analisi I/04 - Estremi Superiori e Inferiori per Insiemi e Funzioni|Estremi Superiori e Inferiori]]).

L'obiettivo è calcolare l'area del *trapezoide* (o rettangoloide) $S$, definito come l'insieme dei punti del piano compresi tra l'asse delle ascisse e il grafico della funzione:
$$S = \{(x, y) \in \mathbb{R}^2 : a \le x \le b, \ 0 \le y \le f(x) \}$$
Poiché il grafico di $f(x)$ non è necessariamente rettilineo, si approssima l'area mediante rettangoli.

Si definisce **partizione** $P$ dell'intervallo $[a, b]$ un insieme finito e ordinato di $n+1$ punti:
$$P = \{x_0, x_1, \dots, x_n\} \quad \text{con} \quad a = x_0 < x_1 < \dots < x_n = b$$
Questa partizione suddivide il dominio in $n$ sottointervalli $I_k = [x_{k-1}, x_k]$.

### 1.2 Somme Integrali Inferiori e Superiori
Per ogni sottointervallo $I_k$, data la limitatezza della funzione, si definiscono gli estremi locali:
- **Estremo inferiore:** $m_k = \inf \{f(x) : x \in [x_{k-1}, x_k]\}$
- **Estremo superiore:** $M_k = \sup \{f(x) : x \in [x_{k-1}, x_k]\}$

Si costruiscono quindi le somme integrali relative alla partizione $P$:
- **Somma integrale inferiore ($s(P)$):** Rappresenta l'area del **plurirettangolo inscritto** nel trapezoide (approssimazione per difetto).
  $$s(P) = \sum_{k=1}^{n} m_k (x_k - x_{k-1})$$
- **Somma integrale superiore ($S(P)$):** Rappresenta l'area del **plurirettangolo circoscritto** al trapezoide (approssimazione per eccesso).
  $$S(P) = \sum_{k=1}^{n} M_k (x_k - x_{k-1})$$

### 1.3 Proprietà di Separazione e Definizione di Integrale
Valgono le seguenti proprietà fondamentali:
1.  **Confronto su stessa partizione:** Per ogni partizione $P$, si ha sempre $s(P) \le S(P)$ poiché $m_k \le M_k$.
2.  **Confronto tra partizioni diverse:** Considerando due partizioni qualsiasi $P$ e $Q$, la somma inferiore è sempre minore o uguale alla somma superiore: $s(P) \le S(Q)$ (vedi [[Analisi I/27 - Resto di Lagrange e Integrale di Riemann#4.2 Proprietà Fondamentali|Proprietà Fondamentali]]).

Di conseguenza, l'insieme delle somme inferiori $A = \{s(P)\}_{P}$ e l'insieme delle somme superiori $B = \{S(Q)\}_{Q}$ sono **insiemi separati**.
Per l'**[[Analisi I/03 - Insiemi Numerici, Completezza e Estremo Superiore#Assioma di Completezza|Assioma di Completezza]]**, esiste almeno un numero reale $c$ (elemento di separazione) tale che:
$$\forall s(P) \in A, \forall S(Q) \in B \implies s(P) \le c \le S(Q)$$

Si definiscono l'integrale inferiore e superiore come:
- $s(f) = \sup A = \sup_{P} \{s(P)\}$
- $S(f) = \inf B = \inf_{Q} \{S(Q)\}$

Se l'elemento di separazione è **unico**, ovvero se $s(f) = S(f)$, la funzione si dice **integrabile secondo Riemann** in $[a, b]$ e tale valore comune è l'integrale definito:
$$\int_a^b f(x) dx = c$$

## 2. Il Criterio di Integrabilità di Riemann

Il seguente criterio fornisce una condizione necessaria e sufficiente per l'integrabilità, basata sulla possibilità di rendere arbitrariamente piccola la differenza tra somme superiori e inferiori.

**Teorema (Criterio di Riemann):**
Una funzione $f$ limitata in $[a, b]$ è integrabile secondo Riemann se e solo se:
$$\forall \epsilon > 0, \exists P \text{ partizione di } [a, b] \text{ tale che } S(P) - s(P) < \epsilon$$

### Dimostrazione

**($\implies$) Condizione Necessaria:**
Sia $f$ integrabile secondo Riemann. Allora $\sup A = \inf B = I$ (dove $I$ è il valore dell'integrale). Per le proprietà caratteristiche dell'estremo superiore e inferiore:
1.  Poiché $I = \sup A$, $\forall \epsilon > 0, \exists P_1$ tale che $s(P_1) > I - \epsilon/2$.
2.  Poiché $I = \inf B$, $\forall \epsilon > 0, \exists P_2$ tale che $S(P_2) < I + \epsilon/2$.

Consideriamo la partizione unione $R = P_1 \cup P_2$, che è un **raffinamento** sia di $P_1$ che di $P_2$. Valgono quindi le relazioni di monotonicità delle somme (raffinando la partizione, la somma inferiore cresce e la superiore decresce):
$$s(P_1) \le s(R) \le S(R) \le S(P_2)$$
Combinando le disuguaglianze otteniamo:
$$I - \epsilon/2 < s(P_1) \le s(R) \le S(R) \le S(P_2) < I + \epsilon/2$$
Sottraendo le disuguaglianze esterne si ottiene la tesi per la partizione $R$:
$$S(R) - s(R) < (I + \epsilon/2) - (I - \epsilon/2) = \epsilon$$

**($\Longleftarrow$) Condizione Sufficiente:**
Supponiamo che $\forall \epsilon > 0, \exists P$ tale che $S(P) - s(P) < \epsilon$.
Sappiamo che per ogni partizione $P$, vale sempre la catena di disuguaglianze:
$$s(P) \le s(f) \le S(f) \le S(P)$$
Sottraendo i termini centrali (che sono costanti rispetto a $P$) e osservando che sono compresi tra quelli esterni:
$$0 \le S(f) - s(f) \le S(P) - s(P) < \epsilon$$
Poiché la differenza $S(f) - s(f)$ è un numero reale non negativo ed è minore di ogni $\epsilon > 0$ arbitrario, deve essere necessariamente nulla. Quindi $S(f) = s(f)$, il che implica che $f$ è integrabile.

## 3. Integrabilità delle Funzioni Continue

La continuità è una condizione sufficiente (ma non necessaria) per l'integrabilità.

**Teorema:** Se una funzione $f$ è continua nell'intervallo chiuso e limitato $[a, b]$, allora $f$ è integrabile secondo Riemann in $[a, b]$.

### 3.1 Continuità Uniforme e Teorema di Cantor
Per la dimostrazione è fondamentale il concetto di **uniforme continuità**. Mentre la continuità puntuale dipende dal punto $x_0$, l'uniforme continuità garantisce una stima globale.

> [!info] Definizione di Uniforme Continuità
> Una funzione $f$ è uniformemente continua in $I$ se:
> $\forall \epsilon > 0, \exists \delta > 0$ (dipendente solo da $\epsilon$) tale che $\forall x, x' \in I, |x - x'| < \delta \implies |f(x) - f(x')| < \epsilon$.

Il **Teorema di Cantor** (o Heine-Cantor) afferma che:
> Se una funzione è continua su un intervallo **chiuso e limitato** (un insieme compatto), allora è **uniformemente continua** su tale insieme.
> (Vedi [[Analisi I/18 - Limiti, Continuità e Teoremi sulle Funzioni Continue#3. Funzioni Continue|Funzioni Continue]])

### 3.2 Dimostrazione del Teorema di Integrabilità
Vogliamo dimostrare l'integrabilità utilizzando il **Criterio di Riemann**.
Fissiamo un $\epsilon > 0$ arbitrario.
1.  Poiché $f$ è continua su $[a, b]$ (chiuso e limitato), per il Teorema di Cantor è **uniformemente continua**.
2.  Scegliamo $\epsilon' = \frac{\epsilon}{b-a}$. Per la definizione di uniforme continuità, esiste un $\delta > 0$ tale che:
    $$|x - x'| < \delta \implies |f(x) - f(x')| < \frac{\epsilon}{b-a}$$
3.  Costruiamo una partizione $P = \{x_0, \dots, x_n\}$ tale che l'ampiezza di ogni sottointervallo sia minore di $\delta$ (ovvero $x_k - x_{k-1} < \delta$ per ogni $k$).
4.  In ogni intervallo chiuso $[x_{k-1}, x_k]$, essendo $f$ continua, per il **[[Analisi I/18 - Limiti, Continuità e Teoremi sulle Funzioni Continue#Teoremi Fondamentali sulle Funzioni Continue|Teorema di Weierstrass]]**, la funzione assume un valore massimo $M_k$ e un valore minimo $m_k$.
5.  Esistono quindi punti $x'_k, x''_k \in [x_{k-1}, x_k]$ tali che $f(x'_k) = M_k$ e $f(x''_k) = m_k$. Poiché la distanza tra questi punti è minore di $\delta$, vale:
    $$M_k - m_k = f(x'_k) - f(x''_k) < \frac{\epsilon}{b-a}$$

Valutiamo ora la differenza tra somma superiore e inferiore per questa partizione $P$:
$$S(P) - s(P) = \sum_{k=1}^{n} (M_k - m_k)(x_k - x_{k-1})$$
Sostituendo la maggiorazione trovata per $(M_k - m_k)$:
$$S(P) - s(P) < \sum_{k=1}^{n} \frac{\epsilon}{b-a} (x_k - x_{k-1})$$
Poiché il fattore $\frac{\epsilon}{b-a}$ è costante, lo portiamo fuori dalla sommatoria. La somma delle lunghezze degli intervalli $(x_k - x_{k-1})$ è esattamente la lunghezza totale dell'intervallo $(b-a)$:
$$S(P) - s(P) < \frac{\epsilon}{b-a} \cdot \underbrace{\sum_{k=1}^{n} (x_k - x_{k-1})}_{b-a} = \frac{\epsilon}{b-a} \cdot (b-a) = \epsilon$$
Abbiamo dimostrato che per ogni $\epsilon$ esiste una partizione che soddisfa la condizione $S(P) - s(P) < \epsilon$. Dunque, $f$ è integrabile.

## 4. Proprietà degli Integrali Definiti

Dalle definizioni precedenti derivano importanti proprietà algebriche dell'integrale.

### 4.1 Addittività rispetto all'intervallo
Se $f$ è integrabile in un intervallo e $a, b, c$ sono tre punti dell'intervallo, vale la relazione:
$$\int_{a}^{b}f(x)dx = \int_{a}^{c}f(x)dx + \int_{c}^{b}f(x)dx$$

### 4.2 Linearità dell'Integrale
Se $f$ e $g$ sono funzioni integrabili in $[a, b]$ e $\alpha, \beta \in \mathbb{R}$ sono costanti reali, allora la combinazione lineare $\alpha f(x) + \beta g(x)$ è integrabile e vale:
$$\int_{a}^{b} [\alpha f(x) + \beta g(x)] dx = \alpha \int_{a}^{b} f(x)dx + \beta \int_{a}^{b} g(x)dx$$