```mermaid
%% Activity Diagram: Parking a Vehicle
activityDiagram
    start
    :User provides vehicle details and clicks "Park Car";
    :Execute ParkingLot.park();
    
    if (Is Lot Full?) then (Yes)
        :Output "Sorry, parking lot is full";
        stop
    else (No)
        if (Is Vehicle Electric (EV)? - ev == 1) then (Yes)
            if (Is EV Spot Available?) then (Yes)
                :Get Empty EV Slot;
                :Create ElectricCar or ElectricBike;
                :Increment numOfOccupiedEvSlots;
                :Output Allocated slot number;
            else (No)
                :Output "Sorry, no EV parking available";
            end
        else (No - Regular Vehicle)
            if (Is Regular Spot Available?) then (Yes)
                :Get Empty Regular Slot;
                :Create Car or Motorcycle;
                :Increment numOfOccupiedSlots;
                :Output Allocated slot number;
            else (No)
                :Output "Sorry, no regular parking available";
            end
        end
    end
    stop
