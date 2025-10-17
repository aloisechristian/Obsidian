# Successioni Reali: Definizioni e Limiti

## Definizione di Successione Reale

Una successione reale è una [[Analisi I/01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] il cui dominio è l'insieme dei numeri naturali $\mathbb{N}$ e il cui codominio è l'insieme dei numeri reali $\mathbb{R}$. Formalmente, è un'applicazione $f: \mathbb{N} \to \mathbb{R}$.

Ad ogni numero naturale $n \in \mathbb{N}$, la funzione associa uno e un solo numero reale, indicato con $a_n$, che prende il nome di **termine n-esimo** della successione. L'intera successione viene denotata con $(a_n)_{n \in \mathbb{N}}$, o più semplicemente con $(a_n)$ o $\{a_n\}$.

### Proprietà delle Successioni: Limitatezza
Una successione $(a_n)$ si definisce:
- **Limitata superiormente**: se il suo codominio ammette un maggiorante, ovvero se esiste un numero reale $L$ tale che $a_n \le L$ per ogni $n \in \mathbb{N}$.
- **Limitata inferiormente**: se il suo codominio ammette un minorante, ovvero se esiste un numero reale $l$ tale che $a_n \ge l$ per ogni $n \in \mathbb{N}$.
- **Limitata**: se è sia limitata superiormente che inferiormente. Ciò è equivalente all'esistenza di una costante $M \ge 0$ tale che $|a_n| \le M$ per ogni $n \in \mathbb{N}$.

## Limite di una Successione

L'analisi delle successioni si concentra sul loro comportamento per valori di $n$ arbitrariamente grandi. Poiché l'insieme $\mathbb{N}$ è illimitato superiormente, non esiste un "ultimo termine" della successione. Si introduce quindi il concetto di **limite** per descrivere a quale valore i termini della successione si "avvicinano" al crescere di $n$.

### Definizione Formale di Limite Finito (Convergenza)
Si dice che la successione $(a_n)$ converge al limite finito $a \in \mathbb{R}$, e si scrive
$$\lim_{n \to +\infty} a_n = a$$
se, per ogni $\epsilon > 0$ (arbitrariamente piccolo), esiste un indice $\nu \in \mathbb{N}$ tale che per ogni $n > \nu$, la distanza tra $a_n$ e $a$ è minore di $\epsilon$. In simboli:
$$\forall \epsilon > 0, \exists \nu \in \mathbb{N} \text{ tale che } \forall n > \nu, \quad |a_n - a| < \epsilon$$
Questa condizione significa che, da un certo punto in poi (cioè per tutti gli indici $n$ maggiori di $\nu$), tutti i termini della successione cadono nell'intorno $(a - \epsilon, a + \epsilon)$ di $a$.

### Esempio: Verifica del Limite
Consideriamo la successione $a_n = \frac{1}{n}$. Intuitivamente, al crescere di $n$, i termini si avvicinano a 0. Verifichiamo formalmente che $\lim_{n \to +\infty} \frac{1}{n} = 0$.

Secondo la definizione, dobbiamo dimostrare che per ogni $\epsilon > 0$, esiste un $\nu$ tale che per $n > \nu$ si ha $|\frac{1}{n} - 0| < \epsilon$.
$$|\frac{1}{n}| < \epsilon \implies \frac{1}{n} < \epsilon \implies n > \frac{1}{\epsilon}$$
Scegliendo $\nu$ come la parte intera di $\frac{1}{\epsilon}$, ovvero $\nu = \lfloor \frac{1}{\epsilon} \rfloor$, la condizione è soddisfatta. Poiché per ogni $\epsilon > 0$ è possibile trovare un tale $\nu$, il limite è verificato.

### Teorema di Unicità del Limite
Se una successione ammette limite, tale limite è unico.

**Dimostrazione:** Si procede per assurdo. Supponiamo che $(a_n)$ converga a due limiti distinti $A$ e $B$, con $A \neq B$. Allora $|A - B| > 0$.
Scegliamo $\epsilon = \frac{|A - B|}{2} > 0$. Per definizione di limite:
1.  Esiste $\nu_1$ tale che per $n > \nu_1$, $|a_n - A| < \epsilon$.
2.  Esiste $\nu_2$ tale che per $n > \nu_2$, $|a_n - B| < \epsilon$.

Sia $\nu = \max(\{\nu_1, \nu_2\})$. Per ogni $n > \nu$, entrambe le condizioni sono verificate. Utilizzando la disuguaglianza triangolare:
$$|A - B| = |A - a_n + a_n - B| \le |A - a_n| + |a_n - B| < \epsilon + \epsilon = 2\epsilon$$
Sostituendo il valore scelto per $\epsilon$:
$$|A - B| < 2 \left( \frac{|A - B|}{2} \right) = |A - B|$$
Si giunge alla contraddizione $|A - B| < |A - B|$. L'ipotesi iniziale è dunque falsa e il limite deve essere unico.

## Classificazione delle Successioni

### Successioni Divergenti
Una successione $(a_n)$ si dice:
- **Divergente positivamente** (tende a $+\infty$) se per ogni $M > 0$, esiste un $\nu \in \mathbb{N}$ tale che $a_n > M$ per ogni $n > \nu$. Si scrive $\lim_{n \to +\infty} a_n = +\infty$.
- **Divergente negativamente** (tende a $-\infty$) se per ogni $M > 0$, esiste un $\nu \in \mathbb{N}$ tale che $a_n < -M$ per ogni $n > \nu$. Si scrive $\lim_{n \to +\infty} a_n = -\infty$.

### Successioni Regolari e Irregolari
- Una successione si dice **regolare** se ammette limite (finito o infinito).
- Una successione che non ammette limite si dice **non regolare** o **indeterminata** (o **oscillante**). Un esempio classico è la successione $a_n = (-1)^n$, i cui termini oscillano tra -1 e 1 senza avvicinarsi a un valore specifico.

### Terminologia
- Una successione che converge a 0 si dice **infinitesima**.
- Una successione che diverge a $+\infty$ o $-\infty$ si dice **infinita**.

## Relazione tra Convergenza e Limitatezza

Esiste una relazione unidirezionale tra i concetti di convergenza e limitatezza.

- **Una successione limitata non è necessariamente convergente.** Il controesempio è la successione $a_n = (-1)^n$, che è limitata (i suoi valori sono compresi tra -1 e 1) ma non ammette limite.
- **Teorema: Una successione convergente è sempre limitata.**

**Dimostrazione:**
Sia $(a_n)$ una successione convergente ad un limite finito $A$. Per definizione, fissato un $\epsilon > 0$ (ad esempio $\epsilon = 1$), esiste un indice $\nu$ tale che per ogni $n > \nu$ si ha $|a_n - A| < 1$.
Applicando la disuguaglianza triangolare, per $n > \nu$:
$$|a_n| = |a_n - A + A| \le |a_n - A| + |A| < 1 + |A|$$
Questo dimostra che i termini della successione sono limitati dall'indice $\nu$ in poi. I termini precedenti, $a_1, a_2, \dots, a_\nu$, sono in numero finito e quindi il loro insieme di valori assoluti $\{|a_1|, |a_2|, \dots, |a_\nu|\}$ ammette un massimo.
Possiamo quindi definire una costante $M$ che limita tutti i termini della successione:
$$M = \max \{ |a_1|, |a_2|, \dots, |a_\nu|, 1 + |A| \}$$
Per costruzione, si ha che $|a_n| \le M$ per ogni $n \in \mathbb{N}$, il che dimostra che la successione è limitata.

## Algebra dei Limiti

Siano $(a_n)$ e $(b_n)$ due successioni convergenti, con $\lim_{n \to +\infty} a_n = A$ e $\lim_{n \to +\infty} b_n = B$.

- **Limite della somma/differenza**: 
  $$\lim_{n \to +\infty} (a_n \pm b_n) = A \pm B$$
- **Limite del prodotto**:
  $$\lim_{n \to +\infty} (a_n \cdot b_n) = A \cdot B$$
  **Dimostrazione (prodotto):** Vogliamo dimostrare che $|a_n b_n - AB| \to 0$. Usiamo l'artificio di aggiungere e togliere il termine $a_n B$:
  $$|a_n b_n - AB| = |a_n b_n - a_n B + a_n B - AB| = |a_n(b_n - B) + B(a_n - A)|$$
  Per la disuguaglianza triangolare:
  $$\le |a_n(b_n - B)| + |B(a_n - A)| = |a_n| |b_n - B| + |B| |a_n - A|$$
  Poiché $(a_n)$ è convergente, è anche limitata, quindi $\exists M>0$ tale che $|a_n| \le M$. Inoltre, per definizione di limite, $|b_n - B| \to 0$ e $|a_n - A| \to 0$. Il termine $|B| |a_n - A|$ tende a zero. Il termine $|a_n| |b_n - B|$ è il prodotto di una successione limitata per una infinitesima, e quindi tende a zero. La somma di quantità che tendono a zero tende a zero, dimostrando la tesi.
- **Limite del quoziente**: Se $B \neq 0$ e $b_n \neq 0$ per ogni $n$, allora:
  $$\lim_{n \to +\infty} \frac{a_n}{b_n} = \frac{A}{B}$$

### Forme Indeterminate
Quando si opera con limiti infiniti, alcune combinazioni non producono un risultato immediato e sono definite **forme indeterminate**. Queste richiedono un'analisi più approfondita del caso specifico.
- **Somma**: $+\infty - \infty$
- **Prodotto**: $0 \cdot \infty$
- **Rapporto**: $\frac{\infty}{\infty}$, $\frac{0}{0}$
- **Potenza**: $1^\infty$, $0^0$, $\infty^0$

**Esempio:** Per calcolare il limite $\lim_{n \to +\infty} \frac{n^2 + 5n - 4}{3n^2 + 1}$ (forma $\frac{\infty}{\infty}$), si raccoglie il termine di grado massimo:
$$\lim_{n \to +\infty} \frac{n^2(1 + \frac{5}{n} - \frac{4}{n^2})}{n^2(3 + \frac{1}{n^2})} = \lim_{n \to +\infty} \frac{1 + \frac{5}{n} - \frac{4}{n^2}}{3 + \frac{1}{n^2}} = \frac{1+0-0}{3+0} = \frac{1}{3}$$

## Successioni Monotone

Una categoria importante di successioni è quella delle successioni monotone.
Una successione $(a_n)$ si dice:
- **Crescente**: se $a_n \le a_{n+1}$ per ogni $n \in \mathbb{N}$.
- **Decrescente**: se $a_n \ge a_{n+1}$ per ogni $n \in \mathbb{N}$.
- **Strettamente crescente/decrescente**: se valgono le disuguaglianze strette ($<, >$).
Una successione si dice **monotona** se è crescente o decrescente.

### Teorema di Convergenza delle Successioni Monotone
Questo teorema fondamentale stabilisce un legame potente tra monotonia, limitatezza e convergenza.
> **Una successione monotona ammette sempre limite (finito o infinito). Se la successione è anche limitata, allora il limite è finito (cioè la successione converge).**

In particolare:
- Se $(a_n)$ è crescente e limitata superiormente, allora $\lim_{n \to +\infty} a_n = \sup\{a_n\}$.
- Se $(a_n)$ è decrescente e limitata inferiormente, allora $\lim_{n \to +\infty} a_n = \inf\{a_n\}$.

Questo teorema garantisce la convergenza senza la necessità di conoscere a priori il valore del limite.

## Teoremi di Confronto

### Teorema della Permanenza del Segno
Se una successione $(a_n)$ converge a un limite $A > 0$, allora esiste un indice $\nu$ tale che $a_n > 0$ per ogni $n > \nu$.

**Dimostrazione:** Sia $A > 0$. Scegliamo $\epsilon = A/2 > 0$. Per definizione di limite, esiste $\nu$ tale che per $n > \nu$:
$$|a_n - A| < \epsilon \implies A - \epsilon < a_n < A + \epsilon$$
In particolare, $a_n > A - \epsilon = A - \frac{A}{2} = \frac{A}{2} > 0$, che dimostra la tesi.

**Corollario 1**: Se $a_n \ge 0$ per ogni $n$ e $\lim_{n \to +\infty} a_n = A$, allora $A \ge 0$.
**Corollario 2**: Se $a_n \ge b_n$ per ogni $n$ e le due successioni convergono rispettivamente ad $A$ e $B$, allora $A \ge B$.

### Teorema dei Carabinieri (o del Confronto)
Siano $(a_n)$, $(b_n)$, e $(c_n)$ tre successioni tali che $a_n \le c_n \le b_n$ per ogni $n$ (o almeno da un certo indice in poi). Se $\lim_{n \to +\infty} a_n = \lim_{n \to +\infty} b_n = A$, allora anche la successione centrale converge allo stesso limite:
$$\lim_{n \to +\infty} c_n = A$$

### Teoremi di Confronto per Successioni Divergenti
Sia $a_n \le b_n$ per ogni $n$.
- Se $\lim_{n \to +\infty} a_n = +\infty$, allora anche $\lim_{n \to +\infty} b_n = +\infty$.
- Se $\lim_{n \to +\infty} b_n = -\infty$, allora anche $\lim_{n \to +\infty} a_n = -\infty$.

## Proprietà delle Successioni Infinitesime

**Proposizione 1**: Una successione $(a_n)$ è infinitesima se e solo se la successione dei suoi valori assoluti $(|a_n|)$ è infinitesima.
$$\lim_{n \to +\infty} a_n = 0 \iff \lim_{n \to +\infty} |a_n| = 0$$

**Proposizione 2**: Il prodotto di una successione limitata per una successione infinitesima è una successione infinitesima.

**Dimostrazione:** Siano $(a_n)$ limitata e $(b_n)$ infinitesima.
- $(a_n)$ limitata $\implies \exists M > 0$ tale che $|a_n| \le M$ per ogni $n$.
- $(b_n)$ infinitesima $\implies \forall \epsilon > 0, \exists \nu$ tale che per $n > \nu$, $|b_n| < \frac{\epsilon}{M}$.

Vogliamo dimostrare che $\lim_{n \to +\infty} (a_n b_n) = 0$. Consideriamo il valore assoluto del prodotto per $n > \nu$:
$$|a_n b_n - 0| = |a_n| |b_n| \le M \cdot |b_n| < M \cdot \frac{\epsilon}{M} = \epsilon$$
Questo verifica la definizione di limite, dimostrando che il prodotto tende a 0.

Questo risultato è utile perché non richiede che la successione $(a_n)$ sia convergente. Ad esempio:
$$\lim_{n \to +\infty} \frac{\sin(n)}{n} = 0$$
poiché $(\sin(n))$ è una successione limitata (i suoi valori sono in $[-1, 1]$) e $\frac{1}{n}$ è una successione infinitesima.