# Introduzione alla Geometria Affine

## 1. Relazione tra Algebra Lineare e Geometria
Il passaggio dall'algebra lineare alla geometria avviene sfruttando la struttura vettoriale di $\mathbb{R}^n$. Mentre intuitivamente siamo portati a visualizzare $\mathbb{R}^1$ come una retta, $\mathbb{R}^2$ come un piano e così via, è necessario formalizzare la distinzione tra oggetti algebrici e oggetti geometrici per trattare spazi di dimensione $n \ge 4$, non visualizzabili graficamente.
Questo processo di astrazione ci permette di trattare problemi geometrici complessi utilizzando gli strumenti di calcolo matriciale (vedi [[Geometria e Algebra/01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali.md|Algebra Lineare]]).

## 2. Spazi Vettoriali e Spazi Affini
È fondamentale distinguere tra due strutture collegate ma distinte, come evidenziato anche nelle dispense del corso:

* **Spazio Vettoriale ($\mathbb{R}^n$):** È l'insieme delle $n$-uple di numeri reali considerate come **vettori**. Un vettore è un'entità definita da modulo, direzione e verso. Può essere visualizzato come un **segmento orientato** che parte dall'origine. In questo spazio sono definite le operazioni di somma tra vettori e moltiplicazione per scalare, che formano la struttura portante definita in [[Geometria e Algebra/06 - Spazi Vettoriali, Sottospazi e Loro Operazioni.md|Spazi Vettoriali]].
* **Spazio Affine ($A^n$):** È l'insieme delle $n$-uple considerate come **punti**. Un punto è un'entità puramente posizionale, priva di struttura vettoriale intrinseca. Non ha senso sommare due punti o moltiplicare un punto per uno scalare ("I punti non hanno questa struttura").

### Operazioni nello Spazio Affine
Sebbene i punti non si possano sommare tra loro ("Non ha senso sommare due punti"), esistono relazioni fondamentali che collegano lo spazio affine $A^n$ allo spazio vettoriale $\mathbb{R}^n$:

1. **Somma Punto-Vettore (Traslazione):** Dato un punto $P \in A^n$ e un vettore $v \in \mathbb{R}^n$, la somma $P+v$ definisce un nuovo punto $Q \in A^n$.
   $$+ : A^n \times \mathbb{R}^n \to A^n, \quad (P, v) \mapsto P+v$$
   Geometricamente, questo corrisponde alla traslazione di $P$ lungo il vettore $v$.
   
