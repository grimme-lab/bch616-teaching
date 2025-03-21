.. include:: symbols.txt

.. _exp_mo:

Experiment 5: Interpretation der Ergebnisse von MO Rechnungen
=============================================================

.. contents::

Hintergrund
-----------

In diesem Experiment sollen Sie sich das erste Mal mit Molekularorbital-Berechnungen (MO) auseinander setzen. Ziel des Experiments ist es Sie mit der Vielfalt an Ergebnissen vertraut zu machen, die eine solche Rechnung liefert.


Totale Energie
--------------

Die totale Energie ist der negative Wert der Energie, die benötigt wird um alle Teile (Elektronen und Nukleonen) des Moleküls unendlich weit voneinander zu entfernen.
Deswegen ist die totale Energie auch sehr groß. Sie wird gemessen in Einheiten von Hartree (auch bekannt als `atomare Einheiten`, a.u.) welche durch das Symbol :math:`\mathrm{E}_\mathrm{h}` definiert sind. Es ist nützlich sich noch einmal die Umrechnungsfaktoren in chemisch relevante Einheiten der Energie vor Augen zu führen.

.. math::
  1 \mathrm{E}_\mathrm{h} = 27.2107 \mathrm{eV} = 627.51 \mathrm{kcal/mol} = 2625.5 \mathrm{kJ/mol} = 219474.2 \mathrm{cm}^{-1}

Obwohl es keine gute wissenschaftliche Praktik ist, werden in der quantenchemischen Literatur die Energie und die Energiedifferenz meistens in :math:`\mathrm{kcal/mol}` angegeben (1 :math:`\mathrm{eV}` = 23.06 :math:`\mathrm{kcal/mol}` und 1 :math:`\mathrm{kcal/mol}` = 4.184 :math:`\mathrm{kJ/mol}`).
In der Spektroskopie dominiert die Einheit :math:`\mathrm{cm}^{-1}` (nutzen Sie den Umrechnungsfaktor 1 :math:`\mathrm{eV}` = 8065.73 :math:`\mathrm{cm}^{-1}`).
Es ist keine schlechte Idee mit den Umrechnungen vertraut zu sein.
Als Beispiel, die nichtrelativistische totale Energie des CO Moleküls beträgt etwa -113 :math:`\mathrm{E}_\mathrm{h}` was etwa :math:`\sim` 71000 :math:`\mathrm{kcal/mol}` entspricht. 
Chemisch relevante Energiedifferenzen liegen in der Größenordnung von 1~kJ/mol. 
Dies spiegelt die enorme Aufgabe der Quantenchemie wieder.

.. note::

   In der Quantenchemie müssen wir die Aufgabe bewältigen kleine Energiedifferenzen mit hoher Genauigkeit zu berechnen. Die Genauigkeit muss auf der dritten Nachkommastelle der totalen Energie liegen (gegeben in :math:`\mathrm{E}_\mathrm{h}`)!

Vorteilhaft ist dabei aber, dass wir nicht die totale Energie des Moleküls mit einer Genauigkeit von 1 :math:`\mathrm{kJ/mol}` berechnen müssen.
Wäre das der Fall, so wäre die Quantenchemie ein sehr frustrierendes Forschungsfeld.
Erst in den letzten Jahren ist es möglich geworden solche Genauigkeiten zu erreichen.
Aber auch das nur für sehr kleine Moleküle und mit einem erheblichen Rechenaufwand.
In der Chemie werden immer Energiedifferenzen gemessen und bei Einführung dieser Differenz wird der größte Teil des Fehlers, den wir bei der Berechnung der totalen Energie machen, eliminiert.
Im Detail: Der größte Anteil der totalen Energie kommt von der starken Wechselwirkung zwischen Kern und kernnahen Elektronen.
Für das chemische Verhalten der Moleküle spielen diese Elektronen aber nur eine untergeordnete Rolle.
Dennoch ist das eigentliche Problem der Quantenchemie das erreichen der hohen Genauigkeit.
Dies ist unerlässlich, denn die Energiedifferenzen sind klein im molekularen Verhältnis, aber sie sind dominant für das chemische Verhalten der Moleküle.
Es ist vergleichsweise einfach $\sim$99\% der totalen Energie zu berechnen. 
Schon die Hartree-Fock-Methode ist dazu in der Lage.
Der Fehler ist in chemischen Skalen dennoch riesig.


