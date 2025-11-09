# Matrice Associata e Cambiamento di Base

## Introduzione: Matrice Associata a un'Applicazione Lineare

Questa lezione approfondisce la relazione tra le matrici associate a un'applicazione lineare al variare delle basi scelte per il dominio e il codominio. Sebbene i concetti siano tecnicamente semplici, la materia richiede particolare attenzione per evitare confusioni.

### Ripasso del Concetto Fondamentale

Consideriamo un'applicazione lineare $f: V \to W$ tra due spazi vettoriali $V$ e $W$. Fissate una base $\mathcal{V} = \{v_1, \dots, v_n\}$ per $V$ e una base $\mathcal{W} = \{w_1, \dots, w_m\}$ per $W$, è possibile associare a $f$ un'unica matrice, denotata con $M_f^{\mathcal{V},\mathcal{W}}$.

**Definizione:** La matrice $M_f^{\mathcal{V},\mathcal{W}}$ è la matrice di dimensioni $m \times n$ le cui colonne sono i vettori delle coordinate delle immagini dei vettori della base del dominio, espressi rispetto alla base del codominio. In simboli, la $j$-esima colonna della matrice è il vettore $[f(v_j)]_\mathcal{W}$.

La proprietà fondamentale di questa matrice è che permette di calcolare l'immagine di un qualsiasi vettore $v \in V$ tramite un prodotto matrice-vettore:

$$M_f^{\mathcal{V},\mathcal{W}} \cdot [v]_\mathcal{V} = [f(v)]_\mathcal{W}, \quad \forall v \in V$$

Dove:

- $[v]_\mathcal{V}$ è il vettore delle coordinate di $v$ rispetto alla base $\mathcal{V}$ (una matrice colonna $n \times 1$).
    
- $[f(v)]_\mathcal{W}$ è il vettore delle coordinate di $f(v)$ rispetto alla base $\mathcal{W}$ (una matrice colonna $m \times 1$).
    

## Il Problema del Cambiamento di Base

La matrice associata dipende intrinsecamente dalla scelta delle basi. Se scegliamo una nuova base $\mathcal{B}$ per $V$ e una nuova base $\mathcal{C}$ per $W$, possiamo costruire una nuova matrice $M_f^{\mathcal{B},\mathcal{C}}$ con la stessa proprietà:

$$M_f^{\mathcal{B},\mathcal{C}} \cdot [v]_\mathcal{B} = [f(v)]_\mathcal{C}, \quad \forall v \in V$$

In generale, $M_f^{\mathcal{V},\mathcal{W}} \neq M_f^{\mathcal{B},\mathcal{C}}$. La domanda centrale è: **qual è la relazione tra queste due matrici?** L'obiettivo è capire come la rappresentazione matriciale di un omomorfismo si trasforma al variare delle basi.

## Matrici di Cambiamento di Base

Per collegare le diverse rappresentazioni, introduciamo lo strumento della matrice di cambiamento di base.

### Definizione e Proprietà

Siano $\mathcal{V} = \{v_1, \dots, v_n\}$ e $\mathcal{B} = \{b_1, \dots, b_n\}$ due basi dello stesso spazio vettoriale $V$. Poiché $\mathcal{V}$ è una base, ogni vettore $b_j$ della base $\mathcal{B}$ può essere scritto come combinazione lineare dei vettori di $\mathcal{V}$:

$$b_j = \sum_{i=1}^{n} a_{ij} v_i = a_{1j}v_1 + a_{2j}v_2 + \dots + a_{nj}v_n$$

I coefficienti $a_{ij}$ formano una matrice quadrata $n \times n$, chiamata **matrice di cambiamento di base da** $\mathcal{B}$ **a** $\mathcal{V}$, che indicheremo con $M_I^{\mathcal{B},\mathcal{V}}$. Le colonne di questa matrice sono le coordinate dei vettori della base "nuova" ($\mathcal{B}$) espresse rispetto alla base "vecchia" ($\mathcal{V}$).

