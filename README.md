
#define trigPin 9
#define echoPin 10
#define buzzerPin 8
#define ledPin 7

void setup() {
  Serial.begin(9600);
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(buzzerPin, OUTPUT);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  long duration, distance;
  
  // Clear the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  
  // Set the trigPin HIGH for 10 microseconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  // Read the echoPin
  duration = pulseIn(echoPin, HIGH);
  
  // Calculate the distance
  distance = (duration * 0.034) / 2; // Distance in cm
  
  // Print the distance to the Serial Monitor
  Serial.print("Distance: ");
  Serial.println(distance);
  
  // Check if the distance is less than 10 cm
  if (distance < 10) {
    digitalWrite(buzzerPin, HIGH); // Turn on buzzer
    digitalWrite(ledPin, HIGH);     // Turn on LED
  } else {
    digitalWrite(buzzerPin, LOW);  // Turn off buzzer
    digitalWrite(ledPin, LOW);      // Turn off LED
  }
  
  delay(500); // Wait for half a second before the next reading
}

//Step 1: Set Up the Circuit
//Open Tinkercad: Go to the Tinkercad website and create a new circuit.

//Add Components: Drag and drop the following components onto the workspace:

Arduino Uno
HC-SR04 Ultrasonic Sensor
Buzzer
LED
Resistor (220 ohm)
Breadboard (optional for organization)
Connect the HC-SR04:

VCC pin to the 5V pin on the Arduino.
GND pin to the GND pin on the Arduino.
Trig pin to a digital pin on the Arduino (e.g., pin 9).
Echo pin to another digital pin on the Arduino (e.g., pin 10).
Connect the Buzzer:

Connect one terminal of the buzzer to a digital pin on the Arduino (e.g., pin 8).
Connect the other terminal of the buzzer to the GND.
Connect the LED (optional):

Connect the anode (long leg) of the LED to a digital pin on the Arduino (e.g., pin 7).
Connect the cathode (short leg) of the LED to one terminal of the resistor.
Connect the other terminal of the resistor to GND.
Step 2: Write the Arduino Code
Open the Code Editor: Click on the "Code" button in Tinkercad.
Select "Blocks" or "Text": You can choose to write in blocks or text. For this project, we will use text.

 Simulate the Circuit
Start Simulation: Click on the "Start Simulation" button in Tinkercad.
Observe the Output: Open the Serial Monitor to see the distance readings. Move an object closer to the sensor to test the buzzer and LED alerts.

<img width="927" height="676" alt="ckt (2)" src="https://github.com/user-attachments/assets/ff9af1d0-268f-4fca-81b5-7a4138c8773e" />
<img width="1909" height="962" alt="ckt (1)" src="https://github.com/user-attachments/assets/87eb69c2-7dc9-4afb-b851-c152175c5daa" />

https://www.tinkercad.com/things/9PepHK1pHbQ-cool-stantia-rottis
https://github.com/user-attachments/assets/ba5528d4-d9a6-457a-9b35-a82278cfb425


    # Obstacle Detection System (Arduino + HC-SR04)
    
    Detects obstacles using the HC-SR04 ultrasonic sensor and triggers **buzzer + LED** alerts when an object is closer than **10 cm**. 
    The code averages multiple readings to stabilize the distance estimate.
    
    ## ✨ Features
    - Real-time distance measurement
    - Alerts for objects **< 10 cm**
    - Simple averaging for stable readings
    - Serial monitor logs for debugging
    
    ## 🧰 Hardware
    - Arduino Uno (or compatible)
    - HC-SR04 ultrasonic sensor
    - Buzzer
    - LED + resistor (220 Ω recommended)
    - Jumper wires + breadboard
