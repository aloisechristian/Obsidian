## Introduzione alle Successioni Numeriche

### Definizione e Notazione
Una **successione numerica** è una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] che associa ad ogni numero naturale $n \in \mathbb{N}$ un numero reale. Formalmente, è una funzione $f: \mathbb{N} \to \mathbb{R}$.
L'immagine di un numero naturale $n$ viene indicata con $a_n$ anziché $f(n)$ e viene chiamata *termine n-esimo* della successione. La successione stessa è denotata come $(a_n)_{n \in \mathbb{N}}$ o semplicemente $(a_n)$.

Il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|dominio]] della successione è l'insieme dei numeri naturali $\mathbb{N} = \{1, 2, 3, \dots \}$, e il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|codominio]] è l'insieme dei numeri reali $\mathbb{R}$. L'insieme dei valori assunti, $\{a_1, a_2, a_3, \dots, a_n, \dots\}$, costituisce l'**immagine** della funzione.

### Successioni Limitate
Le definizioni di limitatezza per gli [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Definizioni per Sottoinsiemi di R|insiemi]] e le [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Funzioni Limitate e Illimitate|funzioni]] si applicano direttamente alle successioni, considerando la loro immagine.
- **Limitata superiormente**: Una successione $(a_n)$ si dice limitata superiormente se la sua immagine è [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Maggioranti, Minoranti e Insiemi Limitati|limitata superiormente]], ovvero se esiste un $M \in \mathbb{R}$ (un **maggiorante**) tale che $a_n \le M$ per ogni $n \in \mathbb{N}$.
- **Limitata inferiormente**: Una successione $(a_n)$ si dice limitata inferiormente se la sua immagine è [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Maggioranti, Minoranti e Insiemi Limitati|limitata inferiormente]], ovvero se esiste un $m \in \mathbb{R}$ (un **minorante**) tale che $a_n \ge m$ per ogni $n \in \mathbb{N}$.
- **Limitata**: Una successione si dice limitata se è sia limitata superiormente che inferiormente. Ciò è equivalente a dire che esiste un $M > 0$ tale che $|a_n| \le M$ per ogni $n \in \mathbb{N}$.

### Esempi di Successioni
- $a_n = \frac{1}{n}$: È una successione strettamente decrescente (1, 1/2, 1/3, ...). È limitata, con $\inf a_n = 0$ e $\sup a_n = \max a_n = 1$.
- $a_n = \frac{n-1}{n}$: È una successione strettamente crescente (0, 1/2, 2/3, ...). È limitata, con $\inf a_n = \min a_n = 0$ e $\sup a_n = 1$.
- $a_n = \frac{(-1)^n}{n}$: Presenta un'alternanza di segni (-1, 1/2, -1/3, ...). È limitata, con $\inf a_n = \min a_n = -1$ e $\sup a_n = \max a_n = 1/2$.
- $a_n = (-1)^n$: Il suo codominio è l'insieme $\{-1, 1\}$. È limitata.
- $a_n = n^2$: È una successione strettamente crescente (1, 4, 9, ...). È limitata inferiormente ma non superiormente.

## Limite di una Successione

Poiché il dominio $\mathbb{N}$ non è limitato superiormente, non è possibile determinare un "ultimo termine" di una successione. Ci si interroga quindi sul comportamento dei termini $a_n$ quando $n$ assume valori molto grandi, ovvero per $n \to +\infty$. Questo concetto è formalizzato dalla nozione di limite.

### Definizione di Limite Finito (Convergenza)
Si dice che la successione $(a_n)$ **converge** al limite $A \in \mathbb{R}$, e si scrive
$$\lim_{n \to +\infty} a_n = A$$
se, per ogni numero reale $\epsilon > 0$, esiste un indice $\nu \in \mathbb{N}$ tale che per ogni $n > \nu$ si ha:
$$|a_n - A| < \epsilon$$
Questa condizione significa che, fissato un **intorno** di $A$ di raggio $\epsilon$ arbitrariamente piccolo, l'intervallo $(A - \epsilon, A + \epsilon)$, tutti i termini della successione, da un certo indice $\nu$ in poi (ovvero *definitivamente*), cadono all'interno di tale intorno. L'indice $\nu$ dipende dalla scelta di $\epsilon$; in generale, più piccolo è $\epsilon$, più grande dovrà essere $\nu$.