$$M_I^{\mathcal{B},\mathcal{V}} = \left( [b_1]_\mathcal{V} \;\; [b_2]_\mathcal{V} \;\; \dots \;\; [b_n]_\mathcal{V} \right)$$

**Interpretazione:** Questa matrice rappresenta l'**applicazione identità** $id: V \to V$, dove si considera la base $\mathcal{B}$ nel dominio e la base $\mathcal{V}$ nel codominio. In simboli: $M_I^{\mathcal{B},\mathcal{V}} = M_{id}^{\mathcal{B},\mathcal{V}}$.

Poiché i vettori di $\mathcal{B}$ sono linearmente indipendenti (essendo una base), le colonne di questa matrice sono linearmente indipendenti. Di conseguenza, la matrice di cambiamento di base ha rango massimo ($n$) ed è sempre **invertibile**.

### Relazione tra le Coordinate di un Vettore

Sia $v \in V$. Le sue coordinate rispetto alla base $\mathcal{V}$, $[v]_\mathcal{V}$, e le sue coordinate rispetto alla base $\mathcal{B}$, $[v]_\mathcal{B}$, sono legate dalla seguente relazione:

$$[v]_\mathcal{V} = M_I^{\mathcal{B},\mathcal{V}} \cdot [v]_\mathcal{B}$$

Questa formula mostra come trasformare le coordinate di un vettore dalla base $\mathcal{B}$ alla base $\mathcal{V}$ ("dalla nuova alla vecchia").

Per ottenere la trasformazione inversa (da $\mathcal{V}$ a $\mathcal{B}$), è sufficiente invertire la matrice:

$$[v]_\mathcal{B} = (M_I^{\mathcal{B},\mathcal{V}})^{-1} \cdot [v]_\mathcal{V}$$

Si noti che l'inversa della matrice di passaggio da $\mathcal{B}$ a $\mathcal{V}$ è la matrice di passaggio da $\mathcal{V}$ a $\mathcal{B}$:

$$(M_I^{\mathcal{B},\mathcal{V}})^{-1} = M_I^{\mathcal{V},\mathcal{B}}$$

## La Formula del Cambiamento di Base per Applicazioni Lineari

Sfruttando le matrici di cambiamento di base, possiamo ora derivare la relazione tra $M_f^{\mathcal{V},\mathcal{W}}$ e $M_f^{\mathcal{B},\mathcal{C}}$.

### Derivazione della Formula

Partiamo dalla relazione fondamentale che definisce la "vecchia" matrice:

$$[f(v)]_\mathcal{W} = M_f^{\mathcal{V},\mathcal{W}} \cdot [v]_\mathcal{V}$$

Applichiamo le formule del cambiamento di base sia nel dominio $V$ che nel codominio $W$:

- In $V$ (Dominio): $[v]_\mathcal{V} = M_I^{\mathcal{B},\mathcal{V}} \cdot [v]_\mathcal{B}$
    
- In $W$ (Codominio): $[f(v)]_\mathcal{W} = M_I^{\mathcal{C},\mathcal{W}} \cdot [f(v)]_\mathcal{C}$
    

Sostituendo queste espressioni nell'equazione di partenza, otteniamo:

$$M_I^{\mathcal{C},\mathcal{W}} \cdot [f(v)]_\mathcal{C} = M_f^{\mathcal{V},\mathcal{W}} \cdot (M_I^{\mathcal{B},\mathcal{V}} \cdot [v]_\mathcal{B})$$

Poiché la matrice $M_I^{\mathcal{C},\mathcal{W}}$ è invertibile, possiamo moltiplicare a sinistra per la sua inversa, $(M_I^{\mathcal{C},\mathcal{W}})^{-1}$, che è $M_I^{\mathcal{W},\mathcal{C}}$:

$$[f(v)]_\mathcal{C} = (M_I^{\mathcal{C},\mathcal{W}})^{-1} \cdot M_f^{\mathcal{V},\mathcal{W}} \cdot M_I^{\mathcal{B},\mathcal{V}} \cdot [v]_\mathcal{B}$$

