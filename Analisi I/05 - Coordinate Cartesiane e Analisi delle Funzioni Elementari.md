# Rappresentazione Geometrica, Funzioni Monotone e Valore Assoluto

## 1. Rappresentazione Geometrica dei Numeri Reali e Punti nel Piano

Questa sezione riesamina la rappresentazione geometrica dei [[03 - Insiemi Numerici, Completezza e Estremo Superiore|numeri reali]] su una retta e la estende alla rappresentazione dei punti in un piano cartesiano.

### 1.1 La Retta Reale e l'Ascissa di un Punto

La rappresentazione geometrica dei numeri reali si basa su una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|corrispondenza biunivoca]] tra i numeri reali e i punti di una retta. Fissando un punto $O$ detto **origine** e un'unità di misura, la retta viene orientata e suddivisa in due semirette:

*   La **semiretta positiva** ($R^+$).
*   La **semiretta negativa** ($R^-$).

Ad ogni punto $P$ della retta si associa un unico numero reale detto **ascissa**, stabilendo una corrispondenza biunivoca tra i punti della retta e l'insieme dei numeri reali $\mathbb{R}$.

### 1.2 Il Piano Cartesiano: Coordinate di un Punto

Per estendere la rappresentazione a un punto $P$ nel piano, si introduce un **sistema di coordinate cartesiane ortogonali**. Questo sistema è costituito da:

1.  Un punto fisso $O$, detto **origine**.
2.  Due rette orientate e perpendicolari passanti per $O$, chiamate **assi cartesiani** (l'asse $Ox$ o **asse delle ascisse** e l'asse $Oy$ o **asse delle ordinate**).

Un punto $P$ nel piano è univocamente descritto da una **[[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#Definizione per due Insiemi|coppia ordinata]]** di numeri reali $(x, y)$, dove $x$ e $y$ sono le sue **coordinate cartesiane ortogonali**. Queste coordinate sono determinate tramite proiezioni ortogonali:

*   Si proietta il punto $P$ sull'asse $Ox$, ottenendo un punto $P_x$. La coordinata $x$ è l'**ascissa** di $P_x$ sull'asse $Ox$.
*   Si proietta il punto $P$ sull'asse $Oy$, ottenendo un punto $P_y$. La coordinata $y$ è l'**ordinata** di $P_y$ sull'asse $Oy$.

Si stabilisce così una corrispondenza biunivoca tra i punti del piano e l'insieme delle coppie ordinate di numeri reali, denotato come $\mathbb{R}^2$, che è il [[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali|prodotto cartesiano]] di $\mathbb{R}$ per se stesso.

## 2. Funzioni Monotone

### 2.1 Definizioni di Monotonia

Sia $f: X \to Y$ una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]] con $X, Y \subseteq \mathbb{R}$.

*   **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|Funzione crescente]]**: $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) \leq f(x_2)$.
*   **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|Funzione decrescente]]**: $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) \geq f(x_2)$.
*   **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|Funzione strettamente crescente]]**: $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) < f(x_2)$.
*   **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|Funzione strettamente decrescente]]**: $\forall x_1, x_2 \in X, x_1 < x_2 \implies f(x_1) > f(x_2)$.

Una funzione si dice **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|monotona]]** se è crescente oppure decrescente. Si dice **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Monotonia delle Funzioni|strettamente monotona]]** se è strettamente crescente o strettamente decrescente.

### 2.2 Proprietà delle Funzioni Monotone

#### Proprietà della Funzione Opposta

Se una funzione $f$ è crescente, la sua funzione opposta, $-f$, è decrescente. Simmetricamente, se $f$ è decrescente, $-f$ è crescente.

*Dimostrazione*: Sia $f$ crescente. Per ipotesi, per ogni $x_1 < x_2$ si ha $f(x_1) \leq f(x_2)$. Moltiplicando entrambi i membri della disuguaglianza per $-1$, si inverte il verso, ottenendo $-f(x_1) \geq -f(x_2)$. Questa è la definizione di funzione decrescente per $-f$.

#### Teorema sulla Monotonia della Funzione Inversa