*Nota*: La condizione $|a_n - A| < \epsilon$ può essere sostituita da $|a_n - A| < C\epsilon$ per una qualsiasi costante $C > 0$, data l'arbitrarietà di $\epsilon$.

### Esempio: Verifica di un Limite
Si può dimostrare che $\lim_{n \to +\infty} \frac{1}{n} = 0$. Intuitivamente, al crescere di $n$, i termini si avvicinano a zero. Formalmente, fissato $\epsilon > 0$, si cerca $\nu$ tale che per $n > \nu$ sia $|\frac{1}{n} - 0| < \epsilon$, ovvero $\frac{1}{n} < \epsilon$, che equivale a $n > \frac{1}{\epsilon}$. Basta quindi scegliere $\nu$ come un qualsiasi numero naturale maggiore di $\frac{1}{\epsilon}$.

## Proprietà dei Limiti

### Teorema di Unicità del Limite
Se una successione $(a_n)$ ammette limite, tale limite è unico.

**Dimostrazione:** La tecnica utilizzata è una [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|dimostrazione per assurdo]].
Si supponga per assurdo che la successione $(a_n)$ ammetta due limiti distinti, $A$ e $B$, con $A \neq B$. Si scelga $\epsilon = \frac{|A - B|}{2} > 0$. Per la definizione di limite, esistono due indici $\nu_1$ e $\nu_2$ tali che:
- $\forall n > \nu_1, |a_n - A| < \epsilon \iff A - \epsilon < a_n < A + \epsilon$
- $\forall n > \nu_2, |a_n - B| < \epsilon \iff B - \epsilon < a_n < B + \epsilon$

Sia $\nu = \max(\{\nu_1, \nu_2\})$. Per ogni $n > \nu$, entrambe le proprietà sono valide. Gli intorni di $A$ e $B$ scelti sono disgiunti. Utilizzando la disuguaglianza triangolare, si ha:
$$|A - B| = |A - a_n + a_n - B| \le |A - a_n| + |a_n - B| < \epsilon + \epsilon = 2\epsilon$$
Sostituendo il valore scelto per $\epsilon$, si ottiene:
$$|A - B| < 2 \left( \frac{|A - B|}{2} \right) = |A - B|$$
Si giunge così all'assurdo $|A - B| < |A - B|$, che dimostra l'unicità del limite.

### Relazione tra Convergenza e Limitatezza
**Teorema**: Ogni successione convergente è limitata.

**Dimostrazione**: Sia $(a_n)$ una successione convergente a un limite $A$. Per la definizione di limite, fissando $\epsilon = 1$, esiste un indice $\nu$ tale che per ogni $n > \nu$, $|a_n - A| < 1$. Dalla disuguaglianza triangolare, per $n > \nu$ si ha:
$$|a_n| = |a_n - A + A| \le |a_n - A| + |A| < 1 + |A|$$
Questo dimostra che i termini della successione dall'indice $\nu+1$ in poi (la *coda* della successione) sono limitati. Per limitare l'intera successione, si considerano anche i primi $\nu$ termini, $\{|a_1|, |a_2|, \dots, |a_\nu|\}$, che sono in numero finito.
Sia $M = \max(\{|a_1|, |a_2|, \dots, |a_\nu|, 1 + |A|\})$. Allora per ogni $n \in \mathbb{N}$, si ha $|a_n| \le M$, il che dimostra che la successione è limitata.

*Nota*: Il viceversa non è vero. Una successione può essere limitata ma non convergente. L'esempio classico è $a_n = (-1)^n$, che è limitata (i suoi valori sono -1 e 1), ma non ammette limite.

### Algebra dei Limiti
Siano $(a_n)$ e $(b_n)$ due successioni convergenti, con $\lim_{n \to +\infty} a_n = A$ e $\lim_{n \to +\infty} b_n = B$. Valgono le seguenti proprietà:
- **Somma**: $\lim_{n \to +\infty} (a_n + b_n) = A + B$
- **Differenza**: $\lim_{n \to +\infty} (a_n - b_n) = A - B$
- **Prodotto**: $\lim_{n \to +\infty} (a_n \cdot b_n) = A \cdot B$
- **Quoziente**: Se $B \neq 0$ e $b_n \neq 0$ per ogni $n$ (o da un certo indice in poi), allora $\lim_{n \to +\infty} \frac{a_n}{b_n} = \frac{A}{B}$

