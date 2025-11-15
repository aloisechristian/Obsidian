# Guida alla Risoluzione: Esercizi su Applicazioni Lineari

Questa nota serve come guida strategica per risolvere gli esercizi del file `Esercizi_Applicazioni_Lineari.pdf`. Ogni sezione collega un tipo di problema ai concetti teorici fondamentali presenti nei tuoi appunti.

---

### 1. Verificare la Linearità (Esercizi 1, 2)

Un'applicazione $f: V \to W$ è lineare (un [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Definizione di Applicazione Lineare (o Omomorfismo)|omomorfismo]]) se soddisfa **due** proprietà per ogni $u, v \in V$ e $\lambda \in \mathbb{R}$:
1.  **Additività:** $f(u+v) = f(u)+f(v)$
2.  **Omogeneità:** $f(\lambda v) = \lambda f(v)$

**Metodi rapidi per Smentire (Esercizio 2):**
* **Test del Vettore Nullo:** Se $f(0_V) \neq 0_W$, l'applicazione **non** è lineare.
    * *Esempio (2.2):* $T(0,0) = (1, 0, 0) \neq (0,0,0)$. Non lineare.
    * *Esempio (2.5):* $L(0) = (0, -1) \neq (0,0)$. Non lineare.
* **Test dei Polinomi (per $f: \mathbb{R}^n \to \mathbb{R}^m$):** Le componenti della funzione devono essere **polinomi omogenei di primo grado**.
    * *Esempio (2.3):* $T(x_1, x_2, x_3) = (x_2x_3, \dots)$. Il termine $x_2x_3$ è di grado 2. Non lineare.
    * *Esempio (2.7):* $L(A) = ad-bc$. Il "determinante" è un polinomio di grado 2 negli input. Non lineare.

---

### 2. Nucleo, Immagine e Proprietà Fondamentali (Esercizi 1, 3, 4)

Per un'applicazione lineare $f: V \to W$ (spesso rappresentata da una matrice $A$):

* **Nucleo ($\text{Ker}(f)$):** È l'insieme dei vettori del dominio che vengono mappati sul vettore nullo.
    * **Come trovarlo:** $\text{Ker}(f)$ corrisponde allo **Spazio Nullo** della matrice associata $A$. Si trova risolvendo il sistema lineare omogeneo $A \cdot x = 0$.
* **Immagine ($\text{Im}(f)$):** È l'insieme dei vettori del codominio che sono "raggiunti" da almeno un vettore del dominio.
    * **Come trovarla:** $\text{Im}(f)$ corrisponde allo **Spazio delle Colonne** ($\text{Col}(A)$) della matrice $A$. Una base per l'immagine è data dalle colonne della matrice *originale* $A$ che corrispondono alle colonne di pivot dopo la riduzione di Gauss.
* **Preimmagine ($f^{-1}(w)$) (Esercizio 1):**
    * **Cosa significa:** Trovare *tutti* i vettori $v$ tali che $f(v) = w$.
    * **Come trovarla:** Risolvi il sistema lineare *non* omogeneo $A \cdot x = w$. L'insieme delle soluzioni sarà $v_p + \text{Ker}(f)$, dove $v_p$ è una soluzione particolare.

---

### 3. Iniettività, Suriettività, Biettività (Esercizi 4, 5, 6, 10)

Queste proprietà dipendono dalle dimensioni di $\text{Ker}(f)$ e $\text{Im}(f)$, che sono legate dal **Teorema del Rango (o della Dimensione)**:
$\dim(V) = \dim(\text{Ker}(f)) + \dim(\text{Im}(f))$

Sia $f: V \to W$ con matrice associata $A$ di dimensioni $m \times n$ ($n = \dim(V), m = \dim(W)$).
* **Iniettiva (Monomorfismo):**
    * $\iff \text{Ker}(f) = \{0_V\}$
    * $\iff \dim(\text{Ker}(f)) = 0$
    * $\iff \text{rank}(A) = n$ (rango massimo rispetto alle colonne)
* **Suriettiva (Epimorfismo):**
    * $\iff \text{Im}(f) = W$
    * $\iff \dim(\text{Im}(f)) = m$
    * $\iff \text{rank}(A) = m$ (rango massimo rispetto alle righe)
* **Biettiva (Isomorfismo):**
    * $\iff$ $f$ è sia iniettiva che suriettiva
    * $\iff \text{rank}(A) = n = m$ (deve essere una matrice quadrata con rango massimo).

**Strategia per Esercizi con Parametri (Esercizi 5, 6):**
1.  **Matrice Quadrata ($m=n$)? (Esercizi 5A, 5D, 6):**
    * L'applicazione è iniettiva, suriettiva e biettiva *contemporaneamente*.
    * Questo accade se e solo se la matrice è [[03 - Rango, Invertibilità delle Matrici e Permutazioni|invertibile]].
    * **Calcola il determinante** $\det(A)$ in funzione del parametro $t$ o $h$ (usando Sarrus o lo [[04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace|Sviluppo di Laplace]]).
    * Se **$\det(A) \neq 0$**: L'applicazione è **biettiva (iniettiva e suriettiva)**.
    * Se **$\det(A) = 0$**: L'applicazione **non è né iniettiva né suriettiva**. (Il rango è < n).
2.  **Matrice Rettangolare ($m \neq n$)? (Esercizi 5B, 5C):**
    * L'applicazione **non può mai** essere biettiva.
    * Se $n > m$ (es. $B: \mathbb{R}^3 \to \mathbb{R}^2$): Non può **mai** essere **iniettiva**. È suriettiva se $\text{rank}(A) = m$.
    * Se $m > n$ (es. $C: \mathbb{R}^2 \to \mathbb{R}^3$): Non può **mai** essere **suriettiva**. È iniettiva se $\text{rank}(A) = n$.
    * Trova il rango in funzione del parametro (es. usando il metodo dei minori orlati).

