```mermaid
activityDiagram
    start
    :User clicks "Park Car";
    :Execute ParkingLot.park();

    if (Is Lot Full?) then (Yes)
      :Output "Sorry, parking lot is full";
      stop
    else (No)
      if (Is Vehicle Electric?) then (Yes)
        if (Is EV Spot Available?) then (Yes)
          :Get Empty EV Slot;
          :Create ElectricCar/ElectricBike;
          :Output Allocated slot number;
        else (No)
          :Output "Sorry, no EV parking available";
        end
      else (No)
        if (Is Regular Spot Available?) then (Yes)
          :Get Empty Regular Slot;
          :Create Car/Motorcycle;
          :Output Allocated slot number;
        else (No)
          :Output "Sorry, no regular parking available";
        end
      end
    end
    stop
