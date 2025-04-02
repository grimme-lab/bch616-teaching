.. include:: symbols.txt

.. _exp_ir_raman:

Experiment 11: Infrarot- und Raman-Spektroskopie
================================================

.. contents::

Hintergrund
-----------
Infrarot- und Raman-Spektroskopie sind Formen der Schwingungsspektroskopie und basieren auf Übergängen zwischen den quantisierten Schwingungszuständen eines Moleküls. Mit quantenchemischen Methoden können sowohl die Schwingungsfrequenzen der verschiedenen Schwingungsmoden, als auch deren Übergangswahrscheinlichkeiten (Intensitäten) bei IR- und Raman-Spektroskopie berechnet werden. Ziel dieses Experiment ist die Vorhersage von Schwingungspektren bei zunehmend komplexeren Molekülen. 

Schwingungsfrequenzen
---------------------
Bei Molekülschwingungen handelt es sich um eine Bewegungen der Atomkerne relativ zu einander. Hier kann erneut die (sehr gute) Born-Oppenheimer Näherung (Elektronen folgen den Kernen instantan) getroffen werde, um die Bewegung von Kernen und Elektronen zu separieren. Die Potentialhyperfläche :math:`E(\vec{R})` ist dann ausschließlich von den Kernkoordinaten :math:`\vec{R}` abhängig und kann, wie auch schon für die Geometrieoptimierung, als Taylorreihe um die aktuelle Geometrie :math:`\vec{R}_{0}` entwickelt werden (siehe Gleichung :eq:`eq-geom-opt-minimum` in :ref:`sec-geom-opt-minimum`).  Die Reihenentwicklung wird für gewöhnlich nach der zweiten Ordnung abgebrochen. Zusätzlich der Term erster Ordnung fällt weg, wenn die Geometrie :math:`\vec{R}_{0}` vor der Frequenzberechnung optimiert wurde (Gradient :math:`\vec{g}(R_{0})=0`). In diesem Modell verhält sich die Energie

.. math:: 

    \Delta E = E(\vec{R}) - E(\vec{R}_{0}) = (\vec{R} - \vec{R}_{0})^T \mathbf{H}(R_{0})(\vec{R} - \vec{R}_{0})


bei der Auslenkung von :math:`\vec{R}_{0}` nach :math:`\vec{R}` entlang einer Schwingungsmode dem harmonischen Oszillator entsprechend quadratisch (mit den höheren Termen kann auch die Anharmonizität der Schwingungen berücksichtigt werden). Der direkte Vergleich mit dem harmonischen Oszillator

.. math:: 

    \Delta E_{\mathrm{harm. Osz.}}(\vec{R} - \vec{R}_{0}) = \frac{1}{2}m\omega^2 \cdot (\vec{R} - \vec{R}_{0})^2

zeigt die Verbindung zwischen den harmonischen Schwingungsfrequenzen |omega| und der Hessematrix :math:`\mathbf{H}`. Explizit sind die Eigenwerte :math:`\varepsilon_{i}` der massengewichteten Hessematrix

.. math:: 

    F_{ij} \equiv \frac{1}{\sqrt{M_{i}M_{j}}} H_{ij}= \frac{1}{\sqrt{M_{i}M_{j}}}\left(\left.\frac{\partial^2 E}{\partial R_{i}\partial R_{j}}\right|_{\vec{R}=\vec{R}_{0}}\right)

mit den atomaren Massen :math:`M_{j}` und den Einträgen der Hessematrix :math:`H_{ij}` proportional zum Quadrat der harmonischen Frequenzen :math:`\nu_{i}`. Die harmonischen Frequenzen :math:`\nu_{i}` sind im Allgemeinen reell, können aber auch imaginär werden, wenn der gefundene stationäre Punkt bei der Geometrieoptimierung ein Sattelpunkt und kein Minimum ist (oder die Optimierung nicht vollständig konvergiert ist). Die Eigenvektoren von :math:`F_{ij}` entsprechen den massengewichteten Normalkoordinaten :math:`\vec{q}` entlang derer die verschiedenen Schwingungen verlaufen. Die Normalmoden sind folglich Linearkombinationen aus allen möglichen Schwingungen einzelner Atompaare und beinhalten das gesamte Molekül. 

