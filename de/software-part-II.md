---
title: Software Teil II
parent: DE - Handbuch
has_children: false
nav_order: 4
---

# Software Teil II
{: .no_toc }

Inhaltsverzeichnis

* TOC
{:toc}

## Einleitung

In diesem Kapitel wird beschrieben wie der Code auf den Mikrocontroller (NodeMCU) geladen wird. Damit könnt ihr loslegen, sobald ihr den Mikrocontroller zur Hand habt (weitere Teile werden nicht hierfür nicht benötigt). Für das Testing sollte dann zumindest der Temperatursensor angeschlossen werden.

## Code auf den Controller laden

Im aktuellen Release befinden sich zwei Datein:
* rancilio-pid.ino
* userConfig.h

Die rancilio-pid.ino ist das eigentliche Programmcode und die userConfig.h eine ausgelagerte Konfigurationsdatei. Diese einhaltet folgende Punkte.

### Vorab Konfig

Die wichtigsten Funktionen müssen hier parametriert werden. Denkt daran, den richtigen PID Mode, Temperatursensor und das ggf. passende Display auszuwählen.

```
define DISPLAY 2 // 1=U8x8libm, 0=Deaktiviert, 2=Externes 128x64 Display

define OFFLINEMODUS 0 // 0=Blynk und WLAN wird benötigt 1=OfflineModus (ACHTUNG EINSTELLUNGEN NUR DIREKT IM CODE MÖGLICH)

define ONLYPID 0 // 1=Nur PID ohne Preinfussion, 0=PID + Preinfussion

define TEMPSENSOR 2 // 1=DS19B20; 2=TSIC306

define BREWDETECTION 1 // 0 = off ,1 = Software, 2 = Hardware

define FALLBACK 1 // 1: fallback auf eeprom Werte, wenn blynk nicht geht 0: deaktiviert

define TRIGGERTYPE HIGH // LOW = low trigger, HIGH = high trigger relay

define OTA true // true=activate update via OTA

define PONE 1 // 1 = P_ON_E (normal), 0 = P_ON_M (spezieller PID Modus, ACHTUNG andere Formel zur Berechnung)
```

### Wifi

Unter Wifi müsst ihr euren Auth Token aus Blynk eintragen und eure Wlan SSID und das zugehörige Passwort. Bei der WLAN SSID bitte drauf achten, dass keine Leerzeichen darin enthalten sind! Auch Sonderzeichen machen gerne Schwierigkeiten im Betrieb.

```
#define AUTH "blynkauthcode"

#define D_SSID "wlanname"

#define PASS "wlanpass"
```

### OTA

Hier wird der Update **O**ver **T**he **A**ir eingestellt.

### PID

Hier definiert ihr eure initialen PID Werte.


## Code hochladen

Wenn ihr die .ino Datei öffnet, öffnet sich automatisch im zweiten Tab die userConfig.h mit den wichtigen Einstellungen. Danach auf den Pfeil klicken für den Upload auf den Microkontroller. Achtet darauf, dass Ihr den Auth-Code der Blynk-App und die WLAN-Zugangsdaten im Code der userConfig.h hinterlegt habt.

![](../img/image-2.png)

Bitte achtet vorher drauf, dass Ihr in den Board Einstellungen den richtigen COM Port ausgewählt habt.

Diesen könnt ihr auch auch im Gerätemanager prüfen (falls ihr ihn nicht wisst):

![](../img/34.png)

![](../img/35.png)

## Testen

Wenn alles geklappt habt könnt ihr auf dem Serial Monitor erkennen, wie sich der Microkontroller mit Blynk verbindet.

![](../img/36.png)

Klappt das und ist der Temperatursensor korrekt angeschlossen seht ihr am Handy in der Blynk App die Raumtemperatur.
Jetzt könnt iht nach und nach die anderen Bauteile verbinden (Relais) und weiter testen.
