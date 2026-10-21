# Fahrtenbuch v6

Sichtbar/CSV: Datum, Start, Ende, Kunde, Zweck, Start km, Ende km, Fahrtart.

Automatisch:
- Zuhause ↔ Arbeitsplatz = Arbeitsweg
- Kunde und Zweck leer = Privat
- alles andere = Geschäftlich
- km-Lücke zwischen letztem Ende und neuem Start = Privat
- „Letzten übernehmen“ kopiert den letzten End-km-Stand
- End-km kann aus GPS/Route vorgeschlagen und vor Speichern korrigiert werden
- Kundenadressen werden lokal gespeichert
- Fahrten sind nachträglich bearbeitbar
- Änderungen werden intern mit Zeitstempel protokolliert, nicht im normalen CSV

Feste Orte:
- Zuhause: Melchiorstrasse 7, 3027 Bern
- Arbeitsplatz: Chemin des Quatre-Vents 7F, 1166 Perroy

GitHub Pages:
Settings → Pages → Deploy from a branch → main → /(root)
Die Datei .nojekyll ist enthalten.


## Version 7
- Arbeitsweg zählt in der Jahresübersicht zu Privat gesamt.
- Arbeitsweg bleibt als eigene Fahrtart sichtbar.
- Anzeige: Privat inkl. Arbeitsweg + davon Arbeitsweg.
- Neue Fahrt: Start km darf nicht kleiner als der letzte gespeicherte Stand sein.
- Ist Start km höher, wird die Differenz als Privat-Lücke angekündigt.
- Nach Speichern wird Start km geleert.
- Datum wird bei einer neuen Fahrt automatisch auf heute gesetzt.


## Version 8 – HR-Monatsbericht
- HR-Monatsbericht mit den Spalten der bereitgestellten HR-Vorlage.
- Nur Geschäftsfahrten werden exportiert; Privat und Arbeitsweg nicht.
- Direktfahrten Zuhause ↔ Kunde: nur Mehrkilometer gegenüber dem üblichen Arbeitsweg werden angerechnet.
- Für solche Direktfahrten bleiben die Km-Stand-Spalten im HR-Bericht leer und die bereinigten km werden in „km manuell“ ausgegeben.
- Die echten Start-/End-km bleiben intern vollständig gespeichert.
- Der übliche Arbeitsweg wird aus vorhandenen Arbeitsweg-Fahrten gemittelt; falls keine vorhanden sind, per Route Zuhause ↔ Arbeitsplatz berechnet.


## Version 9 – Routenberechnung statt Live-Zählen
- Kein GPS-Live-Tracking während der Fahrt.
- START speichert nur Start-GPS, Start-Ortschaft und Start-km.
- Die App kann danach geschlossen bzw. das iPhone gesperrt werden.
- ENDE speichert Ziel-GPS und Ziel-Ortschaft.
- Danach wird die Straßenroute zwischen Start- und Ziel-GPS berechnet.
- End-km wird als Start-km + berechnete Route vorgeschlagen und kann bestätigt oder korrigiert werden.
- Zuhause ↔ Arbeitsplatz = Arbeitsweg.
- Zuhause ↔ Kunde = vollständige Geschäftsfahrt, ohne 116-km-Abzug.
- HR-Monatsbericht übernimmt die vollständigen Geschäftskilometer.


## Version 10 – Perroy entfernt
- Perroy/Arbeitsplatz wird nicht mehr automatisch erkannt.
- Kunde oder Zweck vorhanden = automatisch Geschäftlich.
- Kunde und Zweck leer = automatisch Privat.
- Arbeitsweg bleibt als manuell auswählbare Fahrtart erhalten.
- Kunden in oder nahe Perroy werden wie jeder andere Kunde vollständig als Geschäftsfahrt behandelt.
- Schnellwahl „Arbeitsplatz“ wurde entfernt; „Zuhause“ bleibt.

## Version 11
- Zweck ist bei neuen Fahrten standardmässig **Kundenbesuch**.
- Der Zweck bleibt jederzeit frei änderbar.
- Nach dem Speichern wird der Zweck für die nächste Fahrt wieder auf **Kundenbesuch** gesetzt.
- Dasselbe gilt beim manuellen Nachtragen.