Sia $f: X \to Y$ una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|funzione invertibile]].
*   Se $f$ è strettamente crescente, allora anche la sua funzione inversa $f^{-1}$ è strettamente crescente.
*   Se $f$ è strettamente decrescente, allora anche la sua funzione inversa $f^{-1}$ è strettamente decrescente.

*Dimostrazione (per il caso strettamente crescente)*: Si procede con una [[Concetti Trasversali/Tecniche Algoritmiche e Dimostrative#Dimostrazione per Assurdo|dimostrazione per assurdo]].
1.  **Ipotesi**: $f$ è strettamente crescente.
2.  **Tesi da negare**: Supponiamo per assurdo che $f^{-1}$ non sia strettamente crescente. Ciò implica che esistono $y_1, y_2 \in Y$ tali che $y_1 < y_2$ ma $f^{-1}(y_1) \ge f^{-1}(y_2)$.
3.  Poiché $f$ è invertibile, è anche [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|iniettiva]]. Di conseguenza, $f^{-1}$ è iniettiva, e l'uguaglianza $f^{-1}(y_1) = f^{-1}(y_2)$ è esclusa per $y_1 \ne y_2$. Pertanto, deve essere $f^{-1}(y_1) > f^{-1}(y_2)$.
4.  Siano $x_1 = f^{-1}(y_1)$ e $x_2 = f^{-1}(y_2)$. La disuguaglianza diventa $x_1 > x_2$.
5.  Applichiamo la funzione $f$ a entrambi i membri di $x_1 > x_2$. Poiché $f$ è strettamente crescente per ipotesi, il verso della disuguaglianza si conserva: $f(x_1) > f(x_2)$.
6.  Sostituendo nuovamente le definizioni di $x_1$ e $x_2$, otteniamo $y_1 > y_2$.
7.  **Contraddizione**: Siamo partiti dalla supposizione $y_1 < y_2$ e siamo giunti alla conclusione $y_1 > y_2$, il che è impossibile. L'assurdo deriva dall'aver negato la tesi.

Di conseguenza, la funzione inversa $f^{-1}$ deve essere strettamente crescente.

## 3. Analisi di Funzioni Elementari

### 3.1 La Funzione Lineare: $f(x) = mx + q$

Si chiama funzione lineare una funzione del tipo $y = mx+q$, dove $m$ e $q$ sono costanti reali fissate. $m$ prende il nome di **coefficiente angolare** e $q$ di **termine noto**.

#### Analisi dei casi
1.  **Caso $m = 0$**: La funzione diventa costante, $f(x) = q$.
    -   Il suo grafico è una retta orizzontale di equazione $y=q$.
    -   Non è [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|iniettiva]]: a tutti gli $x$ distinti corrisponde la stessa immagine $q$.
    -   Non è [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Suriettiva (o Suriezione)|suriettiva]] (su $\mathbb{R}$): l'unico valore assunto è $q$, quindi nessun $y \neq q$ ha una controimmagine.

2.  **Caso $m \neq 0$**: La funzione è [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|biettiva]] (iniettiva e suriettiva).
    -   **Iniettività**: Dati $x_1 \neq x_2$, se per assurdo $f(x_1) = f(x_2)$, allora $mx_1+q = mx_2+q$. Per la regola di semplificazione della somma, si ha $mx_1 = mx_2$. Dividendo per $m \neq 0$, si ottiene $x_1 = x_2$, il che contraddice l'ipotesi.
    -   **Suriettività**: Per ogni $y \in \mathbb{R}$, è possibile trovare una $x$ tale che $f(x)=y$. Risolvendo l'equazione $y = mx+q$ rispetto a $x$, si ottiene $x = \frac{y-q}{m}$. Questa è l'espressione della funzione inversa.

#### Monotonia
-   Se **$m > 0$**, la funzione è **strettamente crescente**. Infatti, se $x_1 < x_2$, moltiplicando per $m>0$ si ha $mx_1 < mx_2$. Sommando $q$ a entrambi i membri, $mx_1+q < mx_2+q$, ovvero $f(x_1) < f(x_2)$.
-   Se **$m < 0$**, la funzione è **strettamente decrescente**. Se $x_1 < x_2$, moltiplicando per $m<0$ si inverte il verso: $mx_1 > mx_2$. Sommando $q$, si ottiene $f(x_1) > f(x_2)$.

