# Group Project: Object-Oriented Analysis & Design (OOAD)
**Course:** Object-Oriented System Development  
**Status:** Final Submission  

---

## 1. Hierarchy: Inheritance vs. Interface
We analyzed the relationship between a `Square`, a `Polygon`, and a `Shape`. Our goal was to ensure behavioral consistency while allowing for future expansion.



```mermaid
classDiagram
    class Shape {
        <<interface>>
        +draw()
    }
    class Polygon {
        +int numSides
        +draw()
    }
    class Square {
        +double sideLength
        +draw()
    }
    Shape <|.. Polygon
    Polygon <|-- Square
[!IMPORTANT]Group Reasoning: We chose an Interface for Shape to define a "Contract." While all Polygons are Shapes, not all Shapes follow Polygon logic. Using an interface keeps the system flexible for new geometric types like Circles.2. Ownership: Aggregation vs. CompositionScenario: The relationship between a Book and its Pages.Relationship Type: CompositionJustification: A Page cannot logically exist without its parent Book. The lifecycle of the Page is bound to the Book; if the Book is destroyed, the Pages are cleared from memory.Code snippetclassDiagram
    class Book
    class Page
    Book "1" *-- "many" Page
3. Java Realization: The doIt() MethodBelow is the concrete implementation for the Thing2 class to demonstrate interface compliance.Java/**
 * Thing2 implementation of the Thing1 interface.
 */
public class Thing2 implements Thing1 {
    
    @Override
    public void doIt() {
        // Implementation logic decided during group session
        System.out.println("Executing system-specific logic for Thing2.");
    }
}
[!NOTE]Observation: If Thing2 were an abstract class, we wouldn't need to implement doIt() immediately. However, we noted that you cannot instantiate an abstract class directly.4. Behavioral Logic: Media Player State MachineTo minimize complexity, we grouped the active states into an "ON" Superstate. This simplifies global transitions.Code snippetstateDiagram-v2
    [*] --> Idle
    state ON_SUPERSTATE {
        Idle --> Playing : play
        Playing --> Idle : stop
        Playing --> Rewinding : rewind
        Rewinding --> Playing : resume
    }
    ON_SUPERSTATE --> [*] : Power_Off
5. Complexity Reduction: Orthogonal RegionsScenario: A Smartwatch tracking an Exercise while simultaneously Monitoring Heart Rate.[!TIP]Why it's better: Concurrent (orthogonal) regions allow us to model independent behaviors on a single chart without "State Explosion." Without them, we'd have to draw a state for every possible combination of exercise and heart rate.6. Sequence of Operations: Car Sub-systemsThis tracks the chronological communication between the Driver and the sub-systems.Code snippetsequenceDiagram
    actor Driver
    participant S as Starter
    participant L as Lights
    participant AC as AirCon
    participant A as Accelerator

    Driver->>S: ignite()
    S-->>Driver: Ready
    Driver->>L: switchOn()
    Driver->>AC: setTemp(22)
    Driver->>A: press()
7. Polymorphism: Static vs. DynamicStatic: Resolved at compile-time (Method Overloading).Dynamic: Resolved at runtime (Method Overriding).Static Example (Overloading):Javapublic class Processor {
    public void create(String name) {
        System.out.println("Item: " + name);
    }
    
    public void create(String name, int id) {
        System.out.println("Item: " + name + " ID: " + id);
    }
}
8. Real-World Modeling: ATM StatesWe identified four discrete states for an ATM system:IDLE: Waiting for user input.AUTH_PENDING: Validating credentials.SELECTION: Navigating the menu.DISPENSING: Hardware execution of cash delivery.9. Relationship Summary TableStatementRelationship TypeNotation"A Department has many Professors"AggregationHollow Diamond"A Car is a Vehicle"GeneralizationHollow Arrow"A House is made of Rooms"CompositionFilled Diamond10. Strategy: Beyond Use CasesA Use Case diagram captures the "What" (Requirements) but lacks the "How" (Implementation). It is insufficient because:It does not define Internal Data Structure (Attributes).It does not define the Chronological Order of internal events.Conclusion: Developers require Class and Sequence diagrams to handle the actual logic and handshakes between objects.
---
