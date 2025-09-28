# Introduzione alla Rappresentazione dei Numeri Relativi

La discussione precedente si è concentrata sulla rappresentazione dei numeri naturali (interi non negativi) nel [[02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria#Rappresentazione Polinomiale di un Numero|sistema binario]]. La presente lezione estende tale analisi ai numeri interi relativi, che includono valori sia positivi sia negativi. Per codificare l'informazione aggiuntiva del segno, è necessario adottare schemi di rappresentazione specifici. Verranno analizzate tre principali metodologie: segno e modulo, complemento a uno e a due, e rappresentazione per eccesso K. L'obiettivo è comprendere il funzionamento, i vantaggi e gli svantaggi di ciascuna codifica, con un'attenzione particolare alle implicazioni per le operazioni aritmetiche.

## 1. Rappresentazione in Segno e Modulo

Questa rappresentazione è la più intuitiva per estendere la codifica binaria ai numeri relativi, poiché si ispira direttamente al modo in cui rappresentiamo i numeri con segno nel sistema decimale.

### Principio di Funzionamento
L'idea fondamentale è di dedicare un bit specifico per rappresentare il segno del numero, mentre i restanti bit ne codificano il valore assoluto (o modulo).

- **Bit di Segno**: Si utilizza il bit più significativo (Most Significant Bit, MSB). Per convenzione:
    - `0` indica un segno positivo (+).
    - `1` indica un segno negativo (-).
- **Modulo**: I restanti $L-1$ bit, dove $L$ è la lunghezza totale della parola, rappresentano il modulo del numero in binario puro.

Per decodificare un numero in questa rappresentazione, si esamina l'MSB per determinare il segno e si applica l'algoritmo della somma pesata ai restanti $L-1$ bit per calcolare il modulo. 

**Esempio (L=8 bit):**
- Il numero `01001001` ha MSB=0 (positivo). Il modulo è `1001001`, che corrisponde a 73. Il valore è quindi $+73$.
- Il numero `10101010` ha MSB=1 (negativo). Il modulo è `0101010`, che corrisponde a 42. Il valore è quindi $-42$.

### Intervallo di Rappresentazione e il Problema del Doppio Zero
Dato un numero di $L$ bit, uno è riservato al segno e $L-1$ al modulo. Con $L-1$ bit si possono rappresentare $2^{L-1}$ valori distinti per il modulo, che vanno da 0 a $2^{L-1}-1$. L'intervallo complessivo dei numeri rappresentabili è quindi:

$$ [-(2^{L-1} - 1), +(2^{L-1} - 1)] $$

Una delle principali criticità di questa rappresentazione è la **doppia rappresentazione dello zero**. Esistono due configurazioni binarie per il valore zero:
- `+0`: Un bit di segno `0` seguito da $L-1$ bit a zero (es. `00000000` con $L=8$).
- `-0`: Un bit di segno `1` seguito da $L-1$ bit a zero (es. `10000000` con $L=8$).

Questa ridondanza consuma una delle $2^L$ possibili configurazioni binarie e complica la progettazione degli algoritmi aritmetici.

### Complessità delle Operazioni Aritmetiche
Le operazioni di somma e sottrazione in segno e modulo non sono dirette. L'algoritmo deve:
1.  **Confrontare i bit di segno** degli operandi.
2.  Se i segni sono concordi, sommare i moduli e mantenere il segno comune.
3.  Se i segni sono discordi, confrontare i moduli, sottrarre il modulo minore dal maggiore e assegnare al risultato il segno dell'operando con modulo maggiore.

Questa logica basata su casi rende i circuiti aritmetici più complessi rispetto ad altre rappresentazioni.

## 2. Rappresentazione in Complemento alla Base

Per superare le limitazioni della rappresentazione in segno e modulo, è stata introdotta la rappresentazione in complemento alla base, che è oggi il metodo più diffuso. Essa permette di utilizzare un unico circuito hardware per eseguire sia addizioni che sottrazioni, semplificando notevolmente l'architettura dei processori.

### Definizioni Formali
Sia $N$ un numero rappresentato in base $B$ con $k$ cifre.

- **Complemento alla Base (o Complemento a B)**: È definito come:
  $$ C_B(N) = B^k - |N| $$
- **Complemento alla Base Diminuita (o Complemento a B-1)**: È definito come:
  $$ C_{B-1}(N) = B^k - 1 - |N| $$

Da queste definizioni segue la relazione: $C_B(N) = C_{B-1}(N) + 1$.

### Specializzazione al Sistema Binario: Complemento a 2 e a 1
Nel sistema binario, la base è $B=2$. Le definizioni si specializzano come segue:

- **Complemento a 2 ($C_2$)**: Corrisponde al complemento alla base. Con $L$ bit, la formula è:
  $$ C_2(N) = 2^L - |N| $$
- **Complemento a 1 ($C_1$)**: Corrisponde al complemento alla base diminuita:
  $$ C_1(N) = 2^L - 1 - |N| $$

Esistono metodi operativi rapidi per calcolarli:
- **Per ottenere il Complemento a 1**: Si invertono tutti i bit del numero (da 0 a 1 e viceversa).
- **Per ottenere il Complemento a 2**: Si calcola il complemento a 1 e si somma 1 al risultato.

## 3. Rappresentazione in Complemento a 1

### Codifica e Intervallo di Rappresentazione
In questa rappresentazione, dato un numero $x$ da codificare su $L$ bit:
- Se $x$ è positivo o nullo, la sua codifica $y$ è la rappresentazione in binario puro di $x$.
- Se $x$ è negativo, la sua codifica $y$ è il complemento a 1 del suo modulo $|x|$.

L'intervallo di numeri rappresentabili è **simmetrico**:

$$ [-(2^{L-1} - 1), +(2^{L-1} - 1)] $$

Anche in questo caso, il bit più significativo funge da indicatore di segno (0 per positivi, 1 per negativi).

### Caratteristiche e Svantaggi
- **Facilità di codifica dei negativi**: Si ottiene semplicemente invertendo i bit del corrispondente numero positivo.
- **Doppia rappresentazione dello zero**: Similmente alla rappresentazione in segno e modulo, lo zero ha due codifiche:
    - `+0`: `00...0`
    - `-0`: `11...1` (il complemento a 1 di `00...0`)
- **Complicazioni aritmetiche**: Le somme possono richiedere una correzione del risultato (aggiunta di un'unità) se si verifica un riporto oltre il bit più significativo.

### Conversione da Complemento a 1 a Decimale
Data una stringa binaria $y$ di $L$ bit:
1.  **Si osserva l'MSB**: Se è `0`, il numero è positivo. Si converte l'intera stringa in decimale con la somma pesata.
2.  Se l'MSB è `1`, il numero è negativo. Per trovare il modulo, si calcola il complemento a 1 della stringa (invertendo tutti i bit) e si converte il risultato in decimale. Al valore ottenuto si antepone il segno meno.

**Esercizio Svolto:** Convertire il numero `-43` in complemento a 1 su 8 bit.
1.  Verifica dell'intervallo ($L=8$): L'intervallo è $[-(2^7-1), 2^7-1] = [-127, 127]$. Il numero `-43` è rappresentabile.
2.  Si converte il modulo 43 in binario: $43_{10} = 101011_2$.
3.  Si estende a 8 bit: `00101011`.
4.  Si calcola il complemento a 1 invertendo i bit: `11010100`.

## 4. Rappresentazione in Complemento a 2

È la rappresentazione standard utilizzata nei calcolatori moderni per i numeri interi.

### Codifica e Intervallo di Rappresentazione
- Se $x$ è positivo o nullo, la sua codifica $y$ è la rappresentazione in binario puro.
- Se $x$ è negativo, la sua codifica $y$ è il complemento a 2 del suo modulo $|x|$.

L'intervallo di rappresentazione è **asimmetrico**:

$$ [-2^{L-1}, +(2^{L-1} - 1)] $$

Con questa codifica è possibile rappresentare un numero negativo in più rispetto ai positivi. L'MSB indica ancora il segno.

### Vantaggi e Metodi di Calcolo
- **Unica rappresentazione dello zero**: La configurazione `00...0` rappresenta lo zero. Il complemento a 2 di zero è ancora zero (ignorando il riporto), eliminando l'ambiguità.
- **Aritmetica semplificata**: La somma tra due numeri in complemento a 2 si esegue come una normale somma binaria. Questo permette di usare lo stesso circuito sommatore sia per numeri positivi che negativi e di trattare la sottrazione $A-B$ come una somma $A+(-B)$.

**Esempio:** Rappresentare `-9` in complemento a 2 su 8 bit.
- **Metodo 1 (formula)**: $C_2(9) = 2^8 - 9 = 256 - 9 = 247_{10}$. Convertendo 247 in binario si ottiene `11110111`.
- **Metodo 2 (inversione + 1)**:
    1. Modulo 9 su 8 bit: `00001001`.
    2. Complemento a 1 (inversione): `11110110`.
    3. Somma 1: `11110111`.

### Conversione da Complemento a 2 a Decimale
Esistono due metodi principali per convertire una stringa binaria negativa in C2:

1.  **Metodo della Somma Pesata con MSB Negativo**: Si tratta la stringa come un numero in [[02 - Sistemi di Numerazione Posizionale e Aritmetica Binaria#Rappresentazione Polinomiale di un Numero|notazione posizionale]], ma si assegna al bit più significativo (MSB) un peso **negativo**. Per una stringa $c_{L-1}c_{L-2}...c_0$:
    $$ \text{Valore} = -c_{L-1} \cdot 2^{L-1} + \sum_{j=0}^{L-2} c_j \cdot 2^j $$
    **Esempio:** Convertire `101111` ($L=6$).
    $$ \text{Valore} = -1 \cdot 2^5 + 0 \cdot 2^4 + 1 \cdot 2^3 + 1 \cdot 2^2 + 1 \cdot 2^1 + 1 \cdot 2^0 = -32 + 8 + 4 + 2 + 1 = -17 $$

2.  **Metodo Inverso (Complemento + 1)**: Si applica l'algoritmo di complementazione a 2 alla stringa stessa per trovarne il modulo.
    **Esempio:** Convertire `101111`.
    1. La stringa è `101111`.
    2. Si calcola il complemento a 1 (inversione): `010000`.
    3. Si somma 1: `010001`.
    4. Si converte il risultato in decimale: $(010001)_2 = 17$.
    5. Poiché la stringa di partenza era negativa (MSB=1), il valore è $-17$.

### Gestione dell'Overflow nel Complemento a 2
Si verifica una condizione di **overflow** quando il risultato di un'operazione eccede l'intervallo rappresentabile. Nell'aritmetica in complemento a 2:
- La somma tra due numeri con **segno diverso** non può mai generare overflow.
- L'overflow può verificarsi solo sommando due numeri con **segno concorde** (entrambi positivi o entrambi negativi).

La condizione di overflow è facilmente rilevabile: **si ha overflow se e solo se il segno del risultato è discorde dal segno degli operandi**.

**Esempio (L=4, intervallo [-8, 7]):**
- **Overflow positivo**: $7+2 \rightarrow (+9)$. In binario: `0111` + `0010` = `1001`. Il risultato `1001` ha MSB=1 (negativo), che è discorde dal segno positivo degli addendi. Il valore decodificato sarebbe `-7`, errato.
- **Overflow negativo**: $(-7)+(-2) \rightarrow (-9)$. In binario: `1001` + `1110` = `10111`. Ignorando il riporto, il risultato a 4 bit è `0111`. Ha MSB=0 (positivo), discorde dal segno negativo degli addendi. Il valore decodificato sarebbe `+7`, errato.

## 5. Rappresentazione per Eccesso K (o con Bias)

Questa rappresentazione è meno comune per l'aritmetica intera generica, ma trova un'applicazione cruciale nella rappresentazione dell'esponente nei numeri in [[Rappresentazione dei Numeri Reali in Virgola Mobile#^ae91d1|virgola mobile (standard IEEE 754)]].

### Principio di Funzionamento
Un numero intero $x$ viene rappresentato dalla codifica in binario puro di un valore traslato $y = x+k$, dove $k$ è una costante intera positiva chiamata **eccesso** o **bias**.

$$ y = x + k $$

Una conseguenza importante è che **il bit più significativo non indica direttamente il segno** del numero $x$.

### Intervallo di Rappresentazione
L'intervallo dei numeri $x$ rappresentabili dipende dal valore di $k$. Poiché $y$ (la codifica) varia nell'intervallo $[0, 2^L-1]$, l'intervallo di $x = y-k$ è:

$$ [-k, 2^L - k - 1] $$

### Esempi e Relazione con il Complemento a 2
Un caso di particolare interesse si ha quando l'eccesso è $k = 2^{L-1}$.
- L'intervallo diventa: $[-2^{L-1}, 2^L - 2^{L-1} - 1] = [-2^{L-1}, 2^{L-1}-1]$, identico a quello del complemento a 2.
- **Esiste una relazione semplice: la rappresentazione in eccesso $2^{L-1}$ di un numero è identica alla sua rappresentazione in complemento a 2, ma con il bit di segno invertito**.

## 6. Tabella Comparativa delle Rappresentazioni (L=4 bit)

Per riassumere, ecco un confronto delle diverse codifiche utilizzando 4 bit. L'intervallo per Segno/Modulo e C1 è `[-3, 3]`, mentre per C2 è `[-4, 3]`.

| Valore Decimale | Segno e Modulo | Complemento a 1 | Complemento a 2 |
|:---------------:|:--------------:|:---------------:|:---------------:|
|        +3       |      `0011`      |      `0011`       |      `0011`       |
|        +2       |      `0010`      |      `0010`       |      `0010`       |
|        +1       |      `0001`      |      `0001`       |      `0001`       |
|        +0       |      `0000`      |      `0000`       |      `0000`       |
|        -0       |      `1000`      |      `1111`       |       N/A       |
|        -1       |      `1001`      |      `1110`       |      `1111`       |
|        -2       |      `1010`      |      `1101`       |      `1110`       |
|        -3       |      `1011`      |      `1100`       |      `1101`       |
|        -4       |       N/A        |       N/A       |      `1100`       |