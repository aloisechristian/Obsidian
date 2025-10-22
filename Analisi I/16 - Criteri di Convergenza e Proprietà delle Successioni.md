# Teoremi sui Limiti, Successioni Monotone e Criteri di Convergenza

## Teorema della Permanenza del Segno e Corollari

### Enunciato del Teorema

Il Teorema della Permanenza del Segno stabilisce una proprietà fondamentale delle [[14 - Definizione e Teoremi dei Limiti di Successioni#Definizione Formale di Limite Finito (Convergenza)|successioni convergenti]]. Esso afferma che se una successione $(a_n)$ converge a un limite $A$ strettamente positivo o strettamente negativo, allora i termini della successione, a partire da un certo indice in poi (*definitivamente*), avranno lo stesso segno del limite.

Formalmente:
1.  Se $\lim_{n \to +\infty} a_n = A$ con $A > 0$, allora esiste un indice $n_i \in \mathbb{N}$ tale che per ogni $n > n_i$, si ha $a_n > 0$.
2.  Se $\lim_{n \to +\infty} a_n = A$ con $A < 0$, allora esiste un indice $n_i \in \mathbb{N}$ tale che per ogni $n > n_i$, si ha $a_n < 0$.

L'intuizione dietro questo teorema risiede nella definizione stessa di [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Definizione Formale di Limite Finito (Successione Convergente)|limite]]: se i termini della successione si avvicinano arbitrariamente ad $A$, e $A$ è separato da zero (essendo $A \ne 0$), anche i termini della successione $a_n$, per $n$ sufficientemente grande, dovranno essere separati da zero e avere lo stesso segno di $A$.

**Dimostrazione (Caso A > 0):**
Per definizione di limite, $\forall \epsilon > 0, \exists n_i \in \mathbb{N}$ tale che $\forall n > n_i$, $|a_n - A| < \epsilon$, che equivale a $A - \epsilon < a_n < A + \epsilon$.
Poiché l'affermazione deve valere per ogni $\epsilon > 0$, possiamo sceglierne uno opportuno. Dato che $A > 0$, possiamo scegliere $\epsilon = \frac{A}{2}$. Essendo $A/2 > 0$, questa è una scelta valida per $\epsilon$.
Con questa scelta, la definizione di limite garantisce che esiste $n_i$ tale che per $n > n_i$:
$A - \frac{A}{2} < a_n < A + \frac{A}{2}$
$\frac{A}{2} < a_n < \frac{3A}{2}$
Poiché $A > 0$, anche $\frac{A}{2} > 0$. La disuguaglianza $a_n > \frac{A}{2}$ implica quindi che $a_n > 0$ per ogni $n > n_i$. La dimostrazione per $A < 0$ è analoga, scegliendo $\epsilon = -A/2 = |A|/2$.

### Corollari

Dal teorema principale discendono due importanti corollari:

1.  **Corollario 1:** Se una successione $(a_n)$ ha termini non negativi per ogni $n$ (cioè $a_n \ge 0$ per ogni $n \in \mathbb{N}$) e ammette limite $A$, allora $A \ge 0$. In altre parole, una successione a termini non negativi non può convergere a un limite negativo.
    *Dimostrazione (per assurdo):* Supponiamo che $A < 0$. Per il Teorema della Permanenza del Segno (caso 2), esisterebbe $n_i$ tale che per $n > n_i$, $a_n < 0$. Questo contraddice l'ipotesi che $a_n \ge 0$ per ogni $n$. Dunque, deve essere $A \ge 0$.

2.  **Corollario 2 (Confronto tra Limiti):** Date due successioni convergenti $(a_n)$ e $(b_n)$ tali che $a_n \ge b_n$ per ogni $n$, allora i rispettivi limiti, $A$ e $B$, conservano la stessa relazione d'ordine: $A \ge B$.
    *Dimostrazione:* Si considera la successione differenza $(c_n) = (a_n - b_n)$. Per ipotesi, $c_n = a_n - b_n \ge 0$ per ogni $n$. Per l'[[14 - Definizione e Teoremi dei Limiti di Successioni#Algebra dei Limiti|algebra dei limiti]], $\lim_{n \to +\infty} c_n = \lim a_n - \lim b_n = A - B$. Applicando il Corollario 1 alla successione $(c_n)$, poiché $c_n \ge 0$ e il limite esiste, tale limite deve essere non negativo: $A - B \ge 0$, da cui $A \ge B$.

---
## Teorema del Confronto (o dei Carabinieri)

Questo teorema, noto anche come Teorema dei Carabinieri o Squeeze Theorem, fornisce un metodo potente per determinare il limite di una successione "intrappolandola" tra altre due successioni convergenti allo stesso limite.

* **Caso Convergente:** Siano $(a_n)$, $(b_n)$, e $(c_n)$ tre successioni tali che $a_n \le c_n \le b_n$ per ogni $n$ (o almeno *definitivamente*, cioè da un certo indice $\nu_0$ in poi). Se $\lim_{n \to +\infty} a_n = \lim_{n \to +\infty} b_n = A$, allora anche la successione centrale $(c_n)$ converge allo stesso limite: $\lim_{n \to +\infty} c_n = A$.

    *Dimostrazione:* Fissato $\epsilon > 0$. Per definizione di limite applicata a $(a_n)$ e $(b_n)$:
    * $\exists \nu_1$ t.c. $\forall n > \nu_1$, $|a_n - A| < \epsilon \implies A - \epsilon < a_n < A + \epsilon$.
    * $\exists \nu_2$ t.c. $\forall n > \nu_2$, $|b_n - A| < \epsilon \implies A - \epsilon < b_n < A + \epsilon$.
    Sia $\nu = \max\{\nu_0, \nu_1, \nu_2\}$. Per ogni $n > \nu$, valgono tutte le condizioni:
    $$A - \epsilon < a_n \le c_n \le b_n < A + \epsilon$$
    Questo implica $A - \epsilon < c_n < A + \epsilon$, ovvero $|c_n - A| < \epsilon$. Poiché questo vale per ogni $\epsilon > 0$, si conclude che $\lim_{n \to +\infty} c_n = A$.

* **Caso Divergente:** Il principio si estende alle successioni divergenti:
    * Se $a_n \le b_n$ definitivamente e $\lim_{n \to +\infty} a_n = +\infty$, allora necessariamente $\lim_{n \to +\infty} b_n = +\infty$.
    * Se $a_n \le b_n$ definitivamente e $\lim_{n \to +\infty} b_n = -\infty$, allora necessariamente $\lim_{n \to +\infty} a_n = -\infty$.

---
## Proprietà delle Successioni

* **Limite Nullo e Valore Assoluto:** Una successione $(a_n)$ converge a zero ([[14 - Definizione e Teoremi dei Limiti di Successioni#Terminologia|infinitesima]]) se e solo se la successione dei suoi valori assoluti $(|a_n|)$ converge a zero.
    $$\lim_{n \to +\infty} a_n = 0 \iff \lim_{n \to +\infty} |a_n| = 0$$
    Questo deriva direttamente dalla [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Definizione Formale di Limite Finito (Successione Convergente)|definizione di limite]], poiché la condizione $|a_n - 0| < \epsilon$ è identica a $||a_n| - 0| < \epsilon$. Questa proprietà è specifica per il limite nullo.

* **Prodotto di Infinitesima per Limitata:** Il prodotto di una successione infinitesima per una successione [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Successioni Limitate|limitata]] è una successione infinitesima.
    *Dimostrazione:* Siano $(a_n)$ limitata (cioè $\exists M>0$ t.c. $|a_n| \le M$ $\forall n$) e $(b_n)$ infinitesima ($\lim b_n = 0$). Vogliamo dimostrare che $\lim (a_n b_n) = 0$. Fissato $\epsilon > 0$. Poiché $\lim b_n = 0$, $\exists \nu$ t.c. $\forall n > \nu$, $|b_n - 0| = |b_n| < \frac{\epsilon}{M}$. Allora, per $n > \nu$:
    $$|a_n b_n - 0| = |a_n| |b_n| \le M |b_n| < M \cdot \frac{\epsilon}{M} = \epsilon$$
    Questo verifica la definizione di limite.
    *Esempio:* La successione $a_n = \frac{(-1)^n}{n}$ è il prodotto della successione limitata $b_n = (-1)^n$ e della successione infinitesima $c_n = 1/n$. Pertanto, $\lim_{n \to +\infty} a_n = 0$.

---
## Limiti Notevoli

### Limite della Successione Geometrica $a^n$

Il comportamento della successione $a^n$ per $n \to +\infty$ dipende dal valore della base $a$:
* Se $a > 1$: $\lim_{n \to +\infty} a^n = +\infty$ (Successione [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Successioni Divergenti e Irregolari|infinita]]).
* Se $a = 1$: $\lim_{n \to +\infty} 1^n = 1$ (Successione costante).
* Se $|a| < 1$ (cioè $-1 < a < 1$): $\lim_{n \to +\infty} a^n = 0$ (Successione [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Terminologia Aggiuntiva|infinitesima]]).
* Se $a \le -1$: Il limite non esiste (Successione [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Successioni Divergenti e Irregolari|irregolare/indeterminata]]). La successione oscilla tra valori positivi e negativi che crescono in modulo (se $a < -1$) o rimangono costanti in modulo (se $a = -1$).