Confrontiamo ora questa espressione con la definizione della "nuova" matrice $M_f^{\mathcal{B},\mathcal{C}}$:

$$[f(v)]_\mathcal{C} = M_f^{\mathcal{B},\mathcal{C}} \cdot [v]_\mathcal{B}$$

Per l'unicità della matrice associata a $f$ rispetto a basi fissate, le due matrici che moltiplicano $[v]_\mathcal{B}$ devono essere uguali. Si ottiene così la **formula del cambiamento di base**:

$$M_f^{\mathcal{B},\mathcal{C}} = (M_I^{\mathcal{C},\mathcal{W}})^{-1} \cdot M_f^{\mathcal{V},\mathcal{W}} \cdot M_I^{\mathcal{B},\mathcal{V}}$$

### Il Diagramma Commutativo

La relazione può essere visualizzata tramite un diagramma commutativo, che aiuta a ricordare la formula e le direzioni delle trasformazioni. Il diagramma mostra che si può "andare" da $[v]_\mathcal{B}$ a $[f(v)]_\mathcal{C}$ in due modi che danno lo stesso risultato.

```flowchart TD
    A["\[v\]_B"] -- "M_f^{B,C}" --> B["\[f(v)\]_C"]
    C["\[v\]_V"] -- "M_f^{V,W}" --> D["\[f(v)\]_W"]
    A -- "M_I^{B,V} (da B a V)" --> C
    D -- "(M_I^{C,W})^{-1} (da W a C)" --> B
```

- **Percorso Diretto (sopra):** Moltiplicazione per $M_f^{\mathcal{B},\mathcal{C}}$.
    
- **Percorso Indiretto (sotto):**   1. Trasformare le coordinate da $\mathcal{B}$ a $\mathcal{V}$ (moltiplicando a destra per $M_I^{\mathcal{B},\mathcal{V}}$).   2. Applicare la $f$ nelle "vecchie" basi (moltiplicando per $M_f^{\mathcal{V},\mathcal{W}}$).   3. Trasformare le coordinate da $\mathcal{W}$ a $\mathcal{C}$ (moltiplicando a sinistra per $(M_I^{\mathcal{C},\mathcal{W}})^{-1}$).
    

### Definizione di Matrici Equivalenti

Due matrici $M_1, M_2$ di dimensioni $m \times n$ si dicono **equivalenti** se esistono una matrice invertibile $C$ di dimensioni $m \times m$ e una matrice invertibile $B$ di dimensioni $n \times n$ tali che:

$$M_2 = C^{-1} M_1 B$$

(Nel nostro caso, $C = M_I^{\mathcal{C},\mathcal{W}}$ e $B = M_I^{\mathcal{B},\mathcal{V}}$). Le matrici che rappresentano lo stesso omomorfismo rispetto a coppie di basi diverse sono, per definizione, equivalenti.

## Il Caso Particolare degli Endomorfismi

Un caso di grande importanza è quello degli **endomorfismi**, ovvero applicazioni lineari da uno spazio vettoriale in sé stesso, $f: V \to V$. In questo contesto, si sceglie solitamente la stessa base per il dominio e per il codominio.

Siano $\mathcal{V}$ e $\mathcal{B}$ due basi di $V$. Le matrici associate sono $M_f^{\mathcal{V},\mathcal{V}}$ e $M_f^{\mathcal{B},\mathcal{B}}$, entrambe quadrate $n \times n$.

Applichiamo la formula generale del cambiamento di base ponendo:

- Dominio: $V$, con basi $\mathcal{V}$ e $\mathcal{B}$.
    
- Codominio: $V$, con basi $\mathcal{W}=\mathcal{V}$ e $\mathcal{C}=\mathcal{B}$.
    

