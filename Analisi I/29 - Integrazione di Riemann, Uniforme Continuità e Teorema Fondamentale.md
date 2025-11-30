# Integrazione di Riemann e Teoremi Fondamentali

## Definizione dell'Integrale di Riemann
Collegamento consigliato: [[28 - Integrale di Riemann, Definizione, Criterio e Funzioni Continue]]

L'introduzione all'integrazione secondo Riemann si basa sul concetto di approssimazione dell'area di un **rettangoloide**. Data una funzione $f(x)$ limitata e positiva definita su un intervallo $[a, b]$, il rettangoloide $S$ è la regione di piano delimitata dall'asse $x$, dalle rette $x=a$ e $x=b$, e dal grafico della funzione $y=f(x)$.

Poiché la frontiera superiore è curvilinea, si approssima l'area mediante **plurirettangoli**. Si introduce una **partizione** $P$ dell'intervallo $[a, b]$, ovvero un insieme ordinato di $n+1$ punti:
$$a = x_0 < x_1 < x_2 < \dots < x_n = b$$
Questa partizione suddivide il dominio in $n$ sottointervalli $[x_{k-1}, x_k]$.

### Somme Integrali Inferiori e Superiori
Per ogni intervallo $[x_{k-1}, x_k]$, si definiscono:
* **Estremo inferiore:** $m_k = \inf \{f(x) : x \in [x_{k-1}, x_k]\}$
* **Estremo superiore:** $M_k = \sup \{f(x) : x \in [x_{k-1}, x_k]\}$

Si costruiscono quindi due quantità fondamentali:
1. **Somma integrale inferiore ($s(P)$):** Approssimazione per difetto dell'area.
   $$s(P) = \sum_{k=1}^n m_k (x_k - x_{k-1})$$
2. **Somma integrale superiore ($S(P)$):** Approssimazione per eccesso dell'area.
   $$S(P) = \sum_{k=1}^n M_k (x_k - x_{k-1})$$

**Proprietà fondamentali:**
Vale sempre la relazione $s(P) \le S(P)$ per una stessa partizione. Inoltre, considerate due partizioni qualsiasi $P$ e $Q$, si dimostra che ogni somma inferiore è sempre minore o uguale di ogni somma superiore ($s(P) \le S(Q)$). Questo implica che l'insieme delle somme inferiori $A$ e l'insieme delle somme superiori $B$ sono separati:
$$\sup(A) \le \inf(B)$$

### Definizione di Integrabilità
Per l'assioma di completezza dei numeri reali (vedi [[03 - Insiemi Numerici, Completezza e Estremo Superiore]]), esiste almeno un elemento di separazione tra $A$ e $B$. 
Se tale elemento è **unico**, la funzione si dice **integrabile secondo Riemann** e tale valore è definito come l'integrale definito:
$$\int_a^b f(x) dx$$
In termini di estremi superiori e inferiori, la condizione di integrabilità si traduce in:
$$\sup(A) = \inf(B) = \int_a^b f(x) dx$$

### Criterio di Riemann
Una funzione limitata è integrabile se e soltanto se:
$$\forall \epsilon > 0, \exists P \text{ t.c. } S(P) - s(P) < \epsilon$$
Questo criterio fornisce una condizione necessaria e sufficiente per l'integrabilità senza dover calcolare il valore dell'integrale, basandosi sulla minimizzazione dell'errore tra le stime per eccesso e per difetto.

---

## Continuità Uniforme e Funzioni Lipschitziane
Collegamento consigliato: [[19 - Limiti di Funzioni, Continuità e Teoremi Fondamentali]]

### Continuità vs Continuità Uniforme
La definizione classica di continuità in un punto $x_0$ afferma che $\forall \epsilon > 0, \exists \delta(\epsilon, x_0) > 0$ tale che se $|x - x_0| < \delta$, allora $|f(x) - f(x_0)| < \epsilon$. Qui $\delta$ dipende sia da $\epsilon$ che dal punto $x_0$.

