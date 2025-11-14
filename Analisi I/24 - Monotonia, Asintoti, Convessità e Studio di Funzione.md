## Riepilogo dei Criteri di Monotonia

### Criterio di Monotonia
Il criterio di monotonia stabilisce una connessione fondamentale tra il segno della derivata prima di una funzione e il suo andamento (crescente o decrescente). Data una funzione $f(x)$ continua in un intervallo chiuso e limitato $[a, b]$ e derivabile nell'intervallo aperto $(a, b)$, valgono le seguenti equivalenze:

* La funzione $f(x)$ è **crescente** in $[a, b]$ se e solo se la sua derivata prima è non negativa, ovvero $f'(x) \ge 0$ per ogni $x \in (a, b)$.
* La funzione $f(x)$ è **decrescente** in $[a, b]$ se e solo se la sua derivata prima è non positiva, ovvero $f'(x) \le 0$ per ogni $x \in (a, b)$.

Questo criterio è uno strumento essenziale per determinare gli intervalli di monotonia di una funzione attraverso lo studio del segno della sua derivata prima.

Una conseguenza diretta è la caratterizzazione delle funzioni costanti: una funzione è **costante** in un intervallo se e solo se la sua derivata è identicamente nulla in quell'intervallo.

> [!info] Nota di Collegamento
> La dimostrazione di questo criterio è un'applicazione diretta del [[22 - Teoremi Fondamentali del Calcolo Differenziale e Applicazioni|Teorema di Lagrange]]. Applicando Lagrange all'intervallo $[x_1, x_2] \subset [a, b]$, si ha $f(x_2) - f(x_1) = f'(c)(x_2 - x_1)$. Il segno di $f'(c)$ determina se $f(x_2) \ge f(x_1)$ (crescente) o $f(x_2) \le f(x_1)$ (decrescente).

### Criterio di Stretta Monotonia
Per la stretta monotonia, il criterio è leggermente più specifico:

* Se $f'(x) \ge 0$ in $(a, b)$ e la derivata non si annulla identicamente in nessun sottointervallo di $(a, b)$ (cioè, si annulla al più in punti isolati), allora la funzione $f(x)$ è **strettamente crescente**.

Un esempio classico è la funzione $f(x) = x^3$. La sua derivata è $f'(x) = 3x^2$, che è sempre $\ge 0$. Si annulla solo nel punto $x=0$, ma non in un intervallo. Pertanto, $f(x) = x^3$ è una funzione strettamente crescente su tutto $\mathbb{R}$.

## Concavità e Convessità

### Definizione Geometrica
Una funzione $f(x)$ si dice **convessa** in un intervallo $(a, b)$ se, per ogni punto $x_0 \in (a, b)$, il grafico della funzione si trova al di sopra della retta tangente al grafico nel punto $(x_0, f(x_0))$. Matematicamente, questo si traduce nella seguente disuguaglianza:
$$f(x) \ge f(x_0) + f'(x_0)(x - x_0) \quad \forall x, x_0 \in (a, b)$$
Viceversa, una funzione si dice **concava** se il suo grafico si trova al di sotto della retta tangente:
$$f(x) \le f(x_0) + f'(x_0)(x - x_0) \quad \forall x, x_0 \in (a, b)$$

### Criterio della Derivata Seconda
Per funzioni derivabili due volte, esiste un criterio analitico per determinare la convessità basato sulla derivata seconda. Sussiste la seguente catena di equivalenze:

1.  $f$ è **convessa**.
2.  $f'$ (la derivata prima) è **crescente**.
3.  $f''$ (la derivata seconda) è $\ge 0$.

L'equivalenza tra (2) e (3) è una diretta applicazione del **Criterio di Monotonia** (visto sopra) alla funzione $g(x) = f'(x)$.
L'equivalenza tra (1) e (2) si dimostra (ad esempio, per $1 \implies 2$) applicando il Teorema di Lagrange e manipolando algebricamente la definizione di convessità.

> [!info] Nota di Collegamento
> Questo argomento è trattato in dettaglio nella nota [[23 - Applicazioni delle Derivate per Estremi, Monotonia e Convessità]].