### Limiti Trigonometrici

Data una successione $(a_n)$ tale che $\lim_{n \to +\infty} a_n = 0$:
* $\lim_{n \to +\infty} \sin(a_n) = \sin(0) = 0$.
* $\lim_{n \to +\infty} \cos(a_n) = \cos(0) = 1$.
* $\lim_{n \to +\infty} \frac{\sin(a_n)}{a_n} = 1$. Questo è un limite notevole fondamentale che risolve la [[14 - Definizione e Teoremi dei Limiti di Successioni#Forme Indeterminate|forma indeterminata $0/0$]]. La sua dimostrazione si basa su considerazioni geometriche sulla circonferenza goniometrica.

---
## Successioni Monotone

### Definizioni

Una successione $(a_n)$ si dice:
* **Crescente:** se $a_n \le a_{n+1}$ per ogni $n \in \mathbb{N}$.
* **Strettamente crescente:** se $a_n < a_{n+1}$ per ogni $n \in \mathbb{N}$.
* **Decrescente:** se $a_n \ge a_{n+1}$ per ogni $n \in \mathbb{N}$.
* **Strettamente decrescente:** se $a_n > a_{n+1}$ per ogni $n \in \mathbb{N}$.

Una successione che rientra in uno di questi quattro casi è detta **[[Analisi I/04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|monotona]]**. Se le disuguaglianze sono strette, è **[[Analisi I/04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente monotona]]**.

### Teorema di Regolarità delle Successioni Monotone

Questo teorema stabilisce una proprietà cruciale:
> **Ogni successione monotona ammette limite (è [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Successioni Divergenti e Irregolari|regolare]]).**

Il valore del limite dipende dalla limitatezza della successione:

* **Caso limitato (Convergenza):** Se una successione monotona è anche [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Successioni Limitate|limitata]], allora è **convergente**.
    * Se $(a_n)$ è crescente e limitata superiormente, allora $\lim_{n \to +\infty} a_n = \sup\{a_n \mid n \in \mathbb{N}\}$.
    * Se $(a_n)$ è decrescente e limitata inferiormente, allora $\lim_{n \to +\infty} a_n = \inf\{a_n \mid n \in \mathbb{N}\}$.
