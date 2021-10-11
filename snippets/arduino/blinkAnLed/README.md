# Embedded Programming - Arduino

## Blink An Led

### Implemetation

```c++
/**
  * Neccessary Definitions
  */

// Serial Monitor
#define FREQUENCY 9600

// Serial | AVR | Digital
#define RX_PIN D0
#define TX_PIN D1

// AVR | Digital | Analog
#define ANALOG_PIN_1 A0
#define ANALOG_PIN_2 A0
#define ANALOG_PIN_3 A1
#define ANALOG_PIN_4 A2
#define ANALOG_PIN_5 A3
#define ANALOG_PIN_6 A4  // I2C -> SDA
#define ANALOG_PIN_7 A5  // I2C -> SCL

// AVR | Digital | PWM
#define PWM_PIN_1 D3  // Interapt -> Int1
#define PWM_PIN_2 D5
#define PWM_PIN_3 D6
#define PWM_PIN_4 D9

 // AVR | Digital
#define DIGITAL_PIN_1 D2  // Interept -> Int0
#define DIGITAL_PIN_2 D4
#define DIGITAL_PIN_3 D7
#define DIGITAL_PIN_4 D8
#define DIGITAL_PIN_5 D10  // SPI -> SS
#define DIGITAL_PIN_6 D11  // SPI -> MOSI
#define DIGITAL_PIN_7 D12  // SOI -> MISO
#define DIGITAL_PIN_8 D13  // SPI -> SCK, [Built-In L.E.D]
```

```c++
/**
 * Re-Usable Methods/Functions
 */
void BlinkAnLed(pin, onDelay, offDelay) {
  try {
     // Switched On
     digitalWrite(pin,HIGH)
     delay(onDelay)
     // Switched Off
     digitalWrite(pin,LOW)
     delay(offDelay)
  } catch (Exception err) {
    Serial.print("[BlinkAnLed-Error]: " + err.message)
  }
}
```

```c++
/**
 * Main Setup Method [Runs Once]
 */
void setup() {
  // Serial Configurations
  Serial.begin(FREQUENCY)

  // Pin Configurations
  pinMode(DIGITAL_PIN_8, OUTPUT);
}
```

```c++
/**
 * Main Loop Method [Keeps Running]
 */
void loop() {
  BlinkAnLed(DIGITAL_PIN_8, 1000, 500)
}
```