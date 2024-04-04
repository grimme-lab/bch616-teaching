.. include:: symbols.txt

Experiment 10: Computer gestützte Thermodynamik
===============================================

.. contents::

Hintergrund
-----------

Ziel des Experiments ist es, dass Sie Methoden aus der statistischen Thermodynamik verwenden um chemische Reaktionen und die Energie von chemischen Bindungen zu beschreiben.
Auch soll Ihnen gezeigt werden, dass die Frequenzrechnung ein wichtiges Werkzeug für die theoretische Thermochemie ist.


Grundlagen der statistischen Thermodynamik
------------------------------------------

Der Zusammenhang zwischen (mikroskopischen) molekularen Größen und den (makroskopischen) Messwerten von chemischen System ist durch die Zustandssumme :math:`Q` gegeben.
Sie basiert auf der Boltzmann-Verteilung über die verfügbaren Mikrozustände:

.. math::

    Q = \sum\limits_{j=1}^N g_j \cdot e^{-\frac{E_j}{k_B \cdot T}}

Wobei :math:`N` die Anzahl der erreichbaren Zustände, :math:`E_j` die Energie des :math:`j`ten Zustandes, :math:`k_B` die Boltzmann-Konstante und :math:`T` die Temperatur in Kelvin ist (der Term :math:`k_B \cdot T` kann als vorhandene thermische Energie gesehen werden).
Der Entartungsgrad :math:`g_j` ist direkt gegeben durch die Entartung des :math:`j`-ten Zustandes. Die Werte sind gleich, wenn die Zustände nicht entartet sind.
Nehmen wir als Beispiel ein homogenes chemisches System von Molekülen, z. B. ein molekulares Gas.
Aus der makroskopischen Sicht sind die Systemkomponenten die Moleküle und die Systemenergie :math:`E_j` ist abhängig von Ordnung der Komponenten und deren Energie.
Die dazugehörige Zustandssumme wird als kanonische oder Systemzustandssumme :math:`Q` bezeichnet, wohingegen die mikrokanonische oder molekulare Zustandssumme :math:`q` die einzelnen Moleküle des übergeordneten Systems betrachtet, sie ist also eine Summe über molekulare Energiezustände.
In erster Näherung kann die Gesamtenergie eines Moleküls aufgeteilt werden in Anteile der Molekularen Freiheitsgrade (was eine direkte Folgerung aus der Born-Oppenheimer-Näherung ist).

.. math::

    \varepsilon = \varepsilon^{trans}_{i} + \varepsilon^{rot}_{j} + \varepsilon^{vib}_{k} + \varepsilon^{el}_{l}

Die molekulare Anteile können zerlegt werden:

.. math::

    q = q_{trans} + q_{rot} + q_{vib} + q_{el}

Thermodynamische Größen
-----------------------

Nach der Berechnung der Zustandssumme des Systems können wir diese verwenden, um andere thermodynamische Größen zu bestimmen. Als Beispiel soll hier die Bestimmung der Entropie :math:`S` dienen. Die Faktorisierung der Zustandssumme ist die Basis dieser Berechnungen.

Ein Beispiel: In der klassischen Thermodynamik ist die Entropie (eines reversiblen Prozesses) nach Clausius definiert als:

.. math::

    \mathrm{d}S = \frac{C_V}{T} \mathrm{d}T

Die Wärmekapazität :math:`C_V` ist gegeben durch die erste Ableitung der inneren Energie :math:`U` nach der Temperatur bei konstantem Volumen. Es ergibt sich also:

.. math::

    S - S_0 = \int\limits_0^T \frac{1}{T} \frac{\partial}{\partial T} \left( k_B T^2 \frac{\partial \ln Q}{\partial T} \right)_V \mathrm{d}T

Nach Auswertung des Integrals und Einsetzen der inneren Energie:

.. math::

    S - S_0 = k_B T \left( \frac{\partial \ln Q}{\partial T} \right)_V + k_b \ln Q - (k_B \ln Q)_{T=0}

Der temperaturunabhängige Term :math:`S_0` kann identifiziert werden als :math:`S_0 = (k_B \ln Q)_{T=0}`, was der Nullpunktsentropie, der Entropie bei 0 K, entspricht. Die restlichen Terme entsprechen der temperaturabhängigen Entropie:

.. math::

    S = k_B T \left( \frac{\partial \ln Q}{\partial T} \right)_V + k_b \ln Q

Andere thermodynamische Größen können analog hergeleitet werden. Die nachfolgende Tabelle fasst die wichtigsten thermodynamischen Größen und deren Ausdrücke durch die Zustandssumme zusammen.

