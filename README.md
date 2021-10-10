# Smart-Dustbin
//Smart dustbin using arduino
 #include<Servo.h>
 Servo servoMain;
 const int trigPin=9;
const int echoPin=10;
long duration;
int distance;
void setup() {
  // put your setup code here, to run once:
  servoMain.attach(7);
   pinMode(trigPin,OUTPUT);
   pinMode(echoPin,INPUT);
   
   Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
   digitalWrite(trigPin,LOW);
   delayMicroseconds(2);

   digitalWrite(trigPin,HIGH);
   delayMicroseconds(10);
   digitalWrite(trigPin,LOW);

   duration=pulseIn(echoPin,HIGH);

   distance=duration*0.034/2;

   Serial.print("Distance: ");
   Serial.print(distance);
   delay(10);
   
   if((distance<=50))
   {
    servoMain.write(180);
    delay(1000);
    
   }
   else if(distance>10);
   {
    servoMain.write(0);
    delay(50);
   }
}
