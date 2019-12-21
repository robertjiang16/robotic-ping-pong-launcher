# Conclusion

## Discussion

Overall, our robot did meet most of the design criteria that we set out to achieve in this project. The robot was able to locate and sense the AR tag, as well as aim at the target container and adjust the angle to the ideal ping pong launch angle. There was a complication in the launch angle calculated when the target container was placed in a location below the z-coordinate of the base of the robot, but this can be solved with aome slight adjustments to the code. We would have liked to introduce more complexity into the design of the robot but did not receive the opportunity; some of these complexities include launching over an obstacle or launching from any location within the reachable workspace.

## Difficulties in Implementation

The difficulties that we encountered can be separated into two distinct categories: hardware/mechanics and physics/calculations.

### Hardware and Mechanics

Our project was not only an in-depth look at physics and code, but also an introduction to the world of mechanical engineering. The robot incorporated a launcher system as well as an air-pressurized gauge, and we learned very quickly about potential inaccuracies and inconsistencies that occur in mechanical engineering endeavors.

The first challenge we encountered was in the reliability of our launcher. We did not have the tools necessary to control the air pressure dispensed into it. We also had no good way to measure our initial velocity. Overall, much of the difficulty came as a consequence to our lack of experience and familiarity with the Sawyer. For instance, we struggled to obtain a clear reading for the coordinates of the AR marker attached to our target. After days of trying to fix the problem we realized by accident that using the right hand camera instead of the head camera got rid of the problem entirely.

### Physics and Calculations

Calculating the physics at the core of our project was much less straightforward than anticipated. There was some confusion in using the correct transforms and observed variables to insert into the formulas as well as in finding the formulas themselves. For more information on some of the calculation-based difficulties experienced in our project, take a look at [Physics and Calculations](physics.md).

In the end, while the challenges we faced delayed our progress immensely, each served as a great opportunity to learn.

## Improvements
Does your solution have any flaws or hacks? What improvements would you make if you had additional time?

Despite the apparent success of the robotic ping pong ball launcher, there aspects of the project that could be improved in future iterations of this technology.

### Launcher

The launcher is arguably the most important component to the project, as it is the element that launches the ball into the container and determines the efficacy of the robot. Throughout our implementation, we used a very basic design, with a cardboard tube to insert the ball, a hole to attach the air pressurized gauge to, and a cardboard tube for the ball to be launched from. We chose to use cardboard for our design because of limited expenses and easy manipulability and design adjustment. For future iterations of the launcher, the material used would ideally be PVC pipe or another more stable and solid medium.

Along this line, the air pressure gauge that we used for the implementation of our device did not have any opportunities for pressure adjustment. Ideally, the launcher would have a function allowing for adjustment of the air pressure being released from the gauge, as well as a way to control for the direction of air flow.

One final adjustment that should be made to the launcher in more improved versions of the robot would be to physically attach the launcher to the Sawyer arm. The launcher was attached to the arm using duct tape and holes in a cardboard backing attached to the tube. Because the launcher was removed and reattached every time the robot was adjusted or worked with, the trajectory of the ping pong ball as it was released from the tube was altered each time; controlling for this by attaching the launcher to the arm itself would be the most ideal situation to reconcile the need to remove the launcher with the trajectory of launch.

### Camera

Another important element incorporated into our project was the camera; for the implementation of the project, the Sawyer right arm camera was used to scan for and detect the AR tag attached to the target container. However, the functionality of the Sawyer right arm camera was severely limited throughout the implementation of our project; at distances greater than about 7 feet away, the camera would no longer be able to detect the AR tag, even when it is in the camera's range of vision. Using a better camera, such as a RealSense, would improve the functionality of the robot and allow it to launch the ping pong ball more accurately at farther distances.

Additionally, our robot was hindered by its dependency on the AR tag attached to the target container; the container could only be located by the robot if the AR tag was directly visible to the camera. Finding a way to sense the target container without the AR tag (for example, using image segmentation and a better camera) would remove this dependency and allow this technology to be applied to a broader range of real-world applications.

### Physics

Further improvements could be made to the calculations implemented in our code. The calculations performed by the system as a whole do not take into account the drag forces acting on the ping pong ball from the point that it is released from the launcher to the moment that it reaches the target container. Because these drag forces are not considered, the trajectory and ideal launch angle calculated by the system is inaccurate and would not be conducive to accurate robotic operation. Taking these extraneous forces into account when calculating the trajectory as well as possibly adding an attachment to determine the air currents that could affect the ping pong ball and factoring those into the calculations would make the device more accurate when launching.

For more information on the physics aspect can be improved, click the following link: [Physics and Calculations](physics.md).

### Miscellaneous

Some further improvements that can be made to our project involve its complexity and what different functions it can perform. One idea our team had for introducing complexity to our project was to have the robot be able to launch the ping pong ball at a moving target container using a Turtlebot. Programming the robot to launch a ping pong ball at a target container that is never in the same location at any point would increase it's ability to be applied to other real-world applications.

### [Return to home](index.md)
