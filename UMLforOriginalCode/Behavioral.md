```mermaid
    graph TD
        A[Start: Click "Park"] --> B{Execute park()};
        
        B --> C{Is Lot Full?};
        C -->|Yes| D[Output "Lot full"];
        C -->|No| E{Is Vehicle EV?};
        
        E -->|Yes| F{Is EV Spot Available?};
        F -->|Yes| G[Get EV Slot & Create EV];
        F -->|No| H[Output "No EV parking"];
        
        E -->|No| I{Is Regular Spot Available?};
        I -->|Yes| J[Get Regular Slot & Create Vehicle];
        I -->|No| K[Output "No regular parking"];
        
        G --> L[Increment EV Counter & Output Slot #];
        J --> M[Increment Regular Counter & Output Slot #];
        
        D --> N(End);
        H --> N;
        K --> N;
        L --> N;
        M --> N;
