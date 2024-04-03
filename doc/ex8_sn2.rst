.. include:: symbols.txt

.. _exp_TS:

Experiment 8: Reaktionsmechanismen und Übergangszustände
======================================================

.. contents::

Hintergrund
-----------

Das Aufstellen von Reaktionsmechanismen für den Ablauf chemischer Reaktionen ist besonders für das Verständnis in der Organischen Chemie essentiell. In diesem Experiment sollen Sie mit den Techniken vertraut gemacht werden, die nötig sind, um Reaktionsmechanismen mittels theoretischen Rechnungen vorhersagen und aufklären zu können. Dabei sollen Sie auch einen ersten Einblick in die feineren Unterschiede verschiedener Dichtefunktionalen erhalten. 

Übergangszustände
-----------------
Chemische Reaktionen stellen Wege zwischen verschiedenen (lokalen) Minima der Potentialhyperfläche dar. Auf dem Weg zwischen zwei solchen Minima durchläuft das System einen Übergangszustand an dem die Energie entlang des Reaktionspfads maximal wird. Da auch während einer chemischen Reaktion das System soweit möglich im energetisch niedrigsten Zustand verbleibt, ist der Übergangszustand allgemein nur ein Maximum bezüglich der Bewegung entlang der Reaktionskoordinate und ein Minimum für alle anderen Freiheitsgrade. Es handelt sich also um einen Sattelpunkt erster Ordnung. Hier verschwindet, wie für ein lokales Minimum, der Gradient der Energie, aber die Hessematrix (zweite Ableitung der Energie nach der Koordinaten) hat nun einen negativen Eigenwert (entspricht einer imaginären Frequenz, siehe :numref:`exp_ir_raman`). Die Optimierung der Übergangsgeometrie ist im Vergleich zur Optimierung der Gleichgewichtsgeometrie komplexer, da die Energie gleichzeitig für eine Normalkoordinate maximiert und für alle anderen minimiert werden muss. Dabei kann es leicht dazu kommen, dass die Optimierung in eines der angrenzenden Minima führt. Deshalb erfordert die Übergangszustandsuche eine gewisse Chemische Intuition, um eine Ausgangsgeometrie nah am Übergangszustand zu finden. 

Neben technischen Problemen beim Finden des Übergangszustands, stellt dessen Beschreibung auch eine große Herausforderung für quantenchemische Methoden dar. So sind hier häufiger die Effekte durch die korrelierte Bewegung der Elektronen wichtig sein, die durch mean-field Methoden wie Hartree-Fock oder Kohn-Sham Dichtefunktionaltheorie nur schwer beschrieben werden können. Aber auch wenn HF und DFT formell anwendbar sind, kann es zu großen Unterschieden zwischen verschiedenen Dichtefunktionalen kommen. Reine (meta-)GGA Dichtefunktionalen (z.B.: PBE oder r\ :sup:`2`-SCAN) führen allgemein zu stärkerer Delokalisation der Elektronendichte aufgrund des Selbstinteraktionsfehlers von DFT, während Hartree-Fock durch fehlende Elektronenkorrelation die Elektronendichte zu stark lokalisiert. Da Übergangszustände energetische Maxima entlang des Reaktionspfades sind, haben sie auch eine eine delokalisiertere Elektronendichte, wodurch Barrieren mir reinem DFT zu niedrig und mit Hartree-Fock zu hoch liegen. Die Mischung von beiden in Hybrid-Dichtefunktionale (z.B.: PBE0, B3LYP, |omega|\ B97X-V) kann Ergebnis deutlich verbessern, jedoch besteht hier eine starke Abhängigkeit vom Mischungverhältnis. 

Beschreibung des Experiments
----------------------------

