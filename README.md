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
```SQL
SELECT * FROM person;
```
```SQL
+----------------+---------------+---------+--------------------+----------------+-------+-------------+--------------+
| personennummer | nachname      | vorname | strasse            | ort            | plz   | land        | geburtsdatum |
+----------------+---------------+---------+--------------------+----------------+-------+-------------+--------------+
|              1 | Blotzek       | Ulrich  | Großkopf 4         | Arnsberg       | 59823 | Deutschland | 1960-10-05   |
|              2 | Schatter      | Peter   | Försterstrasse 56  | Augsburg       | 86179 | Deutschland | 1980-01-01   |
|              3 | Wojack        | Albert  | Westendstrasse 92  | Berlin         | 12234 | Deutschland | 1955-06-15   |
|              4 | Virtanen      | Veera   | Oyi Keilasatama 21 | Espoo          |  2150 | Finnland    | 1992-12-30   |
|              5 | Hämäläinen    | Ahvo    | Tapulikuja 56      | Forssa         | 30100 | Finnland    | 1977-04-23   |
|              6 | Huisman       | Fenna   | Spoordreef 87      | Almere         |  1315 | Niederlande | 1971-08-17   |
|              7 | Prins         | Lieke   | Noordgeest 21      | Bergen op Zoom |  4600 | Niederlande | 1987-05-08   |
|              8 | David         | Paula   | Murielstrasse 47   | Klagenfurt     |  9020 | Österreich  | 1970-01-21   |
|              9 | Hardiff       | Joseph  | Bischofstrasse 139 | Klagenfurt     |  9200 | Österreich  | 1962-08-09   |
+----------------+---------------+---------+--------------------+----------------+-------+-------------+--------------+
```

2. Lassen Sie sich in der angegebenen Reihenfolge den Vornamen, den Nachnamen, das Geburtsdatum und den Wohnort aller Personen anzeigen.
```SQL

```
```SQL

```

3. Lassen Sie sich alle Wohnorte anzeigen. Unterdrücken Sie dabei die Mehrfachanzeige identischer Wohnorte.
```SQL

```
```SQL

```

4. Lassen Sie sich in der angegebenen Reihenfolge den Vornamen, den Nachnamen, die Postleitzahl und den Wohnort aller Personen ausgeben. Sortieren Sie Nachname und Vorname in alphabetischer Reihenfolge.
```SQL

```
```SQL

```

5. Lassen Sie sich in der angegebenen Reihenfolge den Nachnamen, den Wohnort, PLZ sowie das Land aller Personen anzeigen. Verwenden Sie in der Ergebnistabelle den Spaltennamen: Name, Land, Wohnort und Postleitzahl.
```SQL

```
```SQL

```

## 2. Abfragen mit einfachen Aggregat-Funktionen

#### Berechnungen mit den in der Datenbank gespeicherten Werten. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich alle Artikeldaten anzeigen.
```SQL

```
```SQL

```

2. Lassen Sie sich alle Artikelnamen, die dazugehörigen Preise (Netto) und die Preise mit einem Aufschlag von 19% (Brutto) anzeigen. Benennen Sie in der Ausgabe die entsprechenden Tabellenspalten Artikel, Nettopreis und Bruttopreis.
```SQL

```
```SQL

```

3. Welche Bestellsumme pro Artikel entsteht, wenn Sie von jedem Artikel 50 Stück bestellen. Lassen Sie sich Artikelname, Einzelpreis und Gesamtpreis anzeigen. Benennen Sie die entsprechenden Tabellenspalten Artikel, Einzelpreis, Gesamtpreis.
```SQL

```
```SQL

```

## 3. Abfragen mit logischen Operatoren

#### WHERE-Klausel und Vergleichsoperationen: Ergebnismenge auf relevanten Datensätze begrenzen. Abfragen mit der Tabelle 'person'.

1. Lassen Sie sich die Personendaten aller Personen anzeigen, die in Berlin wohnen.
```SQL

```
```SQL

```

