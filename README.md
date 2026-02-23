# Object-Oriented Analysis & Design Assignment
**Course:** Object-Oriented System Development  
**Group:** [Insert Group Name]  

---

## 1. Inheritance vs. Interface
Logic: `Shape` is an interface, `Polygon` implements it, and `Square` inherits from `Polygon`.

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
[!IMPORTANT]Reasoning: We used an interface for Shape because it defines a pure "Capability." This allows different types of objects to be drawn without forcing them into a strict polygon hierarchy.2. Aggregation vs. CompositionCase: Book and its Pages.Code snippetclassDiagram
    class Book
    class Page
    Book "1" *-- "many" Page
Relationship: Composition (Represented by the filled diamond).Justification: A Page cannot exist without the Book. If the Book object is deleted, the Pages are destroyed as well.
3. Java: The doIt() MethodImplementation of the Thing1 interface.Javapublic class Thing2 implements Thing1 {
    @Override
    public void doIt() {
        System.out.println("Thing2 implementation of doIt logic.");
    }
}
4. State Machine: Media PlayerUsing a Superstate for organization.Code snippetstateDiagram-v2
    [*] --> Idle
    state ON {
        Idle --> Playing
        Playing --> Idle
        Playing --> Rewinding
        Rewinding --> Playing
    }
    ON --> [*]
5. Orthogonal RegionsScenario: A Smartphone handling a Call and Charging simultaneously.Benefit: It allows us to track two independent behaviors without creating dozens of "combination" states. This is the best way to handle complexity in modern UI systems.6. Sequence Diagram: Car OperationsChronological order of sub-system activation.Code snippetsequenceDiagram
    participant D as Driver
    participant S as Starter
    participant L as Lights
    participant A as Accelerator

    D->>S: turnKey()
    S-->>D: statusReady
    D->>L: switchOn()
    D->>A: pressPedal()
7. Polymorphism: Static vs. DynamicStatic: Method Overloading (Compile-time).Dynamic: Method Overriding (Runtime).Example (Static):Javapublic class Builder {
    public void create(String name) { }
    public void create(String name, int id) { }
}
8. ATM StatesIdle: Waiting for card.Authenticating: PIN check.Selection: Menu navigation.Dispensing: Cash delivery.9. UML RelationshipsStatementRelationship"Department has Professors"Aggregation"Car is a Vehicle"Generalization"House is made of Rooms"Composition10. System StrategyWhy Use Cases are not enough:Use Case diagrams are only for Requirements. They don't show the Variables or the Logic Flow. To actually write code, a developer needs the Class Diagram to see the data structure and a Sequence Diagram to see how objects talk to each other.
---
