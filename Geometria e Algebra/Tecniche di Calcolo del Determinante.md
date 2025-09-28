# Tecniche di Calcolo del Determinante

Il determinante è un valore scalare associato a ogni [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Tipologie di Matrici Speciali|matrice quadrata]] che ne racchiude proprietà fondamentali, come l'[[03 - Rango, Invertibilità delle Matrici e Permutazioni|invertibilità]]. Esistono diversi metodi per calcolarlo, ma è sempre buona norma verificare prima la presenza di casi particolari che possono semplificare enormemente i calcoli.

---

## 1. Casi Particolari e Semplificazioni

Prima di applicare metodi generali, è utile controllare se la matrice presenta una delle seguenti caratteristiche.

### Matrici Triangolari e Diagonali
Il calcolo del determinante è immediato per una [[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali#Tipologie di Matrici Speciali|matrice triangolare]] (superiore o inferiore) o per una matrice diagonale. In questi casi, il determinante è semplicemente il **prodotto degli elementi sulla diagonale principale**.

Data una matrice $A$ triangolare o diagonale di ordine $n$:
$$ \det(A) = a_{11} \cdot a_{22} \cdot \dots \cdot a_{nn} = \prod_{i=1}^{n} a_{ii} $$
Questo include la [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#La Matrice Identità come Elemento Neutro|matrice identità]], il cui determinante è sempre 1.

### Righe o Colonne con Molti Zeri
Se una riga o una colonna contiene molti zeri, il metodo più rapido è quasi sempre lo [[#2. Sviluppo di Laplace (Metodo dei Cofattori)|Sviluppo di Laplace]], scegliendo di espandere lungo quella riga o colonna. Molti termini della sommatoria si annulleranno, riducendo drasticamente il numero di calcoli necessari.

### Riga o Colonna Nulla
Se una matrice ha una riga o una colonna interamente composta da zeri, il suo determinante è nullo:
$$ \det(A) = 0 $$

### Righe o Colonne Uguali o Proporzionali
Se una matrice ha due righe o due colonne identiche, o se una riga/colonna è un multiplo di un'altra, il suo determinante è nullo:
$$ \det(A) = 0 $$

---

## 2. Sviluppo di Laplace (Metodo dei Cofattori)

Il [[04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#Teorema di Laplace per il Calcolo del Determinante|teorema di Laplace]] fornisce un metodo di calcolo ricorsivo che riduce il determinante di una matrice $n \times n$ a una somma di determinanti di matrici $(n-1) \times (n-1)$.

1.  **Sviluppo lungo la riga i-esima**: Si sceglie una riga $i$ e si calcola la somma dei prodotti di ogni elemento $a_{ij}$ di quella riga per il suo [[04 - Proprietà dei Determinanti, Teorema di Binet e Sviluppo di Laplace#1. Sottomatrici, Minori e Cofattori|cofattore]] $a_{ij}^* = (-1)^{i+j} |A_{ij}|$.
    $$ \det(A) = \sum_{j=1}^{n} a_{ij} \cdot a_{ij}^* $$

2.  **Sviluppo lungo la colonna j-esima**: Analogamente, si sceglie una colonna $j$.
    $$ \det(A) = \sum_{i=1}^{n} a_{ij} \cdot a_{ij}^* $$

**Vantaggi:**
-   Molto efficiente se applicato a righe/colonne con molti zeri.
-   Pratico per il calcolo manuale di determinanti di matrici $3 \times 3$ o $4 \times 4$.

---

## 3. Metodo di Riduzione a Scala (Eliminazione Gaussiana)

Questa tecnica sfrutta le proprietà del determinante in relazione alle [[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Scopo del Gioco e Regole: Le Operazioni Elementari di Riga|operazioni elementari di riga]]. L'obiettivo è trasformare la matrice in una [[#Matrici Triangolari e Diagonali|matrice triangolare]], il cui determinante è il prodotto degli elementi diagonali, e risalire al determinante originale.

La procedura è la seguente:
1.  Applicare operazioni elementari di riga per ridurre la matrice $A$ a una forma a scala $A'$.
2.  Tenere traccia di come ogni operazione modifica il determinante:
    -   **Scambio di righe ($R_i \leftrightarrow R_j$)**: Il determinante cambia segno.
    -   **Moltiplicazione per scalare ($R_i \to kR_i$)**: Il determinante viene moltiplicato per $k$.
    -   **Combinazione lineare ($R_i \to R_i + kR_j$)**: Il determinante rimane invariato.
3.  Una volta ottenuta la matrice triangolare $A'$, calcolare il prodotto dei suoi elementi diagonali.
4.  Utilizzare le modifiche tracciate per risalire al determinante della matrice originale $A$.

**Vantaggi:**
-   **Approccio sistematico e universale:** L'algoritmo gestisce efficientemente qualsiasi matrice quadrata.
    -   **Se la matrice è invertibile (rango massimo):** Il metodo la trasforma in una matrice triangolare con tutti elementi non nulli sulla diagonale. Il calcolo del determinante si riduce al semplice prodotto di questi elementi (tenendo conto delle operazioni usate).
    -   **Se la matrice non è invertibile (singolare):** Durante l'eliminazione, l'algoritmo genererà inevitabilmente una riga di zeri. Questo implica che almeno un elemento sulla diagonale della forma triangolare sarà zero, rendendo il suo determinante nullo e terminando il calcolo in anticipo.
-   Metodo algoritmico, ideale per l'implementazione su calcolatore e generalmente il più efficiente per matrici dense di grandi dimensioni.

---

## 4. Metodo della Definizione Formale (tramite Permutazioni)

Questo metodo si basa sulla definizione rigorosa del determinante ed è usato principalmente per scopi teorici.

Data una matrice quadrata $A$ di ordine $n$, il suo determinante è:
$$ \det(A) = \sum_{\sigma \in S_n} \text{sgn}(\sigma) \prod_{i=1}^{n} a_{i, \sigma(i)} $$

**Svantaggi:**
-   Computazionalmente impraticabile per matrici di ordine superiore a $3 \times 3$.