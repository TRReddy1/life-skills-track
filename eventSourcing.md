# Event Sourcing Architecture

## Introduction of Event Sourcing

Event Sourcing is a **pattern for storing data as events in an append-only log.** This simple definition misses the fact that by storing the events, you also keep the context of the events; you know an invoice was sent and for what reason from the same piece of information. In other storage patterns, the business operation context is usually lost, or sometimes stored elsewhere.

Event Sourcing is an architectural pattern that revolutionizes how applications manage and record changes to their state. This approach captures every state change as an immutable event, creating an event log that serves as a source of truth for reconstructing the application's state.

Every change made is represented as an event, and appended to the event log. An entity’s current state can be created by replaying all the events in order of occurrence. The system information is sourced from the events. As the event has already happened, it’s always referred to in the past tense.

## Key Concepts/core principles

### Events

An event represents a fact that took place in the domain. They are the source of truth; your current state is derived from the events. They are immutable, and represent the business facts.

Each event encapsulates a specific action or change, such as **'OrderPlaced'** or **'PaymentReceived'**.

### Event Log/Store

An append-only log or database where all events are stored in chronological order. This log is immutable and captures events with metadata like timestamp and version.

The **events are immutable:** they cannot be changed. This well-known rule of event stores is often the first defining feature of event stores and Event Sourcing that most people hear, and is absolutely true, from a certain point of view.

### State Reconstruction

The current state of the application is derived by replaying events from the event log. This process involves applying events sequentially to build the current state.

### Separation of Concerns

Event Sourcing separates write and read operations, allowing scalability by optimizing read and write models independently.

## Advantages

- **Full History and Audit Trail**: Enables complete historical tracking and auditing of system changes.
- **Temporal Queries**: Allows querying the system's state at any specific point in time.
- **Debugging and Analysis**: Facilitates debugging by replaying events and provides valuable data for analysis.
- **Immutable Log**: Ensures data integrity and resilience to data corruption.
- **Scalability**: Permits scaling of read and write sides independently.
- **Event-driven architecture**:Traditional approaches gather data in discrete areas to be called on only when needed. An event-driven approach can be more efficient by immediately reacting to new published information.

## Considerations

- **Complexity**: Implementation complexity compared to CRUD-based systems.
- **Event Versioning**: Handling changes in event structures and maintaining compatibility.
- **Infrastructure**: Robust infrastructure needed for managing event logs.
- **Querying and Reporting**: Might require additional indexing or caching strategies.

## Event Sourcing Architecture

Event Sourcing is an architectural design pattern that stores data in an append-only log. It is part of a wider ecosystem of design patterns that work together in various ways to allow developers to create the most effective architecture for their needs.
-an event-sourced system works well within a CQRS architecture,

![Alt text](https://6850195.fs1.hubspotusercontent-na1.net/hubfs/6850195/ES-Pillar-10.svg)

## Conclusion

Event Sourcing is a powerful pattern used in complex systems requiring complete historical tracking and auditability. While it introduces complexity, it offers unparalleled benefits in terms of historical data and system resilience.
