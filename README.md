# Daten mit SQL-Abfragen anzeigen und filtern

## Projektbeschreibung

Dieses Projekt ist Teil des [Google Cybersecurity Professional Certificate](https://www.coursera.org/professional-certificates/google-cybersecurity). In diesem Projekt bin ich als Cybersecurity Analyst für ein fiktives Unternehmen tätig, das daran arbeitet, seine IT-Systeme sicherer zu machen. Meine Aufgabe besteht darin, sicherzustellen, dass die Systeme sicher sind, alle potenziellen Sicherheitsprobleme zu untersuchen und die Computer der Mitarbeiter bei Bedarf zu aktualisieren. Die folgenden Schritte sind Beispiele dafür, wie ich SQL-Abfragen mit Filtern verwendet habe, um die Aufgaben zur IT-Sicherheit auszuführen.

## Fehlgeschlagene Anmeldeversuche nach Dienstschluss anzeigen

Ein potenzieller Sicherheitsvorfall ist nach Dienstschluss (nach 18:00 Uhr) aufgetreten. Daher müssen alle fehlgeschlagenen Anmeldeversuche nach Dienstschluss untersucht werden.

Der folgende Code zeigt, wie ich eine SQL-Abfrage erstellt habe, um nach fehlgeschlagenen Anmeldeversuchen zu filtern, die nach Dienstschluss stattgefunden haben.

![SQL_Queries_1](https://github.com/laresd/Apply_filters_to_SQL_queries/assets/53877625/18782cfd-8759-40df-92e1-4874ce242094)

Der erste Teil des Screenshots zeigt meine SQL-Abfrage, der zweite Teil einen Teil der Ausgabe. Diese Abfrage filtert nach fehlgeschlagenen Anmeldeversuchen, die nach 18:00 Uhr stattgefunden haben. Zuerst habe ich alle Daten aus der Tabelle `log_in_attempts` ausgewählt. Dann habe ich eine `WHERE`-Klausel mit einem `AND`-Operator verwendet, um die Ergebnisse so zu filtern, dass nur Anmeldeversuche ausgegeben werden, die nach 18:00 Uhr stattgefunden haben und fehlgeschlagen sind. Die erste Bedingung ist `login_time > '18:00'`, wodurch alle Anmeldeversuche herausgefiltert werden, die nach 18:00 Uhr stattgefunden haben. Die zweite Bedingung ist `success = FALSE`, wodurch fehlgeschlagene Anmeldeversuche herausgefiltert werden.

## Anmeldeversuche nach Datum gefiltert anzeigen

Am 09.05.2022 ist ein verdächtiges Ereignis aufgetreten. Alle Anmeldeaktivitäten, die am 09.05.2022 oder am Tag davor stattgefunden haben, müssen untersucht werden.

Der folgende Code zeigt, wie ich eine SQL-Abfrage erstellt habe, um nach Anmeldeversuchen zu filtern, die an bestimmten Tagen stattgefunden haben.

![SQL_Queries_2](https://github.com/laresd/Apply_filters_to_SQL_queries/assets/53877625/24345777-9799-4294-aa8f-9841724429ed)

Der erste Teil des Screenshots zeigt meine SQL-Abfrage, der zweite Teil einen Teil der Ausgabe. Diese Abfrage gibt alle Anmeldeversuche zurück, die am 09.05.2022 oder am 08.05.2022 stattgefunden haben. Zuerst habe ich alle Daten aus der Tabelle `log_in_attempts` ausgewählt. Dann habe ich eine `WHERE`-Klausel mit einem `OR`-Operator verwendet, um meine Ergebnisse so zu filtern, dass nur Anmeldeversuche ausgegeben werden, die entweder am 09.05.2022 oder am 08.05.2022 stattgefunden haben. Die erste Bedingung ist `login_date = '2022-05-09'`, was nach Anmeldungen am 09.05.2022 filtert. Die zweite Bedingung ist `login_date = '2022-05-08'`, die nach Anmeldungen am 08.05.2022 filtert.

## Anmeldeversuche außerhalb von Mexiko anzeigen

Nach Überprüfung der Daten des Unternehmens zu den Anmeldeversuchen hat sich herausgestellt, dass es ein Problem mit den Anmeldeversuchen gibt, die außerhalb Mexikos stattgefunden haben. Diese Anmeldeversuche müssen weiter untersucht werden.

Der folgende Code zeigt, wie ich eine SQL-Abfrage erstellt habe, um die Anmeldeversuche außerhalb von Mexiko herauszufiltern.

![SQL_Queries_3](https://github.com/laresd/Apply_filters_to_SQL_queries/assets/53877625/ff8ed73a-9515-4e41-92d0-29dbd65d37d0)

Der erste Teil des Screenshots zeigt meine SQL-Abfrage, der zweite Teil einen Teil der Ausgabe. Diese Abfrage gibt alle Anmeldeversuche zurück, die in anderen Ländern als Mexiko stattgefunden haben. Zuerst habe ich alle Daten aus der Tabelle `log_in_attempts` ausgewählt. Dann habe ich eine `WHERE`-Klausel mit dem `NOT`-Operator verwendet, um nach anderen Ländern als Mexiko zu filtern. Zusätzlich habe ich den `LIKE`-Operator mit `MEX%` als Suchmuster verwendet, da im Datensatz das Land Mexiko sowohl mit `MEX` als auch mit `MEXICO` angegeben ist. Das Prozentzeichen (`%`) dient als Platzhalter und steht in Verbindung mit dem `LIKE`-Operator für eine beliebige Anzahl von Zeichen.

## Mitarbeiter aus der Marketingabteilung anzeigen

Mein Team möchte die Computer einiger Mitarbeiter aus der Marketingabteilung aktualisieren. Dazu benötige ich Informationen darüber, welche Computer der Mitarbeiter aktualisiert werden sollen.

Der folgende Code zeigt, wie ich eine SQL-Abfrage erstellt habe, um die Computer der Mitarbeiter der Marketingabteilung im Ostgebäude herauszufiltern.

![SQL_Queries_4](https://github.com/laresd/Apply_filters_to_SQL_queries/assets/53877625/7cd2f5e1-a0b8-4fb5-b605-d4ff3a60a756)

Der erste Teil des Screenshots zeigt meine SQL-Abfrage, der zweite Teil einen Teil der Ausgabe. Diese Abfrage gibt alle Mitarbeiter der Marketingabteilung im Ostgebäude zurück. Zuerst habe ich alle Daten aus der Tabelle `employees` ausgewählt. Dann habe ich eine `WHERE`-Klausel mit einem `AND`-Operator verwendet, um nach Mitarbeitern zu filtern, die in der Marketingabteilung und im Ostgebäude arbeiten. Zusätzlich habe ich den `LIKE`-Operator mit `East%` als Suchmuster verwendet, da die Daten in der Spalte `office` das jeweilige Bürogebäude mit der zugehörigen Raumnummer angeben (z. B. `East-170`). Die erste Bedingung ist der Teil `department = 'Marketing'`, der nach Mitarbeitern in der Marketingabteilung filtert. Die zweite Bedingung ist der Teil `office LIKE 'East%'`, der nach Mitarbeitern im Ostgebäude filtert.

## Mitarbeiter aus der Finanz- oder Vertriebsabteilung anzeigen

Die Computer der Mitarbeiter in den Abteilungen Finanzen und Vertrieb müssen ebenfalls aktualisiert werden. Da ein anderes Sicherheitsupdate erforderlich ist, brauche ich nur Informationen über die Mitarbeiter dieser beiden Abteilungen.

Der folgende Code zeigt, wie ich eine SQL-Abfrage erstellt habe, um nach den Computern der Mitarbeiter in den Abteilungen Finanzen und Vertrieb zu filtern.

![SQL_Queries_5](https://github.com/laresd/Apply_filters_to_SQL_queries/assets/53877625/db267f0e-edd4-446f-8334-2e5a409c7253)

Der erste Teil des Screenshots zeigt meine SQL-Abfrage, der zweite Teil einen Teil der Ausgabe. Diese Abfrage gibt alle Mitarbeiter in den Abteilungen Finanzen und Vertrieb zurück. Zuerst habe ich alle Daten aus der Tabelle `employees` ausgewählt. Dann habe ich eine `WHERE`-Klausel mit einem `OR`-Operator verwendet, um nach Mitarbeitern zu filtern, die in den Abteilungen Finanzen und Vertrieb arbeiten. Zusätzlich habe ich den `OR`-Operator anstelle des `AND`-Operators verwendet, um alle Mitarbeiter anzuzeigen, die in einer der beiden Abteilungen arbeiten. Die erste Bedingung ist `department = 'Finance'`, wodurch die Mitarbeiter aus der Finanzabteilung herausgefiltert werden. Die zweite Bedingung ist `department = 'Sales'`, die nach Mitarbeitern der Vertriebsabteilung filtert.

## Alle Mitarbeiter anzeigen, die nicht in der IT-Abteilung arbeiten

Mein Team muss ein weiteres Sicherheitsupdate für Mitarbeiter durchführen, die nicht zur IT-Abteilung gehören. Um das Update durchführen zu können, muss ich zunächst Informationen über die betroffenen Mitarbeiter sammeln.

Der folgende Code zeigt, wie ich eine SQL-Abfrage erstellt habe, um die Computer von Mitarbeitern herauszufiltern, die nicht zur IT-Abteilung des Unternehmens gehören.

![SQL_Queries_6](https://github.com/laresd/Apply_filters_to_SQL_queries/assets/53877625/62fe7ff7-acd6-4431-880e-bc96e97b45a5)

Der erste Teil des Screenshots zeigt meine SQL-Abfrage, der zweite Teil einen Teil der Ausgabe. Die Abfrage gibt alle Mitarbeiter zurück, die nicht zur IT-Abteilung gehören. Zuerst habe ich alle Daten aus der Tabelle `employees` ausgewählt. Dann habe ich eine `WHERE`-Klausel mit dem `NOT`-Operator verwendet, um nach Mitarbeitern zu filtern, die nicht in der IT-Abteilung arbeiten.

## Zusammenfassung

In diesem Projekt ging es um die Verwendung von Filtern in SQL-Abfragen, um bestimmte Informationen über die Anmeldeversuche und die Computer von Mitarbeitern zu erhalten. Um die Daten abzufragen, habe ich auf zwei verschiedene Tabellen zugegriffen, `log_in_attempts` und `employees`. In den SQL-Abfragen habe ich die Operatoren `AND`, `OR` und `NOT` verwendet, um die für die jeweilige Aufgabe benötigten Informationen herauszufiltern. Außerdem habe ich den `LIKE`-Operator in Verbindung mit dem Prozentzeichen (`%`) als Platzhalter verwendet, um nach bestimmten Suchmustern zu filtern.

## Ressourcen

- [Google Cybersecurity Professional Certificate](https://www.coursera.org/professional-certificates/google-cybersecurity)