La formula $M_f^{\mathcal{B},\mathcal{C}} = (M_I^{\mathcal{C},\mathcal{W}})^{-1} \cdot M_f^{\mathcal{V},\mathcal{W}} \cdot M_I^{\mathcal{B},\mathcal{V}}$ diventa:

$$M_f^{\mathcal{B},\mathcal{B}} = (M_I^{\mathcal{B},\mathcal{V}})^{-1} \cdot M_f^{\mathcal{V},\mathcal{V}} \cdot M_I^{\mathcal{B},\mathcal{V}}$$

Indicando la matrice di cambio base $M_I^{\mathcal{B},\mathcal{V}}$ semplicemente con $B$, la formula diventa:

$$M_f^{\mathcal{B},\mathcal{B}} = B^{-1} \cdot M_f^{\mathcal{V},\mathcal{V}} \cdot B$$

### Definizione di Matrici Simili

Due matrici quadrate $M_1, M_2$ di dimensioni $n \times n$ si dicono **simili** (o _coniugate_) se esiste una matrice invertibile $B$ tale che:

$$M_2 = B^{-1} M_1 B$$

Le matrici che rappresentano lo stesso endomorfismo rispetto a basi diverse sono simili. Questa è una relazione più forte dell'equivalenza e preserva proprietà importanti come il determinante, la traccia e gli autovalori.

## Considerazioni Pratiche

Per calcolare la matrice associata $M_f^{\mathcal{B},\mathcal{C}}$, si possono seguire due approcci: 1.  **Metodo Diretto (Definizione):** Calcolare le immagini $f(b_j)$ dei vettori della base $\mathcal{B}$ e trovare le loro coordinate rispetto alla base $\mathcal{C}$, risolvendo un sistema lineare per ciascuna colonna. Questo metodo è spesso più rapido per calcoli manuali con matrici di piccole dimensioni. 2.  **Formula del Cambiamento di Base:** Calcolare una matrice più semplice (es. $M_f^{E_n, E_m}$ rispetto alle basi canoniche), determinare le matrici di cambiamento di base $B = M_I^{\mathcal{B}, E_n}$ e $C = M_I^{\mathcal{C}, E_m}$, calcolare $C^{-1}$ ed eseguire i prodotti matriciali $C^{-1} \cdot M_f^{E_n, E_m} \cdot B$. Questo metodo è computazionalmente più efficiente per matrici di grandi dimensioni.

## Esempio Svolto: Applicazione da R² a R³

Sia $f: \mathbb{R}^2 \to \mathbb{R}^3$ l'applicazione lineare definita da $f(x, y) = (x+y, x-y, -2y)$. Le coordinate sono intese rispetto alle basi canoniche $E_2$ di $\mathbb{R}^2$ e $E_3$ di $\mathbb{R}^3$.

Consideriamo le seguenti basi:

- Per $\mathbb{R}^2$: $E_2 = \{(1,0), (0,1)\}$ e $\mathcal{B} = \{(1,1), (1,-1)\}$
    
- Per $\mathbb{R}^3$: $E_3 = \{(1,0,0), (0,1,0), (0,0,1)\}$ e $\mathcal{C} = \{(1,1,0), (1,0,1), (0,1,1)\}$
    

### 1. Calcolo della Matrice rispetto alle Basi Standard ($M_f^{E_2, E_3}$)

Calcoliamo le immagini dei vettori della base $E_2$:

- $f(1,0) = (1+0, 1-0, -2 \cdot 0) = (1,1,0)$
    
- $f(0,1) = (0+1, 0-1, -2 \cdot 1) = (1,-1,-2)$
    

Poiché il codominio usa la base canonica $E_3$, le coordinate dei vettori immagine sono i vettori stessi. La matrice è:

$$M_f^{E_2, E_3} = \begin{pmatrix} 1 & 1 \\ 1 & -1 \\ 0 & -2 \end{pmatrix}$$

### 2. Calcolo della Matrice rispetto alle Basi $\mathcal{B}$ e $\mathcal{C}$ ($M_f^{\mathcal{B}, \mathcal{C}}$) - Metodo Diretto

