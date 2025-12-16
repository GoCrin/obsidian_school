# Risikomanagement


1. Risiko identifizieren
	1. Brainstorming, Kreativitätstechniken, Erfahrung
2. Risiken bewerten
	1. Durch 2 Dimensionen: Tragweite / €, Eintrittswahrscheinlichkeit
	2. Risikowert (RW) = Tragweite (TW) \* Eintrittswahrscheinlichkeit (EW)
3. Strategien festlegen
	1. Vermeiden
	2. Reduzieren
	3. Verlagern
	4. Akzeptieren
4. Maßnahmen definieren
5. Maßnahmen umsetzen
6. Auswirkungen überprüfen
7. Risiken überwachen

## Umgang mit Risiken
[Projekte leicht gemacht: Strategien zum Umgang mit Risiken](https://projekte-leicht-gemacht.de/blog/methoden/projektrisiken/strategien-zum-umgang-mit-risiken/)

![[Pasted image 20251118101404.png]]

Tragweite (TW €) von 1 - 10 und Eintrittswahrscheinlichkeit (EW %) zwischen 0 - 100%

## Definition Risiko
**Ereignis** oder Umstand, das / der nicht sicher, sondern in einer gewissen **Wahrscheinlichkeit eintritt** und **negative Auswirkungen** (oder Schaden, Tragweite) verursacht.

DSGVO (en. GDPR - General Data Protection Regulation)

# Projektcontrolling (Projektsteuerung)

Wichtigste sachliche (Gegenteil: fachlich) Aufgabe der Projektmanager (PM). Ziel alles Projektsteuerungsaktivitäten ist es den **IST**-Stand (= aktueller Status des Projekts) mit dem **SOLL**-Zustand abzugleichen (= geplante Projektfortschritt).
![[Pasted image 20251202100341.png]]
## Sachfortschrittskontrolle

Um zu messen wie weit der Fortschritt gibt es mehrere Methoden
* Statusschritt-Technik: man gibt genau an wie weit man ist
* 50-50: 50% wenn man Anfängt, 100% wenn es fertig ist
* 0-100: 0% wenn man Anfängt, 100% wenn es fertig ist (okay wenn man viele kleine Aufgaben hat)

## Earned-Value-Analyse

[Projekte leicht gemacht: Earned-Value-Analyse](https://projekte-leicht-gemacht.de/blog/projektmanagement/klassisch/projektsteuerung/earned-value-analyse/)

Varianz ... Abweichung absolut in €
Performance-Index (oder. Indikatoren) sind Verhältniszahl in Prozent

### Formelsammlung

| Wert                                      | Formel                     |
| ----------------------------------------- | -------------------------- |
| Geplante Gesamtkosten $= GK_{Plan}$       | -                          |
| Fertigstellungsgrad Plan $= FstGr_{Plan}$ | -                          |
| Earned Value Plan $= EV_{Plan}$           | $GK_{Plan} * FstGr_{Plan}$ |
| Fertigstellungsgrad Ist $= FstGr_{Ist}$   | durch Gantt oder PSP       |
| Earned Value Ist $= EV_{Ist}$             | $GK_{Plan} * FstGr_{Ist}$  |
| Ist-Kosten $= IK$                         | durch ERP                  |
| Kostenvarianz                             | $EV_{Ist} - IK$            |
| Terminvarianz                             | $EV_{Ist} - EV_{Plan}$     |
| Kosten-Performance-Index $= KPI$          | $EV_{Ist} / IK$            |
| Termin-Performance-Index $= TPI$          | $EV_{Ist} / EV_{Plan}$     |
| Critical Ratio                            | $KPI * TPI$                |

## Excel Aufgabe
Fertigstellungswerte
EV_Plan = GK_Plan \* FertigstellungsGrad_Plan
EV_ist = GK_Plan \* FstGr_ist

Abweichungen
Pos. Werte gut, neg. schlecht \:\(
Kostenvarianz = EV_ist - IstKosten (... IK) -> durch ERP, Projektcontroller -> Buchhaltung, Arbeitsaufz.
Terminvarianz = EV_ist - EV_Plan

relative Bewertungs verhältnis
Kosten-Performance-Index = EV_ist / IK \[%\]
Termin-Performance-Index = EV_ist / EV_Plan = (GK_Plan \* FstGR_ist) / (GK_Plan \* FstGr_Plan) =  FstGR_ist / FstGr_Plan\[%\]

