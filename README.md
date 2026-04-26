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
