# Lineare Regression

## Idee
Ziel der Regression ist die genauere Beschreibung des Zusammenhangs zweier (oder mehr) Zufallsvariabeln. "Zusammenhang" 
hier bedeutet, dass angenommen wird, dass die Zufallsvariablen **nicht** unabhängig sind (??). Bei der *linearen* Regression
wird zudem ein linearer Zusammenhang angenommen.

Allgemein wird angenommen, dass gilt

$$Y = f(X) + \epsilon$$

Mit den zwei Zufallsvariabeln $Y, X$, der linearen Funktion $f(X)$ und dem Störterm $\epsilon$. $X$ kann mehrere
Dimensionen haben, d.h. es können auch mehrere Variabeln sein. $Y$ wird abhängige (response/ Regressand / erklärte)
Variable genannt und $X$ unabhängige (predictor / covariate / feature / control / erklärende), 
was hat nichts mit stochastischer Abhängigkeit zu tun. Das Vorgehen ist nun, da $f(X)$ unbekannt
ist, aufgrund von Daten (bzw. einer Stichprobe) $f$ durch eine Funktion $\hat f$ zu schätzen. 
D.h. es wird ein *Populationsmodell* angenommen, 
welches dann (bzw. die unbekannten Parameter) geschätzt werden. 

Anders ausgedrückt: (hauptsächlich in der Ökonometrie) interessiert 

$$ E(y \vert x) $$

der bedingte Erwartungswert. 

## Bivariate Regression
Die bivariate Regression beschreibt den Zusammenhang von **zwei** Variabeln. Als Populationsmodell wird angenommen:

$$ y = \beta_0 + \beta_1 x + \epsilon$$

Dabei wird angenommen, dass in der Population gilt:

1. $E(\epsilon) = 0$, d.h. im Schnitt spielt Zufall keine Rolle. 
2. $E(\epsilon \vert x) = 0$, d.h. im Schnitt ist der Störterm gleich über alle Werte von $x$. $\epsilon$ und $x$ sind **mean independent** (jedoch nicht stochastisch unabhängig). Dadurch werden *ceteris paribus* interpretation möglich, weil so $\epsilon$ unverändert bleibt, wenn $x$ sich verändert. Dies impliziert $Cov(x,\epsilon) = E(x\epsilon) = 0$ (aber nicht umgekehrt), ist aber eine stärkere Annahme da Kovarianz nur ein lineares Mass ist. 

Dadurch kann man auch die **population regression function (PRF)** herleiten:

$$E(y\vert x) = \beta_0  +\beta_1 x$$

da gilt $E(\epsilon \vert x) = 0$. Dies ist eine *lineare Funktion*, deshalb ergibt sich: eine Einheit Veränderung von $x$
ändert den Erwartungswert von $y$ um $\beta_1$.

Nun will man die Parameter $\beta_0$ und $\beta_1$ mithilfe einer Stichprobe schätzen (meistens ist nur $\beta_1$ 
interessant). Die Schätzer können mithilfe der **Momenten-Methode** oder der **Kleinsten Quadrate Methode (OLS)** 
hergeleitet werden.

Dadurch ergibt sich für $\beta_1$:

$$\hat \beta_1 = \frac{Cov(x,y)}{Var(x)}$$

**Interpretation:** Im bivariaten Fall ist eine kausale Interpretation unwahrscheinlich (ausser bei randomisierten 
Experimenten). Deshalb: eine Veränderung von $x$ um eine Einheit ist **assoziiert** mit einer Veränderung von 
$\hat y$ um $\hat \beta_1$.


**Goodness-of-fit ($R^2$):**
Ein Mass für die Güte der Regression, gibt an, wie gut die geschätzte Regressionslinie die Stichprobe beschreibt: 

$$ R^2 = \frac{\sum_{i=1}^n (\hat y_i - \bar y)^2}{\sum_{i=1}^n (y_i - \bar y)^2} = 1 - \frac{\sum_{i=1}^n \hat u_i^2}{\sum_{i=1}^n (y_i - \bar y)^2}$$

mit **fitted values** $\hat y_i$, Residuen $\hat u_i$, Stichprobenwerte $y_i$, und Stichprobenmittelwert $\bar y$. 


**Statistische Eigenschaften des OLS Schätzers:**  

