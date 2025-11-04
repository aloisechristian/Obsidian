## Lo Spazio Vettoriale degli Omomorfismi

### Definizione e Notazione
Un [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Applicazioni Lineari (Omomorfismi)|omomorfismo]] tra due [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Spazi Vettoriali|spazi vettoriali]] $V$ e $W$ è una funzione $F: V \to W$ che preserva le operazioni di [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Vettori|somma]] e [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Prodotto per Scalare|prodotto per scalare]]. L'insieme di tutti gli omomorfismi da $V$ a $W$ è un oggetto di grande interesse. Per comodità, a tale insieme viene assegnata una notazione specifica: $Hom(V, W)$.

Esistono notazioni alternative in letteratura:
- $L(V, W)$, dove $L$ sta per "Lineare", comune nei testi italiani.
- $Mor(V, W)$, dove "Mor" sta per "Morfismi", utilizzata in testi di matematica più avanzati.

### Struttura di Spazio Vettoriale
L'obiettivo è dotare l'insieme $Hom(V, W)$ di una [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Spazi Vettoriali|struttura di spazio vettoriale]]. A tal fine, è necessario definire un'operazione di somma e un'operazione di prodotto per uno scalare.

#### Somma di Omomorfismi
Dati due omomorfismi $F, G \in Hom(V, W)$, la loro somma, denotata con $F+G$, è una funzione da $V$ in $W$ definita puntualmente come segue:
$$(F+G)(v) = F(v) + G(v) \quad \forall v \in V$$ 
Poiché $F(v)$ e $G(v)$ sono entrambi vettori in $W$, la loro somma è ben definita in $W$. È necessario verificare che la funzione risultante $F+G$ sia essa stessa un omomorfismo:
1.  **Rispetto della somma:**
    $$\begin{aligned} (F+G)(v_1 + v_2) &= F(v_1 + v_2) + G(v_1 + v_2) \\ &= (F(v_1) + F(v_2)) + (G(v_1) + G(v_2)) \\ &= (F(v_1) + G(v_1)) + (F(v_2) + G(v_2)) \\ &= (F+G)(v_1) + (F+G)(v_2) \end{aligned}$$ 
2.  **Rispetto del prodotto per scalare:**
    $$\begin{aligned} (F+G)(\lambda v) &= F(\lambda v) + G(\lambda v) \\ &= \lambda F(v) + \lambda G(v) \\ &= \lambda (F(v) + G(v)) \\ &= \lambda (F+G)(v) \end{aligned}$$ 
La funzione $F+G$ è dunque un omomorfismo e appartiene a $Hom(V, W)$.

#### Prodotto per Scalare
Dato un omomorfismo $F \in Hom(V, W)$ e uno scalare $\lambda \in \mathbb{R}$, il prodotto $\lambda F$ è una funzione da $V$ in $W$ definita come:
$$(\lambda F)(v) = \lambda F(v) \quad \forall v \in V$$ 
Anche in questo caso, si dimostra con passaggi analoghi che $\lambda F$ è un omomorfismo.

Con queste due operazioni, l'insieme $Hom(V, W)$ soddisfa tutti gli assiomi di uno spazio vettoriale. L'elemento neutro rispetto alla somma è l'**omomorfismo nullo**, ovvero la funzione che mappa ogni vettore di $V$ nel vettore nullo di $W$.

