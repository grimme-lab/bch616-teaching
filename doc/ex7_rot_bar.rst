.. include:: symbols.txt

Experiment: Rotationsbarriere von Ethan
=======================================

.. contents::

Hintergrund
-----------

Wie Sie in den organischen Vorlesungen schon gelernt haben ist die C-C Bindung in Ethan bei Raumtemperatur frei drehbar, aber nicht alle Konfigurationen sind gleich stabil. Dieses Experiment soll Ihnen zeigen, dass solche Rotationsbarrieren gut zu berechnen sind und damit auch quantitative Vorhersagen für die Geschwindigkeitskonstante der Rotation möglich sind. 

Beschreibung des Experiments
----------------------------

Beginnen zunächst mit Ethan. Nutzen Sie für alle Rechnungen die r\ :sup:`2`-SCAN-3c composite-Methode, die besonders für relative Energien von Konformeren eine hohe Genauigkeit besitzt. Die Methode verwendet das r\ :sup:`2`-SCAN Dichtefunktional mit D4-Dispersionskorrektur und geometrischer Counter-Poise Korrektur mit dem modifizierten mTZVPP Basissatz.

    1. Erstellen Sie für das Ethan-Molekül eine Z-Matrix. Finden Sie einen H-C-C-H Diederwinkel für die folgende Rotations.

    .. hint::
    
        Orca beginnt bei der Zählung der Atome bei 0.

    2. Führen Sie einen unrelaxierten Oberflächenscan durch. Varriieren Sie dazu den gefunden H-C-C-H Diederwinkel. Nutzen Sie dazu das Schlüsselwort %paras (siehe :numref:`exp_disp`).
    
    3. Führen Sie nun auch einen relaxierten Oberflächenscan entlang des Diederwinkels durch. Nutzen Sie dabei das Schlüsselwort %geom (siehe :numref:`exp_mol_bauen`).
    
    4. Tragen Sie die beiden Potentialkurve für die Rotations um die C-C Bindungsachse auf (Energie gegen Bindungswinkel). Vergleichen Sie die relaxierte und unrelaxierte Barriere. Was kann man generell über die Barriere des unrelaxierten Scans sagen?
    
    5. Vergleichen Sie die erhaltenen Daten für die Rotationsbarriere von Ethan mit experimentellen Werten. Messungen zeigen, dass die Rotationsbarriere für Ethan 1024 cm\ :sup:`-1` oder etwa 12.25 kJ mol\ :sup:`-1` beträgt.

Wie Sie bei diesen Rechnungen bemerken konnten, ist das Scannen der Potentialhyperfläche schon für einen einzigen Freiheitsgrad aufwendig. Im Folgenden soll ein ähnlicher Oberflächenscan jedoch auch für das deutlich größere substituierte 1,2-Diphenylethan durchgeführt werden. Bei solchen aufwendigen Rechnungen bieten sich Multilevel-Workflows an, bei denen der aufwendige Schritt (hier der Scan) mit einer schnellen Methode (hier GFN2-xTB) durchgeführt wird und am Ende nur für die Geometrien von Interesse genaue Energien (hier erneut r\ :sup:`2`-SCAN-3c) bestimmt werden. Dadurch können im Fall eines relaxierten Scans alle Geometrieoptimierung und sogar die meisten Energieberechnungen mit der teuren Methode vermieden werden. Führen Sie also im Folgenden einen solchen relaxierten Multilevel-Oberflächenscan durch: 

    6. Erstellen Sie zunächst die Geometrie von 1,2-Diphenylethan. Es ist nicht nötig die Z-Matrix aufzustellen, da Orca automatisch die Inputgeometrie in interne Koordinaten transformiert. Suchen Sie nur die im C-C-C-C Diederwinkel vorkommenden Atome heraus.

    7. Starten Sie einen relaxierten Oberflächenscan von trans- bis cis-1,2-Diphenylethan mit GFN2-xTB. Ersetzen Sie dafür lediglich Funktional und Basissatz durch das ``GFN2-xTB`` Keyword. 

    8. Tragen Sie die Potentialkurve für den Scan mit GFN2-xTB auf. Bei welchem Diederwinkel treten Minima und Maxima der Potentialkurve auf und wie werden die entsprechenden Konformere bezeichnet? 

    9. Rechnen Sie nun mit r\ :sup:`2`-SCAN-3c die Energien für die zuvor bestimmten Extremumsgeometrien aus. Optimieren Sie zusätzlich die die Extremumsgeometrien mit r\ :sup:`2`-SCAN-3c unter Einschränkung des Diederwinkels nach (``%geom Constraints``). Tragen Sie sowohl die Single-Point- als auch die Energie nach Optimierung mit der er GFN2-xTB Potentialkurve auf. Vergleichen Sie die drei berechneten Werte für die höchste Barrieren. 

Basierend auf der Theorie des Übergangszustands können mit Hilfe der Eyring-Gleichung 

.. math::

    k = \frac{k_{\mathrm{B}}T}{h}\cdot \exp{\left(-\frac{\Delta G^{\ddagger}}{RT}\right)}

auch Geschwindigkeitskonstanten molekularer Prozesse bestimmt werden. Benötigt wird dafür nur die freie Aktivierungsenthalpie :math:`\Delta G^{\ddagger}`, für die in der Gasphase neben der berechneten Energiedifferenz nur noch eine thermostatistische Korrektur benötigt wird. 

    10. Berechnen Sie :math:`\Delta G^{\ddagger}` für den geschwindigkeitsbestimmenden Schritt der Rotation von Ethan und 1,2-Diphenylethan (höchste Barriere), indem Sie für die optimierten Extremumsgeometrien Frequenzrechnung mit r\ :sup:`2`-SCAN-3c (``AnFreq``) durchführen. Geben Sie auch die thermostatistische Korrektur an. Ist dies ein wichtiger Beitrag bei diesem Prozess. 
    
    11. Bestimmen Sie nun die Geschwindigkeitskonstante bei 298K für die Rotation mit Hilfe der Eyring-Gleichung. Laufen die Prozesse bei Raumtemperatur ab? Hätten Sie aus rein sterischer Hinsicht dieses Ergebnis erwartet?



