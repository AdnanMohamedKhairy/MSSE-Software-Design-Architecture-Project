```markdown
```mermaid
graph TD
S[Start: Click "Remove"] --> T{Execute leave(slotid, ev)};
T --> U{Is Vehicle EV?};
U -->|Yes| V{Is EV Slot Occupied?};
V -->|Yes| W[Free EV Slot & Decrement Counter];
V -->|No| X[Return False];
U -->|No| Y{Is Regular Slot Occupied?};
Y -->|Yes| Z[Free Regular Slot & Decrement Counter];
Y -->|No| X;
W --> A{Was Removal Successful?};
Z --> A;
X --> B[Output "Unable to remove"];
A -->|Success| C[Output "Slot is free"];
A -->|Failure| B;
C --> E(End);
B --> E;
