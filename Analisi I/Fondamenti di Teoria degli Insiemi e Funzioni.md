## Informazioni Generali sul Corso

### Modalità d'Esame
L'esame di Analisi I si compone di una prova scritta e una prova orale. Per agevolare gli studenti, verranno organizzate delle prove in itinere, comunemente definite "provine". Queste prove si terranno a metà e alla fine del corso e, se superate, esonereranno lo studente dalla prova scritta finale, permettendogli di concentrarsi esclusivamente sulla preparazione per l'esame orale previsto per gennaio.

### Metodologia di Studio
È fondamentale studiare in modo costante e rimanere al passo con il programma. Il tempo a disposizione è limitato, pertanto la sola frequenza delle lezioni non è sufficiente. È necessario dedicare tempo allo studio individuale per consolidare i concetti appresi. Le prove in itinere, previste per novembre, rappresentano un'importante occasione di autovalutazione per comprendere il proprio livello di preparazione.

La sessione d'esami principale si terrà tra gennaio e febbraio. È consigliabile sostenere il maggior numero di esami in questa finestra temporale per evitare sovrapposizioni con le lezioni del secondo semestre.

### Orario di Ricevimento e Contatti
L'orario di ricevimento è fissato per il mercoledì e il giovedì mattina alle ore 11:00. Per gli studenti del corso, il giovedì potrebbe risultare più comodo. Si consiglia di inviare un'email preventiva per confermare la propria presenza.

- **Sito Docente:** `docenti.unina.it` (consultare regolarmente per avvisi e materiali).
- **Email:** `teresa.radice@unina.it`

### Materiale Didattico
Il corso si basa su slide preparate direttamente dalla docente, disponibili sulla sua pagina web personale. Si sconsiglia l'uso di appunti non ufficiali presi da altri studenti, in quanto potrebbero contenere imprecisioni. Durante le lezioni, è preferibile concentrarsi sulla spiegazione piuttosto che fotografare le slide, dato che sono già a disposizione online.

I libri di testo consigliati sono:
1.  **Marcellini-Sbordone**, *Analisi Matematica 1*. È accettabile anche la versione intitolata *Calcolo*. La versione *Elementi di Analisi Matematica* non è adatta per questo corso di laurea.
2.  **Fiorenza-Greco**, *Lezioni di Analisi Matematica 1*.

## Introduzione alla Teoria degli Insiemi

### Definizione di Insieme e Notazioni
Si introduce la nozione di insieme secondo la definizione di Cantor:

> Un **insieme** è un aggregato caotico di oggetti determinati e distinti.

Analizziamo i termini di questa definizione:
- **Aggregato caotico**: L'ordine in cui gli elementi sono elencati all'interno dell'insieme è irrilevante.
- **Oggetti determinati**: Per qualsiasi oggetto, è sempre possibile stabilire se esso appartenga o meno all'insieme.
- **Oggetti distinti**: Ogni elemento all'interno dell'insieme viene considerato una sola volta; le ripetizioni sono irrilevanti.

Per convenzione, gli insiemi si indicano con lettere maiuscole (es. $S$), mentre i loro elementi (o oggetti) si indicano con lettere minuscole (es. $a, b$).

**Esempio:**
L'insieme $S$ costituito dagli elementi $a$ e $b$ si rappresenta come:
$$S = \{a, b\}$$
Essendo un aggregato caotico, scrivere $S = \{a, b\}$ è equivalente a scrivere $S = \{b, a\}$.

### Simboli e Notazioni Fondamentali
- **Appartenenza**: Per indicare che un elemento $a$ appartiene all'insieme $S$, si scrive $a \in S$. Per indicare che non appartiene, si scrive $a \notin S$.
- **Quantificatori**: 
  - $\forall$: "per ogni"
  - $\exists$: "esiste"
  - $\nexists$: "non esiste"
- **Tale che**: Si può indicare con i due punti ($:$) o con una barra (/).

### Relazioni tra Insiemi: Inclusione
Dati due insiemi $A$ e $B$, si definiscono le seguenti relazioni:

1.  **Sottoinsieme (o Inclusione)**: $A$ è un sottoinsieme di $B$, e si scrive $A \subseteq B$, se ogni elemento di $A$ è anche un elemento di $B$.
    $$A \subseteq B \iff (\forall x \in A \implies x \in B)$$

2.  **Sottoinsieme Proprio (o Inclusione Stretta)**: $A$ è un sottoinsieme proprio di $B$, e si scrive $A \subset B$, se $A$ è un sottoinsieme di $B$ e i due insiemi non coincidono. Ciò significa che deve esistere almeno un elemento in $B$ che non appartiene ad $A$.
    $$A \subset B \iff (A \subseteq B) \land (\exists y \in B : y \notin A)$$

**Esempio:**
Siano $S = \{a, b\}$ e $S' = \{a, c, d\}$. In questo caso, $S \not\subseteq S'$ perché $b \in S$ ma $b \notin S'$.
Se invece consideriamo $S'' = \{a, b, c, d\}$, allora vale l'inclusione stretta $S \subset S''$, poiché tutti gli elementi di $S$ sono in $S''$ e inoltre esistono elementi in $S''$ (in questo caso $c$ e $d$) che non appartengono a $S$.

### Definizione di Sottoinsiemi tramite Proprietà
Una proprietà $\alpha$ si dice **definita** su un insieme $S$ se, per ogni elemento $x \in S$, è possibile determinare univocamente se $x$ gode della proprietà $\alpha$ oppure no.

