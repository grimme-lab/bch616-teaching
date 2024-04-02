.. include:: symbols.txt

Experiment: Hückel-Theorie für |pi|-Elektronensystem (HMO)
==========================================================

.. contents::

Die Hückelmethode ist eine der einfachsten semiempirischen Methoden zur quantenchemischen Beschreibung molekularer Systeme. Sie wurde 1931 von E. Hückel zur Berechnung planarer konjugierter Kohlenwasserstoffe entworfen. Eine herausragende historische Bedeutung kommt ihr deshalb zu, weil man - vor allem durch Berücksichtigung der Symmetrieeigenschaften - auf eine aufwendige numerische Behandlung, d.h. Computer, verzichten konnte.

Näherungen in der Hückel-Theorie
--------------------------------

Für planare, konjugierte (d.h. aus :math:`\mathrm{sp}^{2}`-hybridisierten Atomen aufgebaute) Systeme können folgende Näherungen eingeführt werden:

1. Die |sigma|-Elektronen werden explizit vernachlässigt, d.h. ergeben ein konstantes Potential für alle |pi|-Elektronen.
2. Für jedes Atom wird nur ein Atomorbital pz in der LCAO-Entwicklung verwendet.
3. Die Überlappungsintegrale werden vernachlässigt für :math:`\mu \neq \nu` (:math:`S_{\mu\mu} = 1`).
4. Die Integrale :math:`H_{\mu\nu}` werden empirisch festgelegt:

(a) :math:`H_{\mu\nu} = \beta`, falls die Atome |mu| und |nu| direkt verbunden sind (Energie eines Elektrons im Feld zweier Kerne mit impliziten Korrekturen für vernachlässigte Terme). Sind |mu| und |nu| nicht direkt miteinander verbunden, gilt :math:`H_{\nu\nu} = 0`.
(b) :math:`H_{\nu\nu} = \alpha` (Energie eines Elektrons im Feld des Kerns |mu| mit impliziten Korrekturen für vernachlässigte Terme).

In der Praxis wird :math:`\alpha` für Kohlenstoff willkürlich auf Null gesetzt, und die Parameter anderer Atome werden relativ dazu empirisch bestimmt. :math:`\beta` (Resonanzintegral) wird für eine :math:`\ce{C-C}` Bindung der Länge 1.4 :math:`\text{Å}` als Standard auf -1 gesetzt. Bei Molekülen mit starken Abweichungen von dieser Standardlänge oder bei :math:`\ce{C-X}` Bindungen wird der :math:`\beta`-Wert empirisch verändert.

Diskussion der eingeführten Näherungen
--------------------------------------

1.  Die :math:`\sigma`-:math:`\pi`-Separation ist gerechtfertigt, wenn die :math:`\sigma`-Elektronen in guter Näherung für die Reihe zu vergleichender :math:`\pi`-Zustände durch die gleiche Produktfunktion dargestellt werden können, d.h. wenn es innerhalb einer Reihe keine unterschiedlichen  :math:`\sigma`-:math:`\pi` Polarisationseffekte gibt. Behandelt man Aromaten unterschiedlichen Typs, ist diese Annahme jedoch bereits problematisch, da der Einfluss der :math:`\sigma`-Orbitale auf die Stabilität von Aromaten wohl nicht zu vernachlässigen ist. Ähnliches gilt für elektronische Spektren von Aromaten.
2. Bei einfachen Kohlenwasserstoffen ist die Korrelation der Parameter :math:`\alpha` und :math:`\beta` mit experimentellen Größen recht brauchbar. Probleme treten beim Vorhandensein von Heteroatomen, stark polarisierbaren Atomen oder Molekülgruppen oder bei Bindungsstabilisierungseffekten wie Hyperkonjugation auf.

Ladungsordnung und Bindungsordnung
-------------------------------------------

Anleitung: Durchführung einer Hückel-Rechnung
---------------------------------------------

Anleitung für das Extended-H ̈uckel Programm EHT
------------------------------------------------

Aufgaben
--------

