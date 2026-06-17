<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/b2be791f-2c42-4b7e-a28f-207d86795835" />
Introduction:
====
We are a team Nishtyak participating in WRO Future Engineers 2026. Our team members are Marat Beksultan and Sadyrov Aryn.
Project Vision:
Our team focused on developing an autonomous mobile robot capable of high-speed navigation and precise obstacle avoidance. The primary objective was to create a robust system that combines mechanical stability with an advanced software architecture to handle the dynamic challenges of the WRO competition.

Engineering Approach:
To achieve 100% reliability, we implemented a Proportional-Control (P-regulator) steering system. This allows our robot to maintain a consistent distance from boundaries with fluid movements, minimizing the energy loss caused by sharp corrections. Our design philosophy centers on three core pillars:

Mobility, Design, and Control Strategy
====

# 1. Mobility & Mechanical Design

1. Mobility and Mechanical Design (Мобильность и механическая конструкция)

Design Overview

Our robot's construction has undergone several profound iterations of engineering analysis to achieve an optimal balance between:


✅ Speed on straight sections (> 0.8 m/s)

✅ Stability in turns (roll angles not exceeding 2-3°)

✅ Reliability with obstacles (no damage when touching walls)

✅ Positioning accuracy (route error < 5 cm)



2. Justification for Architecture Selection (Drivetrain Selection Rationale)

2.1 Rear-Wheel Drive System (RWD - Rear-Wheel Drive)

Why RWD instead of FWD or 4WD?

┌─────────────────────────────────────────────────┐

│         CONFIGURATION ANALYSIS          
│
├─────────────────────────────────────────────────┤

│                                                   │
│  FWD (Front-Wheel Drive):  
│
│  ❌ During acceleration, transfers weight forward│

│  ❌ Front wheels lose traction     
│
│  ❌ Complex steering mechanism (motor + drive) │

│                                                   │

│  4WD (Four-Wheel Drive):                        │

│  ❌ Requires 4 motors + gearboxes (expensive)   │

│  ❌ Difficult traction control in turns         │

│  ❌ Excessive weight for WRO Future Engineers   │

│                                                   │

│  ✅ RWD (Rear-Wheel Drive):                     │

│  ✅ Weight shifts backward during acceleration   │

│  ✅ Improved traction on driving wheels         │

│  ✅ Simple construction with single motor       │

│  ✅ Full control of front wheel steering angle  │

│  ✅ Minimum wheel slipping on smooth floor      │

│                                                   │

└─────────────────────────────────────────────────┘


Physics of RWD System

Traction Force Formula:

Traction Force = μ × Normal Force

where:

  μ = coefficient of friction between wheel and floor (~0.6-0.8 for slick on WRO linoleum)
  
  Normal Force = weight acting on driving wheels


RWD Advantage During Acceleration:


During acceleration, center of gravity shifts backward → ↑ pressure on rear wheels

↑ Normal Force on rear wheels → ↑ maximum traction force

Result: minimum wheel slipping, maximum acceleration



2.2 Parallel Steering Mechanism

Comparison of Steering Mechanisms

ParameterAckermann TrapezoidParallel Steering (Our Choice)PrincipleInner wheel turns at a larger angleBoth front wheels turn at the same angleConstruction ComplexityHigh (crossbar, levers)Low (direct motor transmission)System BacklashDue to multiple joints (±1-2°)Minimal backlash (±0.5°)Space RequirementsRequires wide wheelbaseCompact, ideal for narrow wheelbaseTurning AngleLimited by geometry (~30-35°)Can be adjusted up to 45-50°Cost$$$ (many LEGO parts)$ (Simple Gear Ratio System)Applicability for WROBetter for larger robots (>30 cm)✅ Ideal for compact (~25 cm)

Constructive Implementation of Parallel Steering Mechanism


           EV3 Medium Motor
                  │
                  ▼
          Gearbox (20:1)
                  │
                  ▼
        Main Gear (45T)
                  │
                  ├─────────┬─────────┐
                  ▼         ▼         ▼
            Intermediate Shaft + BACKLASH-FREE COUPLING
                  │
         ┌────────┴────────┐
         ▼                 ▼
    Left Steering   Right Steering
    Wheel          Wheel

