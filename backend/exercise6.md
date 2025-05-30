# Praktikum 6: Testen des Backends

In dieser Aufgabe sollen Sie automatisierte Tests für Ihr Express.js-Backend schreiben.

## Aufgabe 1: Einrichtung von Jest und Supertest

1. Installieren Sie die Pakete `jest` und `supertest`:

    ```bash
    npm install --save-dev jest supertest
    ```

2. Fügen Sie in Ihrer `package.json` folgendes hinzu, um Jest als Test-Runner zu verwenden:

    ```json
    "scripts": {
      "test": "jest"
    }
    ```

3. Erstellen Sie eine Datei `jest.config.js` im Projektverzeichnis mit folgendem Inhalt, um die Unterstützung für ECMAScript-Module (ESM) zu aktivieren:

    ```js
    export default {
      testEnvironment: 'node',
      transform: {},
    };
    ```

    > [!IMPORTANT] 
    > **Hinweis:** Falls Sie ESM verwenden (z.B. `type: "module"` in Ihrer `package.json`), stellen Sie sicher, dass Sie die neueste Jest-Version nutzen und Ihre Testdateien die Endung `.test.js` haben.

## Aufgabe 2: Schreiben Sie einen ersten Test

1. Legen Sie eine Datei `backend/index.test.js` an.
2. Schreiben Sie einen Test, der prüft, ob die Route `GET /todos` erfolgreich eine Liste von Todos zurückgibt.

   Beispiel:

   ```js
   import request from 'supertest';
   import app from './index.js';

   describe('GET /todos', () => {
     it('sollte eine Liste von Todos zurückgeben', async () => {
       const res = await request(app).get('/todos');
       expect(res.statusCode).toBe(200);
       expect(Array.isArray(res.body)).toBe(true);
     });
   });
   ```

   > **Hinweis:** Exportieren Sie Ihr Express-App-Objekt in [`index.js`](index.js), damit Sie es im Test importieren können.

3. Führen Sie den Test aus:

   ```bash
   npm test
   ```

   Sie sollten eine Ausgabe sehen, die bestätigt, dass der Test erfolgreich war.

## Aufgabe 3: Weitere Tests

- Schreiben Sie weitere Tests für die Endpunkte POST, PUT und DELETE.
- Testen Sie auch Fehlerfälle, z.B. das Abrufen eines nicht existierenden Todos.
- Berücksichtigen Sie auch Szenarien:
    - **Hinzufügen eines neuen Todos**
      Überprüfen Sie, dass das Hinzufügen eines neuen Todos erfolgreich ist und das Todo in der Antwort zurückgegeben wird. Stellen Sie sicher, dass die Antwort den richtigen Statuscode (201 Created) hat und das Todo-Objekt anschließend per GET-Anfrage abgerufen werden kann.
    - **Aktualisieren eines bestehenden Todos**
      Überprüfen Sie, dass das Aktualisieren eines bestehenden Todos erfolgreich ist und das aktualisierte Todo in der Antwort zurückgegeben wird. Stellen Sie sicher, dass die Antwort den richtigen Statuscode (200 OK) hat und das Todo-Objekt die erwarteten Änderungen aufweist.
    - **Löschen eines Todos**
      Überprüfen Sie, dass das Löschen eines Todos erfolgreich ist und die Antwort den richtigen Statuscode (204 No Content) hat. Stellen Sie sicher, dass das Todo anschließend nicht mehr abgerufen werden kann.

Weitere Informationen finden Sie in der [Jest-Dokumentation](https://jestjs.io/) und der [Supertest-Dokumentation](https://github.com/ladjs/supertest).