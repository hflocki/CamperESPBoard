# CamperESP Board

⚠️ **STATUS: WORK IN PROGRESS (In Arbeit)** ⚠️  
*Dieses Projekt befindet sich aktuell noch in der Entwicklung und Testphase. Schaltpläne und Layouts können sich jederzeit ändern. Die Verwendung der Daten erfolgt auf eigene Gefahr.*

---

Das Board basiert auf einem **ESP32** und dient zur flexiblen Erfassung von Sensordaten (z. B. Temperatur, Füllstände) und zur Steuerung von Verbrauchern im Fahrzeug über eine integrierte Transistorschaltstufe.

Das Layout wurde maximal geschrumpft, um perfekt in das ultrakompakte **Spelsberg Mini 25-L/w Gehäuse** (Maße: 89 x 43 x 38 mm) zu passen.

---

## Features

- **Spannungsversorgung:** Robuster Step-Down-Regler (TPS5430) für die raue 12V-Camper-Bordnetzumgebung (mit Sicherung `F1` und Verpolungsschutz `D2`).
- **Kompakte Ausgänge:** 2,54 mm Lochreihen (Pin Header) statt klobiger Klemmen für maximale Platzersparnis und Rüttelfestigkeit.
- **Relais-/Schaltstufe:** Integrierter Transistor (`Q1`) an `GPIO10` zum direkten Schalten kleinerer Verbraucher oder Relais.
- **Schnittstellen:** Voller Hardware-I2C-Bus sowie UART (RX/TX) für die Kommunikation mit Displays, Sensoren oder Victron-Geräten.

---

## Pinbelegung (Pinout)

Die Anschlüsse sind logisch auf zwei einreihige Lochleisten (2,54 mm Raster) am rechten Rand aufgeteilt:

### Leiste 1 (J5) – Stromversorgung & I2C Bus
| Pin | Bezeichnung | Beschreibung |
|:---:|:------------|:-------------|
| 1   | **12V** | Abgesicherter 12V-Ausgang für externe Geräte |
| 2   | **5V** | 5V Versorgungsspannung (VDD) |
| 3   | **3V3** | Saubere 3,3V Logikspannung |
| 4   | **GND** | Gemeinsame Fahrzeugmasse (Minuspol) |
| 5   | **SDA** | I2C Datenleitung (`GPIO4`) |
| 6   | **SCL** | I2C Taktleitung (`GPIO5`) |
| 7   | **G0** | Universal Digital I/O (`GPIO0`) / z.B. OneWire |
| 8   | **G1** | Universal Digital I/O (`GPIO1`) |

### Leiste 2 (J6) – GPIOs & UART
| Pin | Bezeichnung | Beschreibung |
|:---:|:------------|:-------------|
| 1   | **G2** | Universal Digital I/O (`GPIO2`) |
| 2   | **G3** | Universal Digital I/O (`GPIO3`) |
| 3   | **REL** | Relais-Steuerpin (`GPIO10` über Transistorstufe) |
| 4   | **RX** | Serieller Empfangskanal (`GPIO20`) |
| 5   | **TX** | Serieller Sendekanal (`GPIO21`) |
| 6   | *NC* | Frei / Reserve |
| 7   | *NC* | Frei / Reserve |
| 8   | *NC* | Frei / Reserve |

---

## Projektstruktur für GitHub

Dieses Repository enthält alle benötigten KiCad-Quelldateien:

- `CamperESP.kicad_pro` - KiCad Projekt-Hauptdatei
- `CamperESP.kicad_sch` - Schaltplan (Schematic) mit optimiertem Label-Wiring
- `CamperESP.kicad_pcb` - Platinen-Layout (PCB) optimiert für Spelsberg-Gehäuse
- `fp-lib-table` & `sym-lib-table` - Lokale Bibliotheksverweise für benutzte Custom-Bauteile

---

## Einbau- & Löthinweise

1. **Leiterbahnen:** Die Leitungen für `12V`, `5V` und `GND` im Layout mit mindestens **1.0 mm bis 1.5 mm** Breite ausführen, um ausreichende Stromtragfähigkeit im Camper zu gewährleisten.
2. **Kabelanschluss:** Kabel können entweder direkt in die Platinenlöcher eingelötet werden (maximale Rüttelfestigkeit im Fahrbetrieb) oder über eine klassische 2,54 mm Stiftleiste steckbar gemacht werden.

---

## Haftungsausschluss (Disclaimer)

**Haftungsausschluss für Bastler- und DIY-Projekte:**

Die hier bereitgestellten Inhalte, Schaltpläne und Layouts dienen ausschließlich zu Informations- und privaten Bildungszwecken. 

1. **Keine Haftung:** Ich übernehme keinerlei Haftung für Schäden jeglicher Art (einschließlich, aber nicht beschränkt auf Sachschäden, Personenschäden, Fahrzeugbrände oder finanzielle Verluste), die direkt oder indirekt durch den Nachbau, die Nutzung oder Fehlfunktionen dieser Schaltung entstehen.
2. **Eigene Verantwortung:** Das Arbeiten an der Fahrzeugelektrik und Elektronik erfolgt vollständig auf eigene Gefahr und Verantwortung des Ausführenden. 
3. **KFZ-Vorschriften:** Es liegt in der Verantwortung des Nachbauers, für eine fachgerechte Absicherung (Sicherungen, Kabelquerschnitte) zu sorgen und alle geltenden Sicherheitsvorschriften sowie KFZ-Richtlinien einzuhalten.