### Casi Particolari: Endomorfismi e Automorfismi
- Un **endomorfismo** è un omomorfismo da uno spazio vettoriale $V$ in sé stesso, ovvero un elemento di $Hom(V, V)$.
- Un **automorfismo** è un endomorfismo che è anche [[11 - Applicazioni Lineari, Basi e Spazi Vettoriali Isomorfi#Isomorfismi|biettivo]] (e quindi invertibile).

### Composizione di Omomorfismi
Essendo funzioni, gli omomorfismi possono essere composti. Se $F: V \to W$ e $G: W \to U$ sono due omomorfismi, la loro [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Composizione di Funzioni|composizione]] $G \circ F$ è una funzione da $V$ a $U$. Si può dimostrare che la composizione di due applicazioni lineari è ancora un'applicazione lineare. Pertanto, $G \circ F \in Hom(V, U)$.

## La Matrice Associata a un Omomorfismo

La discussione precedente rivela una forte analogia strutturale tra lo spazio degli omomorfismi e lo spazio delle [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Matrici|matrici]] (somma, prodotto per scalare, un'operazione simile alla moltiplicazione). Questa sezione formalizza tale corrispondenza.

Siano $V$ e $W$ due [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Spazi Vettoriali|spazi vettoriali]] con $\dim(V) = n$ e $\dim(W) = m$. Fissiamo una [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Base di uno Spazio Vettoriale|base]] $\mathcal{B} = \{v_1, \dots, v_n\}$ per $V$ e una [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Base di uno Spazio Vettoriale|base]] $\mathcal{W} = \{w_1, \dots, w_m\}$ per $W$. Sia $F: V \to W$ un omomorfismo.

L'applicazione $F$ è univocamente determinata dalle immagini dei vettori della base di $V$, ossia dai vettori $F(v_1), \dots, F(v_n) \in W$. Poiché $\mathcal{W}$ è una base di $W$, ogni vettore $F(v_j)$ può essere scritto come [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Combinazioni Lineari|combinazione lineare]] unica dei vettori di $\mathcal{W}$:
$$F(v_j) = \mu_{1j} w_1 + \mu_{2j} w_2 + \dots + \mu_{mj} w_m = \sum_{i=1}^{m} \mu_{ij} w_i$$ 
I coefficienti $\mu_{ij}$ (con $i$ che varia da $1$ a $m$ e $j$ da $1$ a $n$) possono essere organizzati in una matrice.

**Definizione:** La **matrice associata all'omomorfismo $F$ rispetto alle basi $\mathcal{B}$ e $\mathcal{W}$** è la matrice $M \in M_{m \times n}(\mathbb{R})$ le cui [[09 - Rappresentazioni e Operazioni con Sottospazi di R alla n#Vettori Colonna|colonne]] sono i [[08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Vettore delle Coordinate|vettori delle coordinate]] delle immagini dei vettori della base $\mathcal{B}$ rispetto alla base $\mathcal{W}$.
$$M = M_{\mathcal{W}}^{\mathcal{B}}(F) = \begin{pmatrix} \mu_{11} & \mu_{12} & \cdots & \mu_{1n} \\ \mu_{21} & \mu_{22} & \cdots & \mu_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ \mu_{m1} & \mu_{m2} & \cdots & \mu_{mn} \end{pmatrix}$$ 
La j-esima colonna di $M$ è il vettore $[F(v_j)]_{\mathcal{W}}$, ovvero la [[08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Rappresentazione di un Vettore in Base|rappresentazione]] di $F(v_j)$ nella base $\mathcal{W}$.

Questa matrice permette di calcolare l'immagine di un qualsiasi vettore $v \in V$ tramite un prodotto matrice-vettore. Se $v = \sum_{j=1}^{n} \lambda_j v_j$, il suo vettore di coordinate rispetto a $\mathcal{B}$ è $[v]_{\mathcal{B}} = (\lambda_1, \dots, \lambda_n)^T$. Allora, il vettore di coordinate dell'immagine $F(v)$ rispetto a $\mathcal{W}$ è dato da:
$$[F(v)]_{\mathcal{W}} = M \cdot [v]_{\mathcal{B}}$$ 

## Dall'Omomorfismo alla Matrice e Viceversa

