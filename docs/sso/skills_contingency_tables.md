# Skills contingency tables

**Overview**

Test on contingency tables:

- $\chi^2$ test
- Homogenity test
- Fisher test on contingency tables 




### $\chi^2$-Test
**Applicability**  
Contingency tables with frequency counts.

**Notation**   
$O$ observed frequency, $E$ expected frequency

**Requirements**

1. Random sample
2. Contingency table with frequency counts
3. For every cell, the expected frequency $E \geq 5$. 

**Test statistic**

$$\chi^2 = \frac{(O-E)^2}{E}$$

With $E = \frac{(\text{row total}) (\text{ column total})}{\text{grand total}}$.

**Critical values**  
Use $\chi^2$ distribution table (always right sided).  
Degrees of freedom: $df = (r-1)(c-1)$.

**Procedure**

1. Calculate $E$
2. Calculate test statistic, execute test.


### Homogenity test
Same procedure

### Fishers test
Use software.