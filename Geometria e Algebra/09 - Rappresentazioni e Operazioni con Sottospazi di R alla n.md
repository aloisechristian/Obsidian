# Rappresentazione di Sottospazi Vettoriali in $\mathbb{R}^n$

Un [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|sottospazio vettoriale]] $V$ di $\mathbb{R}^n$ può essere descritto principalmente in due forme: cartesiana e parametrica.

---

## Forma Cartesiana

Un sottospazio è in **forma cartesiana** quando è definito come l'insieme delle soluzioni di un [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Sistemi Omogenei e Struttura delle Soluzioni|sistema lineare omogeneo]]. Formalmente, $V$ è il [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Esempi di Sottospazi|nucleo (o kernel)]] di una matrice $A \in M_{m,n}(\mathbb{R})$, indicato come $V = \ker(A)$. I vettori $x \in V$ sono tutti e soli i vettori che soddisfano l'equazione matriciale $Ax = \mathbf{0}$. Questa rappresentazione descrive il sottospazio tramite le *condizioni* che i suoi vettori devono soddisfare.

---

## Forma Parametrica

Un sottospazio è in **forma parametrica** quando è definito come lo [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|spazio generato (span)]] da un insieme di vettori $\{v_1, v_2, \dots, v_k\}$. Formalmente, $V = \text{span}\{v_1, v_2, \dots, v_k\}$. Ogni vettore $v \in V$ può essere espresso come [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|combinazione lineare]] dei generatori: $v = c_1 v_1 + \dots + c_k v_k$, dove i $c_i$ sono i parametri.

Equivalentemente, può essere visto come lo spazio delle righe (**row space**) della matrice $B$ che ha per righe i vettori generatori, ovvero $V = \text{row}(B)$. Questa rappresentazione descrive il sottospazio *costruendo* i suoi vettori a partire dai generatori.

---

## Determinazione di una Base e Dimensione

Un obiettivo fondamentale è determinare una [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Base|base]] per un sottospazio dato, a prescindere dalla sua rappresentazione iniziale, per comprenderne la [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Dimensione|dimensione]].

### Da Forma Parametrica a Base

Se un sottospazio $V$ è dato in forma parametrica come $V = \text{span}\{v_1, \dots, v_m\}$, i vettori $v_i$ sono un insieme di generatori, ma non necessariamente una base (potrebbero non essere [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Indipendenza Lineare|linearmente indipendenti]]).

**Procedura**:
1.  Costruire una matrice $B$ le cui righe sono i vettori generatori $v_1, \dots, v_m$. Dunque $V = \text{row}(B)$.
2.  Applicare l'[[Algoritmo di Eliminazione di Gauss Jordan]] per ottenere una matrice a scala per righe (o ridotta) $B'$.
3.  Le righe non nulle di $B'$ costituiscono una base per $V$.

**Corollario:** La dimensione di $V$, $\dim(V)$, è pari al numero di righe non nulle, che corrisponde al [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]] della matrice $B$:
$$\dim(V) = \dim(\text{row}(B)) = \text{rank}(B)$$
In generale, $m$ vettori $v_1, \dots, v_m$ in $\mathbb{R}^n$ sono linearmente indipendenti se e solo se il rango della matrice che li ha per righe è uguale a $m$.

**Esempio:** Sia $V = \text{span}\{(1, -1, 2), (0, 0, 1), (1, 1, 1)\} \subseteq \mathbb{R}^3$. Costruiamo la matrice e applichiamo Gauss-Jordan:
$$B = \begin{pmatrix} 1 & -1 & 2 \\ 0 & 0 & 1 \\ 1 & 1 & 1 \end{pmatrix} \xrightarrow{\text{Gauss-Jordan}} B' = \begin{pmatrix} 1 & 0 & 3/2 \\ 0 & 1 & -1/2 \\ 0 & 0 & 0 \end{pmatrix}$$
(Nota: I passaggi esatti di Gauss-Jordan possono variare, portando a forme a scala diverse ma con lo stesso numero di righe non nulle. La forma a gradini ridotta è unica.)
Una base per $V$ è data dalle righe non nulle di $B'$, ad esempio $B_V = \{(1, 0, 3/2), (0, 1, -1/2)\}$. La dimensione di $V$ è $\dim(V) = \text{rank}(B) = 2$.
*(Nota: L'esempio nel testo originale arriva a una base diversa, $\{(1, 1, 0), (0, 0, 1)\}$, anch'essa valida.)*

