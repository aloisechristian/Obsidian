# Sistemi di Equazioni Lineari

## Introduzione: Ritorno al Problema Fondamentale
Dopo aver acquisito familiarità con le [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#^1f6aea|matrici]] e le operazioni ad esse associate, si ritorna al problema fondamentale che ha motivato la loro introduzione: la risoluzione efficiente dei sistemi di equazioni lineari. Come visto nell'esempio della ricetta, un problema con poche variabili può essere risolto per sostituzione, ma all'aumentare della complessità questo metodo diventa laborioso e richiede troppo tempo. Le matrici offrono un linguaggio e strumenti potenti per analizzare e risolvere tali sistemi in modo sistematico e computazionalmente efficiente.

## Definizione di Sistema Lineare
Un **sistema di equazioni lineari** è un insieme di $m$ equazioni di primo grado in $n$ incognite (o variabili) $x_1, x_2, \dots, x_n$ che devono essere risolte simultaneamente. La sua forma generale è la seguente:
$$
\begin{cases}
a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n = b_1 \\
a_{21}x_1 + a_{22}x_2 + \dots + a_{2n}x_n = b_2 \\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \dots + a_{mn}x_n = b_m
\end{cases}
$$
Dove:
-   $a_{ij} \in \mathbb{R}$ sono i **coefficienti** del sistema.
-   $x_j$ sono le **incognite** o **variabili**.
-   $b_i \in \mathbb{R}$ sono i **termini noti**.

Una **soluzione** del sistema è una n-upla di numeri $(x_1, x_2, \dots, x_n)$ che soddisfa contemporaneamente tutte le $m$ equazioni.

## Rappresentazione Matriciale di un Sistema Lineare
La struttura tabulare dei coefficienti suggerisce una rappresentazione più compatta ed elegante tramite le matrici. Un sistema lineare può essere interamente descritto definendo tre matrici:

1.  **La Matrice dei Coefficienti (A):** Una matrice $A \in M_{m,n}(\mathbb{R})$ che raccoglie tutti i coefficienti $a_{ij}$.
    $$ A = \begin{pmatrix} a_{11} & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22} & \dots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \dots & a_{mn} \end{pmatrix} $$
2.  **Il Vettore delle Incognite (x):** Una matrice colonna $x \in M_{n,1}(\mathbb{R})$ che contiene le variabili.
    $$ x = \begin{pmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{pmatrix} $$
3.  **Il Vettore dei Termini Noti (B):** Una matrice colonna $B \in M_{m,1}(\mathbb{R})$ che contiene i termini noti.
    $$ B = \begin{pmatrix} b_1 \\ b_2 \\ \vdots \\ b_m \end{pmatrix} $$

Utilizzando la definizione di [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Il Prodotto Riga per Colonna|prodotto righe per colonne]], il sistema lineare può essere riscritto nella forma concisa:
$$ Ax = B $$
Il prodotto $A \cdot x$ genera infatti una matrice colonna $m \times 1$, il cui $i$-esimo elemento è proprio il lato sinistro della $i$-esima equazione del sistema. Questa **notazione matriciale** non solo semplifica la scrittura, ma permette di applicare gli strumenti dell'algebra matriciale al problema.

## Strategia di Soluzione: L'Algoritmo di Gauss-Jordan
L'[[Geometria e Algebra/Algoritmo di Eliminazione di Gauss Jordan|algoritmo di Gauss-Jordan]], già studiato per la riduzione a scala di matrici, è lo strumento principale per la risoluzione dei sistemi. La procedura si articola nei seguenti passaggi:

1.  **Costruzione della Matrice Completa (o Aumentata):** Si costruisce una nuova matrice, indicata con $[A|B] \in M_{m,n+1}(\mathbb{R})$, affiancando la colonna dei termini noti $B$ alla matrice dei coefficienti $A$. Questa matrice contiene tutte le informazioni numeriche del sistema.
    $$ [A|B] = \left( \begin{array}{cccc|c} a_{11} & a_{12} & \dots & a_{1n} & b_1 \\ a_{21} & a_{22} & \dots & a_{2n} & b_2 \\ \vdots & \vdots & \ddots & \vdots & \vdots \\ a_{m1} & a_{m2} & \dots & a_{mn} & b_m \end{array} \right) $$