Orbitalenergien
---------------

In der Hartree-Fock Theorie wird jedem kanonische MO eine spezifische MO Energie zugeordnet.
Unglücklicherweise haben die Orbitalenergien keine `absolute` Bedeutung. 
Sie wurden in die Theorie eingeführt um die Orthonormalität zwischen verschiedenen MO zu gewährleisten.
Dennoch ist es möglich den Orbitalenergien der besetzten Orbitale eine Bedeutung zu geben (Koopman Theorem):

.. note::

   Die Orbitalenergie eines besetzten kanonischen MO entspricht ungefähr der Energie die benötigt wird um ein Elektron von diesem Orbital zu entfernen (`Koopman Theorem`).
   Dies ist vergleichbar mit dem ersten bzw. mit höheren Ionisationspotentialen.

Dieser Ansatz ermöglicht es uns, der negativen Energie des HOMO's (highest occupied MO) dem Ionisationspotential des Moleküls zuzuordnen.
Mehr noch, zeichnet man die Orbitalenergien als vertikale Stricke in ein Diagramm wo die x-Achse den Orbitalenergien entspricht, so kann man daraus ein Photoelektronen Spektrum ableiten. Dies gibt uns einen gute Verbindung zwischen MO Berechnungen und der Spektroskopie. Deswegen werden kanonische Orbitale auch als `spektroskopische Orbitale` bezeichnet.

MO und deren Ladung
-------------------

Anders, als in vielen Fachbüchern behauptet wird, haben Orbitale keine physikalische Bedeutung.
In der Hartree-Fock Theorie beschreibt jedes Orbital die Bewegung eines Elektrons und das Betragsquadrat gibt die Aufenthaltswahrscheinlichkeit wieder.
In diesem Experiment wollen wir uns die Orbitale anschauen und diese nach |pi|- und |sigma|-Orbitalen oder Lone pair klassifizieren.
Die Symmetrie Symbole der Orbitale lassen sich aus der Gruppentheorie folgern (TC II).

.. note::
   
   Zur Erinnerung, kanonische Orbitale transformieren unter der irreduziblen Darstellung der Punktgruppe des Moleküls. Ebenfalls kann die totale Symmetrie des Zustandes von der Symmetrie eines einfach besetzten Orbitals in einer definierten elektronischen Konfiguration bestimmt werden.

   Jede vollständig gefüllte Schale ist totalsymmetrisch. Deswegen haben geschlossenschalige Moleküle einen totalsymmetrischen Grundzustand.


Die totale Ladungsdichte, Momente und Populations Analyse
---------------------------------------------------------

n der Hartree-Fock und DFT Theorie ist die gesamte Elektronendichte gegeben als Summe über die Beiträge der individuellen Orbitale.
Für ein geschlossenschaliges System ist das:

.. math::
  
  \rho (r) = 2 \sum\limits_{i=1}^{N/2} \left| \Psi_i (r) \right|^2

Der Faktor Zwei kommt daher, dass jedes MO zweifach besetzt ist.
Von der gesamt Ladungsdichte ausgehend können verschiedene Momente berechnet werden.
Das wichtigste ist das Dipolmoment, welches der Polarität des Moleküls entspricht.
Das Dipolmoment ist eine Observable.
Es wird aus der Ladungsdichte, den Atompositionen R$_A$ und den Atomaren Ladungen Z$_A$ wie folgt bestimmt:

