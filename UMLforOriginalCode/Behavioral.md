```mermaid
graph TD

%% Parking a Vehicle (ParkingLot.park)
    A[Parking Start] --> B{Execute park method};
    
    B --> C{Is Overall Lot Full?};
    C -->|Yes| D[OUTPUT: Lot is Full];
    C -->|No| E{Is Vehicle Electric?};
    
    E -->|Yes| F{EV Spot Available?};
    F -->|No| H[OUTPUT: No EV parking];
    F -->|Yes| G[Get EV Slot & Create EV];
    
    E -->|No| I{Regular Spot Available?};
    I -->|Yes| J[Get Regular Slot & Create Vehicle];
    I -->|No| K[OUTPUT: No regular parking];
    
    G --> L[Increment EV Counter];
    J --> M[Increment Regular Counter];
    
    L --> P[OUTPUT: Allocated Slot #];
    M --> P;
    
    D --> N(End Parking Process);
    H --> N;
    K --> N;
    P --> N;

%% Removing a Vehicle (ParkingLot.leave)
    S[Removal Start] --> T{Execute leave method};
    
    T --> U{Is Vehicle EV to Remove?};
    
    U -->|Yes| V{Is EV Slot Occupied?};
    U -->|No| Y{Is Regular Slot Occupied?};
    
    V -->|Yes| W[Action: Free EV Slot];
    V -->|No| X[Result: Return False];
    
    Y -->|Yes| Z[Action: Free Regular Slot];
    Y -->|No| X;
    
    W --> A{Is Removal Complete?};
    Z --> A;
    
    X --> B[OUTPUT: Removal Failed];
    A -->|Success| C[OUTPUT: Slot is Now Free];
    A -->|Failure| B;
    
    C --> E2(End Removal Process);
    B --> E2;
