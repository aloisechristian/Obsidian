## 1. Dal Calcolo Definito all'Integrale Indefinito
Nello studio degli integrali definiti, abbiamo stabilito che l'elemento di separazione tra le somme integrali inferiori e superiori, quando unico, è l'integrale definito $\int_a^b f(x) dx$. Geometricamente, per una funzione positiva, questo numero rappresenta l'area del rettangoloide.
Passando agli **integrali indefiniti**, introduciamo la **funzione integrale** $F(x)$, definita come:
$$ F(x) = \int_a^x f(t) dt $$
dove l'estremo superiore di integrazione è variabile.

## 2. Il Teorema Fondamentale del Calcolo Integrale
Il legame tra derivazione e integrazione è sancito dal Teorema Fondamentale del Calcolo Integrale. Esso afferma che se $f(x)$ è una funzione continua nell'intervallo $[a, b]$, allora la funzione integrale $F(x)$ è derivabile e la sua derivata coincide con la funzione integranda:
$$ F'(x) = f(x) $$

### Dimostrazione
La dimostrazione si basa sulla costruzione del rapporto incrementale della funzione integrale:
$$ \frac{F(x+h) - F(x)}{h} = \frac{1}{h} \int_x^{x+h} f(t) dt $$
Per il teorema della media integrale, esiste un punto $x_h \in [x, x+h]$ tale che l'integrale sia uguale a $h \cdot f(x_h)$. Semplificando $h$, il rapporto diventa $f(x_h)$. Facendo tendere $h \to 0$, si ha $x_h \to x$. Poiché $f$ è continua, $f(x_h) \to f(x)$, dimostrando che $F'(x) = f(x)$.

## 3. Definizione di Primitiva e Proprietà
Una funzione $F(x)$ derivabile in $[a, b]$ si dice **primitiva** di $f(x)$ se:
$$ F'(x) = f(x) $$
L'operazione di ricerca della primitiva consiste nel trovare una funzione la cui derivata restituisca la funzione data.

### Caratterizzazione delle Primitive
Se $F(x)$ è una primitiva di $f(x)$, allora anche $G(x) = F(x) + C$ (con $C$ costante reale) è una primitiva, poiché la derivata di una costante è zero. Inversamente, il Teorema di Caratterizzazione afferma che due primitive della stessa funzione differiscono sempre per una costante:
$$ G(x) - F(x) = C $$

## 4. Relazione tra Integrali Definiti e Indefiniti
Sia $\phi(x)$ una generica primitiva di una funzione continua $f(x)$ in $[a, b]$. Vale la relazione:
$$ \int_a^b f(x) dx = \phi(b) - \phi(a) $$
Questa formula permette di calcolare l'integrale definito tramite le primitive (integrale indefinito). Per dimostrarlo, si sfrutta il fatto che la funzione integrale $F(x)$ è una primitiva tale che $F(a)=0$. Ponendo $F(x) = \phi(x) + C$, si determina $C = -\phi(a)$ e infine $F(b) = \phi(b) - \phi(a)$.

## 5. Metodi di Integrazione e Integrali Elementari
Il calcolo degli integrali indefiniti si basa sull'inversione delle regole di derivazione. È cruciale riconoscere le forme composte, dove deve comparire la derivata dell'argomento $f'(x)$.

### Formule Fondamentali
Le seguenti formule valgono a meno di una costante additiva $C$:

* **Potenza:** $\int f(x)^b \cdot f'(x) dx = \frac{f(x)^{b+1}}{b+1} \quad (b \neq -1)$
    * *Esempio elementare:* $\int x dx = \frac{x^2}{2}$
