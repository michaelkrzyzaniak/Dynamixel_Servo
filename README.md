# Dynamixel_Servo
Arduino library for Dynamixel Servos

HTML Documentation is here:
http://michaelkrzyzaniak.github.io/Dynamixel_Servo/

A simple program to move a servo back and forth would look like this:

```C
#include <Dynamixel_Servo.h>

#define HALF_DUPLEX_DIRECTION_PIN 4

/*--------------------------------------------------------------------*/
void setup(void)
{
  servo_init(&Serial, HALF_DUPLEX_DIRECTION_PIN, SERVO_DEFAULT_BAUD);
}

/*--------------------------------------------------------------------*/
void loop(void)
{
  int timeout = 50; //milliseconds
  servo_error_t error;
  
  /* using high-level interface */
  /* Set a brand new servo (with factory default ID) to the 0 degree position */
  error = servo_set(SERVO_DEFAULT_ID, SERVO_REGISTER_GOAL_ANGLE, 0, timeout);
  //if(error) handle_error();
  delay(2000);
  
  /* Set a brand new servo (with factory default ID) to the 0 degree position */
  /* wait two seconds and move it to the 2 pi radians position */
  error = servo_set(SERVO_DEFAULT_ID, SERVO_REGISTER_GOAL_ANGLE, 6.283, timeout);
  //if(error) handle_error();
  delay(2000);
}
```