## Studio degli Asintoti
Gli asintoti sono rette a cui il grafico di una funzione $f(x)$ si avvicina indefinitamente. Si studiano tipicamente agli estremi del dominio della funzione, ovvero nei punti di accumulazione all'infinito o nei punti di accumulazione finiti che non appartengono al dominio.

> [!info] Nota di Collegamento
> Il concetto di asintoto è intrinsecamente legato alla definizione di [[17 - Intorni, Punti di Accumulazione e Limiti di Funzione|Limite di Funzione]].

### Asintoti Orizzontali
Un asintoto orizzontale esiste se il limite della funzione per $x$ che tende a infinito (o meno infinito) è un valore finito $L$. La retta di equazione $y=L$ è l'asintoto orizzontale.
$$\lim_{x \to \pm\infty} f(x) = L, \quad L \in \mathbb{R} \implies y=L \text{ è asintoto orizzontale}$$

### Asintoti Verticali
Un asintoto verticale si manifesta in corrispondenza di un punto di accumulazione finito $x_0$ (tipicamente un punto escluso dal dominio) se il limite della funzione per $x$ che tende a $x_0$ (da destra o da sinistra) è infinito.
$$\lim_{x \to x_0^+} f(x) = \pm\infty \quad \text{oppure} \quad \lim_{x \to x_0^-} f(x) = \pm\infty \implies x=x_0 \text{ è asintoto verticale}$$
> [!info] Nota di Collegamento
> La ricerca di asintoti verticali è strettamente legata allo studio dei [[18 - Limiti, Continuità e Teoremi sulle Funzioni Continue|Punti di Discontinuità]] di una funzione (in particolare, discontinuità di seconda specie).

### Asintoti Obliqui
Se il grafico di una funzione, per $x \to \pm\infty$, si avvicina a una retta non orizzontale di equazione $y = mx + q$ (con $m \ne 0$), tale retta è un asintoto obliquo. La condizione affinché $y=mx+q$ sia asintoto obliquo è che:
$$\lim_{x \to \pm\infty} [f(x) - (mx + q)] = 0$$
Per determinare i coefficienti $m$ e $q$, si procede analiticamente.

**Calcolo di m:**
Se il limite $\lim [f(x) - (mx + q)]$ è zero, a maggior ragione lo è se dividiamo per $x$:
$$\lim_{x \to \pm\infty} \frac{f(x) - mx - q}{x} = \lim_{x \to \pm\infty} \left( \frac{f(x)}{x} - m - \frac{q}{x} \right) = 0$$
Poiché $\lim \frac{q}{x} = 0$, affinché il limite sia nullo, deve valere:
$$m = \lim_{x \to \pm\infty} \frac{f(x)}{x}$$

**Calcolo di q:**
Una volta trovato $m$ (che deve essere finito e $m \ne 0$), si ricava $q$ dalla definizione stessa:
$$q = \lim_{x \to \pm\infty} (f(x) - mx)$$

Perché l'asintoto obliquo esista, entrambi i limiti devono esistere e risultare finiti, con $m \ne 0$.

**Nota:** Se una funzione ammette un asintoto orizzontale per $x \to +\infty$ (cioè $m=0$), non può ammettere un asintoto obliquo per $x \to +\infty$.

## Punti di Non Derivabilità e Tangenti Verticali

### Estensione del Concetto di Derivata
In alcuni casi, il limite del rapporto incrementale può essere infinito. Sebbene formalmente la derivata non esista come valore finito (poiché la derivata è un numero reale), si adotta la notazione:
$$f'(x_0) = \lim_{h \to 0} \frac{f(x_0+h) - f(x_0)}{h} = \pm\infty$$
Questo indica la presenza di una **retta tangente verticale** di equazione $x = x_0$ nel punto $(x_0, f(x_0))$.

> [!info] Nota di Collegamento
> Questi casi particolari emergono quando il [[20 - Infinitesimi, Principio di Sostituzione e Derivata|limite del rapporto incrementale]] non è un numero finito.