.. admonition:: 1. Der pericyclische Ringschluss von 1,3-Butadien: 

    Zunächst soll es um den Ringschluss von 1,3-Butadien zu Cyclobuten gehen. In Experiment :numref:`exp_rel_conf` haben Sie bereits die möglichen Konformere von 1,3-Butadien Butadien betrachtet und auch deren Population nach der Boltzmannverteilung berechenet. 

    1. Welches Konformer ist der sinnvolle Ausgangspunkt für den Ringschluss? Erwarten Sie basierend auf der Boltzmannverteilung zwischen den Konformeren von 1,3-Butadien, dass der Ringschluss bei Raumtemperatur eine effiziente Reaktion ist und wie würden Sie die Reaktionsbedingungen anpassen, um dies zu verbessern?

    Benutzen Sie das gewählte Konformer von 1,3-Butadien im Folgenden als Edukt und Cyclobuten als Produkt. Es soll nun das Reaktionsprofil mit den relativen Energien von Edukt, Produkt und Übergangszustand des Ringschlusses berechnet werden. Verwenden Sie hierfür zunächst das PBE0 Dichtefunktional mit D4 Dispersionskorrektur, den def2-TZVPP Basissatz und das DEFGRID2 Integrationsgrid. Gehen Sie wie folgt vor: 
    
    2. Führen sie eine vollständige Geometrieoptimierung von Edukt un Produkt durch. Charakterisieren sie die gefundenen Geometrien durch eine Frequenzrechnung (``AnFreq``) als Minimumsgeometrien. 

    3. Nutzen Sie Ihr chemischen Verständnis um eine Startstruktur in der Nähe des Übergangszustandes zu finden. Welche Form der pericyclische Reaktion erwarten Sie hier? 

    4. Optimieren Sie nun den Übergangszustand (``OptTS``). Klassifizieren Sie diesen dann erneut durch eine Frequenzrechnung. Visualisieren Sie die imaginäre Schwingungsmode (siehe :numref:`app-molden` für eine kurze Einführung). Welcher Bewegung entspricht diese Mode?

    .. hint:: 

        Es kann passieren, dass trotz ``OptTS`` die Geometrieoptimierung in einem Minimum endet. Verändern Sie dann die Startstruktur solange bis Sie einen Sattelpunkt finden. 

    5. Listen Sie die Diederwinkel und relativen Energien aller Strukturen (Minimums- und Übergansgeometrien) und tragen Sie das Reaktionsprofil mit den Energien graphisch auf. 

    Wie oben beschrieben, sind Barrieren aufgrund der delokalisierten Dichte im Übergangszustand stark von gewählten Dichtefunktional abhängig. Im Folgenden sollen Sie diesen Effekt etwas näher betrachtet werden. 

    6. Berechnen Sie dazu zuerst die Reaktionsbarrieren auch mit PBE und HF. Verwenden Sie dafür die optimierte PBE0 Geometrien von Edukt, Produkt und Übergangszustand für Single-Point-Rechnungen mit den verschiedenen Funktionalen. Verwenden Sie immer den def2-TZVPP Basissatz. 
    
    7. Tragen Sie die Ergebnisse für die relativen Energien zusammen mit PBE0 auf. Entspricht der Verlauf Ihrer Erwartung? Vergleichen Sie auch die Barrieren mit dem theoretischen Referenzwerte (CCSD(T)/def2-QZVP) von :math:`\Delta E^{\ddagger}=43.4\,`\ kcal/mol.

    8. Um die Unterschiede in der Elektronendichte darzustellen, plotten Sie die Differenzdichte zwischen PBE und HF am Übergangszustand. Generieren Sie dafür zunächst in einer weiteren Single-Point-Rechnungen für PBE und HF die .cube Dateien mit der vollständigen Elektronendichte (``ElDens("ElDens.cube");`` im ``%plots`` Block, siehe :numref:`exp_mo`). Berechnen Sie nun mit dem Multiwfn Programm die Differenzdichte (siehe :numref:`app-multiwfn`) und plotten Sie die entstehende .cube Date mit VMD (siehe :numref:`app-Plot-MO-Dens`). Was ist in der Differenzdichte zu erkennen? Fokussieren Sie sich dabei auf die Region in der sich die neue C-C Bindung bildet. 

    .. hint::

        Die Differenzdichte ist verglichen mit der gesamte Dichte einer Rechnung klein, und die Änderung im Bereich der Bindung noch kleiner. Deshalb muss der Isovalue für den Plot der Differenzdichte auch kleiner gewählt werden. Verwenden Sie also beim Plotten die Einstellungen: ``vmd_get_all.sh 1 0.0028``. 

.. admonition:: 2. Die S\ :sub:`N`\2 Reaktion: 

    Bei einfachen Reaktionen mit einer klar definierten Reaktionskoordinate kann es hilfreich sein einen relaxierten Scan durchzuführen, um eine gute Startgeometrie für die Optimierung des Übergangszustands zu erhalten. Betrachten Sie nun die folgenden S\ :sub:`N`\ 2 Reaktionen: 

        CH\ :sub:`3`\ Br + Cl\ :sup:`-` |eqarr| CH\ :sub:`3`\ Cl + Br\ :sup:`-` 

        CH\ :sub:`3`\ I + Br\ :sup:`-` |eqarr| CH\ :sub:`3`\ Br + I\ :sup:`-`

    Da bei dieser Reaktion Anionen beteiligt sind, ist die Beschreibung der Umgebung unerlässlich. Hier soll die Reaktion im recht unpolaren und aprotischen Lösungsmittel DCM beschrieben werden. Fügen Sie dafür in ihrer Inputdatei den Aufruf für das conductor-like polarizable-continuum-model CPCM für DCM ein (``CPCM(DCM)``). Benutzen Sie im Folgenden das PBE0 Dichtefunktional mit dem def2-TZVPP Basissatz. 

    1. Optimieren Sie zunächst alle vorkommenden Moleküle. Listen Sie die optimierten C-X Bindungslängen auf. 

    2. Fügen Sie nun das jeweilige Anion in die Rechnung ein und führen Sie einen relaxierten Scan des C-X\ :sup:`-` Abstands von 3.3 |angst| bis etwas unter den optimialen Abstand durch. Wählen Sie dabei eine geeignete Schrittgröße. 

    3. Finden Sie den Übergangszustand der Reaktion. Verwenden Sie dafür eine geeignete Geometrie aus dem relaxierten Scan in der Optimierung des Übergangszustands. Überprüfen Sie durch eine Frequenzrechnung, dass es sich tatsächlich um einen Übergangszustand handelt. Geben Sie nun auch die Bindungslängen in den Übergangsgeometrien an. 

    .. hint::

        Wenn die Optimierung des Übergangszustands nicht konvergiert, kann es hilfreich sein die Hessematrix an der Startgeometrie zu berechnen (``AnFreq``) und bei der Optimierung einzulesen (``%geom inhess read end``). Andernfalls kann auch durch einen feineren Scan die Startgeometrie verbessert werden. 

    4. Erstellen Sie ein Energiediagramm relativ zu den Edukten in dem beide Reaktionen dargestellt sind. Tragen Sie auch die Energien für den optimierten Übergangszustand ein. Berechnen Sie die Aktivierungsenergien für die vier möglichen Reaktionen. Welche Reaktion ist demzufolge bevorzugt? 