* **Logaritmica:** $\int \frac{f'(x)}{f(x)} dx = \ln|f(x)|$
* **Esponenziale:** $\int e^{f(x)} \cdot f'(x) dx = e^{f(x)}$
    * *Esempio:* $\int x e^{-x^2} dx$. Moltiplicando e dividendo per $-2$ per ottenere la derivata dell'esponente: $-\frac{1}{2} e^{-x^2}$.
* **Seno:** $\int \sin(f(x)) \cdot f'(x) dx = -\cos(f(x))$
* **Coseno:** $\int \cos(f(x)) \cdot f'(x) dx = \sin(f(x))$
* **Funzioni Trigonometriche Inverse:**
    * $\int \frac{1}{\sqrt{1-x^2}} dx = \arcsin x$
    * $\int \frac{1}{1+x^2} dx = \arctan x$

### Esempi di Applicazione
1.  **Integrale della Tangente:**
    $$ \int \tan x dx = \int \frac{\sin x}{\cos x} dx = -\int \frac{-\sin x}{\cos x} dx = -\ln|\cos x| + C $$
2.  **Manipolazione Algebrica:**
    Consideriamo $\int \frac{\sin^3 x \cos x}{1+\sin^2 x} dx$. Scrivendo $\sin^3 x = \sin x(\sin^2 x)$ e aggiungendo/sottraendo 1 al numeratore, si scompone l'integrale in due parti. Risolvendo i passaggi, si ottiene:
    $$ \frac{\sin^2 x}{2} - \frac{1}{2} \ln(1+\sin^2 x) + C $$

## 6. Integrazione di Funzioni Razionali
Per integrare funzioni del tipo $\phi(x) = \frac{N(x)}{D(x)}$ con $N$ e $D$ polinomi:
1.  **Se grado($N$) $\ge$ grado($D$):** Si esegue la divisione polinomiale, riducendo l'integrale alla somma di un polinomio e di una frazione con numeratore di grado inferiore.
2.  **Se grado($N$) $<$ grado($D$):** Ci si concentra sul denominatore $D(x)$.

### Casi con Denominatore di Secondo Grado
Nel caso in cui $D(x)$ sia di secondo grado, si distingue in base al discriminante $\Delta$:

* **Se $\Delta > 0$:** Il denominatore ha due radici reali distinte $x_1, x_2$. Si utilizza il metodo dei fratti semplici:
    $$ \frac{R(x)}{D(x)} = \frac{A}{x-x_1} + \frac{B}{x-x_2} $$
    L'integrazione risulta nella somma di logaritmi: $A \ln|x-x_1| + B \ln|x-x_2| + C$.

* **Se $\Delta = 0$:** Il denominatore ha due radici reali coincidenti $x_1 = x_2$. La decomposizione assume la forma:
    $$ \frac{R(x)}{D(x)} = \frac{A}{x-x_1} + \frac{B}{(x-x_1)^2} $$
    Integrando i termini si ottiene:
    $$ \int \left( \frac{A}{x-x_1} + \frac{B}{(x-x_1)^2} \right) dx = A \ln|x-x_1| - \frac{B}{x-x_1} + C $$

* **Se $\Delta < 0$:** Il denominatore non ha radici reali ma due radici complesse coniugate. Non è possibile scomporre in fattori di primo grado in $\mathbb{R}$.
    L'obiettivo è ricondursi alla forma notevole dell'**arcotangente**: $\int \frac{f'(x)}{1+[f(x)]^2} dx = \arctan(f(x))$.
    Si procede con il completamento del quadrato al denominatore e manipolando il numeratore affinché compaia la derivata del denominatore (per la parte logaritmica) più una parte costante (per l'arcotangente).

## 7. Formula di Hermite
Quando il denominatore $D(x)$ ha un grado elevato e presenta **radici multiple** (sia reali che complesse), il metodo dei fratti semplici classico diventa laborioso. Si ricorre alla **Formula di Hermite**.

### Principio di Scomposizione
La formula di Hermite permette di scomporre la funzione razionale $\frac{N(x)}{D(x)}$ in due parti:
1.  Una somma di fratti semplici "classici" relativi alle radici prese con molteplicità 1.
2.  La derivata di una funzione razionale.

La struttura della scomposizione è:
$$ \frac{N(x)}{D(x)} = \sum \frac{A_i}{x-x_i} + \dots + \frac{d}{dx} \left( \frac{Q(x)}{D^*(x)} \right) $$

Dove:
* La sommatoria include tutte le radici del denominatore (reali o complesse) trattate come se fossero semplici.
* $D^*(x)$ è il polinomio ottenuto dal denominatore $D(x)$ abbassando di 1 la molteplicità di ogni sua radice. In pratica, $D^*(x) = \text{MCD}(D(x), D'(x))$.
* $Q(x)$ è un polinomio a coefficienti incogniti di grado inferiore di uno rispetto a $D^*(x)$.

### Procedimento Operativo
1.  Si calcola $D^*(x)$.
2.  Si scrive l'identità con i coefficienti incogniti ($A, B, \dots$ e i coefficienti di $Q(x)$).
3.  Si deriva il termine $\frac{Q(x)}{D^*(x)}$.
4.  Si fa il minimo comune multiplo e si applica il principio di identità dei polinomi per trovare le costanti risolvendo il sistema lineare associato.

L'integrazione diventa immediata poiché la parte sotto derivata si "elide" con l'integrale:
$$ \int \frac{d}{dx} \left( \frac{Q(x)}{D^*(x)} \right) dx = \frac{Q(x)}{D^*(x)} $$
Mentre la parte rimanente (sommatoria) darà luogo a logaritmi (per radici reali) o arcotangenti (per radici complesse coniugate).

# Approfondimento: La Formula di Hermite

La **Formula di Hermite** è una tecnica di scomposizione per funzioni razionali $\frac{N(x)}{D(x)}$ utilizzata quando il denominatore $D(x)$ presenta **radici con molteplicità elevata** (maggiori di 1).

A differenza del metodo dei fratti semplici standard, che richiederebbe di scrivere una costante per ogni potenza della radice (es. $\frac{A}{x} + \frac{B}{x^2} + \frac{C}{x^3}...$), la formula di Hermite permette di calcolare la parte "difficile" (le potenze alte) tramite una semplice derivata, riducendo drasticamente il numero di costanti da trovare.

## 1. La Struttura della Formula
L'idea chiave è scomporre la funzione in due parti:
1.  **Parte Logaritmica/Arcotangente:** Una somma di fratti semplici che considera tutte le radici del denominatore *come se fossero semplici* (molteplicità 1).
2.  **Parte Razionale (Derivata):** La derivata di una frazione che gestisce le molteplicità elevate.

La formula generale è:
$$ \frac{N(x)}{D(x)} = \underbrace{\sum \frac{A_k}{x-x_k} + \sum \frac{B_j x + C_j}{x^2+p_j x + q_j}}_{\text{Come se le radici fossero semplici}} + \frac{d}{dx} \left( \frac{Q(x)}{D^*(x)} \right) $$

### Definizioni dei componenti
* **$D(x)$**: Il denominatore originale.
* **$D^*(x)$**: Il polinomio ridotto. Si ottiene prendendo tutti i fattori di $D(x)$ e abbassando il loro esponente di 1.
    * *Esempio:* Se $D(x) = (x-1)^3 (x^2+1)^2$, allora $D^*(x) = (x-1)^2 (x^2+1)$.
    * Formalmente: $D^*(x) = \text{MCD}(D(x), D'(x))$.
* **$Q(x)$**: Un polinomio a coefficienti incogniti. Il suo grado deve essere **inferiore di 1** rispetto al grado di $D^*(x)$.

---

## 2. Esempio Pratico Risolto

Proviamo a scomporre una funzione complessa, analoga a quella presente nei tuoi appunti (*Formula di Hermite.pdf*), dove abbiamo radici complesse con molteplicità.

Consideriamo l'integrale:
$$ \int \frac{x^3 + x^2 + 3x + 1}{x(x^2+1)^2} dx $$

### Analisi del Denominatore
Il denominatore è $D(x) = x(x^2+1)^2$.
* $x=0$: radice reale semplice (molteplicità 1).
* $x^2+1=0$: radici complesse coniugate ($\pm i$) con **molteplicità 2**.

### Costruzione di $D^*(x)$
Per trovare $D^*(x)$, abbassiamo di 1 le molteplicità dei fattori di $D(x)$:
* Il fattore $x$ ha esponente 1 $\to$ diventa $x^0 = 1$ (sparisce da $D^*$).
* Il fattore $(x^2+1)$ ha esponente 2 $\to$ diventa $(x^2+1)^1$.

Quindi:
$$ D^*(x) = x^2+1 $$

### Impostazione della Scomposizione
La scomposizione avrà:
1.  Fratti semplici per le radici prese una sola volta ($x$ e $x^2+1$).
2.  La derivata di $\frac{Q(x)}{D^*(x)}$. Poiché $D^*$ è di grado 2, $Q(x)$ sarà un polinomio generico di grado 1 ($ax+b$).

$$ \frac{x^3 + x^2 + 3x + 1}{x(x^2+1)^2} = \frac{A}{x} + \frac{Bx+C}{x^2+1} + \frac{d}{dx} \left( \frac{ax+b}{x^2+1} \right) $$

### Calcolo della Derivata
Svolgiamo la derivata del termine a destra (regola del quoziente):
$$ \frac{d}{dx} \left( \frac{ax+b}{x^2+1} \right) = \frac{a(x^2+1) - (ax+b)(2x)}{(x^2+1)^2} = \frac{ax^2+a - 2ax^2 - 2bx}{(x^2+1)^2} = \frac{-ax^2 - 2bx + a}{(x^2+1)^2} $$

### Minimo Comune Multiplo
Sostituiamo la derivata nell'equazione e facciamo il m.c.m che è $x(x^2+1)^2$:

$$ \frac{x^3 + ...}{D(x)} = \frac{A(x^2+1)^2 + (Bx+C)x(x^2+1) + x(-ax^2 - 2bx + a)}{x(x^2+1)^2} $$

Sviluppando i numeratori (uguaglianza dei polinomi):
* $A(x^4+2x^2+1)$
* $Bx^4 + Bx^2 + Cx^3 + Cx$
* $-ax^3 - 2bx^2 + ax$

Raggruppiamo per potenze di $x$:
* $x^4$: $A + B$
* $x^3$: $C - a$
* $x^2$: $2A + B - 2b$
* $x^1$: $C + a$
* $x^0$: $A$

Il sistema lineare uguagliando al numeratore originale $x^3 + x^2 + 3x + 1$:
$$
\begin{cases}
A + B = 0 & (\text{coef. } x^4) \\
C - a = 1 & (\text{coef. } x^3) \\
2A + B - 2b = 1 & (\text{coef. } x^2) \\
C + a = 3 & (\text{coef. } x^1) \\
A = 1 & (\text{termine noto})
\end{cases}
$$

### Risoluzione del Sistema
1.  Da $A=1$, la prima eq. diventa $1+B=0 \Rightarrow B=-1$.
2.  Dalle eq. con $C$ e $a$:
    * $C-a=1$
    * $C+a=3$
    * Sommando: $2C=4 \Rightarrow C=2$.
    * Sottraendo: $2a=2 \Rightarrow a=1$.
3.  Troviamo $b$: $2(1) + (-1) - 2b = 1 \Rightarrow 1 - 2b = 1 \Rightarrow b=0$.

Coefficienti trovati: $A=1, B=-1, C=2, a=1, b=0$.

### Integrazione Finale
Sostituiamo i coefficienti nella formula di scomposizione iniziale:
$$ \frac{N(x)}{D(x)} = \frac{1}{x} + \frac{-x+2}{x^2+1} + \frac{d}{dx} \left( \frac{x}{x^2+1} \right) $$

Ora integriamo ambo i membri. **La magia di Hermite** sta nel fatto che l'integrale della parte derivata si annulla con la derivata stessa:

$$ \int \frac{N(x)}{D(x)} dx = \int \frac{1}{x} dx + \int \frac{-x+2}{x^2+1} dx + \int \frac{d}{dx} \left( \frac{x}{x^2+1} \right) dx $$

$$ = \ln|x| - \frac{1}{2}\ln(x^2+1) + 2\arctan(x) + \frac{x}{x^2+1} + C $$

*(Nota: $\int \frac{-x}{x^2+1} dx$ diventa $-\frac{1}{2}\ln(x^2+1)$ e $\int \frac{2}{x^2+1} dx$ diventa $2\arctan x$)*.

---
## 3. Quando usare Hermite?
| Metodo | Consigliato quando... |
| :--- | :--- |
| **Fratti Semplici** | Il denominatore ha solo radici semplici o molteplicità basse (es. 2). |
| **Formula di Hermite** | Il denominatore ha radici con **molteplicità alta** (es. $(x-1)^4$) o radici complesse multiple. Riduce drasticamente i calcoli algebrici. |