2. Lassen Sie sich die Vornamen, Nachnamen und Wohnorte aller Personen anzeigen, die entweder in Berlin oder in Klagenfurt wohnen.
```SQL

```
```SQL

```

3. Lassen Sie sich die Vornamen, Nachnamen und Wohnorte aller Personen anzeigen, die nicht in Berlin wohnen.
```SQL

```
```SQL

```

4. Lassen Sie sich die Nachnamen, Wohnorte und Geburtsdaten aller Personen anzeigen, die in Deutschland wohnen und nach dem 01.06.1960 geboren worden sind.
```SQL

```
```SQL

```

## 4. Abfragen mit mathematischen und statischen Funktionen anwenden

#### Mathematische und statistische Funktionen. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich von allen Artikeln, die mehr als 300 kosten, den Artikelnamen, den Preis und einen um 20 % erhöhten Preis ausgeben. Runden Sie den berechneten Preis auf zwei Nachkommastellen. Nennen Sie die Tabellenspalten der Ergebnistabelle Artikel, Nettopreis und Neupreis.
```SQL

```
```SQL

```

2. Ermitteln Sie den durchschnittlichen Preis von Tastatur, Drucker und Festplatte. Nennen Sie die Tabellenspalte der Ergebnistabelle Durchschnittspreis.
```SQL

```
```SQL

```

3. Ermitteln Sie die Anzahl aller Artikel, die vom Hersteller mit der Herstellernummer 10 angeboten werden. Nennen Sie die Tabellenspalte der Ergebnistabelle Artikelanzahl.
```SQL

```
```SQL

```

4. Ermitteln Sie den Gesamtpreis, wenn Sie jeweils 5 Artikel des Herstellers mit der Herstellernummer 10 kaufen würden. Nennen Sie die Tabellenspalte der Ergebnistabelle Gesamtpreis.
```SQL

```
```SQL

```

5. Ermitteln Sie den billigsten und den teuersten Artikel. Nennen Sie die Tabellenspalten der Ergebnistabelle Billig und Teuer.


## 5. Abfragen mit dem Vergleich von Zeichenketten

#### IN, BETWEEN und LIKE Operatoren. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich bis auf die Artikelnummer alle Artikeldaten der Hersteller mit der Herstellernummer 10, 30 und 50 anzeigen.
```SQL

```
```SQL

```

2. Lassen Sie sich alle Artikelnamen und die dazugehörigen Artikelpreise ausgeben, die zwischen 200 und 400 liegen.
```SQL

```
```SQL

```

3. Lassen Sie sich alle Artikelnamen und dazugehörigen Artikelpreise ausgeben, deren Name mit dem Buchstaben M beginnt.
```SQL

```
```SQL

```

#### Abfragen mit der Tabelle 'hersteller' aus.
4. Lassen Sie sich die Herstellernamen und die dazugehörigen Länder anzeigen.
```SQL

```
```SQL

```

5. Lassen Sie sich alle Herstellernamen und die dazugehörigen Länder anzeigen, die Hersteller beginnen mit dem Buchstaben M und sind nicht aus Japan sind.
```SQL

```
```SQL

```

6. Lassen Sie sich alle Herstellernamen und die dazugehörigen Länder anzeigen, die nicht mit dem Buchstaben M beginnen und entweder aus Deutschland oder den USA sind.
```SQL

```
```SQL

```

## 6. Abfragen mit Zeichenketten- und Datumsfunktion

#### Anwendung von Zeichenketten- und Datumsfunktionen. Abfragen mit der Tabelle 'person'.

1. Geben Sie in jeweils einer Spalte einer Ergebnistabelle den Namen einer Person bestehend aus Vornamen und Nachnamen sowie die Anschrift bestehend aus Postleitzahl und Ort aus. Fügen Sie in der Ausgabe zwischen Vornamen und Nachnamen sowie zwischen Postleitzahl und Ort ein Leerzeichen ein. Nennen Sie die Spalten der Ergebnistabelle Name und Anschrift.
```SQL

```
```SQL

```

