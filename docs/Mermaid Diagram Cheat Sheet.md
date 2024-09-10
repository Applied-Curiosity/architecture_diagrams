Here is an updated Mermaid Diagram Cheat Sheet with standard terminology and newer diagram types:

### Mermaid Diagram Cheat Sheet

#### Flowchart
```mermaid
graph TD
    A[Start] --> B{Is it a weekday?}
    B -- Yes --> C[Work]
    B -- No --> D[Relax]
    C --> E[Finish]
    D --> E[Finish]
```
- **graph TD**: Top-down (TB, LR, RL, BT)
- **[]**: Rectangle
- **{}**: Diamond
https://mermaid.js.org/syntax/flowchart.html

#### Sequence Diagram
```mermaid
sequenceDiagram
    participant A as Alice
    participant B as Bob
    A->>B: Hello Bob, how are you?
    B-->>A: I am good thanks!
    A-xB: Bye!
```
- **participant**: Define participants
- **->>**: Solid arrow
- **-->>**: Dashed arrow
- **-x**: Solid line with X
https://mermaid.js.org/syntax/sequenceDiagram.html

#### Class Diagram
```mermaid
classDiagram
    class Animal {
        +String name
        +int age
        +void eat()
    }
    class Dog {
        +String breed
        +void bark()
    }
    Animal <|-- Dog
```
- **classDiagram**: Define class diagram
- **<|--**: Inheritance
https://mermaid.js.org/syntax/classDiagram.html

#### State Diagram
```mermaid
stateDiagram
    [*] --> Idle
    Idle --> Running
    Running --> [*]
    Running --> Idle
```
- **stateDiagram**: Define state diagram
- **[*]**: Start/End state
https://mermaid.js.org/syntax/stateDiagram.html

#### Gantt Chart
```mermaid
gantt
    title A Gantt Diagram
    dateFormat  YYYY-MM-DD
    section Section
    A task           :a1, 2024-05-01, 30d
    Another task     :after a1  , 20d
    section Another
    Task in sec      :2024-06-12  , 12d
    another task     : 24d
```
- **gantt**: Define Gantt chart
- **title**: Chart title
- **dateFormat**: Date format
- **section**: Section title
https://mermaid.js.org/syntax/gantt.html

#### Pie Chart
```mermaid
pie
    title Pie Chart Example
    "Dogs" : 10
    "Cats" : 20
    "Birds" : 30
```
- **pie**: Define pie chart
- **title**: Chart title
https://mermaid.js.org/syntax/pie.html

