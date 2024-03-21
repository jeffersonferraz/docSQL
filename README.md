# SQL Doc

1. [Abfragen erstellen](https://github.com/jeffersonferraz/docSQL?tab=readme-ov-file#1-abfragen-erstellen)
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
```
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
SELECT vorname, nachname, geburtsdatum, ort
FROM person;
```
```
+---------+---------------+--------------+----------------+
| vorname | nachname      | geburtsdatum | ort            |
+---------+---------------+--------------+----------------+
| Ulrich  | Blotzek       | 1960-10-05   | Arnsberg       |
| Peter   | Schatter      | 1980-01-01   | Augsburg       |
| Albert  | Wojack        | 1955-06-15   | Berlin         |
| Veera   | Virtanen      | 1992-12-30   | Espoo          |
| Ahvo    | Hämäläinen    | 1977-04-23   | Forssa         |
| Fenna   | Huisman       | 1971-08-17   | Almere         |
| Lieke   | Prins         | 1987-05-08   | Bergen op Zoom |
| Paula   | David         | 1970-01-21   | Klagenfurt     |
| Joseph  | Hardiff       | 1962-08-09   | Klagenfurt     |
+---------+---------------+--------------+----------------+
```

3. Lassen Sie sich alle Wohnorte anzeigen. Unterdrücken Sie dabei die Mehrfachanzeige identischer Wohnorte.
```SQL
SELECT DISTINCT ort FROM person;
```
```
+----------------+
| ort            |
+----------------+
| Arnsberg       |
| Augsburg       |
| Berlin         |
| Espoo          |
| Forssa         |
| Almere         |
| Bergen op Zoom |
| Klagenfurt     |
+----------------+
```

4. Lassen Sie sich in der angegebenen Reihenfolge den Vornamen, den Nachnamen, die Postleitzahl und den Wohnort aller Personen ausgeben. Sortieren Sie Nachname und Vorname in alphabetischer Reihenfolge.
```SQL
SELECT vorname, nachname, plz, ort
FROM person
ORDER BY nachname, vorname ASC;
```
```
+---------+---------------+-------+----------------+
| vorname | nachname      | plz   | ort            |
+---------+---------------+-------+----------------+
| Ulrich  | Blotzek       | 59823 | Arnsberg       |
| Paula   | David         |  9020 | Klagenfurt     |
| Ahvo    | Hämäläinen    | 30100 | Forssa         |
| Joseph  | Hardiff       |  9200 | Klagenfurt     |
| Fenna   | Huisman       |  1315 | Almere         |
| Lieke   | Prins         |  4600 | Bergen op Zoom |
| Peter   | Schatter      | 86179 | Augsburg       |
| Veera   | Virtanen      |  2150 | Espoo          |
| Albert  | Wojack        | 12234 | Berlin         |
+---------+---------------+-------+----------------+
```

5. Lassen Sie sich in der angegebenen Reihenfolge den Nachnamen, den Wohnort, PLZ sowie das Land aller Personen anzeigen. Verwenden Sie in der Ergebnistabelle den Spaltennamen: Name, Land, Wohnort und Postleitzahl.
```SQL
SELECT nachname AS Name, ort AS Wohnort, plz AS Postleitzahl, land AS Land
FROM person;
```
```
+---------------+----------------+--------------+-------------+
| Name          | Wohnort        | Postleitzahl | Land        |
+---------------+----------------+--------------+-------------+
| Blotzek       | Arnsberg       |        59823 | Deutschland |
| Schatter      | Augsburg       |        86179 | Deutschland |
| Wojack        | Berlin         |        12234 | Deutschland |
| Virtanen      | Espoo          |         2150 | Finnland    |
| Hämäläinen    | Forssa         |        30100 | Finnland    |
| Huisman       | Almere         |         1315 | Niederlande |
| Prins         | Bergen op Zoom |         4600 | Niederlande |
| David         | Klagenfurt     |         9020 | Österreich  |
| Hardiff       | Klagenfurt     |         9200 | Österreich  |
+---------------+----------------+--------------+-------------+
```

## 2. Abfragen mit einfachen Aggregat-Funktionen

#### Berechnungen mit den in der Datenbank gespeicherten Werten. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich alle Artikeldaten anzeigen.
```SQL
SELECT * FROM artikel;
```
```
+---------------+------------------+-------------+--------+
| artikelnummer | herstellernummer | artikelname | preis  |
+---------------+------------------+-------------+--------+
|             1 |               10 | Maus        |  10.00 |
|             2 |               10 | Tastatur    |  20.00 |
|             3 |               50 | Drucker     | 300.00 |
|             4 |               30 | Festplatte  | 400.00 |
|             5 |               20 | Monitor     | 500.00 |
+---------------+------------------+-------------+--------+
```

2. Lassen Sie sich alle Artikelnamen, die dazugehörigen Preise (Netto) und die Preise mit einem Aufschlag von 19% (Brutto) anzeigen. Benennen Sie in der Ausgabe die entsprechenden Tabellenspalten Artikel, Nettopreis und Bruttopreis.
```SQL
SELECT artikelname AS Artikel, preis AS Nettopreis, preis + (preis * 19/100) AS Bruttopreis
FROM artikel;
```
```
+------------+------------+-------------+
| Artikel    | Nettopreis | Bruttopreis |
+------------+------------+-------------+
| Maus       |      10.00 |   11.900000 |
| Tastatur   |      20.00 |   23.800000 |
| Drucker    |     300.00 |  357.000000 |
| Festplatte |     400.00 |  476.000000 |
| Monitor    |     500.00 |  595.000000 |
+------------+------------+-------------+
```

3. Welche Bestellsumme pro Artikel entsteht, wenn Sie von jedem Artikel 50 Stück bestellen. Lassen Sie sich Artikelname, Einzelpreis und Gesamtpreis anzeigen. Benennen Sie die entsprechenden Tabellenspalten Artikel, Einzelpreis, Gesamtpreis.
```SQL
SELECT artikelname AS Artikel, preis AS Einzelpreis, preis * 50 AS Gesamtpreis
FROM artikel;
```
```
+------------+-------------+-------------+
| Artikel    | Einzelpreis | Gesamtpreis |
+------------+-------------+-------------+
| Maus       |       10.00 |      500.00 |
| Tastatur   |       20.00 |     1000.00 |
| Drucker    |      300.00 |    15000.00 |
| Festplatte |      400.00 |    20000.00 |
| Monitor    |      500.00 |    25000.00 |
+------------+-------------+-------------+
```

## 3. Abfragen mit logischen Operatoren

#### WHERE-Klausel und Vergleichsoperationen: Ergebnismenge auf relevanten Datensätze begrenzen. Abfragen mit der Tabelle 'person'.

1. Lassen Sie sich die Personendaten aller Personen anzeigen, die in Berlin wohnen.
```SQL
SELECT * FROM person
WHERE ort = 'Berlin';
```
```
+----------------+----------+---------+-------------------+--------+-------+-------------+--------------+
| personennummer | nachname | vorname | strasse           | ort    | plz   | land        | geburtsdatum |
+----------------+----------+---------+-------------------+--------+-------+-------------+--------------+
|              3 | Wojack   | Albert  | Westendstrasse 92 | Berlin | 12234 | Deutschland | 1955-06-15   |
+----------------+----------+---------+-------------------+--------+-------+-------------+--------------+
```

2. Lassen Sie sich die Vornamen, Nachnamen und Wohnorte aller Personen anzeigen, die entweder in Berlin oder in Klagenfurt wohnen.
```SQL
SELECT vorname, nachname, ort
FROM person
WHERE ort = 'Berlin' OR ort = 'Klagenfurt';
```
```
+---------+----------+------------+
| vorname | nachname | ort        |
+---------+----------+------------+
| Albert  | Wojack   | Berlin     |
| Paula   | David    | Klagenfurt |
| Joseph  | Hardiff  | Klagenfurt |
+---------+----------+------------+
```

3. Lassen Sie sich die Vornamen, Nachnamen und Wohnorte aller Personen anzeigen, die nicht in Berlin wohnen.
```SQL
SELECT vorname, nachname, ort
FROM person
WHERE NOT ort = 'Berlin';
```
```
+---------+---------------+----------------+
| vorname | nachname      | ort            |
+---------+---------------+----------------+
| Ulrich  | Blotzek       | Arnsberg       |
| Peter   | Schatter      | Augsburg       |
| Veera   | Virtanen      | Espoo          |
| Ahvo    | Hämäläinen    | Forssa         |
| Fenna   | Huisman       | Almere         |
| Lieke   | Prins         | Bergen op Zoom |
| Paula   | David         | Klagenfurt     |
| Joseph  | Hardiff       | Klagenfurt     |
+---------+---------------+----------------+
```

4. Lassen Sie sich die Nachnamen, Wohnorte und Geburtsdaten aller Personen anzeigen, die in Deutschland wohnen und nach dem 01.06.1960 geboren worden sind.
```SQL
SELECT nachname, ort, geburtsdatum
FROM person
WHERE land = 'Deutschland' AND geburtsdatum > '1960-06-01';
```
```
+----------+----------+--------------+
| nachname | ort      | geburtsdatum |
+----------+----------+--------------+
| Blotzek  | Arnsberg | 1960-10-05   |
| Schatter | Augsburg | 1980-01-01   |
+----------+----------+--------------+
```

## 4. Abfragen mit mathematischen und statischen Funktionen anwenden

#### Mathematische und statistische Funktionen. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich von allen Artikeln, die mehr als 300 kosten, den Artikelnamen, den Preis und einen um 20 % erhöhten Preis ausgeben. Runden Sie den berechneten Preis auf zwei Nachkommastellen. Nennen Sie die Tabellenspalten der Ergebnistabelle Artikel, Nettopreis und Neupreis.
```SQL
SELECT artikelname AS Artikel, preis AS Nettopreis, ROUND(preis + (preis * 20/100), 2) AS Neupreis
FROM artikel
WHERE preis > 300 ;
```
```
+------------+------------+----------+
| Artikel    | Nettopreis | Neupreis |
+------------+------------+----------+
| Festplatte |     400.00 |   480.00 |
| Monitor    |     500.00 |   600.00 |
+------------+------------+----------+
```

2. Ermitteln Sie den durchschnittlichen Preis von Tastatur, Drucker und Festplatte. Nennen Sie die Tabellenspalte der Ergebnistabelle Durchschnittspreis.
```SQL
SELECT AVG(preis) AS Durchschnittspreis
FROM artikel
WHERE artikelname = 'Tastatur' OR artikelname = 'Drucker' OR artikelname = 'Festplatte';
```
```
+--------------------+
| Durchschnittspreis |
+--------------------+
|         240.000000 |
+--------------------+
```

3. Ermitteln Sie die Anzahl aller Artikel, die vom Hersteller mit der Herstellernummer 10 angeboten werden. Nennen Sie die Tabellenspalte der Ergebnistabelle Artikelanzahl.
```SQL
SELECT COUNT(artikelnummer) AS Artikelanzahl
FROM artikel
WHERE herstellernummer = 10;
```
```
+---------------+
| Artikelanzahl |
+---------------+
|             2 |
+---------------+
```

4. Ermitteln Sie den Gesamtpreis, wenn Sie jeweils 5 Artikel des Herstellers mit der Herstellernummer 10 kaufen würden. Nennen Sie die Tabellenspalte der Ergebnistabelle Gesamtpreis.
```SQL
SELECT SUM(preis * 5) AS Gesamtpreis
FROM artikel
WHERE herstellernummer = 10;
```
```
+-------------+
| Gesamtpreis |
+-------------+
|      150.00 |
+-------------+
```

5. Ermitteln Sie den billigsten und den teuersten Artikel. Nennen Sie die Tabellenspalten der Ergebnistabelle Billig und Teuer.
```SQL
SELECT MIN(preis) AS Billig, MAX(preis) AS Teuer
FROM artikel;
```
```
+--------+--------+
| Billig | Teuer  |
+--------+--------+
|  10.00 | 500.00 |
+--------+--------+
```

## 5. Abfragen mit dem Vergleich von Zeichenketten

#### IN, BETWEEN und LIKE Operatoren. Abfragen mit der Tabelle 'artikel'.

1. Lassen Sie sich bis auf die Artikelnummer alle Artikeldaten der Hersteller mit der Herstellernummer 10, 30 und 50 anzeigen.
```SQL
SELECT herstellernummer, artikelname, preis
FROM artikel
WHERE herstellernummer IN (10, 30, 50);
```
```
+------------------+-------------+--------+
| herstellernummer | artikelname | preis  |
+------------------+-------------+--------+
|               10 | Maus        |  10.00 |
|               10 | Tastatur    |  20.00 |
|               30 | Festplatte  | 400.00 |
|               50 | Drucker     | 300.00 |
+------------------+-------------+--------+
```

2. Lassen Sie sich alle Artikelnamen und die dazugehörigen Artikelpreise ausgeben, die zwischen 200 und 400 liegen.
```SQL
SELECT artikelname, preis
FROM artikel
WHERE preis BETWEEN 200 AND 400;
```
```
+-------------+--------+
| artikelname | preis  |
+-------------+--------+
| Drucker     | 300.00 |
| Festplatte  | 400.00 |
+-------------+--------+
```

3. Lassen Sie sich alle Artikelnamen und dazugehörigen Artikelpreise ausgeben, deren Name mit dem Buchstaben M beginnt.
```SQL
SELECT artikelname, preis
FROM artikel
WHERE artikelname LIKE 'M%';
```
```
+-------------+--------+
| artikelname | preis  |
+-------------+--------+
| Maus        |  10.00 |
| Monitor     | 500.00 |
+-------------+--------+
```

#### Abfragen mit der Tabelle 'hersteller' aus.

4. Lassen Sie sich die Herstellernamen und die dazugehörigen Länder anzeigen.
```SQL
SELECT herstellername, land
FROM hersteller;
```
```
+-----------------+-------------+
| herstellername  | land        |
+-----------------+-------------+
| Logitech        | Schweiz     |
| SONY            | Japan       |
| Maxtor          | USA         |
| Medion          | Deutschland |
| Hewlett Packard | USA         |
+-----------------+-------------+
```

5. Lassen Sie sich alle Herstellernamen und die dazugehörigen Länder anzeigen, die mit dem Buchstaben M beginnen und nicht aus Japan sind.
```SQL
SELECT herstellername, land
FROM hersteller
WHERE herstellername LIKE 'M%' AND NOT land = 'Japan';
```
```
+----------------+-------------+
| herstellername | land        |
+----------------+-------------+
| Maxtor         | USA         |
| Medion         | Deutschland |
+----------------+-------------+
```

6. Lassen Sie sich alle Herstellernamen und die dazugehörigen Länder anzeigen, die nicht mit dem Buchstaben M beginnen und entweder aus Deutschland oder den USA sind.
```SQL
SELECT herstellername, land
FROM hersteller
WHERE herstellername NOT LIKE 'M%' AND land IN ('Deutschland', 'USA');
```
```
+-----------------+------+
| herstellername  | land |
+-----------------+------+
| Hewlett Packard | USA  |
+-----------------+------+
```

## 6. Abfragen mit Zeichenketten- und Datumsfunktion

#### Anwendung von Zeichenketten- und Datumsfunktionen. Abfragen mit der Tabelle 'person'.

1. Geben Sie in jeweils einer Spalte einer Ergebnistabelle den Namen einer Person bestehend aus Vornamen und Nachnamen sowie die Anschrift bestehend aus Postleitzahl und Ort aus. Fügen Sie in der Ausgabe zwischen Vornamen und Nachnamen sowie zwischen Postleitzahl und Ort ein Leerzeichen ein. Nennen Sie die Spalten der Ergebnistabelle Name und Anschrift.
```SQL
SELECT CONCAT(vorname, ' ', nachname) AS Name, CONCAT(plz, ' - ', ort) AS Anschrift
FROM person;
```
```
+--------------------+-----------------------+
| Name               | Anschrift             |
+--------------------+-----------------------+
| Ulrich Blotzek     | 59823 - Arnsberg      |
| Peter Schatter     | 86179 - Augsburg      |
| Albert Wojack      | 12234 - Berlin        |
| Veera Virtanen     | 2150 - Espoo          |
| Ahvo Hämäläinen    | 30100 - Forssa        |
| Fenna Huisman      | 1315 - Almere         |
| Lieke Prins        | 4600 - Bergen op Zoom |
| Paula David        | 9020 - Klagenfurt     |
| Joseph Hardiff     | 9200 - Klagenfurt     |
+--------------------+-----------------------+
```

2. Ermitteln Sie die Länge aller Ortsnamen und geben Sie Ortsnamen und Länge in einer Ergebnistabelle aus. Nennen Sie die Spalten der Ergebnistabelle Ortsname und Ortsnamenlänge. Unterdrücken Sie die Mehrfachanzeige identischer Ortsangaben.
```SQL
SELECT ort AS Ortsname, LENGTH(ort) AS Ortsnamenlänge
FROM person;
```
```
+----------------+-----------------+
| Ortsname       | Ortsnamenlänge  |
+----------------+-----------------+
| Arnsberg       |               8 |
| Augsburg       |               8 |
| Berlin         |               6 |
| Espoo          |               5 |
| Forssa         |               6 |
| Almere         |               6 |
| Bergen op Zoom |              14 |
| Klagenfurt     |              10 |
| Klagenfurt     |              10 |
+----------------+-----------------+
```

3. Ermitteln Sie das Alter aller Personen der Tabelle 'person'. Lassen Sie sich das Alter, den Vornamen, den Nachnamen und das Geburtsdatum jeder Person anzeigen. Nennen Sie die Spalte der Ergebnistabelle, die die Altersangaben enthält, Lebensalter.
```SQL
SELECT vorname AS Vorname, nachname AS Nachname, geburtsdatum AS Geburtsdatum, TIMESTAMPDIFF(YEAR, geburtsdatum, CURRENT_DATE()) AS Lebensalter
FROM person;
```
```
+---------+---------------+--------------+-------------+
| Vorname | Nachname      | Geburtsdatum | Lebensalter |
+---------+---------------+--------------+-------------+
| Ulrich  | Blotzek       | 1960-10-05   |          63 |
| Peter   | Schatter      | 1980-01-01   |          44 |
| Albert  | Wojack        | 1955-06-15   |          68 |
| Veera   | Virtanen      | 1992-12-30   |          31 |
| Ahvo    | Hämäläinen    | 1977-04-23   |          46 |
| Fenna   | Huisman       | 1971-08-17   |          52 |
| Lieke   | Prins         | 1987-05-08   |          36 |
| Paula   | David         | 1970-01-21   |          54 |
| Joseph  | Hardiff       | 1962-08-09   |          61 |
+---------+---------------+--------------+-------------+
```

## 7. Abfragen mit Gruppierung von Datenmengen

#### Aus allen Bestellungen der Tabelle 'bestellung' die Anzahl der Bestellungen für jeden Artikel und die daraus resultierende Gesamtbestellsumme pro Artikel ermitteln. Nur Gesamtbestellsummen, die größer als 200 sind, dabei berücksichtigen. Artikelnummer, die Anzahl der Bestellungen eines Artikels sowie die Gesamtbestellsumme anzeigen lassen. Die Spalten der Ergebnistabelle Artikelnummer, Artikelanzahl und Gesamtbestellsumme nennen. Gruppierung nutzen.
```SQL
SELECT artikelnummer AS Artikelnummer, SUM(artikelanzahl) AS Artikelanzahl, SUM(bestellsumme) AS Gesamtbestellsumme
FROM bestellung
GROUP BY artikelnummer
HAVING SUM(bestellsumme) > 200;
```
```
+---------------+---------------+--------------------+
| Artikelnummer | Artikelanzahl | Gesamtbestellsumme |
+---------------+---------------+--------------------+
|             3 |             1 |             300.00 |
|             5 |             5 |            2500.00 |
+---------------+---------------+--------------------+
```


#### Aus allen Artikeln der Tabelle 'artikel' den Durchschnittspreis aller Artikel eines Herstellers ermitteln. Nur die Hersteller, die mehrere Artikel anbieten, dabei berücksichtigen. Die Herstellernummer und den Durchschnittspreis anzeigen lassen. Die Spalten der Ergebnistabelle Herstellernummer und Durchschnittspreis nennen. Gruppierung nutzen.
```SQL
SELECT herstellernummer AS Herstellernummer, ROUND(AVG(preis), 2) AS Durchschnittspreis
FROM artikel
GROUP BY herstellernummer
HAVING COUNT(*) > 1;
```
```
+------------------+--------------------+
| Herstellernummer | Durchschnittspreis |
+------------------+--------------------+
|               10 |              15.00 |
+------------------+--------------------+
```

## 8. Abfragen über mehrere Tabellen und Unterabfragen erstellen

#### Abfragen mit den Tabellen 'artikel' und 'hersteller'.

1. Lassen Sie sich alle Artikelnamen und alle dazugehörigen Informationen über den Artikelhersteller, sortiert nach Artikelnamen, anzeigen. Benutzen Sie zur Tabellenverknüpfung die WHERE-Klausel. Benutzen Sie außerdem den Aliasnamen a für die Tabelle 'artikel' und den Aliasnamen h für die Tabelle 'hersteller'.
```SQL
SELECT a.artikelname AS Artikelname, h.herstellernummer AS Herstellernummer, h.herstellername AS Hersteller, h.land AS Herstellungsland
FROM artikel AS a, hersteller AS h
WHERE h.herstellernummer = a.herstellernummer
GROUP BY a.artikelname, h.herstellernummer
ORDER BY h.herstellernummer;
```
```
+-------------+------------------+-----------------+------------------+
| Artikelname | Herstellernummer | Hersteller      | Herstellungsland |
+-------------+------------------+-----------------+------------------+
| Maus        |               10 | Logitech        | Schweiz          |
| Tastatur    |               10 | Logitech        | Schweiz          |
| Monitor     |               20 | SONY            | Japan            |
| Festplatte  |               30 | Maxtor          | USA              |
| Drucker     |               50 | Hewlett Packard | USA              |
+-------------+------------------+-----------------+------------------+
```

2. Lassen Sie sich alle Namen, Preise und die zugehörigen Hersteller für Artikel anzeigen, deren Preis höher als 200 ist. Nutzen Sie für die Tabellenverknüpfung die JOIN-Klausel. Benutzen Sie außerdem den Aliasnamen a für die Tabelle 'artikel' und den Aliasnamen h für die Tabelle 'hersteller'.
```SQL
SELECT a.artikelname AS Artikelname, h.herstellernummer AS Herstellernummer, h.herstellername AS Hersteller, h.land AS Herstellungsland, a.preis AS Preis
FROM hersteller AS h
INNER JOIN artikel AS a ON h.herstellernummer = a.herstellernummer
WHERE a.preis > 200
GROUP BY a.artikelname, a.preis, h.herstellernummer
ORDER BY h.herstellernummer;
```
```
+-------------+------------------+-----------------+------------------+--------+
| Artikelname | Herstellernummer | Hersteller      | Herstellungsland | Preis  |
+-------------+------------------+-----------------+------------------+--------+
| Monitor     |               20 | SONY            | Japan            | 500.00 |
| Festplatte  |               30 | Maxtor          | USA              | 400.00 |
| Drucker     |               50 | Hewlett Packard | USA              | 300.00 |
+-------------+------------------+-----------------+------------------+--------+
```

#### Abfragen mit den Tabellen 'person', 'artikel', 'hersteller' und 'bestellung'.

3. Lassen Sie sich zu jedem Bestellvorgang in der angegebenen Reihenfolge folgende Daten anzeigen: Bestellnummer, Nachname und Vorname des Kunden, Artikelanzahl und Bestellsumme.
```SQL
SELECT b.bestellnummer AS Bestellnummer, p.nachname AS Nachname, p.vorname AS Vorname, b.artikelanzahl AS Artikelanzahl, b.bestellsumme AS Bestellsumme
FROM bestellung AS b
INNER JOIN person AS p ON b.kundennummer = p.personennummer
ORDER BY b.bestellnummer;
```
```
+---------------+---------------+---------+---------------+--------------+
| Bestellnummer | Nachname      | Vorname | Artikelanzahl | Bestellsumme |
+---------------+---------------+---------+---------------+--------------+
|             1 | Virtanen      | Veera   |             2 |        20.00 |
|             2 | Blotzek       | Ulrich  |             1 |        20.00 |
|             3 | Schatter      | Peter   |             3 |        30.00 |
|             4 | Wojack        | Albert  |             1 |       300.00 |
|             5 | Hämäläinen    | Ahvo    |             5 |      2500.00 |
+---------------+---------------+---------+---------------+--------------+
```

4. Welche Kunden haben mehr als 2 Artikel bestellt? Lassen Sie sich die Bestellnummer, Vor- und Nachname des Kunden, Artikelname, Artikelanzahl und Artikelpreis anzeigen.
```SQL
SELECT b.bestellnummer AS Bestellnummer, p.vorname AS Vorname, p.nachname AS Nachname, b.artikelanzahl AS Artikelanzahl, a.preis AS Artikelpreis
FROM bestellung AS b
INNER JOIN person AS p ON b.kundennummer = p.personennummer
INNER JOIN artikel AS a ON b.artikelnummer = a.artikelnummer
GROUP BY b.artikelanzahl, b.bestellnummer
HAVING b.artikelanzahl > 2
ORDER BY b.bestellnummer;
```
```
+---------------+---------+---------------+---------------+--------------+
| Bestellnummer | Vorname | Nachname      | Artikelanzahl | Artikelpreis |
+---------------+---------+---------------+---------------+--------------+
|             3 | Peter   | Schatter      |             3 |        10.00 |
|             5 | Ahvo    | Hämäläinen    |             5 |       500.00 |
+---------------+---------+---------------+---------------+--------------+
```

5. Welche Kunden haben Artikel bestellt, die in Japan hergestellt werden? Lassen Sie sich Nachname und Vorname des Kunden, Artikelname, Herstellername sowie das Herstellerland anzeigen.
```SQL
SELECT p.nachname AS Nachname, p.vorname AS Vorname, a.artikelname AS Artikelname, h.herstellername AS Herstellername, h.land AS Herstellerland
FROM bestellung AS b
INNER JOIN person AS p ON b.kundennummer = p.personennummer
INNER JOIN artikel AS a ON b.artikelnummer = a.artikelnummer
INNER JOIN hersteller AS h ON a.herstellernummer
WHERE h.land = 'Japan';
```
```
+---------------+---------+-------------+----------------+----------------+
| Nachname      | Vorname | Artikelname | Herstellername | Herstellerland |
+---------------+---------+-------------+----------------+----------------+
| Virtanen      | Veera   | Maus        | SONY           | Japan          |
| Blotzek       | Ulrich  | Tastatur    | SONY           | Japan          |
| Schatter      | Peter   | Maus        | SONY           | Japan          |
| Wojack        | Albert  | Drucker     | SONY           | Japan          |
| Hämäläinen    | Ahvo    | Monitor     | SONY           | Japan          |
+---------------+---------+-------------+----------------+----------------+
```

6. Überprüfen Sie, ob Kunden aus Forssa Geräte von einem Hersteller aus Japan bestellt haben. Lassen Sie sich Nachname, Vorname und Wohnort des Kunden, den Artikelnamen sowie das Herstellerland anzeigen.
```SQL
SELECT p.nachname AS Nachname, p.vorname AS Vorname, p.ort AS Wohnort, a.artikelname AS Artikelname, h.land AS Herstellerland
FROM bestellung AS b
INNER JOIN person AS p ON b.kundennummer = p.personennummer
INNER JOIN artikel AS a ON b.artikelnummer = a.artikelnummer
INNER JOIN hersteller AS h ON a.herstellernummer
WHERE p.ort = 'Forssa' AND h.land = 'Japan';
```
```
+---------------+---------+---------+-------------+----------------+
| Nachname      | Vorname | Wohnort | Artikelname | Herstellerland |
+---------------+---------+---------+-------------+----------------+
| Hämäläinen    | Ahvo    | Forssa  | Monitor     | Japan          |
+---------------+---------+---------+-------------+----------------+
```

7. Lassen Sie sich die vollständigen Daten aller Kunden anzeigen, die einen Artikel
vom Hersteller Logitech bestellt haben.
```SQL
SELECT p.* FROM person AS p
INNER JOIN bestellung AS b ON b.kundennummer = p.personennummer
INNER JOIN artikel AS a ON b.artikelnummer = a.artikelnummer
INNER JOIN hersteller AS h ON a.herstellernummer
WHERE h.herstellername = 'Logitech';
```
```
+----------------+---------------+---------+--------------------+----------+-------+-------------+--------------+
| personennummer | nachname      | vorname | strasse            | ort      | plz   | land        | geburtsdatum |
+----------------+---------------+---------+--------------------+----------+-------+-------------+--------------+
|              4 | Virtanen      | Veera   | Oyi Keilasatama 21 | Espoo    |  2150 | Finnland    | 1992-12-30   |
|              1 | Blotzek       | Ulrich  | Großkopf 4         | Arnsberg | 59823 | Deutschland | 1960-10-05   |
|              2 | Schatter      | Peter   | Försterstrasse 56  | Augsburg | 86179 | Deutschland | 1980-01-01   |
|              3 | Wojack        | Albert  | Westendstrasse 92  | Berlin   | 12234 | Deutschland | 1955-06-15   |
|              5 | Hämäläinen    | Ahvo    | Tapulikuja 56      | Forssa   | 30100 | Finnland    | 1977-04-23   |
+----------------+---------------+---------+--------------------+----------+-------+-------------+--------------+
```

#### Abfragen mithilfe von Unterabfragen.

1. Ermitteln Sie aus der Tabelle 'person' den Nachnamen und das Geburtsdatum der jüngsten Person. Nennen Sie die Spalten der Ergebnistabelle Name und Geburtsdatum.
```SQL
SELECT nachname AS Nachname, vorname AS Vorname, geburtsdatum AS Geburtsdatum
FROM person
WHERE geburtsdatum = (SELECT MAX(geburtsdatum) FROM person);
```
```
+----------+---------+--------------+
| Nachname | Vorname | Geburtsdatum |
+----------+---------+--------------+
| Virtanen | Veera   | 1992-12-30   |
+----------+---------+--------------+
```

2. Ermitteln Sie aus der Tabelle 'artikel' den Namen und den Preis des billigsten Artikels. Nennen Sie die Spalten der Ergebnistabelle Artikel und Preis.
```SQL
SELECT artikelname AS Artikel, preis AS Preis
FROM artikel
WHERE preis = (SELECT MIN(preis) FROM artikel);
```
```
+---------+-------+
| Artikel | Preis |
+---------+-------+
| Maus    | 10.00 |
+---------+-------+
```

3. Ermitteln Sie mithilfe der Tabellen 'bestellung', 'artikel' und 'person' die Bestellung mit der höchsten Bestellsumme. Lassen Sie sich den dazugehörigen Nachnamen des Kunden, den Artikelnamen und die Bestellsumme anzeigen. Nennen Sie die Spalten der Ergebnistabelle Name, Artikel und Bestellsumme.
```SQL
SELECT p.nachname AS Name, a.artikelname AS Artikel, b.bestellsumme AS Bestellsumme FROM person AS p
INNER JOIN bestellung AS b ON b.kundennummer = p.personennummer
INNER JOIN artikel AS a ON b.artikelnummer = a.artikelnummer
WHERE b.bestellsumme = (SELECT MAX(bestellsumme) FROM bestellung);
```
```
+---------------+---------+--------------+
| Name          | Artikel | Bestellsumme |
+---------------+---------+--------------+
| Hämäläinen    | Monitor |      2500.00 |
+---------------+---------+--------------+
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
