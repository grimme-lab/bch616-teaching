.. include:: symbols.txt

.. _exp_disp:

Experiment 4: Dispersion
========================

.. contents::

Hintergrund
-----------
In diesem Experiment sollen Sie sich mit den schwachen aber wichtigen nicht-kovalenten Wechselwirkungen beschäftigen. Ziel dieses Experiments ist es die London-Dispersion in Edelgasdimeren theoretisch zu beschreiben. 

Beschreibung des Experiments
----------------------------

.. admonition:: 1. Potentialkurven

   Erstellen Sie Potentialkurven für folgende Edelgasdimere: :math:`\ce{Ar-Ar}`, :math:`\ce{Kr-Kr}`. Verwenden Sie dazu das `B3LYP`-Funktional jeweils ohne und mit Dispersionskorrektur (Keyword: `D4`) sowie einen `def2-TZVP` Basissatz. Ein Beispielinput für ein diatomaren System (:math:`\ce{He2}`) ist gegeben. In folgendem Beispiel wird ein unrelaxierter Scan für die Bindungslänge von 3 bis 9 Angström in 60 Schritten durchgeführt:

   .. code-block:: none

      ! B3LYP D4 def2-TZVP TightSCF
      
      %paras
         R= 3.0,9.0,60  # Keywoerter fuer einen unrelaxierten Scan 
      end               # der Parameter R wird in 60 Schritten
                        # von 3 nach 9 Angstroem variiert

      *xyz 0 1
      He 0 0 0 
      He 0 0 {R}

   Sie finden die aufzutragenden Daten im Output. Tragen Sie Abstände (in |angst|) gegen relative Energie (in :math:`\text{kcal} \cdot \text{mol}^{-1}`) auf. 

.. admonition:: 2. Optimale Abstände und Dissoziationsenergien

   Bestimmen Sie jeweils den optimalen :math:`\ce{Ar-Ar}`- und :math:`\ce{Kr-Kr}`-Abstand. Berechnen Sie die Dissoziationsenergien (`B3LYP/def2-TZVP` und `B3LYP-D4/def2-TZVP`) und geben Sie diese in :math:`\text{kcal} \cdot \text{mol}^{-1}` an.

.. admonition:: 3. Diskussion

   Wie verändern sich die Potentialkurven und Dissoziationsenergien mit Dispersionskorrektur im Gegensatz zu den Kurven ohne Dispersionskorrektur? 


.. note::
   :class: warning

   Dichtefunktionale sind allgemein nicht in der Lage van-der-Waals Wechselwirkungen korrekt zu beschreiben, da langreichweitige Korrelation fehlt. Deswegen sollte man immer eine Dispersionskorrektur verwenden! 
