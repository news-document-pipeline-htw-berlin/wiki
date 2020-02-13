# iNews-Pipeline

Implementierung einer Dokumenten-Pipeline für Nachrichtenartikel


![alt text](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/blob/master/I%20News.png "Architecture iNews-Pipeline")


Zur grafischen Einführung bitte unsere [Präsentation](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/blob/master/FinalePraesentation31_01_2020.pdf) anschauen.


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

#### [=> _Repository/Readme_](https://github.com/I-News-Pipeline-HTW-Berlin/Backend)


## 6. Frontend

mit [ReactJS](https://reactjs.org)

- 2011 innerhalb von Facebook entwickelt
- Komponenten
- State und Props
- Virtual DOM

Libraries:
- [react-router](https://github.com/ReactTraining/react-router)
- [MaterialUI](https://material-ui.com)
- [react-vis](https://uber.github.io/react-vis)

#### [=> _Frontend im Projekt_](https://github.com/I-News-Pipeline-HTW-Berlin/wiki/wiki/Frontend)

#### [=> _Repository/Readme_](https://github.com/I-News-Pipeline-HTW-Berlin/Frontend)

#### [=> _nginx config file_](https://github.com/I-News-Pipeline-HTW-Berlin/miscellaneous/blob/master/default.conf)