Abbiamo stabilito un procedimento per associare una matrice a un omomorfismo, date le basi. È possibile anche il percorso inverso. Dati gli spazi $V$ e $W$ con le basi $\mathcal{B}$ e $\mathcal{W}$, e una [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Matrici|matrice]] $A = (a_{ij}) \in M_{m \times n}(\mathbb{R})$, possiamo definire un unico omomorfismo $F_A: V \to W$ imponendo come devono essere trasformati i vettori della base di $V$:
$$F_A(v_j) := \sum_{i=1}^{m} a_{ij} w_i$$ 
Questa definizione determina completamente l'omomorfismo. Se ora calcoliamo la matrice associata a $F_A$ rispetto alle basi $\mathcal{B}$ e $\mathcal{W}$, otteniamo nuovamente la matrice $A$.

### Teorema di Isomorfismo
Siano $V$ e $W$ spazi vettoriali con $dim(V)=n$ e $dim(W)=m$. Fissate una base $\mathcal{B}$ per $V$ e una base $\mathcal{W}$ per $W$, l'applicazione che associa ad ogni omomorfismo $F \in Hom(V, W)$ la sua matrice rappresentativa $M_{\mathcal{W}}^{\mathcal{B}}(F) \in M_{m \times n}(\mathbb{R})$ è un **[[11 - Applicazioni Lineari, Basi e Spazi Vettoriali Isomorfi#Isomorfismi|isomorfismo di spazi vettoriali]]**. 
$$Hom(V, W) \cong M_{m \times n}(\mathbb{R})$$ 
Questo risultato è fondamentale: stabilisce un'equivalenza tra lo studio degli omomorfismi e lo studio delle matrici. Qualsiasi proprietà o problema relativo agli omomorfismi può essere tradotto e risolto nel linguaggio delle matrici, e viceversa.

## Applicazioni dell'Isomorfismo

### Composizione e Prodotto di Matrici
La composizione di omomorfismi corrisponde al [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Prodotto tra Matrici|prodotto righe per colonne]] delle rispettive matrici associate. Siano $F: V \to W$ e $G: W \to U$ omomorfismi e siano $\mathcal{A}, \mathcal{B}, \mathcal{C}$ basi per $V, W, U$. Allora:
$$M_{\mathcal{C}}^{\mathcal{A}}(G \circ F) = M_{\mathcal{C}}^{\mathcal{B}}(G) \cdot M_{\mathcal{B}}^{\mathcal{A}}(F)$$ 
Un caso notevole è l'omomorfismo identità $id_V: V \to V$. La sua matrice associata rispetto a qualsiasi base $\mathcal{B}$ è la [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Matrice Identità|matrice identità]] $I_n$:
$$M_{\mathcal{B}}^{\mathcal{B}}(id_V) = I_n$$
Come corollario, se $F: V \to V$ è un automorfismo (endomorfismo invertibile), la matrice associata alla sua inversa è l'[[03 - Rango, Invertibilità delle Matrici e Permutazioni#Matrice Inversa|inversa della matrice]] associata a $F$:
$$M(F^{-1}) = (M(F))^{-1}$$ 
Di conseguenza, un endomorfismo è un automorfismo se e solo se la sua matrice associata (rispetto a una qualsiasi base) è [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Invertibilità delle Matrici|invertibile]].

