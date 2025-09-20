## Introduzione e Richiami

Nelle lezioni precedenti sono stati introdotti i concetti fondamentali di **insieme**, le operazioni insiemistiche (unione, intersezione, differenza) e la definizione di **funzione** come una legge che associa a ogni elemento x di un insieme di partenza X un unico elemento y di un insieme di arrivo Y.

La lezione odierna prosegue approfondendo la teoria degli insiemi con l'introduzione del prodotto cartesiano e, successivamente, stabilisce le fondamenta del calcolo infinitesimale attraverso la presentazione della **struttura assiomatica dell'insieme dei numeri reali** R. Gli assiomi sono proposizioni fondamentali accettate come vere senza dimostrazione, dalle quali discendono, tramite deduzione logica, teoremi, lemmi e corollari che costituiscono l'intera teoria matematica.

## Il Prodotto Cartesiano

### Definizione per due Insiemi

Dati due insiemi non vuoti A e B, si definisce **prodotto cartesiano** di A per B, e si denota con A×B, l'insieme di tutte le **coppie ordinate** (a,b) dove il primo elemento a appartiene ad A e il secondo elemento b appartiene a B. Formalmente:

A×B={(a,b)∣a∈A e b∈B}

L'attributo "ordinata" sottolinea che la posizione degli elementi all'interno della coppia è significativa. Di conseguenza, il prodotto cartesiano non gode della proprietà commutativa, ovvero in generale A×B=B×A.

### Generalizzazione a n-Insiemi

Il concetto di prodotto cartesiano può essere esteso a un numero finito n di insiemi A1​,A2​,…,An​. In tal caso, il prodotto A1​×A2​×⋯×An​ è l'insieme di tutte le **n-uple ordinate** (a1​,a2​,…,an​), dove ogni elemento ai​ appartiene al corrispondente insieme Ai​ per i=1,…,n.

Ad esempio, per tre insiemi A,B,C, il prodotto cartesiano è l'insieme delle terne ordinate:

A×B×C={(a,b,c)∣a∈A,b∈B,c∈C}

### Notazione Potenziale

Quando si esegue il prodotto cartesiano di un insieme per se stesso, si adotta una notazione potenziale. Ad esempio:

- A×A si denota con A2.
    
- A×A×A si denota con A3.
    
- Il prodotto di A per se stesso n volte si denota con An.
    

### Esempio Pratico

Siano dati gli insiemi A={1,3,7} e B={2,5}. Il loro prodotto cartesiano A×B è:

A×B={(1,2),(1,5),(3,2),(3,5),(7,2),(7,5)}

### Il Grafico di una Funzione

Il prodotto cartesiano è fondamentale per definire il **grafico di una funzione**. Data una funzione f:X→Y, il suo grafico è un sottoinsieme del prodotto cartesiano X×Y costituito da tutte le coppie (x,y) in cui y è l'immagine di x tramite f. Formalmente, il grafico Gf​ è definito come:

Gf​={(x,y)∈X×Y∣y=f(x)}={(x,f(x))∣x∈X}

In questo caso, la seconda componente della coppia non è scelta arbitrariamente all'interno di Y, ma è determinata univocamente dalla prima componente x e dalla funzione f.

## La Struttura Assiomatica dei Numeri Reali (R)

L'insieme dei numeri reali, denotato con R, è definito da un sistema di assiomi che ne stabiliscono le proprietà algebriche, di ordinamento e di completezza. Questi assiomi sono suddivisi in tre gruppi.

### 1. Assiomi Relativi alle Operazioni (Assiomi di Campo)

^e1bb55

Su R sono definite due operazioni binarie interne, l'**addizione** (+) e la **moltiplicazione** (⋅), che associano a ogni coppia di numeri reali (a,b)∈R2 un unico numero reale, rispettivamente a+b e a⋅b. Queste operazioni soddisfano le seguenti proprietà per ogni a,b,c∈R:

