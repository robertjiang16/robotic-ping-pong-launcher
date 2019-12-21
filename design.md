# Design

## Design Goals

Our project incorporates elements and robotic devices that are present in the lab, as well as mechanical elements of our own design.

We wanted our robotic arm launcher to have the ability to scan, aim, and launch the ping pong ball into the target container. This directly translates to the desired functionality of our robot; to be able to identify an AR tag attached to the target container, as well as calculate the ideal angle within the reachable workspace to launch the ball into the container.

## Design Implementation

Our design implementation was based in three techniques: sensing, planning, and actuation.

### Sensing

The first action we wanted our device to take was to scan the general area to locate an AR tag attached to a target container. Our desire for the robot was to orient it at around a 45 degree angle and have it sweep through the reachable workspace.

### Planning

The second aspect to our project is the calculation of the ideal launch angle for the launcher, as well as how to orient and position Sawyer's arm to be able to launch the ball. The way we designed this to work was to aim in the zero configuration at the AR tag and adjust the tool joint angle to launch the ball into the container.

To take a look at the math behind our project, click the link below, which leads to our physics and calculations page:

[Physics and Calculations](physics.md)

### Actuation

The final aspect of our project we planned on implementing was the launching of the ball into the target container using the implementation of an air-pressurized gauge and controlled launcher. Our launcher was attached to the Sawyer arm using duct tape and holes within a cardboard backing attached to the launcher.

## Benefits and Trade-offs

### Benefits

There are many benefits to the design that we chose as we were deciding how we wanted to implement it. The first is the design of the launcher; we chose to use recycled cardboard pieces (cardboard tubes and box parts) to create our launcher in order to reduce the expenses present in the actuation of the device. The use of cardboard to create our launcher not only allowed us to save money on the overall implementation of the device, but it also allowed us to make very quick and easy fixes to the launcher if there were any changes that we wanted to make.

Additionally, the way that we implemented the planning aspect simplified a lot of code. By having the robot enter the zero configuration (save for the configuration of the base, which is angled to point at the container) and only adjusting the tool joint to angle and launch, implementing the code was much easier. This is because there is less trajectory planning involved with this implementation and less concern regarding how the arm will reach the desired position. These variables were controlled in our design.

### Trade-offs

However, although the above benefits that we listed were ideal for the implementation of our robot in this class, they came with some trade-offs that would definitely need to be addressed in future implementations. One of these is the material used for the launcher. Although it was cheap and easy to adjust, this also meant that the launching was much more inaccurate than if we had used a more sturdy material, such as PVC pipe. The launch angle may have been correct for our device but the constant shifting of the launcher in our implementation shifted this angle slightly in some instances.

Additionally, although we had the robot enter the zero configuration and adjust the joint angle in order to simplify the code in many places, we were unable to introduce as much complexity into our project as we had originally intended to.

## Design Choices and their Impacts

The main choice that we made regarding the launcher and the material used to make it was the major factor in the design criteria of a real engineering application. Because we chose to reduce the cost and difficulty of attachment of the launcher, we lost aspects of durability and efficiency, as cardboard is very mendable and non-durable, which leads to inaccuracies in the efficiency of launching the ping pong ball.

### [Return to home](index.md)
