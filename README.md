# Group Project: Object-Oriented Analysis & Design (OOAD)
**Course:** Object-Oriented System Development  
**Focus:** UML 2.0 Notations & Java Implementation  

---

## 1. Hierarchy: Inheritance vs. Interface
We analyzed the relationship between a `Square`, a `Polygon`, and a `Shape`. Our design goal was to ensure behavioral consistency while allowing for future expansion.

### UML Class Diagram


```mermaid
classDiagram
    class Shape {
        <<interface>>
        +draw() void
    }
    class Polygon {
        +int numSides
        +draw() void
    }
    class Square {
        +double sideLength
        +draw() void
    }
    Shape <|.. Polygon : realization
    Polygon <|-- Square : inheritance
[!IMPORTANT]Group Reasoning: We chose an Interface for Shape to define a "Contract." While all Polygons are Shapes, not all Shapes (like a Circle) follow Polygon logic. Using an interface keeps the system decoupled and flexible for new geometric types.2. Ownership: Aggregation vs. CompositionCase Study: The relationship between a Book and its Pages.Relationship Type: CompositionJustification: A Page cannot logically exist without its parent Book. In our system, the lifecycle of the Page is bound to the Book; if the Book is destroyed, the Pages are cleared from memory.Code snippetclassDiagram
    class Book
    class Page
    Book "1" *-- "many" Page : Composition
3. Java Realization: The doIt() MethodWe implemented a concrete realization for the Thing2 class to demonstrate interface compliance.Java/**
 * Thing2 implementation of the Thing1 interface contract.
 */
public class Thing2 implements Thing1 {
    
    @Override
    public void doIt() {
        // Implementation logic decided during group session
        System.out.println("Executing system-specific logic for Thing2.");
    }
}
[!NOTE]Observation: If Thing2 were an abstract class, we wouldn't need to implement doIt() immediately. However, it would prevent us from creating an instance of Thing2 directly.4. Behavioral Logic: Media Player State MachineTo minimize complexity, we grouped the active states into an "ON" Superstate. This simplifies global transitions like "Power Off."Code snippetstateDiagram-v2
    [*] --> Idle
    state ON_SUPERSTATE {
        Idle --> Playing : press play
        Playing --> Idle : press stop
        Playing --> Rewinding : press rewind
        Rewinding --> Playing : resume
    }
    ON_SUPERSTATE --> [*] : Power Off
5. Complexity Reduction: Orthogonal RegionsScenario: A Smartwatch tracking an Exercise while simultaneously Monitoring Heart Rate.[!TIP]Why it's better: Without orthogonal regions, we would have to draw a state for every combination (e.g., "Running + High Heart Rate," "Walking + Low Heart Rate"). Concurrent regions allow us to model independent behaviors on a single chart without "State Explosion."6. Sequence of Operations: Car Sub-systemsThis diagram tracks the chronological communication between the Driver and the sub-systems.Code snippetsequenceDiagram
    actor Driver
    participant S as Starter
    participant L as Lights
    participant AC as AirCon
    participant A as Accelerator

    Driver->>S: ignite()
    S-->>Driver: Engine Ready
    Driver->>L: switchOn()
    Driver->>AC: setTemp(22)
    Driver->>A: press()
7. Polymorphism: Static vs. DynamicWe compared how the JVM handles method resolution.Static: Resolved at compile-time (Overloading).Dynamic: Resolved at runtime (Overriding).Static Example (Method Overloading):Javapublic class Processor {
    public void create(String name) {
        System.out.println("Item: " + name);
    }
    
    public void create(String name, int id) {
        System.out.println("Item: " + name + " ID: " + id);
    }
}
8. Real-World Modeling: ATM StatesWe identified four discrete states for an ATM system:IDLE: Waiting for card input.AUTH_PENDING: Validating user credentials.SELECTION: Navigating the transaction menu.DISPENSING: The hardware process of delivering cash.9. Relationship Summary TableStatementRelationship TypeNotation"A Department has many Professors"AggregationHollow Diamond"A Car is a Vehicle"GeneralizationHollow Arrow"A House is made of Rooms"CompositionFilled Diamond10. Strategy: Beyond Use CasesA Use Case diagram captures the "What" but lacks the "How." For technical implementation, it is insufficient because:It does not define Internal Data Structure (Attributes/Methods).It does not define the Chronological Order of events.Conclusion: Developers require Class and Sequence diagrams to understand the handshake between objects and manage the system's memory and state.
---
