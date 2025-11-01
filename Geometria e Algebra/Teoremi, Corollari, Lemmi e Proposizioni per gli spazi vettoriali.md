# Raccolta di Teoremi sugli Spazi Vettoriali

Questa nota centralizza i principali teoremi, lemmi, proposizioni e corollari relativi alla teoria degli [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|spazi vettoriali]], fondamentali per la comprensione dell'algebra lineare.

---

## Sottospazi Vettoriali

### Proposizione (Condizione Equivalente per Sottospazio)
**Nome:** *Verifica Semplificata di Sottospazio*
Sia $V$ uno spazio vettoriale e $W \subseteq V$ un sottoinsieme non vuoto.
$W$ è un sottospazio vettoriale di $V$ se e solo se per ogni coppia di scalari $\lambda_1, \lambda_2 \in \mathbb{R}$ e per ogni coppia di vettori $w_1, w_2 \in W$, la combinazione lineare $\lambda_1 w_1 + \lambda_2 w_2$ appartiene ancora a $W$.
$$W \text{ sottospazio di } V \iff (\forall \lambda_1, \lambda_2 \in \mathbb{R}, \forall w_1, w_2 \in W \implies \lambda_1 w_1 + \lambda_2 w_2 \in W)$$

### Proposizione (Intersezione di Sottospazi)
**Nome:** *Stabilità dell'Intersezione*
Sia $V$ uno spazio vettoriale e $\{W_i\}_{i \in I}$ una famiglia qualsiasi (anche infinita) di sottospazi vettoriali di $V$. Allora la loro intersezione $W = \bigcap_{i \in I} W_i$ è ancora un sottospazio vettoriale di $V$.

### Proposizione (Spazio Generato è Sottospazio)
**Nome:** *Chiusura dello Spazio Generato*
Sia $V$ uno spazio vettoriale e $S \subseteq V$ un sottoinsieme qualsiasi. Lo [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|spazio generato]] da $S$, denotato con $\langle S \rangle$, è un sottospazio vettoriale di $V$.

### Proposizione (Minimalità dello Spazio Generato)
**Nome:** *Span come Minimo Sottospazio Contenente*
Sia $V$ uno spazio vettoriale, $W \subseteq V$ un sottospazio e $S \subseteq V$ un sottoinsieme. Se $S$ è contenuto in $W$ ($S \subseteq W$), allora anche lo spazio generato da $S$ è contenuto in $W$ ($\langle S \rangle \subseteq W$).
*Nota: $\langle S \rangle$ è il più piccolo sottospazio di $V$ che contiene $S$.*

### Lemma (Caratterizzazione della Somma di Sottospazi)
**Nome:** *Descrizione Esplicita della Somma*
Siano $W_1, W_2$ due sottospazi di uno spazio vettoriale $V$. La [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|somma]] $W_1 + W_2 = \langle W_1 \cup W_2 \rangle$ coincide con l'insieme di tutti i vettori ottenibili sommando un elemento di $W_1$ e un elemento di $W_2$:
$$W_1 + W_2 = \{w_1 + w_2 \mid w_1 \in W_1, w_2 \in W_2 \}$$

### Proposizione (Unicità della Decomposizione in Somma Diretta)
**Nome:** *Unicità della Somma Diretta*
Siano $W_1, W_2$ sottospazi di uno spazio vettoriale $V$ tali che la loro [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma Diretta|somma sia diretta]], $V = W_1 \oplus W_2$. Allora ogni vettore $v \in V$ si può scrivere in **modo unico** come somma $v = w_1 + w_2$, con $w_1 \in W_1$ e $w_2 \in W_2$.

---

## Indipendenza Lineare

### Proposizione (Caratterizzazione della Dipendenza Lineare)
**Nome:** *Criterio di Ridondanza*
Un insieme di vettori $S = \{v_1, \dots, v_n\}$ (con $n \ge 2$) è [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Indipendenza Lineare|linearmente dipendente]] se e solo se esiste almeno un vettore $v_j$ nell'insieme che può essere espresso come [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|combinazione lineare]] degli altri vettori in $S$.
$$\left( \exists j \in \{1, \dots, n\} \text{ t.c. } v_j = \sum_{i=1, i \neq j}^{n} \mu_i v_i \right) \iff S \text{ è L.D.}$$

---

## Basi e Dimensione

### Proposizione (Estrazione di una Base da Generatori)
**Nome:** *Estrazione di una Base*
Sia $V$ uno spazio vettoriale e $S = \{v_1, \dots, v_n\}$ un [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Sistemi di Generatori|insieme di generatori]] finito per $V$. Allora è possibile estrare da $S$ un sottoinsieme che costituisce una [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Base|base]] di $V$.

