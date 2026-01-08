# The Elite Shuttle Service Web Application 
The Elite Shuttle Service Web Application for Autonomous Pupil Shuttle (Team Elite)

## Main Contributor  
Nivetha Saravanan ([niv9244s](https://git.hs-coburg.de/niv9244s))

## Component Description  
This component focuses on the design and development of a web application derived from a high-fidelity desktop GUI prototype for the Autonomous Pupil Shuttle System. Its primary goal is to provide parents with real-time updates on their child’s shuttle journey, enhancing transparency, trust, and peace of mind. The application integrates essential features such as live location tracking, real-time video monitoring, notification alerts based on ROS 2 topics, and an estimated time of arrival (ETA) display. These functionalities are driven by ROSBridge communication and a modular frontend developed in React. The design and functionality are directly based on findings from user-centered research and iterative prototype testing sessions with parents, ensuring that the application aligns with actual user expectations and needs.

---

## Table of Contents  
- [User Research and Human-Centered Design Process](#user-research-and-human-centered-design-process)  
- [User Survey Demographics](#user-survey-demographics)
- [Emotional Response Analysis](#emotional-response-analysis)
- [Criteria C3: Implementation of User Interface Based on Findings of M4](#criteria-c3-implementation-of-user-interface-based-on-findings-of-m4)  
- [Screens](#screens)  
- [Low-Fidelity Prototypes](#low-fidelity-prototypes)  
- [High-Fidelity Prototype](#high-fidelity-prototype)  
- [Design Principles Used](#design-principles-used)  
- [Feature Demand Survey Analysis](#feature-demand-survey-analysis)  
- [Technologies Used](#technologies-used)  
- [Implementation Status (Module 6)](#implementation-status-module-6)
- [Usability Testing](#usability-testing)   
- [Topic Interface Table](#topic-interface-table)  
- [Usage](#usage)  
- [License](#license)

---

## User Research and Human-Centered Design Process

The design process followed a **Human-Centered Design (HCD)** approach to ensure the GUI prototype effectively addresses parents' real concerns about their children's shuttle rides.

### HCD Process Overview

1. **Understanding User Needs**  
   Initial research in Module 4 identified key parental concerns such as safety monitoring, real-time shuttle tracking, and boarding notifications.

2. **Low-Fidelity Prototyping**  
   Based on these insights, three distinct low-fidelity prototype concepts were created in Figma, each exploring different communication styles and feature layouts.

3. **User Testing and Feedback Collection**  
   Comparative usability testing sessions were conducted with **31 parents** across multiple countries:
   - Germany (in-person sessions)
   - India, Canada, USA, UK, France (via Google Meet)

4. **Survey-Based Feedback**  
   After the walkthrough, participants completed a structured questionnaire via **Google Forms**, providing feedback on usability, clarity, and overall preference.

   🔗 **Survey Link:** [Google Form Questionnaire](https://docs.google.com/forms/d/e/1FAIpQLSeLkcUiKzaQ65e2LrqfRX22crVzHstuje8RgOYrDBt9pU6Zwg/viewform?usp=header)  

5. **Data Analysis and Prototype Selection**  
   The collected responses were analyzed using a comparison matrix with evaluation criteria such as clarity, feasibility, and user satisfaction.

📊 **Prototype Selection Result:**  
The feedback from user sessions was analyzed and visualized using the chart below.

<div align="center">
    <img src="user_research/Prototype Comparison Pie Chart.png" alt="Prototype Feedback Pie Chart">
</div>

**Low-fidelity Prototype 2** was selected by the majority (55%) of users, indicating its strong alignment with parental expectations for clarity, safety communication, and interface simplicity.

<div align="center">
    <img src="user_research/Low-fi 2 prototype.png" alt="Selected Low-fidelity Prototype 2">
</div>

---

## User Survey Demographics

### Participant Breakdown:
- **Total Respondents:** 31 parents
- **Age Range:** 24–45 years (average 32.4 years)
- **Countries Represented:**
  - Germany: 14 participants
  - India: 6 participants
  - Canada/USA: 5 participants
  - Other (France, UK, Luxembourg): 6 participants

### Key Characteristics:
- 87% had school-going children (ages 4–10)
- 65% had no prior experience with school transportation apps
- 71% reported being "Comfortable" or "Very Comfortable" with desktop applications

---

## Emotional Response Analysis

The survey revealed strong positive emotional responses to the prototype design:

| Sentiment           | Count | Percentage |
|---------------------|-------|------------|
| Confident using it  | 25    | 80.6%      |
| Safe                | 22    | 71.0%      |
| Reassured           | 18    | 58.1%      |
| Overwhelmed         | 5     | 16.1%      |

*Note: Parents could select multiple emotional responses*

<div align="left">
    <img src="user_research/Emotional response to app.png" alt="Emotional Response Graph">
</div>

---

## Criteria C3: Implementation of User Interface Based on Findings of M4 

### User Story: C3.1  
*As a developer, I want to design a human-centered high-fidelity desktop GUI app for the autonomous pupil shuttle, so that parents are informed about their child's journey status during shuttle rides.*

#### Acceptance Criteria

- **AC1:** Based on the top identified themes in M4, at least three distinct low-fidelity design concepts must be developed, each addressing a minimum of 1–2 parental concerns and showcasing different communication strategies.  
- **AC2:** All low-fidelity prototype concepts must be evaluated through user feedback sessions with parents. The collected feedback must be recorded and analyzed using a comparison matrix to identify the concept that best aligns with parental needs, feasibility, and clarity of communication.  
- **AC3:** The low-fidelity concept receiving the most positive feedback must be selected and taken as the foundation for the high-fidelity prototype. From the low‑fidelity prototype finalized through user research, the high‑fidelity prototype must be developed.

---

## C3. Functional Integration of Interactive Features into an Intuitive, Parent-Facing Web Application GUI : Module 6

### 🧑‍💻 User Story

*As a developer, I want to create a fully functional web application with a clean, intuitive interface, so that parents can easily interact with all essential features like shuttle live-location tracking, student live-video monitoring, real-time notifications, and viewing estimated arrival times for pickup.*

---

### ✅ Acceptance Criteria

- **AC1:** Based on insights from the high-fidelity prototype developed during M5, the web application must include the following core features: **live location tracking**, **notification panel**, and **ETA display**.

- **AC2:** The application must be developed using **React** for the frontend and **ROSBridge** for backend communication with the shuttle system.

- **AC3:** If `behaviour = standing`, a **notification is triggered** and the parent is offered a **mic button** for optional **two‑way voice communication**.

- **AC4:** The **ETA data** must be displayed in the pickup summary section, subscribing to `/ego_planned_path` and `/odom`.

- **AC5:** The app must subscribe to the following ROS 2 topics:  
  `/boarding_completed`, `/vehicle_state`, `/student_location` and display corresponding **notifications** in the UI (e.g., “Nivetha has boarded at 08:05”).

- **AC6:** Notifications must be **time-stamped**, listed in a **scrollable panel**, and **visually distinct** for different event types.

- **AC7:** The application should be bilingual, available in both German and English.

---

## Technologies Used

- **Frontend:** React (Vite), TypeScript, Tailwind CSS, Leaflet (for map)
- **Backend:** Node.js (Express), ROS2 integration via ROSBridge WebSocket (`ws://localhost:9090`)
- **Image Stream:** RealSense camera feed via `/camera/camera/color/image_raw`
- **Notifications:** WebSocket-based real-time updates
- **ETA Calculation:** Based on path data and odometry
- **Development Platform:** Replit (used for integrated development and real-time previews)

---

## Implementation Status (Module 6)

This web app is currently under **active development**. As of now:

- ✅ Real-time **notifications** are successfully displayed from relevant ROS 2 topics  
- ✅ Basic **map rendering** and **live video streaming** implemented  
- ⚠️ Full integration with ROSBridge (`ws://localhost:9090`) is pending resolution  
- 🛠️ Planned path drawing and ETA display logic are written, awaiting full ROS message reception


---

## Usability Testing

During system-level testing in the Model City:

- 👨‍👩‍👧 **3 participants** interacted with the ShuttleGuardian web app  
- ✅ **2 users** responded positively to its layout and clarity  
- ⚠️ **1 user** voiced concerns over:
  - **Privacy**, suggesting **child’s face should be visible only to their own parent**
  - **Past experiences of bullying**, and proposed the addition of **anti-bullying mechanisms**

### 💡 Future Feature Suggestions:
- 🧒 **Face blurring** for students not associated with the logged-in parent  
- 🧠 **AI-based monitoring** to detect potential bullying or distress behavior in real-time  

Feedback collected from this usability test has been documented and will be incorporated in future development cycles.

---

## 🧾 Topic Interface Table

| **Topic**                          | **I/O** | **Message Type**                       | **Description**                                                                 |
|-----------------------------------|---------|----------------------------------------|---------------------------------------------------------------------------------|
| `/map`                            | Input   | `nav_msgs/msg/OccupancyGrid`           | Renders the Model City map as a grid layout                                    |
| `/ego_pose`                       | Input   | `geometry_msgs/msg/PoseStamped`        | Vehicle position for marker movement                                           |
| `/ego_planned_path`              | Input   | `nav_msgs/msg/Path`                    | Path visualization for future route                                            |
| `/odom`                           | Input   | `nav_msgs/msg/Odometry`                | Current vehicle velocity used for ETA                                          |
| `/student_location`              | Input   | `std_msgs/msg/String`                  | Notifications when student's house is reached (e.g., “First student house reached”) |
| `/boarding_completed`            | Input   | `std_msgs/msg/Bool`                    | Triggered once when boarding is complete                                       |
| `/vehicle_state`                 | Input   | `std_msgs/msg/String`                  | “drop_off” triggers school arrival alert                                       |
| `/camera/camera/color/image_raw` | Input   | `sensor_msgs/msg/Image`                | RealSense live video camera feed                                               |
| `/behaviour_status`              | Input   | `custom_msgs/msg/BehaviourStatus`      | Shows “Standing” alert, offers two-way voice                                  |

---

## Screens

| **Screen**               | **Purpose**                                                                  |
|--------------------------|------------------------------------------------------------------------------|
| Home Dashboard           | Overview of shuttle live-location, student live-monitoring, notifications & emergency contact info         |
| Live Shuttle Location    | Map-based tracking using simulated OptiTrack data                            |
| Notification Panel       | Displays notifications such as boarding confirmation and waypoint status     |
| Student Info Overview    | Shows picture and student details, which could be edited                     |
| Student Live Monitoring  | Displays live video for monitoring student safety                |
| Contact Us Page          | Provides space to input user suggestions/queries, which the company will address and revert back   |

---

## Low-Fidelity Prototypes

[🔗 View All Low-Fidelity Design Concepts](https://www.figma.com/design/klLHdmcnt3OJUM4pb9ZOJS/Low-fi-Wireframe-Template--Community-?node-id=123-0&t=RYfZrK2OqOlmbtzg-1)

---

## High-Fidelity Prototype

[🔗 High-Fidelity Prototype Link](https://www.figma.com/design/klLHdmcnt3OJUM4pb9ZOJS/The-Elite?node-id=842-1719&t=Os8z0dqVDOb7uVdS-1)

---

## Design Principles Used

- **Similarity**
- **Proximity**
- **Common Region**

---

## Feature Demand Survey Analysis

![Feature Demand](user_research/Feature%20Demand.png)

---

## Installation
1. Clone the repository:
```bash
 git clone https://git.hs-coburg.de/Team_ELITE/TheEliteShuttleService.git
```
2. Navigate to the project directory:
```bash
 cd TheEliteShuttleService
```
3. Install dependencies for frontend:
```bash
 cd ../server
 npm install
```
4. Install dependencies for backend:
```bash
 cd ../server
 npm install
```

## Usage
### Launching the Nodes
Starting the Application

1. Launch ROSBridge:
```bash
ros2 launch rosbridge_server rosbridge_websocket_launch.xml
```
2. Start the backend server:
```bash
cd server
npm run dev
```
3. Start the frontend application:
```bash
cd ../client
npm run dev
```
4. Open the web browser and navigate to:
```bash
http://localhost:5000
```

## Testing
Manual Testing
Verify that the web app loads and all modules respond as expected:

✅ Real-time notifications panel updates based on /boarding_completed, /path_data, /vehicle_state, and /behavior_status

✅ Live video stream is served from Flask backend at /video_feed

✅ Map section shows dynamic routing when ROS topics are live

✅ Time-stamped logs are visible in the Notification panel

Note: Use simulated or real ROS2 publishers to test each topic response.

## License

This project is licensed under the **Apache 2.0 License** - see the [LICENSE](LICENSE) file for details.
