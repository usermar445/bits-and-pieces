# Offene Fragen Statistik

- Was wird bei Konfidenzintervallen genau ausgesagt? Wie funktioniern diese?
- Was ist die Idee am Testen?
- Unterschiede: standard error, standard deviation, variance, variability
- Was ist die Markov-Ungleichung? Bonferroni? Wofür?
- Wie erklärt man, was ein "p-Wert" ist?
- Was ist ein Erwartungswert? Und entspricht dieser dem Mittelwert?
- Was ist eine Pareto-Verteilung? Exponentialverteilung?
- Was ist Bootstrapping?
- Was ist "statistical Power"? Wie hängt das mit Signifikanz zusammnen? Wie mit Stichprobengrösse? Und hilft hier Bootstrapping?


## Puntkschätzer, Konfidenzintervalle und statistische Tests
*Schliessende Statistik* generell benutzt verschiedene Methoden, um von einer *Stichprobe* 
etwas über die *Population* auszusagen, d.h. in den meisten fällen will man mithilfe 
einer Stichprobe etwas über einen **unbekannten Parameter $\theta$** (bspw. einen Binomialparameter,
Mittelwert, Quantil, Standardabweichung) aussagen.

Ein **Punktschätzer** wird meistens mit $\hat \theta$ bezeichnet. (ist nicht weiter interessant)


**Konfidenzbereiche**  
Ist eine aufgrund von Daten $D$ berechnete Menge $C(D)$ von *möglichen Werten* für $\theta$, die
mit einer gewissen Sicherheit $\alpha$ den tatsächlichen Parameter $\theta$ enthält also:

$$P(C(D) \ni \theta) \ge 1- \alpha$$

Dabei nennt man $\alpha$ *Konfidenzniveau*, oft wird dabei 5% verwendet.


**Interpretation:** Wichtig ist, dass das Konfidenzintervall keine *Wahrscheinlichkeit* darstellt, 
sondern eine *Sicherheit*. Also, die Aussage von Konfidenzintervallen ist, dass mit 
$(1-\alpha)$-prozentiger **Sicherheit** der *tatsächliche* Parameter $\theta$ im Intervall enthalten ist.
Oft wird zur Erklärung der Interpretation folgendes Gedankenexperiment verwendet: Würde man
die Stichprobe (oder das Experiment) sehr oft wiederholen und jeweils ein Konfidenzintervall
schätzen, so wäre in $(1-\alpha)$ Prozent der Konfidenzintervalle der wahre Paremeter enthalten. Die
Aussage von Konfidenzintervallen ist also **nicht**, dass der Parameter mit $(1-\alpha)$-prozentiger 
*Wahrscheinlichkeit* im Intervall enthalten ist. Ein anderes Gedankenexperiment ist, dass man
jeden Tag wieder einen neue Stichprobe zieht und ein neues Konfidenzintervall für einen 
neuen Parameter $\theta_i$ schätzt. Auch dann würden  $(1-\alpha)$ Prozent der Konfidenzintervalle
die wahren Parmeter enthalten.


**Statistische Tests**  
Auch bei statistischen Test wird mithilfe von Daten etwas über die Population (bzw. meistens einen
Populationsparameter) ausgesagt. Jedoch wird hier konkret eine *Hypothese* über den Parameter gebildet, die dann
entsprechend abgelehnt oder angenommen wird. Im Zentrum steht also eine Entscheidung. Das Prinzip ist folgendes:
man eine *Arbeitshypothese*, dass ein bestimmter Effekt vorhanden ist bzw. ein Parameter eine bestimmte 
Grösse hat. Die Arbeitshypothese kann oft nur *indirekt* nachgewiesen werden, deshalb formuliert man
eine *Nullhypothese*, die besagt, dass der zu untersuchende Effekt nicht vorliegt bzw. die Stichprobenergebnisse
zufällig entstanden sind. Danach führt man einen statistischen Test durch. Mit diesem prüft man, ob die 
Nullhypothese mit einer bestimmten Sicherheit $\alpha$ (d.h. *Signifikanzniveau*) abgelehnt werden kann (und dadurch 
die Arbeitshypothese angenommen werden kann). 