Dobbiamo calcolare le immagini dei vettori di $\mathcal{B}$ ed esprimerle come combinazione lineare dei vettori di $\mathcal{C}$.

**Prima colonna:** Immagine di $b_1 = (1,1)$

- Calcoliamo l'immagine: $f(1,1) = (1+1, 1-1, -2 \cdot 1) = (2,0,-2)$.
    
- Cerchiamo $\lambda_1, \lambda_2, \lambda_3$ tali che $(2,0,-2) = \lambda_1 c_1 + \lambda_2 c_2 + \lambda_3 c_3$.
    
- $(2,0,-2) = \lambda_1(1,1,0) + \lambda_2(1,0,1) + \lambda_3(0,1,1) = (\lambda_1 + \lambda_2, \lambda_1 + \lambda_3, \lambda_2 + \lambda_3)$
    
- Questo equivale a risolvere il sistema:  
    
    $$\begin{cases} \lambda_1 + \lambda_2 = 2 \\ \lambda_1 + \lambda_3 = 0 \\ \lambda_2 + \lambda_3 = -2 \end{cases}$$
- La soluzione è $\lambda_1=2, \lambda_2=0, \lambda_3=-2$. La prima colonna è $[f(b_1)]_\mathcal{C} = (2,0,-2)^T$.
    

**Seconda colonna:** Immagine di $b_2 = (1,-1)$

- Calcoliamo l'immagine: $f(1,-1) = (1-1, 1-(-1), -2 \cdot (-1)) = (0,2,2)$.
    
- Cerchiamo $\alpha_1, \alpha_2, \alpha_3$ tali che $(0,2,2) = \alpha_1 c_1 + \alpha_2 c_2 + \alpha_3 c_3$.
    
- $(0,2,2) = \alpha_1(1,1,0) + \alpha_2(1,0,1) + \alpha_3(0,1,1) = (\alpha_1 + \alpha_2, \alpha_1 + \alpha_3, \alpha_2 + \alpha_3)$
    
- Si osserva facilmente (o risolvendo il sistema) che la soluzione è $\alpha_1=0, \alpha_2=0, \alpha_3=2$.
    
- La seconda colonna è $[f(b_2)]_\mathcal{C} = (0,0,2)^T$.
    

La matrice risultante è:

$$M_f^{\mathcal{B}, \mathcal{C}} = \begin{pmatrix} 2 & 0 \\ 0 & 0 \\ -2 & 2 \end{pmatrix}$$

### 3. Verifica tramite la Formula del Cambiamento di Base

La formula è $M_f^{\mathcal{B},\mathcal{C}} = (M_I^{\mathcal{C}, E_3})^{-1} \cdot M_f^{E_2,E_3} \cdot M_I^{\mathcal{B}, E_2}$.

Le matrici di cambiamento di base _dalle nuove basi a quelle canoniche_ (standard) sono le più facili da scrivere: le loro colonne sono semplicemente i vettori delle nuove basi.

- $B = M_I^{\mathcal{B}, E_2} = \left( [b_1]_{E_2} \;\; [b_2]_{E_2} \right) = \begin{pmatrix} 1 & 1 \\ 1 & -1 \end{pmatrix}$
    
- $C = M_I^{\mathcal{C}, E_3} = \left( [c_1]_{E_3} \;\; [c_2]_{E_3} \;\; [c_3]_{E_3} \right) = \begin{pmatrix} 1 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 1 & 1 \end{pmatrix}$
    

Ora dobbiamo applicare la formula:

$$M_f^{\mathcal{B},\mathcal{C}} = C^{-1} \cdot M_f^{E_2,E_3} \cdot B$$

Calcolando l'inversa di $C$ (ad esempio con Gauss-Jordan) e svolgendo il prodotto matriciale, si ottiene esattamente la stessa matrice $M_f^{\mathcal{B}, \mathcal{C}}$ calcolata con il metodo diretto, verificando così la coerenza della teoria.