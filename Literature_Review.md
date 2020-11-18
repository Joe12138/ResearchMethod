# <center>Self-driving cars: A survey</center>

1. The architecture of the autonomy system of self-driving cars is typically organized into the **perception system** and the **decision-making system**.

2. The perception system is generally divided into many subsystems responsible for task such as **self-driving-car localization**, **static obstacles mapping**, **moving obstacles detection** and **tracking**, **road mapping**, **traffic signalization detection** and **recognition**, among others.

3. The **decision-making system** is commonly partitioned as well into  many subsystems responsible for tasks such as **route planning**, **path planning**, **behavior selection**, **motion planning**, and **control**.

4. Typical architecture of self-driving cars

   <img src="C:\Users\Joe Lan\Desktop\WenxingLan\2020_fall\ResearchMethod\LReview\photo\aritecture.png" alt="aritecture" style="zoom:75%;" />

The **Perception** system is responsible for estimating the State of the car and for creating representation of the environment, using **data captured by on-board sensors**, such as Light Detection and Ranging (LIDAR), Radio Detection and Ranging (RADAR), camera, Global Positioning System (GPS), Inertial Measurement Unit (IMU), odometer, etc., and **prior information** about the sensors' models. road network. traffic rules, car dynamics, etc.

The **Decision Making** system is responsible for navigating the car from its initial position to the final goal defined by the user, considering the current car's State and the internal representation of the environment, as well as traffic rules and passengers' safety and comfort.

The **Localizer** subsystem is responsible for estimating the car's State (pose, linear velocities, angular velocities, etc.) in relation to static maps of the environment.

These static maps, or **Offline Maps**, are computed automatically before the autonomous operation, typically using the sensors of the self-driving car itself, although manual annotations (i.e., the position of pedestrian crosswalks or of traffic lights) or editions (for removing non-static objects captured by sensors) are usually required.

The **Mapper** subsystem receives as input the Offline Maps and the self-driving car's State, and generates as output the online map. This online map is typically a merge of information present in the Offline Maps and the current car's State.

The **Moving Objects Tracker** subsystem, or **MOT**, receives the Offline Maps the self-driving car's State, and detects and tracks the nearest moving obstacles.

The **Traffic Signalization Detector** subsystem, or **TSD**, is responsible for the detection and recognition of traffic signalization. It receives the Sensors' data and the car's State, and detects the position of the traffic signalizations.

Given a Final Goal defined in the Offline Maps by the user, the **Route Planner** subsystem computes a Route, **$W$**, in the offline Maps, from the current self-driving car's State to the Final Goal. A route is a sequence of way points, i.e. $W={w_1,w_2,...,w_{|W|}}$, where each way point, $w_i$, is a coordinate pair, i.e. $w_i=(x_i,y_i)$, in the Offline Maps.

The **Behavior Selector** subsystem is responsible for choosing the current driving behavior, such as lane keeping, intersection handling, traffic light handling, etc. It does so by selecting a Path, $P_j$, in $P$, a pose, $p_g$, in $P_j$ a few seconds ahead of the current self-driving car's State, which is the decision horizon, and the desired velocity at this pose. The pair pose in $P_j$ and associated velocity is called $Goal_g=(p_g, v_g)$. The **Behavior Selector** chooses a Goal considering the current driving behavior and avoiding collisions with static and moving obstacles in the environment within the decision horizon time frame.

The **Motion Planner** subsystem is responsible for computing a Trajectory, $T$, from the current self-driving car's State to the current Goal, which follows the Path defined by the Behavior Selector, satisfies car's kinematic and dynamic constraints, and provides comfort to the passengers. A Trajectory $T=\{c_1, c_2,...,c_{|T|}\}$ may be defined as a sequence of commands, $c_k = (v_k, \varphi_k, \Delta t_k)$, where $v_k$ is the desired velocity at time $k$, $\varphi_k$ is the desired steering angle at time $k$, and $\Delta_{t_k}$ is the duration of $c_k$. A Trajectory takes the car from its current State to the current Goal smoothly and safely.

The **Obstacle Avoider** subsystem receives the Trajectory computed by the Motion Planner and change it (typically reducing the velocity), if necessary, to avoid collisions.

The **Controller** subsystem receives the Motion planner trajectory, eventually modified by the Obstacle Avoider subsystem, and computes and sends Effort commands to the actuators of the steering wheel,  throttle and brakes in order to make the car execute the Modified Trajectory as best as the physical world allows.

5. Self-driving car's perception
   1. Localization
      - LIDAR-based localization
      - LIDAR plus camera-based localization
      - Camera-based localization
   2. Offline and  online mapping of unstructured environments
   3. Road mapping
   4. Moving Objects Tracking
   5. Traffic Signalization Detection

6. Self-driving car's decision making
   1. 