Für Standardmethoden wie Hartree-Fock und DFT ist die Hessematrix :math:`\mathbf{H}` als geschlossener analytischer Ausdruck implementiert, was deren (immer noch teure) Berechnung beschleunigt. Abgesehen von einer analytischen Implementierung kann die Hessematrix aber auch numerisch durch Ableitung des Gradient :math:`\vec{g}` bestimmt werden: 

.. math:: 

    H_{ij}=\frac{g_{i}(\vec{R}+\Delta R_{j})-g_{i}(\vec{R}-\Delta R_{j})}{2\cdot \Delta R_{j} }


Intensitäten
------------
Neben den Schwingungsfrequenzen sind auch die Intensitäten notwendig, um ein IR- oder Ramam-Spektrum aufzutragen. Bei der IR-Spektroskopie wird das Molekül durch Absorption eines Photons im infraroten Bereich des Spektrums aus dem Schwingungsgrundzustand angeregt. Dabei koppelt das elektromagnetische Feld an die Änderung des Dipolmoments :math:`\vec{\mu}` (erste Ableitung der Energie nach dem elektrischen Feld :math:`\vec{E}`) entland der Normalkoordinate :math:`\vec{q}`. Es gilt unter Annahme der harmonischen Näherung:

.. math:: 

    \mathrm{IR-Int.} \propto \left(\frac{\partial\vec{\mu}}{\partial\vec{q}}\right)^2 \propto \left(\frac{\partial^{2} E}{\partial \vec{R} \partial \vec{E}}\right)^2  

Die Raman-Spektroskopie hingegen basiert auf der inelastischen Streuung eines Photons aus dem optischen Bereich des Spektrums (monochromatische Laserstrahlung) am Molekül und dem daraus folgenden spektralen Shift der Streustrahlung. Dabei ist für die inelastische Streuung eine Änderung der Polarisierbarkeit :math:`\vec{\alpha}` (zweite Ableitung der Energie nach dem elektrischen Feld) des Moleküls entlang der Normalmode erforderlich. In harmonischer Näherung gilt dann

.. math:: 

    \mathrm{Raman-Int.} \propto \left(\frac{\partial\stackrel{\leftrightarrow}{\alpha}}{\partial\vec{q}}\right)^2 \propto \left(\frac{\partial^{3} E}{\partial \vec{R} \partial \vec{E}^2}\right)^2. 

Durch die Abhängigkeit von der Änderung des Dipolmoments für IR- und der Polarisierbarkeit für Raman-Spektroskopie ergeben sich entgegengesetzte Auswahlregeln. Welche Schwingungen IR- und welche Raman-aktiv sind, lässt sich dabei anhand von gruppentheoretischen Überlegungen bestimmen. 


Beschreibung des Experiments
----------------------------