.. math::
  
  \mu_{dip} = \sum\limits_{A=1}^{M} Z_A R_A - \int \rho (r) r \mathrm{d}r

Das Minuszeichen kommt durch die negative Ladung der Elektronen.
Das Dipolmoment wird in atomaren Einheiten angeben.
Um es in eine (koventionellere) Einheit umzurechnen (Debye) muss das Dipolmoment in a.u. mit 2.541798 multipliziert werden.
Das Dipolmoment ist ein Vektor, welcher vom Schwerpunkt der negativen Ladung des Moleküls auf den Schwerpunkt der positiven Ladung zeigt.

Ein wichtiges Konzept in der Chemie sind partielle Ladungen von Atomen und Molekülen.
Es erscheint unmöglich die gesamte Ladungsdichte so zu zerlegen, dass sie einzelnen Atomen zugeordnet werden kann.
Viele verschiedene Ansätze beschäftigen sich mit diesem Problem.
Alle diese Ansätze werden in der sogenannten `Populationsanalyse` zusammengefasst.
Keiner dieser Ansätze kann eine physikalisch korrekte Antwort geben.
Die Ergebnisse sind mit Vorsicht zu betrachten, können aber einen guten Einblick in die Trends der partiellen Ladung geben.
Deswegen werden in den meisten Programmen auch mehrere Arten der Populationsanalyse im Outputfile angegeben.
ORCA gibt standardmäßig die Mulliken Analyse, die Löwdin Analyse und die Mayer Analyse an.
Im nachfolgenden Abschnitt wollen wir uns den Ursprung der Mulliken Analyse ansehen.
Die Mulliken Populationsanalyse ist, trotz ihrer bekannten Schwächen, Standard in quantechemischen Programmen.
Die Gesamtladungsdichte ist definiert als :math:`\rho (r)` und die gesamte Anzahl der Elektronen ist :math:`N`. Somit haben wir:

.. math::
  
  N = \int \rho (r) \mathrm{d}r

und von der Dichtematrix :math:`P` und den Basisfunktionen :math:`\{ \varphi \}` folgt daraus:

.. math::
  
  \rho (r) = \sum\limits_{\mu \nu} P_{\mu \nu} \varphi_{\mu} (r) \varphi^*_{\nu} (r)

Eingesetzt in :math:`N` ergibt sich:

.. math::
  
  N = \sum\limits_{\mu \nu} P_{\mu \nu} \int \varphi_{\mu} (r) \varphi^*_{\nu} (r) dr = \sum\limits_{\mu \nu} P_{\mu \nu} S_{\nu \mu} = \sum\limits_{\mu} (PS)_{\mu \mu} = \mathrm{tr}PS

N entspricht also genau der Spur der Matrix.
Die Zuordnung, welche Teil der Spur zu welchem Atom gehören ist aber vollkommen willkürlich.


Beschreibung des Experiments
----------------------------

Nehmen Sie die Moleküle die Sie schon in den letzten Experimenten verwendet haben und die entsprechenden Ergebnisse aus den vorherigen Rechnungen (`TPSS-D4/def2-TZVP`).

.. admonition:: 1. Populationsanalyse

   Schauen Sie sich die Ergebnisse der Populationsanalyse an und trage Sie die partiellen Ladungen der Kohlenstoffatome in Methan, Ethan, Ethen, Ethin, Methanol und Kohlenstoffdioxid in die etsprechende folgene Tabelle ein. Stimmen die Ergebnisse mit Ihrer chemischen Intuition überein?

   .. csv-table:: Populationsanalyse der Kohlenstoffatome.
      :header: "Molecule", "Mulliken", "Löwdin", "Oxidationsstufe"
      :widths: 20, 20, 20, 20

      ":math:`\ce{CH4}`", "", "", ""
      ":math:`\ce{C2H6}`", "", "", ""
      ":math:`\ce{C2H4}`", "", "", ""
      ":math:`\ce{C2H2}`", "", "", ""
      ":math:`\ce{H3COH}`", "", "", ""
      ":math:`\ce{CO2}`", "", "", ""

