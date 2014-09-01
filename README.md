arduino
=======
#include <Stepper.h>

const int stepsPerRevolution = 200;  // change this to fit the number of steps per revolution
                                     // for your motor

// initialize the stepper library on pins 8 through 11:
Stepper myStepper(stepsPerRevolution, 8,9,10,11);            


int input;
void setup() {
  // set the speed at 60 rpm:
  myStepper.setSpeed(60);
  // initialize the serial port
  Serial.begin(9600);
  Serial.println(" 0 = +, 1 = -");
}

void loop() {
  while(Serial.parseInt() > 0){
    int steps = Serial.parseInt();
    if (steps > 5){
      input = steps;
      Serial.println(input);
    
    }
    if (steps == 0){
      myStepper.step(input);
      }
    if (steps == 1){
      myStepper.step(-input);
      }
  }
}
