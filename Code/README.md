**Code for ESP 32 Test: ** void setup() { Serial.begin(115200); delay(1000);

Serial.println("================================"); Serial.println(" REFLEXTT ESP32 TEST "); Serial.println("================================"); }

void loop() { Serial.println("ESP32 is working!"); delay(1000); }

This code basically checks if the ESP32 is working by checking if theres a signal by printing the text on the serial monitor if it doesnt print its not working.

Code To test if Servo is functional (Worked)(With ESP32): #include <ESP32Servo.h>

Servo feederServo;

void setup() { Serial.begin(115200);

feederServo.attach(18);

Serial.println("ReflexTT Servo Test Started"); }

void loop() { feederServo.write(0); Serial.println("Position: 0 degrees"); delay(1000);

feederServo.write(90); Serial.println("Position: 90 degrees"); delay(1000);

feederServo.write(180); Serial.println("Position: 180 degrees"); delay(1000); }

This code basically turns the servo motor blade by 90 degrees every 1 second.

Code for test to see if OLED display is functional: #include <SPI.h> #include <Adafruit_GFX.h> #include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128 #define SCREEN_HEIGHT 64

#define OLED_SCK 14 #define OLED_MOSI 13 #define OLED_DC 16 #define OLED_RESET 17 #define OLED_CS 5

Adafruit_SSD1306 display( SCREEN_WIDTH, SCREEN_HEIGHT, &SPI, OLED_DC, OLED_RESET, OLED_CS );

void setup() { Serial.begin(115200);

SPI.begin(OLED_SCK, -1, OLED_MOSI, OLED_CS);

if (!display.begin(SSD1306_SWITCHCAPVCC)) { Serial.println("OLED not found!"); while (true); }

display.clearDisplay();

display.setTextSize(1); display.setTextColor(SSD1306_WHITE);

display.setCursor(0, 5); display.println("REFLEXTT");

display.setCursor(0, 25); display.println("OLED TEST");

display.setCursor(0, 45); display.println("Display Working!");

display.display();

Serial.println("OLED test successful!"); }

void loop() { }

This code basically checks if the OLED display is working by printing text on the screen through the help of the ESP32.

**Code to test if the arcade buttons are funtional:**const int buttonPin = 23;

void setup() { Serial.begin(115200); pinMode(buttonPin, INPUT_PULLUP); }

void loop() { if (digitalRead(buttonPin) == LOW) { Serial.println("BUTTON PRESSED!"); delay(200); } }

This code basically detects a signal whenever the button is pressed and sends the text to the serial monitor.
