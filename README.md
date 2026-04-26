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