2.  **Riduzione a Scala:** Si applica l'algoritmo di Gauss-Jordan alla matrice completa $[A|B]$ per trasformarla nella sua forma a scala ridotta (reduced row echelon form), utilizzando le [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Scopo del Gioco e Regole: Le Operazioni Elementari di Riga|operazioni elementari di riga]].

3.  **Lettura delle Soluzioni:** Si reinterpreta la matrice ridotta come un nuovo sistema lineare equivalente a quello di partenza, dal quale la lettura delle soluzioni è immediata.

### Fondamento delle Operazioni di Gauss-Jordan
Le tre operazioni elementari di riga non sono arbitrarie. Esse corrispondono a manipolazioni algebriche sulle equazioni di un sistema che producono un **sistema equivalente**, ovvero un sistema che ha lo stesso insieme di soluzioni di quello di partenza:
-   **Scambio di due righe:** Corrisponde a scambiare l'ordine di due equazioni.
-   **Moltiplicazione di una riga per uno scalare non nullo:** Corrisponde a moltiplicare entrambi i membri di un'equazione per lo stesso numero.
-   **Somma di una riga con un multiplo di un'altra:** Corrisponde a sommare a un'equazione un multiplo di un'altra equazione.

## Analisi delle Soluzioni

Dalla forma a scala ridotta della matrice completa, possono emergere tre scenari distinti.

### Esempio 1: Sistema con Soluzione Unica
Un sistema ammette una sola soluzione quando, dopo la riduzione, ogni variabile corrisponde a un pivot.
$$
\begin{cases}
x_1 + 2x_2 + 3x_3 = 6 \\
x_2 + x_3 = 2 \\
2x_2 + x_3 = 2
\end{cases}
\implies
[A|B] = \left( \begin{array}{ccc|c} 1 & 2 & 3 & 6 \\ 0 & 1 & 1 & 2 \\ 0 & 2 & 1 & 2 \end{array} \right)
\xrightarrow{\text{Gauss-Jordan}}
\left( \begin{array}{ccc|c} 1 & 0 & 0 & 0 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 1 & 2 \end{array} \right)
$$
Questo corrisponde al sistema semplificato $x_1 = 0, x_2 = 0, x_3 = 2$. La soluzione unica è la terna $(0, 0, 2)$.

### Esempio 2: Sistema Impossibile (Nessuna Soluzione)
Un sistema non ammette soluzioni se, durante il processo di riduzione, si genera una riga che rappresenta una contraddizione.
$$
\begin{cases}
x_1 + x_2 - x_3 = 0 \\
2x_1 + x_2 - x_3 = 1 \\
3x_1 + 2x_2 - 2x_3 = 2
\end{cases}
\implies
[A|B] = \left( \begin{array}{ccc|c} 1 & 1 & -1 & 0 \\ 2 & 1 & -1 & 1 \\ 3 & 2 & -2 & 2 \end{array} \right)
\xrightarrow{\text{Gauss-Jordan}}
\left( \begin{array}{ccc|c} 1 & 0 & 0 & 1 \\ 0 & 1 & -1 & -1 \\ 0 & 0 & 0 & 1 \end{array} \right)
$$
L'ultima riga corrisponde all'equazione $0 \cdot x_1 + 0 \cdot x_2 + 0 \cdot x_3 = 1$, ovvero $0 = 1$. Poiché questa è un'equazione impossibile, il sistema non ammette alcuna soluzione.

### Esempio 3: Sistema con Infinite Soluzioni
Quando, dopo la riduzione, il numero di pivot è inferiore al numero di incognite, il sistema ammette infinite soluzioni. Le variabili che non corrispondono a colonne con pivot sono dette **parametri liberi**.
$$
\begin{cases}
x_1 + x_2 - x_3 + x_4 = 0 \\
2x_1 + x_2 - x_3 + 2x_4 = 1 \\
x_1 + x_3 + x_4 = 2
\end{cases}
\xrightarrow{\text{Gauss-Jordan}}
\left( \begin{array}{cccc|c} 1 & 0 & 0 & 2 & -1 \\ 0 & 1 & 0 & 0 & -1 \\ 0 & 0 & 1 & 0 & 1 \end{array} \right)
$$
La variabile $x_4$ non corrisponde a un pivot e diventa un parametro libero. Ponendo $x_4 = t$, con $t \in \mathbb{R}$, le soluzioni si esprimono in funzione di $t$:
$$
\begin{cases}
x_1 + 2x_4 = -1 \\ 
x_2 = -1 \\
x_3 = 1
\end{cases} 
\implies
\begin{cases}
x_1 = -1 - 2x_4 \\ 
x_2 = -1 \\ 
x_3 = 1
\end{cases}
$$
Per ogni valore reale scelto per il parametro $x_4$, si ottiene una soluzione valida del sistema, data dalla 4-upla $(-1-2t, -1, 1, t)$.

