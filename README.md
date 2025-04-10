We are going to create a smart parking system with an Automatic Number Plate Recognition (ANPR) system using the affordable ESP32-CAM. With its built-in camera, it is possible to capture images and perform number plate recognition. Additionally, we will manage barrier opening and closing, as well as vehicle entry and exit detection, using IR sensors and more. Without any further delay, let's dive into the project.



Overview of Smart Parking System
This project features a fully automated number plate detection system with barrier control. There are two IR sensors: one at the entry and one at the exit. When a car approaches the entry sensor, the camera on the ESP32-CAM captures the car's number plate and sends it to our dedicated Number Plate Detection API, receiving a response within seconds. The result is gets logged, and the barrier opens to allow the vehicle inside. Similarly, when a vehicle approaches the exit, the barrier opens, allowing the vehicle to leave, and the data gets logged. This is what we’ve planned for this project. It serves as an introductory example of our latest API, which has many more possibilities that I leave to you to explore.

Components Required to Build Smart Parking System
The most important component here is the ESP32-CAM, which was chosen for being an affordable microcontroller development board with essential features like a camera and Wi-Fi. If any other microcontrollers fit these criteria, you can select them as well. The rest of the components are based on our own concept. As always, you're not limited to the list provided below; feel free to customize it as needed.

Below is the list of components that are required,

ESP32 CAM x1 

Servo Motor x1

IR Sensor Module x2

Any USB to UART Converter x1

Breadboard x1

Jumper Wires (Required Quantity)

To mount the ESP32-CAM and add aesthetics to the project, I’ve used 3D printing and 2D laser cutting. However, these are not necessary in your case, as there are many alternatives to fulfill these tasks.

Circuit Diagram for the Smart Parking Management System
Finally, we come to the actual hardware connection. The circuit diagram is quite simple and self-explanatory. The main connections will be between the ESP32-CAM, servo motor, and IR sensors, with the rest dedicated to the power supply circuit. One important thing to remember is that the servo motor is powered by 5V, and the IR sensors are powered by the 3.3V output from the ESP32-CAM. This ensures that the digital output from the IR sensors won't exceed the 3.3V limit of the ESP32-CAM's GPIOs. I'm going to provide a 5V power supply using an old USB wire I found lying around, but you can use any 5V source available.

AI Based Smart Parking System Circuit Diagram​

Above, you can see the circuit diagram of the smart parking system we are going to build. Let me explain the circuit connections in detail for clarity. 

We are utilizing three GPIOs of the ESP32-CAM, one for the servomotor and two for the IR sensors. GPIO 14, configured as PWM output, controls the shaft position of the servo motor. GPIO 15 and GPIO 13, configured as digital inputs, are connected to the two IR sensors, representing the entry and exit points.

Regarding the power supply, we need an input voltage of 5V for the overall circuit. Inside the circuit, we need 3.3V for the IR sensors and the ESP32 module within the ESP32-CAM module, which can be drawn from the built-in voltage regulator of the ESP32-CAM module.

That's it—connection complete!

I'm not going to repeat the programming process for the ESP32-CAM development module, as we already have a dedicated article explaining the concept. For beginners, I recommend checking out the article - How to Program the ESP32-CAM? to see the circuit diagram between the USB-to-UART converter module and ESP32-CAM and to learn about the programming modes of the ESP32-CAM and more.

Hardware Assembled Image of Smart Parking System​

Above, you can see the assembled hardware image of the Smart Parking System. I used 3D printing to hold the ESP32-CAM and performed laser cutting to enhance the project's aesthetics. These are additional steps that aren't required for the project. If you're interested in accessing all the source files, they have been attached to the GitHub repository, which you can find at the bottom of this document.

Disclaimer

Something you should know about miniature photography using the ESP32-CAM is that it isn't designed for capturing photos of miniature or close-up objects due to the factory-set focal length of the lens. If you wish to take macro or miniature photos, you'll need to manually adjust the lens's focal length. For reference, there's a GIF video below showing how this adjustment can be done using a couple of pliers. If you're not comfortable taking the risk, you can also purchase extra overlay lenses that can achieve the same result.



ESP32-CAM Code for Smart Parking System
Now comes the final part of the project- coding. However, before diving into the code, there are prerequisites such as generating the API Key and installing additional libraries.

Generating API KEY

You need to generate an API Key for accessing the number plate recognition API. Please refer to the section on "Generating API Key" to learn more about this process.

Once you've obtained the API Key, we can proceed with the coding phase, starting with installing the required libraries.

Installing Additional Libraries

We need to install two libraries to proceed with the code,

ESP32Servo by Kevin Harrington, John K. Bennett.

NTPClient by Fabrice Weinberg

You can install these libraries directly via the provided GitHub link or by searching for them in the Arduino IDE library manager.

ESP32 Code Explnation

To learn more about the Number Plate Recognition API, its working demonstration, and the detailed code explanation, you are welcome to explore another article dedicated to this topic License Plate Recognition using ESP32-CAM. This is because I will be skipping the most repetitive parts of the code in this explanation.

Including Required Libraries

Initially, the necessary libraries are included in the code. Don't worry about the number of libraries listed in the image—most of them are built-in and will be automatically located when you select the AI Tinker ESP32-CAM Board in the board manager.