### Lemma (Lemma di Steinitz)
**Nome:** *Lemma dello Scambio di Steinitz*
Sia $V$ uno spazio vettoriale. Se $\{v_1, \dots, v_n\}$ è un sistema di generatori per $V$ e $\{w_1, \dots, w_r\}$ è un insieme linearmente indipendente di vettori di $V$, allora il numero di vettori linearmente indipendenti non può superare il numero di generatori:
$$r \le n$$

### Corollario (Invarianza della Dimensione)
**Nome:** *Unicità della Dimensione*
Se uno spazio vettoriale $V$ ammette una base finita, allora tutte le basi di $V$ hanno lo stesso numero di elementi. Questo numero è chiamato [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Dimensione|dimensione]] di $V$, denotata con $\dim(V)$.

### Corollario (Proprietà Equivalenti di una Base)
**Nome:** *Caratterizzazioni Equivalenti di una Base*
Sia $V$ uno spazio vettoriale con $\dim(V) = n$. Sia $S = \{s_1, \dots, s_n\}$ un insieme contenente esattamente $n$ vettori di $V$. Le seguenti affermazioni sono equivalenti:
1.  $S$ è linearmente indipendente.
2.  $S$ genera $V$ ($\langle S \rangle = V$).
3.  $S$ è una base di $V$.

### Corollario (Dimensione dei Sottospazi)
**Nome:** *Limitazione sulla Dimensione dei Sottospazi*
Sia $V$ uno spazio vettoriale di dimensione finita $n$, e sia $W$ un suo [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Sottospazi Vettoriali|sottospazio]]. Allora la dimensione di $W$ è minore o uguale alla dimensione di $V$ ($\dim(W) \le n$).
Inoltre, l'uguaglianza delle dimensioni implica l'uguaglianza degli spazi:
$$\dim(W) = n \iff W = V$$

### Proposizione (Completamento a Base)
**Nome:** *Teorema del Completamento della Base*
Sia $V$ uno spazio vettoriale di dimensione finita $n$, e sia $S = \{v_1, \dots, v_r\}$ un insieme linearmente indipendente di vettori di $V$ (con $r \le n$). Allora esistono $n-r$ vettori $v_{r+1}, \dots, v_n \in V$ tali che l'insieme $\{v_1, \dots, v_r, v_{r+1}, \dots, v_n\}$ costituisce una base di $V$.

### Proposizione (Esistenza del Complemento Diretto)
**Nome:** *Esistenza del Complemento*
Sia $V$ uno spazio vettoriale di dimensione finita e $W$ un suo sottospazio. Allora esiste (almeno) un altro sottospazio $W' \subseteq V$, detto [[08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Complemento Diretto di un Sottospazio|complemento]] di $W$ in $V$, tale che $V$ sia la [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma Diretta|somma diretta]] di $W$ e $W'$:
$$V = W \oplus W'$$

### Teorema (Formula di Grassmann)
**Nome:** *Formula delle Dimensioni di Grassmann*
Siano $W_1$ e $W_2$ due sottospazi di uno spazio vettoriale $V$ di dimensione finita. Allora vale la seguente relazione tra le dimensioni:
$$\dim(W_1 + W_2) = \dim(W_1) + \dim(W_2) - \dim(W_1 \cap W_2)$$

---

## Teoremi su Rappresentazioni e Rango

### Teorema (Rango-Nullità)
**Nome:** *Teorema della Dimensione* o *Teorema Rango-Nullità*
Sia $A \in M_{m,n}(\mathbb{R})$ una matrice (o un'applicazione lineare). La somma tra il [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]] della matrice (dimensione dello spazio generato dalle sue righe/colonne, o dell'immagine) e la dimensione del suo [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Esempi di Sottospazi|nucleo]] (nullità) è uguale al numero di colonne della matrice (dimensione dello spazio di partenza):
$$\text{rank}(A) + \dim(\ker(A)) = n$$

