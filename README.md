Mobility, Design, and Control Strategy

The robot’s design was developed with stability, maneuverability, and precision of movement in mind. The robot is built on a “tractor-type” configuration: smaller wheels with a slick surface are mounted at the front, while larger studded wheels connected to the main drive are located at the rear.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (1)" src="https://github.com/user-attachments/assets/7d300361-8527-422d-b58f-badd76d72f16" />


This design ensures an effective distribution of functions: the rear wheels act as drive wheels and are responsible for transmitting torque, while the front wheels provide directional stability and improve maneuverability. The larger diameter of the rear wheels increases off-road capability and reduces the impact of uneven terrain, as well as improving acceleration efficiency.
<img width="1564" height="1195" alt="wheel illustration" src="https://github.com/user-attachments/assets/d4fb4c74-772f-4718-b711-75b01e13a98a" />

The initial design version used studded tires, designed to achieve maximum speed through reduced rolling resistance. However, testing revealed that this configuration led to slippage, particularly during turns and sudden accelerations, which reduced driving precision.
<img width="1564" height="1195" alt="smaller wheels with a studded surface" src="https://github.com/user-attachments/assets/a158220b-4b3c-4986-b143-8832e0cb3fcb" />


As a result, the decision was made to switch to slick tires. This increased traction and improved handling stability. Thus, a deliberate trade-off was made: a slight reduction in top speed in exchange for improved handling, precision, and reliability. You can see the comparison of slick and studded tires
<img width="1564" height="1195" alt="smaller wheels with a studded surface (4)" src="https://github.com/user-attachments/assets/e93acd6a-3870-46af-ae62-1ed64dee6b91" />

The main motor is mounted on the rear axle, as it bears the main load. This allows for efficient power transmission and minimizes energy loss. The vehicle’s center of gravity is shifted closer to the rear wheels, which further increases the driving wheels’ traction. All components are rigidly mounted to reduce vibrations and improve stability.
<img width="1564" height="1195" alt="comparison of motors" src="https://github.com/user-attachments/assets/4813b880-ecff-4f56-baf9-9827ab92922a" />

During development, alternative design options were considered, including the use of identical wheels and other drive configurations; however, these yielded poorer results in terms of stability and control.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (6)" src="https://github.com/user-attachments/assets/055f526a-aeb9-4965-9845-a9b7490b2e87" />

A number of improvements were also implemented at the software strategy level. In the initial version, the robot did not use an ultrasonic sensor, as the primary goal was to achieve maximum speed and simplify the algorithm. The absence of the sensor allowed for reduced data processing delays and faster movement.
However, testing showed that at high speeds, the probability of collision with the track walls increases due to the orientation errors and the lack of feedback from the environment.

To improve reliability, an ultrasonic sensor was added, and the movement strategy was modified. Instead of moving in a straight line, a zigzag algorithm was implemented that continuously measures the distance to the edge.
Navigation Strategy Comparison: Open-Loop vs. Ultrasonic Feedback
<img width="1564" height="1195" alt="smaller wheels with a studded surface (7)" src="https://github.com/user-attachments/assets/76725d59-8757-47ba-a416-8a1f912acb20" />
The robot moves at a slight angle to the wall, periodically measuring the distance and correcting its direction to maintain a safe distance. This approach compensates for movement errors and significantly reduces the risk of collision.

As with the choice of wheels, an engineering compromise was made here as well: a slight reduction in speed and increased algorithm complexity in exchange for a significant improvement in stability and accuracy.

Tests confirmed that the chosen mechanical design and control strategy ensure more reliable and predictable robot behavior when performing tasks.
Performance comparison:
<img width="1408" height="768" alt="Comparison of ultrasonic sensor" src="https://github.com/user-attachments/assets/49abf324-214b-4ee9-8a37-8ab7925a272a" />

2. Power and Sensor Management
The robot’s power and sensor system is designed to meet requirements for reliability, operational stability, and energy efficiency.