L'**uniforme continuità** è una proprietà globale più forte: $\delta$ dipende **soltanto** da $\epsilon$ e non dal punto $x$ scelto nell'intervallo.
$$\forall \epsilon > 0, \exists \delta(\epsilon) > 0 : \forall x, x' \in D, |x - x'| < \delta \implies |f(x) - f(x')| < \epsilon$$

Il **Teorema di Heine-Cantor** stabilisce che se una funzione è continua in un intervallo chiuso e limitato $[a, b]$ (compatto), allora è uniformemente continua in tale intervallo.

### Funzioni Lipschitziane
Una funzione $f$ si dice **lipschitziana** su un intervallo $I$ se esiste una costante $L > 0$ (costante di Lipschitz) tale che:
$$|f(x) - f(x')| \le L |x - x'|, \quad \forall x, x' \in I$$
Geometricamente, questo significa che la pendenza della retta secante passante per due punti qualsiasi del grafico è limitata da $L$.

**Relazioni tra le proprietà:**
1. **Lipschitziana $\implies$ Uniformemente Continua:** Si dimostra ponendo $\delta = \epsilon / L$. Infatti, se $|x - x'| < \delta$, allora:
   $$|f(x) - f(x')| \le L |x-x'| < L \cdot \frac{\epsilon}{L} = \epsilon$$
2. **Uniformemente Continua $\not\implies$ Lipschitziana:** Esempio classico: $f(x) = \sqrt{x}$ in $[0, 1]$.
   * È uniformemente continua per il teorema di Heine-Cantor (è continua su un chiuso e limitato).
   * **Non è lipschitziana**. Se lo fosse, il rapporto incrementale dovrebbe essere limitato ($\le L$). Tuttavia, vicino a $0$, la derivata $f'(x) = \frac{1}{2\sqrt{x}}$ tende a $+\infty$. Essendo la derivata illimitata, la funzione non può essere lipschitziana.

**Caratterizzazione tramite Derivata (Teorema di Lagrange):**
Vedi anche: [[22 - Teoremi Fondamentali del Calcolo Differenziale e Applicazioni]]
Una funzione derivabile in un intervallo è lipschitziana se e soltanto se la sua derivata prima è limitata.
$$|f'(x)| \le L \iff f \text{ è L-Lipschitziana}$$

---

## Integrabilità delle Funzioni Continue

Si dimostra che **ogni funzione continua in un intervallo chiuso e limitato $[a, b]$ è integrabile secondo Riemann**.

**Dimostrazione:**
1. Poiché $f$ è continua su un compatto, per il Teorema di Heine-Cantor è uniformemente continua.
2. Fissato $\epsilon > 0$, esiste $\delta$ tale che per ogni coppia di punti a distanza minore di $\delta$, l'oscillazione della funzione ($|f(x)-f(x')|$) è minore di $\frac{\epsilon}{b-a}$.
3. Scegliendo una partizione $P$ con ampiezza minore di $\delta$, in ogni sottointervallo si ha $M_k - m_k < \frac{\epsilon}{b-a}$.
4. Calcolando la differenza tra le somme:
   $$S(P) - s(P) = \sum_{k=1}^n (M_k - m_k)(x_k - x_{k-1}) < \frac{\epsilon}{b-a} \sum_{k=1}^n (x_k - x_{k-1})$$
   Essendo la somma delle ampiezze pari alla lunghezza dell'intervallo totale $(b-a)$:
   $$S(P) - s(P) < \frac{\epsilon}{b-a} \cdot (b-a) = \epsilon$$
La condizione del criterio di Riemann è soddisfatta.

---

## Teoremi della Media Integrale
Collegamento consigliato: [[27 - Resto di Lagrange e Integrale di Riemann]]

### Primo Teorema della Media (per funzioni limitate)
Se $f$ è limitata in $[a, b]$ con estremo inferiore $m$ e superiore $M$, allora:
$$m(b-a) \le \int_a^b f(x) dx \le M(b-a)$$
Geometricamente, l'area del rettangoloide è compresa tra l'area del rettangolo "minimo" (base $b-a$, altezza $m$) e quella del rettangolo "massimo" (altezza $M$).

### Secondo Teorema della Media (per funzioni continue)
Se $f$ è continua in $[a, b]$, esiste almeno un punto $c \in [a, b]$ tale che:
$$\int_a^b f(x) dx = f(c)(b-a)$$
O equivalentemente, il valor medio integrale $f(c)$ è assunto dalla funzione:
$$f(c) = \frac{1}{b-a}\int_a^b f(x) dx$$

**Dimostrazione:**
Dal primo teorema, dividendo per $(b-a)$, si ottiene che il valore medio integrale $y_0$ è compreso tra $m$ e $M$. Essendo $f$ continua, per il Teorema di Weierstrass $m$ e $M$ sono rispettivamente il minimo e il massimo assoluto. Per il **Teorema dei Valori Intermedi**, la funzione assume tutti i valori compresi tra minimo e massimo; pertanto, deve esistere un $c$ tale che $f(c) = y_0$.

---

## Il Teorema Fondamentale del Calcolo Integrale

Si definisce la **Funzione Integrale** $F(x)$ per una funzione continua $f$ in $[a, b]$:
$$F(x) = \int_a^x f(t) dt$$

**Enunciato (Primo Teorema Fondamentale):**
Se $f$ è continua in $[a, b]$, allora la funzione integrale $F(x)$ è derivabile in $(a, b)$ e la sua derivata coincide con la funzione integranda:
$$F'(x) = f(x)$$

**Dimostrazione:**
Si considera il rapporto incrementale di $F(x)$:
$$\frac{F(x+h) - F(x)}{h} = \frac{1}{h} \left( \int_a^{x+h} f(t) dt - \int_a^x f(t) dt \right)$$
Per l'addittività dell'integrale, la differenza degli integrali è l'integrale da $x$ a $x+h$:
$$= \frac{1}{h} \int_x^{x+h} f(t) dt$$
Applicando il Secondo Teorema della Media all'intervallo $[x, x+h]$, esiste un punto $c_h \in [x, x+h]$ tale che l'integrale vale $f(c_h) \cdot h$. Sostituendo:
$$\frac{1}{h} (f(c_h) \cdot h) = f(c_h)$$
Passando al limite per $h \to 0$, il punto $c_h$ viene "schiacciato" verso $x$ ($c_h \to x$). Per la continuità di $f$, $\lim_{h \to 0} f(c_h) = f(x)$. Dunque $F'(x) = f(x)$.

---

## Applicazione: Calcolo di Limiti con Taylor
Collegamento consigliato: [[26 - Teorema di De L'Hopital e Formula di Taylor con Resto di Peano]]

Per risolvere forme indeterminate nei limiti, gli sviluppi di Taylor permettono di stimare l'ordine di infinitesimo di numeratore e denominatore. 

**Esempio Pratico (dagli appunti di lezione):**
Vogliamo calcolare l'ordine di infinitesimo del seguente denominatore per $x \to 0$:
$$D(x) = x^2(e^{2x^2}-1)$$
E confrontarlo con un numeratore che coinvolge logaritmi e coseni.

1. **Analisi del Denominatore:**
   Sviluppiamo $e^t = 1 + t + o(t)$. Ponendo $t = 2x^2$:
   $$e^{2x^2} = 1 + 2x^2 + \frac{(2x^2)^2}{2} + o(x^4) = 1 + 2x^2 + 2x^4 + o(x^4)$$
   Quindi:
   $$e^{2x^2} - 1 = 2x^2 + o(x^2)$$
   Sostituendo nel denominatore:
   $$D(x) = x^2(2x^2 + o(x^2)) = 2x^4 + o(x^4)$$
   Il denominatore è un infinitesimo di ordine 4. Questo ci dice che **dobbiamo sviluppare anche il numeratore fino all'ordine 4**.

2. **Analisi di un Numeratore complesso:**
   Consideriamo il termine $\log(\cos x)$.
   * Sviluppo di $\cos x$ all'ordine 4:
     $$\cos x = 1 - \frac{x^2}{2} + \frac{x^4}{24} + o(x^4)$$
   * Sviluppo di $\log(1+y)$ con $y = \cos x - 1$:
     $$\log(1+y) = y - \frac{y^2}{2} + o(y^2)$$
   * Sostituzione (algebra degli o-piccolo):
     $$y = -\frac{x^2}{2} + \frac{x^4}{24}$$
     $$y^2 = \left(-\frac{x^2}{2}\right)^2 = \frac{x^4}{4} \quad (\text{trascurando potenze } > 4)$$
     $$\log(\cos x) \approx \left(-\frac{x^2}{2} + \frac{x^4}{24}\right) - \frac{1}{2}\left(\frac{x^4}{4}\right)$$
     $$= -\frac{x^2}{2} + \left(\frac{1}{24} - \frac{1}{8}\right)x^4 = -\frac{x^2}{2} - \frac{1}{12}x^4 + o(x^4)$$

Questa tecnica permette di trasformare limiti complessi in semplici rapporti tra coefficienti di polinomi.