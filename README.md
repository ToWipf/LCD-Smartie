# LCD-Smartie

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


## kann mit den Tastern steuern:
- Anzuzeigende Seite
- Nächstes Lied / Letztes Lied
- Lautstärke
- Theoretisch kann man jedes script oder Anwedung starten


Programm dazu: http://lcdsmartie.sourceforge.net/

Erweitert um 11 Taster und viele kleine Fehlerbehebungen

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
   -  Externer reset Taster ohne Pulldownwiderstand