## Successioni Divergenti e Forme Indeterminate

### Definizioni di Divergenza
- **Divergenza a $+\infty$**: Si dice che $(a_n)$ diverge positivamente se per ogni $M > 0$ (arbitrariamente grande) esiste un indice $\nu$ tale che per ogni $n > \nu$, $a_n > M$. Si scrive $\lim_{n \to +\infty} a_n = +\infty$.
- **Divergenza a $-\infty$**: Si dice che $(a_n)$ diverge negativamente se per ogni $M > 0$ esiste un indice $\nu$ tale che per ogni $n > \nu$, $a_n < -M$. Si scrive $\lim_{n \to +\infty} a_n = -\infty$.

### Successioni Regolari e Non Regolari
- Una successione si dice **regolare** se ammette limite, finito (convergente) o infinito (divergente).
- Una successione si dice **non regolare** (o indeterminata o oscillante) se non ammette limite. Esempio: $a_n = (-1)^n$.

Una successione che tende a 0 si dice **infinitesima**. Una successione che diverge si dice **infinita**.

### Forme Indeterminate
L'algebra dei limiti non copre tutte le situazioni, in particolare quando si combinano successioni divergenti o infinitesime. Le seguenti forme sono dette **indeterminate**, poiché il risultato del limite non può essere stabilito a priori e richiede un'analisi caso per caso:
- $\infty - \infty$
- $0 \cdot \infty$
- $\frac{\infty}{\infty}$
- $\frac{0}{0}$
- $1^\infty$
- $0^0$
- $\infty^0$

## Teoremi di Confronto e Permanenza del Segno

### Teorema della Permanenza del Segno
Se $\lim_{n \to +\infty} a_n = A$ con $A > 0$, allora esiste un indice $\nu$ tale che per ogni $n > \nu$, si ha $a_n > 0$. In altre parole, se una successione converge a un valore positivo, i suoi termini sono definitivamente positivi.

**Dimostrazione**: Si sceglie $\epsilon = A/2 > 0$. Per la definizione di limite, esiste $\nu$ tale che per $n > \nu$, $|a_n - A| < A/2$, ovvero $A - A/2 < a_n < A + A/2$. In particolare, $a_n > A/2 > 0$.

**Corollario 1**: Se $a_n \ge 0$ per ogni $n$ e $\lim_{n \to +\infty} a_n = A$, allora $A \ge 0$.
**Corollario 2 (Confronto fra due successioni)**: Se $a_n \ge b_n$ per ogni $n$ (o da un certo indice in poi) e i limiti esistono, allora $\lim a_n \ge \lim b_n$.

### Teorema dei Carabinieri (o del Confronto)
Siano $(a_n)$, $(b_n)$, e $(c_n)$ tre successioni. Se:
1. $a_n \le c_n \le b_n$ per ogni $n$ (o da un certo indice in poi).
2. $\lim_{n \to +\infty} a_n = \lim_{n \to +\infty} b_n = L$.

Allora anche $\lim_{n \to +\infty} c_n = L$.

### Teorema del Confronto per Successioni Divergenti
Siano $(a_n)$ e $(b_n)$ due successioni tali che $a_n \le b_n$ per ogni $n$.
- Se $\lim_{n \to +\infty} a_n = +\infty$, allora $\lim_{n \to +\infty} b_n = +\infty$.
- Se $\lim_{n \to +\infty} b_n = -\infty$, allora $\lim_{n \to +\infty} a_n = -\infty$.

## Limiti Notevoli

### Limite della Successione Geometrica $a^n$
Il comportamento del limite $\lim_{n \to +\infty} a^n$ dipende dal valore della base $a$.
- Se $a > 1$: $\lim_{n \to +\infty} a^n = +\infty$. (Dimostrato usando la disuguaglianza di Bernoulli).
- Se $a = 1$: $\lim_{n \to +\infty} 1^n = 1$.
- Se $|a| < 1$: $\lim_{n \to +\infty} a^n = 0$. (Dimostrato considerando il reciproco $1/|a| > 1$).
- Se $a \le -1$: Il limite non esiste (la successione è indeterminata).

