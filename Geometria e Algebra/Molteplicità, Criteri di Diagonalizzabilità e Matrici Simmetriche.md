## Teorema sulla Relazione tra Molteplicità Algebrica e Geometrica

### Enunciato del Teorema
Il teorema fondamentale discusso stabilisce che per qualsiasi autovalore $\lambda$ di una matrice, la sua molteplicità geometrica $mg(\lambda)$ è sempre minore o uguale alla sua molteplicità algebrica $ma(\lambda)$.
- La **molteplicità geometrica** $mg(\lambda)$ è definita come la dimensione dell'autospazio associato all'autovalore $\lambda$.
- La **molteplicità algebrica** $ma(\lambda)$ è il numero di volte che $\lambda$ appare come radice del polinomio caratteristico della matrice.

### Dimostrazione
La dimostrazione procede attraverso i seguenti passaggi:
1.  **Impostazione Iniziale**: Si consideri una matrice quadrata $A$ di ordine $n$, un suo autovalore $\lambda = a$ con molteplicità geometrica $mg(a) = r$. Questo implica che l'autospazio $V_a$ ha dimensione $r$.
2.  **Base dell'Autospazio**: È possibile estrarre una base per l'autospazio $V_a$ composta da $r$ autovettori linearmente indipendenti: $\{v_1, v_2, \dots, v_r\}$.
3.  **Completamento a Base dello Spazio Vettoriale**: Si estende l'insieme di questi $r$ autovettori a una base dell'intero spazio vettoriale di dimensione $n$, aggiungendo $n-r$ vettori appropriati: $B = \{v_1, \dots, v_r, v_{r+1}, \dots, v_n\}$. I vettori aggiunti ($v_{r+1}, \dots, v_n$) non sono necessariamente autovettori.
4.  **Matrice Associata alla Nuova Base**: Si costruisce la matrice $A'$ che rappresenta la stessa trasformazione lineare di $A$, ma rispetto alla nuova base $B$. Le matrici $A$ e $A'$ sono simili e, di conseguenza, condividono lo stesso polinomio caratteristico e gli stessi autovalori.
5.  **Struttura della Matrice $A'$**:
    - Le prime $r$ colonne di $A'$ corrispondono agli autovettori $v_1, \dots, v_r$. Poiché $A v_i = a v_i$ per $i \in \{1, \dots, r\}$, la $i$-esima colonna di $A'$ avrà l'autovalore $a$ sulla diagonale e zero in tutte le altre posizioni.
    - Le restanti $n-r$ colonne hanno elementi non noti a priori.
    - La matrice $A'$ assume una forma a blocchi:
    $$ A' = \begin{pmatrix} a I_r & B \\ 0 & C \end{pmatrix} $$
    dove $I_r$ è la matrice identità di ordine $r$, $0$ è una matrice nulla di dimensione $(n-r) \times r$, e $B$ e $C$ sono sottomatrici di dimensioni appropriate.
