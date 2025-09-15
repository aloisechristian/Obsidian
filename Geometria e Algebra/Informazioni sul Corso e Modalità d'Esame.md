### Struttura e Metodologia di Studio
- Si sottolinea l'importanza di uno studio costante e parallelo allo svolgimento delle lezioni, dato il ritmo serrato del calendario accademico.
- La sola frequenza alle lezioni è considerata insufficiente; è indispensabile un approfondimento individuale a casa.
- Le lezioni rappresentano un'opportunità di confronto diretto con il docente, pertanto gli studenti sono incoraggiati a porre domande e a intervenire attivamente.

### Modalità di Valutazione
- L'esame si compone di una prova scritta e una prova orale.
- Sono previste due prove in itinere (una a metà corso, a novembre, e una alla fine) che, se superate, possono esonerare lo studente dalla prova scritta finale.
- Le prove in itinere costituiscono un'importante occasione di autovalutazione per gli studenti.
- Le sessioni d'esame si terranno a partire da gennaio. È consigliabile sostenere il maggior numero di esami possibile durante la prima finestra utile per evitare sovrapposizioni con i corsi del secondo semestre.

### Orario di Ricevimento e Contatti
- **Orario**: Mercoledì e Giovedì alle ore 11:00.
- **Modalità**: Si raccomanda di inviare una mail per annunciare la propria presenza.
- **Email**: `teresa.punto@unina.it`.
- **Sito Docente**: Tutte le informazioni, gli avvisi e il materiale didattico sono pubblicati sulla pagina personale del docente, accessibile dal portale di ateneo `docenti.unina.it`. È responsabilità dello studente consultare regolarmente il sito per aggiornamenti.

## Materiale Didattico

### Risorse Fornite dal Docente
- Il corso si basa su slide preparate dal docente e rese disponibili sulla sua pagina web. Tali slide costituiscono il riferimento principale per il contenuto richiesto in sede d'esame.
- Non è necessario stampare le slide, in quanto sono sempre consultabili online.

### Testi Consigliati
- Il libro di testo di riferimento è **Marcellini-Sbordone, *Analisi Matematica 1***. È accettabile anche la versione intitolata ***Calcolo 1***.
- **Attenzione**: La versione *Elementi di Analisi Matematica* non è adatta per il corso di laurea in Ingegneria, poiché presenta contenuti ridotti.
- Sebbene l'acquisto del testo consigliato sia suggerito, qualsiasi altro libro di testo universitario di Analisi I può essere un valido supporto, da integrare con gli appunti delle lezioni e le slide.

### Appunti degli Studenti
- Si sconsiglia vivamente l'utilizzo di appunti di altri studenti non revisionati dal docente, poiché in passato si sono rivelati contenere errori significativi.

## Introduzione alla Teoria degli Insiemi

### Definizione di Insieme secondo Cantor
Un insieme è definito come un **aggregato caotico di oggetti determinati e distinti**.
- **Aggregato caotico**: L'ordine in cui gli elementi sono elencati non ha importanza. Ad esempio, l'insieme contenente gli elementi $a$ e $b$ è identico sia che venga scritto come $\{a, b\}$ sia come $\{b, a\}$.
- **Oggetti determinati**: Per qualsiasi oggetto, è sempre possibile stabilire in modo univoco se esso appartiene o non appartiene all'insieme.
- **Oggetti distinti**: Ogni elemento all'interno di un insieme è unico. Non è ammessa la ripetizione di elementi.

### Notazione e Simbologia Fondamentale
- **Insiemi**: Si indicano con lettere maiuscole (es. $S$, $A$, $B$).
- **Elementi**: Si indicano con lettere minuscole (es. $a$, $b$, $x$).
- **Appartenenza**: Il simbolo $a \in S$ significa che l'elemento $a$ appartiene all'insieme $S$.
- **Non appartenenza**: Il simbolo $c \notin S$ significa che l'elemento $c$ non appartiene all'insieme $S$. La negazione è spesso indicata sbarrando il simbolo dell'affermazione.