.. admonition:: 2. MO Analyse

   Schauen Sie sich die Grenzorbitale an (Gabedit) und klassifizieren Sie die MOs nach |pi|, :math:`\pi^{\ast}`, |sigma|, :math:`\sigma^{\ast}` oder als Lone pair.


.. admonition:: 3. Orbitalenergien

   Erstellen Sie ein quantitatives MO Schema für Ethen. Geben Sie die Orbitalenergien in eV an. Das Schema soll alle besetzten und die ersten drei unbesetzten MO's enthalten. Finden Sie die irreduziblen Darstellungen für alle MO's und beschriften Sie die MO's entsprechend. Berücksichtigen Sie dabei nur die Molekülorbitale, die einzelnen Atomorbitale müssen nicht berücksichtigt werden.


.. admonition:: 4. Ionisationspotentiale

   Bestimmen Sie das Ionisationspotential nach dem Koopmans' Theorem und vergleichen Sie die Ergebnisse mit den experimentellen Daten aus der folgenden Tabelle.

   .. csv-table:: Experimentelle Dipolmomente und Ionisationspotentiale für kleine Moleküle. 
      :header: "Molecule", "Dipole Moment (Debye)", "Ionization Potential (eV)"
      :widths: 20, 20, 20

      ":math:`\ce{CH4}`", 0.000, "12.61 ± 0.01"
      ":math:`\ce{C2H6}`", 0.000, "11.56 ± 0.02"
      ":math:`\ce{C2H4}`", 0.000, "10.51 ± 0.015"
      ":math:`\ce{C2H2}`", 0.000, "11.41 ± 0.01"
      ":math:`\ce{H3COH}`", 1.700, "10.84 ± 0.07"
      ":math:`\ce{CO2}`", 0.000, "13.778 ± 0.002"
      ":math:`\ce{NH3}`", 1.470, "10.07 ± 0.01"
      ":math:`\ce{H2O}`", 1.850, "12.6188 ±0.0009"

   .. csv-table:: Ionisationspotentiale nach dem Koopman's Theorem in eV.
      :header: "Molekül", "Exp.", "Berechnete Daten", ":math:`\Delta(\mathrm{calc-exp})`"
      :widths: 20, 20, 20, 20

      ":math:`\ce{CH4}`", "12.610", "", ""
      ":math:`\ce{C2H6}`", "11.560", "", ""
      ":math:`\ce{C2H4}`", "10.510", "", ""
      ":math:`\ce{C2H2}`", "11.410", "", ""
      ":math:`\ce{H3COH}`", "10.840", "", ""
      ":math:`\ce{CO2}`", "13.778", "", ""
      ":math:`\ce{NH3}`", "10.070", "", ""
      ":math:`\ce{H2O}`", "12.619", "", ""


.. admonition:: 5. Dipolmomente

   Bestimmen Sie das Dipolmoment, dieses finden Sie am Ende des Outputs und vergleichen Sie die Ergebnisse mit den experimentellen Daten aus der vorherigen Tabelle.

   .. csv-table:: Dipolmoment in Debye.
      :header: "Molekül", "Exp.", "Berechnete Daten", ":math:`\Delta(\mathrm{calc-exp})`"
      :widths: 20, 20, 20, 20

      ":math:`\ce{CH4}`", "0.000", "", ""
      ":math:`\ce{C2H6}`", "0.000", "", ""
      ":math:`\ce{C2H4}`", "0.000", "", ""
      ":math:`\ce{C2H2}`", "0.000", "", ""
      ":math:`\ce{H3COH}`", "1.700", "", ""
      ":math:`\ce{CO2}`", "0.000", "", ""
      ":math:`\ce{NH3}`", "1.470", "", ""
      ":math:`\ce{H2O}`", "1.850", "", ""
