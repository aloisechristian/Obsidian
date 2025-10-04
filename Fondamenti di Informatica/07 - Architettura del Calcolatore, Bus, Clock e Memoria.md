# Architettura del Calcolatore: Bus, Clock e Gerarchia di Memoria

L'architettura di un calcolatore moderno, basata sul **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann|modello di Von Neumann]]**, astrae la comunicazione tra i suoi componenti principali (CPU, memoria, dispositivi di I/O) attraverso un sistema di canali condivisi noto come **bus di sistema**. L'utilizzo di un bus unico favorisce la **modularità** e l'**espandibilità** del calcolatore. Per gestire informazioni di natura diversa—segnali di controllo, indirizzi e dati—il bus è logicamente suddiviso in tre bus specializzati.

### 1. Il Sistema di Bus

#### 1.1. Bus di Controllo (Control Bus)

Il bus di controllo è un canale **bidirezionale** utilizzato dalla **[[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#Struttura della CPU|Control Unit (CU)]]**, il nucleo della CPU, per inviare comandi e sincronizzare le operazioni dei vari dispositivi. I segnali principali, come **Read** e **Write**, specificano l'operazione da eseguire.

*   **Read (Lettura):** Indica al dispositivo selezionato di prepararsi a inviare dati alla CPU.
*   **Write (Scrittura):** Indica al dispositivo di prepararsi a ricevere dati dalla CPU.

Questi segnali sono attivati in istanti di tempo precisi, scanditi dall'orologio di sistema (clock), per garantire che le operazioni avvengano in modo coordinato.

#### 1.2. Bus Dati (Data Bus)

Il bus dati è il canale **bidirezionale** attraverso cui fluiscono i dati effettivi tra la CPU e il registro di memoria o il dispositivo di I/O selezionato. Il flusso dei dati è abilitato e diretto dalla CU per le operazioni di **LOAD** (lettura dalla memoria alla CPU) e **STORE** (scrittura dalla CPU alla memoria), in base al comando inviato sul bus di controllo.

#### 1.3. Bus degli Indirizzi (Address Bus)

Il bus degli indirizzi è un canale **unidirezionale** su cui la CPU invia l'indirizzo per **selezionare univocamente** il dispositivo o la cella di memoria con cui intende comunicare. Ogni componente collegato al bus monitora costantemente questo canale. Quando un dispositivo riconosce il proprio indirizzo, si predispone a partecipare all'operazione, attendendo il comando specifico dal bus di controllo.

### 2. Dinamica delle Operazioni sui Bus

Le operazioni di trasferimento dati sono sempre iniziate e coordinate dalla CPU, che utilizza i suoi [[Fondamenti di Informatica/06 - Architettura dei Calcolatori, il Modello di Von Neumann#I Registri Interni della CPU|registri interni]] per gestire il processo. Una tipica sequenza di lettura (LOAD) si svolge come segue:

1.  **Selezione dell'Indirizzo:** La CPU carica l'indirizzo della locazione di memoria desiderata nel **Memory Address Register (MAR)**, che lo trasmette sul bus degli indirizzi.
2.  **Riconoscimento:** Il sottosistema di memoria decodifica l'indirizzo e abilita il registro corrispondente.
3.  **Comando:** La CPU invia un segnale di `read` sul bus di controllo.
4.  **Trasferimento Dati:** Il dato contenuto nella locazione di memoria viene copiato nel **Memory Data Register (MDR)** attraverso il bus dati, rendendolo disponibile alla CPU.

In un'operazione di **scrittura (STORE)**, la sequenza è simile: la CPU imposta l'indirizzo nel MAR e il dato da scrivere nel MDR, per poi inviare il segnale di `write` sul bus di controllo.

### 3. Caratteristiche Fisiche dei Bus e Prestazioni

*   **Bus Seriale:** I bit vengono trasmessi in sequenza su un unico canale.
*   **Bus Parallelo:** Costituito da $N$ fili, permette la trasmissione simultanea di $N$ bit. Le dimensioni dei bus Address e Data caratterizzano l'architettura di un sistema di calcolo.

La larghezza del bus degli indirizzi determina la **capacità di indirizzamento**. Un bus a $N$ bit permette di indirizzare $2^N$ locazioni di memoria distinte.

La larghezza del bus dati influenza direttamente la **velocità di trasferimento**. Un bus a 32 bit può trasferire 32 bit per ciclo, risultando più veloce di un bus a 16 bit a parità di altre condizioni.

### 4. Il Clock di Sistema

Tutte le attività del calcolatore sono sincronizzate da un **orologio di sistema (clock)**. Questo componente genera un segnale periodico a onda quadra che scandisce il ritmo di lavoro di tutti i dispositivi.

*   **Periodo ($T$):** La durata di un ciclo completo.
*   **Frequenza ($f$):** Il numero di cicli al secondo, calcolato come $f = 1/T$ e misurato in Hertz (Hz). Le CPU moderne operano a frequenze nell'ordine dei Gigahertz (GHz), ovvero miliardi di cicli al secondo ($1 \text{ GHz} = 10^9 \text{ Hz}$).

La frequenza del clock è legata al numero di operazioni elementari che la CU può eseguire nell'unità di tempo. Tuttavia, operazioni complesse o che coinvolgono dispositivi più lenti possono richiedere **più cicli di clock** per essere completate.

#### 4.1. Temporizzazione delle Operazioni di Lettura e Scrittura

In un'ipotesi semplificata, le operazioni sono temporizzate come segue:

*   **Operazione di Lettura (LOAD):**
    1.  **Ciclo 1:** La CPU imposta l'indirizzo sul bus indirizzi.
    2.  **Ciclo 2:** La CPU attiva il segnale `read` sul bus di controllo.
    3.  **Ciclo 3:** Il dispositivo invia il dato sul bus dati.

*   **Operazione di Scrittura (STORE):**
    1.  **Ciclo 1:** La CPU imposta l'indirizzo sul bus indirizzi.
    2.  **Ciclo 2:** La CPU invia il dato da scrivere sul bus dati.
    3.  **Ciclo 3:** La CPU attiva il segnale `write` sul bus di controllo.

I segnali `read` e `write` sono attivati in istanti di tempo differenti, permettendo al sistema di distinguerli in modo inequivocabile.

### 5. Gestione dei Dispositivi di I/O e Interruzioni (Interrupt)

Per evitare che la CPU rimanga in attesa di dispositivi I/O molto più lenti, si usa il meccanismo delle **interruzioni**. Un **processore periferico** gestisce l'operazione di I/O e, una volta terminata, invia una richiesta di interruzione alla CPU.

Il ciclo del processore `fetch-decode-execute` viene esteso con una fase finale di **verifica delle interruzioni**. Se la CU rileva una richiesta di interruzione (interrogando un *bit di interruzione* nel registro di stato **Condition Code (CC)** o **Status Register (SR)**), sospende il programma corrente per eseguire una **Interrupt Service Routine (ISR)**. Questa è una procedura del sistema operativo che identifica la fonte dell'interruzione, la gestisce e infine restituisce il controllo al programma interrotto.

### 6. La Gerarchia di Memoria e la Cache

Anche la memoria centrale (RAM) è più lenta della CPU. Per colmare questo divario, viene introdotta la **memoria cache**: una memoria di piccole dimensioni ma estremamente veloce, che agisce da buffer tra la CPU e la RAM. L'efficacia della cache si basa sul **principio di località**:

*   **Località Spaziale:** Se la CPU accede a una locazione, è probabile che a breve accederà a locazioni fisicamente vicine.
*   **Località Temporale:** Se la CPU accede a una locazione, è probabile che vi accederà di nuovo in un futuro prossimo.

Quando la CPU richiede un dato non presente in cache (*cache miss*), un intero blocco di dati adiacenti viene trasferito dalla RAM alla cache. Le richieste successive, grazie alla località, troveranno i dati direttamente nella cache (*cache hit*), riducendo drasticamente il tempo di accesso.

#### 6.1. Livelli di Cache e Gerarchia Completa

Esistono più livelli di cache, tipicamente:
*   **Cache L1:** Interna alla CPU, la più piccola e veloce.
*   **Cache L2:** Esterna al core ma spesso sullo stesso package, più grande ma leggermente più lenta.

Questo porta a una **gerarchia di memoria** completa, che offre l'illusione di una memoria grande e veloce. Ogni livello funge da buffer per quello successivo. La gerarchia, ordinata per velocità decrescente e capacità crescente, è:

1.  **Registri della CPU**
2.  **Cache L1**
3.  **Cache L2**
4.  **Memoria Centrale (RAM)**
5.  **Memoria di Massa (SSD, HDD)**

### 7. Organizzazione della Memoria e Strati Software

#### 7.1. Allocazione e Indirizzamento

*   **Memorie a Voce vs. a Byte:** Nelle memorie a byte, un'istruzione o un dato può occupare più registri di memoria.
*   **Allocazione Statica vs. Dinamica:** L'allocazione di memoria può avvenire prima dell'esecuzione (statica) o durante (dinamica).
*   **Puntatori:** Un puntatore è una variabile che contiene l'indirizzo di memoria di un'altra entità (dato o istruzione). Il **Program Counter (PC)** è un esempio di puntatore a istruzione.

#### 7.2. Il Ruolo del Sistema Operativo e degli Strati Software

L'architettura fisica (hardware) è gestita e resa accessibile da strati software:
*   **Hardware:** I componenti fisici del calcolatore.
*   **Firmware:** Microprogrammi memorizzati nella memoria interna della CU che implementano le istruzioni base.
*   **Software:**
    *   **Software di Base:** Include il **Sistema Operativo (OS)**, che gestisce tutte le risorse hardware, e i traduttori di linguaggio.
    *   **Software Applicativo:** Programmi che risolvono problemi specifici dell'utente.
*   **Middleware:** Uno strato software intermedio che maschera l'eterogeneità dei dispositivi e dei sistemi operativi sottostanti, fornendo un'interfaccia di programmazione astratta e standardizzata alle applicazioni.