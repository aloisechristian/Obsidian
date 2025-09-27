# Rappresentazione dei Numeri Reali e Standard IEEE 754

Questa lezione conclude l'analisi sulla rappresentazione dei numeri, affrontando il tema dei numeri reali. A differenza degli insiemi numerici come $\mathbb{N}$ o $\mathbb{Z}$, l'insieme dei [[03 - Insiemi Numerici, Completezza e Estremo Superiore|numeri reali $\mathbb{R}$]] è **continuo**. Ciò significa che tra due qualsiasi numeri reali ne esistono infiniti altri. Questa proprietà, formalizzata dall'[[02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|assioma di completezza]], pone una sfida fondamentale per la rappresentazione dei reali in un calcolatore, che per sua natura opera con una quantità finita di memoria e quindi su insiemi di dati discreti. La soluzione adottata è una rappresentazione approssimata nota come **virgola mobile** (in inglese, *floating point*).

## Discretizzazione e Approssimazione

Per rappresentare l'insieme infinito e continuo dei numeri reali, è necessario operare una **discretizzazione**. L'intervallo continuo dei numeri reali viene mappato su un sottoinsieme discreto e finito di valori rappresentabili.

Questo implica che qualsiasi numero reale $x$ che non coincida esattamente con un punto rappresentabile viene **approssimato** al valore discreto più vicino. Questo processo introduce inevitabilmente un **errore di approssimazione**.

Una caratteristica fondamentale di questa rappresentazione è che la distanza tra i punti rappresentabili non è costante: gli intervalli tra valori adiacenti diventano **sempre più ampi al crescere dell'esponente** e **sempre più piccoli al diminuire dell'esponente**. Questo significa che la precisione è maggiore per numeri vicini allo zero e minore per numeri molto grandi.

### Errore Assoluto e Relativo

L'errore di approssimazione può essere quantificato in due modi:

1.  **Errore Assoluto**: È la differenza in valore assoluto tra il numero reale originale $x$ e la sua rappresentazione discreta $X$.
    $$ \text{Errore Assoluto} = |x - X| $$
2.  **Errore Relativo**: È l'errore assoluto normalizzato rispetto al valore del numero reale stesso, fornendo una misura della grandezza dell'errore in proporzione al numero.
    $$ \text{Errore Relativo} = \frac{|x - X|}{|x|} $$

La disciplina del **calcolo numerico** si occupa di sviluppare e analizzare algoritmi che, pur operando con rappresentazioni discrete e finite, minimizzano l'impatto di tali errori di approssimazione sui risultati finali.

## La Notazione in Virgola Mobile

La rappresentazione in virgola mobile si basa sulla notazione scientifica. Un numero reale $r$ viene espresso nella forma:

$$ r = \pm M \times B^E $$

Dove:
- **$M$ (Mantissa)**: È un numero frazionario che definisce le cifre significative del numero. Il numero di cifre utilizzate per la mantissa determina la **precisione** della rappresentazione.
- **$B$ (Base)**: È la base della numerazione (es. 10 per il sistema decimale, 2 per quello binario). Nei calcolatori, la base è implicitamente 2.
- **$E$ (Esponente o Caratteristica)**: È un intero che indica l'ordine di grandezza del numero, ovvero la posizione della virgola. Il range di valori che l'esponente può assumere determina l'**ampiezza dell'intervallo** dei numeri rappresentabili.

### Mantissa Normalizzata

Un numero può avere infinite rappresentazioni in virgola mobile (es. $48000 = 48 \times 10^3 = 4.8 \times 10^4$). Per garantire unicità, si adotta la **forma normalizzata**, che impone una regola sulla mantissa. La mantissa, in valore assoluto, deve essere compresa tra 1 (incluso) e la base (esclusa):

$$ 1 \le |M| < B $$

Nel sistema decimale (base 10), la mantissa avrà la forma `d.ffff...`, con $d \in \{1, 2, ..., 9\}$. Nel sistema binario (base 2), la mantissa avrà sempre la forma `1.bbbb...`, poiché l'unica cifra diversa da zero prima della virgola non può che essere 1.

