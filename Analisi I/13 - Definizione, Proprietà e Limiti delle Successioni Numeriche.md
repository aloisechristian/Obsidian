## Introduzione alle Successioni Numeriche

### Definizione di Successione
Una successione numerica è una legge che associa ad ogni numero naturale $n \in \mathbb{N}$ uno e un solo numero reale. Formalmente, una successione è una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] $a: \mathbb{N} \to \mathbb{R}$.

Il valore che la successione assume in corrispondenza di $n$ si denota con $a_n$ e viene chiamato *termine n-esimo* della successione. L'intera successione si indica con $(a_n)_{n \in \mathbb{N}}$ o semplicemente con $a_n$.

Ad ogni indice naturale corrisponde un termine reale:
- Per $n=1$, si ha il termine $a_1 \in \mathbb{R}$.
- Per $n=2$, si ha il termine $a_2 \in \mathbb{R}$.
- Per $n=3$, si ha il termine $a_3 \in \mathbb{R}$.
- E così via, per ogni $n \in \mathbb{N}$, si ha un termine $a_n \in \mathbb{R}$.

Il [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|dominio]] della successione è l'insieme dei numeri naturali $\mathbb{N}$, che è un insieme infinito e ordinato. Questo implica che per ogni termine $a_n$ esiste sempre un termine successivo $a_{n+1}$. È possibile definire una successione anche se non sono definiti i primi termini, ovvero se il dominio è un sottoinsieme di $\mathbb{N}$ del tipo $\{n \in \mathbb{N} : n \ge n_0\}$ per un certo $n_0$.

## Proprietà delle Successioni

Essendo le successioni un caso particolare di funzioni, molte delle definizioni e proprietà viste per le funzioni, come la [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Estensione dei Concetti alle Funzioni Reali|limitatezza]] e la [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|monotonia]], si applicano anche ad esse.

