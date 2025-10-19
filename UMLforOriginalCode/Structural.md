## 🧩 UML Class Diagram — Exact Image Match (ParkingLot shown twice)

```mermaid
classDiagram
    %% === Vehicle Hierarchy ===
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
        + getType() : "Car"
    }
    class Truck {
        + getType() : "Truck"
    }
    class Motorcycle {
        + getType() : "Motorcycle"
    }
    class Bus {
        + getType() : "Bus"
    }

    Vehicle <|-- Car
    Vehicle <|-- Truck
    Vehicle <|-- Motorcycle
    Vehicle <|-- Bus

    %% === Electric Vehicle Hierarchy ===
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
        + getType() : "Car"
    }
    class ElectricBike {
        + getType() : "Motorcycle"
    }

    ElectricVehicle <|-- ElectricCar
    ElectricVehicle <|-- ElectricBike

    %% === Parking Lot (two visual boxes to match image) ===
    class ParkingLot_Regular {
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
    }

    class ParkingLot_EV {
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
    }

    %% show they are the same logical class (dashed association)
    ParkingLot_Regular <..> ParkingLot_EV : <<same logical class>>

    %% relationships to vehicle classes
    ParkingLot_Regular --> Vehicle : manages
    ParkingLot_EV --> ElectricVehicle : manages
