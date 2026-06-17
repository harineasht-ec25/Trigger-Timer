# NanoRelayTimer

Arduino Nano based relay timer that activates a relay for a predefined duration when a push button is pressed. The relay automatically turns OFF after the configured time, making it suitable for automation and control applications.

---

## 📌 Features

- Push-button triggered operation
- Adjustable relay ON duration through code
- Automatic relay OFF after timer expires
- Simple and low-cost hardware design
- Suitable for automation, industrial, and DIY projects

---

## 🛠 Hardware Requirements

- Arduino Nano
- 5V Relay Module
- Push Button
- 10kΩ Resistor (optional if using internal pull-up)
- Jumper Wires
- 5V Power Supply

---

## 🔌 Circuit Connections

### Push Button

| Arduino Nano | Push Button |
|-------------|-------------|
| D2 | One Terminal |
| GND | Other Terminal |

### Relay Module

| Arduino Nano | Relay Module |
|-------------|-------------|
| D8 | IN |
| 5V | VCC |
| GND | GND |

---

## ⚙️ Working Principle

1. The system continuously monitors the push button.
2. When the button is pressed, the relay turns ON.
3. The relay remains active for the programmed duration.
4. After the timer expires, the relay automatically turns OFF.
5. The system waits for the next button press.

---

## 📷 Project Images

### Circuit Diagram

![Circuit Diagram](Images/circuit_diagram.png)

### Hardware Prototype

![Prototype](Images/prototype.jpg)

---

## 🎥 Demonstration Video

[Watch Project Demo](Videos/demo.mp4)

---

## 📂 Project Structure

```text
NanoRelayTimer/
│
├── Arduino_Code/
│   └── NanoRelayTimer.ino
│
├── Images/
│   ├── circuit_diagram.png
│   ├── prototype.jpg
│   └── relay_working.png
│
├── Videos/
│   └── demo.mp4
│
├── README.md
├── LICENSE
└── .gitignore
```

---

## 💻 Arduino Code

```cpp
#define BUTTON_PIN 2
#define RELAY_PIN 8

const unsigned long relayTime = 5000;

bool relayActive = false;
unsigned long startTime = 0;

void setup() {
  pinMode(BUTTON_PIN, INPUT_PULLUP);
  pinMode(RELAY_PIN, OUTPUT);

  digitalWrite(RELAY_PIN, LOW);
}

void loop() {

  if (digitalRead(BUTTON_PIN) == LOW && !relayActive) {
    relayActive = true;
    startTime = millis();

    digitalWrite(RELAY_PIN, HIGH);
  }

  if (relayActive && millis() - startTime >= relayTime) {
    digitalWrite(RELAY_PIN, LOW);
    relayActive = false;
  }
}
```

---

## 🚀 Applications

- Water Pump Timer
- Industrial Automation
- Motor Control Systems
- Solenoid Valve Control
- Home Automation
- Timed Switching Applications

---

## 🔮 Future Enhancements

- OLED Display Countdown
- Adjustable Time Setting Buttons
- EEPROM Time Storage
- Multiple Relay Outputs
- Bluetooth Control
- Wi-Fi Monitoring with ESP32

---

## 👨‍💻 Author

Developed using Arduino Nano for reliable and cost-effective relay timing control applications.

---

## 📄 License

This project is released under the MIT License.
