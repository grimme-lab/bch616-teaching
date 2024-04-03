.. include:: symbols.txt

Experiment 9: Solvatationseffekte (CPCM)
======================================

.. contents::

Hintergrund
-----------

Solvatationseffekte spielen in allen Bereichen der Chemie eine wichtige Rolle.
Durch die Solvatation kann es zu Änderungen in der Geometrie und zu Änderungen in den elektrischen und magnetischen Eigenschaften kommen.
Um einen hohen Rechenaufwand zu vermeiden wurde, anstelle von einzelnen Lösungsmittelmolekülen ein implizites Solvatationsmodell gewählt.
Die solvatisierten Moleküle sind dabei von einem dielektrischen Kontinuum umgeben.

Zu den populären Modellen gehört das Conductor-like polarizable continuum model (CPCM).


Beschreibung des Experiments
----------------------------

Teil I: Berechnung der Solvationsenergie für kleine Moleküle
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Berechnen Sie die Solvatationsenergie für die folgenden Moleküle:

- Wasser
- Aceton
- n-Octan
- Benzen
- :math:`\ce{OH^-}`
- :math:`\ce{Cl^-}`

Die Berechnung besteht aus mehreren Schritten:

1. Optimieren Sie die Molekülgeometrie in der Gasphase, nutzten Sie das TPSS Funktional und einen TZVP Basissatz.

.. code-block:: none

   ! TPSS TZVP TightSCF TightOpt

2. Optimieren Sie die Struktur in wässriger Lösung, nutzen Sie dazu das CPCM Modell.

.. code-block:: none

   ! TPSS TZVP CPCM(water) TightSCF TightOpt

3. Tragen Sie die Werte der Solvatationsenergie in eine Tabelle ein.
4. Betrachten Sie die absoluten Werte. Was fällt Ihnen auf?
5. Welche Beiträge fehlen um die freie Energie der Solvatation zu berechnen?

Teil II: Berechnung von Glycin in der Gasphase und in Lösung
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Glycin ist eine der zwanzig natürlich vorkommenden Aminosäuren und die kleinste Aminosäure, welche in Lösung als Zwitterion vorliegt. 
Sie bietet sich daher gut als Testmolekül für das CPCM-Modell an.
Ist es in der Lage Glycin in der zwitterionischen Form zu stabilisieren? Führen Sie die Berechnungen auf TPSS/TZVP Level durch. 

1. Optimieren Sie beide Strukturen (neutrale und zwitterionische Form) von Glycin sowohl in der Gasphase als auch in Wasser. Was fällt auf? Berechnen Sie die Stabilisierungsenergie der neutralen Form in der Gasphase und die der zwitterionischen Form in Lösung. 
2. Variieren Sie die Dielektrizitätskonstante und bestimmen Sie den Wert, an welchem die zwitterionische Form gerade noch stabilisiert wird. Benutzen Sie für die neutrale Form die gasphasenoptimierte Geometrie aus 1. und für die zwitterionische Form ausschließlich die bereits in Wasser optimierte Geometrie. Überlegen Sie dazu zunächst, in welchem Bereich beide Formen gleich stabil sein könnten. Variieren Sie dort die Dielektrizitätskonstante in Schritten von 0.1.

.. code-block:: none

   ! TPSS TZVP TightSCF

   %cpcm		     
      epsilon 80.40 # Dielektrizitaetskonstante Wasser
      refrac   1.33 # Brechungsindex Wasser
   end 		     