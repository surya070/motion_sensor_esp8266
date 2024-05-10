#define BLYNK_PRINT Serial
#include <ESP8266WiFi.h>
#include <BlynkSimpleEsp8266.h>

// You should get Auth Token in the Blynk App.
char auth[] = "YourAuthToken";

// Your WiFi credentials.
char ssid[] = "iphone";
char pass[] = "1234567890";

// Define the GPIO pin that is connected to the PIR sensor
#define PIR_PIN D2

BLYNK_WRITE(V1) {
  int pinData = param.asInt();
  if (pinData == 1) {
    Blynk.notify("Motion detected!");
  }
}

void setup() {
  // Debug console
  Serial.begin(9600);

  Blynk.begin(auth, ssid, pass);
  // You can also specify server:
  //Blynk.begin(auth, ssid, pass, "blynk-cloud.com", 80);
  //Blynk.begin(auth, ssid, pass, IPAddress(192,168,1,100), 8080);

  // Configure the PIR_PIN as an input
  pinMode(PIR_PIN, INPUT);
}

void loop() {
  Blynk.run();
  // Read the state of the PIR sensor
  int pirState = digitalRead(PIR_PIN);

  // If the PIR sensor detects motion
  if (pirState == HIGH) {
    Serial.println("Motion detected!");
    Blynk.virtualWrite(V1, 1);
  } else {
    Serial.println("No motion detected.");
    Blynk.virtualWrite(V1, 0);
  }

  // Wait for a second before the next reading
  delay(1000);
}
