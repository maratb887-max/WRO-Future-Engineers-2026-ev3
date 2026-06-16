
Introduction:
====
We are a team cybercrafters participating in WRO Future Engineers 2026. Our team members are Marat Beksultan and Sadyrov Aryn.
Project Vision:
Our team focused on developing an autonomous mobile robot capable of high-speed navigation and precise obstacle avoidance. The primary objective was to create a robust system that combines mechanical stability with an advanced software architecture to handle the dynamic challenges of the WRO competition.

Engineering Approach:
To achieve 100% reliability, we implemented a Proportional-Control (P-regulator) steering system. This allows our robot to maintain a consistent distance from boundaries with fluid movements, minimizing the energy loss caused by sharp corrections. Our design philosophy centers on three core pillars:

Mobility, Design, and Control Strategy
====

The robot’s design was developed with stability, maneuverability, and precision of movement in mind. The robot is built on a “tractor-type” configuration: smaller 
This design ensures an effective distribution of functions: the rear wheels act as drive wheels and are responsible for transmitting torque, while the front wheels provide directional stability and improve maneuverability. The larger diameter of the rear wheels increases off-road capability and reduces the impact of uneven terrain, as well as improving acceleration efficiency.

The initial design version used studded tires, designed to achieve maximum speed through reduced rolling resistance. However, testing revealed that this configuration led to slippage, particularly during turns and sudden accelerations, which reduced driving precision.


As a result, the decision was made to switch to slick tires. This increased traction and improved handling stability. Thus, a deliberate trade-off was made: a slight reduction in top speed in exchange for improved handling, precision, and reliability. You can see the comparison of slick and studded tires


The main motor is mounted on the rear axle, as it bears the main load. This allows for efficient power transmission and minimizes energy loss. The vehicle’s center of gravity is shifted closer to the rear wheels, which further increases the driving wheels’ traction. All components are rigidly mounted to reduce vibrations and improve stability.

During development, alternative design options were considered, including the use of identical wheels and other drive configurations; however, these yielded poorer results in terms of stability and control.


A number of improvements were also implemented at the software strategy level. In the initial version, the robot did not use an ultrasonic sensor, as the primary goal was to achieve maximum speed and simplify the algorithm. The absence of the sensor allowed for reduced data processing delays and faster movement.
However, testing showed that at high speeds, the probability of collision with the track walls increases due to the orientation errors and the lack of feedback from the environment.

To improve reliability, an ultrasonic sensor was added, and the movement strategy was modified. Instead of moving in a straight line, a zigzag algorithm was implemented that continuously measures the distance to the edge.
Navigation Strategy Comparison: Open-Loop vs. Ultrasonic Feedback

The robot moves at a slight angle to the wall, periodically measuring the distance and correcting its direction to maintain a safe distance. This approach compensates for movement errors and significantly reduces the risk of collision.

As with the choice of wheels, an engineering compromise was made here as well: a slight reduction in speed and increased algorithm complexity in exchange for a significant improvement in stability and accuracy.

Tests confirmed that the chosen mechanical design and control strategy ensure more reliable and predictable robot behavior when performing tasks.
Performance comparison:


Power and Sensor Management
====
WRO 2025 Future Engineers - Robot Component Description
📋 Table of Contents
•    EV3 Brick (Control Brick)
•    EV3 Medium Motor
•    EV3 Ultrasonic Sensor
•    EV3 Color Sensor
•    Pixy 2.1 Camera
•    EV3 Battery
•    EV3 Wire
________________________________________
EV3 Brick (Control Brick)
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/e404d268-4b39-420f-a643-b1fb2b416423" />

🎯 Function
The robot controller is the robot’s main “brain,” which controls all other components. The EV3 Brick is responsible for processing data from sensors, executing algorithms, controlling motors, and making real-time decisions.

