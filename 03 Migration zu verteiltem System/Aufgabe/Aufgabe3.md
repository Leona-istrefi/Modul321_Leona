# Aufgabe 3 – Aufteilung des LMS-Monolithen in Microservices

## 1\. Feature-Liste des LMS

1. Anmeldung / Zugriffssteuerung (wer darf welchen Kurs sehen)
2. Kurse anlegen, Module \& Materialien (Video, Dokument) verwalten
3. Individuelle Lernpfade gestalten
4. Prüfungen/Aufgaben erstellen, automatisch oder manuell auswerten
5. Lernfortschritt speichern (erledigte Aufgaben, bestandene Prüfungen)
6. Nachrichten / Diskussionsforen
7. Ankündigungen der Lehrenden
8. Berichte über Aktivität \& Fortschritt für Admins/Lehrende

## 2\. Abgeleitete Microservices

|Microservice|Zuständigkeit|
|-|-|
|**Benutzerservice**|Accounts, Rollen, Login, Zugriffsrechte|
|**Kursservice**|Kurse, Module, Materialien, Lernpfade|
|**Prüfungsservice**|Aufgaben, Tests, Korrektur/Auswertung|
|**Fortschrittsservice**|Ergebnisse, abgeschlossener Verlauf|
|**Kommunikationsservice**|Nachrichten, Forum, Ankündigungen|
|**Reporting-Service**|Aggregiert Daten mehrerer Services zu Berichten|

## 3\. Verbindungen zwischen den Services

Wer mit wem zusammenarbeitet:

* **Benutzerservice <-> Kursservice** – Zugriffsprüfung auf Kurse
* **Kursservice <-> Kommunikation** – Forum/Nachrichten gehören zu Kursen
* **Kursservice <-> Fortschrittsservice** – Fortschritt bezieht sich auf Module
* **Prüfungsservice <-> Fortschrittsservice** – Prüfungsergebnisse fliessen in den Fortschritt ein
* **Fortschrittsservice <-> Reporting** – liefert Rohdaten für Berichte
* **Benutzerservice -> Reporting** *(gestrichelt)* – Reporting aggregiert zusätzlich Nutzerdaten, ohne im Alltag direkt gekoppelt zu sein



