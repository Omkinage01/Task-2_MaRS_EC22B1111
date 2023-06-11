# Task-2_MaRS_EC22B1111
Interrupt Driven Motor

Tinkercad Link: https://www.tinkercad.com/things/ajUQMzrPUYp


Code:

// Pin assignments
int clock_button = 2;
int anticlock_button = 3;
int motorPin_1 = 6;
int motorPin_2 = 7;

void setup()
{
  // Set pin modes
  pinMode(clock_button, INPUT);
  pinMode(anticlock_button, INPUT);
  pinMode(motorPin_1, OUTPUT);
  pinMode(motorPin_2, OUTPUT);

  // Initialize motor pins to LOW
  digitalWrite(motorPin_1, LOW);
  digitalWrite(motorPin_2, LOW);

  // Attach interrupt handlers to buttons
  attachInterrupt(digitalPinToInterrupt(clock_button), clockwise, RISING);
  attachInterrupt(digitalPinToInterrupt(anticlock_button), anti_clockwise, RISING);

  // Initialize Serial communication
  Serial.begin(9600);
}

void loop()
{
  // Empty loop as no continuous actions required
}

// Interrupt handler for anti-clockwise button
void anti_clockwise()
{
  Serial.println("Anti Clockwise");
  digitalWrite(motorPin_1, LOW);
  int input;
  input = digitalRead(motorPin_2);

  if (input == HIGH)
    digitalWrite(motorPin_2, LOW);
  else
    digitalWrite(motorPin_2, HIGH);
}

// Interrupt handler for clockwise button
void clockwise()
{
  Serial.println("Clockwise");
  digitalWrite(motorPin_2, LOW);
  int input;
  input = digitalRead(motorPin_1);

  if (input == HIGH)
    digitalWrite(motorPin_1, LOW);
  else
    digitalWrite(motorPin_1, HIGH);
}
