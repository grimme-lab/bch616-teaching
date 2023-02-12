.. include:: symbols.txt

Experiment: Infrarot- und Raman-Spektroskopie
=============================================

.. contents::

Hintergrund
-----------
Mittels Infrarot (IR)- und Raman-Spektroskopie können Schwingungszustände von Molekülen im elektronischen Grundzustand untersucht werden. Dabei sind beide Methoden gegensätzlich was die beobachtbaren Schwingungsmoden angeht. In der IR-Spektroskopie wird das Molekül durch die Absorption elektromagnetischer Strahlung angeregt, in der Raman-Spektroskopie durch den inelastischen Stoß mit Phononen. Damit Schwingungsmoden IR-aktiv sind, muss sich das Dipolmoment wärend der Schwingung verändern. Bei der Raman-Spektroskopie hingegen muss sich die Polarisierbarkeit des Moleküls (zweite Ableitung der Energie nach dem elektrischen Feld) entlang der Schwingungsmode verändern.

Theorie
-------


Beschreibung des Experiments
----------------------------

.. admonition:: 1. Schwingungsspektroskopie an kleinen Molekülen:

    Zunächst sollen die Schwingungspektren der folgenden zweiatomigen Moleküle berechnet werden: CO, HF, ClF, N\ :sub:`2`, HCl und Cl\ :sub:`2` 
    Hier sind genaue experimentelle Referenzmessungen in der Gasphase vorhanden, um die theoretischen Ergebnisse zu testen: 

    +----------------------+--------------------------------------+
    | Molekül              | :math:`\omega_{exp}/`\ cm\ :sup:`-1` |
    +======================+======================================+
    | CO                   | 2170                                 |
    +----------------------+--------------------------------------+
    | HF                   | 4138                                 |
    +----------------------+--------------------------------------+
    | ClF                  | 786                                  |
    +----------------------+--------------------------------------+
    | N\ :sub:`2`          | 2359                                 |
    +----------------------+--------------------------------------+
    | HCl                  | 2991                                 |
    +----------------------+--------------------------------------+
    | Cl\ :sub:`2`         | 560                                  |
    +----------------------+--------------------------------------+

    * Die Frequenzen sollen mit der composite-Methode r\ :sup:`2`-SCAN-3c berechnet werden. Diese nutzt das meta-GGA Dichtefunktional r\ :sup:`2`-SCAN mit D4 Dispersionskorrektur und geometrischer Counter-Poise Korrektur in der modifizierten triple-|zeta| Basissatz mTZVPP. Um die Schwingungen harmonisch zu Näherung muss das Minimum der Potentialhyperfläche (PES) gefunden werden. Um eine möglichst glatte PES zu erhalten, verwenden Sie das große numerische Integrationsgrid ``DEFGRID3`` und sehr enge Konvergenzkriterien für das SCF (``VeryTightSCF``) und die Geometrieoptimierung (``VeryTightOpt``). Optimieren Sie also nun die Geometrien mit r\ :sup:`2`-SCAN-3c. 


    .. code-block:: none   
        :linenos:

        ! R2SCAN-3C VeryTightSCF VeryTightOpt DefGrid3 NORI

    * Bei der Berechnung von Schwingungsfrequenzen in ORCA (``NumFreq``) werden automatisch IR-Intensitäten bestimmt. Um das Raman-Spektrum eines Moleküls zu berechnen, ist es jedoch notwendig die Ableitung der Polarisierbarkeit |alpha| mit Respekt zu den Normalmoden zu kennen (``% elprop Polar true end``). Diese sind verfügbar bei der Kombination einer numerischen Frequenz- und Polarisierbarkeitsrechnung an, bei der automatisch Raman-Intensitäten ausgegeben werden. Die numerischen Frequenzen werden durch Auslenkung entlang der Normalmoden (``Increment``) über die Zentraldifferenz berechnet. 

    Berechnen Sie nun auf den zuvor optimierten Geometrien die Schwingungsfrequenzen, und IR- sowie Raman-Intensitäten mit r\ :sup:`2`-SCAN-3c. Nutzen Sie dafür den folgenden Input: 

    .. code-block:: none   
        :linenos:
        
        ! R2SCAN-3C VeryTightSCF DefGrid3 NORI
        ! NumFreq
        
        %pal
        nprocs 4
        end

        % freq
        Increment 0.02
        end
        
        % elprop
        Polar true
        end

    * Vergleichen Sie zunächst die harmonisch berechneten Frequenzen mit den experimentell gemessenen Frequenzen. Wie verlässlich sind die berechneten Werte? Diskutieren Sie auch die berechneten Trends der IR-Intensitäten von dem Hintergrund der Populationsanalyse und Ihrer quantenchemischen Intuition. Wieso zeigen die homonuklearen Moleküle keine IR-Intensität? 
    
.. admonition:: 2. IR- und Raman-Spektrum von Benzol: 

    Nun soll das Schwingungsfrequenzen auch für ein größeres Molekül berechnet werden. Hierbei steigt die Zahl der Normalmoden für nicht-lineare Moleküle mit :math:`3N-6`. Dadurch werden sowohl die IR- und Raman-Spektren komplexer, als auch die numerische Berechnung der Frequenzen teurer. Dennoch können numerische Frequenzen und Polarisierbarkeiten für kleine Moleküle wie Benzol noch in kurzer Zeit berechnet werden. 

    * Optimieren Sie nun die Geometrie von Benzol. Berechnen Sie anschließend die Schwingungsfrequenzen, IR- und Raman-Intensitäten. Verwenden Sie hierzu erneut die r\ :sup:`2`-SCAN-3c Methode mit den gleichen Einstellung wie in der vorherigen Aufgabe. 
    * Ordnen Sie die berechneten harmonischen Frequenzen den Experimentellen Frequenzen von Benzol zu und bestimmen Sie den Charakter der Schwingung. Visualisieren Sie dazu die Schwingungsfrequenzen mit dem Programm Molen (siehe ???? für eine kurze Einführung). Geben Sie auch eine durchschnittliche und Maximale Abweichungg von den experimentellen Werten an. Experimentelle Frequenzen: 

        * IR: :math:`\omega_{exp}=674, 1037, 1482, 3030-3120\,`\ cm\ :sup:`-1`
        * Raman: :math:`\omega_{exp}=605, 991.6, 1178.0, 1595.0\,`\ cm\ :sup:`-1`

    .. hint::
        Aufgrund der Symmetrie von Benzol sind viele Schwingungsmoden entartet, sodass einigen Frequenzen mehrere Moden zugeordnet werden können. 

    * Plotten Sie auch das berechnet IR-Spektrum mit ``orca_mapspc``. 
    * Wiederholen Sie nun die Optimierung aber nun mit schwächeren Konvergenzkriterien für SCF (``SCF`` statt ``VeryTightSCF``) und Geometrieoptimierung SCF (``OPT`` statt ``VeryTightOpt``), sowie dem kleinerenn numerischen Integrationsgrid ``DEFGRID1``. Vergleichen Sie die berechneten Frequenzen, sowie die benötigte Rechenzeit.  

    .. code-block:: none   
        :linenos:

        ! R2SCAN-3C SCF Opt DefGrid1 NORI

.. admonition:: 3. Schwingungspektroskopie bei Wasserstoffbrückenbindungen: 

    Die Benzoesäure 

