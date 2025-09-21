## Introduzione al Corso di Geometria e Algebra

### L'Importanza dell'Algebra Lineare
L'algebra lineare rappresenta uno strumento matematico fondamentale, essenziale per modellizzare e comprendere la realtà. In quasi tutte le discipline scientifiche e ingegneristiche, problemi complessi vengono ricondotti e risolti attraverso i metodi dell'algebra lineare. La sua centralità è tale che costituisce un insegnamento di base nel primo semestre di tutte le facoltà di ingegneria a livello globale. La padronanza di concetti come la risoluzione di sistemi di equazioni lineari è una competenza imprescindibile per un ingegnere.

### Struttura e Metodologia Didattica
Il corso si articola in 48 ore di lezione, un formato denso che richiede un approccio didattico mirato. Si privilegerà una metodologia interattiva rispetto alla tradizionale lezione frontale. L'apprendimento attivo sarà incoraggiato attraverso la partecipazione diretta degli studenti, che verranno invitati a svolgere esercizi alla lavagna. Questo approccio ha un duplice obiettivo:
1.  **Consolidare l'apprendimento:** L'esperienza diretta nella risoluzione di un problema favorisce la memorizzazione e una più profonda comprensione dei concetti.
2.  **Fornire feedback:** Permette al docente di valutare il livello di comprensione della classe e di chiarire eventuali dubbi in tempo reale.

La partecipazione attiva è volontaria, ma fortemente incoraggiata, e non avrà alcuna influenza sulla valutazione finale.

### Indicazioni per lo Studio e Modalità d'Esame
Per un apprendimento efficace, è raccomandata una frequentazione costante e attiva delle lezioni. Si stima che per ogni ora di lezione siano necessarie circa due ore di studio individuale. Al termine di ogni blocco tematico, verranno dedicate delle sessioni specifiche alla risoluzione di esercizi.

L'esame è concepito come una verifica delle competenze acquisite e non come il fine ultimo del corso. La sua struttura è la seguente:
- **Prova Scritta (obbligatoria):** Consente di ottenere un voto massimo di 26/30.
- **Prova Orale (facoltativa):** Gli studenti che ottengono un punteggio compreso tra 18 e 26 allo scritto possono decidere se accettare il voto o sostenere una prova orale per migliorarlo. L'orale è obbligatorio per chi ottiene 17. Con un punteggio inferiore a 16, la prova deve essere ripetuta.

### Risorse e Comunicazioni
Le comunicazioni e la distribuzione del materiale didattico avverranno tramite un canale dedicato su Microsoft Teams. Verranno fornite delle note scritte dal docente che copriranno tutti gli argomenti trattati. Non è necessario acquistare un libro di testo specifico; qualsiasi testo di base di algebra lineare o risorsa online affidabile (es. Wikipedia) è sufficiente, dato il carattere fondamentale degli argomenti del corso.

## Introduzione alle Matrici

### Motivazioni: Dai Sistemi Lineari all'Efficienza Computazionale
Il nostro studio dell'algebra lineare inizia con le matrici. Storicamente, le matrici furono introdotte per risolvere in modo sistematico ed efficiente i sistemi di equazioni lineari. Un sistema lineare è un insieme di equazioni lineari che devono essere soddisfatte simultaneamente.

Per illustrare il concetto, consideriamo due esempi:

1.  **Problema Semplice (Ricetta a 3 ingredienti):** La preparazione di una torta da 750g con burro, farina e zucchero, dove le quantità sono legate da semplici relazioni lineari (es. la quantità di burro è nota, la farina è il doppio della somma di burro e zucchero). Questo sistema si risolve agevolmente per sostituzione.

2.  **Problema Complesso (Ricetta a 6 ingredienti):** Aumentando il numero di ingredienti e la complessità delle relazioni tra le loro quantità, il metodo della sostituzione diventa lungo e laborioso. Questo evidenzia un principio cruciale in ingegneria: non è sufficiente saper risolvere un problema, ma è necessario risolverlo in un **tempo utile**. L'efficienza è fondamentale.

Le matrici forniscono un apparato formale e computazionale per affrontare questi problemi in modo più rapido e strutturato. Le loro applicazioni moderne sono vastissime, dalla modellizzazione del traffico urbano all'algoritmo PageRank di Google, che classifica le pagine web utilizzando una matrice di enormi dimensioni.

### Definizione Formale di Matrice

^1f6aea

Una **matrice** è una tabella rettangolare ordinata di elementi, detti **entrate**. Una matrice è univocamente determinata da tre caratteristiche:
1.  Il numero di righe, $m$.
2.  Il numero di colonne, $n$.
3.  L'insieme $S$ a cui appartengono le sue entrate.