A rechargeable battery is used as the power source, providing a stable voltage to all system components. The main power consumers are the drive motor, the controller, and the sensors. The motor bears the heaviest load, as it is responsible for the robot’s movement; therefore, the power system is designed with a power reserve to prevent voltage drops during acceleration and maneuvers.
<img width="2560" height="2560" alt="battery" src="https://github.com/user-attachments/assets/e5471fda-6c8b-4220-a8b8-a7b187e2b00a" />

Power distribution is organized to minimize losses and ensure stable sensor operation. The wiring is kept as short and neat as possible, which reduces resistance and minimizes the impact of electrical interference.

Special attention was paid to the selection and placement of the sensors.
<img width="972" height="597" alt="image" src="https://github.com/user-attachments/assets/7bb2c716-8af4-496a-af7d-060426aa0b76" />

The ultrasonic sensors are mounted at an angle relative to the direction of travel. This design expands the detection zone and reduces “blind spots,” enabling earlier detection of obstacles.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (8)" src="https://github.com/user-attachments/assets/8fcc9ca3-b9ee-4a4c-a0db-d5942991ac15" />

The camera is positioned at the top of the structure and tilted forward. This placement increases the field of view and allows for early detection of objects on the track, giving the robot more time to make decisions.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (9)" src="https://github.com/user-attachments/assets/87316b1c-6bf7-4e1b-9753-90482e6aadd9" />

<img width="500" height="375" alt="image" src="https://github.com/user-attachments/assets/17d4ddfc-4844-484a-95a1-30a98efc4d6e" />
The gyroscopic sensor is mounted inside the body, closer to the center of the structure. This protects it from external influences and vibrations, and also improves measurement accuracy. The gyroscope is used to stabilize movement, maintain a straight-line trajectory, and improve turning accuracy.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (10)" src="https://github.com/user-attachments/assets/3c1565b2-207e-45c7-9289-b66761636bd1" />

<img width="225" height="201" alt="image" src="https://github.com/user-attachments/assets/1aaa0ba4-687e-4a46-bbd5-e86ed44b70bd" />
The color sensor is pointed downward toward the track surface. Its primary function is to detect colored lines and count laps. When moving counterclockwise, the robot counts blue lines; when moving clockwise, it counts red lines. Each detected color marker is recorded by the counting system. After registering 12 lines, the robot automatically stops, which corresponds to completing three full laps of the track. This solution allows for precise distance control and completion of the task without additional intervention.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (11)" src="https://github.com/user-attachments/assets/956e5191-53a6-42fc-9f4d-95cf268fe63d" />

<img width="1009" height="831" alt="image" src="https://github.com/user-attachments/assets/a8ca67ea-c905-47fc-8fa0-cece381f544b" />
The touch sensor is mounted at the front of the robot, as close as possible to the front edge of the structure. This placement allows it to be the first to detect a potential collision with an obstacle or the track wall. When the sensor is triggered, the robot immediately performs a protective maneuver: it stops, moves backward, and then continues moving according to the algorithm. This reduces the likelihood of getting stuck and damaging the structure, as well as increases the reliability of completing the track.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (12)" src="https://github.com/user-attachments/assets/b7de9152-a277-42c5-96e7-8164f969b722" />

During development, potential failure points were taken into account, such as unstable sensor readings and electrical interference. To address these, data filtering methods and pre-launch calibration are employed.

As a result, the power supply and sensor system has been optimized to ensure reliable, accurate, and stable robot operation under competition conditions.

Section 3: Software Architecture and Obstacle Strategy
1. Code Modularity and the State Machine
Despite the use of a visual programming environment (EV3 Education), the software architecture is based on the principles of modularity. The main program loop is a finite state machine (FSM) with several clearly defined states:

INIT State: Port initialization, variable reset (line counter = 0), setting of basic parameters (Setpoint = 60, Kp = ±4).