📝 Description
The LEGO MINDSTORMS EV3 Intelligent Brick is a powerful microcontroller based on an ARM processor, running the ev3dev (Linux) operating system. It allows you to program the robot in Python, making it the ideal choice for WRO Future Engineers. The brick is equipped with built-in ports for connecting motors (A, B, C, D) and sensors (1, 2, 3, 4), and also features a built-in screen for debugging and testing.
🔧 Technical Specifications
Specification    Value
Processor    Texas Instruments Sitara AM1808, ARM9, 300 MHz

Random Access Memory (RAM)    64 MB

Built-in memory (Flash)    4 GB (for program storage)

Nominal voltage    7.2 - 9.0 V

Connection ports    4 ports for motors (A, B, C, D), 4 ports for sensors (1, 2, 3, 4)

Interfaces    USB, Bluetooth, Wi-Fi (with adapter)

Display    178 × 128 pixels, black-and-white LCD

Battery    LEGO Battery Pack

Dimensions    149 × 98 × 54 mm

Weight    368 g (with batteries)

Response time    ~50 ms

Supported OS    ev3dev (Linux), LEGO MINDSTORMS чEducation, LEGO MINDSTORMS Home

⚡ Power Specifications
•    Nominal voltage: 7.2–9.0 V

•    Maximum current: ~2 A

•    Power consumption (standby mode): ~50 mW

•	Power consumption (in operation): ~500 mW - 1.5 W (depending on load)

________________________________________
Medium Motor EV3
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/2243ee6d-8c3a-460e-ae51-95c56b714598" />

🎯 Function
Steering mechanism drive — The Medium Motor is used to turn the robot’s steering system. This motor ensures precise positioning and quick directional control.

📝 Description
The LEGO MINDSTORMS EV3 Medium Motor is a compact, powerful motor with a built-in encoder (rotation sensor) for precise position control. It is ideal for applications requiring precision and speed without excessive torque. In our design, a single unit is used to control the steering angle of the front wheels, ensuring precise path tracking.
🔧 Technical Specifications

Specification    Value

Type    LEGO MINDSTORMS EV3 Medium Motor

Rated Voltage    7.2 - 9.0 V

Maximum RPM    240 RPM (at rated voltage)

Torque (rated)    12 N·cm

Maximum torque    15 N·cm

Built-in encoder    Yes (360 pulses per revolution)

Typical current consumption    ~300 mA (no load), up to 1.5 A (at maximum load)

Response time    ~40 ms

Control range    PWM 0-100% (integrated into the EV3 Brick)

Dimensions    43 × 43 × 43 mm

Weight    90 g

Power (rated)    ~0.8 W

Power (maximum)    ~2 W

⚡ Power specifications
•		Rated voltage: 7.2–9.0 V (matches the EV3 Brick)

•    Operating current (no load): 200–300 mA

•    Peak current (maximum load): up to 1.5 A

•	Power consumption per second (at full power): ~2 Wh

________________________________________
Ultrasonic Sensor EV3
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/5099b5b3-a6de-48d9-ac0f-09ca4261db56" />

🎯 Function
Obstacle sensor — uses ultrasonic waves to measure the distance to objects in front of the robot. It allows the robot to detect and avoid obstacles, parking spots, and other objects on the playing field.

📝 Description
The LEGO MINDSTORMS EV3 Ultrasonic Sensor (distance sensor) works on the principle of echolocation, similar to the sonar used by bats and dolphins. The sensor emits an ultrasonic signal and measures the time it takes for the reflected signal to return, calculating the distance to the object. This allows the robot to navigate its environment with confidence and safely complete WRO tasks.

🔧 Technical Specifications

Specification    Value

Type    Ultrasonic distance sensor (sonar)

Nominal voltage    7.2 - 9.0 V

Measurement range    3 - 250 cm (1 - 98 inches)

Accuracy    ±2 cm (within the 10-200 cm range)

Ultrasonic frequency    40 kHz

Polling frequency    ~20 Hz (50 ms per measurement)

Detection angle    ~60° (detection cone)

Response time to distance change    ~100 ms

Current consumption    ~50 mA (in operating mode)

Dimensions    32 × 31 × 47 mm

Weight    60 g

Power (rated)    ~0.4 W

⚡ Power specifications