## Il Teorema di Rouché-Capelli
Il teorema di Rouché-Capelli fornisce un criterio preciso per determinare l'esistenza e il numero di soluzioni di un sistema lineare prima di calcolarle esplicitamente, basandosi sul concetto di [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]].

Sia $Ax=B$ un sistema lineare con $m$ equazioni e $n$ incognite. Siano $Rk(A)$ il rango della matrice dei coefficienti e $Rk([A|B])$ il rango della matrice completa.

1.  **Compatibilità:** Il sistema ammette soluzioni se e solo se il rango della matrice dei coefficienti è uguale al rango della matrice completa.
    $$ \text{Il sistema ha soluzioni} \iff Rk(A) = Rk([A|B]) $$
    Se $Rk(A) \neq Rk([A|B])$, il sistema è detto **incompatibile** o **impossibile**. Ciò accade quando la riduzione a scala genera un pivot nell'ultima colonna della matrice completa, portando a una contraddizione del tipo $0=k$ con $k \neq 0$.

2.  **Numero di Soluzioni:** Se il sistema è compatibile e si pone $r = Rk(A) = Rk([A|B])$, allora il numero di soluzioni dipende dalla relazione tra $r$ e il numero di incognite $n$:
    -   Se $r=n$, il sistema ammette **una e una sola soluzione**.
    -   Se $r<n$, il sistema ammette **infinite soluzioni**. Le soluzioni dipendono da $n-r$ parametri liberi.

## Sistemi Omogenei e Struttura delle Soluzioni

### Sistemi Omogenei
Un sistema lineare si dice **omogeneo** se tutti i termini noti sono nulli, ovvero se ha la forma $Ax=0$.
-   Un sistema omogeneo è **sempre compatibile**, poiché ammette sempre almeno la **soluzione banale** (o nulla), in cui tutte le incognite sono pari a zero: $x = (0, 0, \dots, 0)$.
-   Dal teorema di Rouché-Capelli, poiché $Rk(A) = Rk([A|0])$, le soluzioni dipendono da $n - Rk(A)$ parametri liberi. Esistono soluzioni non banali se e solo se $Rk(A) < n$.

### Struttura Generale delle Soluzioni
Esiste una relazione profonda tra le soluzioni di un sistema non omogeneo $Ax=B$ e quelle del **sistema omogeneo associato** $Ax=0$.

Sia $\Sigma$ l'insieme delle soluzioni di $Ax=B$ e $\Sigma_0$ l'insieme delle soluzioni di $Ax=0$.
1.  La **differenza** tra due soluzioni qualsiasi di $Ax=B$ è una soluzione del sistema omogeneo associato. Se $y, y' \in \Sigma$, allora $A(y-y') = Ay - Ay' = B - B = 0$, quindi $(y-y') \in \Sigma_0$.
2.  La **somma** di una soluzione particolare di $Ax=B$ e una qualsiasi soluzione di $Ax=0$ è ancora una soluzione di $Ax=B$. Se $y \in \Sigma$ e $z \in \Sigma_0$, allora $A(y+z) = Ay + Az = B + 0 = B$, quindi $(y+z) \in \Sigma$.

Questo implica che l'insieme di tutte le soluzioni di un sistema non omogeneo può essere descritto come la traslazione dell'insieme delle soluzioni dell'omogeneo associato tramite una soluzione particolare:
$$ \Sigma = y_p + \Sigma_0 = \{ y_p + z \mid z \in \Sigma_0 \} $$
dove $y_p$ è una **soluzione particolare** qualsiasi di $Ax=B$. In pratica, per trovare tutte le soluzioni di un sistema, è sufficiente trovare *una* soluzione particolare e sommarla a *tutte* le soluzioni del sistema omogeneo associato.

