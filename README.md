# Smart Device Management System

An object-oriented Python application designed to manage different smart home devices (sensors, lights, and security cameras) through a unified console interface. This project was developed as part of the EL 162 / 234 Object Oriented Programming curriculum.

## Project Architecture

The system utilizes core Object-Oriented Programming (OOP) principles to ensure clean separation of concerns and data integrity:

*   **Inheritance:** A foundational `SmartDevice` base class manages universal properties (such as device names, unique IDs, and power states), while specialized child classes (`TemperatureSensor`, `SmartLight`, and `SecurityCamera`) extend this functionality.
*   **Encapsulation:** Sensitive state variables like `device_id` and `power_status` are kept strictly private using double underscores (`__`). They are exposed safely via read-only `@property` decorators.
*   **Data Validation:** Setters and initialization checks actively protect the system's integrity by blocking invalid configurations (e.g., rejecting empty device IDs or keeping light brightness bounded strictly between 0% and 100%).

---

## Class Breakdown

### 1. SmartDevice (Base Class)
*   **Attributes:** `name` (Public), `__device_id` (Private), `__power_status` (Private).
*   **Methods:** `turn_on()`, `turn_off()`, and `display_info()`.
*   **Properties:** Clean getters to read the power status and ID without allowing direct external modification.

### 2. TemperatureSensor
*   **Attributes:** Inherits base properties + tracks localized `temperature` levels.
*   **Methods:** `read_temperature()` (failsafe protected: only reads data if the sensor is turned on).

### 3. SmartLight
*   **Attributes:** Inherits base properties + tracks `brightness` percentages.
*   **Methods:** `increase_brightness()` and `decrease_brightness()` (automatically clamped between 0 and 100).

### 4. SecurityCamera
*   **Attributes:** Inherits base properties + monitors `recording_status`.
*   **Methods:** `start_recording()` and `stop_recording()` (failsafe protected: camera must be powered on to record).

---

## Getting Started

### Prerequisites
You only need a standard installation of Python 3.x to run this system. No external dependencies or third-party libraries are required.

### Execution Steps
1. Clone this repository to your local machine.
2. Open your terminal or command prompt and navigate to the project directory.
3. Run the script using the following command:

```bash
python main.py

###Author
*  **Maxwell Mensah
*  **FOE.41.006.110.25
*  **EL 162
