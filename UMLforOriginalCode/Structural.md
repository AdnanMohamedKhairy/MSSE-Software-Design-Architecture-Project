## UML — Exact Image-Style (two ParkingLot boxes)

```mermaid
classDiagram
    %% Layout hint (GitHub Mermaid ignores strict positioning but this groups visually)
    %% Vehicle hierarchy (left cluster)
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

    %% ElectricVehicle hierarchy (right cluster)
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

    %% ParkingLot shown TWICE — left = regular slots, right = EV slots (matches image)
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
        + getSlotNumFromMake(make)
        + getSlotNumFromModel(model)
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
        + getSlotNumFromMake(make)
        + getSlotNumFromModel(model)
    }

    %% Visual indication they represent the same logical ParkingLot (dashed line + label)
    ParkingLot_Regular <..> ParkingLot_EV : <<same logical class>>

    %% Management relationships (matches image: left manages Vehicle, right manages ElectricVehicle)
    ParkingLot_Regular --> Vehicle : manages
    ParkingLot_EV --> ElectricVehicle : manages
