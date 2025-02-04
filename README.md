# AI-Powered-Mobile-Robot-for-Assistance-Interaction
This repository contains resources to build an AI-powered mobile robot for telepresence, smart advertising, personal assistance, and delivery. Features include autonomous navigation, an AI voice assistant, and a touchscreen display. Follow the documentation for assembly, software setup, and testing. Contributions are welcome!
# **AI-Powered Mobile Robot for Assistance & Interaction - Complete Documentation**

## **1. Introduction**
This document provides a step-by-step guide to building an **AI-powered mobile robot** for **telepresence, smart advertising, personal assistance, and delivery**. The robot is designed to be **autonomous**, **AI-integrated**, and **cost-effective**, aligning with the goals of the Open Droids Builder Challenge.

---
## **2. Project Overview**
### **Key Features:**
- **Autonomous Navigation** – Uses LiDAR and ultrasonic sensors to avoid obstacles.
- **AI Voice Assistant** – Integrates OpenAI API or Google Assistant.
- **Touchscreen Display** – For user interaction and smart advertising.
- **Motorized Movement** – Controlled by motors and microcontrollers.
- **Battery-Powered** – Rechargeable power supply for long runtime.

### **Use Cases:**
- Virtual meetings and remote communication.
- Dynamic advertising displays based on location.
- Smart assistant for home automation and security patrol.
- Transporting small items in offices, hospitals, and homes.

---
## **3. Bill of Materials (BoM) & Purchase Links**

| Component              | Name                        | Price (Approx) | Purchase Link |
|------------------------|----------------------------|---------------|---------------|
| **Microcontroller**    | Raspberry Pi 4 (4GB)       | $80           | [Amazon](https://www.amazon.com/dp/B07TD42S27) |
| **Motor Driver**       | L298N                       | $10           | [Amazon](https://www.amazon.com/dp/B07L5Y8F6X) |
| **Motors**            | 12V DC Motors (2x)         | $30           | [SparkFun](https://www.sparkfun.com/products/13231) |
| **LiDAR Sensor**      | RPLiDAR A1                  | $150          | [AliExpress](https://www.aliexpress.com/item/4000342951334.html) |
| **Battery**           | 12V 10Ah Li-ion             | $50           | [AliExpress](https://www.aliexpress.com/item/33058927362.html) |
| **Touchscreen Display** | 10” Tablet                 | $100          | [Best Buy](https://www.bestbuy.com/site/searchpage.jsp?st=10%22+touchscreen+tablet) |
| **Speaker & Mic**      | USB Audio Module           | $15           | [Amazon](https://www.amazon.com/dp/B00X4WHP5E) |
| **Frame**             | Aluminum/3D Printed        | $30           | Local Supplier |
| **Total Estimated Cost** | **$465**                 | -             | - |

---
## **4. Circuit Diagram & Wiring Instructions**
- **Microcontroller connections:** Raspberry Pi connected to motor driver, LiDAR, and display.
- **Power distribution:** Battery connected to motor driver and Raspberry Pi.
- **Sensors integration:** LiDAR and ultrasonic sensors wired to detect obstacles.
- **Audio module:** Mic and speakers connected via USB.

---
## **5. Software & AI Integration**
### **Operating System & Software Stack:**
- **Ubuntu or Raspberry Pi OS** (for Raspberry Pi)
- **Robot Operating System (ROS)** for navigation
- **OpenCV** for vision processing
- **OpenAI API/Google Assistant** for voice interaction

### **Installation Commands:**
```bash
sudo apt update && sudo apt upgrade
sudo apt install ros-noetic-desktop-full
pip install openai opencv-python numpy flask
```

### **AI Voice Assistant Code (Python):**
```python
import openai
import speech_recognition as sr

def ai_assistant():
    recognizer = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        audio = recognizer.listen(source)
    
    text = recognizer.recognize_google(audio)
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "system", "content": "You are a helpful assistant."},
                  {"role": "user", "content": text}]
    )
    print("AI Response:", response["choices"][0]["message"]["content"])

ai_assistant()
```

### **Navigation Code (ROS & LiDAR Integration):**
```python
import rospy
from sensor_msgs.msg import LaserScan

def lidar_callback(data):
    print("Obstacle detected at:", min(data.ranges))

rospy.init_node("lidar_node")
rospy.Subscriber("/scan", LaserScan, lidar_callback)
rospy.spin()
```

---
## **6. Assembly & Testing**
### **Step 1: Assemble the Chassis**
- Mount wheels and attach motors.
- Secure LiDAR and touchscreen.

### **Step 2: Wire the Electronics**
- Connect Raspberry Pi, sensors, and motor driver.
- Ensure proper power supply.

### **Step 3: Install Software & Calibrate Sensors**
- Flash Raspberry Pi OS and install dependencies.
- Run AI assistant and navigation code.

### **Step 4: Testing & Optimization**
- Validate motor movement and obstacle detection.
- Test AI voice responses.
- Optimize battery efficiency.

---
## **7. Submission Guidelines**
- **PDF Report** with project details, wiring diagrams, and code.
- **Video Demonstration** showcasing the robot in action.
- **Submit to Open Droids Telegram Group.**

---
## **8. Conclusion**
This AI-powered mobile robot is designed to be cost-effective and multifunctional. With AI integration, it enhances **user interaction, smart navigation, and automation**.

### **Next Steps:**
- Final testing and troubleshooting.
- Refining AI models for improved performance.
- Expanding functionalities (e.g., facial recognition, gesture control).

---
## **9. Additional Resources**
- **ROS Documentation:** [http://wiki.ros.org/](http://wiki.ros.org/)
- **OpenAI API Docs:** [https://beta.openai.com/docs/](https://beta.openai.com/docs/)
- **Raspberry Pi Guide:** [https://www.raspberrypi.org/documentation/](https://www.raspberrypi.org/documentation/)

---
## **10. Need Further Assistance?**
If you have questions or need modifications, feel free to ask!

