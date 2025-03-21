.. include:: symbols.txt

.. _exp_rot_bar:

Experiment 7: Rotationsbarriere von Ethan
=========================================

.. contents::

Hintergrund
-----------

Wie Sie in den organischen Vorlesungen schon gelernt haben ist die C-C Bindung in Ethan bei Raumtemperatur frei drehbar, aber nicht alle Konfigurationen sind gleich stabil. Dieses Experiment soll Ihnen zeigen, dass solche Rotationsbarrieren gut zu berechnen sind und damit auch quantitative Vorhersagen für die Geschwindigkeitskonstante der Rotation möglich sind. 

Beschreibung des Experiments
----------------------------

Beginnen zunächst mit Ethan. Nutzen Sie für alle Rechnungen die r\ :sup:`2`-SCAN-3c composite-Methode, die besonders für relative Energien von Konformeren eine hohe Genauigkeit besitzt.
Die Methode verwendet das r\ :sup:`2`-SCAN Dichtefunktional mit `D4` Dispersionskorrektur und geometrischer Counter-Poise Korrektur mit dem modifizierten `def2-mTZVPP` Basissatz.

.. admonition:: Teil I

    1. Erstellen Sie für das Ethan-Molekül eine Z-Matrix. Finden Sie einen H-C-C-H Diederwinkel für die folgende Rotation.

    .. hint::

        Orca beginnt bei der Zählung der Atome bei 0.

    2. Führen Sie einen unrelaxierten Oberflächenscan durch. Varriieren Sie dazu den gefunden H-C-C-H Diederwinkel. Nutzen Sie dazu folgenden Input durch:

    .. code-block:: none
    
          ! r2scan-3c TightSCF
          
          %pal
          nprocs 4
          end
          
          %paras
            ang = 000.0000, 120.0000, 120
          end
          
          *int 0 1
             C 0 0 0 0.00 000.0000 000.0000
             H 1 0 0 1.10 000.0000 000.0000
             H 1 2 0 1.10 109.4712 000.0000
             H 1 3 2 1.10 109.4712 120.0000
             C 1 4 2 1.54 109.4712 120.0000
             H 5 1 2 1.10 109.4712 {ang+180.0000}
             H 5 6 1 1.10 109.4712 120.0000
             H 5 7 1 1.10 109.4712 120.0000
          *

    3. Führen Sie nun auch einen relaxierten Oberflächenscan entlang des Diederwinkels mit folgendem Input durch:

    .. code-block:: none

          ! r2scan-3c TightSCF TightOpt
          
          %pal
          nprocs 4
          end
          
          %geom
            Scan
                d 1 0 4 5 = 180.0000, 300.0000, 120
            end
          end
          
          *int 0 1
          C 0 0 0 0.00 000.0000 000.0000
          H 1 0 0 1.10 000.0000 000.0000
          H 1 2 0 1.10 109.4712 000.0000
          H 1 3 2 1.10 109.4712 120.0000
          C 1 4 2 1.54 109.4712 120.0000
          H 5 1 2 1.10 109.4712 180.0000
          H 5 6 1 1.10 109.4712 120.0000
          H 5 7 1 1.10 109.4712 120.0000
          *

    4. Tragen Sie die beiden Potentialkurve für die Rotation um die C-C Bindungsachse auf (Energie gegen Bindungswinkel). Vergleichen Sie die relaxierte und unrelaxierte Barriere. Was kann man generell über die Barriere des unrelaxierten Scans sagen?

    5. Vergleichen Sie die erhaltenen Daten für die Rotationsbarriere von Ethan mit experimentellen Werten. Messungen zeigen, dass die Rotationsbarriere für Ethan 1024 cm\ :sup:`-1` oder etwa 12.25 kJ mol\ :sup:`-1` beträgt.

Wie Sie bei diesen Rechnungen bemerken konnten, ist das Scannen der Potentialhyperfläche schon für einen einzigen Freiheitsgrad aufwendig.
Im Folgenden soll ein ähnlicher Oberflächenscan jedoch auch für das deutlich größere substituierte 1,2-Diphenylethan durchgeführt werden.
Gegeben ist die Geometrie für die trans-Konformation (in xyz). Kopieren sie die Struktur in eine Datei und speichern Sie diese als ``xyz`` Datei (bpsw. als  ``struc.xyz``).

