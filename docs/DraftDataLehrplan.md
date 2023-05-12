# 0 Formales

## F 0-1 Übersicht
Daten werden in modernen Anwendungssystemen zunehmend zu "First Class Citizens". Gründe dafür sind etwa der deutlich gestiegene und weiter steigende Einsatz mobiler Endgeräte, die massenweise Integration von Geräten über IoT, die universelle Verfügbarkeit von Anwendungen in der Cloud, der zunehmende Einsatz KI-basierter Lösungen und natürlich die Verfügbarkeit günstiger digitaler Speichertechnologie. Dies zeigt sich auch in Trends/Hypes wie "Big Data" oder "Data Driven". Entsprechend sind in den letzten Jahren die Anforderungen an Software-/ Systemarchitekten gestiegen, sich mit geeigneten Architekturen zur Verarbeitung großer Datenmengen zu befassen.
Der hier vorliegene iSAQB Lehrplan soll einen möglichst umfassenden Überblick über alle Aspekte bieten, die im Zusammenhang mit der Verarbeitung großer Datenmengen aus der Sicht von Software-/ Systemarchitekten Beachtung verdienen.

## F 0-2 Abgrenzung
Insbesondere die folgenden Themengebiete sind im Lehrplan zwar enthalten, werden aber nicht vertieft behandelt: 
- Data Science (Statistik, Machine Learning)
- Business Intelligence (OLAP, Multidimensional Modeling)
- Datenschutz

In vielen Spezialgebieten spielt die Verarbeitung großer Datenmengen ebenfalls eine maßgebliche Rolle. Sie werden in diesem Lehrplan nicht explizit behandelt. Beispiele dafür sind: 
- IoT
- Suchmaschinen
- Wissenschaftliche Anwendungen (Klimaforschung, Kernphysik, Proteinfaltung, etc) 

## F 0-3 Zeiten 
- Motivation und Übersicht: 60
- Referenzarchitekturen für analytische Anwendungssysteme: 120
- Sources: 45
- Ingestion und Transport: 60
- Storage: 120
- Query und Processing: 120
- Transformation: 45
- Presentation und Downstream Integration: 90
- Schema und Modeling: 120
- Data Pipelines: 120
- Data Governance: 90
- Data Mesh: 90


# 1 Motivation und Übersicht

## LZ 1-1 - Unterscheidung operativer und analytischer Daten
Die Teilnehmer können den Unterschied zwischen operativen und analytischen Daten erläutern. Sie können die Begriffe OLTP und OLAP unterscheiden. Sie kennen typische Beispiele für opreative Anwendungen und wissen, welche iSAQB Module sich spezifisch mit der Architektur operativer Anwendungssysteme befassen.
Den Teilnehmern ist klar, warum operative und analytische Daten üblicherweise separat verarbeitet werden. Sie können die folgenden Eigenschaften (?) analytischer Daten erläutern:
- subject-oriented
- nonvolatile
- integrated
- time variant
Die Teilnehmer kennen Beispiele, wie analytische Daten aus operativen Anwendungen entstehen. Sie kennen ebenfalls Beispiele, wie Ergebnisse von Analysen analytischer Daten in operativen Anwendungen genutzt werden können.

[Codd / FASMI]

## LZ 1-2 - Analytische Anwendungen
Die Teilnehmer kennen typische Beispiele für analytische Anwendungen (Berichtswesen, Markt- und Kundenanalyse, Operations Research, KPI, Warenkorbanalyse, Regressionsanalyse, Risikoanalyse, Trendanalyse, etc.) und können Typen von Nutzern (Farmer, Explorer, Miner, Tourist, ...) unterscheiden.
Die Teilnehmer können übliche Herausforderungen bei Konzeption, Umsetzung und Betrieb analytischer Anwendungssysteme speziell im Hinblick auf die folgenden Aspekte bennenen:
- Umfang und Komplexität der zu verarbeitenen Daten
- Komplexität und Anzahl der Analysen, Anfragen / Queries
- Verfügbarkeit
- Datensicherheit

[Data as "first class citizen"]

## LZ 1-3 - Kategorien analytischer Anwendungen
Die Teilnehmer kennen die typischen Kategorien analytischer Anwendungen, können diese unterscheiden und jeweils Beispiele dazu nennen:
- Explorativ und konfirmatorisch
- Deskriptiv, diagnostisch, prediktiv und preskriptiv 
- Inferentiell und prediktiv
- Realtime, near realtime und batch

[Model interpretability]

## LZ 1-4 - Historie der Umsetzung analytischer Anwendungssysteme
Die Teilnehmer haben einen Überblick, wie analytische Anwendungssysteme im Laufe der Zeit umgesetzt worden sind.
Sie kennen Begriffe wie Reporting, DSS, EIS, DWH, Data Mart, Data Vault, Data Mining, ODS, Data Lake, Data Fabric, Data Mesh. Sie können diese Lösungsansätze unterscheiden und wissen, wie sie auseinander hervorgegangen sind.

[Cloud, ML]

## LZ 1-5 - Qualität von Daten
Die Teilnehmer kennen typische Qualitätsmerkmale von Daten und können diese erläutern:
- Genauigkeit
- Verfügbarkeit
- Vollständigkeit
- Aktualität
- Konsistenz
- Privatheit
- Sicherheit
- Vergleichbarkeit
- Granularität
- Glaubwürdigkeit
- Plausibilität
- Validität
- Relevanz
- Nützlichkeit
- Eindeutigkeit
- Zuverlässigkeit
- Konformität
- Einheitlichkeit
- Dauerhaftigkeit
- Interpretierbarkeit

Die Teilnehmer verstehen, warum die Gewährleistung von Datenqualität bei analytischen Daten eine besondere Herausforderung ist. Sie kennen Beispiele für Verfahren zur Prüfung, Gewährleistung und Verbesserung analytischer Daten wie etwa:
- Identifikation von Entitäten und Deduplizierung
- Rechtschreibprüfung und -korrektur
- Schema Vorgabe und Anwendung (Data Constraints)
- Prüfsummen
- Beschreibende fachliche Metadaten
- (Standard-) Datenaustauschformate
- Erkennen von Ausreißern (Outlier Detection), fehlenden Werten und Widersprüchen 