.. admonition:: 1. Schwingungsspektroskopie an kleinen Molekülen:

    Zunächst sollen die Schwingungsspektren der folgenden zweiatomigen Moleküle berechnet werden: CO, HF, ClF, N\ :sub:`2`, HCl und Cl\ :sub:`2`. 
    Als Referenz sind hier genaue experimentelle Referenzmessungen in der Gasphase vorhanden. Das Testen von theoretischen Methoden gegen experimentelle (oder theoretische) Referenzwerte hoher Genauigkeit wird als "Benchmarking" bezeichnet und ist ein essentieller Schritt bei der Auswahl einer geeigneten Methode für eine theoretische Studie.  

    +----------------------+----------------------------------------------------+
    | Molekül              | :math:`\tilde{\nu}_{\mathrm{exp}}/`\ cm\ :sup:`-1` |
    +======================+====================================================+
    | CO                   | 2170                                               |
    +----------------------+----------------------------------------------------+
    | HF                   | 4138                                               |
    +----------------------+----------------------------------------------------+
    | ClF                  | 786                                                |
    +----------------------+----------------------------------------------------+
    | N\ :sub:`2`          | 2359                                               |
    +----------------------+----------------------------------------------------+
    | HCl                  | 2991                                               |
    +----------------------+----------------------------------------------------+
    | Cl\ :sub:`2`         | 560                                                |
    +----------------------+----------------------------------------------------+

    Die Frequenzen sollen mit der composite-Methode r\ :sup:`2`-SCAN-3c berechnet werden. Diese nutzt das meta-GGA Dichtefunktional r\ :sup:`2`-SCAN mit der D4 Dispersionskorrektur und der geometrischen Counter-Poise Korrektur in der modifizierten triple-|zeta| Basissatz def2-mTZVPP. Folgen Sie zur Berechnung der Schwingungsspektren mit r\ :sup:`2`-SCAN-3c den folgenden Schritten:  

    1. Damit die harmonisch Näherung angenommen werden kann, muss zunächst das Minimum der Potentialhyperfläche (PES) gefunden werden. Um eine möglichst glatte PES zu erhalten, verwenden Sie das große numerische Integrationsgrid ``DEFGRID3`` und sehr enge Konvergenzkriterien für das SCF (``VeryTightSCF``). Gleiches gilt auch für die Konvergenz der Geometrieoptimierung (``VeryTightOpt``), um imaginäre Moden bei der Frequenzrechnung zu vermeiden. Optimieren Sie nun die Geometrien mit r\ :sup:`2`-SCAN-3c und den angegebenen Einstellungen: 

    .. code-block:: none  

        ! R2SCAN-3C VeryTightSCF VeryTightOpt DefGrid3

        %pal
        nprocs 4
        end

        * xyzfile 0 1 struc.xyz

    2. Bei der Berechnung von Schwingungsfrequenzen in ORCA werden IR-Intensitäten automatisch bestimmt. Für Raman-Aktivitäten werden hingegen die Polarisierbarkeit |alpha| entlang der Normalmoden benötigt, die in ORCA explizit angeforder werden muss (``% elprop Polar true end``). Dies ist in ORCA nicht möglich mit einer analytischen Hessematrix und erfordert eine numerische Frequenzrechnung (``NumFreq``). Berechnen Sie nun für die zuvor optimierten Geometrien die numerischen Schwingungsfrequenzen und IR- sowie Raman-Intensitäten mit r\ :sup:`2`-SCAN-3c in den selben Einstellungen wie zuvor: 

    .. code-block:: none

        ! R2SCAN-3C VeryTightSCF DefGrid3
        ! NumFreq
        
        % elprop
        Polar true
        end
        
        %pal
        nprocs 4
        end
        
        * xyzfile 0 1 struc.xyz

    3. Vergleichen Sie zunächst die harmonisch berechneten Frequenzen mit den experimentell gemessenen Frequenzen. Wie verlässlich sind die berechneten Werte? Diskutieren Sie auch die berechneten Trends der IR-Intensitäten von dem Hintergrund Ihrer quantenchemischen Intuition und Ihres Kenntnis des harmonischen Oszillators. Wieso zeigen die homonuklearen Moleküle keine IR-Intensität? 
    