### Limiti con Radici
- Se $a > 0$, $\lim_{n \to +\infty} \sqrt[n]{a} = 1$.
- Per ogni $b \in \mathbb{R}$, $\lim_{n \to +\infty} \sqrt[n]{n^b} = 1$.

### Limiti Trigonometrici Notevoli
Sia $(a_n)$ una successione tale che $\lim_{n \to +\infty} a_n = 0$.
1. $\lim_{n \to +\infty} \sin(a_n) = 0$
2. $\lim_{n \to +\infty} \cos(a_n) = 1$
3. $\lim_{n \to +\infty} \frac{\sin(a_n)}{a_n} = 1$

### Prodotto di una Successione Limitata per una Infinitesima
Se $(a_n)$ è una successione limitata e $(b_n)$ è una successione infinitesima (cioè $\lim b_n = 0$), allora il loro prodotto è una successione infinitesima:
$$\lim_{n \to +\infty} (a_n \cdot b_n) = 0$$
Esempio: $\lim_{n \to +\infty} \frac{\sin(n)}{n} = 0$, poiché $\sin(n)$ è limitata ($|\sin(n)| \le 1$) e $\frac{1}{n}$ è infinitesima.

## Successioni Monotone

### Definizioni
Una successione $(a_n)$ si dice **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|monotona]]** se rientra in uno di questi quattro casi:
- **crescente** se $a_n \le a_{n+1}$ per ogni $n$.
- **strettamente crescente** se $a_n < a_{n+1}$ per ogni $n$.
- **decrescente** se $a_n \ge a_{n+1}$ per ogni $n$.
- **strettamente decrescente** se $a_n > a_{n+1}$ per ogni $n$.

### Teorema di Regolarità delle Successioni Monotone
**Ogni successione monotona è regolare**, cioè ammette sempre limite (finito o infinito).

In particolare, si distinguono due casi:

1.  **Successione monotona e limitata**: Se una successione $(a_n)$ è monotona e limitata, allora è **convergente**. 
    - Se $(a_n)$ è crescente e limitata, allora $\lim_{n \to +\infty} a_n = \sup \{a_n : n \in \mathbb{N}\}$.
    - Se $(a_n)$ è decrescente e limitata, allora $\lim_{n \to +\infty} a_n = \inf \{a_n : n \in \mathbb{N}\}$.

2.  **Successione monotona e non limitata**: Se una successione $(a_n)$ è monotona e non limitata, allora è **divergente**.
    - Se $(a_n)$ è crescente e non limitata superiormente, allora $\lim_{n \to +\infty} a_n = +\infty$.
    - Se $(a_n)$ è decrescente e non limitata inferiormente, allora $\lim_{n \to +\infty} a_n = -\infty$.

**Dimostrazione (caso crescente e limitato)**: Sia $(a_n)$ crescente e limitata. Poiché l'insieme dei suoi valori, $A = \{a_n\}$, è non vuoto e limitato superiormente, per l'[[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|assioma di completezza]] ammette [[03 - Insiemi Numerici, Completezza e Estremo Superiore#4.2 Maggioranti, Minoranti, Estremo Superiore e Inferiore|estremo superiore]] $L = \sup A$. Per la definizione di `sup`, valgono due proprietà:
1. $a_n \le L$ per ogni $n$.
2. Per ogni $\epsilon > 0$, esiste un indice $\nu$ tale che $a_\nu > L - \epsilon$.

Dato che la successione è crescente, per ogni $n > \nu$ si ha $a_n \ge a_\nu$. Combinando le proprietà, per ogni $n > \nu$ si ha:
$$L - \epsilon < a_\nu \le a_n \le L < L + \epsilon$$
Questo implica che $L - \epsilon < a_n < L + \epsilon$, ovvero $|a_n - L| < \epsilon$ per ogni $n > \nu$. Questa è la definizione di limite, quindi $\lim_{n \to +\infty} a_n = L$.