### Successioni Limitate
Una successione si dice **limitata superiormente**, **limitata inferiormente** o **limitata** se il suo [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|codominio]] (l'insieme dei suoi termini) possiede la rispettiva proprietà, come definito in [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Maggioranti, Minoranti e Insiemi Limitati|questa nota]].

- **Limitata superiormente**: Esiste un numero reale $L$ (un [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#^857746|maggiorante]]) tale che $a_n \le L$ per ogni $n \in \mathbb{N}$.
- **Limitata inferiormente**: Esiste un numero reale $l$ (un [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#^d4db6f|minorante]]) tale che $a_n \ge l$ per ogni $n \in \mathbb{N}$.
- **Limitata**: La successione è sia limitata superiormente che inferiormente. Ciò è equivalente a dire che esistono $l, L \in \mathbb{R}$ tali che $l \le a_n \le L$ per ogni $n \in \mathbb{N}$.

Una condizione equivalente per la limitatezza è l'esistenza di una costante positiva $L_1$ tale che $|a_n| \le L_1$ per ogni $n \in \mathbb{N}$. Infatti, se $l \le a_n \le L$, si può scegliere $L_1 = \max\{|l|, |L|\}$, da cui segue che $-L_1 \le a_n \le L_1$, ovvero $|a_n| \le L_1$.

### Successioni Monotòne
L'ordinamento naturale del dominio $\mathbb{N}$ semplifica la definizione di [[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|monotonia]]. È sufficiente confrontare ogni termine con il suo successivo.
- **Crescente**: $a_n \le a_{n+1}$ per ogni $n \in \mathbb{N}$.
- **Strettamente crescente**: $a_n < a_{n+1}$ per ogni $n \in \mathbb{N}$.
- **Decrescente**: $a_n \ge a_{n+1}$ per ogni $n \in \mathbb{N}$.
- **Strettamente decrescente**: $a_n > a_{n+1}$ per ogni $n \in \mathbb{N}$.

## Esempi di Successioni

1.  **$a_n = \frac{1}{n}$**: I suoi termini sono $1, \frac{1}{2}, \frac{1}{3}, \frac{1}{4}, \dots$. Poiché per ogni $n \in \mathbb{N}$ si ha $n < n+1$, ne consegue che $\frac{1}{n} > \frac{1}{n+1}$, cioè $a_n > a_{n+1}$. La successione è dunque **strettamente decrescente**. È anche limitata, poiché $0 < a_n \le 1$.

2.  **$a_n = \frac{n-1}{n} = 1 - \frac{1}{n}$**: I suoi termini sono $0, \frac{1}{2}, \frac{2}{3}, \frac{3}{4}, \dots$. Questa successione è **strettamente crescente** e **limitata** ($0 \le a_n < 1$).

3.  **$a_n = \frac{(-1)^n}{n}$**: I termini sono $-1, \frac{1}{2}, -\frac{1}{3}, \frac{1}{4}, \dots$. È una successione a termini di segno alterno. Non è monotòna, ma è limitata.

4.  **$a_n = (-1)^n$**: I termini sono $-1, 1, -1, 1, \dots$. La successione assume solo i valori $-1$ e $1$. È limitata ma non monotòna.

5.  **$a_n = n^2$**: I termini sono $1, 4, 9, 16, \dots$. È una successione **strettamente crescente** e limitata inferiormente (da 1), ma non superiormente.

## Limite di una Successione

L'analisi delle successioni si concentra sul loro comportamento per valori di $n$ molto grandi, ovvero "all'infinito".

### Concetto Intuitivo di Limite
Dire che un numero reale $a$ è il limite di una successione $a_n$ significa che, a partire da un certo indice in poi, tutti i termini della successione diventano arbitrariamente "vicini" ad $a$.

### Definizione Formale di Limite Finito (Successione Convergente)
Si dice che la successione $a_n$ converge al limite $a \in \mathbb{R}$, e si scrive
$$\lim_{n \to +\infty} a_n = a \quad \text{oppure} \quad a_n \to a$$
se, per ogni numero reale $\epsilon > 0$ (arbitrariamente piccolo), esiste un indice $\nu \in \mathbb{N}$ (dipendente da $\epsilon$) tale che per ogni $n > \nu$ si abbia:
$$|a_n - a| < \epsilon$$
L'indice $\nu$ dipende generalmente dalla scelta di $\epsilon$. La condizione $|a_n - a| < \epsilon$ è equivalente a $a - \epsilon < a_n < a + \epsilon$. Geometricamente, significa che per ogni intervallo $(a - \epsilon, a + \epsilon)$ centrato in $a$, i termini della successione, da un certo punto in poi, cadono tutti all'interno di tale intervallo.

## Applicazione della Definizione di Limite

### Esempio 1: Verifica di $\lim_{n \to +\infty} \frac{1}{n} = 0$
Si vuole dimostrare che $a_n = \frac{1}{n}$ tende a $0$. Si deve verificare che per ogni $\epsilon > 0$ esiste un $\nu$ tale che per $n > \nu$ si ha $|\frac{1}{n} - 0| < \epsilon$.
La disuguaglianza diventa:
$$|\frac{1}{n}| < \epsilon \implies \frac{1}{n} < \epsilon$$
poiché $n > 0$. Risolvendo rispetto a $n$, si ottiene:
$$n > \frac{1}{\epsilon}$$
Basta quindi scegliere un indice $\nu$ tale che $\nu \ge \frac{1}{\epsilon}$. Ad esempio, si può prendere $\nu = \lfloor \frac{1}{\epsilon} \rfloor + 1$. Per ogni $n > \nu$, la condizione sarà soddisfatta, il che dimostra la convergenza a 0.

### Esempio 2: Dimostrazione per Assurdo che $\lim_{n \to +\infty} \frac{1}{n} \neq 1$
Si ipotizzi per assurdo che $a_n = \frac{1}{n}$ converga a 1. Dalla definizione, per ogni $\epsilon > 0$ dovrebbe esistere un $\nu$ tale che per $n > \nu$ si abbia $|\frac{1}{n} - 1| < \epsilon$.
Poiché $0 < \frac{1}{n} \le 1$ per $n \ge 1$, la quantità $\frac{1}{n} - 1$ è non positiva. Quindi $|\frac{1}{n} - 1| = -(\frac{1}{n} - 1) = 1 - \frac{1}{n}$. La disuguaglianza è:
$$1 - \frac{1}{n} < \epsilon \implies 1 - \epsilon < \frac{1}{n} \implies n < \frac{1}{1-\epsilon}$$
La definizione di limite richiede che questa relazione valga per *ogni* $\epsilon > 0$. Scegliamo un $\epsilon$ piccolo, ad esempio $\epsilon = \frac{1}{2}$. La disuguaglianza diventa:
$$n < \frac{1}{1 - 1/2} \implies n < 2$$
Questa condizione è soddisfatta solo per $n=1$, ma non "da un certo indice in poi" (cioè per tutti gli $n$ sufficientemente grandi). Ciò contraddice la definizione di limite. L'ipotesi iniziale è quindi falsa.

## Unicità del Limite

### Teorema di Unicità del Limite
Se una successione ammette limite, tale limite è unico.

### Dimostrazione
Si supponga per assurdo che una successione $a_n$ abbia due limiti distinti, $a$ e $b$, con $a \neq b$.
$$a_n \to a \quad \text{e} \quad a_n \to b$$
Poiché $a \neq b$, la quantità $|a-b|$ è strettamente positiva. Si scelga $\epsilon = \frac{|a-b|}{2} > 0$.
Per la definizione di limite, esistono $\nu_1, \nu_2 \in \mathbb{N}$ tali che:
1. Per ogni $n > \nu_1$, $|a_n - a| < \epsilon$.
2. Per ogni $n > \nu_2$, $|a_n - b| < \epsilon$.
Sia $\nu = \max\{\nu_1, \nu_2\}$. Per ogni $n > \nu$, entrambe le disuguaglianze sono vere. Consideriamo la quantità $|a-b|$ e applichiamo la [[06 - Studio delle Funzioni Valore Assoluto e Potenza#La Disuguaglianza Triangolare|disuguaglianza triangolare]]:
$$\begin{aligned} |a-b| &= |a - a_n + a_n - b| \\ &\le |a - a_n| + |a_n - b| \\ &= |a_n - a| + |a_n - b| \\ &< \epsilon + \epsilon = 2\epsilon \end{aligned}$$
Sostituendo il valore scelto per $\epsilon$:
$$|a-b| < 2 \left( \frac{|a-b|}{2} \right) = |a-b|$$
Si ottiene la contraddizione $|a-b| < |a-b|$. Pertanto, l'ipotesi che esistano due limiti distinti è falsa.
^
> [!NOTE] Nota sulla tecnica dimostrativa
> Questa è una classica [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|dimostrazione per assurdo]].

## Successioni Divergenti e Irregolari

### Successioni Divergenti
- Si dice che $a_n$ **diverge positivamente** (o tende a $+\infty$), e si scrive $\lim_{n \to +\infty} a_n = +\infty$, se per ogni numero reale $M > 0$ (arbitrariamente grande) esiste un indice $\nu \in \mathbb{N}$ tale che per ogni $n > \nu$ si ha $a_n > M$.
- Si dice che $a_n$ **diverge negativamente** (o tende a $-\infty$), e si scrive $\lim_{n \to +\infty} a_n = -\infty$, se per ogni numero reale $M > 0$ esiste un indice $\nu \in \mathbb{N}$ tale che per ogni $n > \nu$ si ha $a_n < -M$.

### Classificazione: Successioni Regolari e Irregolari
- Una successione si dice **regolare** se ammette limite, finito (convergente) o infinito (divergente).
- Una successione che non ammette limite si dice **irregolare** o **indeterminata**.

### Esempio di Successione Irregolare: $a_n = (-1)^n$
Si dimostra che questa successione non ammette limite. Supponiamo per assurdo che esista un limite $a \in \mathbb{R}$.
- **Caso 1: $a \ge 0$**. Per gli indici $n$ dispari, $a_n = -1$. La distanza dal limite è $|a_n - a| = |-1 - a| = 1+a \ge 1$. Questa distanza non può essere resa arbitrariamente piccola (es. minore di $\epsilon = 1/2$), contraddicendo la definizione di limite.
- **Caso 2: $a < 0$**. Per gli indici $n$ pari, $a_n = 1$. La distanza è $|a_n - a| = |1 - a| = 1-a > 1$. Anche in questo caso si giunge a una contraddizione.
Poiché nessun valore reale $a$ può essere il limite, la successione non converge. Essendo limitata, non può nemmeno divergere. È quindi irregolare.

### Terminologia Aggiuntiva
- Una successione che converge a 0 si dice **infinitesima**.
- Una successione che diverge (a $+\infty$ o $-\infty$) si dice **infinita**.

## Appendice: Richiami sui Numeri Complessi

Dato un [[11 - Numeri Complessi, Forma Algebrica, Trigonometrica e Operazioni|numero complesso]] $z$, possiamo rappresentarlo in diverse forme.

### Forma Algebrica e Coniugato
La **forma algebrica** è $z = x+iy$, con $x,y \in \mathbb{R}$.
- $x = \text{Re}(z)$ è la **parte reale**.
- $y = \text{Im}(z)$ è il **coefficiente dell'immaginario**.
Il **coniugato** di $z$ è $\bar{z} = x-iy$.

### Modulo e Argomento
Il **modulo** di $z$ è un numero reale non negativo che rappresenta la sua distanza dall'origine nel piano di Gauss:
$$|z| = \sqrt{x^2+y^2} = \sqrt{z \cdot \bar{z}}$$
L'**argomento** $\theta$ è l'angolo formato dal semiasse reale positivo e il vettore che rappresenta $z$.

### Forma Trigonometrica ed Esponenziale
La **forma trigonometrica** lega modulo e argomento alle coordinate cartesiane:
$$z = |z|(\cos\theta + i\sin\theta)$$
Usando la formula di Eulero, $e^{i\theta} = \cos\theta + i\sin\theta$, si ottiene la **forma esponenziale**:
$$z = |z|e^{i\theta}$$
Questa forma è estremamente utile per le operazioni di prodotto, quoziente e potenza.

- **Prodotto**: $z_1 \cdot z_2 = |z_1||z_2| e^{i(\theta_1+\theta_2)}$
- **Quoziente**: $\frac{z_1}{z_2} = \frac{|z_1|}{|z_2|} e^{i(\theta_1-\theta_2)}$
- **Potenza (Formula di De Moivre)**: $z^n = |z|^n e^{in\theta} = |z|^n (\cos(n\theta) + i\sin(n\theta))$

### Radici n-esime di un Numero Complesso
Un numero complesso non nullo $z = |z|e^{i\theta}$ ammette esattamente $n$ [[12 - Radici dei Numeri Complessi|radici n-esime]] distinte, date dalla formula:
$$\omega_k = \sqrt[n]{|z|} \left( \cos\left(\frac{\theta+2k\pi}{n}\right) + i\sin\left(\frac{\theta+2k\pi}{n}\right) \right)$$
per $k = 0, 1, 2, \dots, n-1$. Geometricamente, queste radici sono i vertici di un poligono regolare di $n$ lati inscritto in una circonferenza di raggio $\sqrt[n]{|z|}$.