Anders ausgedrückt: Man betrachtet die Daten $D$ als Zufallsvariable mit Werten in $D$ und
beschreibt mögliche Wahrscheinlichkeitsverteilungen von $D$ unter der Annahme, dass es den besagten Effekt
nicht gibt.

Dabei ist das Signifikanziveau $\alpha$ die Wahrscheinlichkeit einen **Fehler ersten Art** zu begehen, d.h. 
die Nullhypothese abzulehnen, obwohl sie zutrifft.


**Verbindung von Konfidenzintervallen und Tests**  
Unter bestimmten Umständen (gleiche Verteilung?? und gleiches $\alpha$) kann man auch ein Konfidenzintervall
gebrauchen, um die Gültigkeit von $H_0$ zu beurteilen. Dies ist der Fall wenn es sich um einen
zweiseitigen Test handelt (mit einem zweiseitigen Konfidenzintervall). Will man eine Hypothese über einen Parameter 
testen, so kann auch ein Konfidenzintervall berechnen (gleiches $\alpha$, gleiche Verteilung??). Liegt $H_0$ im 
Konfidenzintervall, so kann $H_0$ *nicht* abgelehnt werden.


## Definitionen: standard error, standard deviation, variance, variability

**Variance (Varianz)**  
Ein Skalenparameter (maeasure of variability), der angibt, wie fest "typischerweise" die $X$-Werte 
vom Zentrum sind (und untereinander weit weg sind). **Varianz einer Zufallsvariabel** ist definiert als:

$$Var(X) = E((X- E(X))^2)$$

d.h. ist der Erwartungswert der quadierten Abweichung einer Zufallsvariable von ihrem Mittelwert.

**Standard deviation (Standardabweichung)**  
Die Standardabweichung ist definiert als

$$ Std(X) = \sqrt{Var(X)}$$

Spricht man von einer theoretischen Verteilung, wird die Standardabweichung üblicherweise mit
$\sigma$ bezeichnet.

**Stichprobenstandardabweichung (empirical standard deviation)**  
Mittlere Abweichung vom Stichprobenmittelwert:

$$ S = \sqrt{\frac{1}{n-1}\sum_{i=1}^n(X_i - \bar X)^2}$$

**Stichprobenvarianz**  

$$ S^2 = \frac{1}{n-1} \sum_{i=1}^n (X_i - \bar X)^2 $$

**Standard error (Standardfehler)**  
Der Standardfehler ist die Standardabweichung $\sigma$ eines Schätzers $\hat \theta$ bzw. dessen *Stichprobenverteilung (sampling distribution)*.

$$ se = se(\hat \theta) = \sqrt{Var(\hat \theta)}$$

da diese Standardabweichung oft unbekannt ist, kann man sie durch die Stichprobenstandardabweichung $S$ schätzen.
Bspw. für den Mittelwert ergibt sich so einen Standardfehler:

$$ \hat{se} = \frac{S}{\sqrt{n}}$$

Der Standardfehler ist dann also ein Schätzer für die Standardabweichung eines Schätzers.

**Variability**  
Skalenparameter, die angeben wie weit die $X$-Werte von ihrem Zentrum und untereinander entfernt sind.
Typische Masse sind: Range, Interquartilabstand, Varianz, Standardabweichung.


## Was ist ein p-Wert?
Ein p-Wert ist eine statistische Hilfsgrösse, die bei Hypothesentests verwendet wird, um eine Aussage
über die Annahme bzw. Ablehnung der Nullhypothese zu treffen. Der p-Wert gibt an, wie wahrscheinlich
es ist, eine Teststatistik zu erhalten, die gleich oder extremer des tatsächlichen beobachteten Wertes
ist, unter der Annahme, dass die Nullhypothese (bzw. deren Verteilung) gilt. Formal:

$$ p = P(T \ge t \vert H_0)$$

p-Werte sind **nicht** als Wahrscheinlichkeit, dass $H_0$ zutrifft zu verstehen. 


