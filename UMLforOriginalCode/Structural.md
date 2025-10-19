```mermaid


classDiagram
    direction LR

    %% -------------------- Vehicle Hierarchy --------------------
    class Vehicle {
        - regnum: str
        - make: str
        - model: str
        - color: str
        + __init__(regnum, make, model, color)
        + getMake()
        + getModel()
        + getColor()
        + getRegNum()
    }

    class Car {
        + __init__(regnum, make, model, color)
        + getType(): "Car"
    }

    class Truck {
        + __init__(regnum, make, model, color)
        + getType(): "Truck"
    }

    class Motorcycle {
        + __init__(regnum, make, model, color)
        + getType(): "Motorcycle"
    }

    class Bus {
        + __init__(regnum, make, model, color)
        + getType(): "Bus"
    }

    Vehicle <|-- Car
    Vehicle <|-- Truck
    Vehicle <|-- Motorcycle
    Vehicle <|-- Bus

    %% -------------------- ElectricVehicle Hierarchy --------------------
    class ElectricVehicle {
        - regnum: str
        - make: str
        - model: str
        - color: str
        - charge: int = 0
        + __init__(regnum, make, model, color)
        + getMake()
        + getModel()
        + getColor()
        + getRegNum()
        + setCharge(charge: int)
        + getCharge(): int
    }

    class ElectricCar {
        + __init__(regnum, make, model, color)
        + getType(): "Car"
    }

    class ElectricBike {
        + __init__(regnum, make, model, color)
        + getType(): "Motorcycle"
    }

    ElectricVehicle <|-- ElectricCar
    ElectricVehicle <|-- ElectricBike

    %% -------------------- ParkingLot (Manager) --------------------
    class ParkingLot {
        - capacity: int
        - evCapacity: int
        - level: int
        - slotid: int
        - slotEvId: int
        - numOfOccupiedSlots: int
        - numOfOccupiedEvSlots: int
        - slots: List~Vehicle~
        - evSlots: List~ElectricVehicle~
        + __init__()
        + createParkingLot(capacity, evcapacity, level)
        + park(regnum, make, model, color, ev, motor)
        + leave(slotid, ev)
        + status()
        + chargeStatus()
        + slotNumByReg()
        + slotNumByColor()
        + regNumByColor()
        // ... other methods omitted for brevity
    }

    %% -------------------- Relationships --------------------
    ParkingLot "1" *-- "*" Vehicle : manages
    ParkingLot "1" *-- "*" ElectricVehicle : manages
