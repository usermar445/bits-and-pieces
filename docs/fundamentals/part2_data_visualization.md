# Part 2: Data Visualization

## Principles of Data Visualization

Rules:

1. Know your audience: beware curse of expertise
2. Identify your message before: 1 figure = 1 message 
3. Adapt figure to medium: talk vs. publication 
4. Caption is important: guide audience trough 
5. Do not trust the defaults: fine-tune to specific context 
6. Use color effectively: reason for color? 
7. Do not mislead audience: scale and visual perception important 
8. Avoid "chartjunk": unnecessary visual elements 
9. Choose message over beauty 
10. Know and use the right tool 

**Color**  

- color implies categorical
- sequential vs. diverging: sequential more intuitive; diverging only when meaningful middle point

## Matplotlib

**Fig vs. axes vs. axis**: Figure can contain many axes; axis = axis of a plot

**Two interfaces**  

- `pyplot` interface: (MATLAB style) `plt.subplot()`
- object-oriented interface: `fig, ax = plt.subplots()`

(see cheatsheet)

## Additional libraries

**Seaborn**  

Advantages: 1) pre-defined themes to matplotlib plots, 2) easy to integrate with DataFrames

Examples:

- `sns.jointplot()`


**Geopandas**  
Adds geometry column to dataframe.

**NetworkX** 
To visualize network data

## Visual and media analytics

CRISP model limitation: 

- no explicit role for user
- visualization of data is not considered
- almost no feedback loops

**Visual Analytics tool**: goes deeper (than dashboard), intelligent tool that assists user; integration between
model and visualization through user interaction


**Basic Visual Analytics model**  
Data -> Visualization (user interaction) + Model (parameter refinement) -> Knowledge  + Feedback

Steps:

- Data preparation
- Visualization: user interaction
- Interaction between visualization + model: model building from visualization 
- Interaction between visualization + model: model driving visualization
- Model: parameter refinement
- Both: leading to knowledge
- Feedback loop

Limitations:

- Model is system driven; no human factor
- not several feedback loops
- not for deep-learning


**Sensemaking process**  
Structuring unknown data into a framework enabling us to comprehend, understand, explain, attribute, extrapolate, and
predict

Loops: 

- Foraging loop
- Sensemaking loop
- Reality/policy loop

External data -> shoebox (unordered, loosely filtered, bottom-up, top-down) -> evidence file (snippets, leading/confirming
to hypothesis) -> Schema (structured, well-organized collection of information) -> Hypotheses -> Presentation

Feedback loops everywhere

**Expanding VA pipeline**  

Expand **Knowledge**: Finding, insight, hypothesis, action

**Takeaways**:  

- VA systems domain specific and task-specific
- VA modelling techniques: difficult make model interactive; therefore, lag behind 3-5 years

**Multimedia Analytics**  
Mutlimedia Analytics = Multimedia Analysis + expanded VA model

**Semantic gap**: machines good at large data set, gap narrows in last 20 years


**Visualizing**  
Techniques: grid, similarity space, similarity-based, spreadsheet, thread-based

Desirable aspects: efficiency, navigability, heterogeneous data support

**Pragmatic gap**
Analytical categorization vs. classification

Tasks fall on exploration - search axis, all part of analytical categorization

"Secret ingredient": interactive learning

plus Scale a problem

Limitations of original pipeline: 1) system driven, 2) focus on images, 3) knowledge capurted as categories but not with relations

Therefore: hypergraphs to capture knowledge (categories + relations)

Model

- Data -> Visualization + Model -> Finding + Action -> Insight + Hypothesis -> Knowledge