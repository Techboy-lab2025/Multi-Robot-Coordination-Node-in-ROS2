# Robot Simulation Project

This project contains a simple robot simulation using ROS2, MQTT, and FastAPI. It simulates robot movement, status reporting, and control via a REST API and MQTT messaging.

## Features

- **ROS2 Simulation**: A ROS2 node that simulates robot movement by publishing velocity commands.
- **Robot Control API**: A FastAPI server that accepts velocity control commands via REST API.
- **MQTT Integration**: The system can publish and subscribe to robot status updates over MQTT.
- **Docker Support**: Dockerfile included for easy deployment of the simulation.

## Prerequisites

Before running the project, make sure you have the following installed:

- **ROS2** (e.g., Foxy)
- **Docker** (for containerized deployment)
- **Python 3.8+**
- **MQTT Broker** (e.g., Mosquitto)

## Setup Instructions

1. **Clone the repository**:

    ```bash
    git clone https://github.com/Techboy-lab2025/robot_simulation_project.git
    cd robot_simulation_project
    ```

2. **Create a Python virtual environment (optional)**:

    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install dependencies**:

    Install Python dependencies:
    ```bash
    pip install -r requirements.txt
    ```

    Build ROS2 workspace:
    ```bash
    colcon build
    ```

4. **Run the ROS2 node**:

    Once dependencies are set up, you can run the robot simulation node with the following command:
    ```bash
    ros2 run robot_simulation robot_simulation_node
    ```

5. **Run the FastAPI server** (for control via API):

    To start the API server:
    ```bash
    uvicorn robot_control_api:app --reload
    ```

6. **Start the MQTT broker** (if not already running):

    You can use a local or public MQTT broker. If you don’t have one set up, you can use the public Mosquitto broker:
    ```bash
    mosquitto -v
    ```

7. **Run the Docker container** (optional):

    If you'd prefer to run the entire system in a Docker container, use the provided `Dockerfile` to build and run the container:
    ```bash
    docker build -t robot_simulation_image .
    docker run -it --rm robot_simulation_image
    ```

## API Endpoints

### POST `/cmd_vel`

This endpoint accepts velocity control commands to move the robot.

#### Request Body Example:
```json
{
  "linear_x": 0.5,
  "angular_z": 0.0
}

