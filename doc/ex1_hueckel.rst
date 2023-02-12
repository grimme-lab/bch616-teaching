.. include:: symbols.txt

Experiment: Hückel-Theorie für |pi|-Elektronensystem (HMO)
==========================================================

.. contents::

Die Hückelmethode ist eine der einfachsten semiempirischen Methoden zur quantenchemischen Beschreibung molekularer Systeme. Sie wurde 1931 von E. Hückel zur Berechnung planarer konjugierter Kohlenwasserstoffe entworfen. Eine herausragende historische Bedeutung kommt ihr deshalb zu, weil man - vor allem durch Berücksichtigung der Symmetrieeigenschaften - auf eine aufwendige numerische Behandlung, d.h. Computer, verzichten konnte.

Näherungen in der Hückel-Theorie
--------------------------------

Für planare, konjugierte (d.h. aus :math:'sp^{2}'-hybridisierten Atomen aufgebaute) Systeme können folgende Näherungen eingeführt werden:

1. Die |sigma|-Elektronen werden explizit vernachl  ̈assigt, d.h. ergeben ein konstantes Potential für alle |pi|-Elektronen.
2. Für jedes Atom wird nur ein Atomorbital pz in der LCAO-Entwicklung verwendet.
3. Die Überlappungsintegrale werden vernachl ̈assigt für :math:'\\mu\\neq\\nu' (:math:'S\\mu\\mu = 1').
4. Die Integrale :math:'H\\mu\\nu' werden empirisch festgelegt:

(a) :math:'H\\mu\\nu = \\beta', falls die Atome |mu| und |nu| direkt verbunden sind (Energie eines Elektrons im Feld zweier Kerne mit impliziten Korrekturen für vernachlässigte Terme). Sind |mu| und |nu| nicht direkt miteinander verbunden, gilt :math:'H\\nu\\nu = 0'.
(b) :math:'H\\nu\\nu = \\alpha' (Energie eines Elektrons im Feld des Kerns |mu| mit impliziten Korrekturen für vernachlässigte Terme).

In der Praxis wird |alpha| für Kohlenstoff willkürlich auf Null gesetzt, und die Parameter anderer Atome werden relativ dazu empirisch bestimmt. |beta| (Resonanzintegral) wird für eine C--C Bindung der Länge 1.4|angst| als Standard auf --1 gesetzt. Bei Molekülen mit starken Abweichungen von dieser Standardlänge oder bei C--X Bindungen wird der |beta|-Wert empirisch verändert.

Diskussion der eingeführten Näherungen
--------------------------------------

1.  Die |sigma|-|pi|-Separation ist gerechtfertigt, wenn die |sigma|-Elektronen in guter Näherung für die Reihe zu vergleichender |pi|-Zustände durch die gleiche Produktfunktion dargestellt werden k ̈onnen, d.h. wenn es innerhalb einer Reihe keine unterschiedlichen |sigma|--|pi| Polarisationseffekte gibt. Behandelt man Aromaten unterschiedlichen Typs, ist diese Annahme jedoch bereits problematisch, da der Einfluß der |sigma|-Orbitale auf die Stabilität von Aromaten wohl nicht zu vernachlässigen ist.  ̈Ahnliches gilt für elektronische Spektren von Aromaten.
2. Bei einfachen Kohlenwasserstoffen ist die Korrelation der Parameter |alpha| und |beta| mit experimentellen Größen recht brauchbar. Probleme treten beim Vorhandensein von Heteroatomen, stark polarisierbaren Atomen oder Molekülgruppen oder bei Bindungsstabilisierungseffekten wie Hyperkonjugation auf.

Ladungsordnung und Bindungsordnung
-------------------------------------------

Anleitung: Durchführung einer Hückel-Rechnung
---------------------------------------------

Anleitung für das Extended-H ̈uckel Programm EHT
------------------------------------------------

Aufgaben
--------