---

### Da Forma Cartesiana a Base

Se un sottospazio $W$ è dato in forma cartesiana come $W = \ker(A)$, ovvero l'insieme delle soluzioni del sistema omogeneo $Ax=\mathbf{0}$, per trovare una base è sufficiente risolvere il sistema.

**Procedura**:
1.  Si considera la matrice $A$ (non è necessaria la matrice aumentata $[A|\mathbf{0}]$ poiché i termini noti rimangono nulli).
2.  Si applica l'[[Algoritmo di Eliminazione di Gauss Jordan]] per ridurre $A$ a una forma a scala $A'$.
3.  Si risolve il sistema $A'x=\mathbf{0}$, identificando le variabili dipendenti (corrispondenti ai pivot) e le variabili libere.
4.  Si scrive la soluzione generale in forma vettoriale, esprimendo le variabili dipendenti in funzione delle variabili libere (i parametri).
5.  I vettori che moltiplicano i parametri liberi nella soluzione generale formano una base per lo spazio delle soluzioni $W = \ker(A)$.

**Teorema Rango-Nullità:**
Il [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Il Teorema di Rouché-Capelli|teorema di Rouché-Capelli]] afferma che il numero di variabili libere in un sistema omogeneo $Ax=\mathbf{0}$ (con $A \in M_{m,n}$) è $n - \text{rank}(A)$. Poiché la dimensione del kernel è uguale al numero di vettori nella sua base (che corrisponde al numero di variabili libere), si ha:
$$\dim(\ker(A)) = n - \text{rank}(A)$$
Questa relazione è nota come **Teorema Rango-Nullità** (o Teorema della Dimensione). La dimensione del kernel, $\dim(\ker(A))$, è anche chiamata **nullità** di $A$ (nullity(A)). Il teorema afferma quindi che per una matrice $A$ di dimensioni $m \times n$:
$$\text{rank}(A) + \text{nullity}(A) = n$$

---

## Conversione tra Forme

È spesso necessario convertire la rappresentazione di un sottospazio da una forma all'altra.

### Da Cartesiana a Parametrica

Questo passaggio consiste semplicemente nel trovare una base per il sottospazio dato in forma cartesiana $W = \ker(A)$, seguendo la procedura descritta sopra. La soluzione generale, espressa in forma vettoriale in funzione dei parametri liberi, fornisce i generatori (che formano una base) per la forma parametrica $W = \text{span}\{w_1, \dots, w_k\}$.

### Da Parametrica a Cartesiana

Questo processo è meno diretto e sfrutta una proprietà di dualità. Vogliamo passare da $V = \text{row}(B)$ a $V = \ker(A)$.

**Proprietà:** Date due matrici $A$ e $B$ (con lo stesso numero di colonne), si ha che $\ker(A) = \text{row}(B)$ se e solo se $\ker(B) = \text{row}(A)$.

**Procedura**:
1. Partiamo da $V = \text{row}(B)$. Vogliamo trovare $A$ tale che $V = \ker(A)$.
2. Grazie alla proprietà di dualità, questo è equivalente a trovare $A$ tale che $\text{row}(A) = \ker(B)$.
3. Calcoliamo quindi una base per $\ker(B)$ risolvendo il sistema $Bx=\mathbf{0}$.
4. I vettori della base trovata per $\ker(B)$ diventeranno le righe della matrice $A$ cercata. Il sistema $Ax=\mathbf{0}$ fornirà la forma cartesiana.

**Esempio:** Sia $V = \text{row}(B)$ con $B = \begin{pmatrix} -1 & 1 & 2 \\ 0 & 1 & 1 \end{pmatrix}$.
1. Calcoliamo $\ker(B)$ risolvendo $Bx=0$. La matrice $B$ ridotta a scala (con Gauss-Jordan) è $B' = \begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \end{pmatrix}$.
2. Il sistema associato è $\begin{cases} x_1 - x_3 = 0 \\ x_2 + x_3 = 0 \end{cases}$, da cui $x_1 = x_3$ e $x_2 = -x_3$.
3. La soluzione generale è $x = (x_3, -x_3, x_3) = x_3(1, -1, 1)$.
4. Una base per $\ker(B)$ è il vettore $(1, -1, 1)$.
5. La matrice $A$ avrà questo vettore come unica riga: $A = \begin{pmatrix} 1 & -1 & 1 \end{pmatrix}$.
6. La forma cartesiana di $V$ è quindi l'insieme delle soluzioni di $x_1 - x_2 + x_3 = 0$.

