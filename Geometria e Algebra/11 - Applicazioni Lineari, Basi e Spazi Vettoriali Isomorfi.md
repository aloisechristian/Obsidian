## Definizione di Applicazioni Lineari su Spazi Vettoriali Generali

Nelle lezioni precedenti (vedi [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango]]), gli esempi di [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Definizione di Applicazione Lineare (Omomorfismo)|applicazioni lineari (o omomorfismi)]] si sono concentrati su mappe tra [[Geometria e Algebra/06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Spazio Vettoriale Rn|spazi vettoriali]] della forma $\mathbb{R}^n$ e $\mathbb{R}^m$. Tali applicazioni venivano definite tipicamente associando a un vettore $(x_1, \dots, x_n) \in \mathbb{R}^n$ un vettore le cui componenti erano polinomi omogenei di primo grado nelle variabili $x_i$. Sorge dunque la questione di come definire un'applicazione lineare tra due spazi vettoriali generici $V$ e $W$, che non siano necessariamente spazi di n-uple di numeri reali.

### Il Ruolo Fondamentale della Base
La chiave per definire un omomorfismo in un contesto generale risiede nell'utilizzo di una [[Geometria e Algebra/07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Base di uno Spazio Vettoriale|base]] dello spazio di partenza, il dominio $V$. Un'applicazione lineare è infatti **completamente e univocamente determinata** dalla sua azione sugli elementi di una qualsiasi base di $V$.

Il procedimento è il seguente:
1.  Si fissa una base $B = \{b_1, b_2, \dots, b_n\}$ dello spazio vettoriale $V$. Supponiamo quindi che $\dim(V) = n$ (vedi [[Geometria e Algebra/07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Dimensione di uno Spazio Vettoriale|Dimensione]]).
2.  Si scelgono arbitrariamente $n$ vettori $w_1, w_2, \dots, w_n$ nello spazio di arrivo, il codominio $W$. Questi vettori non devono necessariamente formare una base o essere [[Geometria e Algebra/07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Lineare Indipendenza|linearmente indipendenti]]; possono essere qualsiasi, inclusi vettori nulli o ripetuti.

Una volta fissata la base $B$ e i vettori immagine $\{w_i\}$, è possibile definire un'applicazione lineare $f: V \to W$ imponendo la condizione che $f(b_i) = w_i$ per ogni $i = 1, \dots, n$.

Perché questa informazione è sufficiente? Dato un qualsiasi vettore $v \in V$, poiché $B$ è una base, $v$ può essere espresso in modo unico come [[Geometria e Algebra/07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Combinazioni Lineari|combinazione lineare]] degli elementi di $B$:
$$v = \lambda_1 b_1 + \lambda_2 b_2 + \dots + \lambda_n b_n$$
Sfruttando le proprietà di linearità di $f$ (definite in [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Definizione di Applicazione Lineare (Omomorfismo)|Definizione di Applicazione Lineare]]), possiamo calcolare l'immagine di $v$:
$$\begin{aligned} f(v) &= f(\lambda_1 b_1 + \lambda_2 b_2 + \dots + \lambda_n b_n) \\ &= \lambda_1 f(b_1) + \lambda_2 f(b_2) + \dots + \lambda_n b_n \\ &= \lambda_1 w_1 + \lambda_2 w_2 + \dots + \lambda_n w_n \end{aligned}$$
Questo dimostra che l'immagine di qualsiasi vettore $v \in V$ è determinata, essendo una combinazione lineare dei vettori $w_i$ (scelti da noi) con gli scalari $\lambda_i$ (le [[Geometria e Algebra/08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Coordinate (o Componenti)|coordinate]] di $v$ rispetto alla base $B$).