- Erwartungstreue (Unbiasedness): $E(\hat \beta) = \beta$ (ist erfüllt gegeben 4 Annahmen, am wichtigsten wenn $E(u\vert x) = 0$)
- Konsistenz: wenn $n \to \infty$, dann $\hat \beta \to \beta$
  - Effizienz: Varianz des Schätzers soll möglichst klein sein
    - Übliche Annahme: **Homoskedastizität** $Var(u\vert x) = \sigma^2$, d.h. die Varianz des Fehlerterms ist konstant für alle $x$.
    - **Fehlervarianz (error variance)** $\sigma^2$. **Standardabweichung des Fehlers** $\sigma$
    - Mithilfe der Fehlervarianz, kann die Stichprobenvarianz der Schätzer $Var(\hat \beta_1)$ und $Var(\hat \beta_0)$ hergeleitet werden. Dazu braucht man einen Schätzer $\hat \sigma^2$.
    - **Root Mean Squared Error (RMSE)**: $\hat \sigma = \sqrt{\hat \sigma^2}$, **Standardfehler $\hat \beta_1$** $se(\hat \beta_1) = \hat \sigma / \sqrt{\sum(x_i - \bar x)^2}$
    - **Heteroskedastizität**: OLS Schätzer auch unbiased, aber Standardfehler des Schätzers sind verzerrt


**Funktionale Form:**  
Die Parameter verändern sich folgendermassen, wenn die Masseinheiten geändert werden:

- Veränderung von $y$, mit $\tilde y = c \cdot y$, verändern sich die Parameter mit Faktor $c$, also $c \cdot \beta$
- Veränderung von $x$, mit $\tilde x = d \cdot x$, verändern sich die Parameter mit Faktor $1/d$, also $1/d \cdot \beta$


**Modellierung von nicht-linearen Zusammenhängen:**  

| Modell      | Abhängige Variable | Unabhängige Variable | Interpretation von $\beta_1$          |
|-------------|--------------------|----------------------|---------------------------------------|
| level-level | y                  | x                    | $\Delta y = \beta_1 \Delta x$         |
| level-log   | y                  | ln(x)                | $\Delta y = (\beta_1/100)\% \Delta x$ |
| log-level   | ln(y)              | x                    | $\% \Delta y = 100 \beta_1 \Delta x$  |
| log-log     | ln(y)              | ln(x)                | $\% \Delta y = \beta_1 \% \Delta x$   |


## Multiple Regression

Die bivariate Fall ist meistens die Ausnahme, da meistens mehrere Faktoren einen Einfluss auf $y$ haben. Werden nicht
alle Faktoren berücksichtigt, so ist die Schätzung (von $\beta_1$) verzerrt, d.h. der Einfluss von $x_1$ wird über- oder
unterschätzt. Für eine unverzerrte Schätzung, müssen deshalb alle relevanten Faktoren berücksichtigt werden, ausser
diese sind **unkorreliert** mit $x_1$.

In den meisten Fällen ist man nur am Parameter $\beta_1$ interessiert und die restlichen Variabeln werden als *Kontrollvariabeln*
eingeführt. Die OLS Mechanik würde jedoch eine *ceteris paribus* Interpretation für alle Variabeln erlauben. 


Das bivariate Modell kann erweitert werden mit: 

$$y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + ... + \beta_k  x_k + u$$

Die Schätzer für die Parameter können analog dem bivarianten Modell mit OLS hergeleitet werden. 

**Ceteris paribus**  
Die Mechanik von OLS (unbgeründet ??) stellt sicher, dass eine **ceteris paribus** Interpretation möglich ist. D.h. 
wie verändert sich $y$, wenn sich $x_1$ verändert, gegeben *alle anderen Faktoren bleiben gleich* (diese Interpretation
ist für alle $x$ möglich, aber meistens interessiert nur $x_1$). Diese Interpretation stimmt selbst dann, wenn gilt: 
$E(u \vert x_1, x_2, ..., x_k) \neq 0$. Gilt hingegen: $E(u \vert x_1, x_2, ..., x_k) = 0$, so werden **kausale** 
Interpretationen möglich. 

Die Mechanik von OLS stellt ausserdem sicher, dass $\beta_1$ nur der Anteil vom Effekt von $x_1$ auf $y$ quantifiziert, 
der mit den anderen Faktoren $x_2,..., x_k$ unkorreliert ist.