•    Rated voltage: 7.2 - 9.0 V

•    Current consumption: 40 - 60 mA

•    Power consumption: ~0.35 W

__________________________
EV3 Color Sensor
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/435c4140-d981-4a11-84ff-627da6e84400" />

🎯 Function

The color and light sensor detects color and light intensity to follow a black line on a white background (line following). It can also be used to detect colored markers and determine the brightness of the surroundings.

📝 Description
The LEGO MINDSTORMS EV3 Color Sensor can recognize 7 different colors (black, brown, blue, red, purple, yellow, white) and measure the intensity of reflected light. The sensor uses an LED to illuminate the surface and measure the reflection. It is the primary sensor for navigating a black line on a white field—a standard task in WRO Future Engineers.

🔧 Technical Specifications

Specification    Value

Type    RGB Color Sensor with reflected light mode

Nominal voltage    7.2 - 9.0 V

Operating modes    3 modes: Color (7 colors), Reflected Light (0-100%), Ambient Light (0-100%)

Recognized colors    Black, Brown, Blue, Red, Purple, Yellow, White

Detection range    0 - 20 cm (optimal 1-2 cm)

Color recognition accuracy    ~95% under optimal lighting

Polling rate    ~10 Hz (100 ms per measurement)

Current consumption    ~80 mA (in backlight mode)

Built-in backlight    Yes (white LED, ~50 lux)

Dimensions    32 × 33 × 47 mm

Weight    65 g

Power (rated)    ~0.6 W

Viewing distance    ~2 cm from the surface (optimal)

⚡ Power specifications

•    Nominal voltage: 7.2 - 9.0 V

•    Current consumption: 60 - 100 mA (in backlight mode)

•    Power consumption: ~0.6 W

____________________
Pixy 2.1 Camera
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/578eed5e-fb6b-4434-8095-ce3195cd33de" />

🎯 Function
A camera with built-in image processing—detects and tracks objects by color in real time. Used to locate colored blocks, markers, road signs, and other visual objects on the WRO playing field.

📝 Description
The CMUcam5 Pixy 2.1 is a coin-sized camera with its own ARM Cortex-M7 processor that can detect colored objects in real time without requiring processing on the main computer. The camera is programmed via a graphical interface, where you train it to recognize specific colors, and it automatically tracks objects of that color. Ideal for autonomous robots, as it reduces the load on the main controller.

🔧 Technical Specifications

Specification    Value

Type    Smart Camera (camera with built-in image processing)

Nominal voltage    5.0 V (important: a step-down converter from 7.2–9 V EV3 is required)

Sensor resolution    320 × 200 pixels

Frame rate    50 FPS (50 frames per second)

Communication interface    UART (9600 baud) or SPI

On-board processor    ARM Cortex-M7, 200 MHz

Recognizable objects    Up to 7 different color signatures simultaneously

Maximum number of trackable objects    Up to 255 objects per frame

Data for each detected object    x, y coordinates, width, height, angle (for BarCode modules)

Detection range    10 cm – 3 m (depending on object size)

Field of view    ~75° (horizontal), ~49° (vertical)

Current consumption    ~100 mA (in tracking mode)

Dimensions 43 × 43 × 41 mm

Weight    28 g

Power (rated)    0.5 W

EV3 integration    Requires an EV3 I2C cable or UART adapter

⚡ Power Specifications

•    Nominal voltage: 5.0 V (⚠️ WARNING: NOT 7.2–9V!)

•    Maximum voltage: 5.5 V

•    Minimum voltage: 4.75 V

•    Current consumption: 80–120 mA

•	Power consumption: ~0.5 W

•    Recommendation: Use a DC-DC converter (7.2-9V → 5V) for safe connection

________________________________________
EV3 Battery
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/86f4de5e-63f2-422a-a432-eb011d1faf7b" />

🎯 Function
Power source — supplies power to all robot components (EV3 Brick, motors, sensors). This is an official LEGO battery designed specifically for use with the MINDSTORMS system.

