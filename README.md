# P4
const int trigPin = 9;   // Trig pin connected to digital pin 9 
const int echoPin = 10;  // Echo pin connected to digital pin 10 
long duration;          
float distanceCm;       
 // Variable to store pulse duration 
 // Variable to store calculated distance
 void setup() { 
pinMode(trigPin, OUTPUT);  // Set Trig as output 
pinMode(echoPin, INPUT);   // Set Echo as input 
Serial.begin(9600);        
}
void loop() { 
// Start Serial communication 
// Send a 10µs HIGH pulse to trigger the ultrasonic burst 
digitalWrite(trigPin, LOW); 
delayMicroseconds(2); 
digitalWrite(trigPin, HIGH); 
delayMicroseconds(10); 
digitalWrite(trigPin, LOW);
// Measure the time for echo to return 
duration = pulseIn(echoPin, HIGH);  // Time in microseconds 
// Calculate distance using speed of sound 
distanceCm = (duration * 0.0343) / 2;  // Divide by 2 for round-trip 
// Display the distance 
Serial.print("Distance: ");
Serial.print(distanceCm); 
Serial.println(" cm"); 
delay(500);  // Wait half a second before next reading 
}
