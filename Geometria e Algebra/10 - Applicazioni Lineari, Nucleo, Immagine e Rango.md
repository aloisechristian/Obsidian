## Riepilogo e Introduzione alla Seconda Parte del Corso

Questa lezione segna l'inizio della seconda metà del corso di Geometria e Algebra. La prima parte è stata dedicata alla costruzione degli strumenti fondamentali per risolvere i [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer|sistemi lineari]], la motivazione principale del corso. Il percorso logico seguito è stato:

1.  **[[01 - Introduzione all'Algebra Lineare, Matrici e Operazioni Fondamentali|Matrici]]**: Introduzione alle matrici, alle loro proprietà e operazioni, con un focus sul [[Algoritmo di Eliminazione di Gauss Jordan|metodo di eliminazione di Gauss-Jordan]] come strumento risolutivo primario.
2.  **[[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer|Sistemi Lineari]]**: Applicazione delle matrici per risolvere sistemi di equazioni lineari.
3.  **[[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|Spazi Vettoriali]]**: Studio della struttura dell'insieme delle soluzioni, in particolare per i [[05 - Metodo Matriciale per Sistemi Lineari, Teorema di Rouché-Capelli, Teorema di Cramer#Sistemi Omogenei e Struttura delle Soluzioni|sistemi omogenei]], che ha portato alla nozione di [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|spazio vettoriale]]. Sono stati analizzati vari esempi di spazi vettoriali, come i polinomi, le matrici $M_{m,n}(\mathbb{R})$ e, soprattutto, gli spazi $\mathbb{R}^n$.

La questione che si pone ora è come mettere in relazione questi diversi spazi vettoriali. Esiste un modo per farli "comunicare" tra loro? La risposta è affermativa e ci introduce al concetto di **applicazioni lineari**.

## Applicazioni Lineari: Funzioni che Preservano la Struttura

Il modo più naturale per mettere in relazione due [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Insieme e Notazioni|insiemi]] è tramite una [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Definizione di Funzione|funzione]]. Poiché gli spazi vettoriali non sono semplici insiemi, ma insiemi dotati di una **struttura algebrica** (somma tra vettori e prodotto per uno scalare), siamo interessati a funzioni che non ignorino questa struttura, ma anzi la "preservino". L'idea è quella di definire una corrispondenza che sia compatibile con le operazioni definite sugli spazi.

### Definizione di Applicazione Lineare (o Omomorfismo)

Dati due [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|spazi vettoriali]] $V$ e $W$ su campo $\mathbb{R}$, una funzione $f: V \to W$ è detta **applicazione lineare** (o **omomorfismo** di spazi vettoriali) se soddisfa le seguenti due proprietà per ogni coppia di vettori $u, v \in V$ e per ogni scalare $\lambda \in \mathbb{R}$:

1.  **Additività (rispetto della somma):** L'immagine della somma di due vettori è uguale alla somma delle loro immagini.
    $$f(u+v) = f(u)+f(v)$$
2.  **Omogeneità (rispetto del prodotto per scalare):** L'immagine del prodotto di un vettore per uno scalare è uguale al prodotto dello scalare per l'immagine del vettore.
    $$f(\lambda v) = \lambda f(v)$$

È fondamentale notare che le operazioni non sono le stesse su entrambi i lati delle equazioni. In $f(u+v)$, la somma '$+$' è quella definita in $V$, mentre in $f(u)+f(v)$, la somma '$+$' è quella definita in $W$. Analogamente, in $f(\lambda v)$ il prodotto per scalare '$\cdot$' è in $V$, mentre in $\lambda f(v)$ è in $W$. Lo spazio $V$ è detto **dominio** e $W$ **codominio** dell'applicazione $f$.

## Prime Proprietà delle Applicazioni Lineari

### L'Immagine del Vettore Nullo

Una conseguenza diretta e immediata della definizione è che ogni applicazione lineare mappa il vettore nullo del dominio nel vettore nullo del codominio.

**Proposizione:** Se $f: V \to W$ è un'applicazione lineare, allora $f(0_V) = 0_W$.