---

## Operazioni tra Sottospazi

La forma di rappresentazione influenza la facilità con cui si eseguono operazioni tra sottospazi.

### Somma ($W_1 + W_2$)

La forma **parametrica** è la più adatta. Se $W_1 = \text{span}(B_1) = \text{row}(A_1)$ e $W_2 = \text{span}(B_2) = \text{row}(A_2)$, dove $B_1, B_2$ sono insiemi di generatori (o basi) e $A_1, A_2$ le matrici con quei generatori come righe, allora:
$$W_1 + W_2 = \text{span}(B_1 \cup B_2) = \text{row}\left(\begin{pmatrix} A_1 \\ A_2 \end{pmatrix}\right)$$
Per trovare una base della somma:
1. Si costruisce la matrice $A = \begin{pmatrix} A_1 \\ A_2 \end{pmatrix}$ impilando le matrici dei generatori.
2. Si riduce $A$ con Gauss-Jordan.
3. Le righe non nulle della matrice ridotta formano una base per $W_1 + W_2$.

### Intersezione ($W_1 \cap W_2$)

La forma **cartesiana** è la più adatta. Se $W_1 = \ker(A_1)$ e $W_2 = \ker(A_2)$, un vettore $x$ appartiene all'intersezione se e solo se soddisfa contemporaneamente entrambi i sistemi di equazioni, $A_1x = \mathbf{0}$ e $A_2x = \mathbf{0}$. Questo è equivalente a risolvere il sistema omogeneo associato alla matrice ottenuta impilando le righe di $A_1$ e $A_2$:
$$W_1 \cap W_2 = \ker\left(\begin{pmatrix} A_1 \\ A_2 \end{pmatrix}\right)$$
Per trovare una base dell'intersezione, si risolve questo sistema combinato.

### [[08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#La Formula di Grassmann|Formula di Grassmann]]

Questa formula collega le dimensioni di due sottospazi con quelle della loro somma e intersezione:
$$\dim(W_1 + W_2) = \dim(W_1) + \dim(W_2) - \dim(W_1 \cap W_2)$$
È uno strumento potente per calcolare una dimensione conoscendo le altre tre. Se l'intersezione è il solo vettore nullo ($W_1 \cap W_2 = \{\mathbf{0}\}$), la somma si dice **[[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma Diretta|diretta]]** e si scrive $W_1 \oplus W_2$.

---

## Comparazione di Sottospazi

Per determinare relazioni di inclusione ($U \subseteq W$) o uguaglianza ($U=W$) tra sottospazi, si usano diversi lemmi.

**Lemmi Fondamentali:**
1.  Se $W \subseteq V$ è un sottospazio e $\dim(W) = \dim(V)$, allora $W = V$. Questo è un corollario del [[08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Corollario: Dimensione di un Sottospazio|Corollario: Dimensione di un Sottospazio]].
2.  Siano $U, W \subseteq V$. Se $B_U$ è una base di $U$ e tutti i vettori di $B_U$ appartengono anche a $W$ ($B_U \subseteq W$), allora $U \subseteq W$. Questo è utile per verificare se i generatori di $U$ (in forma parametrica) soddisfano le equazioni di $W$ (in forma cartesiana).
3.  Le seguenti affermazioni sono equivalenti:
    * $U \subseteq W$
    * $U \cap W = U$ (L'intersezione coincide con il sottospazio più piccolo)
    * $U + W = W$ (La somma coincide con il sottospazio più grande)

Questi lemmi permettono di scegliere la strategia più efficiente a seconda delle forme (parametrica, cartesiana o mista) in cui $U$ e $W$ sono presentati. Ad esempio, per verificare $U \subseteq W$, se $\dim(U) = \dim(W)$, basta usare il Lemma 1 dopo aver verificato l'inclusione con il Lemma 2. Altrimenti, si può calcolare $\dim(U+W)$ o $\dim(U \cap W)$ e usare il Lemma 3.

---

## Esempi ed Esercizi Svolti

### Esempio 1: Intersezione e Somma in $\mathbb{R}^3$
Siano $W_1, W_2 \subseteq \mathbb{R}^3$ due sottospazi distinti di dimensione 2 (due piani passanti per l'origine). Dalla formula di Grassmann:
$$\dim(W_1+W_2) = \dim(W_1) + \dim(W_2) - \dim(W_1 \cap W_2) = 2 + 2 - \dim(W_1 \cap W_2) = 4 - \dim(W_1 \cap W_2)$$
Poiché $W_1+W_2 \subseteq \mathbb{R}^3$, la sua dimensione non può superare 3. Quindi, $\dim(W_1+W_2) \le 3$, il che implica $4 - \dim(W_1 \cap W_2) \le 3$, da cui $\dim(W_1 \cap W_2) \ge 1$. L'intersezione ha dimensione almeno 1 (una retta).
Poiché $W_1 \neq W_2$, per il Lemma 1, $\dim(W_1 \cap W_2)$ non può essere 2. Pertanto, $\dim(W_1 \cap W_2)=1$. Di conseguenza, $\dim(W_1+W_2) = 4 - 1 = 3$, il che significa che $W_1+W_2 = \mathbb{R}^3$.

### Esempio 2: Coordinate rispetto a una Base Non Standard
Un vettore $v \in \mathbb{R}^n$ è tipicamente espresso come combinazione lineare della [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Dimensione|base standard]] $E = \{e_1, \dots, e_n\}$. Ad esempio, $v=(4,5)$ in $\mathbb{R}^2$ significa $v = 4e_1 + 5e_2 = 4(1,0) + 5(0,1)$. Tuttavia, è possibile rappresentare $v$ rispetto a qualsiasi altra [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Base|base]] $B = \{b_1, \dots, b_n\}$ di $\mathbb{R}^n$.

