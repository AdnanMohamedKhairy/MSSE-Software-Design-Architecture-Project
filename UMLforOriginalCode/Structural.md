## 🧩 UML Class Diagram — Parking Lot Management System (Image-Style Version)

```mermaid
classDiagram
    %% ===============================
    %%      Vehicle Hierarchy
    %% ===============================
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


    %% ===============================
    %%     Electric Vehicle Hierarchy
    %% ===============================
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


    %% ===============================
    %%        Parking Lot Manager
    %% ===============================
    class ParkingLot {
        - capacity: int
        - evCapacity: int
        - level: int
        - slotid: int
        - slotEvId: int
        - numOfOccupiedSlots: int
        - numOfOccupiedEvSlots: int
        - slots: list
        - evSlots: list
        + createParkingLot(capacity, evcapacity, level)
        + park(regnum, make, model, color, ev, motor)
        + leave(slotid, ev)
        + edit(slotid, regnum, make, model, color, ev)
        + status()
        + chargeStatus()
        + getRegNumFromColor(color)
        + getSlotNumFromRegNum(regnum)
        + getSlotNumFromColor(color)
    }

    ParkingLot --> Vehicle : manages >
    ParkingLot --> ElectricVehicle : manages >