Una matrice $A$ con $m$ righe e $n$ colonne si dice di dimensioni $m \times n$. La sua generica entrata è indicata con $A_{ij}$, dove $i$ rappresenta l'indice di riga ($1 \le i \le m$) e $j$ l'indice di colonna ($1 \le j \le n$). La prima competenza da acquisire è identificare immediatamente le dimensioni di qualsiasi matrice.

### Tipologie di Matrici Speciali
Per le matrici quadrate, ovvero quelle con lo stesso numero di righe e colonne ($m=n$), si definiscono alcune tipologie notevoli:

- **Matrice Quadrata:** Una matrice di dimensioni $n \times n$.
- **Diagonale Principale:** In una matrice quadrata, è l'insieme delle entrate $A_{ii}$ con $i$ che va da 1 a $n$.
- **Matrice Triangolare Superiore:** Una matrice quadrata in cui tutte le entrate al di sotto della diagonale principale sono nulle. Formalmente: $A_{ij} = 0$ per ogni $i > j$.
- **Matrice Triangolare Inferiore:** Una matrice quadrata in cui tutte le entrate al di sopra della diagonale principale sono nulle. Formalmente: $A_{ij} = 0$ per ogni $i < j$.
- **Matrice Diagonale:** Una matrice quadrata in cui tutte le entrate non appartenenti alla diagonale principale sono nulle. Formalmente: $A_{ij} = 0$ per ogni $i \neq j$. Una matrice diagonale è contemporaneamente triangolare superiore e inferiore.
- **Matrice Simmetrica:** Una matrice quadrata tale che $A_{ij} = A_{ji}$ per ogni $i, j$. Si può dimostrare che ogni matrice diagonale è anche simmetrica.

### Operazioni Elementari con le Matrici

#### Somma e Matrice Nulla
La **somma** tra due matrici $A$ e $B$ è definita solo se esse hanno le stesse dimensioni. Il risultato è una matrice $C$ della stessa dimensione, le cui entrate sono la somma delle entrate corrispondenti: $C_{ij} = A_{ij} + B_{ij}$.

La **matrice nulla**, indicata con $0$, è una matrice con tutte le entrate uguali a zero. Essa funge da elemento neutro per la somma: $A + 0 = A$.

#### Moltiplicazione per uno Scalare
Uno **scalare** è un numero reale. Il prodotto di una matrice $A$ per uno scalare $c$ è una matrice della stessa dimensione di $A$, ottenuta moltiplicando ogni entrata di $A$ per $c$: $(cA)_{ij} = c \cdot A_{ij}$.

La **sottrazione** tra matrici $A$ e $B$ (della stessa dimensione) è definita come $A - B = A + (-1)B$.

#### Proprietà della Somma e della Moltiplicazione Scalare
Date due matrici $A, B$ di dimensioni $m \times n$ e due scalari $\lambda, \mu \in \mathbb{R}$, valgono le seguenti proprietà:

- **Associatività (scalare):** $\lambda (\mu A) = (\lambda \mu) A$
- **Distributività (rispetto alla somma di scalari):** $(\lambda + \mu) A = \lambda A + \mu A$
- **Distributività (rispetto alla somma di matrici):** $\lambda (A + B) = \lambda A + \lambda B$
- **Compatibilità con la trasposizione:** $(\lambda A)^T = \lambda A^T$

### [[Prodotto Matricale e Algoritmo di Gauss Jordan#Il Prodotto Riga per Colonna|Prodotto tra Matrici (Prodotto Riga per Colonna)]]
Il prodotto tra due matrici $A$ e $B$ è un'operazione più complessa.

- **Condizione di Conformabilità:** Il prodotto $A \cdot B$ è definito solo se il numero di colonne di $A$ è uguale al numero di righe di $B$. Se $A$ è una matrice $m \times n$ e $B$ è una matrice $n \times p$, la matrice prodotto $C = A \cdot B$ avrà dimensioni $m \times p$.

- **Definizione Formale:** L'entrata $C_{ik}$ della matrice prodotto si ottiene moltiplicando termine a termine gli elementi della $i$-esima riga di $A$ per quelli della $k$-esima colonna di $B$ e sommando i risultati:
$$C_{ik} = \sum_{j=1}^{n} A_{ij} B_{jk}$$

- **Non-Commutatività:** Una delle proprietà più importanti del prodotto tra matrici è che, in generale, **non è commutativo**: $A \cdot B \neq B \cdot A$. Spesso, se il prodotto $A \cdot B$ è definito, $B \cdot A$ potrebbe non esserlo, o potrebbe risultare in una matrice di dimensioni diverse. Anche quando entrambe le matrici sono quadrate della stessa dimensione, il prodotto non è generalmente commutativo.