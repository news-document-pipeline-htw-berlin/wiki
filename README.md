# iNews-Pipeline

Implementierung einer Dokumenten-Pipeline für Nachrichtenartikel


![alt text](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/blob/master/I%20News.png "Architecture iNews-Pipeline")


Zur grafischen Einführung bitte unsere [Präsentation](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/blob/master/FinalePraesentation31_01_2020.pdf) anschauen.

[=> _Hier_](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/wiki/Sonstiges) ein Überblick über die Virtuelle Maschine und die laufenden Dienste.


## 1. Crawler

Aufgaben: 
- regelmäßig neue Artikel von News-Seiten “scrapen”, bestimmte Merkmale erfassen und in eine Datenbank schreiben.

aktuell: 
- [taz](https://www.taz.de)
- [Süddeutsche Zeitung](https://www.sueddeutsche.de)
- [Heise](https://www.heise.de)

Technologien:
- [Scrapy](https://scrapy.org)
- [mongoDB](https://www.mongodb.com)
- [Kibana](https://www.elastic.co/kibana) (mit [Elasticsearch](https://www.elastic.co/de/elasticsearch))

geschrieben in Python

#### [=> _Repository/Readme_](https://github.com/I-News-Pipeline-HTW-Berlin/crawler)


## 2. UIMA

Technologien:
- [UIMA](https://uima.apache.org)
- [DKPro](https://dkpro.github.io)
- [Spark](https://spark.apache.org)

Aufgaben: 
- die gescrapten Artikel analysieren 

aktuell: 
- Lesezeit 
- relevanteste Wörter bzw. Objekte (nach Tf-Idf)
- Lemmas
- Zuordnung eines oder mehrerer Departments

geschrieben in Scala

#### [=> _Repository/Readme_](https://github.com/I-News-Pipeline-HTW-Berlin/uima-pipeline)


## 3. mongoDB

- Dokumentenbasierte NoSQL Datenbank
- Basiert quasi auf JSON-Dokumenten
- unser zentraler Datenspeicher, hält die Daten der Scraper und der UIMA-Pipeline


## 4. ElasticSearch

- Auf JSON basierende Suchmaschine
- nutzt JSON für Anfragen und Antworten
- Teil des Elastic Stacks
- Stellt die Suchfunktion bereit

#### [=> _ElasticSearch im Projekt_](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/wiki/ElasticSearch-&-Kibana)

#### [=> _Repository selbstgeschriebener Connector_](https://github.com/I-News-Pipeline-HTW-Berlin/MongoDB-Elasticsearch-Connector)


#### [=> _Systemd service file for elasticsearch_](https://github.com/I-News-Pipeline-HTW-Berlin/miscellaneous/blob/master/elasticsearch.service)


## 5. HTTP-API

Aufgaben: 
- Zeitungsartikel nach außen sichtbar machen
- Analytics aggregieren
- Elasticsearch-Abfragen (suchen, filtern und aggregieren)
- GET-Anfragen bearbeiten
- Antwort mit JSON-Daten

geschrieben in Scala mit der [Akka-Library](https://akka.io/)

#### [=> _Repository/Readme_](https://github.com/I-News-Pipeline-HTW-Berlin/HTTP-API)


## 6. Frontend

mit [ReactJS](https://reactjs.org) geschrieben

- 2011 innerhalb von Facebook entwickelt
- Komponenten
- State und Props
- Virtual DOM

und folgenden Libraries:
- [react-router](https://github.com/ReactTraining/react-router)
- [MaterialUI](https://material-ui.com)
- [react-vis](https://uber.github.io/react-vis)

#### [=> _Frontend im Projekt_](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/wiki/Frontend)

#### [=> _Repository/Readme_](https://github.com/I-News-Pipeline-HTW-Berlin/Frontend)

#### [=> _nginx config file_](https://github.com/I-News-Pipeline-HTW-Berlin/miscellaneous/blob/master/default.conf)

## 7. Autoren

Technologien:

- [Spark](https://spark.apache.org)

- [SparkMongo](https://docs.mongodb.com/spark-connector/master/scala-api)


Aufgaben: 

- die Autoren der verarbeiteten Artikel aus der NLP Pipeline analysieren



aktuell: 

- anzahl der Artikel pro Tag je Autor 

- anzahl der Artikel pro Kategorie je Autor

- anzahl der Artikel pro Website je Autor

- durchschnittliches Sentiment pro Tag

- durchschnittliches Sentiment pro Kategorie

- anzahl der Wörter für die letzten fünf Artikel

- trust score


geschrieben in Scala

### Mögliche Verbesserungen

- komplexere Berechnung des Trust Scores

- komplexere Analysen:
  - Welche Autoren schreiben häufig zusammen?
  - Schreiben die Autorenpaare gewöhnlicherweise in der gleichen Kategorie?
  - Haben die Paare ähnliche Lücken in der nichts geschrieben wurde? 
  - Hebt sich Sentiment oder Wortanzahl wenn die Autoren zusammen schreiben, oder senkt sie sich sogar?
  - Wann schreibt der Autor **(Veröffentlichungsdatum != Verfassungsdatum)**

Bei weiteren Anreizen empfiehlt es sich das Video zum SpiegelMining anzusehen


#### [=> _Repository/Readme_](https://github.com/news-document-pipeline-htw-berlin/Authors)




