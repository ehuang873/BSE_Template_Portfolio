# Sun Tracker Solar Powered Phone Charger
 This solar powered phone charger uses the Sun to power a battery and charge a phone. However, it can also track the movements of the Sun and will tilt towards the Sun like a sunflower. 

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Eric H | Lynbrook High School | Electrical Engineering | Incoming Sophomore

![Headstone Image](https://bluestampengineering.com/wp-content/uploads/2016/05/improve.jpg)
  
# Final Milestone
My final milestone is the increased reliability and accuracy of my robot. I ameliorated the sagging and fixed the reliability of the finger. As discussed in my second milestone, the arm sags because of weight. I put in a block of wood at the base to hold up the upper arm; this has reverberating positive effects throughout the arm. I also realized that the forearm was getting disconnected from the elbow servo’s horn because of the weight stress on the joint. Now, I make sure to constantly tighten the screws at that joint. 

[![Final Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612573869/video_to_markdown/images/youtube--F7M7imOVGug-c05b58ac6eb4c4700831b2b3070cd403.jpg )](https://www.youtube.com/watch?v=F7M7imOVGug&feature=emb_logo "Final Milestone"){:target="_blank" rel="noopener"}

# Second Milestone
My second milestone is completing the solar panel connected charger. I clipped off the connector of the solar panel wire and connected it to another head that could connect to my powerboost. The powerboost would take power from my solar panel and my lithium ion battery to output 5 volts of energy to properly charge a phone. 
[![Third Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612574014/video_to_markdown/images/youtube--y3VAmNlER5Y-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=y3VAmNlER5Y&feature=emb_logo "Second Milestone"){:target="_blank" rel="noopener"}

# First Milestone
My first milestone is hooking up the servo to the arduino. This is a large part of my project as it uses the gears to reposition the swivel of the solar panels to catch the most sunlight possible. I hooked it up to the arduino and made sure that it worked, writing a sample code to test out the motors. 
  

[![First Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1624630671/video_to_markdown/images/youtube--lRqF1uRTP9g-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=lRqF1uRTP9g ""))](){:target="_blank" rel="noopener"}
# Circuit Diagram
<img width="559" alt="Screen Shot 2021-07-23 at 7 00 51 AM" src="https://user-images.githubusercontent.com/86114139/126793076-ff06d035-94c0-4405-9c20-e6948db062e6.png">

# Code

#include <Servo.h>

Servo servo;   // Create a servo object to control the servo
int eLDRPin = A0; // Assign pins to the LDR's
int wLDRPin = A1;
int eastLDR = 0; //Create variables to store to LDR readings
int westLDR = 0;
int difference = 0; //Create a variable to compare the two LDR's
int error = 10;  // Variable for is there is a noticable difference between the tow LDR's
int servoSet = 80; //Variable for position of servo - will be different for each device


void setup() {
  servo.attach(9);   //attaches the servo object to PWM pin 9
  Serial.begin(9600); 
}

void loop() {
  eastLDR = analogRead(wLDRPin); //Read the LDR values
  westLDR = analogRead(eLDRPin);


  difference = eastLDR - westLDR ; //Check the difference 
  if (difference > 10) {          //Send the panel towards the LDR with a higher reading
    if (servoSet <= 140) {
      servoSet ++;
      servo.write(servoSet);
    }
  } else if (difference < -10) 
  {
    if (servoSet >= 15) {
      servoSet --;
      servo.write(servoSet);
    }
  }
  else
  {
    servo.write(80);
  }
  Serial.print(eastLDR);      //Serial monitor can be useful for debugging/setting up
  Serial.print("   -   ");    //Use it to see if your LDR's are noticeably different when
  Serial.print(westLDR);      //They have equal light shining on them, if so, correct with the error value
  Serial.print("   -   ");
  Serial.print(difference);   
  Serial.print("   -   ");
  Serial.print(servoSet);     //Fine tune the servo settings, to maximise swing available
  Serial.print("   -   ");
  Serial.println(".");
  delay(100);
}
