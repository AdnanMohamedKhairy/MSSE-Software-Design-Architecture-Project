```mermaid
graph TD
    S[Start]
    T{Execute leave()}
    U{Is EV?}
    V{Is Slot Occupied?}
    W[Free EV Slot]
    X[Return False]
    Y{Is Slot Occupied?}
    Z[Free Reg Slot]
    A{Was Successful?}
    B[Output "Unable to remove"]
    C[Output "Slot is free"]
    E(End)

    S --> T
    T --> U
    U -->|Yes| V
    U -->|No| Y
    V -->|Yes| W
    V -->|No| X
    Y -->|Yes| Z
    Y -->|No| X
    W --> A
    Z --> A
    X --> B
    A -->|Success| C
    A -->|Failure| B
    C --> E
    B --> E
