# arduino_soil_moisture_sensor

simple soil moisture sensor with led to indicate if the plant needs water or not
red: need watering
green: no need to water

schematic: 
![schmatic](https://github.com/user-attachments/assets/545ec8bf-e065-4d87-839b-3315ed90eb79)

photo of build: 
![photo](https://github.com/user-attachments/assets/cdd79c08-d02f-4c06-867b-d450c36c1e80)

code: 
```c
#define PIN_AO 0
#define LED_RED 8
#define LED_GREEN 7
#define MOIST_TARGET 800
void setup() {  
  pinMode(LED_RED, OUTPUT);
  pinMode(PIN_AO, INPUT); 
  Serial.begin(9600);  
}  
void loop() {
  Serial.print("AO=");  
  Serial.print(analogRead(PIN_AO));
  Serial.print("\n");
  delay(2000);  
  if(analogRead(PIN_AO) > MOIST_TARGET){
      Serial.print("water plant\n"); 
      digitalWrite(LED_RED, HIGH);
      digitalWrite(LED_GREEN, LOW);
  }
  else{
      digitalWrite(LED_RED, LOW);
      digitalWrite(LED_GREEN, HIGH);
  }
} 

// dry (in air): ao = 1023
// wet (submergued in water): ao < 300

```
reference: 
https://blog.csdn.net/ling3ye/article/details/51416786
