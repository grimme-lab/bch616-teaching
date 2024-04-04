.. include:: symbols.txt

.. _exp_mol_bauen:

Experiment 2: Moleküle am Computer bauen
========================================

.. contents::

Hintergrund
-----------
In diesem grundlegenden und einfachen Experiment soll erklärt werden, wie molekulare Strukturen am Computer entworfen werden können.
Dabei sollen diese sowohl mittels "Papier und Stift" als auch mit graphischen Editoren erstellt werden.


Aufruf des ORCA Programms
-------------------------
Um das Programm ORCA aufrufen zu können müssen Sie eine Inputdatei erstellen (z.B. ``meininput.inp``) und dann folgenden Befehl ausführen:

.. code-block:: bash

   orca meininput.inp > meininput.out &

Den Fortschritt der Rechnung können Sie folgendermaßen verfolgen:

.. code-block:: bash

   tail -f meininput.out

Der Befehl lässt sich mit Strg + C wieder beenden.

Der generelle Aufbau einer Inputdatei sieht so aus:

.. code-block:: none

   # Kommentarzeile (ueberall in der Datei moeglich)
   ! Methode Basissatz weitere-Schluesselwoerter

   # Moegliche Input-Blocks starten mit ``%''
   # z.B.:
   %scf
      MaxIter 150 # Maximale Anzahl an Iterationsschritten im SCF 
                  #Standard ist 50
   end

   * xyz Ladung, Multiplizitaet
      Kartesische Koordinaten
   *
   oder:
   * int Ladung, Multiplizitaet
      Z-Matrix
   *

Zu Beachten ist: die Multiplizität ist definiert als `2S+1` wobei `S` der Gesamtspin ist. Für geschlossenschalige Moleküle ist die Multiplizität immer `1`.

Ein Beispiel einer Single-Point-Rechnung für Wasserstoffperoxid (:math:`\ce{H2O2}`), einmmal mit Kartesischen Koordinaten:

.. code-block:: none

   # Optimierung von H2CO
   ! TPSS TZVP TightOpt TightSCF
   ! PrintBasis

   %output
      print[p_mos] 1
   end

   * xyz 0 1
   C   0.000000   0.000000   0.000000
   O   1.200000   0.000000   0.000000
   H  -0.550000   0.952628   0.000000
   H  -0.550000  -0.952628  -0.000000
   *

und einmal mit Z-Matrix:

.. code-block:: none

   # Optimierung von H2CO
   ! TPSS TZVP TightOpt TightSCF
   ! PrintBasis

   %output
      print[p_mos] 1
   end

   * int 0 1
   C  0 0 0  0.00  000.0000  000.0000 
   O  1 0 0  1.34  000.0000  000.0000
   H  1 2 0  1.10  120.0000  000.0000
   H  1 2 3  1.10  120.0000  180.0000
   *

Verwenden Sie bitte, wenn nicht explizit anders gefordert, die Methode *TPSS*, einen *TZVP* Basissatz sowie die Schlüsselwörter *TightOpt* und *TightSCF*.

Für die Darstellung der Orbitale mit Hilfe von Gabedit verwenden Sie bitte die Schlüsselwörter *PrintBasis* und den ``print[p_mos] 1`` Befehl im Output-Block.

.. note::
   :class: warning

   Während der laufenden Rechnung speichert ORCA sehr viele Daten auf der Festplatte.
   Um eine zu große Netzwerklast zu verhindern, sollten alle zukünftigen Rechnungen (ORCA und MSINDO) immer (!) in einem Verzeichnis starten, das sich lokal auf der Festplatte des Rechners befindet.
   Kopieren Sie dazu immer die Inputdatei in ein ``/tmp1/prakX/`` Unterverzeichnis und starten Sie die Rechnung in diesem Verzeichnis.


Schlüsselworte in ORCA
----------------------

