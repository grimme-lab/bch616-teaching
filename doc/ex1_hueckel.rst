.. include:: symbols.txt

Experiment: Hückel-Theorie für |pi|-Elektronensystem (HMO)
==========================================================

.. contents::

Die Hückelmethode ist eine der einfachsten semiempirischen Methoden zur quantenchemischen Beschreibung molekularer Systeme. Sie wurde 1931 von E. Hückel zur Berechnung planarer konjugierter Kohlenwasserstoffe entworfen. Eine herausragende historische Bedeutung kommt ihr deshalb zu, weil man - vor allem durch Berücksichtigung der Symmetrieeigenschaften - auf eine aufwendige numerische Behandlung, d.h. Computer, verzichten konnte.

Näherungen in der Hückel-Theorie
--------------------------------

Für planare, konjugierte (d.h. aus :math:`\mathrm{sp}^{2}`-hybridisierten Atomen aufgebaute) Systeme können folgende Näherungen eingeführt werden:

1. Die |sigma|-Elektronen werden explizit vernachlässigt, d.h. ergeben ein konstantes Potential für alle |pi|-Elektronen.
2. Für jedes Atom wird nur ein Atomorbital pz in der LCAO-Entwicklung verwendet.
3. Die Überlappungsintegrale werden vernachlässigt für :math:`\mu \neq \nu` (:math:`S_{\mu\mu} = 1`).
4. Die Integrale :math:`H_{\mu\nu}` werden empirisch festgelegt:

(a) :math:`H_{\mu\nu} = \beta`, falls die Atome |mu| und |nu| direkt verbunden sind (Energie eines Elektrons im Feld zweier Kerne mit impliziten Korrekturen für vernachlässigte Terme). Sind |mu| und |nu| nicht direkt miteinander verbunden, gilt :math:`H_{\nu\nu} = 0`.
(b) :math:`H_{\nu\nu} = \alpha` (Energie eines Elektrons im Feld des Kerns |mu| mit impliziten Korrekturen für vernachlässigte Terme).

In der Praxis wird :math:`\alpha` für Kohlenstoff willkürlich auf Null gesetzt, und die Parameter anderer Atome werden relativ dazu empirisch bestimmt. :math:`\beta` (Resonanzintegral) wird für eine :math:`\ce{C-C}` Bindung der Länge 1.4 :math:`\text{Å}` als Standard auf -1 gesetzt. Bei Molekülen mit starken Abweichungen von dieser Standardlänge oder bei :math:`\ce{C-X}` Bindungen wird der :math:`\beta`-Wert empirisch verändert.

Diskussion der eingeführten Näherungen
--------------------------------------

1.  Die :math:`\sigma`-:math:`\pi`-Separation ist gerechtfertigt, wenn die :math:`\sigma`-Elektronen in guter Näherung für die Reihe zu vergleichender :math:`\pi`-Zustände durch die gleiche Produktfunktion dargestellt werden können, d.h. wenn es innerhalb einer Reihe keine unterschiedlichen  :math:`\sigma`-:math:`\pi` Polarisationseffekte gibt. Behandelt man Aromaten unterschiedlichen Typs, ist diese Annahme jedoch bereits problematisch, da der Einfluss der :math:`\sigma`-Orbitale auf die Stabilität von Aromaten wohl nicht zu vernachlässigen ist. Ähnliches gilt für elektronische Spektren von Aromaten.
2. Bei einfachen Kohlenwasserstoffen ist die Korrelation der Parameter :math:`\alpha` und :math:`\beta` mit experimentellen Größen recht brauchbar. Probleme treten beim Vorhandensein von Heteroatomen, stark polarisierbaren Atomen oder Molekülgruppen oder bei Bindungsstabilisierungseffekten wie Hyperkonjugation auf.

Ladungsordnung und Bindungsordnung
-------------------------------------------
In der Hückeltheorie werden zur Beschreibung der Ladungsverteilung
und der Bindungseigenschaften die Begriffe Ladungsordnung und
Bindungsordnung definiert. Die Ladungsordnung kann mit dem Begriff
der Partialladung in Verbindung gebracht werden. Die Bindungsordnung
ist ein Maß für die Stärke der :math:`\pi`-Bindung zwischen zwei Atomen und
kann sehr gut mit Bindungslängen korreliert werden. Da die Hückel-Orbitalenergie
$\epsilon_i$ durch den folgenden Ausdruck

