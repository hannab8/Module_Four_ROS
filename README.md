![Module_Four_ROS](https://github.com/hannab8/Module_Four_ROS/assets/83167499/0f166dc5-0e6f-44c5-ab6b-228bce9cabb9)
# Module Four: ROS

## Introduction
In this fourth module, you will be introduced to ROS (Robot Operating System). It's an open source framework that allows us to develop and control the robot using the tools and libraries that it provides. We will show you how to install ROS and begin to make use of it. Please be sure to follow the instructions as they are written. We want to make sure that you are using the same version we use here in the lab.

## Module Readings

1. **Topics:** A communication channel used in the ROS framework to facilitate the exchange of data between different nodes in a robotic system. 
2. **Nodes:** Individual components that perform tasks, such as sensor data processing, motor control, or higher-level decision-making. They communicate with each other by publishing and subscribing to topics.<br><br>
         2a. **Publisher:** A node that wants to share some data and creates a topic and publishes messages to it.<br>
         2b. **Subscriber:** A node that is interested in the type of data that is being published and can subscribe to the topic. They receive the messages published on the topic and can process the information as needed.<br>
         
3. **Messages:**
4. Packages
5. Code

## Example:

**Topic:** "/move_robot"

**Message Type:** "geometry_msgs/Twist"

**Publisher Node:** move_control

Description: This node controls how the robot moves using linear and angular velocity commands. It publishes "geometry_msgs/Twist" messages on the "/move_robot" topic.
```
import rospy
from geometry_msgs.msg import Twist

rospy.init_node('move_control')
pub = rospy.Publisher('/robot_movement', Twist, queue_size=10)

rate = rospy.Rate(10)  # Publish at 10 Hz

while not rospy.is_shutdown():
    move_cmd = Twist()
    move_cmd.linear.x = 0.2
    move_cmd.angular.z = 0.1
    pub.publish(move_cmd)
    rate.sleep()
```

**Subscriber Node:** movement_execution

Description: This node 
```
import rospy
from geometry_msgs.msg import Twist

def movement_callback(data):
    linear_velocity = data.linear.x
    angular_velocity = data.angular.z
    # Perform robot movement based on velocity commands

rospy.init_node('motion_execution_node')
rospy.Subscriber('/robot_movement', Twist, movement_callback)
rospy.spin()
```

## Assignment

```
1.  Sign into your GitHub Account.

2.  Go to your repository: <YourName>_Training_Modules

3.  Edit your Readme file and format it using the following:
      - Please use a 5 line gap after the previous assignment
      - The first line: "<YourName> Module Four" using H1 (header one)
      - The third line: "Answers:" using H2 (header two)
      - The fifth line: Start an ordered List (1.)



6.  And now you are done! Commit your changes by clicking the 'Commit changes...' button and set the commit message to "Completed Task Four"
```


## References

Here you will find some additional information on ROS. If you have any suggestions on what should be added, please let a team lead know!