6.  **Calcolo del Polinomio Caratteristico**: Il polinomio caratteristico di $A$ è uguale a quello di $A'$.
    $$ p_A(\lambda) = \det(A - \lambda I) = \det(A' - \lambda I) $$
    Calcolando il determinante della matrice a blocchi $A' - \lambda I$:
    $$ \det(A' - \lambda I) = \det \begin{pmatrix} (a - \lambda) I_r & B \\ 0 & C - \lambda I \end{pmatrix} $$
    Utilizzando lo sviluppo di Laplace o la proprietà dei determinanti delle matrici a blocchi triangolari, si ottiene:
    $$ p_A(\lambda) = \det((a - \lambda) I_r) \cdot \det(C - \lambda I) = (a - \lambda)^r \cdot p_C(\lambda) $$
7.  **Conclusione**: Il polinomio caratteristico di $A$ contiene il fattore $(a - \lambda)$ elevato almeno alla potenza $r$. L'autovalore $\lambda=a$ potrebbe essere anche una radice del polinomio caratteristico della sottomatrice $C$, $p_C(\lambda)$. Pertanto, la molteplicità totale di $\lambda=a$ come radice di $p_A(\lambda)$ (la molteplicità algebrica) è maggiore o uguale a $r$. Poiché $r$ è la molteplicità geometrica, si conclude che:
    $$ mg(a) \le ma(a) $$

## Criterio di Diagonalizzabilità

### Enunciato del Teorema
Una matrice quadrata $A$ di ordine $n$ è diagonalizzabile se e solo se sono soddisfatte entrambe le seguenti condizioni:
1.  La somma delle molteplicità algebriche di tutti i suoi autovalori è uguale a $n$. Ciò equivale a dire che il polinomio caratteristico si fattorizza completamente nel campo di riferimento (es. ha $n$ radici reali, contate con molteplicità, se si lavora in $\mathbb{R}$).
2.  Per ogni autovalore $\lambda_i$, la sua molteplicità geometrica è uguale alla sua molteplicità algebrica: $mg(\lambda_i) = ma(\lambda_i)$.

### Dimostrazione (implicazione diretta)
Se le due condizioni sono verificate, è possibile costruire una base di autovettori per lo spazio vettoriale:
- Siano $\lambda_1, \dots, \lambda_k$ gli autovalori distinti con molteplicità algebriche $m_1, \dots, m_k$.
- Dalla prima condizione, $\sum_{i=1}^{k} m_i = n$.
- Dalla seconda condizione, la dimensione di ogni autospazio $V_{\lambda_i}$ è $\text{dim}(V_{\lambda_i}) = m_i$.
- Si può quindi estrarre una base di $m_i$ autovettori da ciascun autospazio $V_{\lambda_i}$.
- L'unione di tutte queste basi forma un insieme di $\sum m_i = n$ vettori.
- Poiché autovettori associati ad autovalori distinti sono linearmente indipendenti, l'intero insieme di $n$ vettori è linearmente indipendente.
- Un insieme di $n$ vettori linearmente indipendenti in uno spazio di dimensione $n$ costituisce una base.
- Avendo trovato una base di autovettori, la matrice $A$ è, per definizione, diagonalizzabile.

## Matrici Simmetriche

### Definizioni
- Una matrice $A$ è **simmetrica** se coincide con la sua trasposta: $A = A^T$. In pratica, ogni riga è uguale alla colonna corrispondente.
- Una matrice $A$ è **antisimmetrica** se la sua trasposta è il suo opposto: $A^T = -A$. Una conseguenza è che gli elementi sulla diagonale principale devono essere tutti nulli.

### Teorema Fondamentale sulle Matrici Simmetriche
Una matrice simmetrica di ordine $n$ a coefficienti reali possiede esattamente $n$ autovalori, tutti reali (contati con la loro molteplicità).
- Questa proprietà è estremamente importante nelle applicazioni pratiche (es. fisica, meccanica), dove le matrici che descrivono i sistemi sono spesso simmetriche (es. la matrice di inerzia) e si richiedono autovalori reali.
- Per contro, le matrici antisimmetriche hanno autovalori puramente immaginari.

## Applicazione alla Risoluzione di Equazioni Differenziali

### Introduzione al Problema
L'algebra lineare, e in particolare la diagonalizzazione, offre strumenti per risolvere sistemi di equazioni differenziali lineari.
- L'equazione differenziale scalare $y' = ay$ ha come soluzione la funzione esponenziale $y(x) = c \cdot e^{ax}$.

### Trasformazione in Sistema Matriciale
1.  **Da Ordine Superiore a Sistema del Primo Ordine**: Un'equazione differenziale di ordine superiore può essere convertita in un sistema di equazioni del primo ordine introducendo nuove funzioni incognite per le derivate.
2.  **Forma Matriciale**: Un sistema di $n$ equazioni differenziali lineari del primo ordine in $n$ funzioni incognite può essere scritto in forma compatta come:
    $$ Y' = AY $$
    dove $Y(x)$ è un vettore le cui componenti sono le funzioni incognite e $Y'(x)$ è il vettore delle loro derivate, mentre $A$ è la matrice dei coefficienti.
3.  **Soluzione Formale**: Per analogia con il caso scalare, la soluzione formale del sistema è:
    $$ Y(x) = e^{Ax} Y_0 $$
    dove $Y_0$ è il vettore delle condizioni iniziali e $e^{Ax}$ è l'**esponenziale di una matrice**.
4.  **Prospettive Future**: La definizione, il significato e il calcolo dell'esponenziale di una matrice $e^A$ rappresentano il passo successivo e richiederanno l'uso di autovalori e autovettori.