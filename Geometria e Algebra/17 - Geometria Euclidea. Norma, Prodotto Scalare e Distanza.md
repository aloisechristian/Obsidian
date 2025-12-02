# Geometria Euclidea in $\mathbb{R}^n$: Norma, Prodotto Scalare e Distanze

## 1. Introduzione: Dall'Intuizione all'Astrazione
L'algebra lineare funge da ponte tra la geometria intuitiva (limitata alle dimensioni 1, 2 e 3) e una geometria generalizzata in $n$ dimensioni. Attraverso il processo di misurazione, riduciamo la complessità del reale a vettori numerici. L'obiettivo è estendere concetti metrici come lunghezza e angolo a spazi vettoriali di dimensione arbitraria $\mathbb{R}^n$, dove la visualizzazione diretta non è possibile.

## 2. La Norma di un Vettore
La nozione di lunghezza di un vettore viene formalizzata attraverso il concetto di **norma**.
* **Caso Unidimensionale ($\mathbb{R}$):** La lunghezza è il valore assoluto $|x_1| = \sqrt{x_1^2}$.
* **Caso Bidimensionale ($\mathbb{R}^2$) e Tridimensionale ($\mathbb{R}^3$):** Si applica il [[Teorema di Pitagora]]. Per $v = (x_1, x_2)$, la lunghezza è $\sqrt{x_1^2 + x_2^2}$.
* **Caso Generale ($\mathbb{R}^n$):** Si definisce la **norma euclidea** di un vettore $v = (x_1, \dots, x_n)$ come:
    $$\|v\| := \sqrt{x_1^2 + x_2^2 + \dots + x_n^2} = \sqrt{\sum_{i=1}^n x_i^2}$$
Questa definizione permette di trattare la "lunghezza" in spazi astratti $\mathbb{R}^n$ (es. $\mathbb{R}^{200}$) in modo coerente con gli spazi fisici.

## 3. Il Prodotto Scalare Standard
Per manipolare la norma con gli strumenti dell'algebra lineare (evitando radici e potenze non lineari), introduciamo il **prodotto scalare**.
La norma al quadrato può essere espressa come il prodotto matriciale di un vettore riga per il suo trasposto (colonna), oppure tramite la notazione del prodotto scalare:
$$\|v\|^2 = \langle v, v \rangle = v^T \cdot v = \sum_{i=1}^n x_i^2$$
Generalizzando per due vettori distinti $v = (x_1, \dots, x_n)$ e $w = (y_1, \dots, y_n)$, definiamo il prodotto scalare standard come:
$$v \cdot w = \langle v, w \rangle = \sum_{i=1}^n x_i y_i$$
Il risultato di questa operazione è uno **scalare**.

### Proprietà del Prodotto Scalare
Siano $u, v, w \in \mathbb{R}^n$ e $\lambda \in \mathbb{R}$. Il prodotto scalare è un'operazione bilineare simmetrica definita positiva:
1.  **Simmetria:** $v \cdot w = w \cdot v$.
2.  **Additività (Bilinearietà):** $u \cdot (v + w) = u \cdot v + u \cdot w$.
3.  **Omogeneità:** $(\lambda u) \cdot v = \lambda (u \cdot v)$.
4.  **Positività:** $v \cdot v \ge 0$, con $v \cdot v = 0 \iff v = 0$ (vettore nullo).

## 4. Angolo tra Vettori e Teorema di Carnot
Una delle applicazioni più potenti del prodotto scalare è la possibilità di definire l'**angolo** $\alpha$ tra due vettori in spazi di dimensione $n > 3$, generalizzando la geometria piana.
Dati due vettori $v, w \in \mathbb{R}^n$ non nulli, l'angolo $\alpha$ compreso tra essi è definito come:
$$\alpha = \arccos \left( \frac{v \cdot w}{\|v\| \cdot \|w\|} \right)$$
con $\alpha \in [0, \pi]$. Da cui segue la relazione fondamentale:
$$v \cdot w = \|v\| \cdot \|w\| \cdot \cos \alpha$$

### Collegamento con il Teorema di Carnot
Questa definizione non è arbitraria ma deriva direttamente dalla generalizzazione del **Teorema di Carnot** (o [[Teorema del Coseno]]). In un triangolo definito dai vettori $v$ e $w$, il quadrato della lunghezza del lato opposto all'angolo (vettore differenza $v-w$) è dato da:
$$\|v - w\|^2 = \|v\|^2 + \|w\|^2 - 2 \|v\| \|w\| \cos \alpha$$
Sviluppando il calcolo con il prodotto scalare si ottiene l'identità $-2(v \cdot w) = -2 \|v\| \|w\| \cos \alpha$, che conferma la definizione di angolo.