### Classificazione dei Punti di Non Derivabilità
1.  **Flesso a Tangente Verticale**: Si ha quando le derivate destra e sinistra in $x_0$ sono entrambe $+\infty$ o entrambe $-\infty$.
    * $f'_-(x_0) = f'_+(x_0) = +\infty$ (funzione crescente in un intorno di $x_0$).
    * $f'_-(x_0) = f'_+(x_0) = -\infty$ (funzione decrescente).
2.  **Punto Angoloso**: Si verifica quando le derivate destra e sinistra in $x_0$ esistono, sono diverse tra loro e almeno una delle due è finita. Un esempio è $f(x)=|x|$ in $x_0=0$, dove $f'_-(0)=-1$ e $f'_+(0)=1$.
3.  **Cuspide**: Si ha quando le derivate destra e sinistra in $x_0$ sono entrambe infinite ma di segno opposto (es. $f'_-(x_0) = -\infty$ e $f'_+(x_0) = +\infty$, o viceversa). Il grafico della funzione forma una punta acuta in $x_0$.

## Funzioni Iperboliche
Le funzioni iperboliche sono combinazioni di [[09 - Funzioni Esponenziali, Logaritmiche e Trigonometriche Fondamentali|funzioni esponenziali]].

* **Seno iperbolico**: $\sinh(x) = \frac{e^x - e^{-x}}{2}$
* **Coseno iperbolico**: $\cosh(x) = \frac{e^x + e^{-x}}{2}$
* **Tangente iperbolica**: $\tanh(x) = \frac{\sinh(x)}{\cosh(x)} = \frac{e^x - e^{-x}}{e^x + e^{-x}}$

**Proprietà principali:**
* **Dominio**: $\sinh(x)$ e $\cosh(x)$ sono definite su $\mathbb{R}$. $\tanh(x)$ è definita su $\mathbb{R}$.
* **Parità**: $\sinh(x)$ e $\tanh(x)$ sono funzioni dispari. $\cosh(x)$ è una funzione pari.
* **Monotonia**: La funzione $\sinh(x)$ è strettamente crescente, essendo somma di due funzioni crescenti ($e^x$ e $-e^{-x}$).
* **Relazione fondamentale**: $\cosh^2(x) - \sinh^2(x) = 1$

### Inverse delle Funzioni Iperboliche

#### Inversione del Seno Iperbolico
Essendo strettamente monotona su $\mathbb{R}$, $\sinh(x)$ è invertibile su tutto $\mathbb{R}$. Per trovare la sua inversa, si risolve l'equazione $y = \frac{e^x - e^{-x}}{2}$ rispetto a $x$.
$$2y = e^x - \frac{1}{e^x} \implies 2ye^x = e^{2x} - 1$$
Ponendo $t=e^x$ (con $t>0$), si ottiene un'equazione di secondo grado in $t$:
$$t^2 - 2yt - 1 = 0$$
Le cui soluzioni sono $t = \frac{2y \pm \sqrt{4y^2 + 4}}{2} = y \pm \sqrt{y^2 + 1}$.
Poiché $t=e^x$ deve essere positivo e $\sqrt{y^2 + 1} > \sqrt{y^2} = |y| \ge y$, la soluzione $t_1 = y - \sqrt{y^2 + 1}$ è sempre negativa e va scartata.
Si accetta solo la soluzione $t_2 = y + \sqrt{y^2 + 1}$.
$$e^x = y + \sqrt{y^2 + 1} \implies x = \ln(y + \sqrt{y^2 + 1})$$
La funzione inversa, chiamata **settore seno iperbolico** (o arcoseno iperbolico), è:
$$\text{arsinh}(x) = \ln(x + \sqrt{x^2 + 1}) \quad (D = \mathbb{R})$$
La sua derivata è:
$$D[\text{arsinh}(x)] = \frac{1}{\sqrt{x^2 + 1}}$$

#### Inversione del Coseno Iperbolico
$\cosh(x)$ è una funzione pari, non è invertibile su $\mathbb{R}$. La si restringe all'intervallo $[0, +\infty)$, dove è strettamente crescente. La sua inversa (settore coseno iperbolico) è:
$$\text{arcosh}(x) = \ln(x + \sqrt{x^2 - 1}) \quad (D = [1, +\infty))$$
La sua derivata è:
$$D[\text{arcosh}(x)] = \frac{1}{\sqrt{x^2 - 1}} \quad (\text{per } x > 1)$$

