# Riepilogo dei Concetti: Sottospazi Generati e Basi

La discussione riprende l'analisi dei [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|sottospazi vettoriali]], in particolare il concetto di sottospazio generato da un sottoinsieme $S$ di uno spazio vettoriale $V$.

## Sottospazio Generato
Dato un sottoinsieme non vuoto $S \subseteq V$, si definisce il **sottospazio generato** da $S$, denotato con $L(S)$ o $\langle S \rangle$, come l'insieme di tutte le possibili combinazioni lineari di un numero finito di vettori appartenenti a $S$:
$$ L(S) = \langle S \rangle := \left\{ \sum_{i=1}^{k} \alpha_i v_i \mid v_i \in S, \alpha_i \in \mathbb{R}, k \in \mathbb{N} \right\} $$
Questa costruzione garantisce che, partendo da un qualsiasi insieme di vettori $S$, si possa sempre ottenere un sottospazio vettoriale di $V$. $\langle S \rangle$ è, di fatto, il più piccolo sottospazio di $V$ che contiene $S$.

## Sistemi di Generatori
Un caso di particolare interesse si verifica quando il sottospazio generato da un insieme $F \subseteq V$ coincide con l'intero spazio vettoriale $V$. In tale circostanza, l'insieme $F$ è definito **sistema di generatori** (o insieme di generatori) per $V$.

> **Definizione:** $F$ è un sistema di generatori per $V$ se $\langle F \rangle = V$.

Questo significa che ogni vettore di $V$ può essere espresso come combinazione lineare di un numero finito di vettori appartenenti a $F$.
Ad esempio, in $\mathbb{R}^2$, l'insieme $F = \{(1, 0), (0, 1)\}$ è un sistema di generatori, poiché ogni vettore $(x, y) \in \mathbb{R}^2$ può essere scritto come:
$$ (x, y) = x(1, 0) + y(0, 1) $$
L'utilità di un sistema di generatori risiede nella possibilità di descrivere l'intero spazio vettoriale, potenzialmente infinito, attraverso un insieme finito di "mattoni" fondamentali.

## Indipendenza Lineare

### L'Ambiguità della Rappresentazione
Un problema che può sorgere con i sistemi di generatori è la non unicità della rappresentazione. Un vettore di $V$ potrebbe essere espresso come combinazione lineare dei generatori in modi diversi. Ad esempio, l'insieme $F = \{(1, 1, 0), (1, 0, 0), (0, 1, 0), (0, 0, 1)\}$ genera tutto $\mathbb{R}^3$, ma la rappresentazione non è unica, come si può verificare risolvendo il sistema lineare associato che risulta avere infinite soluzioni. Questa ambiguità è indesiderata.

### Definizione di Indipendenza Lineare
Per superare tale ambiguità, si introduce il concetto di **indipendenza lineare**.

> **Definizione:** Un insieme di vettori $F = \{v_1, v_2, \dots, v_n\}$ si dice **linearmente indipendente** se l'unica combinazione lineare dei suoi elementi che risulta nel vettore nullo è quella con tutti i coefficienti nulli.
$$ \sum_{i=1}^{n} \lambda_i v_i = \mathbf{0} \implies \lambda_i = 0 \quad \forall i = 1, \dots, n $$
Un insieme che non è linearmente indipendente è detto **linearmente dipendente**.

### Esempi di Verifica
- **Esempio 1 (Indipendente):** L'insieme $\{(1, 0), (0, 1)\}$ in $\mathbb{R}^2$ è linearmente indipendente. Infatti, l'equazione $\lambda_1(1, 0) + \lambda_2(0, 1) = (0, 0)$ porta al vettore $(\lambda_1, \lambda_2) = (0, 0)$, che implica necessariamente $\lambda_1 = 0$ e $\lambda_2 = 0$.

