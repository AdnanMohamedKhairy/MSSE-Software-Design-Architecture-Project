```mermaid
classDiagram
    direction LR
    
    %% --- Application Layer (Composition/Dependency) ---
    class ParkingLotApp {
        - parking_lot: ParkingLot
        - tfield: tk.Text
        + _handle_park_car()
        + _output(message)
        + main_loop()
    }
    
    class ParkingLot {
        - factory: VehicleFactory
        - slots: List~Vehicle~
        - evSlots: List~Vehicle~
        + createParkingLot(...)
        + park(vehicleDetails)
        + leave(slotId)
        + get_status(): str
        + _find_vehicles(condition)
    }

    class VehicleFactory {
        + create_vehicle(type, regnum, make, color) Vehicle
    }
    
    %% --- Vehicle Model Layer (Inheritance) ---
    class Vehicle {
        - regnum: str
        - make: str
        - model: str
        - color: str
        - is_electric: bool
        - charge: int
        + getRegNum()
        + getType()
    }

    class Car
    class Truck
    class Motorcycle
    class Bus
    
    
    %% --- Relationships ---
    
    %% Generalization (Inheritance) - Single Unified Tree
    Vehicle <|-- Car : Generalization
    Vehicle <|-- Truck : Generalization
    Vehicle <|-- Motorcycle : Generalization
    Vehicle <|-- Bus : Generalization
    
    %% Composition (The App owns the core logic)
    ParkingLotApp "1" *-- "1" ParkingLot : holds
    
    %% Aggregation (The Lot manages vehicles in its slots)
    ParkingLot "1" o-- "*" Vehicle : manages
    
    %% Dependency (The Lot relies on the Factory to create products)
    ParkingLot ..> VehicleFactory : creates
