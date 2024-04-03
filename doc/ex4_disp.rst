.. include:: symbols.txt

.. _exp_disp:

Experiment 4: Dispersion
======================

.. contents::

Beschreibung des Experiments
----------------------------

1. Erstellen Sie Potentialkurven für folgende Edelgasdimere: :math:`\ce{Ar-Ar}`, :math:`\ce{Kr-Kr}`. verwenden Sie dazu das B3LYP-Funktional jeweils ohne und mit Dispersionskorrektur (Keyword: `D3BJ`) mit einer TZVP-Basis. Ein Beispielinput für ein diatomaren System (:math:`\ce{He2}`) ist gegeben. In folgendem Beispiel wird ein unrelaxierter Scan für die Bindungslänge von 3 bis 9 Angström in 60 Schritten durchgeführt:

   .. code-block:: none

      ! B3LYP TZVP TightSCF
      
      %paras
         R= 3.0,9.0,60  # Keywoerter fuer einen unrelaxierten Scan 
      end               # der Parameter R wird in 60 Schritten
                        # von 3 nach 9 Angstroem variiert

      *xyz 0 1
      He 0 0 0 
      He 0 0 {R}

   Sie finden die aufzutragenden Daten im Output. Tragen Sie Abstände (in Å) gegen relative Energie (in :math:`\text{kcal} \cdot \text{mol}^{-1}`) auf. 

2. Bestimmen Sie jeweils den optimalen :math:`\ce{Ar-Ar}`- und :math:`\ce{Kr-Kr}`-Abstand. Berechnen Sie die Dissoziationsenergien (B3LYP/TZVP und B3LYP-D3BJ/TZVP) und geben Sie diese in :math:`\text{kcal} \cdot \text{mol}^{-1}` an.
3. Wie verändern sich die Potentialkurven und Dissoziationsenergien mit Dispersionskorrektur im Gegensatz zu den Kurven ohne Dispersionskorrektur? 