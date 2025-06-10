const int trigPin = 9;                 //sets trigPin as a constant integer to port 9
const int echoPin = 10;                //sets echoPin as a constant integer to port 10

const int trigPin2 = 5;                //sets trigPin and echoPin for the second sensor
const int echoPin2 = 6;

float duration, distance;              //declares the variables duration and distance
float duration2, distance2;      
  
float amplitude = 0;                   //declares amplitude

#include "analogWave.h"                //includes a set of commands
analogWave wave(DAC); 


void setup() {
  int frek = 300;                     //declares frek as an integer of 300
  pinMode(trigPin, OUTPUT);           //makes trigPin an output
  pinMode(echoPin, INPUT);            //makes echoPin an input
  
  pinMode(trigPin2, OUTPUT);
  pinMode(echoPin2, INPUT);
  
  wave.sine(frek);                    //makes a sine wave of 300(frek)

  Serial.begin(9600);
}

void loop() {

//measures distance for the first distance measurer
  digitalWrite(trigPin, LOW);         //makes the trigpin not send out a signal
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);        //makes the trigpin send out a signal
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  
  duration = pulseIn(echoPin, HIGH);  //detects when the bounced back signal from the trigPin arrives  
  distance = (duration*.0343)/2;      //calculates the distance and makes it the variable "distance"
  Serial.print("Distance: ");
  Serial.println(distance);           //prints the distance

//measures distance for the second distance measurer
  digitalWrite(trigPin2, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin2, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin2, LOW);

  duration2 = pulseIn(echoPin2, HIGH);
  distance2 = (duration2*.0343)/2;
  Serial.print("otherDistance: ");
  Serial.println(distance2);

//SOUND STUFF

  int freq = 10.9*distance+250.7;     //equation for frequency
  Serial.println("Frequency is now " + String(freq) + " hz");
  wave.freq(freq);                    //makes variable "freq" a wave
  
  if  (distance2<20) {                //turnes sound on if the players hand is present
    amplitude=1;
  } else {
    amplitude=0;
  }
  wave.amplitude(amplitude);