1. **Proprietà Associativa:**
    
    - (a+b)+c=a+(b+c)
        
    - (a⋅b)⋅c=a⋅(b⋅c)
        
2. **Proprietà Commutativa:**
    
    - a+b=b+a
        
    - a⋅b=b⋅a
        
3. **Proprietà Distributiva:**
    
    - a⋅(b+c)=a⋅b+a⋅c
        
4. **Esistenza degli Elementi Neutri:**
    
    - Esiste un elemento
        
        0∈R (zero) tale che a+0=a.
        
    - Esiste un elemento
        
        1∈R (uno), con 1=0, tale che a⋅1=a.
        
5. **Esistenza dell'Opposto (Inverso Additivo):**
    
    - Per ogni a∈R, esiste un elemento −a∈R (l'opposto di a) tale che a+(−a)=0.
        
6. **Esistenza dell'Inverso (Inverso Moltiplicativo):**
    
    - Per ogni a∈R con a=0, esiste un elemento a−1∈R (l'inverso di a) tale che a⋅a−1=1.
        

### 2. Assiomi di Ordinamento

^6ced7f

In R è definita una relazione d'ordine totale "minore o uguale" (≤) che soddisfa le seguenti proprietà per ogni a,b,c∈R:

7. **Proprietà di Dicotomia:** Si ha sempre a≤b oppure b≤a.
    
8. **Proprietà Asimmetrica:** Se a≤b e b≤a, allora necessariamente a=b. ^a37a9a
    
9. **Compatibilità con l'Addizione:** Se a≤b, allora a+c≤b+c per ogni c∈R. ^84ce53
    
10. **Compatibilità con la Moltiplicazione (Chiusura dei non-negativi):** Se a≥0 e b≥0, allora a+b≥0 e a⋅b≥0.
    

### 3. Assioma di Completezza

^240591

Questo assioma distingue

R dall'insieme dei numeri razionali Q e garantisce l'assenza di "buchi" sulla retta reale.

- **Definizione di Insiemi Separati:** Due sottoinsiemi non vuoti A,B⊂R si dicono **separati** se ogni elemento di A è minore o uguale di ogni elemento di B, cioè ∀a∈A,∀b∈B,a≤b.
    
- **Assioma di Completezza:** Dati due sottoinsiemi non vuoti A,B⊂R separati, esiste almeno un elemento c∈R (detto **elemento di separazione**) tale che a≤c≤b per ogni a∈A e per ogni b∈B.
    
- **Insiemi Contigui:** Se l'elemento di separazione c è unico, i due insiemi A e B si dicono **contigui**.
    

---

## Dagli Assiomi alla Gerarchia degli Insiemi Numerici

A partire dagli assiomi di R, è possibile costruire e caratterizzare i sottoinsiemi numerici fondamentali.

#### L'Insieme dei Numeri Naturali (N)

Dall'assioma di esistenza degli elementi neutri, sappiamo che

1∈R. Applicando ripetutamente l'operazione di addizione, generiamo l'insieme dei

**numeri naturali**:

N={1,2,3,…}

Questo è un sottoinsieme di

R in cui valgono le proprietà associativa, commutativa e distributiva, ma mancano l'elemento neutro della somma (0) e gli opposti.

#### Dagli Interi (Z) ai Razionali (Q)

Per includere lo zero e gli opposti, si definiscono prima

N0​=N∪{0} e poi l'insieme degli **interi relativi** Z={0,±1,±2,…}. In

Z, tuttavia, manca l'esistenza dell'inverso per la maggior parte degli elementi.

Per soddisfare anche l'ultimo assioma algebrico, si introducono le frazioni, costruendo l'insieme dei **numeri razionali**:

Q={nm​∣m∈Z,n∈Z∖{0}}

Si ottiene così la seguente catena di inclusioni:

N⊂N0​⊂Z⊂Q⊆R

L'insieme

Q soddisfa tutti gli assiomi algebrici e di ordinamento, ma non l'assioma di completezza.

### L'incompletezza di Q: l'irrazionalità di 2![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0%20-0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834%2080h400000v40h-400000z"></path></svg>)​

Per dimostrare che Q⊂R (l'inclusione è stretta), è sufficiente mostrare che esiste un numero reale non razionale. L'esempio classico è 2![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0%20-0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834%2080h400000v40h-400000z"></path></svg>)​.

**Proposizione:** Non esiste alcun numero razionale c∈Q tale che c2=2.

_Dimostrazione (per assurdo):_ Supponiamo che esista un tale

c∈Q. Potremmo scriverlo come una frazione

c=nm​ ridotta ai minimi termini, ovvero con m e n primi tra loro.

Dall'ipotesi c2=2 segue:

(nm​)2=2⟹m2=2n2

Questo implica che m2 è un numero pari. Si può dimostrare che se il quadrato di un numero è pari, anche il numero stesso deve essere pari. Quindi,

m è pari e può essere scritto come m=2k per un qualche intero k. Sostituendo nell'equazione precedente:

(2k)2=2n2⟹4k2=2n2⟹n2=2k2

Questo mostra che anche

n2 è pari, e di conseguenza anche n è pari.

Siamo giunti a una contraddizione: sia

m sia n sono pari, quindi hanno 2 come fattore comune, il che va contro l'ipotesi che la frazione fosse ridotta ai minimi termini. L'assurdo dimostra che

2![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.08em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702
c-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14
c0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54
c44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10
s173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429
c69,-144,104.5,-217.7,106.5,-221
l0%20-0
c5.3,-9.3,12,-14,20,-14
H400000v40H845.2724
s-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7
c-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z
M834%2080h400000v40h-400000z"></path></svg>)​ non può essere un numero razionale, e pertanto Q=R.

---

Dagli assiomi enunciati è possibile dedurre tutte le proprietà algebriche e di ordinamento dei numeri reali.

### Conseguenze degli Assiomi delle Operazioni

- **Regola di Semplificazione per la Somma:** Se a+b=a+c, allora b=c. _Dimostrazione:_ Partendo da b e utilizzando l'esistenza dell'elemento neutro (0) e dell'opposto (-a), si ha: b=b+0=0+b=(−a+a)+b=−a+(a+b). Sfruttando l'ipotesi a+b=a+c: −a+(a+c)=(−a+a)+c=0+c=c. Dunque b=c.
    
- **Regola di Semplificazione per il Prodotto:** Se a⋅b=a⋅c e a=0, allora b=c. _Dimostrazione:_ Dato che a=0, esiste il suo inverso a−1. Si ha: b=b⋅1=b⋅(a⋅a−1)=(a⋅b)⋅a−1. Per ipotesi a⋅b=a⋅c: (a⋅c)⋅a−1=(c⋅a)⋅a−1=c⋅(a⋅a−1)=c⋅1=c. Dunque b=c.
    
- **Legge di Annullamento del Prodotto:** a⋅b=0⟺a=0 oppure b=0. _Dimostrazione (⇐):_ Proviamo che a⋅0=0 per ogni numero reale a. Consideriamo: a+a⋅0=a⋅1+a⋅0=a⋅(1+0)=a⋅1=a=a+0. Otteniamo quindi l'uguaglianza a+a⋅0=a+0. Per la regola di semplificazione rispetto alla somma, si conclude che a⋅0=0. _Dimostrazione (⇒):_ Si supponga a⋅b=0. Se a=0, allora esiste l'inverso a−1. Moltiplicando entrambi i membri per a−1 si ha: b=b⋅1=b⋅(a⋅a−1)=a−1⋅(a⋅b)=a−1⋅0=0.
    
- **Inesistenza dell'Inverso di Zero:** Non è possibile definire l'inverso di 0. Se per assurdo esistesse 0−1, per definizione di inverso si dovrebbe avere 0⋅0−1=1. Tuttavia, per la legge di annullamento del prodotto, 0⋅0−1=0. Si giungerebbe quindi all'assurdo 1=0.
    
- **Unicità dell'Opposto:** L'opposto di un numero reale è unico. Per ogni numero reale a esiste l'opposto −a tale che a+(−a)=0. Se supponiamo che esista un altro elemento b tale che a+b=0, allora per la legge di semplificazione dell'addizione, partendo da a+(−a)=a+b, si ottiene −a=b.
    
- **Unicità dell'Inverso:** L'inverso di un numero reale a=0 è unico. Per ogni a=0 esiste a−1 tale che a⋅a−1=1. Se supponiamo che esista un altro elemento b tale che a⋅b=1, allora per la legge di semplificazione del prodotto si ha che a−1=b.
    
- **Opposto dell'opposto:** Per ogni numero reale a vale −(−a)=a. Infatti, −(−a) è l'opposto di −a, ma anche a è l'opposto di −a, poiché −a+a=0. Per l'unicità dell'opposto, segue la tesi.
    
- **Regola dei segni:** Per ogni a,b∈R:
    
    1. (−a)⋅b=−(a⋅b). Dimostrazione: (−a)⋅b+a⋅b=[(−a)+a]⋅b=0⋅b=0. Questo significa che (−a)⋅b è l'opposto di a⋅b, cioè −(a⋅b).
        
    2. (−a)⋅(−b)=a⋅b. Dimostrazione: (−a)⋅(−b)=−[a⋅(−b)]=−[−(a⋅b)]. Per la proprietà dell'opposto dell'opposto, si ottiene a⋅b.
        

### Conseguenze degli Assiomi di Ordinamento

- **Equivalenza della disuguaglianza:** a≤b⟺b−a≥0. _Dimostrazione:_ Se a≤b, sommando −a a entrambi i membri si ottiene a−a≤b−a, ovvero 0≤b−a. Viceversa, se b−a≥0, sommando a a entrambi i membri si ha (b−a)+a≥0+a, da cui b≥a.
    
- **Proprietà Transitiva:** Se a≤b e b≤c, allora a≤c. _Dimostrazione:_ Da a≤b segue b−a≥0. Allo stesso modo, da b≤c segue c−b≥0. Poiché la somma di numeri non negativi è non negativa, si ha (b−a)+(c−b)≥0. Semplificando si ottiene c−a≥0, che equivale a c≥a.
    
- **Segno dell'Opposto:** a≥0⟺−a≤0. _Dimostrazione:_ Se a≥0, sommando −a a entrambi i membri si ottiene a+(−a)≥0+(−a), ovvero 0≥−a.
    
- **Moltiplicazione per un Numero Positivo:** Se a≤b e c≥0, allora a⋅c≤b⋅c. La disuguaglianza si conserva. _Dimostrazione:_ Da a≤b segue b−a≥0. Poiché anche c≥0, il prodotto (b−a)c≥0. Per la proprietà distributiva, bc−ac≥0, da cui bc≥ac.
    
- **Moltiplicazione per un Numero Negativo:** Se a≤b e c≤0, allora a⋅c≥b⋅c. La disuguaglianza si inverte. _Dimostrazione:_ Se c≤0, allora −c≥0. Poiché b−a≥0, si ha (b−a)(−c)≥0. Svolgendo il prodotto, si ottiene −bc+ac≥0, da cui ac≥bc.
    
- **Relazione tra gli Inversi:** Se 0<a<b, allora 0<b−1<a−1. _Dimostrazione:_ Poiché a,b>0, anche a−1,b−1>0. Si moltiplica la disuguaglianza a<b per la quantità positiva a−1b−1. Si ottiene a(a−1b−1)<b(a−1b−1). Semplificando, si arriva a b−1<a−1.