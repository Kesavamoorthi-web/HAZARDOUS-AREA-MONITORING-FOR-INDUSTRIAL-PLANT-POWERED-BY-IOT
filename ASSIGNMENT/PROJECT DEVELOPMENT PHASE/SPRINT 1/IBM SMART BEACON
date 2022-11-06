#include <dht.h>

#define dht_apin A0                                               // Analog Pin 0 is connected to DHT sensor
#define mqt_apin A1                                               // Analog Pin 1 is connected to MQT 135 sensor
dht DHT;
int sensorValue;
 
void setup(){
 
  Serial.begin(9600);                                             //Serial port to communicate with Python code
  Serial1.begin(9600);                                            //Serial port to communicate with Wearable device through Bluetooth (HC-05)
  delay(500);                                                     //Delay to let system boot 
}
 
void loop(){
 
    DHT.read11(dht_apin);                                         // read analog input pin 0(DHT11)
    sensorValue = analogRead(mqt_apin);                           // read analog input pin 1(MQ135)

    //Send Humidity status to Python Code
    Serial.print("Current humidity = ");
    Serial.print(DHT.humidity);
    Serial.print("%  ");

    //Send Temperature status to Python Code
    Serial.print("temperature = ");
    Serial.print(DHT.temperature); 
    Serial.println("C  ");

    //Send AirQuality sensor value to Python code
    Serial.print("AirQua=");
    Serial.print(sensorValue, DEC);                               
    Serial.println(" PPM");

    //Send signals to the Wearable
    Serial1.println("H T A");
    Serial1.println(DHT.humidity);
    Serial1.println(DHT.temperature);
    Serial1.println(sensorValue, DEC);
    
    delay(100);                                                  // wait 100 milliseconds for next reading 
}