### Esistenza e Unicità dell'Omomorfismo
Il procedimento descritto non solo definisce l'applicazione, ma garantisce anche la sua unicità. Se esistesse un'altra applicazione lineare $g: V \to W$ tale che $g(b_i) = w_i$ per ogni $i$, allora per qualsiasi vettore $v = \sum_{i=1}^n \lambda_i b_i$ avremmo:
$$g(v) = g\left(\sum_{i=1}^n \lambda_i b_i\right) = \sum_{i=1}^n \lambda_i g(b_i) = \sum_{i=1}^n \lambda_i w_i = f(v)$$
Poiché $g(v) = f(v)$ per ogni $v \in V$, le due applicazioni sono identiche ($f=g$). Questo ragionamento porta alla seguente proposizione fondamentale.

**Proposizione:** Dati due spazi vettoriali $V$ e $W$, una base $B = \{b_1, \dots, b_n\}$ di $V$ e $n$ vettori arbitrari $w_1, \dots, w_n \in W$, esiste ed è unico l'omomorfismo $f: V \to W$ tale che $f(b_i) = w_i$ per ogni $i=1, \dots, n$.

## Esempio: Applicazione Lineare tra Matrici e Polinomi

Consideriamo un'applicazione lineare $f$ dallo spazio delle matrici reali $2 \times 2$, denotato con $M_{2,2}(\mathbb{R})$, allo spazio dei polinomi di grado al più 1, denotato con $\mathbb{R}_1[t]$. (Vedi [[Geometria e Algebra/06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Esempi di Spazi Vettoriali|Esempi di Spazi Vettoriali]]).

1.  **Fissiamo una base del dominio $M_{2,2}(\mathbb{R})$:** La base standard è costituita dalle matrici ($\dim(M_{2,2}(\mathbb{R}))=4$):
    $B_1 = \begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$, $B_2 = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}$, $B_3 = \begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix}$, $B_4 = \begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix}$.
2.  **Scegliamo 4 vettori nel codominio $\mathbb{R}_1[t]$:** (Notiamo che $\dim(\mathbb{R}_1[t])=2$). Scegliamo ad esempio i polinomi $1$, $t$, $t+1$, e $t-1$.
3.  **Definiamo l'azione di $f$ sulla base:**
    - $f(B_1) = 1$
    - $f(B_2) = t$
    - $f(B_3) = t+1$
    - $f(B_4) = t-1$

Ora possiamo calcolare l'immagine di una generica matrice $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$. Poiché $A = aB_1 + bB_2 + cB_3 + dB_4$, la sua immagine sarà:
$$\begin{aligned} f(A) &= a f(B_1) + b f(B_2) + c f(B_3) + d f(B_4) \\ &= a(1) + b(t) + c(t+1) + d(t-1) \\ &= a + bt + ct + c + dt - d \\ &= (a+c-d) + (b+c+d)t \end{aligned}$$
Abbiamo così definito un'applicazione lineare tra spazi vettoriali non convenzionali specificando unicamente la sua azione su una base.

## Classificazione delle Applicazioni Lineari

