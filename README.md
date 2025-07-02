# AI-Powered-Smart-Fire-Extinguisher-Network-with-Digital-Twin-Based-Risk
This project is a real-time fire safety solution that integrates sensors, machine learning, and alert systems to detect and respond to fire risks before they escalate.

**Overview:**
An Arduino board continuously collects environmental data using sensors for temperature, humidity, smoke, and flame detection. These readings are sent over serial to a Python program, where a machine learning model analyzes the data and predicts whether a fire risk exists.

**Core Logic**
The system follows a multi-step logic:

**1.Data Collection**

Sensors gather live readings of temperature, humidity, smoke levels, and flame intensity. A temperature history is maintained to detect sudden spikes.

**2.Fire Risk Evaluation**
The Python program receives this data and feeds it into a trained machine learning model (Random Forest). The model uses five inputs:

a)Current temperature
b)Humidity
c)Smoke level
d)Presence of flame
e)Temperature spike based on historical average

Based on this input, the model outputs either 0 (safe) or 1 (fire risk).

**3.Response Actions**
If a fire risk is predicted:

The servo motor is triggered to simulate a fire extinguisher.

An SMS alert is sent to a registered phone number using Twilio.

The data and risk status are published to Adafruit IO for cloud monitoring.

The risk status is sent to a Flask server.

**4.Visualization**
A Unity application fetches the live risk level from the Flask API. It updates the 3D interface:

Shows a green cube when safe.

Shows a red cube with fire and extinguisher effects when a fire risk is detected.

**5.Safety Reset**
If no fire risk is detected in the next cycle, the system resets the servo, clears SMS flags, and updates the visualization to reflect a safe state.

**Technologies Used**
The system uses Arduino for sensing, Python for data processing and AI, Flask for serving the risk level, Twilio for SMS alerts, Adafruit IO for IoT dashboarding, and Unity for real-time visualization.

**Purpose**
The project demonstrates how intelligent decision-making using sensor data and AI can lead to faster, smarter fire risk detection. By combining hardware, software, and cloud services, it offers a proactive safety system suitable for industrial or smart building environments.
