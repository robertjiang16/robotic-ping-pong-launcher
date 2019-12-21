# Physics and Mathematics

## Problem

The main problem our calculations intend to address is determining the ideal joint torques to position the robot arm in the optimal position to shoot the ball into the container. 

The trajectory of the ball primarily depended on its velocity, the position relative to the cup, and the angle of the launcher. Many secondary factors such as the spin of the ball, air resistance, air currents, and forward kinematics errors also affect this trajectory.  

## Approaches

### Deep RL Approach

Our initial plan involved using a Deep RL approach using a Hierarchical Actor-Critic (HAC) as implemented by Levy et al (Paper referred to - https://openreview.net/pdf?id=ryzECoAcY7).  Our rationale for this implementation was that using a deep learning architecture would allow us to model all secondary factors without using complex equations with numerous variables that would not always be feasible. The reason for working with a HAC was that the different hierarchies of the model would be able to learn different subtasks to achieve the final goal in parallel. This would allow for faster and more precise calculations. 

We experimented with a UR5 reacher environment in Mujoco using Levy’s HAC to test the feasibility of using this approach. We tested 3, 4 and 6 layer models with various horizon, penalty and test frequency parameters. The results looked good and the arm was able to learn how to accurately move to goal positions with an average success rate of over 95%. 

However, we realized that this simulation-based approach had two major problems. Firstly, training the model to near optimality took over 8 hours. We could not afford to have such a large bottleneck in our iteration process as we needed to constantly tune our hardware alongside our software to improve the launcher’s ability to make consistent shots. Additionally, this was only the training time for the movement stage of the model and training time would more than double once we introduced trajectory calculations and other dynamics. The second problem with this approach was that our model would be training completely in a simulation environment as training a physical robot for 8 hours while manually moving the container and loading the balls was infeasible. Once the robot was trained in Mujoco, it’s performance was not guaranteed to be the same when tested on the physical robot and we would have to constantly tune parameters and introduce thresholds.

### Newtonian Approach

As a result, we decided to physically model the primary factors using a physical model. Even though this approach would limit our potential accuracy, it was much more time-efficient to work with and improve.  

We modeled the trajectory of the ball using projectile motion equations that we derived using Newton’s laws. The next two sections will explain how we measured known values and how we derived the equations.

## Measurements

We first required 2 values to be able to rotate the base of the arm along the z-axis: the x- and y-axis distance of the container to the arm of the robot. We found these values by taking the tf_echo transforms of the base of the arm with respect to the AR tag on the container. This was used to calculate <img src="https://render.githubusercontent.com/render/math?math=$theta_{1}$">, the angle of the base joint. 

Next, we had to calculate the angle for the launcher. As shown in the figure below, we had to measure 6 variables to be able to determine ideal values for the “pitch angle” of the shooter. We will refer to this angle as <img src="https://render.githubusercontent.com/render/math?math=$theta_{2}$"> and apply it to joint 5. 

The x- and z-axis distances were calculated using tf_echo transforms. <img src="https://render.githubusercontent.com/render/math?math=$L$"> was calculated using the iOS measurement app and verified using a ruler. The initial velocity of the ball was calculated using a slow-motion video of the ball being shot with scale in the background for reference. We used this video to determine the distance traveled by the ball in many short time increments and averaged to get an estimated velocity. We adjusted this estimate by taking readings of the ball being shot at 45° and used the standard projectile motion equations to determine the velocity.