* **Caso non limitato (Divergenza):** Se una successione monotona non è limitata, allora è **divergente**.
    * Se $(a_n)$ è crescente e non limitata superiormente, allora $\lim_{n \to +\infty} a_n = +\infty$.
    * Se $(a_n)$ è decrescente e non limitata inferiormente, allora $\lim_{n \to +\infty} a_n = -\infty$.

*(Per la dimostrazione del caso convergente, vedi [[15 - Teoremi Fondamentali dei Limiti di Successioni#Dimostrazione (caso crescente e limitato)]])*

---
## Il Numero di Nepero $e$

Si considera la successione $a_n = \left(1 + \frac{1}{n}\right)^n$. Per $n \to +\infty$, si ha $1 + \frac{1}{n} \to 1$ e $n \to +\infty$. Si presenta la [[14 - Definizione e Teoremi dei Limiti di Successioni#Forme Indeterminate|forma indeterminata]] $1^\infty$.
Altre forme indeterminate esponenziali sono $0^0$ e $\infty^0$.

Si può dimostrare (la dimostrazione dettagliata si trova su testi di riferimento come Marcellini-Sbordone) che la successione $(a_n)$ è:
1.  **Monotona crescente**
2.  **Limitata** (si dimostra che $2 < a_n < 3$ per ogni $n$)

Per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema di Regolarità delle Successioni Monotone|Teorema di Regolarità delle Successioni Monotone]], essendo $(a_n)$ monotona crescente e limitata, essa deve convergere a un limite finito. Questo limite è il **numero di Nepero**, denotato con $e$.
$$\lim_{n \to +\infty} \left(1 + \frac{1}{n}\right)^n = e$$
Il valore di $e$ è approssimativamente $2.71828...$, ed è un numero irrazionale e trascendente. Si dimostra che $2 < e < 3$.

---
## Criterio del Rapporto per le Successioni

Questo criterio fornisce una condizione *sufficiente* (ma non necessaria) per determinare se una successione a termini positivi è [[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Terminologia Aggiuntiva|infinitesima]] (tende a zero).

**Teorema:** Sia $(a_n)$ una successione con $a_n > 0$ per ogni $n$. Si consideri il limite del rapporto tra due termini consecutivi:
$$\lim_{n \to +\infty} \frac{a_{n+1}}{a_n} = B$$
* Se $B < 1$, allora la successione è infinitesima, cioè $\lim_{n \to +\infty} a_n = 0$.
* Se $B > 1$, allora la successione diverge a $+\infty$.
* Se $B = 1$, il criterio è inconclusivo (non si può dire nulla sul limite di $a_n$).

**Dimostrazione (sintesi del caso B < 1):**
1.  Poiché $\lim_{n \to +\infty} \frac{a_{n+1}}{a_n} = B < 1$, applicando il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema della Permanenza del Segno|Teorema della Permanenza del Segno]] alla successione $b_n = \frac{a_{n+1}}{a_n}$, esiste un $\epsilon > 0$ (ad esempio $\epsilon = (1-B)/2$) e un indice $n_i$ tale che per $n > n_i$, si ha $\frac{a_{n+1}}{a_n} < B + \epsilon < 1$. In particolare, $a_{n+1} < a_n$ per $n > n_i$.
2.  La successione $(a_n)$ è quindi, da un certo punto in poi, **strettamente decrescente**.
3.  Essendo $a_n > 0$ per ipotesi, la successione è **limitata inferiormente** da 0.
4.  Per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema di Regolarità delle Successioni Monotone|Teorema delle successioni monotone]], essendo decrescente e limitata inferiormente, ammette un limite finito $A \ge 0$.
5.  Si dimostra per [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|assurdo]] che $A=0$. Se fosse $A > 0$, allora, per l'[[14 - Definizione e Teoremi dei Limiti di Successioni#Algebra dei Limiti|algebra dei limiti]], si avrebbe $\lim_{n \to +\infty} \frac{a_{n+1}}{a_n} = \frac{\lim a_{n+1}}{\lim a_n} = \frac{A}{A} = 1$. Questo contraddice l'ipotesi $B < 1$. Pertanto, l'unica possibilità è $A=0$.

