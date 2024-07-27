# Turtlebot3 Web-based Navigation System

## Project Overview
In this project, I developed a web interface to teleoperate and monitor a Turtlebot3 robot using ROS (Robot Operating System). The web interface, built with ReactJS, enables users to control the robot remotely and view real-time data about the robot's status.

## Key Features
- **Connection Status**: Displays whether the robot is connected or not.
- **Teleoperation**: Provides a web-based joystick for controlling the robot and an emergency stop button.
- **Live Robot Information**: Shows the robot's position, orientation, and linear/angular velocity.
- **Map-based Navigation**: Displays a navigation map where users can set goal locations for the robot to navigate to.

## Technologies Used
- **Ubuntu 20.04**
- **ROS Noetic**
- **ReactJS**
- **ROSBridge**

## File Structure
```
react-ros-robot/
│
├── node_modules/
├── public/
├── src/
│   ├── App.js
│   ├── bootstrap/
│   │   ├── lux-bootstrap.min.css
│   │   ├── sketchy-bootstrap.min.css
│   │   └── spacelab-bootstrap.min.css
│   ├── components/
│   │   ├── About.jsx
│   │   ├── Body.jsx
│   │   ├── Connection.jsx
│   │   ├── Footer.jsx
│   │   ├── Header.jsx
│   │   ├── Home.jsx
│   │   ├── Map.jsx
│   │   ├── RobotState.jsx
│   │   └── Teleoperation.jsx
│   ├── scripts/
│   │   └── config.js
│   ├── index.css
│   ├── index.js
│   ├── reportWebVitals.js
│   └── setupTests.js
├── package.json
```

### Component Descriptions
- **About.jsx**: Contains information about the project and its purpose.
- **Body.jsx**: The main body of the web application.
- **Connection.jsx**: Displays the connection status of the robot.
- **Footer.jsx**: The footer section of the web application.
- **Header.jsx**: The header section of the web application.
- **Home.jsx**: The landing page of the web application.
- **Map.jsx**: Displays the navigation map and allows the user to set the robot's goal location.
- **RobotState.jsx**: Displays live information about the robot's position, orientation, and linear/angular velocity.
- **Teleoperation.jsx**: Provides teleoperation controls, including a web-based joystick and an emergency stop button.

### Config.js
```javascript
const Config = {
  ROSBRIDGE_SERVER_IP: "192.168.8.101",
  ROSBRIDGE_SERVER_PORT: "9090",
  RECONNECTION_TIMER: 3000,
  CMD_VEL_TOPIC: "/cmd_vel",
  ODOM_TOPIC: "/odom",
  POSE_TOPIC: "/robot_pose",
};

export default Config;
```

Note: Update `ROSBRIDGE_SERVER_IP` with the IP address of your ROSBridge server, which can be found using `ifconfig`.

## Setup Instructions

### Prerequisites
- **Ubuntu 20.04**
- **ROS Noetic**
- **Node.js and npm**

### Installation

1. **Download Catkin Workspace**: 
   Download my catkin_ws workspace from [this link](https://drive.google.com/drive/folders/1-u4qolXatmV3-Idyaji1KlyhNpGl1Rss?usp=sharing) and place it in your home directory.
   
2. **Build Catkin Workspace**:
   ```sh
   cd ~/catkin-ws
   catkin_make
   source ~/catkin-ws/devel/setup.bash
   ```

3. **Clone React Project**:
   ```sh
   git clone https://github.com/Sourav9348/react-ros-robot.git
   cd react-ros-robot
   ```

4. **Install Dependencies**:
   ```sh
   npm install
   ```

### Running the Project

1. **Start React Application**:
   ```sh
   npm start
   ```
   The web application will be accessible at `http://localhost:3000`.

2. **Launch ROS Nodes**:
   Open new terminal windows and run the following commands:

   **Terminal 1**:
   ```sh
   roslaunch turtlebot3_gazebo turtlebot3_house.launch
   ```
<img width="1345" alt="Screenshot 2024-07-27 at 5 21 30 PM" src="https://github.com/user-attachments/assets/7ff92a8c-e341-4b35-964b-fd34cf761f2a">

   **Terminal 2**:
   ```sh
   roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=/path/to/catkin-ws/src/tb3map/tb3_house_map.yaml
   ```
<img width="1352" alt="Screenshot 2024-07-27 at 5 21 45 PM" src="https://github.com/user-attachments/assets/3e03ebb0-0ce9-43df-888b-6b9c4ef6b05b">

   **Terminal 3**:
   ```sh
   roslaunch rosbridge_server rosbridge_websocket.launch
   ```

   **Terminal 4**:
   ```sh
   rosrun srm_robot_pose_publisher srm_robot_pose_publisher
   ```

### Usage
- Open your web browser and navigate to `http://localhost:3000`.
- Use the web-based joystick to teleoperate the robot.
- Monitor live data about the robot's status.
- Set goal locations on the navigation map for the robot to follow.

<img width="966" alt="Screenshot 2024-07-27 at 5 20 20 PM" src="https://github.com/user-attachments/assets/ae3349f7-d7db-4dbf-9743-f13186eee95c">


## Conclusion
This project provides a comprehensive web interface for teleoperating and monitoring a Turtlebot3 robot using ROS and ReactJS. The system is designed to be user-friendly and efficient, enabling seamless interaction with the robot.