2. Ermitteln Sie die Länge aller Ortsnamen und geben Sie Ortsnamen und Länge in einer Ergebnistabelle aus. Nennen Sie die Spalten der Ergebnistabelle «Ortsname» und «Ortsnamenlänge». Unterdrücken Sie die Mehrfachanzeige identischer Ortsangaben.
```SQL

```
```SQL

```

3. Ermitteln Sie das Alter aller Personen der Tabelle 'person'. Lassen Sie sich das Alter, den Vornamen, den Nachnamen und das Geburtsdatum jeder Person anzeigen. Nennen Sie die Spalte der Ergebnistabelle, die die Altersangaben enthält, Lebensalter.
```SQL

```
```SQL

```

## 7. Abfragen mit Gruppierung von Datenmengen

#### Aus allen Bestellungen der Tabelle 'bestellung' die Anzahl der Bestellungen für jeden Artikel und die daraus resultierende Gesamtbestellsumme pro Artikel ermitteln. Nur Gesamtbestellsummen, die größer als 200 sind, dabei berücksichtigen. Artikelnummer, die Anzahl der Bestellungen eines Artikels sowie die Gesamtbestellsumme anzeigen lassen. Die Spalten der Ergebnistabelle Artikelnummer, Artikelanzahl und Gesamtbestellsumme nennen. Gruppierung nutzen.
```SQL

```
```SQL

```


#### Aus allen Artikeln der Tabelle 'artikel' den Durchschnittspreis aller Artikel eines Herstellers ermitteln. Nur die Hersteller, die mehrere Artikel anbieten, dabei berücksichtigen. Die Herstellernummer und den Durchschnittspreis anzeigen lassen. Die Spalten der Ergebnistabelle Herstellernummer und Durchschnittspreis nennen. Gruppierung nutzen.
```SQL

```
```SQL

```

## 8. Abfragen über mehrere Tabellen und Unterabfragen erstellen

#### Abfragen mit den Tabellen 'artikel' und 'hersteller'.

1. Lassen Sie sich alle Artikelnamen und alle dazugehörigen Informationen über den Artikelhersteller, sortiert nach Artikelnamen, anzeigen. Benutzen Sie zur Tabellenverknüpfung die WHERE-Klausel. Benutzen Sie außerdem den Aliasnamen a für die Tabelle 'artikel' und den Aliasnamen h für die Tabelle 'hersteller'.
```SQL

```
```SQL

```

2. Lassen Sie sich alle Namen, Preise und die zugehörigen Hersteller für Artikel anzeigen, deren Preis höher als 200 ist. Nutzen Sie für die Tabellenverknüpfung die JOIN-Klausel. Benutzen Sie außerdem den Aliasnamen a für die Tabelle 'artikel' und den Aliasnamen h für die Tabelle 'hersteller'.
```SQL

```
```SQL

```

#### Abfragen mit den Tabellen 'person', 'artikel', 'hersteller' und 'bestellung'.

3. Lassen Sie sich zu jedem Bestellvorgang in der angegebenen Reihenfolge folgende Daten anzeigen: Bestellnummer, Nachname und Vorname des Kunden, Artikelanzahl und Bestellsumme.
```SQL

```
```SQL

```

4. Welche Kunden haben mehr als 2 Artikel bestellt? Lassen Sie sich die Bestellnummer, Vor- und Nachname des Kunden, Artikelname, Artikelanzahl und Artikelpreis anzeigen.
```SQL

```
```SQL

```

5. Welche Kunden haben Artikel bestellt, die in Japan hergestellt werden? Lassen Sie sich Nachname und Vorname des Kunden, Artikelname, Herstellername sowie das Herstellerland anzeigen.
```SQL

```
```SQL

```

6. Überprüfen Sie, ob Kunden aus Forssa Geräte von einem Hersteller aus Japan bestellt haben. Lassen Sie sich Nachname, Vorname und Wohnort des Kunden, den Artikelnamen sowie das Herstellerland anzeigen.
```SQL

```
```SQL

```

