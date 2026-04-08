# Question-3---Build-a-reaction-time-tester
This project demonstrates how to measure the time interval between events using Arduino and pushbutton. When the pushbutton is pressed, the system calculates and dsiplays the time elapsed since the last press, using the millis() function.

-> Objective :
1. To use pushbutton as input.
2.  To measure time intervals using millis() function.
3.  To display time elapsed on Serial monitor.
4.  To understand non-blocking timing techniques.

-> Tinkercad simulation link : https://www.tinkercad.com/things/biGFhAl3W37-reaction-time-tester/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard&sharecode=XFw4tp0L0KI47RNUVXl2iOoMRZkxxdpVu3oUENtU33Y

-> Components used : 
Arduino uno
Pushbutton
LED
Resistor(220 Ohm for LED)
Resistor(10K Ohm for pushbutton)
Breadboard
Jumperwires

-> Circuit connection :
Pushbutton : 
  One terminal to Digital pin 8
  Other terminal to GND
LED :
  Positive terminal to pin 10
  Negative terminal to GND

-> Working principle : 
The pushbutton is configured using INPUT_PULLUP() function which keeps the input HIGH by default.
When the button is pressed, the input becomes LOW.
The program records the current time using millis() function when the button is pressed and calculates the difference from the previous recorded time.
The time is calculated using millis() function by finding the difference between the current time and the previously recorded time.
This gives the elapsed time between button presses.
The result is displayed on the Serial monitor, and the timer is reset for the next measurement.

-> Code : [Build_a_reaction_time_tester.c](https://github.com/user-attachments/files/26574668/Build_a_reaction_time_tester.c)

//Build a reaction time tester
// C
// Defining pins
int buttonPin = 8;
int ledPin = 10;
unsigned long startTime;
unsigned long reactionTime; 

void setup(){
  pinMode(buttonPin, INPUT_PULLUP);
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
  
  /*Serial.begin function is used to start communication between
  Arduino and the computer*/
  /*9600 is standard speed for communication*/
}

void loop(){

  /*Random delay before the LED turns ON*/
  int waitTime = random(2000, 5000); // 2 to 5 seconds
  delay(waitTime);
  
  //Turn ON LED
  digitalWrite(ledPin, HIGH);
  startTime = millis();
  
  while(digitalRead(buttonPin) == HIGH);
    //Calculating reaction time
    reactionTime = millis() - startTime;
    
    //turn OFF LED
    digitalWrite(ledPin, LOW);
    
    //Printing elapsed time
    Serial.print("Reaction time : ");
    Serial.print(reactionTime);
    Serial.println(" ms"); // prints in new line
    
    delay(2000);
  }

