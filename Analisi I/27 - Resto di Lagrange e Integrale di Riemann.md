# Formula di Taylor: Applicazioni e Introduzione all'Integrazione di Riemann

## 1. Il Polinomio di Taylor e il Resto

Sia $f(x)$ una funzione derivabile $n$ volte in un punto $x_0$. È possibile approssimare $f(x)$ mediante un polinomio $P_n(x)$ di grado $n$, i cui coefficienti sono determinati dalle derivate della funzione valutate in $x_0$.
Per approfondimenti sulla costruzione dei polinomi, vedi [[Analisi I/25 - Sviluppi di Taylor e Classificazione degli Estremi|Sviluppi di Taylor]].

La formula generale è:

$$
f(x) = \sum_{k=0}^{n} \frac{f^{(k)}(x_0)}{k!} (x - x_0)^k + R_n(x)
$$

dove $R_n(x)$ rappresenta il termine di errore o **resto**, che quantifica l'approssimazione.

### 1.1 Forme del Resto

Esistono diverse formulazioni per il resto, utili in contesti differenti:

* **Resto di Peano:** Utile per il calcolo dei limiti (vedi [[Analisi I/26 - Teorema di De L'Hopital e Formula di Taylor con Resto di Peano|Applicazioni ai Limiti]]) e per il comportamento locale. Se $f$ è derivabile $n$ volte in $x_0$, allora:
    $$
    R_n(x) = o((x - x_0)^n) \quad \text{per } x \to x_0
    $$
    Questo indica che l'errore è un infinitesimo di ordine superiore rispetto a $(x - x_0)^n$.

* **Resto di Lagrange:** Utile per stimare l'errore quantitativamente. Se $f$ è derivabile $n+1$ volte in un intorno di $x_0$, esiste un punto $x_1$ (o $\xi$) compreso tra $x_0$ e $x$ tale che:
    $$
    R_n(x) = \frac{f^{(n+1)}(x_1)}{(n+1)!} (x - x_0)^{n+1}
    $$
    
    > [!check] Stima dell'errore
    > Se la derivata $(n+1)$-esima è continua in un intervallo chiuso e limitato $[a, b]$, per il **Teorema di Weierstrass** essa ammette un massimo $M_{n+1}$. Ne consegue la stima globale dell'errore:
    > $$
    > |R_n(x)| \le \frac{M_{n+1}}{(n+1)!} |x - x_0|^{n+1} \quad \forall x \in [a, b]
    > $$

#### Dimostrazione della Formula con Resto di Lagrange
Fissati $x, x_0 \in [a, b]$ con $x \ne x_0$, si definisce una funzione ausiliaria $g(t)$ per $t$ nell'intervallo di estremi $x_0$ e $x$:
$$
g(t) = \sum_{k=0}^{n} \frac{f^{(k)}(t)}{k!} (x - t)^k + R_n(x) \frac{(x - t)^{n+1}}{(x - x_0)^{n+1}}
$$
Si osserva che:
1.  $g(t)$ è derivabile nell'intervallo.
2.  Agli estremi assume valori identici:
    * $g(x) = f(x)$ (tutti i termini della sommatoria si annullano eccetto il primo termine $f(x)$... in realtà per $t=x$ rimane solo $f(x)$ nella somma se $k=0$ e il resto si annulla). *Nota: Più precisamente, calcolando $g(x)$ si ottiene $f(x)$*.
    * $g(x_0) = \sum_{k=0}^{n} \frac{f^{(k)}(x_0)}{k!} (x - x_0)^k + R_n(x) = f(x)$ (per definizione di $R_n$).
    
Essendo $g(x) = g(x_0)$, per il **Teorema di Rolle** (vedi [[Analisi I/22 - Teoremi Fondamentali del Calcolo Differenziale e Applicazioni|Teoremi Fondamentali]]) esiste un punto $x_1$ interno all'intervallo tale che $g'(x_1) = 0$.
Calcolando la derivata $g'(t)$ (si noti che è una somma telescopica in cui molti termini si elidono), rimane solo:
$$
g'(t) = \frac{f^{(n+1)}(t)}{n!} (x - t)^n - (n+1) R_n(x) \frac{(x - t)^n}{(x - x_0)^{n+1}}
$$
Imponendo $g'(x_1) = 0$ e risolvendo per $R_n(x)$, si ottiene la tesi.

## 2. Applicazione: Classificazione dei Punti Stazionari

La formula di Taylor fornisce un criterio generale per stabilire la natura di un punto stazionario $x_0$ (dove $f'(x_0) = 0$), basandosi sul segno della prima derivata non nulla successiva.

**Teorema:** Sia $f$ di classe $C^n$ e supponiamo che:
$$
f'(x_0) = f''(x_0) = \dots = f^{(n-1)}(x_0) = 0 \quad \text{e} \quad f^{(n)}(x_0) \neq 0
$$

La natura del punto $x_0$ dipende dall'ordine $n$ di derivazione:

1.  **Se $n$ è PARI:**
    * $f^{(n)}(x_0) > 0 \implies x_0$ è un punto di **minimo relativo**.
    * $f^{(n)}(x_0) < 0 \implies x_0$ è un punto di **massimo relativo**.
2.  **Se $n$ è DISPARI:**
    * $x_0$ non è né massimo né minimo (è un punto di flesso a tangente orizzontale).

**Approfondimento:** Per una dimostrazione dettagliata basata sul segno del rapporto incrementale e il teorema della permanenza del segno, consultare la nota [[Analisi I/25 - Sviluppi di Taylor e Classificazione degli Estremi#Dimostrazione del Teorema|Dimostrazione Classificazione Estremi]].

## 3. Algebra degli o-piccoli

Il simbolo di Landau $o(x^n)$ gode di specifiche proprietà algebriche fondamentali per il calcolo degli sviluppi asintotici ($x \to 0$). Per la definizione formale, vedi [[Analisi I/20 - Infinitesimi, Principio di Sostituzione e Derivata|Infinitesimi]].

* **Somma:** $o(x^n) \pm o(x^n) = o(x^n)$.
* **Prodotto per scalare:** $a \cdot o(x^n) = o(x^n)$ per ogni costante $a \in \mathbb{R} \setminus \{0\}$.
* **Prodotto di o-piccoli:** $o(x^n) \cdot o(x^m) = o(x^{n+m})$.
* **Assorbimento:** Se $m > n$, allora $x^m = o(x^n)$ e $o(x^n) + o(x^m) = o(x^n)$. I termini di grado superiore vengono "inglobati".
* **Prodotto misto:** $x^m \cdot o(x^n) = o(x^{m+n})$.
* **Composizione:** $o(o(x^n)) = o(x^n)$.

**Esempio pratico:** Sviluppo di $\sin^2(x)$ all'ordine 4.
Utilizziamo lo sviluppo noto: $\sin(x) = x - \frac{x^3}{6} + o(x^4)$.
$$
\sin^2(x) = \left(x - \frac{x^3}{6} + o(x^4)\right)^2
$$
Svolgendo il quadrato del trinomio:
$$
= x^2 + \frac{x^6}{36} + [o(x^4)]^2 - \frac{2x^4}{6} + 2x \cdot o(x^4) - \frac{x^3}{3} o(x^4)
$$
Analizziamo gli ordini di infinitesimo per $x \to 0$:
* $x^6/36$ è di ordine superiore a $x^5$ (quindi $o(x^5)$).
* $[o(x^4)]^2 = o(x^8)$.
* $2x \cdot o(x^4) = o(x^5)$.
* $- \frac{x^3}{3} o(x^4) = o(x^7)$.

Tutti questi termini sono riassumibili in $o(x^5)$ (o $o(x^4)$ se ci fermiamo all'ordine 4).
$$
\sin^2(x) = x^2 - \frac{x^4}{3} + o(x^5)
$$

## 4. Introduzione all'Integrale di Riemann

L'obiettivo è definire l'area sottesa da una funzione $f: [a, b] \to \mathbb{R}$ limitata.
L'area è definita formalmente come insieme $S = \{(x,y) \in [a,b] \times \mathbb{R} \mid 0 \le y \le f(x)\}$ (nel caso $f \ge 0$).

### 4.1 Partizioni e Somme Integrali

* **Partizione $P$:** Un insieme ordinato di punti $x_0, x_1, \dots, x_n$ tale che $a = x_0 < x_1 < \dots < x_n = b$.
* Dati gli intervalli $I_k = [x_{k-1}, x_k]$, definiamo (vedi [[Analisi I/03 - Insiemi Numerici, Completezza e Estremo Superiore|Estremo Superiore e Inferiore]]):
    * $m_k = \inf \{ f(x) : x \in I_k \}$
    * $M_k = \sup \{ f(x) : x \in I_k \}$

Definiamo le somme integrali relative alla partizione $P$:
* **Somma integrale inferiore:** $s(P) = \sum_{k=1}^{n} m_k (x_k - x_{k-1})$ (Area plurirettangolo inscritto).
* **Somma integrale superiore:** $S(P) = \sum_{k=1}^{n} M_k (x_k - x_{k-1})$ (Area plurirettangolo circoscritto).

### 4.2 Proprietà Fondamentali

1.  **Confronto locale:** Per ogni partizione $P$, vale sempre $s(P) \le S(P)$ poiché $m_k \le M_k$.
2.  **Raffinamento:** Se $R$ è un raffinamento di $P$ (ovvero $P \subset R$, $R$ contiene più punti), l'approssimazione migliora:
    $$
    s(P) \le s(R) \le S(R) \le S(P)
    $$
    *Dimostrazione intuitiva:* Aggiungendo un punto $\bar{x}$ in un intervallo $[x_{k-1}, x_k]$, l'inf della funzione sui due sotto-intervalli generati sarà $\ge$ all'inf sull'intervallo intero. Quindi la somma inferiore aumenta.

3.  **Lemma del confronto tra partizioni arbitrarie:**
    Siano $P$ e $Q$ due partizioni *qualsiasi* di $[a, b]$. Vale sempre:
    $$
    s(P) \le S(Q)
    $$
    **Dimostrazione:**
    Si considera la partizione unione $R = P \cup Q$. Poiché $R$ è un raffinamento sia di $P$ che di $Q$, valgono le disuguaglianze:
    $$
    s(P) \le s(R) \le S(R) \le S(Q)
    $$
    Questo implica che l'insieme delle somme inferiori è sempre separato dall'insieme delle somme superiori.

L'**integrale di Riemann** è definito come l'elemento separatore unico tra la classe delle somme inferiori e quella delle somme superiori:
$$
\int_a^b f(x) dx = \sup_P \{s(P)\} = \inf_P \{S(P)\}
$$