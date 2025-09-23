# Algoritmo di Eliminazione di Gauss-Jordan

L'algoritmo di eliminazione di Gauss-Jordan è una procedura sistematica e fondamentale dell'algebra lineare che permette di trasformare qualsiasi matrice nella sua **forma a scala ridotta** (Reduced Row Echelon Form). Questo metodo è di importanza capitale perché costituisce la base per la risoluzione di molti problemi da parte dei calcolatori.

---

## Scopo e Operazioni Consentite

L'obiettivo dell'algoritmo è di semplificare una matrice applicando in sequenza una serie di operazioni specifiche, dette **operazioni elementari di riga**, che non alterano le soluzioni del sistema lineare associato.

Le tre operazioni elementari consentite sono:
1.  **Scambio:** Scambiare la posizione di due righe ($R_i \leftrightarrow R_j$).
2.  **Scalatura:** Moltiplicare tutti gli elementi di una riga per uno scalare non nullo ($R_i \to k R_i$, con $k \neq 0$).
3.  **Combinazione Lineare:** Sostituire una riga con la somma di se stessa e un multiplo di un'altra riga ($R_i \to R_i + k R_j$, con $i \neq j$).

---

## Le Fasi dell'Algoritmo

Il metodo si articola in due fasi principali:

### Fase 1: Eliminazione in Avanti (Metodo di Gauss)
Questa fase ha lo scopo di trasformare la matrice in una **forma a scala** (Echelon Form).
1.  Si identifica la prima colonna non nulla e si sceglie un **pivot** (il primo elemento non nullo). Se necessario, si scambia la riga del pivot per portarlo nella posizione più in alto possibile.
2.  Si normalizza il pivot a 1, dividendo la sua riga per il valore del pivot stesso.
3.  Si utilizza il pivot per annullare tutti gli elementi sottostanti nella stessa colonna, sottraendo multipli appropriati della riga del pivot.
4.  Si ripete il processo sulla sottomatrice rimanente, ignorando la riga e la colonna del pivot appena utilizzato, fino a esaurire tutte le righe.

### Fase 2: Sostituzione all'Indietro (Metodo di Jordan)
Questa fase trasforma la matrice da forma a scala a **forma a scala ridotta**.
1.  Partendo dall'ultimo pivot (quello più in basso a destra), lo si utilizza per annullare tutti gli elementi *sopra* di esso nella stessa colonna, tramite operazioni di combinazione lineare.
2.  Si ripete il processo per ogni pivot, procedendo dal basso verso l'alto, fino a quando ogni pivot non è l'unico elemento non nullo nella propria colonna.

---

## Applicazioni Fondamentali

L'algoritmo di Gauss-Jordan è lo strumento operativo per:


- [[Rango, Invertibilità delle Matrici e Permutazioni#Il Rango di una Matrice|Calcolare il rango di una matrice]]
- [[Rango, Invertibilità delle Matrici e Permutazioni#Algoritmo per il Calcolo della Matrice Inversa|Calcolare la matrice inversa]]