## Lo Standard IEEE 754

^ae91d1

Per garantire l'interoperabilità tra sistemi di calcolo diversi, nel **1985** l'**Institute of Electrical and Electronic Engineers (IEEE)** ha definito lo standard 754 per l'aritmetica in virgola mobile. Questo standard definisce formati di rappresentazione e regole per le operazioni.

I formati principali sono:
- **Precisione Singola (Single Precision)**: 32 bit.
- **Doppia Precisione (Double Precision)**: 64 bit.
- **Precisione Estesa (Extended Precision)**: 80 bit.

La rappresentazione di un numero reale $r$ si basa sulla formula:

$$ r = (-1)^S \times M \times 2^E $$

Le quantità da memorizzare sono tre: il segno $S$, la mantissa $M$ e l'esponente $E$.

### Formato a Precisione Singola (32 bit)

I 32 bit sono così suddivisi:
- **Bit di Segno (S)**: 1 bit (il più significativo, $b_{31}$). $0$ per positivo, $1$ per negativo.
- **Esponente (E)**: 8 bit ($b_{30}...b_{23}$). Rappresentato in **[[Fondamenti di Informatica/Rappresentazione Binaria dei Numeri Interi Relativi#5. Rappresentazione per Eccesso K (o con Bias)|eccesso 127]]**.
- **Mantissa (M)**: 23 bit ($b_{22}...b_0$). Rappresenta la parte frazionaria della mantissa normalizzata.

La formula per ricostruire il valore è:

$$ V = (-1)^S \times (1.M) \times 2^{(E_{dec} - 127)} $$

**Dettagli dei componenti:**
- **Segno**: Un singolo bit.
- **Esponente**: Gli 8 bit permettono di rappresentare il range decimale $[0, 255]$. Utilizzando la notazione in eccesso 127, l'esponente reale $e$ si ottiene da quello memorizzato $E$ con la formula $e = E - 127$. I valori $E=0$ e $E=255$ sono riservati a casi speciali, quindi l'intervallo per i numeri normalizzati è $E \in [1, 254]$, che corrisponde a un esponente reale $e \in [-126, 127]$.
- **Mantissa**: Poiché in binario la mantissa normalizzata ha sempre la forma `1.frazionario`, si memorizzano solo i 23 bit della parte frazionaria. L'`1.` iniziale è un **bit implicito** o **nascosto**, che viene reintrodotto durante i calcoli per massimizzare la precisione. La precisione è di circa 7 cifre decimali.

### Formato a Doppia Precisione (64 bit)

I 64 bit sono così suddivisi:
- **Bit di Segno (S)**: 1 bit ($b_{63}$).
- **Esponente (E)**: 11 bit ($b_{62}...b_{52}$). Rappresentato in **eccesso 1023**.
- **Mantissa (M)**: 52 bit ($b_{51}...b_0$).

La formula per ricostruire il valore è:

$$ V = (-1)^S \times (1.M) \times 2^{(E_{dec} - 1023)} $$

L'intervallo per l'esponente reale $e$ dei numeri normalizzati è `[-1022, 1023]`. La precisione è di circa 15 cifre decimali.

### Valori Speciali (Precisione Singola)

Lo standard definisce configurazioni specifiche di esponente e mantissa per rappresentare valori non numerici o eccezionali:

| Categoria | Esponente (E) | Mantissa (M) | Descrizione |
|:---|:---:|:---:|---|
| Zeri | 0 | 0 | Rappresenta $+0$ e $-0$. |
| Numeri Denormalizzati | 0 | $\neq 0$ | Numeri molto piccoli, vicini allo zero (perdono il bit implicito). |
| Numeri Normalizzati | $1 \le E \le 254$ | Qualsiasi | I numeri reali standard. |
| Infiniti | 255 | 0 | Rappresenta $+\infty$ e $-\infty$ (es. risultato di divisione per zero). |
| Not a Number (NaN) | 255 | $\neq 0$ | Risultato di operazioni invalide (es. $0/0$, $\sqrt{-1}$). |

### Overflow e Underflow

- **Overflow**: Si verifica quando il risultato di un'operazione è troppo grande in valore assoluto per essere rappresentato nell'intervallo consentito. Ad esempio, un numero maggiore del massimo valore rappresentabile (es. $\approx 10^{38}$ per la precisione singola).
- **Underflow**: Si verifica quando un numero positivo è troppo piccolo (vicino a zero) per essere rappresentato come numero normalizzato. Questi valori vengono "confusi con lo zero" o gestiti tramite numeri denormalizzati per mantenere una certa precisione.

## Aritmetica e Errori di Approssimazione

Le operazioni aritmetiche in virgola mobile sono più complesse di quelle intere e possono introdurre o propagare errori.
- **Somma e Sottrazione**: Richiedono l'**allineamento degli esponenti**. Per sommare due numeri, quello con esponente minore deve essere riscritto (denormalizzato) per eguagliare l'esponente maggiore. Questo processo può causare la perdita di cifre significative meno importanti del numero più piccolo.
- **Prodotto e Divisione**: Sono più semplici. Le mantisse vengono moltiplicate/divise e gli esponenti sommati/sottratti.
- **Cancellazione numerica**: La sottrazione di due numeri quasi uguali può portare a un risultato con molte meno cifre significative corrette rispetto agli operandi, amplificando l'errore relativo.

## Esempi di Conversione

### Esempio 1: Da Binario a Decimale

Convertire il numero a 32 bit: `1 10000001 01000000000000000000000`

1.  **Segno (S)**: Il primo bit è `1`, quindi il numero è **negativo**.
2.  **Esponente (E)**: I successivi 8 bit sono `10000001`. Convertito in decimale: $10000001_2 = 128 + 1 = 129$. L'esponente reale è $129 - 127 = 2$. 
3.  **Mantissa (M)**: I restanti 23 bit sono `0100...0`. La parte frazionaria è `.01`. Ricostruendo la mantissa con il bit implicito, otteniamo $1.01_2$. 
    Convertiamo in decimale: $1.01_2 = 1 \times 2^0 + 0 \times 2^{-1} + 1 \times 2^{-2} = 1 + 0.25 = 1.25$. 
4.  **Numero Finale**: Mettiamo insieme i pezzi:
    $$ V = (-1)^1 \times 1.25 \times 2^2 = -1.25 \times 4 = -5 $$

### Esempio 2: Da Decimale a Binario

Convertire il numero decimale `8.5` in formato IEEE 754 a precisione singola.

1.  **Segno (S)**: Il numero è positivo, quindi il bit di segno è **0**.
2.  **[[Fondamenti di Informatica/Sistemi di Numerazione Posizionale e Aritmetica Binaria#Conversione da Decimale a Binario|Conversione in Binario]]**: 
    - Parte intera: $8_{10} = 1000_2$.
    - Parte frazionaria: $0.5_{10} = \frac{1}{2} = .1_2$.
    - Numero binario completo: $1000.1_2$.
3.  **Normalizzazione**: Spostiamo la virgola per ottenere la forma `1.xxxx...`: 
    $1000.1_2 = 1.0001 \times 2^3$. 
4.  **Esponente (E)**: L'esponente reale è 3. Lo convertiamo in eccesso 127: $E = 3 + 127 = 130_{10}$. 
    Convertiamo in binario su 8 bit: $130_{10} = 128 + 2 = 10000010_2$. 
5.  **Mantissa (M)**: Dalla forma normalizzata $1.0001$, la parte frazionaria da memorizzare è `0001`. Va rappresentata su 23 bit, aggiungendo zeri a destra: `00010000000000000000000`.
6.  **Numero Finale (32 bit)**: Assembliamo i tre campi:
    - S: `0`
    - E: `10000010`
    - M: `00010000000000000000000`

    Il numero completo è: `0 10000010 00010000000000000000000`.