## Il Teorema di Cramer (Metodo dei Determinanti)
Oltre al metodo di Gauss-Jordan, esiste un approccio alternativo per la risoluzione di un sistema lineare che fa uso dei determinanti. Questo metodo, noto come **Teorema di Cramer**, fornisce una formula esplicita per calcolare la soluzione, ma è applicabile solo a sistemi che rispettano condizioni molto specifiche.

> **Teorema (Cramer):**
> Sia $Ax = B$ un sistema lineare con $n$ equazioni in $n$ incognite (quindi con la matrice dei coefficienti $A$ quadrata di ordine $n$).
> Se la matrice $A$ è [[03 - Rango, Invertibilità delle Matrici e Permutazioni|invertibile]], ovvero se $\det(A) \neq 0$, allora il sistema ammette **una e una sola soluzione**.
> Tale soluzione è data da:
> $$ x_i = \frac{\det(A_i)}{\det(A)} \quad \text{per } i = 1, 2, \dots, n $$
> Dove $A_i$ è la matrice ottenuta sostituendo la $i$-esima colonna della matrice $A$ con il vettore dei termini noti $B$.

### Dimostrazione
La dimostrazione del teorema è una diretta conseguenza della formula per il calcolo della [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Algoritmo per il Calcolo della Matrice Inversa|matrice inversa]] tramite la matrice aggiunta.

1.  Poiché per ipotesi $A$ è invertibile, la soluzione del sistema $Ax=B$ è unica e data da $x = A^{-1}B$.
2.  Ricordiamo la formula per l'inversa che utilizza la [[Geometria e Algebra/04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#Applicazione Pratica e Matrice Aggiunta|matrice aggiunta]] $A^*$:
    $$ A^{-1} = \frac{1}{\det(A)} A^* $$
3.  Sostituendo, otteniamo l'espressione per il vettore soluzione $x$:
    $$ x = \frac{1}{\det(A)} (A^* B) $$
4.  Analizziamo la generica componente $x_i$ di questo vettore. Essa è data dal prodotto della $i$-esima riga di $A^*$ per la colonna $B$, il tutto diviso per $\det(A)$. Ricordando che $A^*$ è la trasposta della matrice dei cofattori, l'elemento $(A^*)_{ij}$ è il cofattore $a_{ji}^* = (-1)^{j+i}|A_{ji}|$. Quindi:
    $$ x_i = \frac{1}{\det(A)} \sum_{j=1}^{n} (A^*)_{ij} b_j = \frac{1}{\det(A)} \sum_{j=1}^{n} b_j \cdot a_{ji}^* = \frac{1}{\det(A)} \sum_{j=1}^{n} b_j (-1)^{j+i} |A_{ji}| $$
5.  Consideriamo ora il determinante della matrice $A_i$. Se calcoliamo $\det(A_i)$ utilizzando lo [[04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#Teorema di Laplace per il Calcolo del Determinante|sviluppo di Laplace]] lungo la sua $i$-esima colonna (che è esattamente il vettore $B$), otteniamo:
    $$ \det(A_i) = \sum_{j=1}^{n} b_j \cdot (\text{cofattore dell'elemento in posizione } (j,i)) = \sum_{j=1}^{n} b_j \cdot a_{ji}^* $$
6.  Confrontando le due espressioni, si vede che la sommatoria nella formula di $x_i$ è esattamente $\det(A_i)$. Sostituendo, si ottiene la tesi:
    $$ x_i = \frac{\det(A_i)}{\det(A)} $$

### Vantaggi e Svantaggi
-   **Vantaggi:** Il metodo di Cramer fornisce una formula diretta ed elegante. Può risultare più rapido del metodo di Gauss-Jordan per sistemi molto piccoli (es. $2 \times 2$ o $3 \times 3$) o per matrici che contengono molti zeri, poiché ciò semplifica notevolmente il calcolo dei determinanti con lo sviluppo di Laplace.
-   **Svantaggi:** Per sistemi di dimensioni maggiori, il metodo di Cramer diventa computazionalmente molto oneroso. Richiede il calcolo di $n+1$ determinanti di ordine $n$, un'operazione la cui complessità cresce in modo fattoriale ($n!$). L'[[Geometria e Algebra/Algoritmo di Eliminazione di Gauss Jordan|algoritmo di Gauss-Jordan]] è, nella maggior parte dei casi, molto più efficiente ed è il metodo standard utilizzato nei calcolatori.