Result: Angle α = identical for both wheels

        Turning Radius R = wheelbase distance / sin(α)


3. Design Iterations and Compromise Analysis (Design Iterations & Trade-offs)

During 8 weeks of testing, we reconsidered the initial concept, moving away from a bulky "tractor-like" design toward a more compact sports variant with improved dynamics.

3.1 Evolution of Construction

<img width="1920" height="1080" alt="Parameter" src="https://github.com/user-attachments/assets/47b09a2b-55b9-4714-8e8d-8aa12950b144" />


3.2 Physical Parameters - V1 vs V2 Comparison

╔════════════════════════════════════════════════════════════════╗

║              PERFORMANCE IMPROVEMENTS (V1 → V2)                ║

╠════════════════════════════════════════════════════════════════╣

║                                                                  ║

║  Maximum Speed:                                                 ║

║  V1: 50 cm/s  →  V2: 72 cm/s                [↑ 44%]            ║

║                                                                  ║

║  Roll in Turn (at R = 50 cm):                                  ║

║  V1: 4.0°  →  V2: 2.5°                      [↓ 37%]            ║

║                                                                  ║

║  Line Following Accuracy:                                       ║

║  V1: ±2.5 cm  →  V2: ±1.5 cm                [↓ 40%]            ║

║                                                                  ║

║  Object Detection Reliability (Pixy 2.1):                      ║

║  V1: 72% success  →  V2: 84% success        [↑ 17%]            ║

║                                                                  ║

║  Robot Weight:                                                  ║

║  V1: 1200 g  →  V2: 700 g                   [↓ 42%]            ║

║                                                                  ║

║  Power Consumption (at 60 cm/s):                               ║

║  V1: 38 W  →  V2: 28 W                      [↓ 26%]            ║

║                                                                  ║

╚════════════════════════════════════════════════════════════════╝


4. Key Mechanical Solutions (Key Mechanical Solutions)

4.1 Roll Reduction System in Turns

Problem with V1: The robot turned too aggressively, losing stability and speed in turns.

V2 Solution - Three approaches simultaneously:


Wheelbase Extension (Wheelbase Extension)

Increased axle distance from 150 → 150 mm (maintained for stability)
Physics: moment of inertia increases → more stable rotation



Center of Gravity Lowering (CG Lowering)

Moved battery lower by 1.5 cm
Effect: reduced CG height from 11 cm → 9.5 cm
Result: maximum moment causing roll reduced by approximately 18%



Increased Track Width (Track Width)

Moved wheels further apart by 8 mm
Greater moment of resistance to roll





Turn Stability Formula:

Critical Roll Angle = arctan(g × v² / (R × h))

where:
  g = 9.81 m/s²
  v = movement speed
  R = turning radius
  h = center of gravity height

Reducing h from 11 cm to 9.5 cm → critical angle increased by approximately 18%

4.2 Traction and Weight Optimization (Traction & Weight Optimization)

What we did: In V1 the robot was heavy and often slipped. In V2 we optimized weight and battery placement.

<img width="1920" height="1080" alt="Parameter (1)" src="https://github.com/user-attachments/assets/deaa8701-f79a-4522-bcd2-fd848c1f9db3" />


Conclusion: Reducing weight from 1200 g to 700 g gave us better dynamics without requiring special wheel modifications.


5. Component Placement (Component Placement Strategy)