.. code-block:: none

      28
      
      C  0.4479   -0.0177    0.6475
      C -0.4429   -0.0175   -0.6108
      C  1.9236   -0.0068    0.3310
      C -1.9057   -0.0069   -0.3199
      C  2.5956   -1.2100    0.1824
      C -2.5973   -1.2099   -0.1781
      C  2.5805    1.2060    0.1942
      C -2.5821    1.2061   -0.1892
      C  3.9594   -1.2001   -0.1102
      C -3.9653   -1.2001    0.0942
      C  3.9444    1.2158   -0.0986
      C -3.9501    1.2158    0.0832
      C  4.6337    0.0127   -0.2507
      C -4.6417    0.0127    0.2248
      H  0.2152   -0.8934    1.2684
      H  0.2055    0.8502    1.2758
      H -0.2014   -0.8912   -1.2316
      H -0.1918    0.8486   -1.2385
      H  2.0785   -2.1594    0.2878
      H -2.0813   -2.1615   -0.2753
      H  2.0516    2.1479    0.3087
      H -2.0542    2.1502   -0.2951
      H  4.4961   -2.1367   -0.2292
      H -4.5038   -2.1368    0.2051
      H  4.4695    2.1601   -0.2087
      H -4.4768    2.1600    0.1857
      H  5.6955    0.0204   -0.4789
      H -5.7068    0.0204    0.4372

Bei solchen aufwendigen Rechnungen bieten sich Multilevel-Workflows an, bei denen der aufwendige Schritt (hier der Scan) mit einer schnellen Methode (hier GFN2-xTB) durchgeführt wird und am Ende nur für die Geometrien von Interesse genaue Energien (hier erneut r\ :sup:`2`-SCAN-3c) bestimmt werden
Dadurch können im Fall eines relaxierten Scans alle Geometrieoptimierung und sogar die meisten Energieberechnungen mit der teuren Methode vermieden werden.
Führen Sie also im Folgenden einen solchen relaxierten Multilevel-Oberflächenscan durch: 

.. admonition:: Teil II

    1. Erstellen Sie einen ORCA-Input mit der gegebenen Geometrie von trans-1,2-Diphenylethan.

    2. Starten Sie einen relaxierten Oberflächenscan von trans- bis cis-1,2-Diphenylethan mit GFN2-xTB mithilfe des folgenden Inputs:

    .. code-block:: none
    
          ! GFN2-xTB TightOpt
          
          %pal
          nprocs 4
          end
          
          %geom
            Scan
                d 3 1 0 2 = 180.0000, 000.0000, 90
            end
          end
          
          * xyzfile 0 1 struc.xyz 

    3. Tragen Sie die Potentialkurve für den Scan mit GFN2-xTB auf. Bei welchem Diederwinkel treten Minima und Maxima der Potentialkurve auf und wie werden die entsprechenden Konformere bezeichnet? 

    4. Rechnen Sie nun mit r\ :sup:`2`-SCAN-3c die Energien für die zuvor bestimmten Extremumsgeometrien aus (Tipp: Diederwinkel 0°, 60°, 120°, 180°). Optimieren Sie zusätzlich die die Extremumsgeometrien mit r\ :sup:`2`-SCAN-3c unter Einschränkung des Diederwinkels nach. Tragen Sie sowohl die Single-Point- als auch die Energie nach Optimierung mit der er GFN2-xTB Potentialkurve auf. Vergleichen Sie die drei berechneten Werte für die höchste Barrieren. 

 .. code-block:: none
    
          ! R2SCAN-3c TightSCF TightOpt
          
          %pal
          nprocs 4
          end
          
          * xyzfile 0 1 struc.xyz 

.. hint::

    Mit der Zeile ``* xyzfile 0 1 struc.xyz`` im ORCA Input verweisen Sie dabei auf die ``.xyz`` Datei, in der Sie vorher die Struktur gespeichert haben (Diese muss sich immer im selben Ordner       befinden!).

Basierend auf der Theorie des Übergangszustands können mit Hilfe der Eyring-Gleichung 

.. math::

    k = \frac{k_{\mathrm{B}}T}{h}\cdot \exp{\left(-\frac{\Delta G^{\ddagger}}{RT}\right)}

auch Geschwindigkeitskonstanten molekularer Prozesse bestimmt werden. Benötigt wird dafür nur die freie Aktivierungsenthalpie :math:`\Delta G^{\ddagger}`, für die in der Gasphase neben der berechneten Energiedifferenz nur noch eine thermostatistische Korrektur benötigt wird. 

.. admonition:: Teil III

    1. Berechnen Sie :math:`\Delta G^{\ddagger}` für den geschwindigkeitsbestimmenden Schritt der Rotation von Ethan und 1,2-Diphenylethan (höchste Barriere), indem Sie für die optimierten Extremumsgeometrien Frequenzrechnung mit r\ :sup:`2`-SCAN-3c (``AnFreq``) durchführen. Geben Sie auch die thermostatistische Korrektur an. Ist dies ein wichtiger Beitrag bei diesem Prozess. 

    2. Bestimmen Sie nun die Geschwindigkeitskonstante bei 298K für die Rotation mit Hilfe der Eyring-Gleichung. Laufen die Prozesse bei Raumtemperatur ab? Hätten Sie aus rein sterischer Hinsicht dieses Ergebnis erwartet?