- **Esempio 2 (Dipendente):** L'insieme $F = \{(1, 1, 0), (1, 0, 0), (0, 1, 0), (0, 0, 1)\}$ in $\mathbb{R}^3$ è linearmente dipendente. Ponendo una combinazione lineare uguale al vettore nullo:
$$ \lambda_1(1,1,0) + \lambda_2(1,0,0) + \lambda_3(0,1,0) + \lambda_4(0,0,1) = (0,0,0) $$
si ottiene il vettore $(\lambda_1 + \lambda_2, \lambda_1 + \lambda_3, \lambda_4) = (0,0,0)$, che conduce al sistema omogeneo:
$$ \begin{cases} \lambda_1 + \lambda_2 = 0 \\ \lambda_1 + \lambda_3 = 0 \\ \lambda_4 = 0 \end{cases} $$
Questo sistema di 3 equazioni in 4 incognite ammette infinite soluzioni non nulle (ad esempio, $\lambda_1 = 1, \lambda_2 = -1, \lambda_3 = -1, \lambda_4 = 0$). L'esistenza di una soluzione non banale dimostra la dipendenza lineare.

- **Esempio 3 (Vettore Nullo):** Qualsiasi insieme di vettori che contenga il vettore nullo $\mathbf{0}$ è sempre linearmente dipendente. È sufficiente considerare la combinazione lineare in cui il coefficiente del vettore nullo è non nullo (es. $1$) e tutti gli altri sono nulli.

- **Esempio 4 (Indipendente in $\mathbb{R}^4$):** L'insieme $\{(1,1,0,0), (1,0,1,0), (0,1,1,0)\}$ in $\mathbb{R}^4$ è linearmente indipendente. L'equazione vettoriale $\lambda_1(1,1,0,0) + \lambda_2(1,0,1,0) + \lambda_3(0,1,1,0) = (0,0,0,0)$ si traduce nel sistema:
$$ \begin{cases} \lambda_1 + \lambda_2 = 0 \\ \lambda_1 + \lambda_3 = 0 \\ \lambda_2 + \lambda_3 = 0 \end{cases} $$
La matrice dei coefficienti di questo sistema omogeneo 3x3 ha determinante diverso da zero, quindi il suo [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]] è massimo. Di conseguenza, il sistema ammette solo la soluzione banale $(\lambda_1, \lambda_2, \lambda_3) = (0,0,0)$, provando l'indipendenza lineare.

### Caratterizzazione della Dipendenza Lineare
Una proprietà fondamentale lega la dipendenza lineare alla ridondanza dei vettori.

**Proposizione:** Un insieme di vettori $F = \{v_1, \dots, v_n\}$ (con $n \ge 2$) è linearmente dipendente se e solo se esiste almeno un vettore $v_j$ nell'insieme che può essere espresso come combinazione lineare degli altri vettori.

**Dimostrazione:**
($\implies$) Se $F$ è linearmente dipendente, esistono scalari $\lambda_1, \dots, \lambda_n$, non tutti nulli, tali che:
$$ \sum_{i=1}^{n} \lambda_i v_i = \mathbf{0} $$
Poiché non tutti i coefficienti sono nulli, esiste almeno un $\lambda_j \neq 0$. Si può quindi isolare il termine $j$-esimo:
$$ \lambda_j v_j = - \sum_{i=1, i \neq j}^{n} \lambda_i v_i $$
Essendo $\lambda_j \neq 0$, è possibile dividere per esso, ottenendo $v_j$ come combinazione lineare degli altri vettori:
$$ v_j = \sum_{i=1, i \neq j}^{n} \left(-\frac{\lambda_i}{\lambda_j}\right) v_i $$
($\impliedby$) Viceversa, se un vettore $v_j$ è combinazione lineare degli altri, allora $v_j = \sum_{i \neq j} \mu_i v_i$. Portando $v_j$ al secondo membro si ottiene $\sum_{i \neq j} \mu_i v_i - 1 \cdot v_j = \mathbf{0}$. Questa è una combinazione lineare nulla con almeno un coefficiente (quello di $v_j$, che è -1) non nullo, il che dimostra la dipendenza lineare.

## Basi e Dimensione di uno Spazio Vettoriale

