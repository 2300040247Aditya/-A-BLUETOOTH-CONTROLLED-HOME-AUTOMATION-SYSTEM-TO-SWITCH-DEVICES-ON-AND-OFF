# -A-BLUETOOTH-CONTROLLED-HOME-AUTOMATION-SYSTEM-TO-SWITCH-DEVICES-ON-AND-OF/

char command;

#define DEVICE1 8   
#define DEVICE2 9   
void setup() {
  Serial.begin(9600);  
  pinMode(DEVICE1, OUTPUT);
  pinMode(DEVICE2, OUTPUT);

  digitalWrite(DEVICE1, LOW);
  digitalWrite(DEVICE2, LOW);

  Serial.println("System Ready. Awaiting Bluetooth Commands.");
}

void loop() {
  if (Serial.available()) {
    command = Serial.read();

    switch (command) {
      case 'A':  
        digitalWrite(DEVICE1, HIGH);
        Serial.println("Device 1 ON");
        break;

      case 'a':  
        digitalWrite(DEVICE1, LOW);
        Serial.println("Device 1 OFF");
        break;

      case 'B':  
        digitalWrite(DEVICE2, HIGH);
        Serial.println("Device 2 ON");
        break;

      case 'b':  
        digitalWrite(DEVICE2, LOW);
        Serial.println("Device 2 OFF");
        break;

      default:
        Serial.println("Invalid Command Received");
        break;
    }
  }
}

Send "A": Turns Device 1 ON

Send "a": Turns Device 1 OFF

Send "B": Turns Device 2 ON

Send "b": Turns Device 2 OFF

image![image](https://github.com/user-attachments/assets/5abb3f7d-504d-4e34-b7fa-eeb8735dcbe7)