📝 Description
The LEGO MINDSTORMS EV3 Rechargeable Battery Pack is a professional lithium-ion battery developed by LEGO specifically for the MINDSTORMS system. The battery features built-in protection against overcharging, over-discharging, and overheating, as well as a charge level indicator on the casing. It is a stable and reliable power source that ensures predictable robot performance throughout all competitions.

🔧 Technical Specifications

Specification    Value

Type    Lithium-ion battery (Li-Ion)

Nominal voltage    7.2 V (nominal), 7.2 - 8.4 V (during operation)

Maximum voltage (fully charged)    8.4 V

Minimum voltage (discharge)    5.6 V (shutdown)

Capacity    2100 mAh

Chemistry    Li-Ion 1S2P (1 cell in series, 2 in parallel)

Built-in protections    BMS (Battery Management System) microchip for protection against overcharging,  Overdischarge, overheating, short circuit

Charging time (with the official charger)    ~4–6 hours

Battery life cycle    ~500–1,000 charge cycles

Self-discharge per month    ~10–15% (when not in use)

Dimensions    148 × 68 × 27 mm

Weight    160 g

Operating temperature    0°C to +45°C

Storage temperature    -20°C to +60°C

Standard energy (nominal)    ~15 Wh (2100 mAh × 7.2V)

⚡ Power Specifications

•    Nominal voltage: 7.2 V (range 7.2–8.4 V)

•    Maximum output current: 2.0–2.5 A (continuous)

•    Peak current: up to 4 A (briefly when motors are activated)

•    Full charge: 8.4 V, 2100 mAh

•    Full discharge: 5.6 V (shutdown for battery protection)

•    Battery life (typical): 8–12 hours (with moderate use of 2 motors)

________________________________________
Wire EV3
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/7a840827-d74c-41da-a1bc-5bd8462cf2f7" />

🎯 Function
Component connection cable — connects all sensors and motors to the main EV3 Brick. Provides both power and data transmission between components and the controller.
📝 Description

LEGO MINDSTORMS EV3 Cables are specialized cables with 6-pin connectors, designed by LEGO to reliably connect MINDSTORMS system components. The cables feature built-in pin identification, which prevents incorrect connections. Each cable carries both power (for motors and sensors) and data (I2C, UART) for two-way communication.
🔧 Technical Specifications

Specification    Value

Connector Type    6-pin LEGO connector (proprietary)

Standard connector    Modified RJ12 (not compatible with telephone cables)

Signal voltage    7.2–9.0 V (for power); TTL 3.3 V (for data)

Maximum current    2 A per power line

Wire material    4 conductors (2 for power + 2 for data) copper, cross-section ~0.14 mm²

Insulation material    PVC (polyvinyl chloride)

Cable diameter    ~3 mm

Available lengths    20 cm, 35 cm, 50 cm

Color coding	Cables come in different colors for easy identification

Contacts    6 gold-plated contacts for a reliable connection

Cable resistance    ~0.5 Ohm (for power wire)

Maximum insulation resistance    >10 MΩ

Standard operating temperature    -10°C to +50°C

Flexibility    High — the cable bends easily without damage

⚡ Power specifications

•    Nominal voltage: 7.2 - 9.0 V (supplied by the battery via the EV3 Brick)

•    Maximum current: 2.0 A per cable

•	Voltage drop: ~0.1 V per 35 cm of cable at 1 A

•    Data lines: I2C (400 kHz) and UART at 9600/19200 baud

________________________________________
📊 Summary table of voltages for all components

Component    Nominal voltage	Operating range    Max. current

EV3 Brick    7.2 - 9.0 V    7.2 - 9.0 V    2.0 A

EV3 Medium Motor    7.2 - 9.0 V    7.2 - 9.0 V    1.5 A

Ultrasonic Sensor    7.2 - 9.0 V	7.2 - 9.0 V    60 mA

Color Sensor    7.2 - 9.0 V    7.2 - 9.0 V    100 mA

Pixy 2.1    5.0 V ⚠️    4.75 - 5.5 V    120 mA

EV3 Battery    7.2 V	5.6 - 8.4 V    2.5 A