.. csv-table:: 
   :header: "Funktion", "Statistischer Ausdruck"
   :widths: 30, 70

   "innere Energie :math:`U`", ":math:`U = k_B T^2 \left( \frac{\partial \ln Q}{\partial T} \right)_V`"
   "Entropie :math:`S`", ":math:`S = k_B T \left( \frac{\partial \ln Q}{\partial T} \right)_V + k_b \ln Q`"
   "Enthalpie :math:`H`", ":math:`H = k_B T^2 \left( \frac{\partial \ln Q}{\partial T} \right)_V + k_B T V \left( \frac{\partial \ln Q}{\partial V} \right)_T`"
   "freie Gibbs Enthalpie :math:`G`", ":math:`G = k_B T V \left( \frac{\partial \ln Q}{\partial V} \right)_T - k_B T \ln Q`"


Die meisten quantenchemischen Programme nutzen das ideale Gasgesetz, die Modelle des Starren Rotators und des harmonischen Oszillators als Basis für die Berechnung der Zustandssumme.


Bindungsdissoziationsenergie und Atomisierungsenergie
-----------------------------------------------------

Die Stärke einer intramolekularen Bindung ist, im chemischen Sinne, definiert als die Bindungsenergie :math:`E^{bind}`, was im Falle eines zweiatomigen Moleküls identisch mit der Dissoziationsenergie :math:`E^{diss}` ist. Für größere Moleküle AB\ :sub:`n` ist die Bindungsenergie das arithmetische Mittel der Summe über alle :math:`n` möglichen A-B Bindungsdissoziationsenergien:

.. math::

    E^{bind}_{AB} = \frac{1}{n} \sum\limits_{i=1}^{n} E_i^{diss}

Selbst für mittelgroße Moleküle gibt es oft einen signifikanten Unterschied zwischen der Dissoziationsenergie und der Bindungsenergie.

Im Unterschied dazu ist die Atomisierungsenergie :math:`E^{atom}` definiert als die Reaktionsenergie, welche frei wird, wenn die gasförmige Spezies AB\ :sub:`n` in ein Atom A und :math:`n` Atome B zerfällt. Eine mögliche Berechnung besteht darin, die Bildungsenthalpie der Gasphasenreaktion (A + :math:`n` B → AB\ :sub:`n`) und die benötigte Energie für den Transfer von der stabilsten Elementmodifikation A\ :sub:`x`, B\ :sub:`y` in die Gasphase zu addieren.


Beschreibung des Experiments
----------------------------

.. admonition:: Änderung der freien Gibbs-Enthalpie

   Um das Konzept zu verstehen, werden Sie einfache chemische Systeme untersuchen und die Änderung der freien Gibbs-Enthalpie :math:`\Delta G^0` berechnen. Die Beispielreaktionen beinhalten die Haber-Bosch-Reaktion, die Knallgas-Reaktion von Wasserstoff und Sauerstoff zu Wasser und eine Gasphasenreaktion zwischen Wasser und Kohlenstoffmonoxid (Wassergasgleichgewicht).

   * Knallgas-Reaktion: :math:`\ce{2 H2 + O2 -> 2 H2O}`
   * Haber-Bosch-Reaktion: :math:`\ce{N2 + 3 H2 -> 2 NH3}`
   * Wassergasgleichgewicht: :math:`\ce{H2O + CO -> H2 + CO2}`

   #. Im ersten Schritt optimieren Sie die Geometrie aller Reaktanden. Nutzen Sie dazu das TPSS Funktional und einen TZVP Basissatz.
   #. Führen Sie eine Frequenzrechnung für die optimierten Strukturen durch und entnehmen Sie dem Output die relevanten thermochemischen Daten.
   #. Berechnen Sie die Änderung der freien Gibbs-Enthalpie für alle Reaktionen und vergleichen Sie diese mit den experimentellen Werten.


.. admonition:: Stärke verschiedener :math:`\ce{C-H}`-Bindungen

   Als nächstes soll die Stärke verschiedener :math:`\ce{C-H}`-Bindungen an verschiedenen, einfachen, organischen Molekülen untersucht werden. Folgende Systeme sollen untersucht werden: Methan, Acetylen, Benzen und Acetaldehyd.

   #. Optimieren Sie die Struktur für alle Moleküle. Starten Sie wieder mit der Kombination von TPSS und TZVP.

   #. Machen Sie sich mit der Berechnung von Radikalen vertraut (Stichworte: Multiplizität, UHF-Rechnung). Bestimmen Sie die Bindungsenergie für folgenden Vorgang: :math:`\ce{CH4 -> H3C. + H.}`. Vergleichen Sie diese mit :math:`\frac{1}{4}` der Atomisierungsenergie von :math:`\ce{CH4}`.

   #. Berechnen Sie ebenfalls die Bindungsenergien für:
      
      a. :math:`\ce{H-CCH -> H. + HCC.}`
      
      b. :math:`\ce{H-C6H5 -> H. + H5C6.}`
      
      c. :math:`\ce{H-CH2CHO -> H. + CHOH2C.}`
      
      d. :math:`\ce{H-COCH3 -> H. + CH3OC.}`
      
   #. Wiederholen Sie die Rechnungen mit einem kleineren (SVP) und einem größeren (QZVP) Basissatz. Beobachten Sie einen Basissatzeffekt?

