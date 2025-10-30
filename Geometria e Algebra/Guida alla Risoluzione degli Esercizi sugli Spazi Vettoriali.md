# Guida alla Risoluzione degli Esercizi sugli Spazi Vettoriali

Questa nota serve come guida strategica per affrontare gli esercizi proposti nel file `Esercizi_Spazi_Vettoriali.pdf`. Ogni sezione delinea l'approccio generale per una categoria di problemi, con collegamenti diretti ai concetti teorici nel tuo vault per un ripasso mirato.

---

## 1. Dipendenza Lineare (Esercizi 1-6)

**Obiettivo**: Determinare se un insieme di vettori $\{v_1, v_2, \dots, v_k\}$ è linearmente indipendente.

Un insieme di vettori è **linearmente dipendente** se almeno uno di essi può essere scritto come [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|combinazione lineare]] degli altri. Altrimenti, è **linearmente indipendente**.

### Strategia di Risoluzione Generale 🧠

Il metodo più sistematico consiste nell'utilizzare le matrici e il concetto di [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]].

1.  **Costruire la Matrice**: Disponi i vettori dell'insieme come **righe** (o colonne) di una matrice $A$.
2.  **Riduzione a Scala**: Applica l'[[Algoritmo di Eliminazione di Gauss Jordan]] per trasformare la matrice $A$ nella sua forma a scala (echelon form).
3.  **Calcolare il Rango**: Il rango della matrice, $Rk(A)$, è uguale al numero di pivot (o di righe non nulle) nella forma a scala.
4.  **Verificare la Condizione**:
    * Se il **rango è uguale al numero di vettori** ($Rk(A) = k$), l'insieme è **linearmente indipendente**.
    * Se il **rango è minore del numero di vettori** ($Rk(A) < k$), l'insieme è **linearmente dipendente**.

**Collegamento Teorico**: Questa procedura funziona perché il rango di una matrice corrisponde al numero massimo di righe (o colonne) linearmente indipendenti. Se il rango è inferiore al numero di righe che hai inserito, significa che c'erano delle ridondanze, ovvero delle dipendenze lineari.

---

## 2. Basi e Dimensioni (Esercizi 7-12)

**Obiettivo**: Trovare una [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Definizione di Base|base]] e la dimensione di un sottospazio, completare un insieme a una base o estrarne una.

Una **base** è un insieme di generatori linearmente indipendenti. La **dimensione** di un sottospazio è il numero di vettori in una sua base.

### 2.1 Trovare una Base da un Sottospazio (Esercizi 7, 9, 11)

Il metodo dipende da come è definito il sottospazio.

#### Caso 1: Sottospazio in Forma Parametrica (Span di Generatori)
* **Definizione**: $W = \text{span}\{v_1, \dots, v_k\}$ (es. Esercizio 9.1, 9.2).
* **Procedura**: Questa è la procedura di **estrazione di una base**.
    1.  Crea una matrice $A$ con i vettori generatori come righe.
    2.  Riduci $A$ a forma a scala con l'[[Algoritmo di Eliminazione di Gauss Jordan]].
    3.  Le **righe non nulle** della matrice ridotta formano una base per $W$.
    4.  La **dimensione** di $W$ è il numero di righe non nulle, ovvero il [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]] di $A$.

#### Caso 2: Sottospazio in Forma Cartesiana (Kernel di una Matrice)
* **Definizione**: $W = \{(x_1, \dots, x_n) \mid Ax=0\}$, ovvero il [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Esempi di Sottospazi|kernel]] di A (es. Esercizio 7, 9.3, 9.4, 11).
* **Procedura**:
    1.  Risolvi il [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Sistemi Omogenei e Struttura delle Soluzioni|sistema lineare omogeneo]] $Ax=0$ usando l'algoritmo di Gauss-Jordan sulla matrice $A$.
    2.  Identifica le variabili dipendenti (quelle corrispondenti ai pivot) e le **variabili libere** (quelle senza pivot).
    3.  La **dimensione** del sottospazio (il kernel) è uguale al numero di variabili libere: $\dim(\ker A) = n - Rk(A)$, dove $n$ è il numero di colonne.
    4.  Esprimi la soluzione generale del sistema in funzione delle variabili libere.
    5.  Raccogli i termini per ogni parametro libero. I vettori che moltiplicano i parametri formano una **base** per il kernel.

### 2.2 Completamento ed Estrazione di una Base (Esercizio 10)

* **Completare a una base**: Se hai un insieme di $k$ vettori linearmente indipendenti in $\mathbb{R}^n$ (con $k<n$), devi aggiungere $n-k$ vettori per formare una base.
    1.  Crea una matrice con i tuoi $k$ vettori come prime righe e i vettori della base canonica di $\mathbb{R}^n$ come righe successive.
    2.  Riduci a scala. I vettori corrispondenti alle righe con i pivot formano la base completata.

