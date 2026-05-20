# REST-API für die ToDo-Anwendung

Die ToDo-Anwendung soll das Erstellen, Lesen, Aktualisieren und Löschen von ToDos ermöglichen. Aufgrund der Anfangsbuchstaben der englischen
Worte **C**reate, **R**ead, **U**pdate und **D**elete spricht man auch von _CRUD_ Operationen.

Eine übliche Implementierung ist es, diese vier Operationen auf entsprechende HTTP-Methoden und URLs abzubilden:

| Operation | Methode | URL          | Beschreibung                                                                                                       |
| --------- | ------- | ------------ | ------------------------------------------------------------------------------------------------------------------ |
| Create    | POST    | `/todos`     | Anlegen eines neuen ToDos. Die ID wird dabei vom Backend vergeben.                                                 |
| Read      | GET     | `/todos/:id` | Lesen des ToDos mit ID `id`. Die Syntax `:id` wird von Express.js verwendet, <br> um _Path Parameter_ zu spezifizieren. |
| Read      | GET     | `/todos`     | Lesen der Liste _aller_ ToDos.                                                                                     |
| Update    | PUT     | `/todos/:id` | Update des ToDos mit ID `id`.                                                  |
| Delete    | DELETE  | `/todos/:id` | Löschen des ToDos mit ID `id`.                                                  |

## Aufgabe 1: Lesen aller ToDos

Wir verwenden vorerst noch ein Array für die Speicherung der ToDos (s. [index.js](index.js)).

- [ ] Implementieren Sie mithilfe von _Express.js_ für Route `/todos` die Methode _GET_. Diese soll die Liste der ToDos zurückgeben.
      Orientieren Sie sich dabai am [Hello World Beispiel](https://expressjs.com/de/starter/hello-world.html) von Express.
      Denken Sie daran, dass Sie auch die Methode `app.listen()` aufrufen müssen.
- [ ] Testen Sie mithilfe von `curl`, dass Ihre Anwendung funktioniert.
- [ ] Richten Sie ggf. in Ihrer Entwicklungsumgebung eine passende Portweiterleitung ein und testen Sie die Route mithilfe Ihres Webbrowsers.

## Aufgabe 2: Vollständiges REST-API

Implementieren und testen Sie die übrigen Operationen. Hierbei können Sie als Gruppe gleich das parallele Arbeiten üben, d.h. jedes Mitglied jetzt
eine Funktion um und hinterher mergen Sie Ihren Code.

- [ ] Create zum Anlegen eines ToDos,
- [ ] Read eines einzelnen ToDos,
- [ ] Update eines ToDos,
- [ ] Delete eines ToDos.

> [!IMPORTANT]
> **Achten Sie auf die richtigen Status-Codes im Erfolgsfall**: 
> - Create sollte `201` (created) zurückgeben,
> - Delete sollte `204` (no content) zurückgeben.

> [!NOTE]  
> Um den Inhalt des Requests (den *Body*) als JSON-Objekt zu lesen, müssen Sie den *Body-Parser* aktivieren:
> ```javascript
> app.use(express.json());
> ```
