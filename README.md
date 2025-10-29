# Relay


Here’s a clean, professional, and GitHub-ready rewrite of your **Arduino Relay Module Control** README section — formatted in Markdown with headings, emojis, and code snippets for better readability:

---

#  Arduino Relay Module Control

This project demonstrates how to interface a **two-channel relay module** with an **Arduino** to control **two LEDs**. The LEDs toggle on and off to visually represent how the relay operates — simulating the switching of electrical devices.

---

##  Author

**Designed by:** Prince Kushwaha
**Organization:** COSM Electronics

---

##  Components Required

| Component                | Quantity | Description                |
| ------------------------ | -------- | -------------------------- |
| Arduino Board (Uno/Nano) | 1        | Microcontroller board      |
| 2-Channel Relay Module   | 1        | For switching the two LEDs |
| LEDs (Red & Green)       | 2        | Indicate relay status      |
| Resistors (220Ω)         | 2        | Current limiting for LEDs  |
| Breadboard               | 1        | For prototyping            |
| Jumper Wires             | —        | For circuit connections    |

---

## 🔌 Wiring Diagram

### **Relay Module → Arduino**

| Relay Module Pin | Arduino Pin |
| ---------------- | ----------- |
| VCC              | 5V          |
| GND              | GND         |
| IN1              | D7          |
| IN2              | D8          |

---

### **Relay → LEDs**

####  Relay 1 (IN1 – Red LED)

| Connection | Description                       |
| ---------- | --------------------------------- |
| COM        | Cathode (short leg) of Red LED    |
| NO         | GND                               |
| Anode      | Connected to a 220Ω resistor → 5V |

####  Relay 2 (IN2 – Green LED)

| Connection | Description                       |
| ---------- | --------------------------------- |
| COM        | Cathode (short leg) of Green LED  |
| NO         | GND                               |
| Anode      | Connected to a 220Ω resistor → 5V |

---

## How It Works

1. **Initialization**
   In the `setup()` function, relay control pins are configured as **OUTPUT** and initialized to a **LOW** state (relays off).

2. **Loop Operation**
   The `loop()` function alternates the relay states:

   * Turns **Relay 1 ON** and **Relay 2 OFF**, waits for 1 second.
   * Turns **Relay 1 OFF** and **Relay 2 ON**, waits for 1 second.

3. **LED Indication**
   Each LED lights up when its respective relay is activated — providing a visual representation of relay switching.

---

## 🧠 Example Code

```cpp
// Pin definitions
const int RELAY1 = 7;
const int RELAY2 = 8;

void setup() {
  pinMode(RELAY1, OUTPUT);
  pinMode(RELAY2, OUTPUT);

  // Start with both relays OFF
  digitalWrite(RELAY1, LOW);
  digitalWrite(RELAY2, LOW);
}

void loop() {
  // Relay 1 ON, Relay 2 OFF
  digitalWrite(RELAY1, HIGH);
  digitalWrite(RELAY2, LOW);
  delay(1000);

  // Relay 1 OFF, Relay 2 ON
  digitalWrite(RELAY1, LOW);
  digitalWrite(RELAY2, HIGH);
  delay(1000);
}
```

---

## Safety Precautions

* **Low Voltage Only:** This example uses **5V LEDs**.
  If connecting to higher-voltage devices, use appropriate insulation and safety procedures.
* **Disconnect Power:** Always remove power before wiring or adjusting the circuit.
* **Avoid Overload:** Ensure connected devices do not exceed the relay’s rated current/voltage.

---

## Future Enhancements

* Control AC appliances (bulbs, fans) through relays.
* Integrate with sensors (e.g., temperature, light) for automated switching.
* Add Wi-Fi or Bluetooth control for remote operation.
