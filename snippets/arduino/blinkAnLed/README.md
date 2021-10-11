# Embedded Programming - Arduino

## Blink An Led

Main Project File: `sketch.ino`

### Schema

#### Pins

ANALOG PINS:  `A0` `A1` `A2` `A3` `A4` `A5`

DIGITAL PINS:  `D0` `D1` `D2` `D3` `D4` `D5` `D6` `D7` `D8` `D9` `D10` `D11` `D12` `D13` 

![alt text](https://lh3.googleusercontent.com/proxy/Do6pVqIv9LdvV7c0TNwt8fXhiPqzvu0TJcbLUL0D6vrnckoYDZlhKkM7VFDpconOCY3D_RqkFYofA6I99eKC86GBwB7NcOMrKtLDEiBkumkB7EM42R6eg8vdchFeLIACOd9AFCbKVekdGadmki2_UJRwbHAoaTTCMJSbVDU)

### Library Imports

```c++
...
```

### PIN Settings / Definitions & Global Constants

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

### Wrappers & Methods

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

### Setup Method

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

### Loop Method

```c++
/**
 * Main Loop Method [Keeps Running]
 */
void loop() {
  BlinkAnLed(DIGITAL_PIN_8, 1000, 500)
}
```