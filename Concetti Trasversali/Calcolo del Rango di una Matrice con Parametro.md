#tecnica-risolutiva #geometria-e-algebra #matrici #rango

Questa nota descrive le strategie per calcolare il rango di una matrice quando una o più delle sue entrate dipendono da un parametro variabile (es. $x, k, \lambda$, ecc.). L'approccio cambia a seconda che la matrice sia quadrata o rettangolare.

---

## Principio Generale

Il [[03 - Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|rango]] di una matrice è l'ordine massimo di una sua sottomatrice quadrata con determinante non nullo. Questa idea guida la nostra strategia.

### 1. Strategia per Matrici Quadrate ($n \times n$)

Si sfrutta il legame diretto tra rango e determinante.

1.  **Calcolare il Determinante**: Si calcola il determinante della matrice. Il risultato sarà un'espressione dipendente dal parametro.
2.  **Trovare i Valori Critici**: Si trovano i valori del parametro che annullano il determinante, risolvendo l'equazione $\det(A) = 0$.
3.  **Discutere i Casi**:
    *   **Caso A ($\det(A) \neq 0$)**: Per tutti i valori del parametro che non sono critici, il determinante è non nullo. Per il [[04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#6. Relazione tra Determinante e Invertibilità|teorema di equivalenza]], la matrice ha rango massimo, ovvero $Rk(A)=n$.
    *   **Caso B ($\det(A) = 0$)**: Per ogni valore critico del parametro, il rango è certamente minore di $n$. Si sostituisce il valore nella matrice e si calcola il rango della matrice numerica risultante, tipicamente cercando un minore di ordine $n-1$ con determinante non nullo.

### 2. Strategia per Matrici Rettangolari ($m \times n$)

Non potendo calcolare il determinante della matrice intera, si usa il **metodo dei minori**.

1.  **Determinare il Rango Massimo Possibile**: Il rango massimo è $k = \min(m, n)$.
2.  **Identificare i Minori di Ordine Massimo**: Si estraggono tutte le sottomatrici quadrate di ordine $k$.
3.  **Calcolare i Determinanti**: Si calcola il determinante di ciascun minore.
4.  **Discutere i Casi**:
    *   Il rango è $k$ se esiste **almeno un** minore di ordine $k$ con determinante non nullo.
    *   Il rango è minore di $k$ **solo se** esiste un valore del parametro che annulla **contemporaneamente tutti** i determinanti dei minori di ordine $k$.

---

## Esempio Svolto (Matrice Quadrata $3 \times 3$)

Calcolare il rango della matrice $A$ al variare di $x \in \mathbb{R}$:
$$ A = \begin{pmatrix} 1+x & 1 & 2 \\ 3 & -1 & 1 \\ -1 & 3 & 4-x \end{pmatrix} $$

1.  **Calcolo del Determinante**:
    $\det(A) = x^2 - 3x - 4$

2.  **Ricerca dei Valori Critici**:
    $x^2 - 3x - 4 = 0 \implies (x-4)(x+1) = 0$
    I valori critici sono $x=4$ e $x=-1$.

3.  **Discussione dei Casi**:

    *   **Caso 1: $x \in \mathbb{R} \setminus \{-1, 4\}$**
        In questo caso, $\det(A) \neq 0$. La matrice ha rango massimo.
        **$Rk(A) = 3$**

    *   **Caso 2: $x = 4$ o $x = -1$**
        In questi casi, $\det(A) = 0$, quindi il rango è certamente minore di 3. Analizziamoli singolarmente.

        **Sottocaso A: $x = 4$**
        Sostituiamo $x=4$ nella matrice originale:
        $$ A(4) = \begin{pmatrix} 5 & 1 & 2 \\ 3 & -1 & 1 \\ -1 & 3 & 0 \end{pmatrix} $$
        Poiché il $\det(A(4)) = 0$, il rango è $< 3$. Verifichiamo se è 2. Prendiamo un minore $2 \times 2$, ad esempio quello in alto a sinistra:
        $$ \det \begin{pmatrix} 5 & 1 \\ 3 & -1 \end{pmatrix} = (5)(-1) - (1)(3) = -5 - 3 = -8 $$
        Dato che $-8 \neq 0$, abbiamo trovato una sottomatrice $2 \times 2$ con determinante non nullo.

> [!info] Giustificazione Teorica
> Il [[04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#6. Relazione tra Determinante e Invertibilità|Criterio di Invertibilità e Rango]] afferma che una matrice quadrata ha rango massimo se e solo se il suo determinante è non nullo.
> 1. Dato che $\det(A(4))=0$, sappiamo che $Rk(A(4)) < 3$.
> 2. Abbiamo trovato una [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Sottomatrici|sottomatrice]] $2 \times 2$ con determinante non nullo ($-8$). Questa sottomatrice, considerata come matrice a sé stante, ha rango massimo 2.
> 3. Il rango di una matrice è sempre maggiore o uguale al rango di una sua qualsiasi sottomatrice. Pertanto, $Rk(A(4)) \ge 2$.
> Mettendo insieme i punti 1 e 3, otteniamo $2 \le Rk(A(4)) < 3$. Poiché il rango è un numero intero, l'unica possibilità è che sia 2.

**Se $x = 4$, allora $Rk(A) = 2$.**

**Sottocaso B: $x = -1$**
Sostituiamo $x=-1$ nella matrice originale:
$$ A(-1) = \begin{pmatrix} 0 & 1 & 2 \\ 3 & -1 & 1 \\ -1 & 3 & 5 \end{pmatrix} $$
Anche in questo caso $Rk(A(-1)) < 3$. Troviamo un minore non nullo, ad esempio:
$$ \det \begin{pmatrix} 0 & 1 \\ 3 & -1 \end{pmatrix} = (0)(-1) - (1)(3) = -3 \neq 0 $$
Per la stessa logica del caso precedente, concludiamo che il rango è 2.
**Se $x = -1$, allora $Rk(A) = 2$.**

### Riepilogo Finale
-   **Se $x \neq -1$ e $x \neq 4$**, il rango è **3**.
-   **Se $x = -1$ o $x = 4$**, il rango è **2**.