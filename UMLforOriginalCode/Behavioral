```mermaid
%% Activity Diagram for Parking a Vehicle
activityDiagram
    start
    :User clicks "Park Car";
    :Execute ParkingLot.park();
    
    if (Lot is full?) then (Yes)
        :Output "Sorry, parking lot is full";
        stop
    else (No, spot available)
        if (Vehicle is Electric?) then (Yes, ev == 1)
            if (EV spot available?) then (Yes)
                :Get Empty EV Slot;
                :Create ElectricCar/ElectricBike;
                :Increment numOfOccupiedEvSlots;
                :Output Allocated slot number;
                end
            else (No)
                :Output "Sorry, EV parking full";
                end
            end
        else (No, Regular Vehicle)
            if (Regular spot available?) then (Yes)
                :Get Empty Regular Slot;
                :Create Car/Motorcycle;
                :Increment numOfOccupiedSlots;
                :Output Allocated slot number;
                end
            else (No)
                :Output "Sorry, Regular parking full";
                end
            end
        end
    end
