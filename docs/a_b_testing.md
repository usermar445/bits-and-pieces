# A/B Testing Übersicht


## Welche Verteilung?

Hier Binomialverteilung, weil 2 verschiedene Outcomes und Metrik ist eine Wahrscheinlichkeit (ausserdem 
unabhängige Ereignisse mit gleicher Wahrscheinlichkeit).

## Konfidenzintervalle
Zuerst, prüfen ob der Standardfehler normalverteilt ist.

Vorgehen: Punktschätzer + Z-Score * Standardfehler

Sicherheit vs. Wahrscheinlichkeit: Im spezifischen Fall einer Stichprobe, sollte man nicht
von Wahrscheinlichkeit reden, sondern Sicherheit. Das Konfidenzintervall sagt, 
dass wenn man viele Konfidenzintervalle berechnen würde, dann man nur in alpha 
daneben liegen würde.

## Testen
Idee: wie wahrscheinlich ist es, dass das Resultat zufällig ist?

Entsprechend ist die Nullhypothese, dass die Resultate sind entstanden sind und 
die Arbeitshypothese, dass die Resultate *nicht* zufällig sind.

Oder mit zwei Gruppen: 
*Nullhypothese:* Wahrscheinlichkeit in Control = Wahrscheinlichkeit in Experiment

*Arbeitshypothese:* Wahrscheinlichkeit in Control - Wahrscheinlichkeit in Experiment ungleich 0.

Mit zwei Samples: pooled standard error berechnen für Konfidenzintervall.

## Signifikanz vs. substantielle (praktische) Signifikanz
Unterscheiden zwischen: statistisch signifikant und aus Business-Perspektive (substantiell) signifikant

## Test Design
alpha = Nullhypothese ablehnen, obwohl wahr

beta = Nullhypothese nicht ablehnen, obwohl falsch


Kleines Sample führt dazu: tiefes alpha, aber hohes beta; mit grösserem Sample, tieferes beta

Sensitivity: 1 - beta  
Ziel ist es eine hohe Sensitivity zu haben


**Wie verändert sich Sample Size:**

Höhere click-through-probability: erhöht Standardfehler, deshalb auch Sample Size, um Standardfehler auf gleichem
Niveau zu halten

Höhere praktische Signifikanz: grössere Veränderungen sind einfacher zu entdecken, deshalb kleineres Sample

Höheres Signifikanzniveau: wenn Sensitivity gleich bleiben soll, muss Sample grösser werden

Höhere Sensitivity: braucht grösseres Sample

## Konfidenzintervalle
Konfidenzintervall ist: 

- mit beiden Bounds über praktischer Signifikanz: Launch Change
- inkludiert null und unter praktischer Signifikanz: not launch
- statistisch signifikant (über 0), aber nicht praktisch: not launch
- bounds gehen auf beiden Seiten über praktische Signifikanz hinaus: additional test (nicht genug power)
- inkludiert 0, aber geht über praktische signifikant hinaus: mehr power
- inkludiert nicht 0, aber geht unter praktische Signifikanz: mehr power


