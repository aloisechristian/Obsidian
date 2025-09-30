# Dalla Rappresentazione Numerica alla Codifica dell'Informazione Complessa

Dopo aver analizzato in dettaglio la rappresentazione dei numeri in formato binario, standardizzata dalla specifica [[04 - Rappresentazione dei Numeri Reali in Virgola Mobile#^ae91d1|IEEE 754]] per includere numeri interi, frazionari, positivi e negativi con vari livelli di precisione (singola, doppia ed estesa), l'attenzione si sposta sulla rappresentazione di dati non numerici.

L'obiettivo è comprendere come sequenze di bit possano codificare informazioni complesse. Il principio fondamentale rimane lo stesso: stabilire uno standard di codifica a priori. Senza un codice condiviso, una sequenza di bit in memoria è una stringa indifferenziata di 0 e 1, priva di significato. È l'interpretazione, guidata da uno standard, che le attribuisce un valore specifico, che sia un numero, una lettera o un colore. Un'informazione può essere considerata completa quando un **attributo** assume un **valore** di un determinato **tipo**, come definito nella tripla `Tipo-Attributo-Valore`.

## Rappresentazione del Testo

Il testo è una delle forme più comuni di informazione digitale, costituendo la base di documenti elettronici, messaggistica e contenuti web. Un testo digitale è una stringa di simboli (lettere, numeri, punteggiatura) e, analogamente ai numeri, a ciascun simbolo viene associata una specifica parola codice, tipicamente un [[Fondamenti di Informatica/01 - Introduzione al Corso e Fondamenti dell'Informazione#Byte, Word e Multipli|byte]] (8 bit). Per garantire l'interoperabilità tra sistemi diversi, sono stati sviluppati standard di codifica dei caratteri.

### Gli Standard Storici: ASCII ed Estensioni

Lo standard **ASCII (American Standard Code for Information Interchange)**, sviluppato dall'ANSI (American National Standard Institute) alla fine degli anni '60, è stato uno dei primi e più influenti sistemi di codifica. Il suo scopo era creare un alfabeto comune che permettesse a calcolatori di produttori diversi di comunicare tra loro e con i dispositivi ad essi collegati.

Originariamente, ASCII utilizza **7 bit** per rappresentare **128 caratteri**, sebbene comunemente si utilizzi un byte intero (8 bit), lasciando il bit più significativo a 0. La codifica viene definita tramite una tabella di conversione che associa a ogni carattere un valore numerico.

La tabella ASCII include:
*   **Caratteri di controllo:** Codici non stampabili usati per gestire la comunicazione (es. per segnalare l'inizio o la fine di una trasmissione).
*   **Caratteri stampabili:** Caratteri alfabetici, numerici, di punteggiatura e simbolici.

Altri standard storici includono:
*   **EBCDIC (Extended Binary Coded Decimal Interchange Code)**: Una codifica a 8 bit sviluppata da IBM nel 1964.
*   **ASCII Esteso (ISO 8859)**: Una famiglia di codifiche a 8 bit che utilizzano il bit più significativo, precedentemente inutilizzato, per aggiungere altri 128 caratteri specifici per diverse lingue (es. ISO-8859-1 per il latino).

Il principale limite di questi standard è la loro **mancanza di supporto a un multilinguismo globale**. Essendo stati concepiti per la lingua inglese o per gruppi linguistici ristretti, non sono in grado di rappresentare simultaneamente alfabeti diversi come quello latino, cirillico e cinese.

### Lo Standard Globale: Unicode

Per superare i limiti di ASCII, è stato introdotto lo standard **Unicode (Universal Encoding)**. Il suo obiettivo è assegnare un numero univoco (chiamato *code point*) a ogni simbolo esistente, indipendentemente dalla piattaforma, dal programma o dalla lingua. Unicode è un soprainsieme di ASCII: i primi 128 caratteri di Unicode corrispondono esattamente a quelli di ASCII, garantendo la retrocompatibilità.

Unicode supporta alfabeti di tutto il mondo, inclusi il cirillico, il greco, il cinese, il giapponese e molti altri, oltre a un'ampia gamma di simboli speciali.

La codifica effettiva dei *code point* Unicode in sequenze di bit avviene tramite diversi formati di trasformazione (**UTF - Unicode Transformation Format**):
*   **UTF-8:** Utilizza un numero variabile di byte (da 1 a 4) per carattere. Per i caratteri ASCII, utilizza un solo byte (quelli i cui valori iniziano con il bit 0), rendendolo molto efficiente e retrocompatibile. È lo standard più diffuso sul web.
*   **UTF-16:** Utilizza parole a 16 bit (2 o 4 byte per carattere). È la rappresentazione interna nativa di sistemi operativi come Windows e macOS, e di linguaggi come Java.
*   **UTF-32:** Utilizza sempre 4 byte per ogni carattere, offrendo una rappresentazione a lunghezza fissa ma con un maggiore dispendio di memoria.

#### Emoticon ed Emoji

Unicode include anche blocchi di caratteri speciali come le **emoji**. Il concetto di rappresentare emozioni tramite testo nasce con le **emoticon** (da *emotional icon*), combinazioni di caratteri di punteggiatura come `:-)` e `:-(`. Le **emoji**, nate in Giappone (dal giapponese 'e' + 'moji', pittogramma), sono l'evoluzione grafica delle emoticon e sono oggi standardizzate all'interno di Unicode, nel blocco "Emoticons" compreso nell'intervallo `U+1F600` e `U+1F64F`, permettendone una rappresentazione consistente su tutte le piattaforme.

## Rappresentazione dei Dati Multimediali

Suoni, immagini e video sono grandezze **continue** (o analogiche), che variano senza soluzione di continuità nel tempo o nello spazio. Questa proprietà è analoga a quella dell'insieme dei [[Analisi I/03 - Insiemi Numerici, Completezza e Estremo Superiore|numeri reali $\mathbb{R}$]], la cui continuità è formalizzata dall'[[Analisi I/02 - Prodotto Cartesiano e Assiomi dei Numeri Reali#^240591|assioma di completezza]]. I calcolatori, tuttavia, possono elaborare solo informazioni **finite e discrete** (digitali). È quindi necessario un processo di conversione da analogico a digitale, noto come **digitalizzazione**, che si articola in due fasi principali: campionamento e quantizzazione.

### Campionamento e Quantizzazione

1.  **Campionamento:** Consiste nel prelevare campioni rappresentativi del dato multimediale misurandone il valore a intervalli regolari di tempo (o di spazio). La frequenza con cui queste misurazioni vengono effettuate è detta **frequenza di campionamento**. Maggiore è la frequenza, più fedele sarà la rappresentazione digitale del segnale originale.
2.  **Quantizzazione:** Consiste nell'approssimare il valore di ogni campione prelevato con uno di un insieme finito di livelli discreti, ovvero il valore digitale più vicino rappresentabile dal calcolatore. Il numero di bit utilizzato per rappresentare ogni livello determina la **profondità di bit**. Un numero maggiore di bit consente un'approssimazione più accurata.

Il processo trasforma un segnale continuo in una sequenza di valori numerici.

### Digitalizzazione del Suono

Un suono è una vibrazione che si propaga in un mezzo come l'aria sotto forma di onde di pressione. Le sue caratteristiche principali sono il **volume** (intensità/pressione) e la **tonalità** (frequenza/numero di oscillazioni al secondo).

*   **Campionamento del suono:** Secondo il **Teorema di Nyquist**, la frequenza di campionamento deve essere almeno il doppio della frequenza massima contenuta nel segnale audio da registrare. Poiché l'orecchio umano percepisce frequenze fino a circa $20.000$ Hz, una frequenza di campionamento di $40.000$ Hz è generalmente sufficiente. Lo standard per i CD audio è di **$44.100$ Hz** ($44.1$ kHz).
*   **Quantizzazione del suono:** La precisione di ogni campione è determinata dalla profondità di bit. Lo standard CD audio utilizza **16 bit per campione**, consentendo $2^{16} = 65.536$ livelli di quantizzazione distinti per rappresentare sia valori positivi che negativi del segnale.

**Esempio di calcolo:** Spazio necessario per un brano di 3 minuti campionato a 30 kHz con quantizzazione a 16 bit.
1.  **Durata in secondi:** $3 \text{ min} \times 60 \frac{\text{s}}{\text{min}} = 180 \text{ s}$
2.  **Bit al secondo:** $30.000 \frac{\text{campioni}}{\text{s}} \times 16 \frac{\text{bit}}{\text{campione}} = 480.000 \frac{\text{bit}}{\text{s}}$
3.  **Bit totali:** $480.000 \frac{\text{bit}}{\text{s}} \times 180 \text{ s} = 86.400.000 \text{ bit}$
4.  **Byte totali:** $\frac{86.400.000}{8} = 10.800.000 \text{ Byte}$
5.  **Megabyte totali:** $\frac{10.800.000 \text{ Byte}}{2^{20} \frac{\text{Byte}}{\text{MB}}} \approx 10,3 \text{ MB}$ (dove $1 \text{ MB} = 2^{20} \text{ Byte}$)

### Digitalizzazione delle Immagini

Un'immagine viene digitalizzata suddividendola in una griglia di punti equidistanti chiamati **pixel** (picture element). La rappresentazione dell'immagine attraverso questa griglia di pixel è detta **codifica bitmap**.

*   **Risoluzione:** È il numero di pixel che compongono l'immagine, espresso come prodotto `larghezza × altezza` (es. 640x480).
*   **Profondità di colore:** È il numero di bit usati per codificare il colore di ogni singolo pixel.
    *   **Bianco e Nero:** 1 bit per pixel (0 = bianco, 1 = nero, per convenzione).
    *   **Scala di grigi:** Tipicamente 8 bit per pixel (256 livelli di grigio).
    *   **Colore (RGB):** Lo standard più comune è **RGB (Red, Green, Blue)**, dove il colore di ogni pixel è visto come la somma di tre colori fondamentali. Con 24 bit per pixel (8 bit per rosso, 8 per verde, 8 per blu) si possono rappresentare circa $16.7$ milioni di colori ($2^{24}$). Immagini ad alta definizione possono usare 48 bit per pixel.

La fedeltà di un'immagine digitale dipende sia dalla risoluzione (aumento del numero di pixel) sia dalla profondità di colore.

**Esempio di calcolo:** Spazio per un'immagine 640x480 pixel a 256 colori.
1.  **Bit per pixel:** 256 colori richiedono $\log_2(256) = 8$ bit per pixel.
2.  **Pixel totali:** $640 \times 480 = 307.200 \text{ pixel}$
3.  **Bit totali:** $307.200 \text{ pixel} \times 8 \frac{\text{bit}}{\text{pixel}} = 2.457.600 \text{ bit}$
4.  **Byte totali:** $\frac{2.457.600}{8} = 307.200 \text{ Byte}$
5.  **Megabyte totali:** $\frac{307.200 \text{ Byte}}{2^{20} \frac{\text{Byte}}{\text{MB}}} \approx 0,29 \text{ MB}$

### Digitalizzazione dei Video

Un video è una sequenza di immagini statiche, chiamate **frame**, visualizzate rapidamente per creare l'illusione del movimento. La digitalizzazione di un video consiste nel catturare e digitalizzare una sequenza continua nel tempo di immagini.

*   **Frequenza di campionamento (Frame Rate):** È il numero di frame catturati o visualizzati al secondo (fps). Standard comuni sono 24 fps (cinema) e 25-30 fps (televisione).

Lo spazio di archiviazione per un video non compresso è molto elevato. Per questo motivo, si utilizzano tecniche di **compressione** (es. MPEG), che sfruttano la ridondanza tra frame consecutivi: poiché due immagini consecutive sono spesso molto simili, la compressione memorizza solo "la differenza" tra di esse, riducendo drasticamente le dimensioni del file.

## Introduzione all'Algebra di Boole

L'Algebra di Boole è il fondamento matematico della logica digitale e dell'informatica.

### Proposizioni Logiche e Predicati

Una **proposizione logica semplice** è un'affermazione (o enunciato) che può assumere uno e un solo valore logico: **vero (V o 1)** o **falso (F o 0)**.
*   Esempio di proposizione: "25 è un numero pari" (Falso).
*   Esempio di non proposizione: "Vittorio è molto simpatico?" (Domanda soggettiva, non è un enunciato).

I **predicati** sono espressioni che contengono variabili e il cui valore di verità dipende dal valore assegnato a tali variabili. Si costruiscono spesso con **operatori di relazione** (o di confronto) come `=`, `≠`, `<`, `>`.
*   Esempio di predicato: `$x \neq 0$`. Il suo valore di verità dipende da cosa rappresenta `$x$`.

### Operatori Logici e Tabelle di Verità

Le proposizioni semplici possono essere combinate in **proposizioni composte** tramite **operatori logici**. I tre operatori fondamentali (binari e unari chiusi) sono:
*   **AND (Congiunzione logica, `·`)**: `A AND B` è vero solo se sia A che B sono veri. Detto anche prodotto logico.
*   **OR (Disgiunzione logica, `+`)**: `A OR B` è vero se almeno uno tra A e B è vero. Detto anche somma logica.
*   **NOT (Negazione logica, ` `$\overline{A}$` `)**: `NOT A` è vero se A è falso, e viceversa. Detto anche operatore di complementazione.

Il comportamento di questi operatori è definito formalmente da **tabelle di verità**, che elencano il risultato dell'operazione per tutte le possibili combinazioni dei valori di verità degli operandi.

| A | B | $A \cdot B$ | $A + B$ |
|:-:|:-:|:-----------:|:-------:|
| 0 | 0 |      0      |    0    |
| 0 | 1 |      0      |    1    |
| 1 | 0 |      0      |    1    |
| 1 | 1 |      1      |    1    |

| A | $\overline{A}$ |
|:-:|:--------------:|
| 0 |       1        |
| 1 |       0        |

Questi operatori si applicano **bit a bit (bitwise)** quando operano su stringhe binarie.

### Proprietà dell'Algebra di Boole

L'algebra di Boole gode di diverse proprietà fondamentali:
*   **Commutativa:** $A+B = B+A$; $A \cdot B = B \cdot A$
*   **Associativa:** $(A+B)+C = A+(B+C)$; $(A \cdot B) \cdot C = A \cdot (B \cdot C)$
*   **Distributiva:** $A \cdot (B+C) = A \cdot B + A \cdot C$; $A + (B \cdot C) = (A+B) \cdot (A+C)$
*   **Idempotenza:** $A+A = A$; $A \cdot A = A$
*   **Assorbimento:** $A + (A \cdot B) = A$; $A \cdot (A+B) = A$
*   **Proprietà di Minimo e Massimo:** $A \cdot 0 = 0$; $A+1=1$
*   **Complemento:** $A \cdot \overline{A} = 0$; $A + \overline{A} = 1$

Una proprietà fondamentale è il **principio di dualità**: da una qualsiasi identità booleana se ne ricava un'altra sostituendo l'operatore `+` con `·` e l'elemento logico 0 con 1, e viceversa.

I **Teoremi di De Morgan** sono un'applicazione diretta di questo principio e sono cruciali per la semplificazione delle espressioni logiche:
1.  $\overline{A+B} = \overline{A} \cdot \overline{B}$
2.  $\overline{A \cdot B} = \overline{A} + \overline{B}$

Questi teoremi e proprietà possono essere dimostrati rigorosamente costruendo le relative tabelle di verità per verificare l'uguaglianza dei risultati in tutti i casi possibili.
