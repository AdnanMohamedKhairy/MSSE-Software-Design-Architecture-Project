
## 🧩 UML Class Diagram — Parking Lot Management System

```mermaid
classDiagram
    %% === Base Vehicle Classes ===
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


    %% === Electric Vehicle Classes ===
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
        + setCharge(charge)
        + getCharge()
    }

    class ElectricCar {
        + getType()
    }

    class ElectricBike {
        + getType()
    }

    ElectricVehicle <|-- ElectricCar
    ElectricVehicle <|-- ElectricBike


    %% === Parking Lot ===
    class ParkingLot {
        - capacity: int
        - evCapacity: int
        - level: int
        - slots: list
        - evSlots: list
        - numOfOccupiedSlots: int
        - numOfOccupiedEvSlots: int
        + createParkingLot(capacity, evcapacity, level)
        + park(regnum, make, model, color, ev, motor)
        + leave(slotid, ev)
        + edit(slotid, regnum, make, model, color, ev)
        + status()
        + chargeStatus()
        + getRegNumFromColor(color)
        + getSlotNumFromRegNum(regnum)
    }

    ParkingLot --> Vehicle : uses
    ParkingLot --> ElectricVehicle : uses