WALL_FOLLOWING state (Round 1): Basic movement using a P-controller.

COLLISION / OVERRIDE state: Processing of touch sensor activation (port 1). When pressed, the robot stops the steering motor and engages forward motion (50%) for 2 seconds. This allows the robot to be freed from a jam or to forcibly set the start vector.

OBSTACLE_AVOIDANCE state (Round 2): Object recognition via computer vision (Pixy2) and execution of evasion maneuvers.

FINISH state: All motors stop after 13 red or blue lines are detected.
<img width="1264" height="777" alt="How the clockwise code works" src="https://github.com/user-attachments/assets/c8e810f8-e666-4d79-b319-bd45ec424c0d" />

2. Algorithm Justification

Lane-following Strategy (Round 1): A proportional controller (P-controller) is used instead of relay control. Data from the ultrasonic sensor (port 4) is compared to the target distance (60 cm).
Formula: Error = Distance - 60. The control action is calculated as Turn = Error * Kp.
To adapt to the direction of movement (clockwise/counterclockwise), we programmatically change the sign of the coefficient (Kp = 4 or Kp = -4). The main motor operates at -40% reverse thrust to ensure optimal torque.
<img width="1362" height="792" alt="image" src="https://github.com/user-attachments/assets/660d5f5b-23d8-4a44-a33d-69b2a98cd6c3" /> <img width="1273" height="787" alt="image" src="https://github.com/user-attachments/assets/a484dcd7-fcf9-44c8-a4e8-8f058cb1f279" />

Obstacle Logic (Round 2): A Computer Vision (CV) algorithm based on the Pixy2 camera is used. To filter out noise, the program analyzes the array of detected objects and selects the largest one based on the area of the bounding rectangle (Width x Height). This ensures that the robot reacts only to the nearest block. Depending on the color signature (Signature 1 or 2), the steering motor turns by ±45 degrees, the robot moves forward for 1.0 seconds (Base Speed = 30), after which the wheels return to the zero position (centering).Also, it uses color sensor and if he sees blue line 13 times robot is doing final moves for parking.
<img width="1855" height="658" alt="image" src="https://github.com/user-attachments/assets/0f409b24-0177-4337-a1ab-9acffbe56a43" />

3. Handling Edge Cases
The system is designed to account for potential hardware failures and physical limitations:

Steering Mechanism Protection: The calculated turn angle is strictly limited by software limits within the range [-75, 75]. This prevents the servo motor from locking up due to abnormal spikes in the ultrasonic sensor’s readings.
<img width="742" height="508" alt="image" src="https://github.com/user-attachments/assets/002852a2-d630-4207-9aaf-eefbc35cf2ad" />

Color Sensor Debounce: When a red or blue line is detected, the program increments the counter and forcibly pauses color checking for 2 seconds. This eliminates false multiple triggers on the same line during slow movement.
<img width="1016" height="491" alt="image" src="https://github.com/user-attachments/assets/7979323d-15c0-40ff-854c-f0138ac92c3a" />

Ignoring background noise in Pixy2: In the absence of signatures (Signature 3), the robot continues moving in a straight line without reacting to random light glare on the track.

4. Testing, Tuning, and Performance Metrics
During the iterative testing and tuning process, the controller parameters were calibrated:

When Kp > 5, overcorrection (chassis oscillations) was observed.

At Kp < 3, the robot could not react quickly enough to changes in the turning radius.

The optimal value of Kp = ±4 provides a balance between smoothness and response speed.
<img width="1564" height="1195" alt="smaller wheels with a studded surface (13)" src="https://github.com/user-attachments/assets/a7211525-c4b9-4bf8-b349-a25a2d4a5d79" />

Performance Metrics: The main criterion for the algorithm’s success was the stable completion of 13 consecutive sections with a maximum deviation from the target line (60 cm) of no more than ±5 cm, as well as 100% activation of the lap counter without missing any red or blue markers.