.. math::
   \epsilon_i=\sum_{r=1}^{M} c^2_{ir}\alpha_r + \sum_{r\ne s} c_{ir}c_{is}\beta_{rs}

gegeben ist (:math:`M` ist die Zahl der :math:`\pi`-Atome bzw. Atomorbitale :math:`p_z`, :math:`c_{ir}` ist der LCAO-Entwicklungskoeffizient des MOs :math:`i` am Atom(orbital) :math:`r`), ergeben sich für Ladungs- und Bindungsordnung die folgenden Ausdrücke:

1. **Ladungsordnung** am Atom $A$

.. math::
   \begin{split}
   q_A \equiv \frac{\partial E}{\partial \alpha_A} &= \sum_{i=1}^{M} n_i \frac{\partial \epsilon_i}{\partial \alpha_A} \\
   &= \sum_{i=1}^{M} n_i \frac{\partial}{\partial \alpha_A}\left(\sum_{r=1}^{M} c^2_{ir}\alpha_r + \sum_{r\ne s} c_{ir}c_{is}\beta_{rs}\right)\\
   &= \sum_{i=1}^{M} n_i |c_{iA}|^2.
   \end{split}

:math:`n_i` ist dabei die Besetzungszahl des MOs $i$ (0, 1 oder 2).

Anschaulich summiert man also von allen besetzten MOs (für unbesetzte ist :math:`n_i = 0`) die 
AO-Koeffizienten am Atom :math:`A` auf, so dass eine "Gesamt-:math:`\pi`-Elektronendichte" am 
Atom :math:`A` erhalten wird.

2. **Bindungsordnung** zwischen den Atomen :math:`A` und :math:`B`

.. math::
      \begin{split}
      p_{AB} \equiv \frac{1}{2} \frac{\partial E}{\partial \beta_{AB}} &= \frac{1}{2} \sum_{j=1}^{M} n_j \frac{\partial \epsilon_j}{\partial \beta_{AB}}\\
      &= \frac{1}{2}\sum_{j=1}^{M} n_j \frac{\partial}{\partial \beta_{AB}}(\sum_{r=1}^{M} c^2_{jr}\alpha_r + \sum_{r\ne s} c_{jr}c_{js}\beta_{rs})\\
      &= \sum_{j=1}^{M} n_j c_{jA} c_{jB} 
      \end{split}

Wie erkennbar ist, hat dieser Ausdruck eine große Ähnlichkeit mit der Definition der Ladungsordnung. 
Es wird ebenfalls über alle besetzten MOs summiert. Um eine *Bindungs*ordnung zu erhalten, sind 
die Summanden aber hier Produkte von AO-Koeffizienten benachbarter Atome.




Anleitung: Durchführung einer Hückel-Rechnung
---------------------------------------------

Erstellen Sie zunächst ein Verzeichnis für die Hückelrechnungen (z.B. ``mkdir hueckel``).  
Wechseln Sie in dieses Verzeichnis (``cd hueckel``).  

Erstellen Sie die Eingabedatei mit einem Editor. Die erste Zeile enthält die Anzahl der :math:`\pi`-Atome. In der zweiten Zeile wird die Zahl der :math:`\pi`-Elektronen angegeben. Danach erfolgt die Eingabe der Hückel-Matrix, und zwar zuerst die Nummern der verbundenen Atome gefolgt vom Betrag des Resonanzintegrals :math:`\beta` bzw.\ des Coulombintegrals :math:`\alpha`.

Im Folgenden ist eine Beispieleingabe für Pyrrol angegeben (5 Atome, 6 :math:`\pi`-Elektronen):

.. code-block:: bash

   5
   6
   1 1 0.5
   1 2 0.8
   2 3 1.0
   3 4 1.0
   4 5 1.0
   1 5 0.8



Anleitung für das Extended-H ̈uckel Programm EHT
------------------------------------------------

Aufgaben
--------