.. admonition:: 2. IR- und Raman-Spektrum von Benzol: 

    Nun soll das Schwingungsspektrum auch für Benzol berechnet werden. Hierbei steigt die Zahl der Normalmoden für nicht-lineare Moleküle mit :math:`3N-6`. Dadurch werden sowohl die IR- und Raman-Spektren komplexer, als auch die numerische Berechnung der Frequenzen teurer. Dennoch können numerische Frequenzen und Polarisierbarkeiten für kleine Moleküle wie Benzol noch in kurzer Zeit berechnet werden. 

    1. Optimieren Sie die Geometrie von Benzol. Berechnen Sie anschließend die Schwingungsfrequenzen, IR- und Raman-Intensitäten. Verwenden Sie hierzu erneut die r\ :sup:`2`-SCAN-3c Methode mit den gleichen Einstellung wie in der vorherigen Aufgabe  (Die Rechnung dauert ca. 30 min!). 

    2. Ordnen Sie nun die berechneten den experimentellen Frequenzen von Benzol zu. Bestimmen Die auch den Charakter der Schwingung (sym/anti-CH-Streckschwinung, CH-Deformationsschwingung oder Ringschwingung). Visualisieren Sie dazu die Schwingungsmoden mit dem Programm Molden (siehe :ref:`app-molden` für eine kurze Einführung). Experimentelle Frequenzen:

    +------+---------+---------+
    | IR   | Raman   | inaktiv |
    +======+=========+=========+
    | 410  | 	     |         |
    +------+---------+---------+
    |      | 605.6   | 	       |
    +------+---------+---------+
    | 673  | 	     |         |
    +------+---------+---------+
    |      |         | 703     |
    +------+---------+---------+
    |      | 848.9   | 	       |
    +------+---------+---------+
    | 975  | 	     |         |
    +------+---------+---------+
    |      | 992     |         |
    +------+---------+---------+
    | 1038 | 	     |         |
    +------+---------+---------+
    |      |         |  1150   |
    +------+---------+---------+
    |      | 1178    |         |
    +------+---------+---------+
    |      |         | 1310    |
    +------+---------+---------+
    |      |         | 1326    |
    +------+---------+---------+
    | 1486 | 	     |         |
    +------+---------+---------+
    |      | 1596    |         |
    +------+---------+---------+
    |      | 	     | 3068    |
    +------+---------+---------+
    |      | 3047    |         |
    +------+---------+---------+
    | 3063 | 	     |         |
    +------+---------+---------+
    |      | 3062    |         |
    +------+---------+---------+
      
    .. hint::

        Aufgrund der Symmetrie von Benzol sind viele Schwingungsmoden entartet, sodass einigen Frequenzen mehrere Moden zugeordnet werden können  (siehe den NIST-Eintrag für Benzol). Zusätzlich sind die angegebenen experimentellen Frequenzen nicht vollständig, sodass nicht alle berechneten Moden zugeordnet werden können.

    3. Geben Sie eine durchschnittliche und maximale absolute Abweichung der berechneten Frequenzen von den experimentellen Referenzwerten an.

    4. Plotten Sie auch das berechnet IR-Spektrum mit ``orca_mapspc`` (siehe :ref:`app-orca_mapspc` für eine kurze Einführung). :numref:`fig_benzene_IR` zeigt ein experimentelles Referenzspektrum gemessen in der Gasphase.


    .. _fig_benzene_IR:
    
    .. figure:: img/benzeneIRneu.png
        :width: 400px

        Experimentelles IR-Spektrum von Benzol in der Gasphase.


.. _fig_benzoic_IR_gas:
    