"Alle anderen Faktoren fixiert halten" bedeutet hier, dass durch die Mechanik der Regression nur ein Datensatz verwendet
werden kann und nicht jeder Faktor einzeln erhoben werden muss. 

**Achtung:** eine ceteris paribus Interpretation ist aber logisch nicht immer möglich, d.h. wenn gewisse $x$ voneinander
abhängig sind. 


**Eigenschaften des Schätzers**  
Der OLS Schätzer ist **erwartungstreu** unter folgenden Annahmen:

- Populationsmodell ist linear in Parametern
- Zufallsstichprobe der Grösse $n$ aus Population
- Der Störterm $u$ hat den Erwartungswert Null gegeben alle Werte der unabhängigen Variabeln ($E(u \vert x_1, x_2, ..., x_k) = 0$)
- Keines der $x$ ist konstant und es gibt keine exakte lineare Beziehung zwischen den $x$ (keine perfekte Multikolinarität)

Unter der zusätzlichen Annahme (zusammengenommen **Gauss-Markov**)

- Homoskedastizität $Var(u\vert x_1, x_2, ..., x_k)= \sigma^2$

ist der OLS Schätzer der Schätzer mit der kleinsten Varianz unter allen erwartungstreuen, linearen Schätzern. 

Aber: 

- je grösser Fehlervarianz $\sigma^2$, desto grösser die Varianz des OLS Schätzers (d.h. desto unpräziser)
- grösser Stichprobengrösse $n$ reduziert Varianz des OLS Schätzers
- Problem Multikoliniarität: je grösser $R_j^2$, desto mehr Variation von $x_j$ wird durch die anderen $x$ erklärt; d.h. desto unpräziser wird die Schätzung (da nur der unkorrelierte Teil verwendet wird für die Schätzung); aber: Multikolinarität ist keine Verletzung von Gauss-Markov; bedeutet oft: Modell ist nicht richtig spezifiziert


**Omitted Variable Bias**  
Werden nicht alle relevanten Faktoren (auf $y$) in der Regression berücksichtigt, führt dies zu einem Omitted 
Variable Bias. D.h. der Schätzer $\beta_1$ ist verzerrt und unter- oder oberschätzt den Effekt von $x_1$ auf $y$.
Unberücksichtigte Faktoren haben nur dann keinen verzerrenden Effekt, wenn sie entweder **unkorreliert** mit $x_1$
sind oder keinen Einfluss auf $y$ haben. 

**Aber Achtung:** blindes Einfügen von zahlreichen *recht-hand* Variabeln kann zu **bad controls** führen, welche (zwar
nicht zu einem verzerrt Schätzer führen), aber eine kasuale Interpretation verhindern. Bspw. wenn gewisse Faktoren 
voneinander Abhängig sind. 

## Kausale Analyse (mit einer Dummy Variabel)
Eine Regression mit einer Dummy Variabel (0 oder 1 als Outcome), kann unter Umständen kausal interpretiert werden. Dazu
wird die Welt in zwei Gruppen geteilt: die **treatment Gruppe** (welche eine Invernention erhalten hat) und die 
**Kontrollgruppe** welche keine Intervention erhalten hat. Der Effekt der Intervention (**treatment effect**) wäre dann
Ergebnis treatment minus Ergebnis Kontroll. 

Keine Beobachtung kann aber gleichzeitig in beiden Gruppen sein. Deshalb führt man sogenannte *potentielle Ergebnisse*
(**counterfactual or potential outcome**) ein. $y_i(1)$ sind die individuellen Ergebnisse mit Treatment und $y_i(0)$ 
ohne Treatment. Der individuelle Treatmenteffekt ist dann gegeben durch: 

$$ te_i = y_i(1) - y_i(0)$$

bzw. der **Average Treatment Effect ATE**:

$$ t_{ate} = E[y_i(1)] - E[y_i(0)]$$

**Konstanter (bzw. gleichverteilter) Treatmenteffekt**  
Angenommen, der individuelle Treatmenteffekt ist **konstant** mit $te_i = \tau$, kann basierend darauf ein 
Regressionsmodell für die Population hergleitet werden:

$$y_i = \beta_0 + \beta_1 d_i + u \text{ mit } \beta_1 = \tau$$

