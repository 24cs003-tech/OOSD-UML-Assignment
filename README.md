# Object-Oriented Analysis & Design Assignment
**Group Project** | **Course:** Object-Oriented System Development

---

## 1. Inheritance vs. Interface
We modeled the relationship between Shape, Polygon, and Square.



```mermaid
classDiagram
    class Shape {
        <<interface>>
        +draw()
    }
    class Polygon {
        +int numSides
    }
    class Square {
        +double sideLength
    }
    Shape <|.. Polygon
    Polygon <|-- Square
Reasoning: We used an interface for Shape because it acts as a contract for the draw() method. This allows us to add non-polygon shapes like Circles later without breaking the system.2. Aggregation vs. CompositionCase Study: The relationship between a Book and its Pages.Code snippetclassDiagram
    class Book
    class Page
    Book "1" *-- "many" Page
Justification: We chose Composition (filled diamond). A Page belongs to one Book; if the Book is destroyed, the Pages are also destroyed.3. Java Implementation: doIt()Implementation of the Thing1 interface requirement.Javapublic class Thing2 implements Thing1 {
    @Override
    public void doIt() {
        System.out.println("Thing2 performing the doIt action.");
    }
}
4. State Machine: Media PlayerUsing an "ON" Superstate to organize the internal states of the player.Code snippetstateDiagram-v2
    [*] --> Idle
    state ON {
        Idle --> Playing
        Playing --> Idle
        Playing --> Rewinding
        Rewinding --> Playing
    }
    ON --> [*]
5. Complexity: Orthogonal RegionsScenario: A Smartwatch tracking a workout while syncing data.Benefit: Orthogonal regions allow these two independent behaviors to run in parallel on one diagram, preventing "state explosion" where you'd have to draw every possible combination of states.6. Sequence Diagram: Car SystemsThe chronological handshake between the driver and the car components.Code snippetsequenceDiagram
    participant D as Driver
    participant S as Starter
    participant L as Lights
    participant A as Accelerator

    D->>S: turnKey()
    S-->>D: statusReady
    D->>L: switchOn()
    D->>A: pressPedal()
7. Polymorphism: Static vs. DynamicStatic: Overloading (Compile-time). Same method name, different parameters.Dynamic: Overriding (Runtime). Child class provides specific implementation.Code Example (Static):Javapublic class Builder {
    public void create(String name) { }
    public void create(String name, int id) { }
}
8. ATM StatesIdle: Waiting for card.Authenticating: PIN verification.Selection: Menu choice.Dispensing: Cash out.9. Class Relations IdentificationStatementRelationshipNotation"Dept has Professors"AggregationHollow Diamond"Car is a Vehicle"GeneralizationHollow Arrow"House is made of Rooms"CompositionFilled Diamond10. System Modeling StrategyWhy Use Cases aren't enough:Use Case diagrams show what a user wants, but not how the code works. A developer needs Class Diagrams for the variables/structure and Sequence Diagrams for the chronological order of method calls to actually build the system.
---