2. **Differenza tra Punti:** Dati due punti $P, Q \in A^n$, la loro differenza $Q - P$ restituisce un vettore $v \in \mathbb{R}^n$.
   $$- : A^n \times A^n \to \mathbb{R}^n, \quad (P, Q) \mapsto Q-P$$
   Questo vettore corrisponde al **segmento orientato** che congiunge $P$ a $Q$ (o equivalentemente, il vettore che traslato nell'origine rappresenta lo spostamento da $P$ a $Q$).

In coordinate, se $P=(p_1, \dots, p_n)$ e $v=(v_1, \dots, v_n)$, allora:
$$P+v = (p_1+v_1, \dots, p_n+v_n)$$

## 3. Sottospazi Affini
Un **sottospazio affine** $\Sigma$ di $A^n$ non è altro che la traslazione di un sottospazio vettoriale mediante un punto. Formalmente:

$$\Sigma = P + H = \{ P+v \mid v \in H \}$$

Dove:
* $P \in A^n$ è il **punto di applicazione** (o origine locale).
* $H \subseteq \mathbb{R}^n$ è un sottospazio vettoriale, detto **giacitura** o *spazio direttore*.

> [!example] Esempio
> [cite_start]Se $P \in A^n$, allora il singoletto $\{P\}$ è un sottospazio affine di dimensione 0, in quanto $\{P\} = P + \{0\}$[cite: 692].

### Connessione con i Sistemi Lineari
Questa definizione chiude il cerchio con la teoria dei sistemi lineari trattata in [[Geometria e Algebra/05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer.md|Sistemi Lineari]]. L'insieme delle soluzioni di un sistema lineare risolubile $Ax=b$ è sempre un sottospazio affine. La soluzione generale si scrive come:
$$\Sigma = z + \ker(A)$$
dove:
* $z$ è una **soluzione particolare** del sistema non omogeneo (il punto di applicazione $P$)[cite: 703].
* $\ker(A)$ è lo spazio delle soluzioni del sistema omogeneo associato $Ax=0$ (la giacitura $H$).

## 4. Dimensione e Classificazione
La dimensione di un sottospazio affine $\Sigma = P + H$ è definita come la dimensione del suo spazio direttore $H$.
$$\dim(\Sigma) := \dim(H)$$

Classificazione standard:
* **Dimensione 0:** Punto.
* **Dimensione 1:** Retta.
* **Dimensione 2:** Piano.
* **Dimensione $n-1$:** Iperpiano.

Ad esempio, in $A^4$, una retta ha dimensione 1, un piano ha dimensione 2 e un iperpiano ha dimensione 3.

### Famiglie di Sottospazi Affini
Variando il punto di applicazione o la giacitura, si ottengono diverse "famiglie" di sottospazi :
1. **Fascio di sottospazi paralleli:** Fissata una giacitura $H$, al variare di $P$ si ottiene l'insieme di tutti i sottospazi paralleli a $H$ ($\Omega_H = \{P+H \mid P \in A^n\}$).
2. **Stella di sottospazi:** Fissato un punto $P$, al variare della giacitura $H$ (di dimensione fissa $m$) si ottiene l'insieme di tutti i sottospazi passanti per $P$.

## 5. Rappresentazioni: Parametrica e Cartesiana
Esiste una dualità nella rappresentazione dei sottospazi affini:

1. **Forma Parametrica:** Scrittura come somma di un punto e una combinazione lineare di vettori della base di $H$:
   $$\Sigma = P + \langle v_1, \dots, v_k \rangle = \{ P + t_1 v_1 + \dots + t_k v_k \mid t_i \in \mathbb{R} \}$$
   *Vantaggio:* È la forma più facile da "disegnare" o visualizzare.
   
2. **Forma Cartesiana:** Rappresentazione come luogo delle soluzioni di un sistema lineare:
   $$\Sigma : Ax = b$$
   *Vantaggio:* È spesso più facile da comunicare in forma compatta e utile per verificare l'appartenenza di un punto.

### Passaggio tra le forme
Il passaggio dalla cartesiana alla parametrica equivale a risolvere il sistema lineare. Il passaggio inverso (parametrica $\to$ cartesiana) richiede di trovare un sistema $Ax=b$ il cui nucleo sia generato dai vettori direttori della parametrica.

> [!info] Algoritmo Parametrica $\to$ Cartesiana
> Se hai $H = \langle v_1, \dots, v_k \rangle$, costruisci una matrice con i vettori $v_i$ come righe e calcolane il nucleo (o usa l'eliminazione di Gauss per trovare le equazioni cartesiane del sottospazio vettoriale). Poi determina il termine noto $b$ imponendo il passaggio per il punto $P$.
> Vedi [[Geometria e Algebra/Algoritmo di Eliminazione di Gauss Jordan.md|Algoritmo di Gauss-Jordan]].

## 6. Posizione Reciproca e Intersezioni
Per studiare l'intersezione di due sottospazi affini $\Sigma_1$ e $\Sigma_2$, si utilizza spesso la forma cartesiana combinata. Se $\Sigma_1: A_1 x = b_1$ e $\Sigma_2: A_2 x = b_2$, l'intersezione è data dal sistema complessivo:
$$\begin{pmatrix} A_1 \\ A_2 \end{pmatrix} x = \begin{pmatrix} b_1 \\ b_2 \end{pmatrix}$$

Applicando il [[Geometria e Algebra/05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer.md|Teorema di Rouché-Capelli]], analizziamo i ranghi per determinare la natura dell'intersezione.

### Parallelismo e Sghembità
Date due sottospazi $\Sigma_1 = P_1 + H_1$ e $\Sigma_2 = P_2 + H_2$:

1. **Paralleli:** Si dicono paralleli se le loro giaciture sono una contenuta nell'altra (es. $H_1 \subseteq H_2$ o viceversa). 
   *Nota:* Due sottospazi paralleli e distinti hanno sempre intersezione vuota ($\Sigma_1 \cap \Sigma_2 = \emptyset$).
   
2. **Sghembi:** Si dicono sghembi se **non** sono paralleli e la loro intersezione è vuota ($\Sigma_1 \cap \Sigma_2 = \emptyset$). Questo accade tipicamente in dimensioni superiori a 2 (es. due rette in $\mathbb{R}^3$ che non si toccano e non sono parallele).

3. **Incidenti:** Se l'intersezione non è vuota.