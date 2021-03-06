# triped_description
This repository contains descriptions and configuration files for the TriPed robot.
This includes a URDF of a simplified Robot model (since the TriPed is a hybrid chain it can not be represented using URDF, see [here](trip-kinematics.readthedocs.io/en/main/) )
as well as rqt configurations for a TriPed GUI:

## TriPed-GUI
This package can be used as a TriPed-GUI, with rqt perpectives and a robot visualisation in rviz.

### How to use the TriPed GUI 
Clone this repo into your catkin workspace src folder.
### Robot visualisation in rviz

Execute:   
`source devel/setup.bash`  
`catkin_make`  
`roslaunch triped_description display.launch`  
#### TriPed-GUI in rqt
On a different terminal execute:
`./rqt/rqt-bbb-as-master.sh` if you are using the Beaglebone, or `rqt` if you are using a simulation.
Load the TriPed-GUI perspective file into rviz.  
Start the joint_level_controller on the BeagleBone or use a Simulation of the TriPed.

### Some views of the TriPed GUI
![The TriPed-Gui](/docs/pictures/triped-gui-rqt-only.png)
This shows the rqt gui, containing a topic monitor, a Message Publisher, a topic plotter and a Runtime Monitor plugin. The Topic monitor has the OK diagnostic message of the right swing joint highlighted. The plotter shows the positions of the left and right swing joints. Using the Message publisher, it is possible to send commands to the joints, as shown here.

![The TriPed-Gui with console on startup](/docs/pictures/triped-gui-position-monitoring-startup.png "The TriPed-Gui & console startup")
This picture shows the startup of the joint level controller. The TriPed-GUI is on the left and the console output of the controller is on the right.

![The TriPed-Gui with console running OK](docs/pictures/triped-gui-ok.png "The TriPed-Gui & console on normal operation")
This picture shows the TriPed-GUI and the controller console output on normal operation.
The GUI shows, that no errors occurred in the topic monitor.

![The TriPed-Gui with console ERROR](docs/pictures/triped-gui-error.png "The TriPed-Gui & console on ERROR state")
This picture shows the TriPed-GUI and console output in ERROR state. The hall sensor was disconnected for this picture, to reach the ERROR state. The console output clearly shows the error types occurring and the GUI shows that the diagnostics for the left swing joint have been updated to show the joint in ERROR state.
The diagnostic montior plugin however doesn't always work and may need a diagnostic aggregator to work reliably.

### Some views of the rviz visualisation

![Rviz with the TriPed](docs/pictures/triped_rviz.png "Rviz with the TriPed model on startup")
This picture shows the robot visualization in rviz, with the updated TriPed model. Currently a joint_state_publisher is used to manipulate the model. It can be seen to the right. In the future, a ros node using Trip will be reading in the joint states and updating the visualization based on the actual joint readings.

![Rviz with the TriPed](docs/pictures/triped_rviz_2.png "Rviz with the TriPed model")
This picture shows how to manipulate the model usign the joint_state_publisher.