* **Estrarre una base**: Se hai un insieme di $k$ generatori in $\mathbb{R}^n$ (con $k>n$), usa la procedura standard di estrazione vista al punto 2.1.

### 2.3 Calcolo delle Coordinate (Esercizio 12)

* **Obiettivo**: Dato un vettore $v$ e una base $B = \{b_1, \dots, b_n\}$, trovare le coordinate $[v]_B = (c_1, \dots, c_n)$ significa risolvere l'equazione vettoriale:
    $$v = c_1 b_1 + c_2 b_2 + \dots + c_n b_n$$
* **Procedura**:
    1.  Scrivi l'equazione come un sistema di equazioni lineari, dove le incognite sono i coefficienti $c_i$.
    2.  La matrice dei coefficienti del sistema avrà come colonne i vettori della base $b_i$.
    3.  Risolvi il sistema. La soluzione $(c_1, \dots, c_n)$ è il vettore delle coordinate cercato.

---

## 3. Rappresentazioni Cartesiane e Parametriche (Esercizi 18-20)

**Obiettivo**: Passare da una rappresentazione all'altra di un sottospazio.

* **Da Cartesiana a Parametrica**:
    * **Problema**: Dato $W = \ker(A)$. Trovare un insieme di generatori.
    * **Soluzione**: È esattamente la procedura vista al punto **2.1 (Caso 2)**. Risolvi il sistema $Ax=0$. La base che trovi per il kernel ti fornisce i generatori per la forma parametrica $W = \text{span}\{\dots\}$.

* **Da Parametrica a Cartesiana**:
    * **Problema**: Dato $W = \text{span}\{v_1, \dots, v_k\}$. Trovare un sistema di equazioni $Ax=0$ il cui spazio delle soluzioni sia $W$.
    * **Soluzione (Metodo Generale)**:
        1.  Un generico vettore $x = (x_1, \dots, x_n)$ appartiene a $W$ se e solo se è combinazione lineare dei generatori $\{v_1, \dots, v_k\}$.
        2.  Questo è vero se e solo se il rango della matrice formata dai generatori è uguale al rango della stessa matrice a cui è stato aggiunto il vettore $x$.
            $$Rk(v_1, \dots, v_k) = Rk(v_1, \dots, v_k, x)$$
        3.  Costruisci la matrice aumentata con i generatori **in colonna** e il vettore generico $x$ come ultima colonna.
        4.  Riduci la matrice a scala. Le condizioni che rendono il sistema compatibile (annullando eventuali pivot nella colonna di $x$) sono le equazioni cartesiane cercate.

---

## 4. Operazioni con i Sottospazi (Esercizi 21-23)

**Obiettivo**: Calcolare l'intersezione ($H_1 \cap H_2$) e la somma ($H_1 + H_2$) di due sottospazi e verificare la **Formula di Grassmann**.

$$\dim(H_1 + H_2) = \dim(H_1) + \dim(H_2) - \dim(H_1 \cap H_2)$$

### Calcolo dell'Intersezione ($H_1 \cap H_2$)

* **Se entrambi i sottospazi sono in forma cartesiana**:
    $$H_1 = \ker(A_1), \quad H_2 = \ker(A_2)$$
    L'intersezione è l'insieme dei vettori che soddisfano *entrambe* le condizioni.
    * **Procedura**: Metti a sistema le equazioni di $H_1$ e quelle di $H_2$. Risolvi il nuovo sistema omogeneo. La base delle soluzioni è una base per $H_1 \cap H_2$.

* **Se uno è in forma cartesiana ($H_1 = \ker(A)$) e uno in forma parametrica ($H_2 = \text{span}\{v_1, \dots, v_k\}$)**:
    * **Procedura**: Sostituisci il generico vettore di $H_2$, $v = c_1 v_1 + \dots + c_k v_k$, nelle equazioni di $H_1$. Questo ti darà un sistema lineare nelle incognite $c_i$. Risolvendolo, troverai i coefficienti dei vettori di $H_2$ che appartengono anche a $H_1$, e quindi una base per l'intersezione.

### Calcolo della Somma ($H_1 + H_2$)

* **Definizione**: $H_1 + H_2 = \text{span}(B_1 \cup B_2)$, dove $B_1$ e $B_2$ sono le basi di $H_1$ e $H_2$.
* **Procedura**:
    1.  Trova una base per $H_1$ e una base per $H_2$.
    2.  Unisci i vettori delle due basi in un unico insieme di generatori.
    3.  Usa la procedura di **estrazione di una base** (punto 2.1) su questo insieme unito per trovare una base di $H_1 + H_2$.

Spero che questa guida ti sia d'aiuto per organizzare lo studio e affrontare gli esercizi con una strategia chiara. Buon lavoro! 💪