7. Lassen Sie sich die vollständigen Daten aller Kunden anzeigen, die einen Artikel
vom Hersteller Logitech bestellt haben.
```SQL

```
```SQL

```

#### Abfragen mithilfe von Unterabfragen.

1. Ermitteln Sie aus der Tabelle 'person' den Nachnamen und das Geburtsdatum der jüngsten Person. Nennen Sie die Spalten der Ergebnistabelle Name und Geburtsdatum.
```SQL

```
```SQL

```

2. Ermitteln Sie aus der Tabelle 'artikel' den Namen und den Preis des billigsten Artikels. Nennen Sie die Spalten der Ergebnistabelle Artikel und Preis.
```SQL

```
```SQL

```

3. Ermitteln Sie mithilfe der Tabellen 'bestellung', 'artikel' und 'person' die Bestellung mit der höchsten Bestellsumme. Lassen Sie sich den dazugehörigen Nachnamen des Kunden, den Artikelnamen und die Bestellsumme anzeigen. Nennen Sie die Spalten der Ergebnistabelle Name, Artikel und Bestellsumme.
```SQL

```
```SQL

```


## Tabellen

### person
|`personennummer`| `nachname`    |`vorname`| `strasse`          | `ort`          | `plz` | `land`      |`geburtsdatum`|
|----------------|---------------|---------|--------------------|----------------|-------|-------------|--------------|
|              1 | Blotzek       | Ulrich  | Großkopf 4         | Arnsberg       | 59823 | Deutschland | 1960-10-05   |
|              2 | Schatter      | Peter   | Försterstrasse 56  | Augsburg       | 86179 | Deutschland | 1980-01-01   |
|              3 | Wojack        | Albert  | Westendstrasse 92  | Berlin         | 12234 | Deutschland | 1955-06-15   |
|              4 | Virtanen      | Veera   | Oyi Keilasatama 21 | Espoo          |  2150 | Finnland    | 1992-12-30   |
|              5 | Hämäläinen    | Ahvo    | Tapulikuja 56      | Forssa         | 30100 | Finnland    | 1977-04-23   |
|              6 | Huisman       | Fenna   | Spoordreef 87      | Almere         |  1315 | Niederlande | 1971-08-17   |
|              7 | Prins         | Lieke   | Noordgeest 21      | Bergen op Zoom |  4600 | Niederlande | 1987-05-08   |
|              8 | David         | Paula   | Murielstrasse 47   | Klagenfurt     |  9020 | Österreich  | 1970-01-21   |
|              9 | Hardiff       | Joseph  | Bischofstrasse 139 | Klagenfurt     |  9200 | Österreich  | 1962-08-09   |

### artikel
|`artikelnummer`|`herstellernummer`|`artikelname`| `preis`|
|---------------|------------------|-------------|--------|
|             1 |               10 | Maus        |  10.00 |
|             2 |               10 | Tastatur    |  20.00 |
|             3 |               50 | Drucker     | 300.00 |
|             4 |               30 | Festplatte  | 400.00 |
|             5 |               20 | Monitor     | 500.00 |

### hersteller
|`herstellernummer`| `herstellername`|   `land`    |
|------------------|-----------------|-------------|
|               10 | Logitech        | Schweiz     |
|               20 | SONY            | Japan       |
|               30 | Maxtor          | USA         |
|               40 | Medion          | Deutschland |
|               50 | Hewlett Packard | USA         |

### bestellung
|`bestellnummer`|`artikelnummer`|`kundennummer`|`artikelanzahl`|`bestellsumme`|
|---------------|---------------|--------------|---------------|--------------|
|             1 |             1 |            4 |             2 |        20.00 |
|             2 |             2 |            1 |             1 |        20.00 |
|             3 |             1 |            2 |             3 |        30.00 |
|             4 |             3 |            3 |             1 |       300.00 |
|             5 |             5 |            5 |             5 |      2500.00 |