Für weitere Informationen über die einzelnen Schlüsselwörter und welche es noch so gibt empfiehlt sich einen Blick in das `ORCA Manual <https://orcaforum.kofo.mpg.de>`_ oder die 
`ORCA Website <https://www.orcasoftware.de/tutorials_orca/>`_ (https://www.orcasoftware.de/tutorials_orca/) oder `Faccts Website <https://www.faccts.de/docs/orca/5.0/tutorials/>`_ (https://www.faccts.de/docs/orca/5.0/tutorials/).

Um nur einen bestimmten Teil eines Moleküls zu optimieren, kann man eine beschränkte (sog. contstraint optimization) Geometrieoptimierung durchführen:

.. code-block:: none

   ! TPSS TZVP TightSCF TightOpt
   %geom
      Constraints # Start Beschraenkungen
         { B 0 1 1.25 C }
         { A 2 0 3 120.0 C }
      end #Ende Constraints-Block
   end

   * int 0 1 
   C   0 0 0  0.0000    0.000    0.00
   O   1 0 0  1.2500    0.000    0.00
   H   1 2 0  1.1075  122.016    0.00
   H   1 2 3  1.1075  122.016  180.00
   *

.. admonition:: Constraints
   :class: shaded

   - **Beschränkung der Bindungslänge**
     
     - Syntax: ``{ B N1 N2 Wert C }``
     - Bedeutung: Beschränkung der Bindungslänge zwischen den Atomen mit den Nummern `N1` und `N2` auf den Wert `C`.

   - **Beschränkung des Bindungswinkels**
     
     - Syntax: ``{ A N1 N2 N1 Wert C }``
     - Bedeutung: Beschränkung des Bindungswinkels um das Atom `N1` zwischen den Atomen `N2` und `N3` auf den Wert `C`.

   - **Beschränkung des Diederwinkels**
     
     - Syntax: ``{ D N1 N2 N3 N4 Wert C }``
     - Bedeutung: Beschränkung des Diederwinkels um das Atom `N2` zwischen den Atomen `N1`, `N3` und `N4` auf den Wert `C`.

   - **Beschränkung der kartesischen Koordinaten**
     
     - Syntax: ``{ C N1 C }``
     - Bedeutung: Beschränkung der kartesischen Koordinaten des Atoms mit der Nummer `N1` auf den Wert `C`.
     - Hinweis: Es kann kein Wert angegeben werden.

   - **Hinweis**

     - Der "Wert" in der Beschränkung ist optional. Wird kein Wert angegeben, so wird der aktuelle Wert aus dem Input genommen und dieser festgehalten. Für die kartesischen Koordinaten kann kein Wert angegeben werden, bei internen Koordinaten hingegen schon.
     - Es wird empfohlen den "Wert" nicht zu weit von der Startstruktur zu entfernen.
     - Es ist möglich ganze Sätze von Koordinaten zu beschränken.



Ein relaxierter Oberflächenscan kann folgendermaßen durchgeführt werden:
In dem folgenden Beispiel wird die Bindungslänge zwischen C und O in 12 äquivalenten Schritten von 1.35 auf 1.10 |angst| reduziert und an jedem Punkt eine beschränkte Geometrieoptimierung durchgeführt.

.. code-block:: none

   ! TPSS TZVP TightSCF TightOpt
   %geom
      Scan
         B 0 1 = 1.35, 1.10, 12
         # Die C-O Bindung wird in 12 Schritten
         # zwischen 1.10 und 1.35 Angstroem gescannt
      end
   end

   * int 0 1 
   C   0 0 0  0.0000    0.000    0.00
   O   1 0 0  1.2500    0.000    0.00
   H   1 2 0  1.1075  122.016    0.00
   H   1 2 3  1.1075  122.016  180.00
   *

Das folgende Beispiel zeigt eine Übergangszustandsrechnung in der bekannt ist, welche Bindung für den Übergangszustand günstig ist.
Diese Bindung wird mit ``TS_Mode{B A1 A2}`` angegeben.  

.. code-block:: none

   ! TPSS SVP TightSCF SlowConv NumFreq
   ! OptTS
   %geom
      Calc_Hess true
      NumHess true
      InHessName "orca.hess"
      TS_Mode {B 0 5} end 
   end

   * xyz -1 1
   C   0.02680541905148      0.04376170728416     -0.14514485601314
   H   1.08243985356433     -0.00438817432505      0.01460672503542
   H  -0.49595504676237      0.96212098485972      0.01463831543019
   H  -0.49593569371790     -0.80993091189900     -0.51950906290707
   Br -0.39934182676539     -0.65205676024535      2.16341018213528
   Cl  0.44142404529964      0.72114079760597     -2.39226002066145
   *

Die Z-Matrix
------------

Ist das zu erstellende Molekül nicht zu groß und komplex, ist es am einfachsten einen manuellen Input zu schreiben, der Bindungsabstände, Bindungswinkel und Diederwinkel enthält.
Die Beschreibung eines Moleküls in dieser Art wird `Z-Matrix` genannt.
Um das Molekül beschreiben zu können benötigen Sie sechs Zahlen: `NA`, `NB`, `NC` sind die Nummern der Atome, mit denen das neue Atom verbunden ist.
Mit `R`, `A` und `D` wird die Bindungslänge, der Bindungswinkel und der Diederwinkel beschrieben. 
Die Definition von `NA`, `NB` und `NC` ist wie folgt:

- `NA`: Das Atom mit dem Abstand `R` zum aktuellen Atom
- `NB`: Das aktuelle Atom schließt mit den Atomen `NA` und `NB` einen Winkel `A` ein.
- `NC`: Das aktuelle Atom hat einen Diederwinkel von `D` mit den Atomen `NA`, `NB` und `NC`. `D` ist der Winkel zwischen dem aktuellen Atom und dem Atom `NC`, wenn entlang der `NA`-`NB` Achse geschaut wird.

Alle Winkel werden in Grad angegeben. Das erste Atom wird immer an den Ursprung ``(0,0,0)`` gesetzt. 
Das zweite Atom wird im Abstand `R` entlang einer Koordinatenachse (z.B. `x`) gesetzt. Die Angabe der Längen erfolgt standardmäßig in |angst|.
Das dritte Atom wird in der `xz`-Ebene gesetzt und alle weiteren Atome benötigen alle sechs oben beschriebenen Parameter.

Das Format für ORCA ist wie folgt:

.. code-block:: none

   * int Ladung Multiplizitaet
   AtomName-1   NA NB NC  R A D
   AtomName-2   NA NB NC  R A D
   *

Als Beispiel der Input von CO:

.. code-block:: none

   * int 0 1
   C   0 0 0   0.0   000.0   000.0
   O   1 0 0   1.2   000.0   000.0
   *



Beschreibung des Experiments
----------------------------

.. admonition:: Z-Matrizen

   Erstellen Sie die Z-Matrizen für folgende Moleküle:

   1. :math:`\text{CH}_4`
   2. :math:`\text{H}_3\text{COH}`
   3. :math:`\text{CO}_2`
   4. :math:`\text{NH}_3`
   5. :math:`\text{H}_2\text{O}`

.. table:: Geometrieparameter für verschiedene Bindungen.

   +--------------------+------------------------+
   | Bindung            | Bindungslänge (|angst|)|
   +====================+========================+
   | :math:`\text{C-C}` | 1.54                   |
   +--------------------+------------------------+
   | :math:`\text{C-O}` | 1.40                   |
   +--------------------+------------------------+
   | :math:`\text{C=O}` | 1.20                   |
   +--------------------+------------------------+
   | :math:`\text{C-H}` | 1.10                   |
   +--------------------+------------------------+
   | :math:`\text{N-H}` | 1.05                   |
   +--------------------+------------------------+
   | :math:`\text{O-H}` | 1.00                   |
   +--------------------+------------------------+
   | Tetraeder Winkel   | 109.4712°              |
   +--------------------+------------------------+

.. table:: Resultierende Z-Matrix für verschiedenen Moleküle.
   :align: center

   +------------------------------+--------------------------------------------------+
   | Moleküle                     | Koordinaten (|angst| und $^{\circ}$)             |
   +==============================+==================================================+
   | :math:`\text{CH}_4`          | C                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +------------------------------+--------------------------------------------------+
   | :math:`\text{H}_3\text{COH}` | C                                                |
   +                              +--------------------------------------------------+
   |                              | O                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +------------------------------+--------------------------------------------------+
   | :math:`\text{CO}_2`          | C                                                |
   +                              +--------------------------------------------------+
   |                              | O                                                |
   +                              +--------------------------------------------------+
   |                              | O                                                |
   +------------------------------+--------------------------------------------------+
   | :math:`\text{NH}_3`          | N                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +------------------------------+--------------------------------------------------+
   | :math:`\text{H}_2\text{O}`   | H                                                |
   +                              +--------------------------------------------------+
   |                              | O                                                |
   +                              +--------------------------------------------------+
   |                              | H                                                |
   +------------------------------+--------------------------------------------------+