Wire (cable)    7.2 - 9.0 V    7.2 - 9.0 V    2.0 A

⚠️ WARNING: Pixy 2.1 requires 5V!
Pixy 2.1 operates at 5.0V, which is differs from the standard 7.2–9.0V voltage of all other EV3 components. Be sure to use a DC-DC step-down converter (7.2–9.0V → 5V) to connect the camera safely.
________________________________________
🔧 Wiring Diagram
EV3 Battery (7.2–9.0V)
    │
    ├─→ EV3 Brick
    
    │       │
    │       ├─→ Port A: EV3 Medium Motor
    
    │       │
    │       ├─→ Port 1: EV3 Color Sensor
    
    │       │
    │       ├─→ Port 2: EV3 Ultrasonic Sensor
    
    │       │
    │       └─→ Port 3: Pixy 2.1 (via a 5V DC-DC converter!)
    
    │
    └─→ EV3 cables (for connecting components)
    
________________________________________
________________________________________






 Software Architecture and Obstacle Strategy
 ====
1. Code Modularity and the State Machine
Despite the use of a visual programming environment (EV3 Education), the software architecture is based on the principles of modularity. The main program loop is a finite state machine (FSM) with several clearly defined states:

INIT State: Port initialization, variable reset (line counter = 0), setting of basic parameters (Setpoint = 60, Kp = ±4).

WALL_FOLLOWING state (Round 1): Basic movement using a P-controller.

COLLISION / OVERRIDE state: Processing of touch sensor activation (port 1). When pressed, the robot stops the steering motor and engages forward motion (50%) for 2 seconds. This allows the robot to be freed from a jam or to forcibly set the start vector.

OBSTACLE_AVOIDANCE state (Round 2): Object recognition via computer vision (Pixy2) and execution of evasion maneuvers.

FINISH state: All motors stop after 13 red or blue lines are detected.
<img width="1264" height="777" alt="How the clockwise code works" src="https://github.com/user-attachments/assets/c8e810f8-e666-4d79-b319-bd45ec424c0d" />

Algorithm Justification
====
Lane-following Strategy (Round 1): A proportional controller (P-controller) is used instead of relay control. Data from the ultrasonic sensor (port 4) is compared to the target distance (60 cm).
Formula: Error = Distance - 60. The control action is calculated as Turn = Error * Kp.
To adapt to the direction of movement (clockwise/counterclockwise), we programmatically change the sign of the coefficient (Kp = 4 or Kp = -4). The main motor operates at -40% reverse thrust to ensure optimal torque.
<img width="1362" height="792" alt="image" src="https://github.com/user-attachments/assets/660d5f5b-23d8-4a44-a33d-69b2a98cd6c3" /> <img width="1273" height="787" alt="image" src="https://github.com/user-attachments/assets/a484dcd7-fcf9-44c8-a4e8-8f058cb1f279" />

Obstacle Logic (Round 2):The program’s logic is based on a continuous loop in which the robot selects one of two states every fraction of a second: normal movement or task completion. At the start of each lap, the program checks the “lines” variable (the number of lines): if it is less than 13, the robot continues driving along the track, and if it is equal to 13, it immediately proceeds to the final maneuver—backing up and turning.

While the robot is in motion mode, its behavior is determined by sensors:

The color sensor constantly searches for the blue line: as soon as it sees it, the program reads the current number from memory, adds one to it, and writes it back.

To prevent the robot from counting the same line multiple times, a wait block is built into the code: the program pauses briefly (for example, 0.2 seconds) while the robot physically crosses the line, and only then allows it to move forward.

The rest of the time, while the sensor sees only the floor, the P-controller is active: the robot measures the distance to the wall with an ultrasonic sensor and compares it to the ideal distance of 60 cm.

If the robot deviates from its course, the program multiplies the difference in distance by a coefficient and adjusts the motors to return to the desired distance, simultaneously checking the Pixy2 camera for obstacles.

