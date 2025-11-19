## Motivazione: L'Efficienza delle Matrici Diagonali

L'efficienza computazionale è un fattore cruciale nell'algebra lineare applicata all'ingegneria. Consideriamo il [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan|prodotto di una matrice]] per un vettore. Se la matrice è generica, il calcolo richiede un numero elevato di operazioni. Ad esempio, per moltiplicare una matrice $A \in M_{n,n}(\mathbb{R})$ per un vettore $v \in \mathbb{R}^n$, sono necessarie circa $n^2$ operazioni di moltiplicazione e somma.

Tuttavia, se la matrice è **diagonale**, la situazione cambia radicalmente. Una matrice diagonale $D$ ha elementi non nulli solo sulla sua diagonale principale. Il prodotto $D \cdot v$ si calcola semplicemente moltiplicando ogni componente $v_i$ del vettore per il corrispondente elemento diagonale $d_{ii}$ della matrice. Questo richiede solo $n$ moltiplicazioni, un guadagno di efficienza notevole.

> [!info] Vantaggio Ingegneristico
> Una matrice diagonale $n \times n$ può essere memorizzata utilizzando solo $n$ valori, a differenza degli $n^2$ valori necessari per una matrice generica.

## Il Problema della Diagonalizzazione per gli Endomorfismi

Dato un [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango|endomorfismo]] $F: V \to V$ e fissata una base $\mathcal{B}$ dello spazio vettoriale $V$, l'applicazione di $F$ è rappresentata dalla matrice associata $M_{\mathcal{B}}^{\mathcal{B}}(F)$.

La relazione tra l'immagine di un vettore e le sue coordinate è data da:
$$[F(v)]_{\mathcal{B}} = M_{\mathcal{B}}^{\mathcal{B}}(F) \cdot [v]_{\mathcal{B}}$$

Il problema centrale della **diagonalizzazione** è determinare se esiste una base $\mathcal{B}$ tale che la matrice associata $M_{\mathcal{B}}^{\mathcal{B}}(F)$ sia diagonale.

## Definizioni Formali

### Diagonalizzazione di Endomorfismi e Matrici

Sia $F: V \to V$ un endomorfismo.
* **Endomorfismo Diagonalizzabile**: $F$ è diagonalizzabile se esiste una base $\mathcal{B}$ di $V$ (detta *base diagonalizzante*) tale che la matrice $M_{\mathcal{B}}^{\mathcal{B}}(F)$ è diagonale.
* **Matrice Diagonalizzabile**: Una matrice quadrata $A$ è diagonalizzabile se è [[13 - Matrici Associate e Cambiamento di Base|simile]] a una matrice diagonale $D$. Ovvero, se esiste una matrice invertibile $B$ tale che:
    $$D = B^{-1} \cdot A \cdot B$$
    La matrice $B$ è la **matrice del cambio di base** (o di passaggio) dalla base canonica alla base diagonalizzante $\mathcal{B}$.

## Autovalori e Autovettori

L'equazione fondamentale nasce dall'osservazione che una matrice diagonale agisce sui vettori della base semplicemente "scalandoli".

* **Autovalore ($\lambda$)**: Uno scalare $\lambda \in \mathbb{R}$ tale che esiste un vettore $v \neq 0$ per cui $A \cdot v = \lambda v$.
* **Autovettore ($v$)**: Un vettore non nullo che soddisfa l'equazione $A \cdot v = \lambda v$.

### Il Polinomio Caratteristico

Per trovare gli autovalori, cerchiamo i valori di $\lambda$ che rendono la matrice $(A - \lambda I)$ non invertibile (ovvero con [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango|kernel]] non banale). Questo accade se e solo se:

$$p_A(\lambda) = \det(A - \lambda I) = 0$$

Le radici del **polinomio caratteristico** $p_A(\lambda)$ sono gli autovalori di $A$.

## Molteplicità e Criterio di Diagonalizzazione

Per ogni autovalore $\lambda_0$, definiamo:

1.  **Molteplicità Algebrica ($m_a(\lambda_0)$)**: Il numero di volte che $\lambda_0$ appare come radice del polinomio caratteristico.
2.  **Molteplicità Geometrica ($m_g(\lambda_0)$)**: La dimensione dell'autospazio $V_{\lambda_0}$ relativo all'autovalore.
    $$m_g(\lambda_0) = \dim(V_{\lambda_0}) = \dim(\text{ker}(A - \lambda_0 I)) = n - \text{rk}(A - \lambda_0 I)$$

> [!important] Teorema di Diagonalizzazione
> Una matrice $A \in M_{n,n}$ è diagonalizzabile se e solo se:
> 1. La somma delle molteplicità algebriche è $n$ (il polinomio caratteristico è interamente scomponibile in $\mathbb{R}$).
> 2. Per ogni autovalore $\lambda$, vale **$m_g(\lambda) = m_a(\lambda)$**.

## Esempi di Calcolo

### Esempio 1: Autovalori Reali e Distinti
Sia $A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}$.
Il polinomio caratteristico è $\lambda^2 - 5\lambda - 2 = 0$.
Le radici sono $\lambda_{1,2} = \frac{5 \pm \sqrt{33}}{2}$.
Poiché abbiamo 2 autovalori distinti, $m_a=1$ e necessariamente $m_g=1$. La matrice è diagonalizzabile e la forma diagonale è:
$$D = \begin{pmatrix} \frac{5 + \sqrt{33}}{2} & 0 \\ 0 & \frac{5 - \sqrt{33}}{2} \end{pmatrix}$$

### Esempio 2: Autovalori Coincidenti (Non Diagonalizzabile)
Sia $A = \begin{pmatrix} 0 & 4 \\ -1 & 4 \end{pmatrix}$.
Il polinomio caratteristico è $(\lambda - 2)^2$, quindi $\lambda = 2$ con $m_a(2) = 2$.
Calcoliamo la dimensione dell'autospazio $V_2 = \text{ker}(A - 2I)$:
$$A - 2I = \begin{pmatrix} -2 & 4 \\ -1 & 2 \end{pmatrix}$$
Il rango è 1, quindi $m_g(2) = 2 - 1 = 1$.
Dato che **$m_g(2) < m_a(2)$** ($1 < 2$), la matrice non è diagonalizzabile.

## Costruzione della Matrice $B$

Se la matrice è diagonalizzabile, la matrice $B$ che realizza la diagonalizzazione ($D = B^{-1} \cdot A \cdot B$) ha per colonne gli autovettori linearmente indipendenti che formano la base $\mathcal{B}$:

$$B = (v_1 | v_2 | \dots | v_n)$$