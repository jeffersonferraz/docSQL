# SQL Doc

1. Abfragen erstellen
2. Abfragen mit einfachen Aggregat-Funktionen
3. Abfragen mit logischen Operatoren
4. Abfragen mit mathematischen und statischen Funktionen anwenden
5. Abfragen mit dem Vergleich von Zeichenketten
6. Abfragen mit Zeichenketten- und Datumsfunktion
7. Abfragen mit Gruppierung von Datenmengen
8. Abfragen über mehrere Tabellen und Unterabfragen erstellen


## 1. Abfragen erstellen

#### Abfragen mit der Tabelle 'person' aus.

1. Lassen Sie sich alle Personendaten anzeigen.
2. Lassen Sie sich in der angegebenen Reihenfolge den Vornamen, den Nachnamen, das Geburtsdatum und den Wohnort aller Personen anzeigen.
3. Lassen Sie sich alle Wohnorte anzeigen. Unterdrücken Sie dabei die Mehrfachanzeige identischer Wohnorte.
4. Lassen Sie sich in der angegebenen Reihenfolge den Vornamen, den Nachnamen, die Postleitzahl und den Wohnort aller Personen ausgeben. Sortieren Sie Nachname und Vorname in alphabetischer Reihenfolge.
5. Lassen Sie sich in der angegebenen Reihenfolge den Nachnamen, den Wohnort, PLZ sowie das Land aller Personen anzeigen. Verwenden Sie in der Ergebnistabelle den Spaltennamen: Name, Land, Wohnort und Postleitzahl.


## 2. Abfragen mit einfachen Aggregat-Funktionen

#### Berechnungen mit den in der Datenbank gespeicherten Werten. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich alle Artikeldaten anzeigen.
2. Lassen Sie sich alle Artikelnamen, die dazugehörigen Preise (Netto) und die Preise mit einem Aufschlag von 19% (Brutto) anzeigen. Benennen Sie in der Ausgabe die entsprechenden Tabellenspalten Artikel, Nettopreis und Bruttopreis.
3. Welche Bestellsumme pro Artikel entsteht, wenn Sie von jedem Artikel 50 Stück bestellen. Lassen Sie sich Artikelname, Einzelpreis und Gesamtpreis anzeigen. Benennen Sie die entsprechenden Tabellenspalten Artikel, Einzelpreis, Gesamtpreis.


## 3. Abfragen mit logischen Operatoren

#### WHERE-Klausel und Vergleichsoperationen: Ergebnismenge auf relevanten Datensätze begrenzen. Abfragen mit der Tabelle 'person'.

1. Lassen Sie sich die Personendaten aller Personen anzeigen, die in Berlin wohnen.
2. Lassen Sie sich die Vornamen, Nachnamen und Wohnorte aller Personen anzeigen, die entweder in Berlin oder in Klagenfurt wohnen.
3. Lassen Sie sich die Vornamen, Nachnamen und Wohnorte aller Personen anzeigen, die nicht in Berlin wohnen.
4. Lassen Sie sich die Nachnamen, Wohnorte und Geburtsdaten aller Personen anzeigen, die in Deutschland wohnen und nach dem 01.06.1960 geboren worden sind.


## 4. Abfragen mit mathematischen und statischen Funktionen anwenden

#### Mathematische und statistische Funktionen. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich von allen Artikeln, die mehr als 300 kosten, den Artikelnamen, den Preis und einen um 20 % erhöhten Preis ausgeben. Runden Sie den berechneten Preis auf zwei Nachkommastellen. Nennen Sie die Tabellenspalten der Ergebnistabelle Artikel, Nettopreis und Neupreis.
2. Ermitteln Sie den durchschnittlichen Preis von Tastatur, Drucker und Festplatte. Nennen Sie die Tabellenspalte der Ergebnistabelle Durchschnittspreis.
3. Ermitteln Sie die Anzahl aller Artikel, die vom Hersteller mit der Herstellernummer 10 angeboten werden. Nennen Sie die Tabellenspalte der Ergebnistabelle Artikelanzahl.
4. Ermitteln Sie den Gesamtpreis, wenn Sie jeweils 5 Artikel des Herstellers mit der Herstellernummer 10 kaufen würden. Nennen Sie die Tabellenspalte der Ergebnistabelle Gesamtpreis.
5. Ermitteln Sie den billigsten und den teuersten Artikel. Nennen Sie die Tabellen-
spalten der Ergebnistabelle Billig und Teuer.
