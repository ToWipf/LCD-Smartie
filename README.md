# LCD-Smartie

LCD Smartie zeigt informationen 
zb. 
- Uhr
- Liedtitel
- CPU Auslastung
- Temperatur
- ...

des Computers auf einen kleinen LCD Bildschirm an

Programm dazu: http://lcdsmartie.sourceforge.net/

Erweitert um 11Taster und viele kleinen Fehlerbehebungen

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
      
## Software:
   - LED Smartie 5.4
   - matrix.dll COM8,9600
   - Refresh intervall 50 ms
   - scroll intervall 600

## Optional:
   -  Bildschirmhelligkeit über 5kOhm Poti
   -  Externer RST Taster ohne Pull down widerstand
