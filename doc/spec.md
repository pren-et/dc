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

## Ein/Aus Schalter
* Ein Schalter (überbrückbar) für ein Enable der Spannungsversorgung

## Strombegrenzungsschaltung
Die Strombegrenzung am Ausgang kann durch eine Verstärkerschaltung realisiert werden.
* Ein Shunt über den der Laststrom fliesst, wird als Eingangsspannung des OPV benutzt.
* Der nichtinvertierende Verstärker verstärkt die Spannung. Mit einem Potentiometer kann die Verstärkung variabel eingestellt werden.
* Die Ausgangsspannung vom OPV wird am Gate eines Transistors (z.B. 2N6804) angeschlossen.
* Der Transistor, Lastwiderstand und Shunt bilden einen geschlossenen Kreis.
* Bei mittlerem Strom fällt am Transistor eine kleine Spannung ab, da der Widerstand Rds_on klein ist. Kommt nun der Strom an die eingestellte Strombegrenzung, steigt die Spannung am Gate an. Die Strombegrenzung stellt sich ein, da Rds grösser wird wegen dem Strom und der niedrigen Spannung Vgs.
* [Kennlinie MOSFET](../RDS_Kennlinie.png)

## Offene Fragen
* Schutzfunktionen
    * Übertemperatur
    * Überstrom (mittels selbstrückstellender [PTC Sicherung](http://uk.farnell.com/littelfuse/1812l014dr/resettable-fuse-ptc-10a-60v-1812/dp/1822211)?)
    * Überspannung
* Speisungskonzept
* Eingangspegel