.. csv-table:: Bindungsdissoziationsenergie von :math:`\ce{C-H}`-Bindungen
   :header: "Bindung", ":math:`D_{298}^{0}` [kJ/mol]"
   :widths: 30, 30

   :math:`\ce{H-CH3}`, 
   :math:`\ce{H-C6H5}`, 
   :math:`\ce{H-CCH}`, 
   :math:`\ce{H-CH2CHO}`, 
   :math:`\ce{H-COCH3}`

.. csv-table:: Freie Gibbs-Enthalpie, SVP Basissatz
   :header: "Reaktanden", ":math:`\\Delta G` [Eh]", ":math:`\\Delta G` [kJ/mol]"
   :widths: 30, 30, 30

   :math:`\ce{N2}`, ,
   :math:`\ce{H2}`, ,
   :math:`\ce{NH3}`, ,
   :math:`\ce{CO}`, ,
   :math:`\ce{CO2}`, ,
   :math:`\ce{H2O}`, ,
   :math:`\ce{O2}`,

.. csv-table:: Freie Gibbs-Enthalpie, TZVP Basissatz
   :header: "Reaktanden", ":math:`\\Delta G` [Eh]", ":math:`\\Delta G` [kJ/mol]"
   :widths: 30, 30, 30

   :math:`\ce{N2}`, ,
   :math:`\ce{H2}`, ,
   :math:`\ce{NH3}`, ,
   :math:`\ce{CO}`, ,
   :math:`\ce{CO2}`, ,
   :math:`\ce{H2O}`, ,
   :math:`\ce{O2}`,


.. csv-table:: Freie Gibbs-Enthalpie, QZVP Basissatz
   :header: "Reaktanden", ":math:`\\Delta G` [Eh]", ":math:`\\Delta G` [kJ/mol]"
   :widths: 30, 30, 30

   :math:`\ce{N2}`, ,
   :math:`\ce{H2}`, ,
   :math:`\ce{NH3}`, ,
   :math:`\ce{CO}`, ,
   :math:`\ce{CO2}`, ,
   :math:`\ce{H2O}`, ,
   :math:`\ce{O2}`,

.. csv-table:: Änderung der freien Gibbs-Enthalpie, SVP Basissatz
   :header: "Reaktion", ":math:`\\Delta G_\\mathrm{exp}` [kJ/mol]", ":math:`\\Delta G_\\mathrm{calc}` [kJ/mol]", ":math:`\\Delta G_\\mathrm{calc}` [Eh]"
   :widths: 30, 30, 30, 30

   :math:`\ce{2 H2 + O2 -> 2 H2O}`, -572.0, , 
   :math:`\ce{N2 + 3 H2 -> 2 NH3}`, -92.3, , 
   :math:`\ce{H2O + CO -> H2 + CO2}`, -41.2, , 

.. csv-table:: Änderung der freien Gibbs-Enthalpie, TZVP Basissatz
   :header: "Reaktion", ":math:`\\Delta G_\\mathrm{exp}` [kJ/mol]", ":math:`\\Delta G_\\mathrm{calc}` [kJ/mol]", ":math:`\\Delta G_\\mathrm{calc}` [Eh]"
   :widths: 30, 30, 30, 30

   :math:`\ce{2 H2 + O2 -> 2 H2O}`, -572.0, , 
   :math:`\ce{N2 + 3 H2 -> 2 NH3}`, -92.3, , 
   :math:`\ce{H2O + CO -> H2 + CO2}`, -41.2, , 

.. csv-table:: Änderung der freien Gibbs-Enthalpie, QZVP Basissatz
   :header: "Reaktion", ":math:`\\Delta G_\\mathrm{exp}` [kJ/mol]", ":math:`\\Delta G_\\mathrm{calc}` [kJ/mol]", ":math:`\\Delta G_\\mathrm{calc}` [Eh]"
   :widths: 30, 30, 30, 30

   :math:`\ce{2 H2 + O2 -> 2 H2O}`, -572.0, , 
   :math:`\ce{N2 + 3 H2 -> 2 NH3}`, -92.3, , 
   :math:`\ce{H2O + CO -> H2 + CO2}`, -41.2, , 
