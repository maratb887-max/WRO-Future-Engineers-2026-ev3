<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/5ee21ce6-bb96-4127-bcb3-85b6660cba90" />


Introduction:
We are a team cybercrafters participating in WRO Future Engineers 2026. Our team members are Marat Beksultan and Sadyrov Aryn.
Project Vision:
Our team focused on developing an autonomous mobile robot capable of high-speed navigation and precise obstacle avoidance. The primary objective was to create a robust system that combines mechanical stability with an advanced software architecture to handle the dynamic challenges of the WRO competition.

Engineering Approach:
To achieve 100% reliability, we implemented a Proportional-Control (P-regulator) steering system. This allows our robot to maintain a consistent distance from boundaries with fluid movements, minimizing the energy loss caused by sharp corrections. Our design philosophy centers on three core pillars:

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

Obstacle Logic (Round 2):The program’s logic is based on a continuous loop in which the robot selects one of two states every fraction of a second: normal movement or task completion. At the start of each lap, the program checks the “lines” variable (the number of lines): if it is less than 13, the robot continues driving along the track, and if it is equal to 13, it immediately proceeds to the final maneuver—backing up and turning.

While the robot is in motion mode, its behavior is determined by sensors:

The color sensor constantly searches for the blue line: as soon as it sees it, the program reads the current number from memory, adds one to it, and writes it back.

To prevent the robot from counting the same line multiple times, a wait block is built into the code: the program pauses briefly (for example, 0.2 seconds) while the robot physically crosses the line, and only then allows it to move forward.

The rest of the time, while the sensor sees only the floor, the P-controller is active: the robot measures the distance to the wall with an ultrasonic sensor and compares it to the ideal distance of 60 cm.

If the robot deviates from its course, the program multiplies the difference in distance by a coefficient and adjusts the motors to return to the desired distance, simultaneously checking the Pixy2 camera for obstacles.

In this way, the algorithm allows the robot to consistently maintain a distance from the wall and accurately track the path traveled until the number of markers reaches the finish value.
<img width="1881" height="628" alt="image" src="https://github.com/user-attachments/assets/3d2df106-4307-456a-96c3-6ef66cbb0514" />


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


4. Development Iterations & Risk Management
Through extensive field testing and multiple trial runs, we refined both the mechanical structure and the control algorithms to ensure maximum reliability under competition conditions.

Key achievements of our iterative process:

Proactive Path Planning: Unlike simple wall-following, our P-regulator is tuned to maintain a safe "buffer zone" (61 cm). By comparing operational risks, we decided to keep the robot further from obstacles to account for sensor noise and mechanical drift, significantly reducing the probability of collisions.
<img width="1920" height="1080" alt="Can be nervous if the Kp (gain) is too high" src="https://github.com/user-attachments/assets/28a79547-caed-46f2-9727-31079515332c" />

Collision Recovery System: We implemented a reliable safety logic. In the event of an unexpected impact or friction with a barrier, the algorithm detects the stall or distance anomaly and triggers an automated "recovery maneuver." The robot can back away from the obstacle and realign its steering to continue the race without human intervention.

Risk vs. Speed Optimization: Our final configuration represents the best balance between high-speed performance and collision avoidance. Multiple runs proved that a slightly more conservative path (further from walls) results in more consistent lap times and prevents DNF (Did Not Finish) scenarios.

5. Final Documentation Overview
We have fully documented our engineering process to ensure transparency and provide a clear roadmap for our project. The following materials are included to support our work:

Comprehensive Build Instructions: A detailed guide on the robot's construction is provided, ensuring that the mechanical design is fully reproducible.

Component & Sensor Logic: Each hardware part is listed with its specific function, explaining how the sensor placement (Ultrasonic on Port B, Color on Port C) contributes to the robot's performance.

Visual Evidence: We have provided high-quality video demonstrations showing the robot’s real-world behavior, successfully counting lines and maintaining trajectory.

Software Clarity: All algorithms are explained through professional flowcharts and clean Python (Pybricks) code, bridging the gap between theoretical logic and physical execution.

This documentation serves as a complete record of our engineering journey, proving that our robot is not just functional, but built upon solid, well-documented principles.

Photos of robot:

<img width="1600" height="1200" alt="right view" src="https://github.com/user-attachments/assets/d1ff1eac-baa3-4088-9be2-86c79198981f" />
<img width="1200" height="1600" alt="Bottom view" src="https://github.com/user-attachments/assets/06b69a2e-8908-489e-9b63-77ed9f57ab7a" />
<img width="1200" height="1600" alt="Top view" src="https://github.com/user-attachments/assets/8bcb4239-896e-4f17-a2f1-6381f7ebb017" />
<img width="1200" height="1600" alt="rear view" src="https://github.com/user-attachments/assets/e8c86329-95f6-455d-99b4-17dd4c1b1c62" />
<img width="1600" height="1200" alt="left view" src="https://github.com/user-attachments/assets/8adb96dc-8525-4f07-9e63-ea1d873be744" />
<img width="1200" height="1600" alt="Front view" src="https://github.com/user-attachments/assets/fa8211f1-d32f-47f6-8eb0-2e954fd5c8ac" />

Team photo:
<img width="1600" height="1200" alt="BexAryn" src="https://github.com/user-attachments/assets/77646167-b3c5-4791-b07c-f3218fafd2ae" />
Thanks for your attention and bye!