---
## Gerarchia degli Infiniti

Esiste un ordine di "velocità" con cui le successioni divergenti tendono all'infinito. Le seguenti successioni sono elencate in ordine crescente di infinito (ognuna tende a infinito "più velocemente" della precedente), per $a > 1$ e $b > 0$:
$$\log_a(n), \quad n^b, \quad a^n, \quad n!, \quad n^n$$
Questo significa che il limite del rapporto tra una successione e una successiva nella lista è zero. Tutti i seguenti limiti, che rappresentano [[14 - Definizione e Teoremi dei Limiti di Successioni#Forme Indeterminate|forme indeterminate]] $\frac{\infty}{\infty}$, valgono 0:
* $\lim_{n \to +\infty} \frac{\log_a n}{n^b} = 0$
* $\lim_{n \to +\infty} \frac{n^b}{a^n} = 0$
* $\lim_{n \to +\infty} \frac{a^n}{n!} = 0$
* $\lim_{n \to +\infty} \frac{n!}{n^n} = 0$

Questi risultati si possono dimostrare utilizzando il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Criterio del Rapporto per le Successioni|Criterio del Rapporto]]. Ad esempio, per dimostrare che $\lim_{n \to +\infty} \frac{n!}{n^n} = 0$, si pone $a_n = \frac{n!}{n^n}$ (che è a termini positivi) e si calcola il limite del rapporto:
$$\lim_{n \to +\infty} \frac{a_{n+1}}{a_n} = \lim_{n \to +\infty} \frac{(n+1)!/(n+1)^{n+1}}{n!/n^n} = \lim_{n \to +\infty} \frac{(n+1)!}{(n+1)^{n+1}} \cdot \frac{n^n}{n!}$$
$$= \lim_{n \to +\infty} \frac{(n+1) \cdot n!}{(n+1) \cdot (n+1)^n} \cdot \frac{n^n}{n!} = \lim_{n \to +\infty} \frac{n^n}{(n+1)^n} = \lim_{n \to +\infty} \left(\frac{n}{n+1}\right)^n$$
$$= \lim_{n \to +\infty} \left(\frac{1}{\frac{n+1}{n}}\right)^n = \lim_{n \to +\infty} \frac{1}{\left(1+\frac{1}{n}\right)^n} = \frac{1}{\lim_{n \to +\infty} \left(1+\frac{1}{n}\right)^n} = \frac{1}{e}$$
Poiché $e \approx 2.718$, si ha $B = 1/e < 1$. Per il Criterio del Rapporto, la successione $a_n$ tende a 0.