In analogia con le funzioni generiche (vedi [[Analisi I/01 - Fondamenti di Teoria degli Insiemi e Funzioni#Proprietà delle Funzioni (Iniettività, Suriettività, Biettività)|Proprietà delle Funzioni]]), introduciamo una terminologia specifica per le applicazioni lineari basata sulle proprietà di iniettività e suriettività.

- Un'applicazione lineare $f$ si dice **monomorfismo** se è iniettiva.
- Un'applicazione lineare $f$ si dice **epimorfismo** se è suriettiva.
- Un'applicazione lineare $f$ si dice **isomorfismo** se è biettiva (cioè sia iniettiva che suriettiva).

Un isomorfismo, essendo una funzione biettiva, ammette un'applicazione inversa $f^{-1}: W \to V$. Un risultato importante dell'algebra lineare è che se $f$ è un isomorfismo, allora anche la sua inversa $f^{-1}$ è un'applicazione lineare (e quindi un isomorfismo).

### Spazi Vettoriali Isomorfi
Due spazi vettoriali $V$ e $W$ si dicono **isomorfi**, e si scrive $V \cong W$, se esiste un isomorfismo $f: V \to W$. Il concetto di isomorfismo (dal greco "stessa forma") è cruciale: esso implica che i due spazi, dal punto di vista della struttura algebrica (somma di vettori e prodotto per scalare), sono indistinguibili. Sebbene gli elementi possano apparire diversi (es. matrici e polinomi), le operazioni si comportano allo stesso modo. L'isomorfismo è una relazione di equivalenza.

## Criteri di Iniettività, Suriettività e Biettività

Per determinare se un'applicazione lineare possiede queste proprietà, si possono utilizzare dei criteri pratici legati ai sottospazi associati all'applicazione: il [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Nucleo (Kernel)|Nucleo (Kernel)]] e l'[[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Immagine (Im)|Immagine]].

### Criterio di Iniettività tramite il Nucleo (Kernel)
**Proposizione:** Un'applicazione lineare $f: V \to W$ è iniettiva (è un monomorfismo) se e solo se il suo nucleo è il sottospazio nullo, cioè $\ker(f) = \{0_V\}$.

*Dimostrazione:*
- $(\implies)$ Assumiamo $f$ iniettiva. Sappiamo che $f(0_V) = 0_W$ (proprietà degli omomorfismi), quindi $0_V \in \ker(f)$. Se esistesse un altro vettore $v \in \ker(f)$ con $v \neq 0_V$, avremmo $f(v) = 0_W = f(0_V)$, contraddicendo l'iniettività (elementi distinti $v$ e $0_V$ mappati sullo stesso elemento). Pertanto, l'unico elemento nel kernel è il vettore nullo.
- $(\impliedby)$ Assumiamo $\ker(f) = \{0_V\}$. Vogliamo dimostrare che $f$ è iniettiva. Siano $v_1, v_2 \in V$ tali che $f(v_1) = f(v_2)$. Per la linearità di $f$, abbiamo $f(v_1) - f(v_2) = f(v_1 - v_2) = 0_W$. Questo significa che il vettore $v_1 - v_2$ appartiene al [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Nucleo (Kernel)|nucleo]] di $f$. Poiché il nucleo contiene solo il vettore nullo, deve essere $v_1 - v_2 = 0_V$, da cui $v_1 = v_2$. Ciò dimostra l'iniettività.

Questo criterio fornisce un metodo algoritmico per verificare l'iniettività: è sufficiente calcolare il kernel e controllarne la dimensione. Se $\dim(\ker(f)) = 0$, l'applicazione è iniettiva.

### Caratterizzazione tramite l'Immagine di una Base
Sia $f: V \to W$ un'applicazione lineare e $B = \{b_1, \dots, b_n\}$ una base di $V$. Le proprietà di $f$ possono essere caratterizzate osservando l'insieme delle immagini dei vettori della base, $\{f(b_1), \dots, f(b_n)\} \subseteq W$.

- **Iniettività:** $f$ è un **monomorfismo** se e solo se l'insieme $\{f(b_1), \dots, f(b_n)\}$ è linearmente indipendente in $W$.
- **Suriettività:** $f$ è un **epimorfismo** se e solo se l'insieme $\{f(b_1), \dots, f(b_n)\}$ genera $W$. Questo segue direttamente dalla definizione di [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Immagine (Im)|Immagine]], $\text{Im}(f) = \text{Span}(f(b_1), \dots, f(b_n))$.
- **Biettività:** $f$ è un **isomorfismo** se e solo se l'insieme $\{f(b_1), \dots, f(b_n)\}$ è una base di $W$.

(Nota: queste caratterizzazioni sono strettamente collegate al [[Geometria e Algebra/10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Teorema della Dimensione (o del Rango)|Teorema della Dimensione (Nullità + Rango)]], che stabilisce $\dim(V) = \dim(\ker(f)) + \dim(\text{Im}(f))$).

---

## Corollario Pratico: Confronto Dimensionale (n vs m)

Le proposizioni precedenti, basate sul [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Lemma di Steinitz (Teorema dello Scambio)|Lemma di Steinitz]], ci danno due regole fondamentali per un'applicazione $L: V \to W$ con $\dim(V)=n$ e $\dim(W)=m$:
1.  Se $L$ è **INIETTIVA** $\implies n \le m$ (La dimensione del dominio non può superare quella del codominio).
2.  Se $L$ è **SURIETTIVA** $\implies n \ge m$ (La dimensione del dominio non può essere inferiore a quella del codominio).

