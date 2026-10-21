# -Rover-PCB-for-XRC-Xplore-rover-challenge-
My first PCB made for rover challenge at my university was designed to connect all electronics for out rover.

1.	Main Purpose:
I decided to design our PCB solely for connections and routing logic signals between our components. The power supply lines for the servo and DC motors will not run through the board in order to avoid significant electrical noise that could interfere with the operation of the logic components.
2.	Brain – Master – Slaves 
The Raspberry Pi will not be fully mounted on the PCB; only a header with 20 pins will be included.
The same approach will be used for the Arduino master.
For the Arduino slaves, there will be dedicated spots on the PCB, allowing them to be mounted and removed as needed.
This design choice was made to avoid wasting space on the board and to keep it compact.
An important clarification: the appropriate resistors have been placed on the PCB to ensure proper logic operation.
Pull-up resistors are used for UART, along with a voltage divider between the Arduino master and the other components to ensure correct signal transmission.

Some additional components were placed to make the work of arduinos proper:

The ferrite bead (FB1) filters high-frequency noise on the power line.
The 100nF capacitor suppresses fast voltage spikes near the Arduino.
The 4.7µF capacitor smooths slower voltage drops.
Together, they stabilize the power and reduce noise from motors and servos.
This setup helps prevent glitches and random resets.
3.	More about Slaves…
Overall, we will have four Arduino slaves, each with its own specific role. Slaves #1 and #2 will handle rover control. Each of them will receive signals from the master (which in turn receives them from the Raspberry Pi), and will control the motors in parallel pairs via a driver (left front & rear + right front & rear), as well as one servo motor each.
This approach was chosen to improve the rover’s turning performance, where the servo motors will be especially useful.
Slave #3 will be used as a mini controller for the robotic arm, managing five servo motors, as well as two additional servos used in the LiDAR system. In total, it will control seven servo motors.
A dedicated slave was assigned for this purpose to avoid overloading the system and adding extra strain to the other components.

The final slave, #4, will manage all the sensors in the system and transmit the data to the appropriate modules.