---
## Successioni Estratte (Sottosuccessioni)

### Definizione
Data una successione $(a_n)_{n \in \mathbb{N}}$ e una successione **strettamente crescente** di indici naturali $(n_k)_{k \in \mathbb{N}}$ (cioè $n_1 < n_2 < n_3 < \dots$), la successione $(a_{n_k})_{k \in \mathbb{N}}$ è detta **successione estratta** (o sottosuccessione) di $(a_n)$. Si ottiene selezionando dalla successione originale solo i termini corrispondenti agli indici $n_k$.

*Esempi:*
* Se $n_k = 2k$ (indici pari): $a_2, a_4, a_6, \dots$
* Se $n_k = 2k-1$ (indici dispari): $a_1, a_3, a_5, \dots$
* Se $n_k = k^2$: $a_1, a_4, a_9, a_{16}, \dots$

### Proprietà

1.  **Lemma:** Se $(n_k)$ è una successione strettamente crescente di interi naturali, allora $n_k \ge k$ per ogni $k \in \mathbb{N}$.
    *Dimostrazione (per induzione):*
    * Base ($k=1$): $n_1$ è un numero naturale, quindi $n_1 \ge 1$. Vero.
    * Passo induttivo: Assumiamo $n_k \ge k$. Dobbiamo provare $n_{k+1} \ge k+1$. Poiché la successione è strettamente crescente, $n_{k+1} > n_k$. Per ipotesi induttiva, $n_k \ge k$. Quindi $n_{k+1} > n_k \ge k$. Essendo $n_{k+1}$ e $k$ interi, $n_{k+1} > k$ implica $n_{k+1} \ge k+1$.

2.  **Teorema:** Se una successione $(a_n)$ converge (o diverge) al limite $A \in \mathbb{R} \cup \{-\infty, +\infty\}$, allora **ogni** sua successione estratta $(a_{n_k})$ converge (o diverge) allo stesso limite $A$.
    *Dimostrazione (caso convergente ad $A \in \mathbb{R}$):* Fissato $\epsilon > 0$. Poiché $\lim a_n = A$, $\exists \nu$ t.c. $\forall n > \nu$, $|a_n - A| < \epsilon$. Vogliamo dimostrare che $\lim_{k \to +\infty} a_{n_k} = A$. Dobbiamo trovare un $k_0$ t.c. $\forall k > k_0$, $|a_{n_k} - A| < \epsilon$.
    Per il lemma, $n_k \ge k$. Se scegliamo $k_0 = \nu$, allora per ogni $k > k_0 = \nu$, si ha $n_k \ge k > \nu$. Essendo l'indice $n_k$ maggiore di $\nu$, vale la condizione $|a_{n_k} - A| < \epsilon$.