### Proposizione (Dualità Kernel-Row Space)
**Nome:** *Ortogonalità Kernel-Spazio Righe*
Siano $A$ e $B$ due matrici con lo stesso numero di colonne $n$. Allora lo [[09 - Rappresentazioni e Operazioni con Sottospazi di R alla n#Forma Parametrica|spazio delle righe]] di $A$ coincide con il [[09 - Rappresentazioni e Operazioni con Sottospazi di R alla n#Forma Cartesiana|nucleo]] di $B$ se e solo se lo spazio delle righe di $B$ coincide con il nucleo di $A$.
$$\text{row}(A) = \ker(B) \iff \text{row}(B) = \ker(A)$$
*(Questa proprietà è alla base della conversione dalla forma parametrica alla forma cartesiana)*.

### Lemmi (Comparazione di Sottospazi)
**Nome:** *Lemmi di Confronto*
Siano $U, W$ sottospazi di uno spazio vettoriale $V$ di dimensione finita.
1.  **Uguaglianza per dimensione:** Se $U \subseteq W$ e $\dim(U) = \dim(W)$, allora $U = W$. (Questo è un corollario diretto della *Limitazione sulla Dimensione dei Sottospazi*).
2.  **Inclusione da base:** Sia $B_U$ una base di $U$. Se tutti i vettori di $B_U$ appartengono a $W$ ($B_U \subseteq W$), allora $U \subseteq W$.
3.  **Equivalenze di inclusione:** Le seguenti affermazioni sono equivalenti:
    * $U \subseteq W$
    * $U \cap W = U$
    * $U + W = W$

---

## Applicazioni Lineari (Omomorfismi)

### Proposizione (Immagine del Vettore Nullo)
**Nome:** *Conservazione del Vettore Nullo*
Se $f: V \to W$ è un'[[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Definizione di Applicazione Lineare (Omomorfismo)|applicazione lineare]], allora l'immagine del vettore nullo del dominio è il vettore nullo del codominio:
$$f(0_V) = 0_W$$

### Proposizione (Definizione tramite Azione sulla Base)
**Nome:** *Esistenza e Unicità dell'Omomorfismo*
Dati due [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|spazi vettoriali]] $V$ e $W$, una [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Base|base]] $B = \{b_1, \dots, b_n\}$ di $V$ e $n$ vettori arbitrari $w_1, \dots, w_n \in W$, esiste ed è **unico** l'omomorfismo $f: V \to W$ tale che:
$$f(b_i) = w_i \quad \forall i=1, \dots, n$$
*(L'applicazione lineare è completamente determinata dalla sua azione su una base del dominio)*.

### Teorema (Struttura di Nucleo e Immagine)
**Nome:** *Nucleo e Immagine come Sottospazi*
Sia $f: V \to W$ un'applicazione lineare. Allora:
1.  Il [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Nucleo (Kernel)|Nucleo]] di $f$, $\text{Ker}(f)$, è un sottospazio vettoriale del dominio $V$.
2.  L'[[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Immagine (Im)|Immagine]] di $f$, $\text{Im}(f)$, è un sottospazio vettoriale del codominio $W$.

### Corollario (Generatori dell'Immagine)
**Nome:** *Immagine dei Generatori*
Sia $f: V \to W$ un'applicazione lineare. Se $V$ è [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Sistemi di Generatori|generato]] da un insieme di vettori $S = \{v_1, \dots, v_n\}$, allora $\text{Im}(f)$ è generata dalle immagini di questi vettori:
$$\text{Im}(f) = \text{Span}(f(v_1), \dots, f(v_n))$$

### Teorema (Teorema della Dimensione per Applicazioni Lineari)
**Nome:** *Teorema della Dimensione (o Rango-Nullità)*
Sia $f: V \to W$ un'applicazione lineare e sia $V$ uno spazio vettoriale di dimensione finita. Allora vale la seguente relazione:
$$\dim(V) = \dim(\text{Ker}(f)) + \dim(\text{Im}(f))$$
La dimensione del dominio è la somma della dimensione del nucleo (**nullità**) e della dimensione dell'immagine (**rango**).
*(Questo è l'analogo per le applicazioni lineari del [[Teoremi, Corollari, Lemmi e Proposizioni per gli spazi vettoriali#^58117a|Teorema Rango-Nullità]] definito per le matrici)*.

### Proposizione (Criterio di Iniettività)
**Nome:** *Caratterizzazione dell'Iniettività tramite Nucleo*
Un'applicazione lineare $f: V \to W$ è iniettiva (un **monomorfismo**) se e solo se il suo nucleo è il sottospazio nullo:
$$f \text{ è iniettiva} \iff \text{Ker}(f) = \{0_V\}$$
(Ovvero, $\dim(\text{Ker}(f)) = 0$).

### Proposizione (Caratterizzazione tramite Immagine di Base)
**Nome:** *Criteri di Classificazione su Base*
Sia $f: V \to W$ un'applicazione lineare, $\dim(V)=n$, e $B = \{b_1, \dots, b_n\}$ una base di $V$.
1.  $f$ è **iniettiva** (monomorfismo) $\iff$ l'insieme $\{f(b_1), \dots, f(b_n)\}$ è linearmente indipendente in $W$.
2.  $f$ è **suriettiva** (epimorfismo) $\iff$ l'insieme $\{f(b_1), \dots, f(b_n)\}$ genera $W$.
3.  $f$ è **biettiva** (isomorfismo) $\iff$ l'insieme $\{f(b_1), \dots, f(b_n)\}$ è una base di $W$.

### Corollario (Teorema Fondamentale degli Isomorfismi)
**Nome:** *Criterio Dimensionale per Isomorfismo*
Due spazi vettoriali $V$ e $W$ di dimensione finita sono [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Proprietà delle Applicazioni Lineari Iniettività Suriettività Biettività|isomorfi]] se e solo se hanno la stessa dimensione.
$$V \cong W \iff \dim(V) = \dim(W)$$