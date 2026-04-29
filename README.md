# mini-bots


XIAO C3 + TC1508A:

```c++
// Define Pins for TC1508A
const int IN1 = D3; 
const int IN2 = D2;

// PWM Properties
const int pwmFreq = 5000;
const int pwmResolution = 8; // 0-255
const int pwmLedChannelA = 0;
const int pwmLedChannelB = 1;

void setup() {
  // Configure PWM functionalities
  ledcSetup(pwmLedChannelA, pwmFreq, pwmResolution);
  ledcSetup(pwmLedChannelB, pwmFreq, pwmResolution);
  
  // Attach the channel to the GPIO to be controlled
  ledcAttachPin(IN1, pwmLedChannelA);
  ledcAttachPin(IN2, pwmLedChannelB);
}

void loop() {
  // Forward at full speed
  ledcWrite(pwmLedChannelA, 255);
  ledcWrite(pwmLedChannelB, 0);
  delay(2000);

  // Stop
  ledcWrite(pwmLedChannelA, 0);
  ledcWrite(pwmLedChannelB, 0);
  delay(1000);

  // Reverse at half speed
  ledcWrite(pwmLedChannelA, 0);
  ledcWrite(pwmLedChannelB, 127);
  delay(2000);
}
```