### Definizione di Base
Il connubio tra i concetti di generazione e indipendenza lineare porta alla definizione di **base**.

> **Definizione:** Una **base** di uno spazio vettoriale $V$ è un sottoinsieme di vettori $B \subseteq V$ che soddisfa due proprietà:
> 1.  $B$ è un sistema di generatori per $V$ ($\langle B \rangle = V$).
> 2.  $B$ è un insieme linearmente indipendente.

Una base rappresenta l'insieme "perfetto" di vettori: abbastanza numeroso da generare l'intero spazio, ma senza elementi ridondanti (essendo linearmente indipendente). Grazie a queste proprietà, ogni vettore dello spazio si può scrivere in **modo unico** come combinazione lineare dei vettori della base. Gli scalari di tale combinazione sono detti **coordinate** del vettore rispetto a quella base.

### Unicità della Cardinalità delle Basi: Lemma di Steinitz
Un risultato fondamentale, dimostrato tramite il **Lemma di Steinitz**, afferma che, se uno spazio vettoriale ammette una base finita, allora tutte le sue basi hanno lo stesso numero di elementi.

> **Lemma di Steinitz:** Sia $V$ uno spazio vettoriale. Se $\{v_1, \dots, v_n\}$ è un sistema di generatori per $V$ e $\{w_1, \dots, w_r\}$ è un insieme linearmente indipendente di vettori di $V$, allora $r \le n$.

Questo lemma implica che il numero di vettori in un qualsiasi insieme linearmente indipendente non può superare il numero di vettori di un qualsiasi sistema di generatori. Poiché una base è entrambe le cose, se $B_1$ e $B_2$ sono due basi di $V$ con $|B_1|=n$ e $|B_2|=r$, applicando il lemma due volte si ottiene $n \le r$ e $r \le n$, da cui $r=n$.

Questo permette di associare un numero univoco a ogni spazio vettoriale e di vedere una base come:
- Un **sistema di generatori minimale**: non è possibile rimuovere alcun vettore senza perdere la capacità di generare lo spazio.
- Un **insieme linearmente indipendente massimale**: non è possibile aggiungere alcun vettore senza perdere l'indipendenza lineare.

### Definizione di Dimensione
La cardinalità (numero di elementi) di una qualsiasi base di uno spazio vettoriale $V$ è chiamata **dimensione** di $V$, e si denota con $\dim(V)$.

- **Esempi:**
    - $\dim(\mathbb{R}^2) = 2$. Una base è $\{(1, 0), (0, 1)\}$.
    - $\dim(\mathbb{R}^3) = 3$. Una base è $\{(1, 0, 0), (0, 1, 0), (0, 0, 1)\}$.
    - In generale, $\dim(\mathbb{R}^n) = n$. La base più naturale, chiamata **base standard** o **canonica**, è formata dai vettori $e_i$ che hanno un $1$ nella $i$-esima posizione e $0$ altrove.
    - Lo spazio vettoriale nullo $\{\mathbf{0}\}$ ha dimensione 0, in quanto l'unico sottoinsieme non vuoto, $\{\mathbf{0}\}$, è linearmente dipendente, quindi non può avere una base.

## L'Importanza dell'Approccio Algebrico in Geometria
La definizione algebrica di dimensione fornisce uno strumento potente per studiare la geometria in modo rigoroso, superando i limiti dell'intuizione visiva. Mentre la nostra esperienza si ferma a tre dimensioni, l'algebra lineare ci permette di definire e operare in spazi di dimensione $n$ qualsiasi, come $\mathbb{R}^n$, semplicemente come l'insieme di $n$-uple di numeri reali.

Questo approccio è cruciale per rispondere a domande geometriche in contesti non visualizzabili. Ad esempio, per determinare la natura dell'intersezione tra due piani in uno spazio a 4 dimensioni, l'intuizione derivata da $\mathbb{R}^3$ è insufficiente. L'algebra lineare, invece, fornisce gli strumenti formali per analizzare e risolvere tali problemi in qualsiasi dimensione.