Damit der OLS Schätzer unverzerrt ist muss gelten $E[u_i(0) \vert d_i] = 0$. Damit kann man herleiten, dass gelten
muss $E[y_i(0)\vert d_i] = E[y_i(0)]$, d.h. das potentielle Ergebniss $y_i(0)$ muss unabhängig von Treatment $d_i$, also
$E[y_i(0)]$ ist in der Kontroll- und Treatmentgruppe gleich gross (??).

**Nicht konstanter Treatmenteffekt:** ist der Treatmenteffekt nicht konstant über die Population, so muss zudem gelten, 
dass $E[y_i(1)\vert d_i] = E[y_i(1)]$, d.h. *beide* potentiellen Ergebnisse müssen stochastisch unabhängig sein 
von $d_i$.

**Achtung:** Dies ist üblicherweise nur der Fall bei einem randomisierten Experiment. 


**Nicht randomisierte Daten**  
Effekt kann dann *kausal* interpretiert werden, wenn die **Conditional Independence Assumption (CIA)** gilt. D.h. man 
kann gleichzeitig alle Faktoren $x$ beobachten, die gleichzeitig die potentiellen Ergebnisse und die Entscheidung für das
Treatment beeinflussen. Formal $[y_i(0), y_i(1)]{\perp \!\!\! \perp} d_i\vert x$

**Konstanter Treatmenteffekt:** Angenommen der Treatmenteffekt ist konstant über die Population mit $\tau$ *und* 
$E[y_i(0) \vert x_i]$ kann als lineare Funktion geschrieben werden, so gilt für die Regression

$$y_i = \alpha + \tau d_i + \textbf{x} \gamma + v_i$$


Wichtig hierbei: die schwächere Annahme CIA fokussiert auf die Identifizierung eines kausalen Effekts von $d$ und nicht
auf die Identzifizerung aller Effekte. D.h. $x$ sind nur **Kontrollvariabeln** und die Parameter haben keine kausale
Interpretation. $x$ darf keine **Mediatoren** (ist bad control) enthalten, d.h. Variabeln, die selbst Ergebnis des Treatments sind. 


## Inferenz
Unter den Gauss-Markov Annahmen ist OLS der Best Linear Unbiased Estimator (nicht bewiesen?), d.h. **erwartungstreu**
und **minimale Varianz**. Für Tests braucht man aber eine komplette Verteilung des Schätzers, deshalb führt man eine
weitere (sehr starke) Annahme ein: **Normalität**, d.h. der Fehlerterm in der Population ist unabhängig von den 
erklärenden Variablen und **normalverteilt**, also $u \sim N(0, \sigma^2)$. Zusammengenommen werden diese Annahmen
als klassische Annahmen für lineare Modelle bezeichnet (CLM).

Testen:  
Für das Durchführen der von Hypothesentest gilt unter den oben aufgeführten Annahmen, die folgende Teststatistik:

$$(\hat \beta_j - \beta_j)/se(\hat \beta_j) \sim t_{n-k-1}$$

D.h. da die Standardabweichung in der Population unbekannt ist, kann diese nur durch $\hat \sigma$ geschätzt werden, 
was zu einer $t$-Verteilung führt. 


Danach kann mithilfe des kritischen Werts, des $p$-Werts, oder eines Konfidenzintervalls ein Test durchgeführt werden.

Für das Testen von multiplen Hypothesen kann ein $F$-Test verwendet werden (??).

## Funktionale Form
**Natürlicher Logarithmus**  
Wird oft eingesetzt, wenn $y$ heteroskedastisch oder schief. Reduziert den Einfluss von Outlier. Interpretation 
vom Effekt auf $y$ ändert sich (entweder Elastizität oder prozentuale Veränderung).

**Quadratische Modelle**  
Verwendet um den marginalen Effekt einer Variable zu bestimmen. 

**Interaktionsterme**  
Wird verwendet wenn der Effekt einer Variable vom Wert einer anderen Variable abhängt. 

## Anpassungsgüte
$R^2$ steigt immer, wenn mehr Regressoren ins Modell eingeführt werden. Deshalb adjusted $R^2$: $\bar R^2$.
Damit können zwei *ungenestete* Modelle miteinander verglichen werden. **Aber** nicht nur auf Anpassungsgüte 
konzentrieren: wenn ökonomische Theorie sagt, dass eine Variable ins Modell gehört, dann muss sie vorkommen. 
Aber aufpassen auch für "bad controls".







