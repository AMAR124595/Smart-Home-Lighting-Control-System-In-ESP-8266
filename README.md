# Smart-Home-Lighting-Control-System-In-ESP-8266
This project features a Smart Home Lighting Control System built using the ESP8266 microcontroller. The system integrates an LDR (Light Dependent Resistor) for ambient light detection and an LED for lighting control.
# Aim
To interface an LDR (Light Dependent Resistor) with an ESP8266 and create a system with both Automatic and Manual modes,
# Components
* ESP 8266
* LDR
# Connetion
![ldr-nodemcu](https://github.com/user-attachments/assets/aa6d1fe1-2aff-4dda-9e5f-896755c845ca)
* A0 ----> S
* VCC ----> VCC
* GND ----> GND
# Procedure
1. Open visual studio code Create New Project,with  a Framework of " Arduino"
   * We can also  Interface ESP8266 microcontroller to Arduino IDE
   * In the Arduino IDE, you typically do not need to explicitly include #include <Arduino.h> 
2. Interface LDR sensor  With VScode And Print  data on the serial Moniter For Analysing The Nature
3. Modify the program to get desired outputs on serial monitor
# Code
```
#include <Arduino.h>

int aut();
int man();
void setup() 
{
   Serial.begin(9600);
  pinMode(D4,OUTPUT);
  Serial.println("SMART HOME");
  Serial.println(" a) Auto Mode      b) Manual Mode      c) exit");
}
void loop()
{
  char x;
   if(Serial.available())
   {
    x=Serial.read();
    if(x=='a')
    {
      aut();
      Serial.println("SMART HOME");
      Serial.println(" a) Auto Mode      b) Manual Mode      c) exit");
    }
     else if(x=='b')
    {
      man();
      Serial.println("SMART HOME");
      Serial.println(" a) Auto Mode      b) Manual Mode      c) exit");
    }
   }
}
int aut()
{
  Serial.println("AUTO MODE");
  while(1)
  {
      
            if(analogRead(A0)<400)
              {
                  Serial.println("DAY LIGHT OFF");
                  digitalWrite(D4,HIGH);
                  delay(100);
                  while(analogRead(A0)<400)
                    {
                      
                      char x;
                        if(Serial.available())
                          {
                            x=Serial.read();
                            if(x=='c')
                            {
                              return 0;
                            }
                          }
                          delay(10);
                    }
            }
              else if(analogRead(A0)>400)
            {
                Serial.println("DAY NIGHT ON");
                digitalWrite(D4,LOW);
                delay(100);
                while(analogRead(A0)>400)
                  {
                    
                    char x;
                      if(Serial.available())
                        {
                          x=Serial.read();
                          if(x=='c')
                          {
                            return 0;
                          }
                        }
                        delay(10);
                  }
          }
        
   }
}
int man()
{
  Serial.println("MANUAL MODE");
  Serial.println(" a) ON      b) 0FF      c) exit");
  while(1)
  {
    
    char x;
    if(Serial.available())
      {
        x=Serial.read();
        if(x=='a')
        {
          Serial.println("LED ON ");
          digitalWrite(D4,LOW);
        }
        else if(x=='b')
        {
          Serial.println("LED OFF ");
          digitalWrite(D4,HIGH);
        }
        else if(x=='c')
        {
          return 0;
        }
      }
  }
}
```
# Output
![VideoCapture_20240829-115914](https://github.com/user-attachments/assets/b8ac18d1-fd2d-4355-8290-0880aeccf6eb)
![VideoCapture_20240829-115950](https://github.com/user-attachments/assets/32cf42ef-67e3-4d7d-bbfd-be288f8c8d02)
![VideoCapture_20240829-115939](https://github.com/user-attachments/assets/16183cdc-8de5-46e1-94c9-bc8ceee0a73a)

# Linkedin