Le **coordinate** di $v$ rispetto a $B$, denotate con $[v]_B = (\lambda_1, \dots, \lambda_n)$, sono i coefficienti unici tali che:
$$v = \lambda_1 b_1 + \dots + \lambda_n b_n$$
Trovare $[v]_B$ equivale a risolvere il sistema lineare non omogeneo che si ottiene da questa equazione vettoriale.

Sia $B = \{(2,1), (-1,2)\}$ una base di $\mathbb{R}^2$ e $v=(4,5)$. Cerchiamo $\lambda_1, \lambda_2$ tali che:
$$(4,5) = \lambda_1(2,1) + \lambda_2(-1,2) = (2\lambda_1 - \lambda_2, \lambda_1 + 2\lambda_2)$$
Questo si traduce nel sistema:
$$\begin{cases} 2\lambda_1 - \lambda_2 = 4 \\ \lambda_1 + 2\lambda_2 = 5 \end{cases}$$
Risolvendo (es. per sostituzione: $\lambda_2 = 2\lambda_1 - 4$, sostituendo nella seconda $\lambda_1 + 2(2\lambda_1 - 4) = 5 \implies 5\lambda_1 - 8 = 5 \implies 5\lambda_1 = 13 \implies \lambda_1 = 13/5$. Poi $\lambda_2 = 2(13/5) - 4 = 26/5 - 20/5 = 6/5$), si ottiene $\lambda_1 = 13/5$ e $\lambda_2 = 6/5$.
Pertanto, le coordinate di $v=(4,5)$ rispetto alla base $B$ sono $[v]_B = (13/5, 6/5)$.

### Esempio 3: Identificazione di Sottospazi
Un sottoinsieme $S \subseteq \mathbb{R}^n$ è un [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Sottospazi Vettoriali|sottospazio]] se soddisfa le condizioni di chiusura (o la condizione combinata). In particolare, deve contenere il vettore nullo $\mathbf{0}$.
* $S_1 = \{ (x,y) \in \mathbb{R}^2 \mid x^2+y^2=1 \}$ (circonferenza unitaria) **non** è un sottospazio perché $\mathbf{0}=(0,0) \notin S_1$ (poiché $0^2+0^2=0 \neq 1$).
* $S_2 = \{ (x,y,z) \in \mathbb{R}^3 \mid x,y,z \ge 0 \}$ (primo ottante) **non** è un sottospazio. Contiene $\mathbf{0}=(0,0,0)$ ed è chiuso rispetto alla somma di vettori con componenti non negative. Tuttavia, non è chiuso rispetto alla moltiplicazione per scalari negativi. Ad esempio, $v=(1,1,1) \in S_2$, ma $\lambda=-1$, $\lambda v = (-1,-1,-1) \notin S_2$.
* $S_3 = \{ (x,y) \in \mathbb{R}^2 \mid x^2+y^2=-1 \}$ è l'insieme vuoto $\emptyset$, che per definizione **non** è un sottospazio (richiede di essere non vuoto).