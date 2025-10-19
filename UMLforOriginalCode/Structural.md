## 🧩 UML Class Diagram — Exact-Image-Style (two ParkingLot boxes, same visible name)

```mermaid
%% Image-style UML: two ParkingLot boxes visually separated but both labeled "ParkingLot"
classDiagram
    %% try to encourage left-to-right grouping
    %% (GitHub's Mermaid does not guarantee perfect placement but this matches the image structure)
    %% ---------- LEFT: Vehicle hierarchy ----------
    class Vehicle {
        - regnum: str
        - make: str
        - model: str
        - color: str
        + getMake()
        + getModel()
        + getColor()
        + getRegNum()
    }

    class Car {
        + getType()
    }
    class Truck {
        + getType()
    }
    class Motorcycle {
        + getType()
    }
    class Bus {
        + getType()
    }

    Vehicle <|-- Car
    Vehicle <|-- Truck
    Vehicle <|-- Motorcycle
    Vehicle <|-- Bus

    %% ---------- RIGHT: ElectricVehicle hierarchy ----------
    class ElectricVehicle {
        - regnum: str
        - make: str
        - model: str
        - color: str
        - charge: int
        + getMake()
        + getModel()
        + getColor()
        + getRegNum()
        + setCharge(charge: int)
        + getCharge() : int
    }

    class ElectricCar {
        + getType()
    }
    class ElectricBike {
        + getType()
    }

    ElectricVehicle <|-- ElectricCar
    ElectricVehicle <|-- ElectricBike

    %% ---------- CENTER: Two visual ParkingLot boxes (same visible label) ----------
    %% We use distinct internal IDs but make the displayed name identical by quoting the visible name.
    class "ParkingLot" as ParkingLot_Regular {
        - capacity: int
        - level: int
        - slotid: int
        - numOfOccupiedSlots: int
        - slots: list
        + createParkingLot(capacity, evcapacity, level)
        + park(regnum, make, model, color, ev, motor)
        + leave(slotid, ev)
        + edit(slotid, regnum, make, model, color, ev)
        + status()
        + getRegNumFromColor(color)
        + getSlotNumFromRegNum(regnum)
        + getSlotNumFromColor(color)
        + getSlotNumFromMake(make)
        + getSlotNumFromModel(model)
    }

    class "ParkingLot" as ParkingLot_EV {
        - evCapacity: int
        - level: int
        - slotEvId: int
        - numOfOccupiedEvSlots: int
        - evSlots: list
        + createParkingLot(capacity, evcapacity, level)
        + park(regnum, make, model, color, ev, motor)
        + leave(slotid, ev)
        + edit(slotid, regnum, make, model, color, ev)
        + chargeStatus()
        + getRegNumFromColor(color)
        + getSlotNumFromRegNum(regnum)
        + getSlotNumFromColor(color)
        + getSlotNumFromMake(make)
        + getSlotNumFromModel(model)
    }

    %% dashed association indicating both visual boxes represent the same logical class
    ParkingLot_Regular <..> ParkingLot_EV : <<same logical class>>

    %% ---------- Relationships (match image grouping) ----------
    %% Left parkinglot manages regular Vehicles
    ParkingLot_Regular --> Vehicle : manages
    %% Right parkinglot manages ElectricVehicles
    ParkingLot_EV --> ElectricVehicle : manages