### Quantificatori Logici e Operatori
- **Per ogni** (Quantificatore universale): $\forall$
- **Esiste** (Quantificatore esistenziale): $\exists$
- **Non esiste**: $\nexists$
- **Tale che**: Si indica con i due punti ($:$) o con una barra verticale ($|$).

### Relazioni tra Insiemi: Inclusione
Siano $A$ e $B$ due insiemi.
- **Inclusione (o Sottoinsieme)**: $A$ è incluso in $B$, e si scrive $A \subseteq B$, se ogni elemento di $A$ è anche elemento di $B$. Formalmente: $$ A \subseteq B \iff (\forall x, x \in A \Rightarrow x \in B) $$
- **Inclusione Stretta (o Sottoinsieme Proprio)**: $A$ è strettamente incluso in $B$, e si scrive $A \subset B$, se $A$ è incluso in $B$ e $A$ è diverso da $B$. Ciò implica che esiste almeno un elemento in $B$ che non appartiene ad $A$.

### Proprietà Definite su un Insieme
- Una proprietà $\alpha$ è **ben definita** su un insieme $S$ se, per ogni elemento $x \in S$, è possibile determinare se $x$ gode della proprietà $\alpha$ oppure non ne gode.
- **Esempio 1**: Sia $S = \{1, 2, 3, 4, 5\}$ e $\alpha$ la proprietà "$x$ è pari". $\alpha$ è ben definita su $S$ perché per ogni numero in $S$ possiamo dire se è pari o no. Il sottoinsieme di $S$ che soddisfa $\alpha$ è $\{2, 4\}$.
- **Esempio 2**: Sia $T$ l'insieme delle automobili e $\alpha$ la proprietà "$x$ è pari". $\alpha$ non è ben definita su $T$, poiché il concetto di parità non si applica alle automobili.

### L'Insieme Vuoto
- L'insieme vuoto, indicato con il simbolo $\emptyset$ o con $\{\}$, è l'insieme che non contiene alcun elemento.
- Viene introdotto per rappresentare il caso in cui nessun elemento di un insieme di partenza soddisfa una data proprietà. Ad esempio, il sottoinsieme di $S = \{1, 2, 3, 4, 5\}$ che verifica la proprietà "$x > 100$" è l'insieme vuoto.
- Per convenzione, l'insieme vuoto è sottoinsieme di ogni insieme: $\forall S, \emptyset \subseteq S$.

### Implicazione ed Equivalenza tra Proprietà
- **Implicazione**: Si dice che una proprietà $\alpha$ implica una proprietà $\beta$ (scritto $\alpha \Rightarrow \beta$) se ogni volta che $\alpha$ è vera, anche $\beta$ è vera.
- **Equivalenza (o Doppia Implicazione)**: Due proprietà $\alpha$ e $\beta$ sono equivalenti (scritto $\alpha \iff \beta$) se $\alpha$ implica $\beta$ e, viceversa, $\beta$ implica $\alpha$. Verificare una delle due proprietà equivale a verificare anche l'altra.

## Cenni sulle Funzioni
- Una **funzione** da un insieme dominio $X$ a un insieme codominio $Y$ è una legge che associa a **ogni** elemento di $X$ **uno e un solo** elemento di $Y$.
- **Esempio**: Sia $X$ l'insieme degli iscritti a Ingegneria e $Y$ l'insieme delle donne. L'associazione "ad ogni studente $x \in X$ si associa la sua mamma $y \in Y$" definisce una funzione, poiché ogni studente ha una e una sola madre biologica.
- **Funzione Iniettiva**: Una funzione è iniettiva se a elementi distinti del dominio associa elementi distinti del codominio.
- **Esempio di non iniettività**: La funzione precedente (studente $\rightarrow$ madre) non è iniettiva. Infatti, due fratelli sono elementi distinti del dominio $X$, ma vengono associati allo stesso elemento del codominio $Y$ (la stessa madre).