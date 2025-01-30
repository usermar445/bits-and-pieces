# Part 5: Ethics and Data Science

## Basics


**Trade-off**
Often a trade-off between fairness and performance. And domain-specific. 

## Case studies
**Fairness: NSA's skynet program**  
False negative rate of $0.18\%$ but on a whole country has sever consequences.

**Fairness: Amazon Prime racist algorithm**  
Same-day delivery not available for certain people. 

**Fairness: Compas Case**  
Risk asssessment of reoffending. 

Problems: 

- taken full ranges of crimes into account, precision dropped to 60%
- questionnaire questionable
- almost same precision among groups, but different FPR and FNR
- satisfied Demographic parity but not EO

**Privacy: Facebook emotional contagion study**  
Massive experiment with emotions. 

Problems:

- Facebook did not get real consent
- psychological manipulation without knowing
- Facebook claims they got consent

**Privacy: De-anonymization of Netflix**  
De-anonymization of users for Netflix prize. 

**Transparancy: EVAAS-case**  
Evaluation of teachers. 


**Strategic classification: health care algorithms**  

- Problem: gaming effects
- problem: risk to fairness

**Predictive policing**  

- Lack of transparancy
- if biased data is used, bias is reproduced
- shapes future data: more police presence, more liklier to detect crime

**Link-recommendation algorithms**  
Isolated communities build.

## Fairness
**Types**  

- group fairness
- individual fairness

**What is fairness?** Connected to bias, seen as non-discrimination:

- *direct* discrimination: because of race, etc. 
- *indirect* discrimination: disproportionately impacts people of a certain group

Both a technical and social issue. 

**Measurments**

- equal precision
- equal FPR/FNR among groups
- equal accuracy
- Demographic parity: probability of bein labeled positive is equal for all groups
- Equalised odds: FPR *and* FNR is equal among groups


**Two uses**

- fairness metrics
- fairness intervention

**Demographic parity**  
Positive (and negative) predictions are balanced between groups = demographics of these having positive label are equal
to demographics of whole dataset.

Advantage: easily understood

Problems: assumes no difference between group

**Equalised odds**  
False labels must be equally distributed among groups (FPR and FNR).

Problems: more difficult to understand, depends on true labels


**Other approaches**  

- Fairness through unawarness: can increase unfairness, no insight
- Causal fairness: forbids causal path from sensitive attribute to decision

**Types of bias**  

- pre-existing bias: society; introduced through data
- technical bias: from technical constraints; model selection and choice
- emergent bias: context of use; can lead to self-perpuating dynamics and bias; e.g. predictive policing
- societal vs. statistical bias

**When to tackle bias**  

- pre-processing: transform training data so that bias is removed
- in-processing: modify learning algorithm during training, e.g. regularizer term
- post-processing: correct model classification after training (often less accuracy); e.g. setting different thresholds of classifiers for different groups

**Fairness in clustering**  
In-processing approach: *Balanced clusters* (using *fairlest*, i.e. point that are close but from different groups)

## Privacy
Privacy is fundamental right (secrecy and autonomy), right about information (limit, control, contextual integrity). 

Depends on **informational norms** that depend on context. If it is appropriate to context. 

Integrity of dealing with information and context dependent. 

**Public data**  
Does not mean you can use it.

**Anonymization**  
Different techniques; 87% of people in the US can be identified with zip code, birth date, and gender. 

**k-anonymity:** each sequence of quasi-identifiers has at least $k$ occurences. *Problems*: combining data.

**Differential Privacy**  
Adds noise to outputs. People accessing data set won't learn much about an individual if or if not this individual is 
part of the data set. 

$\epsilon$-differential private with $1/\lambda$. Increase $\lambda$ leads to more privacy but less accuracy. 


## Transparency
Understand and accept decision. But: explainability for whom?

Trade-offs: transparancy and accuracy, or trade-secrets, and privacy. 

Not enough to tackle discrimination. 

**Types**  

- model-based interpretability: choose simpler model; use regularization; domain-based feature engineering
- post-hoc interpretability: extract interpretation

**Post-hoc**  
local explanations: **LIME** local interpretable model-agnostic explanations