```mermaid
graph TD
    S[Start: Click "Remove Car"] --> T{Execute leave()};
    
    T --> U{Is Vehicle EV?};
    
    U -->|Yes| V{Is EV Slot Occupied?};
    U -->|No| Y{Is Regular Slot Occupied?};
    
    V -->|Yes| W[Free EV Slot];
    V -->|No| X[Return False];
    
    Y -->|Yes| Z[Free Regular Slot];
    Y -->|No| X;
    
    W --> A{Was Successful?};
    Z --> A;
    
    X --> B[Output "Failure Message"];
    A -->|Success| C[Output "Success Message"];
    A -->|Failure| B;
    
    C --> E(End);
    B --> E;