*Dimostrazione:* Possiamo scrivere il vettore nullo $0_V$ come il prodotto dello scalare $0$ per un qualsiasi vettore $v \in V$: $0_V = 0 \cdot v$. Applicando la funzione $f$ e usando la proprietà di omogeneità (ii), otteniamo:
$$f(0_V) = f(0 \cdot v) = 0 \cdot f(v) = 0_W$$
Si noti la distinzione tra lo scalare $0 \in \mathbb{R}$, il vettore nullo $0_V \in V$ e il vettore nullo $0_W \in W$. Un'applicazione $f: V \to W$ che non soddisfa $f(0_V)=0_W$ non può essere lineare.

### Linearità sulle Combinazioni Lineari

Le due proprietà (i) e (ii) di un'applicazione lineare possono essere combinate per mostrare che l'immagine di una [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#Somma di Sottospazi e Spazio Generato|combinazione lineare]] di vettori è la combinazione lineare delle immagini dei vettori con gli stessi coefficienti. Per $n$ vettori $v_1, \dots, v_n \in V$ e $n$ scalari $\lambda_1, \dots, \lambda_n \in \mathbb{R}$:
$$f(\lambda_1 v_1 + \lambda_2 v_2 + \dots + \lambda_n v_n) = \lambda_1 f(v_1) + \lambda_2 f(v_2) + \dots + \lambda_n f(v_n)$$
Questo può essere scritto in modo compatto usando la notazione di sommatoria:
$$f\left(\sum_{i=1}^n \lambda_i v_i\right) = \sum_{i=1}^n \lambda_i f(v_i)$$
Questa proprietà è centrale e verrà utilizzata frequentemente, in quanto mostra come l'applicazione lineare "rispetti" la struttura fondamentale dello spazio vettoriale.

## Esempi di Applicazioni Lineari e Non Lineari

### L'Applicazione Nulla
Dati due spazi vettoriali $V$ e $W$, la funzione $f: V \to W$ definita da $f(v) = 0_W$ per ogni $v \in V$, è un'applicazione lineare. È chiamata **applicazione nulla**.

*Verifica:*
1.  Additività: $f(u+v) = 0_W$. Inoltre, $f(u)+f(v) = 0_W + 0_W = 0_W$. Quindi $f(u+v) = f(u)+f(v)$.
2.  Omogeneità: $f(\lambda u) = 0_W$. Inoltre, $\lambda f(u) = \lambda \cdot 0_W = 0_W$. Quindi $f(\lambda u) = \lambda f(u)$.

### Un Esempio di Funzione non Lineare (con Termine Prodotto)
Si consideri la funzione $f: \mathbb{R}^2 \to \mathbb{R}^3$ definita da $f(x,y) = (x+y, x-y, xy)$. Questa funzione **non** è lineare. Il termine non lineare $x \cdot y$ viola l'additività. Per dimostrarlo, è sufficiente un controesempio. Siano $e_1=(1,0)$ e $e_2=(0,1)$:
- $f(e_1) = (1, 1, 0)$
- $f(e_2) = (1, -1, 0)$
- $f(e_1) + f(e_2) = (2, 0, 0)$
D'altra parte:
- $f(e_1 + e_2) = f(1,1) = (1+1, 1-1, 1 \cdot 1) = (2, 0, 1)$
Poiché $f(e_1+e_2) \neq f(e_1)+f(e_2)$, la funzione non è lineare.

### Un Esempio di Funzione non Lineare (con Termine Costante)
Si consideri la funzione $h: \mathbb{R}^2 \to \mathbb{R}^2$ definita da $h(x,y)=(2x, y-1)$. Questa funzione **non** è lineare perché non manda il vettore nullo in sé: $h(0,0) = (0, -1) \neq (0,0)$.

### Un Esempio di Applicazione Lineare da $\mathbb{R}^3$ a $\mathbb{R}^2$
Si consideri la funzione $g: \mathbb{R}^3 \to \mathbb{R}^2$ definita da $g(x,y,z) = (x+y+z, x-y-z)$. Questa è un'applicazione lineare. Per dimostrarlo, verifichiamo le due proprietà per vettori generici $u=(x_1, y_1, z_1)$ e $v=(x_2, y_2, z_2)$ in $\mathbb{R}^3$ e uno scalare $\lambda \in \mathbb{R}$.

1.  **Additività:**
    $$\begin{aligned} g(u+v) &= g(x_1+x_2, y_1+y_2, z_1+z_2) \\ &= ((x_1+x_2) + (y_1+y_2) + (z_1+z_2), (x_1+x_2) - (y_1+y_2) - (z_1+z_2)) \\ &= ((x_1+y_1+z_1) + (x_2+y_2+z_2), (x_1-y_1-z_1) + (x_2-y_2-z_2)) \\ &= (x_1+y_1+z_1, x_1-y_1-z_1) + (x_2+y_2+z_2, x_2-y_2-z_2) \\ &= g(u) + g(v) \end{aligned}$$
   
2.  **Omogeneità:**
    $$\begin{aligned} g(\lambda u) &= g(\lambda x_1, \lambda y_1, \lambda z_1) \\ &= (\lambda x_1 + \lambda y_1 + \lambda z_1, \lambda x_1 - \lambda y_1 - \lambda z_1) \\ &= (\lambda(x_1+y_1+z_1), \lambda(x_1-y_1-z_1)) \\ &= \lambda(x_1+y_1+z_1, x_1-y_1-z_1) \\ &= \lambda g(u) \end{aligned}$$
   
Entrambe le proprietà sono soddisfatte, quindi $g$ è un'applicazione lineare.

> [!TIP] Caratterizzazione delle Applicazioni Lineari tra $\mathbb{R}^n$ e $\mathbb{R}^m$
> Una funzione $f: \mathbb{R}^n \to \mathbb{R}^m$ definita da $f(x_1, \dots, x_n) = (f_1(x_1, \dots, x_n), \dots, f_m(x_1, \dots, x_n))$ è lineare se e solo se ogni componente $f_i$ è un **polinomio omogeneo di primo grado** nelle variabili $x_1, \dots, x_n$ (oppure la funzione nulla). Ciò significa che ogni $f_i$ deve essere della forma $a_{i1}x_1 + a_{i2}x_2 + \dots + a_{in}x_n$ per opportuni coefficienti reali $a_{ij}$. Non devono esserci termini costanti (come in $h(x,y)$) né termini di grado superiore (come in $f(x,y)$).

## Sottospazi Fondamentali: Nucleo e Immagine

Ad ogni applicazione lineare $f: V \to W$ sono associati due sottoinsiemi di fondamentale importanza: l'immagine e il nucleo.

- **Immagine ($\text{Im}(f)$ o $f(V)$)**: È l'insieme di tutti i vettori di $W$ che sono immagine di almeno un vettore di $V$. Formalmente:
  $$\text{Im}(f) = \{ w \in W \mid \exists v \in V \text{ tale che } f(v) = w \} = f(V)$$
  È un sottoinsieme del codominio $W$. Contiene sempre il vettore nullo $0_W$ (poiché $f(0_V)=0_W$).

- **Nucleo o Kernel ($\text{Ker}(f)$ o $f^{-1}(0_W)$)**: È l'insieme di tutti i vettori di $V$ la cui immagine tramite $f$ è il vettore nullo di $W$. Formalmente:
  $$\text{Ker}(f) = \{ v \in V \mid f(v) = 0_W \} = f^{-1}(0_W)$$
  È un sottoinsieme del dominio $V$. Contiene sempre il vettore nullo $0_V$ (poiché $f(0_V)=0_W$).

**Teorema:** Sia $f: V \to W$ un'applicazione lineare. Allora $\text{Im}(f)$ è un [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni|sottospazio vettoriale]] di $W$ e $\text{Ker}(f)$ è un sottospazio vettoriale di $V$.

*Dimostrazione (schizzo):* Utilizziamo la [[06 - Spazi Vettoriali, Sottospazi e Loro Operazioni#^a6327e|caratterizzazione dei sottospazi]].
- **Per il Nucleo ($\text{Ker}(f)$):** Siano $u, v \in \text{Ker}(f)$ (cioè $f(u)=0_W$ e $f(v)=0_W$) e $\lambda, \mu \in \mathbb{R}$. Dobbiamo dimostrare che $\lambda u + \mu v \in \text{Ker}(f)$.
  $$f(\lambda u + \mu v) = f(\lambda u) + f(\mu v) \quad (\text{per additività di } f)$$
  $$= \lambda f(u) + \mu f(v) \quad (\text{per omogeneità di } f)$$
  $$= \lambda \cdot 0_W + \mu \cdot 0_W = 0_W + 0_W = 0_W$$
  Poiché l'immagine della combinazione lineare è $0_W$, essa appartiene a $\text{Ker}(f)$.
- **Per l'Immagine ($\text{Im}(f)$):** Siano $w_1, w_2 \in \text{Im}(f)$ e $\lambda, \mu \in \mathbb{R}$. Per definizione di immagine, esistono $v_1, v_2 \in V$ tali che $f(v_1)=w_1$ e $f(v_2)=w_2$. Dobbiamo dimostrare che $\lambda w_1 + \mu w_2 \in \text{Im}(f)$.
  $$\lambda w_1 + \mu w_2 = \lambda f(v_1) + \mu f(v_2)$$
  $$= f(\lambda v_1) + f(\mu v_2) \quad (\text{per omogeneità di } f)$$
  $$= f(\lambda v_1 + \mu v_2) \quad (\text{per additività di } f)$$
  Poiché $V$ è uno spazio vettoriale, $\lambda v_1 + \mu v_2 \in V$. Abbiamo trovato un vettore nel dominio la cui immagine è $\lambda w_1 + \mu w_2$. Quindi, $\lambda w_1 + \mu w_2 \in \text{Im}(f)$.

**Corollario (Generatori dell'Immagine):** Se $V$ è [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Sistemi di Generatori|generato]] da un insieme di vettori $\{v_1, \dots, v_n\}$, allora $\text{Im}(f)$ è generata dalle immagini di questi vettori, cioè $\text{Im}(f) = \text{span}\{f(v_1), \dots, f(v_n)\}$.

> [!warning] Attenzione
> Se $\{v_1, \dots, v_n\}$ è una [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Base|base]] di $V$, l'insieme delle immagini $\{f(v_1), \dots, f(v_n)\}$ genera $\text{Im}(f)$, ma **non** è necessariamente una base per $\text{Im}(f)$, in quanto potrebbe essere linearmente dipendente.

## Il Teorema del Rango (o della Dimensione o dell'Omomorfismo)

Poiché nucleo e immagine sono sottospazi vettoriali, possiamo considerare la loro [[07 - Indipendenza Lineare, Basi e Dimensione Vettoriale#Definizione di Dimensione|dimensione]]. Queste dimensioni sono così importanti da avere nomi specifici.

- **Nullità ($\text{nullity}(f)$)**: È la dimensione del nucleo di $f$.
  $$\text{nullity}(f) = \dim(\text{Ker}(f))$$
- **Rango ($\text{rank}(f)$)**: È la dimensione dell'immagine di $f$.
  $$\text{rank}(f) = \dim(\text{Im}(f))$$

Queste due quantità sono legate da un teorema fondamentale, noto anche come **Teorema della Nullità più Rango**.

**Teorema del Rango (o della Dimensione):** Sia $f: V \to W$ un'applicazione lineare con $V$ spazio vettoriale di dimensione finita. Allora:
$$\text{rank}(f) + \text{nullity}(f) = \dim(V)$$
Ovvero:
$$\dim(\text{Im}(f)) + \dim(\text{Ker}(f)) = \dim(V)$$
 La somma della dimensione dell'immagine e della dimensione del nucleo è uguale alla dimensione dello spazio di partenza (il dominio).

> [!NOTE] Analogia con il Teorema Rango-Nullità per Matrici
> Questo teorema stabilisce una forte analogia con il [[09 - Rappresentazioni e Operazioni con Sottospazi di R alla n#Teorema Rango-Nullità|Teorema Rango-Nullità]] per le matrici ($A \in M_{m,n}$), che afferma $\text{rank}(A) + \text{nullity}(A) = n$ (numero di colonne). Questa corrispondenza non è casuale: come vedremo, ad ogni applicazione lineare tra spazi di dimensione finita può essere associata una matrice.

## Proprietà delle Applicazioni Lineari: Iniettività, Suriettività, Biettività

Le definizioni standard per le funzioni si applicano al contesto degli omomorfismi. Un'applicazione lineare $f: V \to W$ è:
- **Iniettiva** (o **monomorfismo**): Se a elementi distinti del dominio corrispondono immagini distinte. Equivalentemente, $f(v_1) = f(v_2) \implies v_1 = v_2$. Vedi [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Iniettiva (o Iniezione)|Definizione di Funzione Iniettiva]].
- **Suriettiva** (o **epimorfismo**): Se la sua immagine coincide con il codominio, cioè $\text{Im}(f) = W$. Ogni elemento di $W$ è immagine di almeno un elemento di $V$. Vedi [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Suriettiva (o Suriezione)|Definizione di Funzione Suriettiva]].
- **Biettiva** (o **isomorfismo**): Se è sia iniettiva che suriettiva. Vedi [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Biettiva (o Biiezione)|Definizione di Funzione Biettiva]].

Un'applicazione lineare biettiva è anche [[01 - Fondamenti di Teoria degli Insiemi e Funzioni#Funzione Inversa e Funzione Composta|invertibile]], ovvero esiste un'applicazione (che si dimostra essere anch'essa lineare) $f^{-1}: W \to V$ tale che $f^{-1} \circ f = \text{id}_V$ (l'identità su $V$) e $f \circ f^{-1} = \text{id}_W$ (l'identità su $W$). $f^{-1}$ è chiamata l'**inversa** di $f$.

### Caratterizzazione dell'Iniettività tramite il Nucleo

Una proprietà fondamentale lega l'iniettività al nucleo dell'applicazione lineare.

**Proposizione:** Un'applicazione lineare $f: V \to W$ è **iniettiva se e solo se** il suo nucleo contiene solo il vettore nullo, ovvero $\text{Ker}(f) = \{0_V\}$.

*Dimostrazione:*
- ($\implies$) Assumiamo $f$ iniettiva. Sappiamo che $f(0_V)=0_W$, quindi $0_V \in \text{Ker}(f)$. Sia $v \in \text{Ker}(f)$ un vettore qualsiasi. Allora $f(v)=0_W$. Poiché $f(0_V)=0_W$, abbiamo $f(v)=f(0_V)$. Essendo $f$ iniettiva, questo implica $v=0_V$. Dunque, l'unico elemento nel nucleo è il vettore nullo.
- ($\impliedby$) Assumiamo $\text{Ker}(f) = \{0_V\}$. Siano $v_1, v_2 \in V$ tali che $f(v_1) = f(v_2)$. Allora $f(v_1) - f(v_2) = 0_W$. Per la linearità di $f$, $f(v_1 - v_2) = 0_W$. Questo significa che il vettore $v_1 - v_2$ appartiene al nucleo di $f$. Ma per ipotesi, il nucleo contiene solo il vettore nullo, quindi $v_1 - v_2 = 0_V$, da cui $v_1 = v_2$. Questo dimostra che $f$ è iniettiva.

---

## Strategie Operative dagli Esercizi

La teoria definisce i concetti, ma gli esercizi richiedono strategie specifiche. Ecco alcune "ricette" pratiche emerse dalla risoluzione dei problemi.

### 1. Ricetta: Analisi con Parametri (Esercizi 5, 6)

**Obiettivo:** Discutere Iniettività e Suriettività di un'applicazione $L_A$ al variare di un parametro ($t$ o $h$) nella matrice $A$.

La strategia dipende dalla forma della matrice $A$ (di tipo $m \times n$):

> [!TIP] Caso 1: Matrice Quadrata ($m = n$)
> Questo è il caso più semplice. L'applicazione $L_A: V \to V$ è un endomorfismo.
> 1.  Le proprietà di [[10 - Applicazioni Lineari, Nucleo, Immagine e Rango#Proprietà delle Applicazioni Lineari|Iniettività, Suriettività e Biettività (Isomorfismo)]] **coincidono**.
> 2.  L'applicazione ha queste proprietà se e solo se la matrice è [[03 - Rango, Invertibilità delle Matrici e Permutazioni|invertibile]].
> 3.  **Azione:** Calcola il **determinante** $\det(A)$ in funzione del parametro.
> 4.  **Discussione:**
>     * Se $\det(A) \neq 0$: (il rango è massimo) $\implies$ $L_A$ è **Iniettiva, Suriettiva e un Isomorfismo**.
>     * Se $\det(A) = 0$: (il rango è < n) $\implies$ $L_A$ **non è né Iniettiva né Suriettiva**.

> [!TIP] Caso 2: Matrice Rettangolare ($m \neq n$)
> L'applicazione $L_A$ non può **mai** essere un isomorfismo.
> 1.  **Azione:** Calcola il **rango** $\text{rank}(A)$ in funzione del parametro (solitamente usando il metodo dei minori o Gauss).
> 2.  **Discussione (Iniettività):**
>     * $L_A$ è Iniettiva $\iff \dim(\text{Ker}) = 0 \iff \text{rank}(A) = n$ (numero di colonne).
>     * Se $n > m$ (es. $A: \mathbb{R}^3 \to \mathbb{R}^2$), è **impossibile** che sia iniettiva.
> 3.  **Discussione (Suriettività):**
>     * $L_A$ è Suriettiva $\iff \dim(\text{Im}) = m \iff \text{rank}(A) = m$ (numero di righe).
>     * Se $m > n$ (es. $A: \mathbb{R}^2 \to \mathbb{R}^3$), è **impossibile** che sia suriettiva.

### 2. Ricetta: Immagine di un Sottospazio (Esercizio 7)

**Obiettivo:** Trovare la base e la dimensione di $L(U)$, dove $U$ è un *sottospazio* del dominio (es. $U$ è un piano in $\mathbb{R}^4$).

**Strategia:**
1.  Trova una base per il sottospazio $U$. (Nell'Esercizio 7, questo si fa risolvendo il sistema omogeneo che definisce $U$). Sia $\mathcal{B}_U = \{v_1, \dots, v_k\}$.
2.  Applica l'omomorfismo $L$ a *ciascun vettore* della base $\mathcal{B}_U$. (Nell'Esercizio 7, si calcolano $w_1 = A \cdot v_1$ e $w_2 = A \cdot v_2$).
3.  Il sottospazio immagine $L(U)$ è l'insieme generato da questi nuovi vettori:
    $$L(U) = \text{span}\{L(v_1), \dots, L(v_k)\}$$
4.  Per trovare la **base di $L(U)$**, basta estrarre una base dall'insieme di generatori $\{L(v_1), \dots, L(v_k)\}$ (verificando la loro indipendenza lineare, ad esempio calcolando il rango della matrice che li ha come colonne).

### 3. Ricetta: Gestire Spazi "Astratti" (Polinomi) (Esercizi 11, 12)

**Obiettivo:** Risolvere problemi su spazi come $\mathbb{R}[t]_{\le n}$ (spazio dei polinomi).

**Strategia:** Non farsi spaventare. Questi spazi sono [[11 - Applicazioni Lineari, Basi e Spazi Vettoriali Isomorfi|isomorfi]] a $\mathbb{R}^k$. Il trucco è **tradurli** in vettori di coordinate.

1.  **Identifica la Dimensione:** Ricorda che $\dim(\mathbb{R}[t]_{\le n}) = n + 1$ (perché c'è il termine $t^0 = 1$).
    * $\mathbb{R}[t]_{\le 1} \implies \dim = 2$.
    * $\mathbb{R}[t]_{\le 2} \implies \dim = 3$.
    * $\mathbb{R}[t]_{\le 3} \implies \dim = 4$.
2.  **Scegli una Base:** Solitamente la [[08 - Basi, Dimensione e Rappresentazione di Spazi Vettoriali|base standard (monomiale)]]:
    * Per $\mathbb{R}[t]_{\le 2}$: $\mathcal{B} = \{1, t, t^2\}$
3.  **Traduci:** Ogni polinomio diventa un vettore di coordinate:
    * $p(t) = 5 - 2t + 4t^2 \implies [p]_{\mathcal{B}} = (5, -2, 4) \in \mathbb{R}^3$.
4.  **Risolvi:** Un'applicazione $L: \mathbb{R}[t]_{\le 2} \to \mathbb{R}[t]_{\le 1}$ è (nascostamente) un'applicazione $L_A: \mathbb{R}^3 \to \mathbb{R}^2$. Puoi trovare la [[12- Rappresentazione Matriciale degli Omomorfismi e Applicazioni|matrice associata]] $A$ (di tipo $2 \times 3$) e usare tutti gli strumenti standard (rango, ker, col) per analizzare $L$.