## Was ist eine Teststatistik?
Eine Teststatistik $T$ ist eine Statstik (quantiative Grösse basierend auf Daten $D$), die für einen
Hypothesentest verwendet wird. Üblicherweise werden damit die Daten $D$ auf *eine* Zahl reduziert und
mit dieser wird danach einen statistischen Test durchgeführt. Unterschiedliche statistische Tests
haben unterschiedliche Teststatistiken, die wiederum unterschiedliche Verteilungen haben. Welche
Teststatistik verwendet wird, hängt entsprechend vom durchgeführten Test ab. 


## Was wird bei Konfidenzintervallen genau ausgesagt? Wie funktioniern diese?
Konfidenzintervalle sind ein aufgrund von Daten $D$ berechneter Bereich möglicher Werte für einen 
Populationsparameter $\theta$. Dabei geben sie mit einer bestimmten *Sicherheit* $1-\alpha$ an, dass
der *wahre* Populationsparemeter in diesem Bereich liegt. Wichtig ist, dass der Populationsparameter
**nicht** mit einer gewissen *Wahrscheinlichkeit* im Konfidenzintervall enthalten ist, sondern
mit einer bestimmten **Sicherheit**. D.h. würde man ein Experiment sehr oft wiederholen und jeweils
ein Konfidenzintervall schätzen, so würden $1-\alpha$ Prozent dieser den wahren Parameter enthalten.

Dabei gibt es verschiedene Möglichkeiten, Konfidenzintervalle zu berechnen. Am weitesten verbreitet
sind dabei die approximativen Konfidenzintervalle nach Wald. Grundsätzlich wird dabei einen Punktschätzer
berechnet und von diesem eine gewissen Abweichung (*margin of error $m$*) addiert/subtrahiert (angenommen standardnormalverteilt).
Formal:

$$\hat \theta &plusmn; \text{margin of error}$$


**Konfidenzintervalle nach Wald**  
Es wird angenommen, dass die (standardisierte) Abweichung des Schätzers **standardnormalverteilt** ist ((??)):

$$\frac{\hat \theta - \theta}{\hat \tau}$$

Entsprechend wird der *margin of error* berechnet durch $m = \text{z-score} * \text{standard error}$, bzw. z-Score als
Verteilung der Standardnormalverteilung. 

Somit ergibt sich für das Konfidenzintervall (zweiseitig):

$$ \hat \theta &plusmn; \Phi^{-1}(1-\alpha/2) * \text{se} $$

Walds Konfidenzintervalle können gebraucht werden für folgende Parameterschätzungen:

- Mittelwerte $\mu$
- Binomialparameter $p$
- Vergleich zweier Mittelwerte


**Wilsons Konfidenzintervalle für Binomialparameter**  
(ausgelassen)


**Konfidenzintervalle für einen Mittelwert (normalverteilt)**  
Ist die Standardabweichung bekannt, kann das Konfidenzintervall für einen Mittelwert einer normalverteilten
Population durch

$$ \bar X &plusmn; \Phi(1-\alpha/2) * \sigma/\sqrt{n}$$

geschätzt werden. Da die Standardabweichung der Population aber in den meisten Fällen **nicht** bekannt ist, muss
man auf die Stichprobenstandardabweichung zurückfreifen. Dazu muss man aber ein Stundet t-Konfidenzinverall 
berechnen. 


**Student's t-Konfidenzintervalle**  
Sind die Beobachtungen **normalverteilt** kann man Student t-Konfidenzintervalle
berechnen. Die Hilfsgrösse:

$$ \frac{\bar X - \mu}{S/\sqrt{n}} \sim t_{n-1}$$

ist Student verteilt.  
Somit ergibt sich für das Konfidenzintervall (für einen **Mittelwert**):

$$\bar X &plusmn; t_{n-1;1-\alpha/2} * \frac{S}{\sqrt{n}}$$


**$\chi^2$ Konfidenzintervalle (für $\sigma$)**  
(ausgelassen)


**Konfidenzintervalle für Quantile**  
(ausgelassen)


**Asympotitische Konfidenzintervalle für nicht normalverteilte Populationen**  
Für nicht normalverteilte Populationen können mit der gleiche Methode Konfidenzinveralle für Mittelwerte 
berechnet werden, wenn die Stichprobengrösse $n$ genügend gross ist:

