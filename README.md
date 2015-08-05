# gluing
we write the program gluing. 
The PUMA robot is used to solve this part. First we load
the suitable end effector file. Here it is also important to load the correct one, because the frame is defined
differently. Then we initialize variables for inputs which give information about the gun whether it is
empty or full. The numbers of the input are given in the lab description.
To draw we use the defined A B C D locations which is defined in the pre-defined board frame. That’s why
the moving instructions are defined as it is in the program. After we move to the first location we start
gluing with closei. Then we move to the other locations. Here to get the right rectangle with sharp edges
we use break instruction because we want that the motion finishes completely. After each cycle the
coordinates of each location are shifted accordingly to the exercise.
There is also an event which must be handled. When the gun is empty we must suspend the program and
go to refill the gun. Here we choose asynchronous mode because of the nature of the event as it can
happen any time. From the asynchronous modes we use reacti as when the gun is empty we must stop
immediately the motion because the robot cannot draw with empty guns. Our subroutine is named as
refillgun. To be able to continue the interrupted exercise first we save the current location of the robot
and the destination position. To save the destination is important because if the interrupt happens
between two points the robot will assume that the motion instruction is finished and after the subroutine
it will go to the next point which yields to bad result.
To run the program in an infinite loop we put -1 after the operation system command ex.