3.  **Il viceversa non è vero:** L'esistenza di una o più estratte convergenti (anche allo stesso limite) non garantisce la convergenza della successione di partenza. L'esempio classico è $a_n = (-1)^n$, che non converge. Tuttavia, possiede:
    * L'estratta dei pari $(a_{2k}) = ((-1)^{2k}) = (1)$, che converge a 1.
    * L'estratta dei dispari $(a_{2k-1}) = ((-1)^{2k-1}) = (-1)$, che converge a -1.

### Teorema di Bolzano-Weierstrass
Questo teorema fornisce una condizione sufficiente per garantire l'esistenza di almeno una sottosuccessione convergente.
> **Teorema:** Ogni successione **[[13 - Definizione, Proprietà e Limiti delle Successioni Numeriche#Successioni Limitate|limitata]]** di numeri reali ammette almeno una successione estratta convergente.

---
## Successioni di Cauchy

### Definizione
Una successione $(a_n)$ si dice **di Cauchy** se i suoi termini diventano arbitrariamente vicini tra loro al crescere dell'indice. Formalmente:
$$\forall \epsilon > 0, \exists \nu \in \mathbb{N} \text{ tale che } \forall h, k > \nu, \quad |a_h - a_k| < \epsilon$$
Intuitivemente, una successione di Cauchy è una successione i cui termini, da un certo punto in poi, sono "addensati".

### Teorema di Completezza di $\mathbb{R}$ (Criterio di Convergenza di Cauchy)
La nozione di successione di Cauchy è fondamentale perché fornisce un criterio *intrinseco* di convergenza, che non richiede la conoscenza a priori del valore del limite. In $\mathbb{R}$, vale la seguente importantissima equivalenza, che esprime la **completezza** dello spazio dei numeri reali:

> **Teorema:** Una successione $(a_n)$ di numeri reali è **convergente** se e solo se è una **successione di Cauchy**.

La dimostrazione si articola nei seguenti passaggi logici:

1.  **(⇒) Ogni successione convergente è di Cauchy.**
    *Dimostrazione:* Sia $\lim a_n = A$. Fissato $\epsilon > 0$. Per definizione di limite, $\exists \nu$ t.c. $\forall n > \nu$, $|a_n - A| < \epsilon/2$. Siano $h, k > \nu$. Allora, usando la [[06 - Studio delle Funzioni Valore Assoluto e Potenza#La Disuguaglianza Triangolare|disuguaglianza triangolare]]:
    $$|a_h - a_k| = |a_h - A + A - a_k| \le |a_h - A| + |A - a_k| = |a_h - A| + |a_k - A|$$
    Poiché $h > \nu$ e $k > \nu$, entrambi i termini sono minori di $\epsilon/2$:
    $$< \frac{\epsilon}{2} + \frac{\epsilon}{2} = \epsilon$$
    Questo prova che $(a_n)$ è di Cauchy.

2.  **(Lemma 1) Ogni successione di Cauchy è limitata.**
    *Dimostrazione:* Fissiamo $\epsilon = 1$. Per definizione di successione di Cauchy, $\exists \nu$ t.c. $\forall h, k > \nu$, $|a_h - a_k| < 1$. Fissiamo un indice particolare $h_0 > \nu$. Allora, per ogni $k > \nu$, si ha $|a_k - a_{h_0}| < 1$, che implica $a_{h_0} - 1 < a_k < a_{h_0} + 1$. Questo mostra che la *coda* della successione (i termini con indice $k>\nu$) è limitata. L'insieme dei primi $\nu$ termini $\{a_1, \dots, a_\nu\}$ è finito, quindi limitato. Sia $A = \min\{a_1, \dots, a_\nu, a_{h_0}-1\}$ e $B = \max\{a_1, \dots, a_\nu, a_{h_0}+1\}$. Allora $A \le a_k \le B$ per ogni $k \in \mathbb{N}$, dimostrando che l'intera successione è limitata.

3.  **(Lemma 2) Se una successione di Cauchy ammette una successione estratta $(a_{n_k})$ convergente a $L$, allora l'intera successione $(a_n)$ converge a $L$.**
    *Dimostrazione:* Fissato $\epsilon > 0$.
    * Poiché $(a_n)$ è di Cauchy, $\exists \nu_1$ t.c. $\forall h, k > \nu_1$, $|a_h - a_k| < \epsilon/2$.
    * Poiché $\lim_{k \to \infty} a_{n_k} = L$, $\exists k_0$ t.c. $\forall k > k_0$, $|a_{n_k} - L| < \epsilon/2$.
    Possiamo scegliere $k_0$ abbastanza grande in modo che $n_{k_0} > \nu_1$ (questo è possibile perché $n_k \to \infty$ per $k \to \infty$).
    Sia $\nu = n_{k_0}$. Consideriamo un qualsiasi $n > \nu = n_{k_0}$. Poiché $n > \nu_1$ e $n_{k_0} > \nu_1$, vale la condizione di Cauchy: $|a_n - a_{n_{k_0}}| < \epsilon/2$. Inoltre, essendo $k_0 > k_0$ non è vero, ma basta prendere $k' = k_0 + 1 > k_0$, allora $|a_{n_{k'}} - L| < \epsilon/2$. Usiamo $n_{k_0}$ come indice "ponte". Per $n > \nu = n_{k_0} > \nu_1$:
    $$|a_n - L| = |a_n - a_{n_{k_0}} + a_{n_{k_0}} - L| \le |a_n - a_{n_{k_0}}| + |a_{n_{k_0}} - L|$$
    Il primo termine è $< \epsilon/2$ per la proprietà di Cauchy (poiché $n > n_{k_0} > \nu_1$). Il secondo termine è $< \epsilon/2$ per la convergenza dell'estratta (poiché $k_0$ è stato scelto opportunamente).
    $$< \frac{\epsilon}{2} + \frac{\epsilon}{2} = \epsilon$$
    Questo dimostra che $\lim_{n \to \infty} a_n = L$.

4.  **(⇐) Ogni successione di Cauchy è convergente.**
    *Dimostrazione:* Sia $(a_n)$ una successione di Cauchy.
    * Per il Lemma 1, $(a_n)$ è limitata.
    * Per il [[15 - Teoremi Fondamentali dei Limiti di Successioni#Teorema di Bolzano-Weierstrass|Teorema di Bolzano-Weierstrass]], essendo limitata, $(a_n)$ ammette almeno una successione estratta $(a_{n_k})$ convergente a un limite $L$.
    * Per il Lemma 2, poiché $(a_n)$ è di Cauchy e ammette un'estratta convergente a $L$, l'intera successione $(a_n)$ converge a $L$.

Questo completa la dimostrazione dell'equivalenza tra convergenza e proprietà di Cauchy in $\mathbb{R}$.

---
## Valori di Aderenza

Un numero reale $A$ è detto **valore di aderenza** per una successione $(a_n)$ se è il limite di almeno una sua [[15 - Teoremi Fondamentali dei Limiti di Successioni#Successioni Estratte (Sottosuccessioni)|successione estratta]]. Formalmente, $A$ è un valore di aderenza se per ogni $\epsilon > 0$, l'insieme $\{n \in \mathbb{N} : |a_n - A| < \epsilon\}$ è **infinito**.

L'insieme dei valori di aderenza di una successione coincide con l'insieme dei limiti di tutte le sue possibili sottosuccessioni convergenti.

* Se una successione $(a_n)$ **converge** ad $A$, allora $A$ è il suo **unico** valore di aderenza (poiché tutte le estratte convergono ad $A$).
* Una successione **non convergente** può avere **più valori di aderenza** o nessuno (se non è limitata). Ad esempio, per $a_n = (-1)^n$, i valori di aderenza sono $1$ (limite dell'estratta dei pari) e $-1$ (limite dell'estratta dei dispari).
* Una successione **limitata** ammette sempre almeno un valore di aderenza (conseguenza del Teorema di Bolzano-Weierstrass).