5.1 V2 Chassis Topology

                    ┌─────────────────────┐
                    │   Pixy 2.1 Camera   │
                    │  (positioned at     │
                    │   -20° angle down)  │
                    └────────────┬────────┘
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
    ┌───▼────┐          ┌────────▼────────┐          ┌───▼────┐
    │ Sensor │          │   EV3 Brick     │          │ Sensor │
    │ Color  │          │   + Battery     │          │  US    │
    │ (L)    │          │ (center of mass)│          │  (R)   │
    └───┬────┘          └────────┬────────┘          └───┬────┘
        │                        │                       │
    ┌───────────────────────┬────┴────┬─────────────────────┐
    │                       │         │                     │
    ┌───▼────┐          ┌──────▼──┐ ┌───▼──────┐          ┌───▼────┐
    │ Motor  │          │ Drive   │ │ Drive    │          │ Motor  │
    │ Steering│         │ Wheel L │ │ Wheel R  │          │ Spare  │
    │(Medium)│          │(RW)     │ │(RW)      │          │        │
    └────────┘          └─────────┘ └──────────┘          └────────┘

FRONT OF ROBOT ↑

5.2 Sensor Placement Justification

Color Sensor (Color Sensor)


Position: Approximately centered, between two drive wheels

Height: 1-2 cm above floor (optimal for line following)

Angle: Straight down (0°)

Justification: Maximum stable readings of black line, minimal interference
<img width="1920" height="1080" alt="Parameter (12)" src="https://github.com/user-attachments/assets/dab01ea1-1bb3-49c8-af3d-1d49eb862ff0" />


Ultrasonic Sensor (US Sensor)


Position: Front right (offset +15 cm to the right) and front left

Height: 8-10 cm above floor

Direction: Forward, with slight downward angle (-10°)

Justification: Proportional regulator
<img width="1920" height="1080" alt="Parameter (13)" src="https://github.com/user-attachments/assets/8bb28250-c374-43dd-a487-62ccd2c10893" />


Pixy 2.1 (Camera)


Position: Front, between two ultrasonic sensors

Height: 12-15 cm above floor

Direction: Forward and down at -15° angle

Justification: Wide field of view for detecting colored blocks on floor. -20° angle allows seeing objects 40-100 cm ahead
<img width="1920" height="1080" alt="Parameter (14)" src="https://github.com/user-attachments/assets/8647fc31-7751-4084-83de-b0db0cd676b3" />




6. Trade-offs and Limitations (Trade-offs & Constraints)

6.1 Main Trade-offs

<img width="1920" height="1080" alt="Parameter (2)" src="https://github.com/user-attachments/assets/231321bf-2038-43f6-9837-61600c8b2c8e" />


6.2 Residual Problems (Known Limitations)


<img width="1920" height="1080" alt="Parameter (11)" src="https://github.com/user-attachments/assets/42838e11-02ae-4822-b2c1-005a7a75d291" />



7. Recommendations for Further Improvements (Future Improvements)

7.1 Short-term (Before Next Round)


 Install tire pressure sensor for traction control
 
 Add accelerometer for more accurate roll control
 
 Conduct wind-tunnel testing of streamlined chassis


7.2 Mid-term (By Next Season)


 Consider four-wheel steering mechanism (4WS) for improved maneuverability
 
 Try carbon fiber elements instead of LEGO for 20% weight reduction
 
 Add IMU sensor for stabilization at high speeds



8. Conclusions

V2 represents an optimal balance for WRO Future Engineers:

✅ Speed increased by 44% (50 to 72 cm/s) thanks to weight reduction and design optimization

✅ Navigation accuracy improved by 40% (±2.5 cm → ±1.5 cm) through reduced roll and improved stability

✅ Object detection reliability improved by 17% (72% → 84%) with proper sensor placement

✅ Weight reduced by 42% (1200 g to 700 g), significantly improving dynamics

✅ Power consumption reduced by 26% (38 W → 28 W) → battery lasts longer

V2 mechanics are ready for competition. This is a simple, reliable LEGO robot with well-proven construction.


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

<img width="1920" height="1080" alt="Parameter (3)" src="https://github.com/user-attachments/assets/23404343-594e-43e1-a069-ecc30e017e75" />


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

<img width="1920" height="1080" alt="Parameter (4)" src="https://github.com/user-attachments/assets/29a86348-49a1-4874-8c98-9d72ff649ce6" />