---

### 4. Immagine di un Sottospazio (Esercizio 7)

Per trovare l'immagine di un *sottospazio* $U$ (cioè $L(U)$):
1.  Trova una base per $U$ (es. $\mathcal{B}_U = \{v_1, v_2\}$). Nell'Esercizio 7, questo significa risolvere il sistema omogeneo che definisce $U$.
2.  Calcola l'immagine di *ogni vettore della base* tramite l'applicazione: $w_1 = L(v_1)$ e $w_2 = L(v_2)$.
3.  L'immagine $L(U)$ è il sottospazio generato da questi nuovi vettori: $L(U) = \text{span}\{w_1, w_2\}$.
4.  Per trovare una *base* di $L(U)$, metti i generatori $w_1, w_2$ come colonne di una matrice e riduci per trovare le colonne di pivot (o semplicemente scarta i vettori linearmente dipendenti).

---

### 5. Matrici di Cambio di Base (Esercizi 8, 9, 13, 14)

Questa è la teoria chiave della [[13 - Matrici Associate e Cambiamento di Base]].
* **Matrice di Cambio Base $M_{\mathcal{C}}^{\mathcal{B}}$ (da $\mathcal{B}$ a $\mathcal{C}$):**
    * È la matrice $M_{\mathcal{C}}^{\mathcal{B}}(\text{id})$ che ha per colonne i vettori della base *vecchia* $\mathcal{B}$ espressi nelle coordinate della base *nuova* $\mathcal{C}$.
    * Proprietà: $M_{\mathcal{B}}^{\mathcal{C}} = (M_{\mathcal{C}}^{\mathcal{B}})^{-1}$.
* **Matrice Associata $M_{\mathcal{C}}^{\mathcal{B}}(T)$ (per $T: V \to W$):**
    * $\mathcal{B}$ è la base di partenza (Dominio $V$), $\mathcal{C}$ è la base di arrivo (Codominio $W$).
    * Le colonne della matrice sono le immagini dei vettori della base di partenza $\mathcal{B}$, $T(v_i)$, espresse nelle coordinate della base di arrivo $\mathcal{C}$.
    * In formula: $[T(v)]_{\mathcal{C}} = M_{\mathcal{C}}^{\mathcal{B}}(T) \cdot [v]_{\mathcal{B}}$.

---

### 6. Applicazioni a Spazi "Abstratti" (Polinomi) (Esercizi 11, 12)

Il trucco è tradurre i polinomi in vettori di coordinate usando una base.
* **Spazio:** $\mathbb{R}[t]_{\le n}$ (es. $\mathbb{R}[t]_{\le 2}$ per polinomi $a_0 + a_1t + a_2t^2$).
* **Dimensione:** $\dim(\mathbb{R}[t]_{\le n}) = n + 1$.
* **Base Standard:** $\mathcal{E} = \{1, t, t^2, \dots, t^n\}$.
* **Isomorfismo:** C'è un isomorfismo tra $\mathbb{R}[t]_{\le n}$ e $\mathbb{R}^{n+1}$.
    * $p(t) = a_0 + a_1t + a_2t^2 \iff [p]_{\mathcal{E}} = (a_0, a_1, a_2) \in \mathbb{R}^3$.

**Come risolvere (Esercizio 11):**
Per trovare la matrice $M_{\mathcal{C}}^{\mathcal{B}}(L)$ per $L: \mathbb{R}[t]_{\le 2} \to \mathbb{R}[t]_{\le 1}$:
1.  Si tratta di una matrice $2 \times 3$ (perché $\dim(\text{Dom})=3$, $\dim(\text{Cod})=2$).
2.  Prendi il primo vettore $p_1$ della base $\mathcal{B}$.
3.  Calcola la sua immagine: $w_1 = L(p_1) = tp_1'' - p_1'$. $w_1$ sarà un polinomio di grado $\le 1$.
4.  Scrivi $w_1$ nelle coordinate della base $\mathcal{C}$. Il vettore di coordinate risultante è la prima colonna della matrice.
5.  Ripeti per gli altri due vettori della base $\mathcal{B}$.

**Come risolvere (Esercizio 12):**
Vogliamo $A = M_{\mathcal{E}_4}^{\mathcal{B}}(T)$ con $\mathcal{B} = \{1, x, x^2, x^3\}$.
1.  Le colonne di $A$ devono essere $T(1), T(x), T(x^2), T(x^3)$.
2.  Il testo ci dà le immagini di una base diversa $\mathcal{D} = \{x^2+1, x^3, x^3+x+1, x-1\}$.
3.  **Strategia:** Per trovare la prima colonna $T(1)$, dobbiamo scrivere $1$ come combinazione lineare dei vettori di $\mathcal{D}$:
    $1 = a(x^2+1) + b(x^3) + c(x^3+x+1) + d(x-1)$
4.  Risolvendo il sistema (uguagliando i coefficienti di $1, x, x^2, x^3$), trovi $a, b, c, d$.
5.  Per linearità, applichiamo $T$ a entrambi i lati:
    $T(1) = T(a \cdot v_1 + b \cdot v_2 + \dots) = a \cdot T(v_1) + b \cdot T(v_2) + \dots$
6.  Ora sostituisci i valori dati (es. $T(v_1) = (1,0,k,1)$) e calcola il vettore $T(1)$.
7.  Questo vettore è la prima colonna di $A$. Ripeti per $x, x^2, x^3$.