.. admonition:: 3. Schwingungspektroskopie bei Wasserstoffbrückenbindungen: 

    Abschließend soll nun auch eine chemische Fragestellung mit der theoretischen Schwingungsspektroskopie beantwortet werden. Dabei ist das Testsystem die Benzoesäure, die über zwei Wasserstoffbrückenbindungen verbrückt auch als Dimer vorliegen kann. 
    
    1. Berechnen Sie zunächst die Schwingungsspektren der Benzoesäure als Monomer in der Gasphase. Optimieren Sie die Struktur dafür zuerst wie in den vorherigen Aufgaben. Plotten Sie die beiden berechneten Spektren erneut mit ``orca_mapspc``. Input für die Frequenzrechnung:

    .. code-block:: none

        ! R2SCAN-3C VeryTightSCF DefGrid3
        ! AnFreq
        
        %pal
        nprocs 4
        end
        
         * xyzfile 0 1 geom.xyz

    2. Berechnen Sie die Schwingungsspektren auch in CCl\ :sub:`4`. Nutzen Sie dafür denselben Input wie zuvor für die Optimierung, wobei Sie den Block ``%cpcm`` einfügen (siehe Frequenzinput), der Input für die Frequenzrechnung sieht wie folgt aus:

    .. code-block:: none

        ! R2SCAN-3C VeryTightSCF DefGrid3
        ! AnFreq
        ! SMD(CCl4)

        %pal
        nprocs 4
        end
        
         * xyzfile 0 1 geom.xyz

    3. In :numref:`table-spec` ist das experimentelle IR-Spektrum von Benzoesäure in Gasphase (links) und in einer 2%-igen CCl\ :sub:`4` Lösung (rechts) abgebildet. [#]_ Vergleichen Sie diese mit den berechneten Spektren. Können Sie eine Aussage über das Vorliegen des Benzoesäure Monomers und Dimers machen? An welchen Banden machen Sie dies fest?

    .. |pic1| image:: img/benzoic-acid_gas.png
        :scale: 35%

    .. |pic2| image:: img/benzoic-acid_solv.png
        :scale: 35%

    .. _table-spec:

    .. table:: IR-Spektren von Benozesäure in der Gasphase (links) und in 2%-igen CCl\ :sub:`4` Lösung (rechts).

        +---------+---------+
        | |pic1|  | |pic2|  |
        +---------+---------+


    4. Mithilfe der sehr effizienten GFN2-xTB Methode, soll nun auch das Gasphasen IR-Spektrum des Benzoesäuredimers berechnet werden. Dafür wird auch das Dimer optimiert und dann dessen Frequenzen berechnet. Optimieren Sie dafür zunäcsht folgende Dimer Struktur mithilfe von GFN2-xTB (über das ``xtb`` Programm): 

    .. code-block:: none

        30
        Coordinates from ORCA-job orca
          O   4.08361963686171      1.42100218491426     -0.00000073226728
          O   1.83133921050916      1.51376110969457     -0.00000053756247
          C   2.89118961455814     -0.61275126220347     -0.00000015830084
          C   1.66786596921808     -1.28923217083174      0.00000005650774
          C   4.08873266661149     -1.33464374377284     -0.00000003849925
          C   1.64337277394040     -2.67695964944375      0.00000040139691
          C   4.05781228404398     -2.72342243751457      0.00000031385609
          C   2.83755368068430     -3.39501341473763      0.00000053723225
          C   2.88427383486136      0.86920719639148     -0.00000049420274
          H   0.75047050342712     -0.71148827584570     -0.00000005200708
          H   5.03274509066108     -0.80298251176861     -0.00000021712756
          H   0.69345649532693     -3.20143513223073      0.00000056800684
          H   4.98681514348201     -3.28415658889913      0.00000041400331
          H   2.81696772552290     -4.48033640386284      0.00000081338830
          H   4.00016402380650      2.42784908552584     -0.00000094507038
          O   1.67544949026866      4.13087276718472     -0.00000067484339
          O   3.92772992055675      4.03811393489232     -0.00000056319142
          C   2.86787941980673      6.16462626264076     -0.00000012977032
          C   4.09120303233605      6.84110723503027      0.00000008450553
          C   1.67033633312375      6.88651868255242     -0.00000002372187
          C   4.11569615382849      8.22883471528941      0.00000040502321
          C   1.70125664287554      8.27529737658171      0.00000030086711
          C   2.92151520995280      8.94688841795884      0.00000051914385
          C   2.87479526761332      4.68266780421806     -0.00000047595502
          H   5.00859853276044      6.26336339406959     -0.00000000626668
          H   0.72632393627822      6.35485740291696     -0.00000019498359
          H   5.06561240572427      8.75331024546315      0.00000056989514
          H   0.77225375376621      8.83603147964344      0.00000038541034
          H   2.94210110784763     10.03221140797559      0.00000077470791
          H   1.75890513974578      3.12402588816740     -0.00000090017462

    In der Kommandozeile müssen sie dafür folgendes eingeben (in ``struc.xyz`` sollte die obere Struktur gespeichert sein):

    .. code-block:: none

        xtb struc.xyz --opt vtight > xtb.out

    Die optimierte Struktur befindet sich nun in ``xtbopt.xyz``. (Mit ``molden xtbopt.log`` können sie wie gehabt die Optimierung visualisieren)

    5. Berechnen Sie nun die IR-Frequenzen mit GFN2-xTB + PTB, indem Sie die optimierte Geometrie in einen neuen Ordner kopieren und folgendes eingeben:

    .. code-block:: none

        xtb xtbopt.xyz --ptb --hess > xtb.out

    Die IR-Frequenzen befinden sich in der Datei ``vibspectrum``.

    6. Abschließend nutzen Sie folgenden Befehl um die IR-aktiven Moden aus dem ``vibspectrum`` in eine Daten Datei zu schreiben:

    .. code-block:: none

        nsm vibspectrum --plot --range 0.0 4000.0  

    Plotten Sie nun die erstelle ``plot.dat`` Datei mithilfe eines geeigneten Programms (Gnuplot, Excel, Libreofficecalc, ...) 
    Wie unterscheiden sich die berechneten IR-Spektren des Monomers und des Dimers in Gasphase?

    .. hint::

      Im Dimer treten aufgrund der zwei enthaltenen Monomere die Moden zweifach auf. Diese können aber auch Kombinationsmoden sein und müssen nicht entartet sein. 


    Wasserstoffbrückenbindungen sind ein wichtiges Phänomen, beispielsweise für die Lösungsmitteleigenschaften von Wasser und das Benzoesäuredimer zeigt deren substantiellen Einfluss auf das IR-Spektrum. Das wirft für die Modellierung von IR-Spektren in protischen Lösungsmitteln wie Wasser die Frage auf, ob die häufig verwendeten impliziten Lösungsmittelmodel wie CPCM ausreichen. Dazu soll im Folgenden der Effekt von weiteren umgebenden Benzoesäuremolekülen auf die Schwingungsfrequenzen implizit modelliert werden. 

    7. Modellieren Sie also nun ein Benzoesäuremonomer in der Umgebung von Benzoesäure mit dem impliziten Lösungsmittelmodel CPCM. Setzen Sie dafür die Dielektrizitätskonstante :math:`\varepsilon_0=8.94` der Wert von Benzoesäure. [#]_ Nutzen Sie dafür wieder ORCA und die Inputs aus Punkt 2 dieser Aufgabe., wobei Sie den ``%cpcm`` Block in der Inputdatei für die Optimierung und Frequenzrechnung wie folgt anpassen: 

    .. code-block:: none   
        :linenos:

        %cpcm 
        epsilon 8.94
        end


    8. Beeinflusst das Kontinuumsmodell die Schwingungsfrequenzen der Benzoesäure in gleichem Maße wie im Benzoesäuredimer? Achten Sie dabei besonders auf die OH-Streckschwingung. Was bedeutet dies für die Anwendung von impliziten Lösungsmittelmodellen bei protischen Lösungsmitteln wie beispielsweise Wasser?


.. [#] Coblentz Society, Inc., "Evaluated Infrared Reference Spectra" in NIST Chemistry WebBook, NIST Standard Reference Database Number 69, Eds. P.J. Linstrom and W.G. Mallard, National Institute of   Standards and Technology, Gaithersburg MD, 20899, https://doi.org/10.18434/T4D303, (retrieved February 25, 2023). 

.. [#] J. Chem. Educ. 2019, 96, 1760-1766

.. [#] Journal of Molecular Liquids, Volume 108, Issues 1–3, November 2003, Pages 119-133