In this way, the algorithm allows the robot to consistently maintain a distance from the wall and accurately track the path traveled until the number of markers reaches the finish value.
<img width="1881" height="628" alt="image" src="https://github.com/user-attachments/assets/3d2df106-4307-456a-96c3-6ef66cbb0514" />


Handling Edge Cases
====
The system is designed to account for potential hardware failures and physical limitations:

Steering Mechanism Protection: The calculated turn angle is strictly limited by software limits within the range [-75, 75]. This prevents the servo motor from locking up due to abnormal spikes in the ultrasonic sensor’s readings.
<img width="742" height="508" alt="image" src="https://github.com/user-attachments/assets/002852a2-d630-4207-9aaf-eefbc35cf2ad" />

Color Sensor Debounce: When a red or blue line is detected, the program increments the counter and forcibly pauses color checking for 2 seconds. This eliminates false multiple triggers on the same line during slow movement.
<img width="1016" height="491" alt="image" src="https://github.com/user-attachments/assets/7979323d-15c0-40ff-854c-f0138ac92c3a" />

Ignoring background noise in Pixy2: In the absence of signatures (Signature 3), the robot continues moving in a straight line without reacting to random light glare on the track.

Testing, Tuning, and Performance Metrics
====
During the iterative testing and tuning process, the controller parameters were calibrated:

When Kp > 5, overcorrection (chassis oscillations) was observed.

At Kp < 3, the robot could not react quickly enough to changes in the turning radius.

The optimal value of Kp = ±4 provides a balance between smoothness and response speed.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (13)" src="https://github.com/user-attachments/assets/a7211525-c4b9-4bf8-b349-a25a2d4a5d79" />

Performance Metrics: The main criterion for the algorithm’s success was the stable completion of 13 consecutive sections with a maximum deviation from the target line (60 cm) of no more than ±5 cm, as well as 100% activation of the lap counter without missing any red or blue markers.


 Development Iterations & Risk Management
 ====
Through extensive field testing and multiple trial runs, we refined both the mechanical structure and the control algorithms to ensure maximum reliability under competition conditions.

Key achievements of our iterative process:

Proactive Path Planning: Unlike simple wall-following, our P-regulator is tuned to maintain a safe "buffer zone" (61 cm). By comparing operational risks, we decided to keep the robot further from obstacles to account for sensor noise and mechanical drift, significantly reducing the probability of collisions.
<img width="1920" height="1080" alt="Can be nervous if the Kp (gain) is too high" src="https://github.com/user-attachments/assets/28a79547-caed-46f2-9727-31079515332c" />

Collision Recovery System: We implemented a reliable safety logic. In the event of an unexpected impact or friction with a barrier, the algorithm detects the stall or distance anomaly and triggers an automated "recovery maneuver." The robot can back away from the obstacle and realign its steering to continue the race without human intervention.

Risk vs. Speed Optimization: Our final configuration represents the best balance between high-speed performance and collision avoidance. Multiple runs proved that a slightly more conservative path (further from walls) results in more consistent lap times and prevents DNF (Did Not Finish) scenarios.

Final Documentation Overview
====
We have fully documented our engineering process to ensure transparency and provide a clear roadmap for our project. The following materials are included to support our work:

Comprehensive Build Instructions: A detailed guide on the robot's construction is provided, ensuring that the mechanical design is fully reproducible.

Component & Sensor Logic: Each hardware part is listed with its specific function, explaining how the sensor placement (Ultrasonic on Port B, Color on Port C) contributes to the robot's performance.

Visual Evidence: We have provided high-quality video demonstrations showing the robot’s real-world behavior, successfully counting lines and maintaining trajectory.

Software Clarity: All algorithms are explained through professional flowcharts and clean Python (Pybricks) code, bridging the gap between theoretical logic and physical execution.

This documentation serves as a complete record of our engineering journey, proving that our robot is not just functional, but built upon solid, well-documented principles.

Photos of robot:
====



Team photo:
====
<img width="1600" height="1200" alt="BexAryn" src="https://github.com/user-attachments/assets/77646167-b3c5-4791-b07c-f3218fafd2ae" />
Thanks for your attention and bye!
