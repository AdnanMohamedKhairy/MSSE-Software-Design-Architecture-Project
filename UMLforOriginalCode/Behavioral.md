```mermaid
graph TD
    A[Start: User Clicks "Park Car"] --> B{Execute ParkingLot.park()};

    B -->|Is Lot Full?| C{Is Lot Full?};
    C -->|Yes| D[Output "Sorry, parking lot is full"];
    C -->|No| E{Is Vehicle Electric?};

    E -->|Yes (EV)| F{Is EV Spot Available?};
    F -->|Yes| G[Get Empty EV Slot & Create EV];
    F -->|No| H[Output "No EV parking available"];

    E -->|No (Regular)| I{Is Regular Spot Available?};
    I -->|Yes| J[Get Empty Regular Slot & Create Vehicle];
    I -->|No| K[Output "No regular parking available"];

    G --> L[Increment EV Counter & Output Slot #];
    J --> M[Increment Regular Counter & Output Slot #];

    D --> N(End);
    H --> N;
    K --> N;
    L --> N;
    M --> N;