### Kernel e Immagine
Il [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Kernel (Nucleo) di un'Applicazione Lineare|kernel]] e l'[[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Immagine di un'Applicazione Lineare|immagine]] di un omomorfismo $F$ sono legati al [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Spazio Nullo (Kernel) di una Matrice|kernel (spazio nullo)]] e allo [[09 - Rappresentazioni e Operazioni con Sottospazi di R alla n#Spazio delle Colonne (Immagine)|spazio delle colonne]] della sua matrice associata $A$.
- **Kernel:** Il kernel di $F$, $Ker(F)$, è isomorfo al kernel di $A$. I vettori in $Ker(F)$ sono quelli le cui coordinate rispetto alla base del dominio formano un vettore in $Ker(A)$.
- **Immagine:** L'immagine di $F$, $Im(F)$, è isomorfa allo spazio delle colonne di $A$, $Col(A)$. Le colonne di $A$ sono le coordinate dei generatori di $Im(F)$ rispetto alla base del codominio.

### Teorema della Dimensione (Rank-Nullity)
Questo isomorfismo permette una semplice dimostrazione del [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Teorema della Dimensione (o del Rango)|teorema della dimensione]] per gli omomorfismi. Per un omomorfismo $F: V \to W$:
$$\dim(V) = \dim(Ker(F)) + \dim(Im(F))$$ 
Dato che $\dim(Ker(F)) = \text{[[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Nullità di una Matrice|nullità]](A)}$ e $\dim(Im(F)) = \text{[[03 - Rango, Invertibilità delle Matrici e Permutazioni#Rango di una Matrice|rango]](A)}$, e per le matrici vale $\text{numero di colonne} = \text{nullità}(A) + \text{rango}(A)$, il teorema segue direttamente, poiché il numero di colonne di $A$ è $n = \dim(V)$.

## Esempi Pratici

### Esempio 1: Calcolo della matrice associata con basi standard
Sia $F: \mathbb{R}^3 \to \mathbb{R}^2$ definita da $F(x,y,z) = (x+y, y+z)$. Fissiamo le [[08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali#Base Canonica (Standard)|basi standard]] $\mathcal{E}_3$ in $\mathbb{R}^3$ e $\mathcal{E}_2$ in $\mathbb{R}^2$. Per trovare la matrice associata $A$, calcoliamo le immagini dei vettori della base del dominio:
- $F(1,0,0) = (1,0)$
- $F(0,1,0) = (1,1)$
- $F(0,0,1) = (0,1)$
Le colonne della matrice sono questi vettori (già espressi nella base standard del codominio):
$$A = \begin{pmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \end{pmatrix}$$ 

### Esempio 2: Cambio di base
Consideriamo lo stesso omomorfismo $F$, ma con basi diverse:
- Base per $\mathbb{R}^3$: $\mathcal{B} = \{(1,1,0), (1,0,1), (0,1,1)\}$
- Base per $\mathbb{R}^2$: $\mathcal{W} = \{(1,1), (1,-1)\}$
Calcoliamo le immagini dei vettori di $\mathcal{B}$ e le esprimiamo come combinazioni lineari dei vettori di $\mathcal{W}$:
1.  $F(1,1,0) = (2,1) = \frac{3}{2}(1,1) + \frac{1}{2}(1,-1)$. La prima colonna è $(3/2, 1/2)^T$.
2.  $F(1,0,1) = (1,1) = 1(1,1) + 0(1,-1)$. La seconda colonna è $(1,0)^T$.
3.  $F(0,1,1) = (1,2) = \frac{3}{2}(1,1) - \frac{1}{2}(1,-1)$. La terza colonna è $(3/2, -1/2)^T$.
La nuova matrice associata è:
$$M = \begin{pmatrix} 3/2 & 1 & 3/2 \\ 1/2 & 0 & -1/2 \end{pmatrix}$$ 

### Esempio 3: Dall'omomorfismo alla matrice
Data la matrice $A = \begin{pmatrix} 2 & 3 \\ 1 & 5 \end{pmatrix}$, si vuole definire l'omomorfismo $F: \mathbb{R}^2 \to \mathbb{R}^2$ associato rispetto alle basi standard. Le colonne di $A$ definiscono le immagini dei vettori della base standard:
- $F(1,0) = 2(1,0) + 1(0,1) = (2,1)$
- $F(0,1) = 3(1,0) + 5(0,1) = (3,5)$
L'immagine del generico vettore $(x,y)$ è:
$$F(x,y) = F(x(1,0) + y(0,1)) = xF(1,0) + y(F(0,1)) = x(2,1) + y(3,5) = (2x+3y, x+5y)$$