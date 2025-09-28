# Tecniche Algoritmiche e Dimostrative

Questa nota ha lo scopo di raccogliere e collegare le tecniche di problem-solving, gli algoritmi e i metodi dimostrativi che si incontrano in diverse discipline. Riconoscere questi pattern trasversali è fondamentale per sviluppare una comprensione più profonda e integrata della matematica e dell'ingegneria.

---

## Tecniche Algoritmiche

Un **algoritmo** è una sequenza finita e ordinata di passi elementari che portano alla risoluzione di un problema. Molti problemi complessi possono essere scomposti e risolti attraverso procedure sistematiche.

### Algoritmi Iterativi

Questi algoritmi applicano ripetutamente un insieme di operazioni fino al raggiungimento di una condizione di terminazione.

- **[[02 - Prodotto Matricale e Algoritmo di Gauss Jordan#Il Metodo di Eliminazione di Gauss-Jordan|Algoritmo di Eliminazione di Gauss-Jordan]]:** Una procedura sistematica per trasformare una qualsiasi matrice nella sua forma a scala ridotta tramite operazioni elementari di riga. È il metodo fondamentale utilizzato dai calcolatori per risolvere i sistemi di equazioni lineari e calcolare la matrice inversa.

- **[[Fondamenti di Informatica/Sistemi di Numerazione Posizionale e Aritmetica Binaria#Conversione da Decimale a Binario|Conversione da Decimale a Binario]]:** Un algoritmo che utilizza divisioni successive per 2 (per la parte intera) e moltiplicazioni successive per 2 (per la parte frazionaria) per convertire un numero dalla base 10 alla base 2. La logica si può generalizzare per la conversione in qualsiasi base B.

---

## Metodi Dimostrativi

In matematica, una dimostrazione è un argomento logico che, a partire da un insieme di assiomi, stabilisce la verità di un'affermazione (teorema).

### Dimostrazione per Assurdo

Questa tecnica dimostrativa è una delle più potenti. La sua logica consiste nel:
1.  Negare la tesi che si vuole dimostrare.
2.  Sviluppare le conseguenze logiche di questa negazione.
3.  Arrivare a una contraddizione, ovvero un'affermazione che è palesemente falsa (es. $1=0$) o che contraddice una delle ipotesi iniziali.
4.  Concludere che, poiché la negazione della tesi porta a un assurdo, la tesi originale deve essere necessariamente vera.

- **[[03 - Insiemi Numerici, Completezza e Estremo Superiore#^1ca686|Esempio: Irrazionalità della Radice di 2]]:** Un esempio classico di dimostrazione per assurdo. Si suppone che $\sqrt{2}$ sia un numero razionale e, attraverso passaggi logici, si arriva alla contraddizione che numeratore e denominatore della frazione ridotta ai minimi termini sarebbero entrambi pari.