## 5. Ortogonalità e Complemento Ortogonale
Il concetto di ortogonalità è puramente algebrico, mentre la "perpendicolarità" è una proprietà geometrica. In $\mathbb{R}^n$ coincidono.
Due vettori $v, w$ si dicono **ortogonali** se il loro prodotto scalare è nullo (corrispondente a un angolo di $\pi/2$):
$$v \cdot w = 0$$

### Complemento Ortogonale di un Sottospazio
Dato un sottospazio $S \subseteq \mathbb{R}^n$, definiamo il suo **complemento ortogonale** $S^\perp$ come l'insieme dei vettori ortogonali a tutti i vettori di $S$:
$$S^\perp = \{ w \in \mathbb{R}^n \mid w \cdot v = 0, \forall v \in S \}$$
Se $B = \{v_1, \dots, v_m\}$ è una base di $S$, allora $S^\perp$ equivale al **Kernel** (nucleo) della matrice $A$ avente per righe i vettori della base $B$. Vale la relazione di somma diretta:
$$\mathbb{R}^n = S \oplus S^\perp$$
Questo implica che ogni vettore di $\mathbb{R}^n$ può essere scomposto in modo unico come somma di un componente in $S$ e uno in $S^\perp$.

## 6. Basi Ortogonali e Ortonormali
In uno spazio euclideo, distinguiamo basi con proprietà metriche particolari che semplificano i calcoli:
* **Base Ortogonale:** Una base $\{v_1, \dots, v_n\}$ dove i vettori sono a due a due ortogonali ($v_i \cdot v_j = 0$ per $i \neq j$).
* **Base Ortonormale:** Una base ortogonale in cui ogni vettore è normalizzato (ha norma unitaria, $\|v_i\| = 1$). La base canonica standard è l'esempio più semplice.

### Algoritmo di Gram-Schmidt
Data una base generica di uno spazio vettoriale, esiste un procedimento algoritmico, detto **Algoritmo di Gram-Schmidt**, che permette di costruire una base ortonormale a partire da essa. Questo è fondamentale per la stabilità numerica nei calcoli ingegneristici.

## 7. Distanza Euclidea
Uno spazio vettoriale dotato di prodotto scalare definito positivo è uno spazio euclideo. Definiamo la **distanza euclidea** tra due punti (vettori) $P$ e $Q$ come la norma della loro differenza:
$$d(P, Q) := \| P - Q \|$$

### Proprietà della Metrica
1.  **Simmetria:** $d(P, Q) = d(Q, P)$.
2.  **Disuguaglianza Triangolare:** $d(P, Q) \le d(P, R) + d(R, Q)$. La via più breve tra due punti è il segmento retto.
3.  **Positività:** $d(P, Q) \ge 0$, e $d(P, Q) = 0 \iff P = Q$.

## 8. Calcolo della Distanza dai Sottospazi Affini
Generalizzando, la distanza di un punto $P$ da un sottospazio affine $\Sigma = R + S$ (dove $S$ è la giacitura/sottospazio direttore) è la minima distanza tra $P$ e un punto qualsiasi di $\Sigma$. Si calcola proiettando il vettore differenza sul complemento ortogonale $S^\perp$.

### Formule Notevoli
* **Distanza Punto-Retta in $\mathbb{R}^2$:**
    Dato un punto $P=(x_0, y_0)$ e una retta $r: ax + by = c$, la distanza è:
    $$d(P, r) = \frac{|ax_0 + by_0 - c|}{\sqrt{a^2 + b^2}}$$

* **Distanza Punto-Piano in $\mathbb{R}^3$:**
    Dato un punto $P=(x_0, y_0, z_0)$ e un piano $\pi: ax + by + cz = d$:
    $$d(P, \pi) = \frac{|ax_0 + by_0 + cz_0 - d|}{\sqrt{a^2 + b^2 + c^2}}$$

* **Distanza Punto-Retta in $\mathbb{R}^3$:**
    Dato $P$ e una retta $r = Q + \langle v \rangle$ (passante per $Q$ con direzione $v$), si calcola il vettore $w = P - Q$. La distanza è la norma della componente di $w$ ortogonale a $v$:
    $$d(P, r) = \left\| w - \frac{w \cdot v}{\|v\|^2}v \right\|$$