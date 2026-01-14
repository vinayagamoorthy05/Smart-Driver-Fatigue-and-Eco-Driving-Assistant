# Smart-Driver-Fatigue-and-Eco-Driving-Assistant
Smart-Driver-Fatigue-and-Eco-Driving-Assistant

🧠 Project Description

This project demonstrates a simple automotive embedded safety and eco-driving assistant, inspired by ADAS (Advanced Driver Assistance Systems).

The system monitors driver steering behavior and aggressive driving events to:

Detect potential driver fatigue

Identify aggressive acceleration

Encourage eco-friendly driving behavior

The project is simulated using Wokwi and implemented with embedded C / Arduino logic, representing real-world STM32 automotive ECU behavior.

🎯 Key Features

🚨 Driver fatigue detection based on steering inactivity

🚀 Aggressive driving detection using acceleration input

🌱 Eco-driving indication for smooth driving

🔊 Real-time driver alerts using buzzer

💡 Visual feedback using dashboard LEDs

🔧 Hardware / Simulation Components

Microcontroller (Arduino / STM32 logic)

Potentiometer (Steering angle sensor simulation)

Push Button (Acceleration / brake event)

Buzzer (Driver alert)

Green LED (Eco mode indicator)

Red LED (Warning indicator)

⚙️ Working Principle

Continuous steering input is monitored using ADC

Long periods without steering change indicate possible driver fatigue

Frequent acceleration events indicate aggressive driving

System provides real-time alerts and feedback to the driver

🛠️ Tools & Technologies

Embedded C / Arduino

Wokwi Simulator

Automotive Embedded Concepts

GPIO, ADC, Timers

🚀 Future Enhancements

CAN Bus integration

Real steering angle sensor

Speed and RPM calculation
code
#define POT A0
#define BUTTON 2
#define GREEN_LED 8
#define RED_LED 9
#define BUZZER 10

void setup() {
  pinMode(BUTTON, INPUT_PULLUP);
  pinMode(GREEN_LED, OUTPUT);
  pinMode(RED_LED, OUTPUT);
  pinMode(BUZZER, OUTPUT);

  Serial.begin(9600);
}

void loop() {
  int steering = analogRead(POT);
  int buttonState = digitalRead(BUTTON);

  Serial.print("Steering: ");
  Serial.print(steering);
  Serial.print(" Button: ");
  Serial.println(buttonState);

  // Steering moved → ECO MODE
  if (steering > 600) {
    digitalWrite(GREEN_LED, HIGH);
    digitalWrite(RED_LED, LOW);
    noTone(BUZZER);
  }
  // Button pressed → Warning
  else if (buttonState == LOW) {
    digitalWrite(RED_LED, HIGH);
    digitalWrite(GREEN_LED, LOW);
    tone(BUZZER, 1000);
  }
  else {
    digitalWrite(GREEN_LED, LOW);
    digitalWrite(RED_LED, LOW);
    noTone(BUZZER);
  }

  delay(200);
}


AI-based fatigue detection

EV energy optimization logic
