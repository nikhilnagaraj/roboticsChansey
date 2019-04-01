# Graph Traversal – Chansey  - (Nikhil Nagaraj, r0727410)

**Q. Can Chansey (currently at Room 0.01) reach its goal at Room 2.01?**

A. Chansey currently is at Room 0.01. That marks its current position. 2.01 is on level 2, 10 units from the elevator. The relevant state variables are set as follows:

```Javascript

"deliveryLocation": {
        ...
        ...
        ...
        "@id": "Delivery_Location",
        "@value": [
            ...
            ...
            {
                "@id": "Steps",
                "heightDifference": 2,
                "toElevator": 10,
                "fromElevator": 12,
                "intoElevator": 2,
                "sameFloorDistance": 0
            }
        ]
    }
```

Starting from the goal to choose the action plan, we move to the action plan selector. The condition here is falsified, as  `sameFloorDistance` is 0. As the condition has not been satified, the action plan chosen is `Chansey action plan`.
The sequence of actions executed are as follows:

  * `Move(distance = 10)` which satifies the preconditions (distance > 0) set by the meta model - `Motion`.
  * `RequestElevator` which satisfies the preconditions set by the meta model `Elevator Communication`.

  > **Note**: 10 units of motion puts it at the `accessPosition` since the distance from the elevator to the room is 10.

  * `Move(distance = 2)` which satifies the preconditions (distance > 0) set by the meta model - `Motion`.
  * `Move Elevator(floors = 2)` which satifies the preconditions (robot is inside the elevator) set by the meta model - `Elevator Communication` and with this Chansey reaches the 2nd Floor.
  * `Move(distance = 12)` satisfies the required preconditions (distance > 0) and puts the robot in front of `Room 2.01`.

Since the action plan has been completely executed, on checking the goal we find that the desired result has been achieved.