Questo ci permette di creare un "filtro" immediato per qualsiasi applicazione, riassunto in questa tabella:

| Caso | Confronto Dimensioni | Esempio                                         | Può essere INIETTIVA?                                                                                                                           | Può essere SURIETTIVA?                                                                                                                                                |                                                                                                                   |
| :--- | :------------------- | :---------------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| 1    | **$n > m$**          | $L: \mathbb{R}^3 \to \mathbb{R}^2$ ($n=3, m=2$) | **NO, MAI.** <br> (Se fosse iniettiva, $n$ dovrebbe essere $\le m$, ma $3 \not\le 2$). Il [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango | Teorema del Rango]] implica $\dim(\text{Ker}) = n - \text{rank} \ge n - m > 0$.                                                                                       | **SÌ, POSSIBILE.** <br> (Se $\text{rank}(L) = m = 2$). La regola 2 ($n \ge m$) è rispettata. (Vedi Esercizio 5B). |
| 2    | **$n < m$**          | $L: \mathbb{R}^2 \to \mathbb{R}^3$ ($n=2, m=3$) | **SÌ, POSSIBILE.** <br> (Se $\text{rank}(L) = n = 2$). La regola 1 ($n \le m$) è rispettata. (Vedi Esercizio 5C).                               | **NO, MAI.** <br> (Se fosse suriettiva, $n$ dovrebbe essere $\ge m$, ma $2 \not\ge 3$). L'immagine $\dim(\text{Im}) = \text{rank}(L) \le n < m$. Non può coprire $W$. |                                                                                                                   |
| 3    | **$n = m$**          | $L: \mathbb{R}^3 \to \mathbb{R}^3$ ($n=3, m=3$) | **SÌ, POSSIBILE.**                                                                                                                              | **SÌ, POSSIBILE.**                                                                                                                                                    |                                                                                                                   |

---
### Il Caso Speciale $n = m$ (Endomorfismi)

Questo è il caso più importante. Quando le dimensioni sono uguali, le proprietà collassano in un'unica condizione.

Per un'applicazione $L: V \to W$ con $\dim(V) = \dim(W) = n$:

**$L$ è INIETTIVA $\iff L$ è SURIETTIVA $\iff L$ è un ISOMORFISMO**

Questo discende direttamente dal [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango|Teorema del Rango]]:
* $L$ è iniettiva $\iff \dim(\text{Ker})=0 \iff \text{rank}=n$
* $L$ è suriettiva $\iff \dim(\text{Im})=n \iff \text{rank}=n$

Entrambe le condizioni equivalgono a $\text{rank}=n$, che per matrici quadrate associate $A$ equivale a $\det(A) \neq 0$.

---

## Il Teorema Fondamentale degli Isomorfismi

Da queste caratterizzazioni deriva un corollario di immensa importanza pratica.

**Corollario:** Due spazi vettoriali di dimensione finita $V$ e $W$ (sullo stesso campo) sono isomorfi se e solo se hanno la stessa dimensione.
$$V \cong W \iff \dim(V) = \dim(W)$$

*Dimostrazione:*
- $(\implies)$ Se $f: V \to W$ è un isomorfismo e $B = \{b_1, \dots, b_n\}$ è una base di $V$ (quindi $\dim(V)=n$), allora per la caratterizzazione precedente, $\{f(b_1), \dots, f(b_n)\}$ è una base di $W$. Poiché questa base ha $n$ elementi, $\dim(W) = n$.
- $(\impliedby)$ Se $\dim(V) = \dim(W) = n$, possiamo costruire un isomorfismo. Siano $B_V = \{v_1, \dots, v_n\}$ una base di $V$ e $B_W = \{w_1, \dots, w_n\}$ una base di $W$. Per la proposizione sull'esistenza e unicità, definiamo l'applicazione lineare $f: V \to W$ tale che $f(v_i) = w_i$. Poiché l'immagine della base $B_V$ è la base $B_W$ (un insieme di generatori linearmente indipendenti di $W$), l'applicazione $f$ è biettiva, e quindi un isomorfismo.

