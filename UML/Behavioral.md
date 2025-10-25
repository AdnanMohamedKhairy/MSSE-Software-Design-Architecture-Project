```mermaid
graph TD

%% Parking Flow
subgraph A_Parking_Flow
    A[Start UI Gathers Input] --> B{Call ParkingLotpark};
    
    B --> C{Is Overall Lot Full};
    C -->|Yes| D[RETURN -1 Lot Full];
    
    C -->|No| E{Determine Vehicle Type};
    
    E --> F[Call VehicleFactorycreate_vehicle];
    F --> G[Factory Returns New Vehicle Object];

    G --> H{Is Regular Spot Available};
    H -->|Yes| I[Assign Vehicle to Regular Slot];
    H -->|No| J{Is EV Spot Available};
    
    J -->|Yes| K[Assign Vehicle to EV Slot];
    J -->|No| D;

    I --> L[RETURN Allocated Slot ID];
    K --> L;
    
    D --> N(End UI Displays Lot Full);
    L --> P(End UI Displays Slot ID);
end

%% Removal Flow
subgraph B_Removal_Flow
    S[Start UI Gathers Slot ID] --> T{Call ParkingLotleave};
    
    T --> U{Is Slot an EV Slot};
    
    U -->|Yes| V{Is Target EV Slot Occupied};
    U -->|No| Y{Is Target Regular Slot Occupied};
    
    V -->|Yes| W[Action Free EV Slot Index];
    V -->|No| X[RETURN False];
    
    Y -->|Yes| Z[Action Free Regular Slot Index];
    Y -->|No| X;
    
    W --> A2{Decrement Counter};
    Z --> A2;
    
    A2 --> C2[RETURN True];
    
    C2 --> E2[End UI Displays Slot is Free];
    X --> B2[End UI Displays Unable to Remove];
end