#### Equazioni e Disequazioni
-   **Equazione $f(x) = 0$**: Risolvere $mx+q=0$ significa trovare l'intersezione del grafico con l'asse delle ascisse. La soluzione (per $m \neq 0$) è $x = -\frac{q}{m}$.
-   **Disequazione $f(x) > 0$**: Risolvere $mx+q>0$ significa trovare gli intervalli di $x$ per cui il grafico della funzione si trova sopra l'asse delle ascisse. La soluzione dipende dal segno di $m$:
    -   Se $m>0$: $mx > -q \implies x > -\frac{q}{m}$.
    -   Se $m<0$: $mx > -q \implies x < -\frac{q}{m}$.

### 3.2 La Funzione Valore Assoluto

La funzione **valore assoluto** (o **modulo**) di $x \in \mathbb{R}$ è definita come:

$$|x| = \begin{cases} x & \text{se } x \ge 0 \\ -x & \text{se } x < 0 \end{cases}$$

*   **[[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|Dominio]]**: $\mathbb{R}$.
*   **[[04 - Estremi Superiori e Inferiori per Insiemi e Funzioni#Estensione dei Concetti alle Funzioni Reali|Codominio (o insieme delle immagini)]]**: $\mathbb{R}^+ \cup \{0\}$, ovvero l'[[03 - Insiemi Numerici, Completezza e Estremo Superiore#Intervalli in R|intervallo]] $[0, +\infty)$.
*   **Proprietà**:
    -   È [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Suriettiva (o Suriezione)|suriettiva]] se considerata come $f: \mathbb{R} \to [0, +\infty)$.
    -   **Non è [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|iniettiva]]**, in quanto per ogni $a \ne 0$, si ha $a \ne -a$ ma $f(a) = f(-a) = |a|$.
*   **[[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#Il Grafico di una Funzione|Grafico]]**: Il grafico è composto da due semirette:
    *   La bisettrice del primo quadrante, $y=x$, per $x \ge 0$.
    *   La bisettrice del secondo quadrante, $y=-x$, per $x < 0$.

#### Proprietà Fondamentali
Per ogni $x, x_1, x_2 \in \mathbb{R}$ valgono le seguenti proprietà:
1.  $|x| \ge 0$
2.  $|x| = 0 \iff x=0$
3.  $|-x| = |x|$
4.  $|x_1 \cdot x_2| = |x_1| \cdot |x_2|$
5.  $|\frac{x_1}{x_2}| = \frac{|x_1|}{|x_2|}$, se $x_2 \ne 0$

#### Disequazioni con il Valore Assoluto

Sia $R \ge 0$. Valgono le seguenti equivalenze fondamentali:
1.  $|x| \le R \iff -R \le x \le R$
2.  $|x| \ge R \iff x \le -R \lor x \ge R$

*Dimostrazione della prima equivalenza ($|x| \le R$)*: Si analizzano i due casi della definizione di modulo.
*   **Caso A ($x \ge 0$)**: La disequazione $|x| \le R$ diventa $x \le R$. L'intersezione con la condizione del caso, $\{x \mid x \ge 0\} \cap \{x \mid x \le R\}$, fornisce la soluzione $\{x \mid 0 \le x \le R\}$.
*   **Caso B ($x < 0$)**: La disequazione $|x| \le R$ diventa $-x \le R$, che, moltiplicando per $-1$, equivale a $x \ge -R$. L'intersezione con la condizione del caso, $\{x \mid x < 0\} \cap \{x \mid x \ge -R\}$, fornisce la soluzione $\{x \mid -R \le x < 0\}$.

L'[[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Operazioni Fondamentali tra Insiemi|unione]] delle soluzioni dei due casi, $[-R, 0) \cup [0, R]$, fornisce la soluzione completa $-R \le x \le R$.