Questa nozione è fondamentale per costruire sottoinsiemi. Dato un insieme $S$ e una proprietà $\alpha$ definita su di esso, è possibile definire un nuovo insieme $A$ contenente tutti e soli gli elementi di $S$ che soddisfano la proprietà $\alpha$.
$$A = \{x \in S : x \text{ verifica } \alpha\}$$
Per costruzione, $A$ è un sottoinsieme di $S$ ($A \subseteq S$).

**Esempio 1: Numeri pari**
- Insieme: $S = \{1, 2, 3, 4, 5\}$
- Proprietà $\alpha$: "$x$ è un numero pari".
La proprietà $\alpha$ è ben definita in $S$, perché per ogni numero in $S$ possiamo stabilire se è pari o no.
L'insieme $A$ degli elementi di $S$ che soddisfano $\alpha$ è:
$$A = \{x \in S : x \text{ è pari}\} = \{2, 4\}$$
Poiché $A$ non coincide con $S$, si ha che $A \subset S$.

**Esempio 2: L'Insieme Vuoto**
- Insieme: $S = \{1, 2, 3, 4, 5\}$
- Proprietà $\beta$: "$x$ è maggiore di 100".
Anche $\beta$ è ben definita in $S$. Tuttavia, nessun elemento di $S$ soddisfa questa proprietà. L'insieme risultante è privo di elementi e si chiama **insieme vuoto**, indicato con il simbolo $\emptyset$.
$$B = \{x \in S : x > 100\} = \emptyset$$
Per convenzione, l'insieme vuoto è sottoinsieme di ogni insieme.

## Operazioni Fondamentali tra Insiemi
Dati due insiemi $A$ e $B$, si definiscono le seguenti operazioni:

1.  **Intersezione ($A \cap B$)**: L'insieme degli elementi che appartengono sia ad $A$ sia a $B$.
    $$A \cap B = \{x : x \in A \text{ e } x \in B\}$$

2.  **Unione ($A \cup B$)**: L'insieme degli elementi che appartengono ad almeno uno dei due insiemi, $A$ o $B$.
    $$A \cup B = \{x : x \in A \text{ oppure } x \in B\}$$

3.  **Differenza ($A - B$)**: L'insieme degli elementi che appartengono ad $A$ ma non appartengono a $B$.
    $$A - B = \{x : x \in A \text{ e } x \notin B\}$$

**Esempio:**
Siano $A = \{1, 2, 3, 5\}$ e $B = \{2, 6, 7\}$.
- $A \cap B = \{2\}$
- $A \cup B = \{1, 2, 3, 5, 6, 7\}$
- $A - B = \{1, 3, 5\}$

## Elementi di Logica: Implicazioni tra Proprietà

- **Implicazione Semplice ($\implies$)**: Se la proprietà $\alpha$ implica la proprietà $\beta$ ($"\alpha \implies \beta"$), significa che ogni volta che $\alpha$ è vera, anche $\beta$ deve essere vera. In questo caso, $\alpha$ è **condizione sufficiente** per $\beta$, e $\beta$ è **condizione necessaria** per $\alpha$.
- **Doppia Implicazione ($\iff$)**: Se $\alpha \implies \beta$ e $\beta \implies \alpha$, le due proprietà sono **equivalenti** e si scrive $"\alpha \iff \beta"$ (si legge "$\alpha$ se e solo se $\beta$").

**Esempio:**
Siano $r, s, t$ tre rette nel piano.
- Proprietà $\alpha$: $r$ e $s$ sono entrambe parallele a $t$.
- Proprietà $\beta$: $r$ e $s$ sono parallele tra loro.

Per la proprietà transitiva del parallelismo, se $\alpha$ è vera, allora anche $\beta$ è vera ($"\alpha \implies \beta"$). Il viceversa non è vero: due rette $r$ e $s$ possono essere parallele tra loro senza essere parallele a una terza retta $t$. Quindi $\beta$ non implica $\alpha$.
In termini di insiemi, l'insieme delle terne di rette che verificano $\alpha$ è un sottoinsieme proprio dell'insieme delle terne di rette che verificano $\beta$.

## Introduzione al Concetto di Funzione

### Definizione di Funzione
Una **funzione** $f$ da un insieme $X$ a un insieme $Y$ è una legge che associa a ogni elemento di $X$ uno e un solo elemento di $Y$. Si scrive:
$$f: X \to Y$$
- $X$ è il **dominio** della funzione.
- $Y$ è il **codominio** della funzione.
- Per un elemento $x \in X$, l'elemento corrispondente in $Y$ si chiama **immagine** di $x$ tramite $f$ e si indica con $f(x)$.
### Funzione iniettiva, suriettiva, biettiva
- Una funzione si definisce iniettiva se e solo se ad elementi distinti del dominio corrispondo elementi distinti del codominio
- Una funzione si definisce suriettiva se tutte le y del codominio sono immagini di almento una x
- Una funzione si definisce biettiva se tutte le y del codominio sono immagini uniche di X distinte del dominio
### Funzione Inversa e Funzione Composta
- **Funzione Inversa ($f^{-1}$)**: Se una funzione $f: X \to Y$ è sia **iniettiva** (elementi diversi del dominio hanno immagini diverse) sia **suriettiva** (ogni elemento del codominio è immagine di almeno un elemento del dominio), allora è possibile definire la **funzione inversa** $f^{-1}: Y \to X$. Questa funzione associa a ogni elemento $y \in Y$ l'unico elemento $x \in X$ tale che $f(x) = y$.

- **Funzione Composta ($g \circ f$)**: Date due funzioni $f: X \to Y$ e $g: Y \to Z$, la funzione composta $g \circ f$ (si legge "g composto f") è una nuova funzione che va da $X$ a $Z$ e si definisce applicando prima $f$ e poi $g$:
    $$(g \circ f)(x) = g(f(x))$$