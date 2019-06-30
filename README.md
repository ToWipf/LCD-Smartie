# LCD-Smartie 

## zeigt informationen z.B. : 
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
- Files

Zeigt diese Werte des Computers über USB auf einen LCD Bildschirm an

## kann mit den Tastern steuern:

- Anzuzeigende Seite
- Nächstes Lied / Letztes Lied
- Lautstärke
- Theoretisch kann man jedes script oder Anwedung starten

## Hardware:

 - Arduino Nano
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
   
## Fehler:
 
 - beim Ausgeben des 'þ' Zeichen
 
## Bilder: 

![Bild 1](https://github.com/ToWipf/LCD-Smartie/blob/master/pic/Bild1.jpg)
***
![Bild 2](https://github.com/ToWipf/LCD-Smartie/blob/master/pic/Bild2.jpg)
***
![Bild 3](https://github.com/ToWipf/LCD-Smartie/blob/master/pic/Bild3.jpg)

Programm dazu: http://lcdsmartie.sourceforge.net/

Erweitert um 11 Taster und viele kleine Fehlerbehebungen
 
Tobias Fritsch  August 2016 - Juni 2019