#### Inversione della Tangente Iperbolica
$\tanh(x)$ è strettamente crescente e ha immagine $(-1, 1)$. La sua inversa (settore tangente iperbolica) è:
$$\text{artanh}(x) = \frac{1}{2} \ln\left(\frac{1+x}{1-x}\right) \quad (D = (-1, 1))$$
La sua derivata è:
$$D[\text{artanh}(x)] = \frac{1}{1 - x^2} \quad (\text{per } x \in (-1, 1))$$

## Esercizio Svolto: Studio di Funzione
Si consideri la funzione $f(x) = \frac{|x+1|}{x^2 - 4x + 3}$. Determinare asintoti e punti di massimo e minimo relativi.

> [!abstract] Nota Metodologica: Schema dello Studio di Funzione
> Questo esercizio applica quasi tutti i concetti visti finora. Uno studio di funzione completo segue tipicamente questi passi:
> 1.  Dominio ed eventuali simmetrie (parità/disparità).
> 2.  Studio del segno e intersezioni con gli assi.
> 3.  Limiti agli estremi del dominio e ricerca di [[#Studio degli Asintoti|Asintoti]] (Verticali, Orizzontali, Obliqui).
> 4.  Calcolo della Derivata Prima $f'(x)$.
> 5.  Studio del segno di $f'(x)$ per determinare [[#Riepilogo dei Criteri di Monotonia|Monotonia]] (intervalli crescenti/decrescenti) e Punti Stazionari (Max/Min relativi).
> 6.  Identificazione di [[#Punti di Non Derivabilità e Tangenti Verticali|Punti di non derivabilità]].
> 7.  (Se richiesto) Calcolo della Derivata Seconda $f''(x)$ per [[#Concavità e Convessità|Convessità]] e Punti di Flesso.

### 1. Dominio e Studio del Modulo
Il denominatore $x^2 - 4x + 3 = (x-1)(x-3)$ si annulla per $x=1$ e $x=3$.
Il dominio è $D = \mathbb{R} \setminus \{1, 3\}$.

Poiché l'esercizio chiede uno studio di $f(x) = \frac{|x+1|}{(x-1)(x-3)}$, notiamo che il numeratore è sempre $\ge 0$. Tuttavia, la funzione *non* è $f(x) = \left| \frac{x+1}{x^2-4x+3} \right|$. Il modulo è solo al numeratore.
*Correggiamo l'impostazione dell'esercizio data nel testo originale, assumendo $f(x) = \frac{|x+1|}{x^2 - 4x + 3}$ (come scritto).*

La funzione si divide in due casi in base al segno di $x+1$:
$$f(x) = \begin{cases} \frac{x+1}{x^2 - 4x + 3} & \text{se } x \ge -1, \quad x \ne 1, 3 \\ -\frac{x+1}{x^2 - 4x + 3} & \text{se } x < -1 \end{cases}$$

### 2. Ricerca degli Asintoti
* **Asintoti Orizzontali**: Poiché il grado del denominatore (2) è maggiore di quello del numeratore (1), si ha:
    $$\lim_{x \to \pm\infty} f(x) = \lim_{x \to \pm\infty} \frac{|x+1|}{x^2 - 4x + 3} = 0$$
    La retta $y=0$ è asintoto orizzontale sia per $x \to +\infty$ che per $x \to -\infty$. Non ci sono asintoti obliqui.
* **Asintoti Verticali**: Si studiano i limiti nei punti esclusi dal dominio, $x=1$ e $x=3$.
    * Per $x \to 1$: Il numeratore $|x+1| \to 2$. Il denominatore $(x-1)(x-3) \to 0$.
        $$\lim_{x \to 1^-} f(x) = \lim_{x \to 1^-} \frac{2}{(0^-)(-2)} = +\infty$$
        $$\lim_{x \to 1^+} f(x) = \lim_{x \to 1^+} \frac{2}{(0^+)(-2)} = -\infty$$
        La retta $x=1$ è asintoto verticale.
    * Per $x \to 3$: Il numeratore $|x+1| \to 4$. Il denominatore $(x-1)(x-3) \to 0$.
        $$\lim_{x \to 3^-} f(x) = \lim_{x \to 3^-} \frac{4}{(2)(0^-)} = -\infty$$
        $$\lim_{x \to 3^+} f(x) = \lim_{x \to 3^+} \frac{4}{(2)(0^+)} = +\infty$$
        La retta $x=3$ è asintoto verticale.

*(Nota: L'esercizio nel testo originale sembrava assumere $f(x) = \left| \frac{x+1}{x^2-4x+3} \right|$ dato che concludeva $f(x) \ge 0$ e trovava solo limiti $+\infty$. Ho svolto l'esercizio per la funzione $f(x) = \frac{|x+1|}{x^2 - 4x + 3}$ come scritta esplicitamente).*

### 3. Studio della Monotonia (e Punti di Non Derivabilità)
La funzione non è derivabile in $x=-1$ (a causa del modulo $|x+1|$), che è un punto angoloso.
$f(-1) = 0$.

Calcoliamo la derivata prima $g'(x)$ di $g(x) = \frac{x+1}{x^2 - 4x + 3}$.
$$g'(x) = \frac{1(x^2 - 4x + 3) - (x+1)(2x - 4)}{(x^2 - 4x + 3)^2} = \frac{x^2 - 4x + 3 - (2x^2 - 2x - 4)}{(x^2 - 4x + 3)^2}$$
$$g'(x) = \frac{-x^2 - 2x + 7}{(x^2 - 4x + 3)^2}$$

La derivata $f'(x)$ è:
$$f'(x) = \begin{cases} g'(x) = \frac{-x^2 - 2x + 7}{(x^2 - 4x + 3)^2} & \text{se } x > -1, \quad x \ne 1, 3 \\ -g'(x) = -\frac{-x^2 - 2x + 7}{(x^2 - 4x + 3)^2} & \text{se } x < -1 \end{cases}$$

Studiamo il segno del numeratore $-x^2 - 2x + 7 \ge 0$. Le radici sono $x = \frac{2 \pm \sqrt{4 - 4(-1)(7)}}{-2} = \frac{2 \pm \sqrt{32}}{-2} = -1 \mp \sqrt{8} = -1 \mp 2\sqrt{2}$.
$-x^2 - 2x + 7 \ge 0$ per $x \in [-1-2\sqrt{2}, -1+2\sqrt{2}]$.
($-1-2\sqrt{2} \approx -3.82$, $-1+2\sqrt{2} \approx 1.82$).

Analizziamo il segno di $f'(x)$:
* **Per $x < -1$**: $f'(x) = -g'(x)$.
    * $g'(x) > 0$ per $x \in (-1-2\sqrt{2}, -1)$. $f'(x) < 0$ (decrescente).
    * $g'(x) < 0$ per $x \in (-\infty, -1-2\sqrt{2})$. $f'(x) > 0$ (crescente).
* **Per $x > -1$**: $f'(x) = g'(x)$.
    * $g'(x) > 0$ per $x \in (-1, 1) \cup (1, -1+2\sqrt{2})$. $f'(x) > 0$ (crescente).
    * $g'(x) < 0$ per $x \in (-1+2\sqrt{2}, 3) \cup (3, +\infty)$. $f'(x) < 0$ (decrescente).

### 4. Massimi e Minimi
Dall'analisi della monotonia:
* $x = -1 - 2\sqrt{2}$: $f'(x)$ passa da $+$ a $-$. Punto di **massimo relativo**.
* $x = -1$: $f'(x)$ passa da $-$ a $+$. $f(-1)=0$. Punto di **minimo relativo** (è un punto angoloso).
* $x = -1 + 2\sqrt{2}$: $f'(x)$ passa da $+$ a $-$. Punto di **massimo relativo**.

La funzione non è limitata né superiormente né inferiormente (a causa degli asintoti verticali). **Non esistono massimi o minimi assoluti**.
*(Questo risultato differisce da quello del testo originale, che presupponeva $f(x) \ge 0$ e trovava un minimo assoluto in $x=-1$. La mia analisi si basa su $f(x) = \frac{|x+1|}{x^2 - 4x + 3}$).*