```mermaid
graph TD
subgraph Parking Flow
    A[Start UI Gathers Input] --> B{Call ParkingLotpark};
    
    B --> C{Is Overall Lot Full};
    C -->|Yes| D[RETURN -1 Lot Full];
    
    C -->|No| E{Determine Vehicle Type};
    
    E --> F[Call VehicleFactorycreate_vehicle];
    F --> G[Factory Returns New Vehicle Object];

    G --> H{Is Regular Spot Available?};
    H --> I[Assign Vehicle to Regular Slot];
    H --> J{Is EV Spot Available?};
    
    J --> K[Assign Vehicle to EV Slot];
    J --> D;

    H -->|No| J;
    I --> L[RETURN Allocated Slot ID];
    K --> L;
    
    D --> N(End UI Displays Lot Full);
    L --> P(End UI Displays Slot ID);

    P --> N;
end

subgraph Removal Flow
    S[Start UI Gathers Slot ID] --> T{Call ParkingLotleave};
    
    T --> U{Is Slot an EV Slot?};
    
    U -->|Yes| V{Is Target EV Slot Occupied?};
    U -->|No| Y{Is Target Regular Slot Occupied?};
    
    V --> W[Action Free EV Slot Index];
    V --> X[RETURN False];
    
    Y --> Z[Action Free Regular Slot Index];
    Y --> X;
    
    V -->|No| X;
    Y -->|No| X;

    W --> A2{Decrement Counter};
    Z --> A2;
    
    A2 --> C2[RETURN True];
    
    C2 --> E2[End UI Displays Slot is Free];
    X --> B2[End UI Displays Unable to Remove];
    
    B2 --> E2;
end
