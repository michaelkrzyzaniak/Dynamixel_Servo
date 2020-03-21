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

  /* wait two seconds and move it to the 2 pi radians position */
  error = servo_set(SERVO_DEFAULT_ID, SERVO_REGISTER_GOAL_ANGLE, 6.283, timeout);
  //if(error) handle_error();
  delay(2000);
}
```

This library basically supports everything. You can burst read and write sequential servo registers for speed. You can control the torque and speed, or turn the servo LED on and off. You can broadcast messages to several servos. You can prepare several servos to move and then brodcast a trigger that causes them to all initiate movement at once, for perfect timing. If you prefer, you can work in physical units (like radians) and this library will convert it to the raw register values, and correctly handle multi-byte registers. On the other hand, if you prefer, you can individually access the raw vaules of the servo registers. Whatever you  want, you can do it. I believe in you!
