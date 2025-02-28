# soil_moisture
#define MOISTURE_SENSOR A0  // Analog pin for soil moisture sensor
#define MOTOR_PIN 9  
#define MOTOR_PIN1 8        // Digital pin for motor relay or motor driver

// Set threshold for dry soil
 // Adjust based on your sensor readings

void setup(){
    pinMode(MOISTURE_SENSOR, INPUT);
    pinMode(MOTOR_PIN, OUTPUT);
    pinMode(MOTOR_PIN1, OUTPUT);
    Serial.begin(9600);
}

void loop() {
    const int moistureThreshold = 400;
    int moistureValue = analogRead(MOISTURE_SENSOR);
    Serial.print("Soil Moisture Level: ");
    Serial.println(moistureValue);
    
    if (moistureValue > moistureThreshold) {
        digitalWrite(MOTOR_PIN, HIGH); // Turn on motor
        digitalWrite(MOTOR_PIN1, HIGH); 
        delay(5000);
        Serial.println("Motor ON: Watering the plant");
    } else {
        digitalWrite(MOTOR_PIN, LOW); // Turn off motor
        digitalWrite(MOTOR_PIN1, LOW);
        Serial.println("Motor OFF: Soil moisture is sufficient");
    }
    
    delay(2000); // Wait 2 seconds before next reading
}
#include <Servo.h>
Servo myservo; 

// Define pins
#define MOISTURE_SENSOR A0  // Analog pin for soil moisture sensor
      // Digital pin for motor relay or motor driver

// Set threshold for dry soil
 // Adjust based on your sensor readings

void setup(){
    pinMode(MOISTURE_SENSOR, INPUT);
    Serial.begin(9600);
    myservo.attach(9);     
}

void loop() {
   myservo.write(90);   
    const int moistureThreshold = 500;
    int moistureValue = analogRead(MOISTURE_SENSOR);
    Serial.print("Soil Moisture Level: ");
    Serial.println(moistureValue);
    
    if (moistureValue < moistureThreshold) {
         myservo.write(0);    // Turn on motor
        Serial.println("Motor ON: Watering the plant");
    } else {
// Turn off motor
        Serial.println("Motor OFF: Soil moisture is sufficient");
    }
    
    delay(2000); // Wait 2 seconds before next reading
}
