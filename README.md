# LCD-Smartie 
***
## zeigt informationen zb: 
- Uhrzeit / Datum
- Aktuellen Liedtitel, Dauer uvm. (Winamp)
- CPU Auslastung
- GPU Auslastung
- RAM Verbrauch
- Temperaturen (HWINFO)
- RSS Feeds
- Festplatten
- derzeitiger Upload und Download (Netzwerk)
- Gesammte Up/Downloadmenge (seit letzen neustart)
- PC uptime

des Computers auf einen kleinen LCD Bildschirm an

***
## kann mit den Tastern steuern:
- Anzuzeigende Seite
- Nächstes Lied / Letztes Lied
- Lautstärke
- Theoretisch kann man jedes script oder Anwedung starten

![Bild 1](https://github.com/ToWipf/LCD-Smartie/blob/master/Bild1.jpg)
![Bild 2](https://github.com/ToWipf/LCD-Smartie/blob/master/Bild2.jpg)

Programm dazu: http://lcdsmartie.sourceforge.net/

Erweitert um 11 Taster und viele kleine Fehlerbehebungen

***
## Hardware:
-   Arduino Nano
     - Pin 0,1 USB DATEN
     - Pin 2-12: Eingaenge // 10kOhm nach GND
     - Pin A0 : HintergrundLED - einstellbar
     - Pin A1 :
     - Pin A2 :
     - Pin A3 :
     - Pin A4 : SDA
     - Pin A5 : SCL
     - Pin A6 :
     - Pin A7 :

***
## Software:
   - LED Smartie 5.4
   - matrix.dll COM8,9600
   - Refresh intervall 50 ms
   - scroll intervall 600

***
## Optional:
   -  Bildschirmhelligkeit über 5kOhm Poti
   -  Externer reset Taster ohne Pulldownwiderstand

***
## Code: (mit Kommentaren [hier](https://github.com/ToWipf/LCD-Smartie/blob/master/smartie.ino))
```c++
#include <LiquidCrystal_I2C.h>
#define VERSION "V 5.2"
#define TASTERANZAHL 11
#define LED A0
#define PAUSE 50000
unsigned int warten = 0;
byte i = 0;
byte pin;
byte IN[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11};
byte incoming, rxbyte, col, row;

LiquidCrystal_I2C lcd(0x3F, 20, 4);

void setup()
{
  pinMode(LED, OUTPUT);
  digitalWrite(LED, HIGH);
  Serial.begin(9600);
  for (pin = 2; pin <= 10; pin++)
  {
    pinMode(pin , INPUT);
  }
  pinMode(13, OUTPUT);
  lcd.begin();
  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("Smartie by Wipf");
  lcd.setCursor(0, 3);
  lcd.print(TASTERANZAHL);
  lcd.print(" Tasten ");
  lcd.setCursor(15, 3);
  lcd.print(VERSION);
  digitalWrite(LED, LOW);
}

byte serial_getch()
{
  while (Serial.available() == 0)
  {
    taster();
  }
  incoming = Serial.read();
  return (byte) (incoming & 0xff);
}

void loop()
{
  {
    rxbyte = serial_getch();
    if (rxbyte == 254)
    {
      switch (serial_getch())
      {
        case 66:
          digitalWrite(LED, HIGH);
          break;
        case 70:
          digitalWrite(LED, LOW);
          break;
        case 71:
          col = (serial_getch() - 1);
          row = (serial_getch());
          lcd.setCursor(col, row - 1);
          break;
        case 72:
          lcd.setCursor(0, 0);
          break;
        case 88:
          lcd.clear();
          lcd.setCursor(0, 0);
          break;

      }
      return;
    }

    switch (rxbyte) 
    {
      case 0x02:
        rxbyte = 0xC6;
        break;
      case 0x03:
        rxbyte = 0xDB;
        break;
      case 0x01:
        rxbyte = 0xFF;
        break;
      case 0x04:
      case 0x05:
      case 0x06:
      case 0x07:
      case 0x08:
        rxbyte = 0x20;
        break;

      case 0xE4:
        rxbyte = 0xE1;
        break;
      case 0xF1:
        rxbyte = 0xEE;
        break;
      case 0xF6:
        rxbyte = 0xEF;
        break;
      case 0xFC:
        rxbyte = 0xF5;
        break;
      case 0xA3:
        rxbyte = 0xED;
        break;
      case 0xB0:
        rxbyte = 0xDF;
        break;
      case 0xB5:
        rxbyte = 0xE4;
        break;
      case 0xC4:
        rxbyte = 0xE1;
        break;
      case 0xC0:
      case 0xC1:
      case 0xC2:
      case 0xC3:
      case 0xC5:
        rxbyte = 0x41;
        break;
      case 0xC8:
      case 0xC9:
      case 0xCA:
      case 0xCB:
        rxbyte = 0x45;
        break;
      case 0xCC:
      case 0xCD:
      case 0xCE:
      case 0xCF:
        rxbyte = 0x49;
        break;
      case 0xD1:
        rxbyte = 0x43;
        break;
      case 0xD6:
        rxbyte = 0xEF;
        break;
      case 0xD2:
      case 0xD3:
      case 0xD4:
      case 0xD5:
      case 0xD8:
        rxbyte = 0x4F;
        break;
      case 0xDC:
        rxbyte = 0xF5;
        break;
      case 0xD9:
      case 0xDA:
      case 0xDB:
        rxbyte = 0x55;
        break;
      case 0xDD:
        rxbyte = 0x59;
        break;
      case 0xE0:
      case 0xE1:
      case 0xE2:
      case 0xE3:
      case 0xE5:
        rxbyte = 0x61;
        break;
      case 0xE7:
        rxbyte = 0x63;
        break;
      case 0xE8:
      case 0xE9:
      case 0xEA:
      case 0xEB:
        rxbyte = 0x65;
        break;
      case 0xEC:
      case 0xED:
      case 0xEE:
      case 0xEF:
        rxbyte = 0x69;
        break;
      case 0xF2:
      case 0xF3:
      case 0xF4:
      case 0xF5:
      case 0xF8:
        rxbyte = 0x6F;
        break;
      case 0xF7:
        rxbyte = 0xFD;
        break;
      case 0xF9: 
      case 0xFA:
      case 0xFB:
        rxbyte = 0x75;
        break;
      default:
        break;
    }
    lcd.write(rxbyte);
  }
}

void taster(void)
{
  if (warten > PAUSE)
  {
    for (i = 2; i < TASTERANZAHL + 2; i++)
    {
      IN[i] = digitalRead(i);
      if (IN[i] == HIGH)
      {
        digitalWrite(13, HIGH);
        Serial.write(i + 47); //pin 2 == 50 == ASCII "2"
        Serial.flush(); 
        warten = 0;
        break;
      }
    }

   if (warten > PAUSE+10000)
   {
    warten = PAUSE;
   }
  }
  if (warten == PAUSE)
  {
    digitalWrite(13, LOW);
  }
  warten++;
}


```