### Conseguenze: Ogni Spazio Vettoriale è Isomorfo a $\mathbb{R}^n$
Questo risultato implica che qualsiasi spazio vettoriale di dimensione finita $n$ sul campo $\mathbb{R}$ è isomorfo allo spazio vettoriale $\mathbb{R}^n$. Questo ci permette di "tradurre" problemi definiti su spazi vettoriali astratti (come spazi di matrici, polinomi o funzioni) in problemi equivalenti su $\mathbb{R}^n$, dove abbiamo a disposizione strumenti computazionali consolidati (es. [[Geometria e Algebra/Algoritmo di Eliminazione di Gauss Jordan|riduzione a scala di Gauss]]).

### L'Isomorfismo delle Coordinate
Dato uno spazio vettoriale $V$ di dimensione $n$ e una base $B = \{b_1, \dots, b_n\}$, possiamo definire esplicitamente l'isomorfismo $\phi_B: V \to \mathbb{R}^n$. Questo isomorfismo associa a ogni vettore $v \in V$ il vettore delle sue coordinate rispetto alla base $B$ (vedi [[Geometria e Algebra/08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#L'isomorfismo delle coordinate|Isomorfismo delle Coordinate]]).

Se $v = \lambda_1 b_1 + \dots + \lambda_n b_n$, allora:
$$\phi_B(v) = (\lambda_1, \dots, \lambda_n) \in \mathbb{R}^n$$
Il vettore $(\lambda_1, \dots, \lambda_n)$ è detto **vettore delle coordinate** di $v$ rispetto a $B$, talvolta denotato come $[v]_B$.

## Applicazione Pratica: Riformulare un Omomorfismo in Termini di $\mathbb{R}^n$

Riprendiamo l'esempio $f: M_{2,2}(\mathbb{R}) \to \mathbb{R}_1[t]$.
- Lo spazio $M_{2,2}(\mathbb{R})$ ha $\dim=4$, quindi $M_{2,2}(\mathbb{R}) \cong \mathbb{R}^4$. Fissando la base standard $B = \{B_1, B_2, B_3, B_4\}$, l'isomorfismo delle coordinate $\phi_B$ associa la matrice $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$ al vettore delle coordinate $(a, b, c, d) \in \mathbb{R}^4$.
- Lo spazio $\mathbb{R}_1[t]$ ha $\dim=2$, quindi $\mathbb{R}_1[t] \cong \mathbb{R}^2$. Fissando la base canonica $C = \{1, t\}$, l'isomorfismo delle coordinate $\phi_C$ associa il polinomio $p(t) = a_0 + a_1 t$ al vettore delle coordinate $(a_0, a_1) \in \mathbb{R}^2$.

La nostra applicazione originale $f(A) = (a+c-d) + (b+c+d)t$ può essere ora "tradotta" in un'applicazione $\tilde{f}: \mathbb{R}^4 \to \mathbb{R}^2$ che mappa il vettore delle coordinate di $A$ (in base $B$) al vettore delle coordinate di $f(A)$ (in base $C$):
$$\tilde{f}(a, b, c, d) = (a+c-d, \ b+c+d)$$
Questa nuova formulazione $\tilde{f} = \phi_C \circ f \circ \phi_B^{-1}$ è più familiare e permette di riconoscere immediatamente che si tratta di un'applicazione lineare, poiché le sue componenti sono polinomi omogenei di primo grado. Questa $\tilde{f}$ è quella che, come vedremo, può essere rappresentata da una [[11 - Matrice Associata ad un'Applicazione Lineare|matrice associata]].

### La Dipendenza dalla Base Scelta
È fondamentale sottolineare che il vettore delle coordinate di un elemento dipende intrinsecamente dalla base scelta. Cambiando la base di riferimento, lo stesso elemento di uno spazio vettoriale sarà rappresentato da un vettore di coordinate differente. Questa osservazione sarà cruciale per lo studio dei [[12 - Cambiamenti di Base|cambiamenti di base]].