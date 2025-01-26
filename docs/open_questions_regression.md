# Offene Fragen Lineare Regression

- Für was braucht man OLS, wenn man bereits Schätzer hat für die Parameter aus der Stichprobe?
- Was ist genau das Ziel? Beschreibung des Zusammenhangs? Wie unterscheidet sich das von anderen Methoden?
- Zusammenhang: Abhängigkeit/Unabhängigkeit, Korrelation, Kovarianz, Regression - was hängt wie zusammen? Was wird wo ausgesagt?
- Was ist Kovarianz? Haben abhängige Variabeln eine Kovarianz? Was Korrelation?
- Müssen, um überhaupt eine Regression rechnen zu können, die Variabeln "zusammenhängen"? Abhängig sein?
- "Beschreibung Zusammenhang": Weshalb Erwartungswert?
- Wie prüft man, ob zwei Variabeln abhängig bzw. unabhängig sind? Wenn z.B. keine Korrelation/Kovarianz, bedeutet das gleich Unabhängigkeit?
- Joint Distributions
- Ceteris paribus Interpretation: Effekt von Faktor x gegeben, dass alle anderen Variabeln "fix" bleiben - wie wird das sichergestellt?
- Was ist der Unterschied Fehlervarianz, Root Mean Squared Error der Regression, Standardfehler von OLS Schätzer?
- Was sind die Gauss-Markov Annahmen?
- Kausale Analyse: Weshalb gilt: wenn $E[u\vert x]=0$, dann $E[y \vert x]=0$
- Kausale Analyse: Weshalb gilt: wenn $E[u_i(0)\vert d]=0$, dann $E[y_i(0) \vert x]=0$ bzw. weshalb nur $y_i(0)$ Kontrollgruppe??
- Weshalb ist OLS unbiased wenn gilt $E[u \vert x]=0$
- Kausale Analyse: wie kann es $y_i(0)$ in der Treatmentgruppe geben?
- Was ist der Unterschied zwischen einer Normalverteilung und $t$-Verteilung? Wann kann die $t$-Verteilung mit dem Schätzer $\hat \sigma$ verwendet werden?
- Was ist der F-Test? Wofür wird dieser bei der Regressionsanalys gebraucht?
- Wie liest man genau einen Regressions Output? Auf was muss man achten?
- Für was quadratische Modelle? Für was Interaktionsterme?

## Zusammenhang: Was ist was?
Es gibt verschiedene Arten von Zushammenhängen von statistischen Variabeln. "Zusammenhang" an sich ist dabei etwas 
schwammig:

**Stochastische Unabhängigkeit (bwz. Abhängigkeit):**  
Hierbei handelt es sich um den "Zusammenhang" zweier **Ereignisse**. Dies ist nicht zu verwechseln
mit dem Zusammenhang zweier Zufallsvariablen. Zwei Ereignisse sind stochastisch unabhängig, wenn das Eintreten des einen, 
die Eintretenswahrscheinlichkeit des anderen nicht beeinflusst. Formal ist Unabhängigkeit definiert als: 
$P(A \cap B) = P(A) * P(B)$, woraus folgt: $P(A \vert B) = P(A)$. 
Unabhängigkeit wird in gewissen Fällen *angenommen* und in gewissen Fällen *hergeleitet*. Zwei disjunkte Ereignisse mit
positiver Wahrscheinlichkeit, können nicht unabhängig sein. Dabei gilt es zu beachten, dass die Voraussetzung der 
Unabhängigkeit nicht immer ganz einfach zu beurteilen ist. Die formale Überprüfung der Unabhängigkeit kann aber nur
durchgeführt werden, wenn die Wahrscheinlichkeiten bekannt sind. Will man den "Zusammenhang" zweier Zufallsvariabeln 
überprüfen, muss man bspw. einen Test oder eine Regression verwenden. Stochastische Unabhängigkeit bzw. Abhängigkeit ist
nicht gleichzusetzen mit einem "Zusammenhang".

**Kovarianz:**  
Kovarianz ist ein Mass für den **linearen Zusammenhang** zweier Zufallsvariabeln. D.h. existiert ein *nicht-linearer* 
Zusammenhang zwischen zwei Variabeln, kann dies nicht durch die Kovarianz erfasst werden. Die Kovarianz erfasst, inwiefern
zwei Variabeln miteinander "gekoppelt" sind, d.h. grosse (kleine) Abweichungen vom Erwartungswert von $X$ gehen tendenziell
einher mit grossen (kleinen) Abweichungen vom Erwartungswert von $Y$. Formal:

$$ Cov(X, Y) = E((X - E(X))(Y - E(Y)))$$

oder auch

$$ Cov(X, Y) = E(XY) - E(X) E(Y)$$

Der Zusammenhang zur Unabhängigkeit ist hierbei folgender:   
Wenn zwei Zufallsvariabeln unabhängig sind, dann gilt Cov(X,Y) = 0. Dieser Zusammenhang gilt jedoch umgekehrt **nicht**.
D.h. aber auch: zwei *linear* abhängige Variabeln haben eine $Cov(X, Y) \neq 0$. **Achtung:** Zwei abhängige Variabeln 
können theoretisch trotzdem $Cov(X,Y) = 0$ haben, wenn der Zusammenhang **nicht linear** ist (weil Kovarianz
nur ein Mass für lineare Abhängigkeit ist).


Der Wert an sich der Kovarianz ist nicht interpretierbar (??).

Ein weiteres Problem (neben der Linearität) der Kovarianz ist, dass diese sich verändert wenn man eine oder beide
der Zufallsvariabeln mit einer Konstanten multipliziert. Dies ist oft relevant, wenn Zufallsvariabeln verschiedene
Masseinheiten haben bzw. transformiert werden. 


**Korrelation (bzw. Korrelationskoeffizient $r$):**  
Korrelation ist ein weiteres Mass für einen **linearen Zusammenhang**. Im Gegensatz zur Kovarianz, hat sie den Vorteil, 
dass der Wert interpretierbar ist und dieser sich bei linearen Transformationen nicht verändert. Der Korrelationskoeffzient
ist definiert als: 

$$ Corr(X, Y) = \frac{Cov(X, Y}{sd(X)\cdot sd(Y)} = \frac{\sigma_{XY}}{\sigma_X \sigma_Y}$$

Wobei gilt:

$$-1 \le Corr(X, Y) \le 1$$


Der Zusammenhang zu den anderen Massen ist folgender: $Corr(X, Y) = 0$ genau dann wenn gilt $Cov(X, Y) = 0$. Ebenso 
gilt: Wenn zwei Zufallsvariabeln *unabhängig* sind, dann gilt $Corr(X, Y) = 0$, jedoch **nicht** umgekehrt.

Auch die Korrelation bleibt ein Mass der *linearen* Abhängigkeit.


**Regression**  
Eine Regression, ist ein möglicher Weg, einen Zusammenhang genauer zu beschreiben. 



## Für was braucht man OLS, wenn man bereits Schätzer hat für die Parameter aus der Stichprobe?
In der Vorlesung zur Regression werden **zwei** mögliche Methoden vorgestellt, wie man zu Schätzern für die 
Parameter kommt: die Momenten-Methode und die Least Square Methode (OLS). In diesem Fall, liefern beide Schätzer
das gleiche Ergebnis bzw. die Momenten-Methode ist eine ein Least Square Schätzer (und vice versa).