$$ \bar X &plusmn; \Phi(1-\alpha/2) * se(\bar X)$$


## Was ist die Idee am Testen?
Bei statistischen Tests will man mithilfe von Daten $D$ (einer Zufallsstichprobe) einen bestimmten Effekt nachweisen. 
Dazu formuliert man eine *Arbeitshypothese*, dass besagter Effekt vorhanden ist. Da die Arbeitshypothese oft nur
*indirekt* nachgewiesen werden kann, formuliert man eine eine *Nullhypothese*: man betrachtet die Daten $D$ als
Zufallsvariable und beschreibt mögliche Wahrscheinlichkeitsverteilungen unter der Annahme, dass es den besagten Effekt
*nicht* gibt. Also

$H_0\text{: kein Effekt, d.h. Daten } D \text{ zufällig unter Annahme einer bestimmten Verteilung}$
$H_1\text{: Effekt besteht}$

Danach entscheidet man anhand der Daten $D$, ob man $H_0$ mit einer bestimmten Sicherheit $1-\alpha$ annimmt oder 
ablehnt (und damit von $H_1$ überzeugt ist). Dazu berechnet man üblicherweise eine Hilfsgrösse, d.h. 
eine **Teststatistik $T$**.

Es gibt zwei Möglichkeiten den Test durchzuführen: 

- man berechnet den **kritischen Wert** $P(X > c_{\alpha}) \le \alpha$, d.h. der Wert, wo unter der Annahme von $H_0$ die Verteilungsfunktion $F(x)$ grösser-gleich  $1-\alpha$ ist
- man berechnet einen **$p$-Wert**, d.h. die Wahrscheinlichkeit, unter Annahme von $H_0$ eine gleiche oder extremere Teststatistik $T$ zu erhalten und vergleicht diesen mit den Daten


Dabei kann man immer zwei mögliche Fehler begehen: 

- **Fehler 1. Art**: man lehnt $H_0$ ab, obwohl sie zutrifft
- **Fehler 2. Art**: man lehnt $H_1$ nicht ab, obwohl sie nicht zutrifft



## Was ist die Markov Ungleichung? Was ist die Bonferroni-Korrektur?
Die **Markov-Ungleichung** wird gebraucht, um Wahrscheinlichkeiten abzuschätzen (von Zufallsvariabeln). Sie besagt

$$ P(X \ge a) \le \frac{E(X)}{a}$$

Die Markov-Ungleichung definiert so eine obere Schranke (*upper bound*) für die Wahrscheinlichkeit. 


Die Bonferroni-Korrektur wird gebraucht für das Testen von mehreren Metriken. Testet man mehrer Hypothesen gleichzeitig,
so steigt die Wahrscheinlichkeit, einen Fehler 1. Art zu begehen. Die Bonferroni-Korrektur testet jede Hypothese mit
Signifikanzniveau $\alpha/m$, mit $\alpha$ als gesamten Signifikanzniveau und $m$ Anzahl Hypothesen. Allerdings ist
die Bonferroni-Korrektur recht konservativ.


## Was ist ein Erwartungswert? Und entspricht dieser dem Mittelwert?
Der Erwartungswert einer Zufallsvariable ist ein gewichteter Druchschnitt und definiert als: 

$$ E(X)=\sum x \text{Pr}(X=x)$$ 

im Fall einer diskreten Zufallsvariable bzw.

$$E(X) = \int_{-\infty}^{\infty} x f(x) dx$$

Informell entspricht der Erwartungswert dem Mittelwert, d.h. $E(X) = \mu$ (??). Empirisch konvergiert das arithmetische
Mittel gegen den Erwartungswert wenn $n \to \infty$. Der Erwartungswert bzw. der Mittelwert ist auch das *erste Moment*
einer Verteilung.  
Bestimmte Verteilungen haben bekannte Mittelwerte bzw. Erwartungswerte, bspw. $X \sim \text{B}(n,p)$ hat 
$E(X) = \mu = np$.