# 2 Referenzarchitekturen für analytische Anwendungssysteme
## LZ 2-1 - Überblick zu Referenzarchitekturen
Den Teilnehmern ist der generelle Nutzen von Referenzarchitekturen bewusst:
- eine Vorlage für eine funktionale Zerlegung in wesentliche Bestandteile zur Verfügung zu stellen
- ein einheitliches Vorgehen für die Aufnahme, Verarbeitung und Verwendung von Daten vorzugeben
- dadurch eine Vorlage für die Ausprägung konkreter Software-Architekturen zu bieten

Die Teilnehmer verstehen, dass Referenzarchitekturen für analytische Anwendungssysteme generell unterschieden werden, je nachdem, ob eine Basis für
- die Vereinheitlichung und Integration analytischer Daten
- die Anwendung von Verfahren der KI und des ML auf analytischen Daten
- beides zugleich
geschaffen werden soll.

Die Teilnehmer kennen Ansätze, ein einheitliches Framework für Referenzarchitekturen zu analytischen Anwendungssystemen zu beschreiben [Bornstein: https://future.com/emerging-architectures-modern-data-infrastructure/].

Die Teilnehmer kennen Beispiele zu Referenzarchitekturen für analytische Anwendungssysteme wie etwa
- Data Warehouse
  - Enterprise DWH [Inmon]
  - DWH [Kimball]
  - Scalable DWH / Data Vault [Linstedt]
- Data Lake
  - DL Architecture Framework [Giebler]
  - DL Lambda Architecture [Marz]
- Machine Learning
  - Reference Architecture for big data systems [Pääkkönen] 

## LZ 2-2 - Referenzarchitekturen zur Vereinheitlichung analytischer Daten
Die Teilnehmer können die folgenden Phasen der Datenverarbeitung zur Vereinheitlichung analytischer Daten unterscheiden und wissen, welche Komponenten in den jeweiligen Phasen typischerweise zum Einsatz kommen [Bornstein]:
- Sources - Das Erzeugen der Daten (ERP-Systeme, Logs, APIs, ...)
- Ingestion und Transport - Das Extrahieren der Daten und deren Transport zum den Speichersystemen (Workflow Manager, Replikationslösungen, Streamprocessing Engines, ...)
- Storage - Das Abspeichern der Daten (Data Lake, Data Warehouse, ...) 
- Query und Processing - Code zur Verarbeitung und Abfragen gegen die gespeicherten Daten (Spark, SQL, Dataframes, ...)
- Transformation - Transformation der Daten in eine für die Analyse geeignete Form (Workflow Manager, SQL/Spark Code Generierung, ...)
- Analysis und Output - Präsentation der Daten für die Analyse und deren Ergebnisse sowie Integration der Analysemöglichkeiten in Anwendungen (Dashboards, Embedded Analytics, Report-Engines, ...)

Den Teilnehmern ist bewußt, dass Referenzarchitekturen begleitend zu diesen Phasen auch die folgenden Aufgabenbereiche mit geeigneten Komponenten abdecken müssen:
- Data Discovery - Information bereitstellen, welche Daten es gibt, wie sie aufbereitet und wo sie zu finden sind
- Data Governance - Erarbeiten und Überwachen allgemein gültiger Regeln für die Verarbeitung der Daten
- Data Security - Gewährleisten eines angemessenen Grads an Datenschutz
- Data Quality - Gewährleisten eines angemessenen Grads an Datenqualität

## LZ 2-3 - Referenzarchitekturen zur Anwendung von Verfahren der KI und des ML
Die Teilnehmer können die folgenden Phasen der Datenverarbeitung zur Anwendung von Verfahren der KI und des ML unterscheiden und wissen, welche Komponenten in den jeweiligen Phasen typischerweise zum Einsatz kommen [Bornstein]:
- Data Transformation - Konvertieren der Rohdaten in ein geeignetes Format für das Model Training (Data Labeling, Data Science Libraries, ...)
- Model Training und Development - Iteratives Trainieren der Modelle mit den Daten, Optimieren und Automatisieren der Abläufe für das Trainieren der Modelle (Feature Store, Model Registry, ML/DL Framework, Workflow Manager, ...)
- Model Inference - Anwenden der Modelle auf die zu analysierenden Daten. Monitoring der Verarbeitung ()
- Integration - Integration der Analyse-Verfahren und Ergebnisse in Anwendungen ()

## LZ 2-4 - Architekturentscheidungen anhand von Referenzarchitekturen
Die Teilnehmer können Architekturentscheidungen speziell zu den folgenden Fragestellungen anhand von Referenzarchitekturen diskutieren:
- ob ein zentrales/monolithisches oder dezentrales/förderiertes System zu wählen ist 
[Single Point of Truth, Canonical Data Model, Master Data Management]
- ob ein Deployment in der Cloud (ggfs. Cloud-Ready), hybrid oder on-Premise vorzuziehen ist
- ob ein einheitliches Schema für die auszuwertenden Daten vorgegeben werden soll
- ob eine eigenständige Entwicklung von Komponenten erforderlich ist oder das Kaufen und Konfigurieren von Standardkomponenten ausreicht
- ob die Integration von Komponenten selbst vorgenommen oder auf die Verwendung bereits integrierter Komponenten vertraut wird
- ob Stream-, Batch-Processing (ggfs Micro-Batch) oder beides unterstützt werden muss
- welches Bezahlmodell (Pay as you go, subscription fee, buy) Vorteile bietet
- welche Form der Skalierbarkeit konkret benötigt wird: Datenvolumen, Geschwindigkeit der Verarbeitung und des Datenzugriffs, Anzahl und Variabilität der Datenquellen, Anzahl der Nutzer, Anzahl und Variabilität der analytischen Auswertungen
- inwieweit Daten repliziert/redundant gespeichert werden müssen
- ob eine fachliche Modularisierung (im Sinne von DDD) erforderlich ist
- welche Rollen und Verantwortlichkeiten vorgesehen werden müssen
- wie groß Komponenten dimensioniert werden müssen

# 3 - Datenquellen
## LZ 3-1 - Arten von Datenquellen und Quellsystemen
Die Teilnehmer kennen Arten von Datenquellen und Quellsystemen, von denen analytische Daten typischerweise übernommen werden, wie etwa
- Business Anwendungen
  - Legacy-Anwendungen
  - (REST-) APIs
- Datenbanken
  - OLTP
  - Event-Stores
- Messaging Systeme
- Metrics Systeme
  - (Web-) Analytics
  - Sensordaten
- (Cloud) Storage Systeme
- Logging Systeme

## LZ 3-2 - Eigenschaften von Datenquellen und Quellsystemen
Die Teilnehmer können unterscheiden, ob Datenquellen strukturierte, semi-strukturierte oder unstukturierte Daten liefern. Ihnen sind übliche Formate vertraut, in denen Datenquellen ihre Daten zur Verfügung stellen, wie etwa
- Dokument
- Datenstrom
- Liste von Datensätzen

Die Teilnehmer wissen, dass Datenquellen den aktuellen Zustand der zuletzt geänderten Daten oder die Änderungen (Events) selbst wiedergeben können, mit denen dieser aktuelle Zustand erzeugt wurde. Sie wissen, dass ggfs. eine initiale Bereitstellung (initial Load) der Daten erforderlich ist. 
Die Teilnehmer wissen, dass Datenquellen ihre Daten selbst aktiv liefern (Push) oder aber auf Anfrage bereitstellen (Pull) können.

Den Teilnehmern ist bewusst, dass Quellsysteme in unterschiedlicher Weise und Qualität den Schutz der Daten sowie eine Kontrolle des Zugriffs auf die Daten unterstützen.

Den Teilnehmern ist bewusst, dass Quellsysteme z.T. sehr große Datenmengen bereitstellen, und dass geeignete Maßnahmen getroffen werden müssen, um diese Datenmengen transportieren zu können.

Den Teilnehmern wissen, dass das zur Verfügung stellen analytischer Daten idR nicht der eigenliche Zweck von Quellsystemen ist. Sie wissen, dass dadurch zusätzliche Last für das jeweilige Quellsystem erzeugt werden kann und dass dies idR den eigentlichen Zweck eines Quellsystems nicht beeinträchtigen darf.

## LZ 3-3 - Metadaten
Die Teilnehmer verstehen die Bedeutung von Metadaten für die Nutzung von Datenquellen. Sie können technische und fachliche Metadaten unterscheiden. Sie wissen, dass Quellsysteme oft umfassend Metadaten zu den von ihnen bereitgestellten Datenquellen zur Verfügung stellen.

Die Teilnehmer wissen, dass es Verfahren gibt (Schema Inference), um Metadaten aus Daten abzuleiten. Ihnen ist bewusst, dass sich Metadaten über die Nutzungsdauer von Daten ändern können (Schema Evolution) und dass Verfahren existieren, diese Änderungen beim Zugriff auf die Daten zu erkennen.


# 4 - Ingestion und Transport
## LZ 4-1 - Erkennen von Änderungen
Den Teilnehmern sind Verfahren für das Identifizieren von Entitäten sowie für das Erkennen von Änderungen dieser Entitäten in Quellsystemen bekannt, wie etwa
- Change Data Capture (CDC)
- DB-Trigger
- Outbox Pattern
- Event-Sourcing
- Create und Update Timestamps
- Audit Trail Reader
- Datensatz-Hashes
- Primary Keys
- (RSS-)Feeds

Die Teilnehmer wissen, für welche Art von Quellsystemen welche dieser Verfahren jeweils geeignet sind.

Den Teilnehmern ist bewußt, dass das Löschen von Daten üblicherweise ebenfalls als Änderung geliefert wird, da auch gelöschte Daten für die Analyse ggfs. weiter benötigt werden.

Den Teilnehmern ist bewußt, dass sich Änderungen von Entitäten auf den internen Zustand von Quellsystemen beziehen können und dass mit der Weitergabe dieser Änderungen das Prinzip des Information Hidings verletzt werden kann. Sie verstehen, wie etwa das Outbox Pattern dazu genutzt werden kann, die von Quellsystemen zur Verfügung gestellten Änderungen auf das erforderliche Maß zu beschränken. 

## LZ 4-2 - Konnektoren
Die Teilnehmer kennen Tools und Frameworks, die über vordefinierte Konnektoren einen vereinheitlichten Zugriff auf Quellsysteme zur Verfügung stellen. Sie wissen, dass diese Tools und Frameworks vorrangig für die folgenden Aufgaben eingesetzt werden:
- Datenreplikation
- Datenintegration
- Datenvirtualisierung
- Datenorchestrierung
- Metadatenmanagement

Die Teilnehmer kennen Beispiele für diese Tools, wie etwa
- Fivetran
- Stitch
- funnel
- integrate.io
- talend
- airbyte
- Kafka Connect
- Pulsar IO
- Trino / Presto
- alluxio
- Collibra
- Alation

## LZ 4-3 - [File Transfer]

## LZ 4-4 - [Message Passing]
- Message Broker
- Pub/Sub, Brodcast, Request/Response
- Routing
Die Teilnehmer kennen Beispiele für Message Broker wie
- Apache Kafka
- Apache Pulsar
- AWS Kinesis
- Google Pub/Sub
- Azure Event Hubs

## LZ 4-5 - Event Streaming
Die Teilnehmer wissen, dass 
- beim Event Streaming je Datenquelle idR ein Producer für das Lesen der Daten aus dieser Quelle und das Weiterleiten an eine entsprechende Middleware Komponente (Message Broker) verantwortlich ist.
- beim Event Streaming je Datensenke idR ein Consumer für das Lesen der Daten vom Message Broker und das Schreiben in diese Senke verantwortlich ist.
- entsprechend die Daten einer Datenquelle von mehreren Consumern in mehrere Datensenken geschrieben werden können. 
- Event Streaming nicht generell garantiert, dass jeder Datensatz genau einmal (exactly once) verarbeitet wird, sondern meist nur zusichert, dass jeder Datensatz höchstens (almost once) oder mindestens einmal (at least once) verarbeitet wird.
- mit Event Streaming idR nur eventuelle Konsistenz der Daten in der Datensenke zusichert wird.

## LZ 4-6 - Reverse ETL
Den Teilnehmern ist das Konzept der Reverse ETL vertraut. Sie kennen Anwendungsfälle für die Integration von vereinheitlichten Daten oder von Ergebnissen analytischer Auswertungen in operative Anwendungen. 
Die Teilnehmer wissen, dass Reverse ETL Tools mit Konnektoren für gängige operative Anwendungen existieren, die die Umsetzung entsprechender Integrationslösungen deutlich erleichtern. Sie kennen Beispiele für diese Tools. 


# 5 - Storage
## LZ 5-1 - Speichersysteme
Die Teilnehmer kennen die folgenden wesentlichen Systeme zum Speichern digitaler Daten und können die jeweiligen Besonderheiten erläutern:
- Filesystem
- Block-Storage System
- Objekt-Storage System

Die Teilnehmer kennen Kriterien zur Auswahl des passenden Systems, wie etwa
- Flüchtigkeit (Volatility) / Dauerhaftigkeit (Persistence) 
- Änderbarkeit (Mutality)
- Zugreifbarkeit (Accessibility)
- Adressierbarkeit (Addresability)
- Kosten
- Zuverlässigkeit (Reliability) / Fehlertoleranz
- Performanz - Zugriffszeit (Latency), Durchsatz (Throughput)
- Skalierbarkeit
- Kapazität
- Administrierbarkeit
- Unterstützung für Metadaten
- Datenschutz / Unterstützung für Verschlüsselung
- Umweltbelastung / Nachhaltigkeit / Energiebedarf

Die Teilnehmer verstehen den Unterschied zwischen blockierenden und nicht-blockierenden Zugriffen auf Speichersysteme.

Die Teilnehmer wissen, dass Speichersysteme unterschiedlich an Systeme zur Verarbeitung der Daten angebunden werden können:
- Direkte Anbindung (Direct Attached Storage - DAS)
- Speichernetzwerk (Storage-Area-Network - SAN)
- Netzwerkspeicher (Network Attached Storage - NAS)

Die Teilnehmer wissen, dass Speichersysteme auf die folgenden unterschiedlichen Weisen zur Verfügung gestellt werden können:
- Multi-Cloud
- Public Cloud
- Private Cloud
- Hybrid Clouds
- On-Premise

Die Teilnehmer wissen, dass Speichersysteme in der Cloud mit unterschiedlichen SLAs angeboten werden können (etwa Hot vs Cold Storage).

## LZ 5-2 - Datenbanksysteme
Die Teilnehmer verstehen, dass die Verwaltung von Daten Aufgaben umfasst, die von Speichersystemen nicht direkt unterstützt werden, wie etwa
- Verwaltung der Metadaten zu den Daten
- Vorgabe und Anwendung von Schema-Informationen zu den Daten
- Sicherstellen der Konsistenz der Daten (s. LZ 5-3)
- Validierung von Daten
- Redundante Datenhaltung speziell für verbesserte Verfügbarkeit und Zugriffsszeiten
- Standardisierte, flexible und performante Datenzugriffe
- Feingranulare Zugriffskontrolle
- Skalierbarkeit
- Optimierung (Reduzierung) der Speichernutzung 

Die Teilnehmer wissen, dass Datenbanksysteme (DBS) diese Aufgaben übernehmen. Sie verstehen, dass DBS auf der Basis aller Speichersysteme umgesetzt werden können. Sie kennen die folgenden Typen von DBS und sind mit den jeweiligen Besonderheiten vertraut:
- Relationale DBS
- NoSQL DBS
  - Key-Value DBS
  - (Wide) Column DBS
  - Document DBS
  - Graph DBS

Die Teilnehmer kennen entsprechende Produkte zu diesen DBS-Typen und ihnen ist bewusst, dass Produkte auch mehrere dieser Typen abbilden können.

Die Teilnehmer kennen Systeme, die lediglich einen Teil der o.g. Aufgaben von DBS übernehmen und sind mit deren jeweiligen Besonderheiten vertraut:
- Searchengines
- Timeseries DBS
- Multidimensionale DBS / Data Marts / Cubes
- In-Memory DBS
- Event Store DBS
- Vector DBS

Die Teilnehmer verstehen, dass einige o.g. Aufgaben alleine durch die Verwendung geeigneter Datei- oder Tabellenformate abgedeckt werden können. Sie kennen speziell die folgenden:
- Dateiformate: Avro, ORC, Parquet
- Tabellenformate (Open Table Formats): Delta, Iceberg, Hudi

## LZ 5-3 - Concurrency Control
Die Teilnehmer verstehen, dass bei Multi-Threading und -Processing Systemen mit nebenläufiger Verarbeitung sowie redundanter Speicherung von Daten die Konsistenz von Daten explizit sichergestellt werden muss. Ihnen ist das Konzept von ACID Transaktionen und deren Serialisierbarkeit vertraut. Sie wissen, dass ACID Transaktionen auf unterschiedliche Weisen und mit unterschiedlichen Garantien für Konsistenz (Consistency) und Isolation umgesetzt werden können.

Die Teilnehmer wissen, dass ACID Transaktionen üblicherweise von (relationalen) Datenbankmanagementsystemen zur Verfügung gestellt werden, dass sie aber nicht auf diese Systeme beschränkt sind.

Den Teilnehmern ist bekannt, dass ACID Transaktionen speziell bei verteilten Anwendungen (mit dem dafür erforderlichen Two-Phase-Commit Protokoll) deren Verfügbarkeit idR zu stark einschränken. Ihnen ist das alternative Konzept der BASE-Eigenschaften sowie speziell der eventuellen Konsistenz (Eventual Consistency) verteilter Anwendungen vertraut.

Die Teilnehmer verstehen, dass es Verarbeitung großer Datenmengen (speziell im Batch) sinnvoll sein kann, auf ACID Transaktionen zu verzichten oder sie zumindest mit schwächeren Garantien für Consistency und Isolation zu verwenden.

[Concurrent data structures]

## LZ 5-4 - Versionierung von Daten
Den Teilnehmern ist bewusst, dass bei veränderlichen Daten nicht nur der aktuelle Zustand, sondern auch die früheren Zustände (speziell für analytische Auswertungen) von Interesse sein können. Sie kennen die folgenden Verfahren für die Versionierung von Daten und verstehen, wie diese etwa in Form von Datenbanksystemen mit den o.g. Speichersystemen kombiniert werden:
- Transaktionen (über die Serialisierbarkeit)
- Versionskontrollsysteme
- Event-Sourcing

## LZ 5-5 - Optimierung und Skalierung
Die Teilnehmer kennen übliche Verfahren, um Speichersysteme bei steigender Last zu optimieren und zu skalieren, wie etwa
- Sharding
- Partitionierung (vertikal/horizontal)
- Indexierung
- Caching
- Append Only / Read Only

## LZ 5-6 Data Warehouse und Data Lake
Die Teilnehmer wissen, dass Data Warehouse (DWH) Systeme idR für die Vereinheitlichung und Integration analytischer Daten verwendet werden. Sie wissen, dass Data Lake (DL) Systeme neben dieser Vereinheitlichung und Integration analytischer Daten auch eher als DWH Systeme geeignet sind, die Anwendung von Verfahren der KI und des ML auf analytischen Daten zu ermöglichen.

Die Teilnehmer wissen, wie Speichersysteme und darauf aufbauende Datenbanksysteme als Grundlage für DWH und DL Systeme verwendet werden.

Die Teilnehmer wissen, dass Cloud-basiert erweiterte Datenbanksysteme etwa von Snowflake, Google (BigQuery), Teradata (Vantage) oder AWS (Redshift) angeboten werden, mit denen kombinierte DWH und DL Systeme umgesetzt werden können.

Die Teilnehmer kennen wesentliche Unterschiede zwischen DWH und DL Systemen, wie etwa
- Ein definiertes Schema (Schema on Write) beim DWH (das sich im Laufe der Zeit ändern kann) gegenüber mehreren parallelen Schema (etwa mit Schema on Read) beim DL.
- Nur vereinheitlichte Daten im DWH während im DL auch die ursprünglichen Quelldaten (Rohdaten) vorgehalten werden.
- Optimierte Strukturen für den lesenden (analytischen) Zugriff beim DWH gegenüber vereinfachten schreibenden Zugriffen beim DL.
- Begrenzung auf strukturierte Daten beim DWH während DL auch unstrukturierte und semi-strukturierte Daten aufnehmen können.
- Hoher Aufwand für die Integration neuer Datenquellen beim DWH während neue Datenquellen in den DL direkt aufgenommen werden können.
- Hoher Aufwand für die Vereinheitlichung von Daten beim lesenden (analytischen) Zugriff im DL während dies beim DWH in deutlich geringerem Umfang erforderlich ist.

Die Teilnehmer kennen Lösungsansätze, um in DWH Systemen den Aufwand für Änderungen am Schema sowie für die Integration neuer Datenquellen zu reduzieren, wie etwa
- Verwendung künstlicher Schlüssel (Surrogate Keys)
- Multidimensionale Modellierung
- Data Vault
- Automatisierung der Schemaänderungen (Data Warehouse Automation)

Die Teilnehmer kennen Lösungsansätze, um in DL Systemen den Aufwand für die Vereinheitlichung beim lesenden Zugriff zu reduzieren
- Aufteilen des DL in Bereiche unterschiedlicher Datenqualität (etwa Bronze, Silber und Gold), wobei die Rohdaten im Bronze-Bereich und die vereinheitlichten, gut analysierbaren Daten im Gold-Bereich zu finden sind.
- Technische Aspekte der Vereinheitlichung direkt bei der Eingangsverarbeitung erledigen (einheitliche Zeichensätze, Null-Values, Datumsformate, ...)
- Modularisierung des DL etwa über die Verwendung von DDD (s. LZ - 12)


# 6 - Query und Processing
## LZ 6-1 - Queries
Die Teilnehmer kennen den üblichen Aufbau analytischer Queries mit Angaben zu
- Filtern (Where)
- Projektionen (Select)
- Gruppierungen (Group by)
- Sortierungen (Order by)
- Joins (Inner, Outer, Left, Right, Full, ...)
- Aggregationen (Sum, Count, Avg, ...)
- Fenstern/Windows (Over Partition by)
- OLAP Operationen (Slice/Dice, Drill up/down/...)
- Umformungen (Pivot, Transpose, ...)
- Modularisierung ([Materialized] Views, Common Table Expressions, Stored Procedures, User Defined Functions)

Die Teilnehmer verstehen, dass sich analytische Queries stets lesend auf eine größere Anzahl von Datensätzen beziehen.
Sie wissen, dass diese Daten für die Analyse sowohl komplett abgespeichert (Data in Rest) als auch im Fluss (Data in Motion) sein können.
Die Teilnehmer wissen, dass analytische Queries oft auf verteilten Daten operieren müssen. Sie verstehen den Nutzen von Ausführungsplänen für analytische Queries und deren Optimierung.
Die Teilnehmer verstehen, dass analytische Queries idR nicht komplett im Hauptspeicher verarbeitet werden können. Ihnen ist bekannt, dass analytische Queries daher eine separate Komponente (Engine / Platform) benötigen, die eine performante Ausführung insbesondere durch Lastverteilung auf parallel arbeitende Worker gewährleistet.
Die Teilnehmer wissen, dass diese Engines sehr eng an ein verwendetes Datenbanksystem gekoppelt sein können, dass es aber auch Engines gibt, die davon unabhängig arbeiten. Sie wissen, dass diese Engines in der Cloud (public/private) und auch on-Premises betrieben werden können. 
Die Teilnehmer wissen, dass unterschiedliche Programmiermodelle für analytische Queries eingesetzt werden. Ihnen sind wesentliche Programmiermodelle bekannt und sie können beurteilen, für welche Aufgaben sie speziell geeignet sind:
- SQL
- OLAP
- Spark
- Map-Reduce
- Stream Processing
- Dataframes
- Numerical/Statistical

Den Teilnehmern ist bewusst, dass diese Programmiermodelle idR miteinander kombiniert werden.

Die Teilnehmer kennen für jedes dieser Programmiermodelle Beispiele zu Frameworks, Libraries und Tools für die Verarbeitung analytischer Queries wie etwa

- SQL - BigQuery, Oracle, Trino/Presto, Databricks SQL
- OLAP - MS Analysis Services, ClickHouse, Apache Pinot 
- Spark - Databricks
- Map-Reduce - Hadoop
- Stream processing - Kafka Streams, Apache Flink, Databricks Structured Streaming
- Dataframes - Pandas, Ray, Dask
- Numerical/Statistical - SAS, STATA, SPSS

## LZ 6-2 - Batch Verarbeitung
Die Teilnehmer verstehen das Verfahren der Batch Verarbeitung (Batch Processing) von Daten. Ihnen ist bewusst, dass
- die Batch Verarbeitung üblicherweise dazu dient, eine größere Anzahl Datensätze aus mehreren Datenquellen in einem Schritt zu verarbeiten und die Ergebnisse in eine Datensenke zu schreiben
- alle (initial/complete load) oder nur die letzten Änderungen (incremental load) im Batch verarbeitet werden können
- die Batch-Verarbeitung idR zeitlich geplant (scheduled) und wenige Male je Tag ausgeführt wird
- eine Batch-Verarbeitung idR alle Datensätze verarbeitet oder (im Fehlerfalle) keine
- eine Batch-Verarbeitung üblicherweise die Konsistenz (s. LZ 5-3) der Daten in der Datensenke erhält
- eine Batch-Verarbeitung komplexe Operationen zur Datenverarbeitung enthalten kann

Die Teilnehmer verstehen das Verfahren der Micro-Batch Verarbeitung von Daten. Ihnen ist bewusst, dass sich die Micro-Batch Verarbeitung von der Batch Verarbeitung i.W. im folgenden Punkt unterscheidet:
- Die Micro-Batch Verarbeitung wird sehr häufig am Tag ausgeführt: Jeweils nach Ablauf einer kurzen Zeitspanne seit der letzten Ausführung oder auch schon früher, wenn ausreichend Datensätze in der Datenquelle angefallen sind

## LZ 6-3 - Stream Verarbeitung
Die Teilnehmer verstehen das Verfahren der Stream Verarbeitung (Stream Processing) von Daten. Sie wissen, dass Stream Verarbeitung auf der Basis des Event Streamings aufsetzt. 
Die Teilnehmer wissen, dass bei der Stream Verarbeitung
- die Daten mehrerer Streams miteinander zu einem weiteren Stream kombiniert werden können.
- Datensätze (etwa fehlerhafte oder unvollständige) im Stream voneinander getrennt und separat (in unterschiedlichen Streams) weiterverarbeitet werden können.
- bei der Verarbeitung von Daten im Stream üblicherweise auf komplexe Operationen verzichtet wird.

Die Teilnehmer verstehen, dass das Schreiben von Daten aus einem Datenstrom meist idempotent gestaltet wird (Verzicht auf Two-Phase-Commit).

Die Teilnehmer können zustandslose (stateless) und zustandsbehaftete (stateful) Stream Verarbeitung unterscheiden.

Die Teilnehmer verstehen, dass Operationen nicht auf allen Datensätzen eines Streams erfolgen können, sondern immer nur auf einzelnen oder einer Gruppe von aufeinanderfolgenden Datensätzen. Sie kennen dazu das Konzept der Fenster (Window) Funktionen.

Die Teilnehmer kennen Frameworks oder Tools für die Stream Verarbeitung wie
- Kafka Streams
- Apache Flink
- Pulsar Functions
- Spark Streaming

## LZ 6-4 - Daten-orientierte Programmierung
Die Teilnehmer kennen die Prinzipien einer Daten-orientierten Programmierung: 
- Trennung von Code und Daten
- Nutzung generischer Datenstrukturen für die Repräsentation von Daten
- Verwendung unveränderbarer (immutable) Daten Repräsentationen

## LZ 6-5 - [ML Processing]
Classification: logistic regression, naive Bayes,...
Regression: generalized linear regression, survival regression,...
Decision trees, random forests, and gradient-boosted trees
Recommendation: alternating least squares (ALS)
Clustering: K-means, Gaussian mixtures (GMMs),...
Topic modeling: latent Dirichlet allocation (LDA)
Frequent itemsets, association rules, and sequential pattern mining
ML workflow utilities include:

Feature transformations: standardization, normalization, hashing,...
ML Pipeline construction
Model evaluation and hyper-parameter tuning
ML persistence: saving and loading models and Pipelines
Other utilities include:

Distributed linear algebra: SVD, PCA,...
Statistics: summary statistics, hypothesis testing,...


# 7 - Transformation
## LZ 7-1 - Aufbereitung
Die Teilnehmer verstehen, dass (Daten-)Transformationen erforderlich sind, um Daten aus operativen Systemen für die Analyse aufzubreiten. Sie kennen übliche Aufgaben, die von Transformationen übernommen werden, wie speziell
- Umwandeln der Datenrepräsentation von Quell- in Zielformate
- Bereinigen/Standardisieren der Daten (Data Cleansing)
- Identifizieren und Entfernen von Duplikaten
- Ergänzung der Daten (Enhancement)
- Entkopplung der Daten der Quell- von denen der Zielsysteme
- Vereinheitlichung von Daten mehrerer Quellsysteme
- Optimierte Speicherung und Verteilung von Daten für performante Queries
- Reduktion des Datenumfangs, Komprimierung
- Anonymisierung, Pseudonomisierung, Verschlüsselung
- Lokalisierung der Daten
- (In Ausnahmen) Ausführen von Geschäftslogik (s. LZ 7-4)

Die Teilnehmer verstehen, wie Transformationen Verfahren des Query und Processing (s. LZ 6) nutzen, um auf die Daten in den Speichersystemen (s. LZ 5) zuzugreifen.
Sie verstehen auch, wie Transformationen in Data Pipelines (LZ 10) kombiniert werden, um komplexere Anforderungen an die Aufbereitung von Daten für die Analyse umzusetzen.

Die Teilnehmer verstehen die Bedeutung von Schemas und Datenmodellen (s. LZ 9) für die Umsetzung von Transformationen.

## LZ 7-2 - Typische Transformationen
Die Teilnehmer kennen typische Transformationen für die Aufbereitung analytischer Daten, wie etwa
- Normalisierung / Denormalisierung von Datenstrukturen - Star/Snowflake Schema, Data Vault
- Zuordnung von künstlichen IDs (surrogate keys) zu IDs der Quellsysteme 
- Zuordnung von Enum-Werten
- Rechtschreibkorrektur 
- (Multidimensionale) Aggregation (Cubes)
- Pivotisieren
- Transponieren
- Umwandlung zwischen flachen und geschachtelten Datenstrukturen
- Normierung skalarer Werte
- Ergänzen 
- Parsen und Zusammenfügen von Text
- Sortieren und Gruppieren
- Historisieren (Slowly Changing Dimensions)
- Ersetzen / Aussortieren unwahrscheinlicher Werte / Datensätze (Outlier)

## LZ 7-3 - Staging Area
Den Teilnehmern ist das Konzept der Staging Area vertraut. Sie wissen, dass
- analytische Daten aus Datenquellen in einer Staging Area gesammelt und aufbereitet werden, bevor sie für die Analyse zur Verfügung gestellt werden
- Staging Areas typischerweise für die Batch Verarbeitung von Daten zum Befüllen eines DWH Systems eingesetzt werden
- das tatsächliche Befüllen des DWH keine komplexen Operationen mehr erfordert
- die Staging Area sowohl das vollständige Verarbeiten der Daten einer Datenquelle (initial load) als auch das Verarbeiten der Änderungsdaten (incremental load) unterstützen muss.
- die Staging Area immer nur genau die Änderungsdaten erhält, die seit der letzten Batchverarbeitung in den Quellsystemen angefallen sind.

Die Teilnehmer wissen, welche Transformationen typischerweise in einer Staging Area angewendet werden.

## LZ 7-4 - Robuste Transformationen
Die Teilnehmer verstehen, dass die Umsetzung von Transformationen oft fragil ist, da sich die zu verarbeitenden Daten von Ausführung zu Ausführung im Hinblick auf Umfang, Format oder Bedeutung ändern können. Die Teilnehmer kennen Lösungsansätze, um Transformationen robust zu gestalten:
- Validieren der Eingangsdaten
- Verwenden unstrukturierter oder semi-strukturierter Daten
- Verwenden generischer Transformationen
- Vermeiden der Umsetzung von Geschäftslogik
- Geschäftslogik von Domain-Teams umsetzen lassen (s. Data Mesh, LZ 12)
- Gewährleisten der Wiederholbarkeit - Idempotente Transformationen
- Verwendung von Standards
- Einsatz von Verfahren zur Code-Generierung für eine automatisierte Anpassung von Transformationen bei Schema-Änderungen
- Zerlegen komplexer Transformationen
- Auswahl geeigneter Programmiermodelle

Die Teilnehmer kennen Verfahren zum Data Profiling, um die zu erwartenden Daten für die Umsetzung der Transformationen vorab zu analysieren.
Die Teilnehmer kennen Verfahren für die Überwachung (Monitoring) der Ausführung von Transformationen.
Die Teilnehmer kennen das Konzept der Data Lineage für das Nachvollziehen der Abhängigkeiten zwischen Ein- und Ausgangsdaten von Transformationen.

## LZ 7-5 - Qualitätsstufen
Die Teilnehmer verstehen, dass über eine schrittweise Transformation eingehender Daten Qualitätsstufen (Quality-Gates) definiert werden können. Sie verstehen, dass damit je nach Art der Analyse Daten einer höheren (Clean Data) oder einer niedrigeren (Raw Data) herangezogen werden können.
Die Teilnehmer verstehen, dass Staging Areas (s. LZ 7-3) ein Quality Gate darstellen, mit dem sichergestellt wird, dass nur qualitätsgesicherte Daten zur Analyse in einem Data Warehouse bereitgestellt werden.
Die Teilnehmer verstehen, dass in einem Data Lake (s. LZ 7-3) Daten unterschiedlicher Qualitätsstufen gemeinsam aufbewahrt werden und dass es daher sinnvoll sein kann, Zonen unterschiedlicher Datenqualität (etwa Bronze, Silber, Gold) innerhalb von Data Lakes festzulegen.

# 8 - Presentation
## LZ - Personalisierung
## LZ - Auswertungen auf Data in Rest vs auf Data in Transit/Motion
## LZ - Ad-Hoc vs predefined Reports
## LZ - Dashboards / Pitchbooks
## LZ - Alerts
## LZ - Drill / Slice & Dice
## LZ - Visualisierungen
## LZ - Lastverteilung
## LZ - SDK
## LZ - Time Travelling

## LZ - Query Builder / Code Gen / Interactive Analytics

# 9 - Schema und Modeling
## LZ - Schema on write vs Schema on read
## LZ - Data in Rest vs Data in Transit/Motion
## LZ - Event vs State
## LZ - Welches Datenmodell ist geeignet
## LZ - Historie der Metadaten, Metadata Tracking
## LZ - Historie der Daten, Data Versioning 
## LZ - Schema Enforcement
## LZ - Schema Registry
## LZ - Granularität der Daten
## LZ - Schema Detection / Schema on the fly
## LZ - Schema on Read Data migration
Multiple Schemas, only last schema, lazy migration
## LZ - Schema Evolution
## LZ - Schema compatibility
Backward, Forward, * Transitive
## LZ - Arten von Schema Änderungen
Datensatz-Strukturen ergänzen oder entfernen, Attribute ergänzen oder entfernen, Datentyp Vergrößerung/Verkleinerung, Änderungen in Datensatz-Substrukturen
## LZ - ER vs Multidimensional (Data Vault) vs Document vs Graph 


# 10 - Data Pipelines
## LZ - Eigenschaften von Data Pipelines
Accessible, Scalable, Monitored, Efficient
## LZ - Arten von Data Pipelines
ETL vs ELT, reverse ETL, Microbatches vs Stream
Data Engineering, Analytics/ML Processing, Delivery 
## LZ - Stateful vs Stateless processing
## LZ - At least once vs Exactly once Processing
## LZ - Data Pipline Qualitätskriterien
Throughput, Reliability, Latency, Stability
## LZ - Wiederanlauf
Idempotenz, Append Only
## LZ - Building Blocks von Data Pipelines
Scheduler, Workflow Engine, Query Engine, HTTP/MQTT Endpoints, Message Broker, Low Cost/High Volume Data Storage, Stream Processing Engine, Data Catalog, ML Framework
## LZ - Technologien/Tools für Data Pipelines
SQL, Dataframes, Spark
## LZ - Stages
Ingestion, Transport, Storage, Transformation, Presentation
## LZ - Monitoring
## LZ - Optimization
## LZ - Cloud vs on-Premise
Edge-Computing


# 11 - Data Governance
## LZ - Was ist Data Governance
Welche Regeln sind im gegebenen Kontext erforderlich, welche davon global und welche lokal, wie können sie überprüft werden, wann müssen sie angepasst werden
## LZ - Anforderungen an Datenschutz
GDPR, DSGVO, Personally Identifiable Information (PII)
## LZ - least privilege best practice
## LZ - separation of duties
## LZ - Pseudonymization
## LZ - Encryption
## LZ - Data Lineage / Metadata Tracking
## LZ - Access Control (Data, Metadata)
Data-Centricity, Rich Access Policies, Scalability and Automation, Unified Visibility, Open / API-First Design, Hybrid and Multi-Cloud Ready
## LZ - Fine vs Course grained access control
## LZ - Weitere iSAQB-Module

## LZ- Metadaten
Die Teilnehmer kennen Programmiersprachen für die Spezifikation von Metadaten, wie etwa
- XML/JSON Schema
- ASN.1
- (SQL) DDL
- POJO

Die Teilnehmer wissen, dass Metadaten oft in Datenkatalogen, Metadatenrepositories oder Metadaten-Registries verwaltet werden.

# 12 - Data Mesh
In diesem Modul wird das sozio-technische Konzept des Data Mesh erläutert und motiviert. Die Teilnehmer lernen, wann eine dezentralisierte Datenarchitektur angemesssen ist. Sie lernen zudem die vier grundlegenden Data Mesh Prinzipien kennen:
- Domain Ownership
- Data as a Product
- Self-serve Data Platform
- Federated Computational Governance

Terms and concepts
Data Mesh, Domain-driven Design, Bounded Context, Context Mapping, Data as a Product, Product Thinking, Self-serve Data Platform, Federated Computational Governance, Team Topologies

Learning goals

## LZ 12-1 - Probleme zentralisierter Datenarchitekturen
Die Teilnehmer verstehen, aufgrund welcher Probleme zentrale Data-Teams nicht gut skalieren. Sie verstehen, warum dezentrale Domain-Teams nicht gut zu zentralen Data Teams passen.

## LZ 12-2: Domain Ownership
Die Teilnehmer kennen relevante Konzepte des Strategic Domain-Driven Design, wie Domains, Subdomains, Bounded Contexts und Context Mapping Patterns.
Die Teilnehmer verstehen, dass die Verantwortung für analytische Daten und deren Qualität von den zentralen Data Teams an die einzelnen Domain Teams übergeht.
Sie wissen, dass Domain Teams ihre eigenen analytischen Daten haben.
Sie wissen, dass Domain Teams die analytischen Daten ihrer Domain ihrem Unternehmen in Form von Datenprodukten zur Verfügung stellen.
Sie können die drei Archetypen von Datenprodukten in einem Data Mesh unterscheiden:
- source-aligned
- aggregate
- consumer-aligned

Die Teilnehmer verstehen die Bedeutung sowie das Problem von Polysemen als geteilte Konzepte zwischen unterschiedlichen Domains.

## LZ 12-3: Data as a Product

Understand that domain teams provide data to other teams as data products.
Understand that data products are first-class citizens in the system architecture, similar to UI and API products.
Know characteristics of data products: data are discoverable, addressable, trustworthy, self-descriptive, secure, understandable, interoperable, natively accessible, and valuable on their own.
Know the different forms of data products, including datasets, reports, dashboards, machine learning features or entire models.

## LZ 12-4: Self-serve Data Platform

Understand the key concepts of the domain-agnostic data infrastructure as a platform.
Know that the platform is managed by a data platform team.
Know typical components of a data platform, i.e. storage, data pipelines, data catalog, access management, monitoring, visualisation.
Are aware of existing solutions provided by cloud vendors.

## LZ 12-5: Federated Computational Governance

Know that the governance group, typically called a "guild", consists of representatives of the domain teams and the data platform team.
Know that the governance group agrees on global policies of the data eco-systems, including interoperability, security and compliance.
Understand that the self-serve data platform may support, automate, or enforce the global policies.

References

"Data Mesh in Action" by Jacek Majchrzak, Sven Balnojan, and Marian Siwiak. Manning. Publication in Summer 2022
"Data Mesh" by Zhamak Dehghani. O'Reilly Media, Inc. April 2022 datamesh-architecture.com
"Data Management at Scale" by Piethein Strengholt
"Software Architecture: The Hard Parts" by Neal Ford, Mark Richards, Pramod Sadalage, Zhamak Dehghani


------------------------------------
Maybe relevant stuff
------------------------------------
Lernziele

- Data Usage

- Unterschied Stream, Batch und Micro-Batch Processing
- Multidimensonale Modellierung (Fakten/Dimensionen, Events/Snapshots, Additiv/Semi-Additiv)
- Slowly Changing Dimensions
- Point In Time Zuordnungen
- Conformed Dimensions
- Idempotenz
- Aggregation
- Cubes
- Unterschied analytische/operative Daten
- Unterschied ETL/ELT
- Schema on Read / Schema on Write
- Alerts
- Drill Down/Up/Across
- Slice and Dice
- AdHoc Reporting
- SQL Generator
- Multidimensionale DB/(Wide)ColumnStore/
- Reporting (Pixel-Perfect)
- Dashboards
- Pitchbooks
- CDC
- Connectoren
- Schema
- Data Cleansing
- Data Integration/Unification/Harmonization
- Data Replication
- Consistency / eventual Consistency
- Query Engine
- Data Virtualisation
- DWH / DataLake / Data Marts
- Methoden
- Data Pipelines
- Rollen
- UseCases
- Referenzarchitekturen
- DataOps
- MultiCloud
- Skills needed
- fault tolerance, checkpointing, mid-query failures
- UDF
- Compact small files
- tests / great-expectations
- Data Lifecycle
Phases: Collection, Process, Store and secure, Use, Share and communicate, Archive, Destroy or re-use
Cross-Cutting Concerns: Purpose and value, Privacy, Data ownership, Liability, Public perception, Security, Standards and Data Quality
https://static.tti.tamu.edu/tti.tamu.edu/documents/PRC-17-84-F.pdf
Phases: Data Ingestion — Bringing raw data into the data environment, Data Transformation — logic applied to landed data to produce clean datasets, Testing & Deployment — Quality/validation tests applied during data publication, Monitoring & Debugging — Tracking data health and finding cause of errors
https://lakefs.io/what-is-data-lifecycle-management/
- DataOps
- Lifecycle
- closed-loop data engines
- data labeling
- feature stores
- low-code ML
- vector databases
- Apache Arrow
- Compaction
- Serverless
- Öffentliche Datasets
- Monitoring und Logging
- Location Transparency
- GIS
- Materialized Views
- Förderierte Abfragen
- NLP
- CEP

Architekturentscheidungen
- Grundlagen
  - operative/analytische Daten
    - Unterscheidung
    - Qualitative Anforderungen an analytische Daten
    - Anforderungen an Präsentation analytischer Daten
    - Anforderungen an Verarbeitung analytischer Daten
    - Randbedingungen analytischer Daten
  - Typische Use-Cases
- Sizing / Kosten / Skalierung / Optimierung
- Modularisierung
  - technisch
    - Sources / Ingestion und Transport / Storage / Query und Processing / Transformation / Analysis und Output
  - fachlich
  - Teamzusammensetzung / Rollen
- Test / Deployment / Betrieb
- Patterns / Best Practices / Methoden / Tools
- Referenzarchitekturen / Beispiele

