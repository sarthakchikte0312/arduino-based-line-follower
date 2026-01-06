#define IR_SENSOR_RIGHT 11
#define IR_SENSOR_LEFT 12
#define MOTOR_SPEED 180

// Right motor
int enableRightMotor = 6;
int rightMotorPin1 = 7;
int rightMotorPin2 = 8;

// Left motor
int enableLeftMotor = 5;
int leftMotorPin1 = 9;
int leftMotorPin2 = 10;

void setup()
{
  // Increase PWM frequency for smoother motor control
  TCCR0B = TCCR0B & B11111000 | B00000010;

  pinMode(enableRightMotor, OUTPUT);
  pinMode(rightMotorPin1, OUTPUT);
  pinMode(rightMotorPin2, OUTPUT);

  pinMode(enableLeftMotor, OUTPUT);
  pinMode(leftMotorPin1, OUTPUT);
  pinMode(leftMotorPin2, OUTPUT);

  pinMode(IR_SENSOR_RIGHT, INPUT);
  pinMode(IR_SENSOR_LEFT, INPUT);

  rotateMotor(0, 0);
}

void loop()
{
  int rightIR = digitalRead(IR_SENSOR_RIGHT);
  int leftIR = digitalRead(IR_SENSOR_LEFT);

  if (rightIR == LOW && leftIR == LOW)
    rotateMotor(MOTOR_SPEED, MOTOR_SPEED);

  else if (rightIR == HIGH && leftIR == LOW)
    rotateMotor(-MOTOR_SPEED, MOTOR_SPEED);

  else if (rightIR == LOW && leftIR == HIGH)
    rotateMotor(MOTOR_SPEED, -MOTOR_SPEED);

  else
    rotateMotor(0, 0);
}

void rotateMotor(int rightSpeed, int leftSpeed)
{
  // Right motor direction
  if (rightSpeed > 0) {
    digitalWrite(rightMotorPin1, HIGH);
    digitalWrite(rightMotorPin2, LOW);
  } else if (rightSpeed < 0) {
    digitalWrite(rightMotorPin1, LOW);
    digitalWrite(rightMotorPin2, HIGH);
  } else {
    digitalWrite(rightMotorPin1, LOW);
    digitalWrite(rightMotorPin2, LOW);
  }

  // Left motor direction
  if (leftSpeed > 0) {
    digitalWrite(leftMotorPin1, HIGH);
    digitalWrite(leftMotorPin2, LOW);
  } else if (leftSpeed < 0) {
    digitalWrite(leftMotorPin1, LOW);
    digitalWrite(leftMotorPin2, HIGH);
  } else {
    digitalWrite(leftMotorPin1, LOW);
    digitalWrite(leftMotorPin2, LOW);
  }

  analogWrite(enableRightMotor, abs(rightSpeed));
  analogWrite(enableLeftMotor, abs(leftSpeed));
}