⚡ Power specifications
•		Rated voltage: 7.2–9.0 V (matches the EV3 Brick)

•    Operating current (no load): 200–300 mA

•    Peak current (maximum load): up to 1.5 A

•	Power consumption per second (at full power): ~2 Wh

________________________________________
Ultrasonic Sensor EV3
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/5099b5b3-a6de-48d9-ac0f-09ca4261db56" />

🎯 Function
Function & Software Implementation:
The ultrasonic sensor measures the distance to objects in front of the robot. In our project, it serves a dual purpose: first, it provides feedback for the P-regulator by continuously tracking the distance to the wall and adjusting Motor A's steering angle based on the calculated error to keep the robot parallel to the borders; second, during the final stage, it acts as a parking trigger by monitoring the distance to the back wall of the garage and immediately stopping Motor D when the distance drops below 35 cm.

📝 Description
The LEGO MINDSTORMS EV3 Ultrasonic Sensor (distance sensor) works on the principle of echolocation, similar to the sonar used by bats and dolphins. The sensor emits an ultrasonic signal and measures the time it takes for the reflected signal to return, calculating the distance to the object. This allows the robot to navigate its environment with confidence and safely complete WRO tasks.

🔧 Technical Specifications

<img width="1920" height="1080" alt="Parameter (6)" src="https://github.com/user-attachments/assets/766ace84-0351-4586-9b99-a214073156ee" />


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

<img width="1920" height="1080" alt="Parameter (7)" src="https://github.com/user-attachments/assets/247d5205-74ab-48bb-b6d9-c007420caeba" />


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

<img width="1920" height="1080" alt="Parameter (8)" src="https://github.com/user-attachments/assets/033bf77c-407f-4c2a-b5f7-1a051ab1459e" />


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

<img width="1920" height="1080" alt="Parameter (9)" src="https://github.com/user-attachments/assets/eaecdbd4-000e-4b4e-b21c-c5dbd5db6890" />


⚡ Power Specifications

•    Nominal voltage: 7.2 V (range 7.2–8.4 V)

•    Maximum output current: 2.0–2.5 A (continuous)

•    Peak current: up to 4 A (briefly when motors are activated)

•    Full charge: 8.4 V, 2100 mAh

•    Full discharge: 5.6 V (shutdown for battery protection)

•    Battery life (typical): 8–12 hours (with moderate use of 2 motors)

________________________________________
Wire EV3

<img width="674" height="296" alt="image" src="https://github.com/user-attachments/assets/dc931efb-70a7-41b9-8b21-d31f97a485b5" />


🎯 Function
Component connection cable — connects all sensors and motors to the main EV3 Brick. Provides both power and data transmission between components and the controller.
📝 Description

LEGO MINDSTORMS EV3 Cables are specialized cables with 6-pin connectors, designed by LEGO to reliably connect MINDSTORMS system components. The cables feature built-in pin identification, which prevents incorrect connections. Each cable carries both power (for motors and sensors) and data (I2C, UART) for two-way communication.
🔧 Technical Specifications

<img width="1920" height="1080" alt="Parameter (10)" src="https://github.com/user-attachments/assets/f6367d07-470b-4222-809e-a897cc5b3069" />


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
<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/2f27f061-325a-4b0d-b419-d8e37379a3cd" />

<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/283add3d-fce4-47b9-9b5a-07b5b734babe" />

<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/035fe0cc-7501-4cf0-851a-c4fb3ae2f32b" />

<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/0b5ec545-ef1a-4a01-983d-77f59082835c" />

<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/c5db02a9-8725-4e21-bb3f-f7f9dde44cc6" />

<img width="960" height="1280" alt="image" src="https://github.com/user-attachments/assets/97e64b03-d991-485e-b332-2911d9a304a0" />

Team photo:
====
<img width="1600" height="1200" alt="BexAryn" src="https://github.com/user-attachments/assets/77646167-b3c5-4791-b07c-f3218fafd2ae" />
Thanks for your attention and bye!