#### Entity Relationship Diagram (ERD)
```mermaid
erDiagram
    CUSTOMER ||--o{ ORDER : places
    ORDER ||--|{ LINE-ITEM : contains
    CUSTOMER {
        string name
        string address
    }
    ORDER {
        int orderNumber
        date orderDate
    }
    LINE-ITEM {
        int quantity
        double price
    }
```
- **erDiagram**: Define ERD
- **||--o{**: One-to-many relationship
- **||--|{**: One-to-one relationship
https://mermaid.js.org/syntax/entityRelationshipDiagram.html

#### User Journey
```mermaid
journey
    title User Journey
    section Stage 1
      Alice: 5: Happy
    section Stage 2
      Bob: 3: Neutral
    section Stage 3
      Charlie: 2: Sad
```
- **journey**: Define user journey
- **title**: Journey title
- **section**: Stage section
https://mermaid.js.org/syntax/userJourney.html

#### Quadrant Chart
```mermaid
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
```
- **quadrantChart**: Define quadrant chart
- **x-axis/y-axis**: Define axis
https://mermaid.js.org/syntax/quadrantChart.html

#### Gitgraph
```mermaid
gitGraph
    commit
    branch newBranch
    checkout newBranch
    commit
    checkout main
    merge newBranch
```
- **gitGraph**: Define Gitgraph
- **branch/commit/checkout/merge**: Git operations
https://mermaid.js.org/syntax/gitgraph.html

#### Mindmap
```mermaid
mindmap
    root((Root))
        A
        B
            B1
            B2
        C
```
- **mindmap**: Define mindmap
- **root**: Root node
- **A, B, C**: Child nodes
https://mermaid.js.org/syntax/mindmap.html

#### Timeline
```mermaid
timeline
    title Timeline Example
    2024 : A new year
    2024-05 : An event in May
```
- **timeline**: Define timeline
- **title**: Timeline title
https://mermaid.js.org/syntax/timeline.html

#### Sankey Diagram
```mermaid
---
config:
  sankey:
    showValues: false
---
sankey-beta

Agricultural 'waste',Bio-conversion,124.729
Bio-conversion,Liquid,0.597
Bio-conversion,Losses,26.862
Bio-conversion,Solid,280.322
Bio-conversion,Gas,81.144
Biofuel imports,Liquid,35
Biomass imports,Solid,35
Coal imports,Coal,11.606
Coal reserves,Coal,63.965
Coal,Solid,75.571
District heating,Industry,10.639
District heating,Heating and cooling - commercial,22.505
District heating,Heating and cooling - homes,46.184
Electricity grid,Over generation / exports,104.453
Electricity grid,Heating and cooling - homes,113.726
Electricity grid,H2 conversion,27.14
Electricity grid,Industry,342.165
Electricity grid,Road transport,37.797
Electricity grid,Agriculture,4.412
Electricity grid,Heating and cooling - commercial,40.858
Electricity grid,Losses,56.691
Electricity grid,Rail transport,7.863
Electricity grid,Lighting & appliances - commercial,90.008
Electricity grid,Lighting & appliances - homes,93.494
Gas imports,Ngas,40.719
Gas reserves,Ngas,82.233
Gas,Heating and cooling - commercial,0.129
Gas,Losses,1.401
Gas,Thermal generation,151.891
Gas,Agriculture,2.096
Gas,Industry,48.58
Geothermal,Electricity grid,7.013
H2 conversion,H2,20.897
H2 conversion,Losses,6.242
H2,Road transport,20.897
Hydro,Electricity grid,6.995
Liquid,Industry,121.066
Liquid,International shipping,128.69
Liquid,Road transport,135.835
Liquid,Domestic aviation,14.458
Liquid,International aviation,206.267
Liquid,Agriculture,3.64
Liquid,National navigation,33.218
Liquid,Rail transport,4.413
Marine algae,Bio-conversion,4.375
Ngas,Gas,122.952
Nuclear,Thermal generation,839.978
Oil imports,Oil,504.287
Oil reserves,Oil,107.703
Oil,Liquid,611.99
Other waste,Solid,56.587
Other waste,Bio-conversion,77.81
Pumped heat,Heating and cooling - homes,193.026
Pumped heat,Heating and cooling - commercial,70.672
Solar PV,Electricity grid,59.901
Solar Thermal,Heating and cooling - homes,19.263
Solar,Solar Thermal,19.263
Solar,Solar PV,59.901
Solid,Agriculture,0.882
Solid,Thermal generation,400.12
Solid,Industry,46.477
Thermal generation,Electricity grid,525.531
Thermal generation,Losses,787.129
Thermal generation,District heating,79.329
Tidal,Electricity grid,9.452
UK land based bioenergy,Bio-conversion,182.01
Wave,Electricity grid,19.013
Wind,Electricity grid,289.366

```
- **sankey**: Define Sankey diagram
- **== $value ==>**: Flow with value
https://mermaid.js.org/syntax/sankey.html

#### XY Chart
```mermaid
xychart-beta
    title "Sales Revenue"
    x-axis [jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec]
    y-axis "Revenue (in $)" 4000 --> 11000
    bar [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]
    line [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]

```
- **xyChart**: Define XY chart
- **"Series"**: Data series
https://mermaid.js.org/syntax/xyChart.html
### Tags
#diagram #mermaid #cheatsheet 