[README (3).md](https://github.com/user-attachments/files/32374289/README.3.md)
# Activity 02 – Push Button

## Objective
To understand digital input programming using Arduino by reading the state of a push button.

## Components Used
- Arduino UNO
- Push Button
- 220 Ω Resistor (pull-down)
- Breadboard
- Jumper Wires

## Circuit Diagram
![Circuit Diagram](circuit.png)

The push button is wired between 5V and digital pin 2 (green wire). A 220 Ω resistor connects pin 2 to GND (black wire), acting as a pull-down resistor so the pin reads a stable LOW when the button is not pressed.

## Arduino Program
The full sketch is available in [`code.ino`](./code.ino).

```cpp
const int buttonPin = 2;  
int buttonState = 0;       

void setup() {
  pinMode(buttonPin, INPUT);  
  Serial.begin(9600);          
}

void loop() {
  buttonState = digitalRead(buttonPin);  

  if (buttonState == HIGH) {
    Serial.println("Button Pressed");
  } else {
    Serial.println("Button Released");
  }

  delay(200);  
}
```

## Output
*(Insert a screenshot of the Serial Monitor showing "Button Pressed" / "Button Released" while running the simulation.)*

## Learning Outcome
- Understood digital input pins.
- Learned the use of `digitalRead()`.
- Understood the purpose of a pull-down resistor in preventing a floating input.
- Learned how to use `Serial.begin()` and `Serial.println()` to debug and monitor input values.
- Understood the difference between `INPUT` and `OUTPUT` pin modes.

## Challenges Faced
- Floating pin readings before adding the pull-down resistor.
- Incorrect wiring of the resistor initially caused the button state to always read HIGH.
- Needed to add a small delay to keep the Serial Monitor output readable.

## Real-World Applications
- User input controls in embedded devices (e.g., power buttons, mode switches).
- Doorbell or alert-trigger systems.
- Manual override switches in automated systems.

## Connection to Your PoC
The push button concept can be used in my Smart Irrigation System as a manual override switch — allowing the user to manually start or stop the water pump regardless of the automatic sensor readings.
