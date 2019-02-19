# Instruction
1. Download and Install Arduino IDE https://www.arduino.cc/en/main/software
2. Download the above Prosthetic_Simulation.rar file and extract it.
3. Open Arduino_calibration_code.ino in Arduino_Code folder and upload the code to Arduino and find the calibration threshold value.
4. Open Arduino_main_code.ino  in Arduino_Code folder and set the calibration threshold value in the respective integer value and upload the code to Arduino.
5. Now change the COM port of Arduino to COM5 through Device manager. 
6. Now remove the Arduino and insert it again to restart the arduino code (This step is to make sure that the Arduino is connected in the right COM port)
7. Now open the Hand_Sim_Final.exe in the folder and you can see the simulation once you contract your muscles.

# Arduino Code

#### Calibration Code [Arduino]
```
void setup() 
{
  Serial.begin(9600);
}
void loop() {
 
  int sensorValue = analogRead(A0);
  Serial.println(sensorValue);
  delay(1);        // delay in between reads for stability
}
```
#### Main Code [Arduino]
```
void setup() 
{
Serial.begin(9600);
}
const int threshold_value = 300;   //Set your threshold value
const int time_duration=2000;
unsigned long signal_time;
void loop()
{
if((analogRead(A0)>threshold_value)&& (millis()>signal_time))
{
signal_time=millis()+time_duration;
Serial.write(1);
Serial.flush();
}
}
```

