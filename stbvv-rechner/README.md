# StBVV Honorar- und Angebotsrechner

Eigenständige Web-App (eine HTML-Datei, keine Abhängigkeiten, kein Build-Schritt) zur Berechnung von
Steuerberater-Gebühren nach der **Steuerberatervergütungsverordnung (StBVV)** und zur Erstellung von
Angeboten / Honorarrechnungen.

## Nutzung

Datei `index.html` direkt im Browser öffnen (lokal, kein Server nötig) oder z. B. über GitHub Pages
hosten. Positionen, Dokumentdaten und Tabellenwerte werden automatisch im Browser (`localStorage`)
zwischengespeichert.

1. **Tab „Angebot / Positionen“**: Leistung auswählen, Gegenstandswert/Grundlage eingeben, Satz innerhalb
   des gesetzlichen Rahmens per Schieberegler wählen, Position hinzufügen. Zuschläge (mehrere Auftraggeber,
   Auslagenpauschale §16, USt) werden automatisch berechnet.
2. **Tab „Dokument & Druck“**: Kanzlei-/Mandantendaten, Dokumentart (Angebot / Honorarrechnung /
   Kostenvoranschlag) und Nummer/Datum pflegen, dann drucken oder als PDF speichern (Browser-Druckdialog).
3. **Tab „Tabellen & Sätze“**: Alle Tabellenwerte (A/B/C) und Parameter (Zeitgebühr, Mindestgegenstandswert)
   sind direkt editierbar — siehe Hinweis zur Datenlage unten.
4. **Tab „Hinweise“**: Umfang, Grenzen und Quellen des Rechners.

## Abgedeckte Leistungen

- Rat/Auskunft, Erstberatung (§21)
- Steuererklärungen: ESt, KSt, GewSt, GewSt-Zerlegung, USt-VA, USt-Jahr, Feststellungserklärung,
  sonstige Steuererklärungen (§24)
- Einnahmen-Überschuss-Rechnung (§25)
- Jahresabschluss (Bilanz/GuV), Anhang, Lagebericht (§35)
- Laufende Buchführung in allen Varianten (§33)
- Lohnbuchführung inkl. Einrichtung (§34)
- Mitwirkung bei Außenprüfung / schriftliche Einwendungen (§29)
- Zeitgebühr (§13)
- Einspruchs-/Rechtsbehelfsverfahren (vereinfacht, seit 2020 RVG-basiert)
- Freie Positionen / Pauschalen

**Nicht abgedeckt:** landwirtschaftliche Tabelle D, vollständige RVG-Gebührentabelle für
Rechtsbehelfs-/Klageverfahren, Sonderfälle (Organschaften, Übergangsrecht für Altfälle vor dem 1.7.2025 usw.).

## Wichtiger Hinweis zur Datenlage der Tabellenwerte

Die hinterlegten Werte der Tabellen A (Beratungstabelle), B (Abschlusstabelle) und C
(Buchführungstabelle) sowie die Zehntelsatz-Rahmen je Leistung wurden am **09.10.2026** aus frei
zugänglichen Sekundärquellen zusammengestellt (NWB Gesetze, buzer.de, lexmea.de, Bundessteuerberaterkammer),
**da der direkte Zugriff auf den amtlichen Verordnungstext** (gesetze-im-internet.de, Bundesgesetzblatt)
in der Erstellungs-Umgebung **technisch nicht möglich war** (keine DNS-Auflösung über den Netzwerk-Proxy).

Die Werte sollen dem Stand nach der *Fünften Verordnung zur Änderung der StBVV* (in Kraft seit 1. Juli 2025,
BGBl. 2025 I Nr. 105) entsprechen; mehrere Sekundärquellen widersprachen sich teilweise bei einzelnen
Zwischenwerten. In der App als <code>ungeprüft</code> markierte Rahmen (z. B. Anhang, Lagebericht,
Lohnbuchführung-Beträge, Feststellungserklärung) konnten in dieser Sitzung nicht gegen den Originaltext
verifiziert werden.

**Vor dem produktiven Einsatz** sollten alle Tabellenwerte und Rahmensätze im Tab „Tabellen & Sätze“
gegen die aktuelle amtliche Fassung der StBVV geprüft und bei Bedarf korrigiert werden — jeder Wert ist
dort direkt editierbar (Format `Gegenstandswert;Gebühr` je Zeile).

## Berechnungsmethodik

- Zwischenwerte innerhalb einer Tabelle werden linear zwischen den beiden benachbarten Stützpunkten
  interpoliert und auf volle Euro gerundet (Methodik analog zur StBVV-Vorgabe für Wertgebühren).
- Werte außerhalb des hinterlegten Tabellenbereichs werden auf den Randwert geklemmt und als Warnung
  markiert — es wird nicht extrapoliert.
- Mindestgegenstandswerte werden pro Leistung automatisch angewendet, wenn hinterlegt.
- Auslagenpauschale §16 StBVV: 20 % der Gebühren, gedeckelt auf 20 € (hier vereinfacht auf das gesamte
  Angebot angewendet; im Original je Angelegenheit).
