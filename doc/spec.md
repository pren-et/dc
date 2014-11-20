# Spezifikation

[Zurück](./README.md)

Die hier aufgeführten Punkte sind noch in Bearbeitung und sind somit noch
nicht verbindlich.

## Interface
* Das DC-Modul hat potentialfreie digitale Eingänge für Logikpegel von 3.3V
bis 24V

### Eingänge
* DIR für die Angabe der Drehrichtung
* PWM für externes Takten
* ON für voreingestellten PWM
* EN für ein Enable der Taktung

### Ausgänge
* M1 für den einen Motoranschluss
* M2 für den anderen Motoranschluss

## Speisung
* V_MOTOR: 5V bis 60V für die Motorspannung
* V_LOGIK: 5V bis 15V für die Modulspannung

Die interne Versogung ist mit einem 3.3V Step-Down Regler realisiert für
allfällige Erweiterungen und Abgriffe auf Logik (Mikrocontroller etc.).

## Internes PWM
Um das DC-Modul auch ohne Regelung oder permanente Ansteuerung betreiben zu
können, stehen zwei PWM-Generatoren zur verfügung, die auf verschiedene
Frequenzen und Duty-Cycle eingestellt werden können (Spannungsteier o.ä.).
Diese werden dann aus der Kombination aus DIR und ON gewählt (ein ON blockiert
den PWM Eingang).
