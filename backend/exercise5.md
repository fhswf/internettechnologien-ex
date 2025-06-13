## Aufgabe 1: Validierung der Daten

Gehen Sie wie folgt vor, um `express-validator` zur Überprüfung der Daten in Ihrem REST API zu verwenden:

1. Installieren Sie das Paket `express-validator`:

```bash
npm install express-validator
```

2. Importieren Sie `express-validator` in der Datei, in der Sie Ihre Routen definieren (z.B. `todos.js`):

```javascript
import { check, validationResult } from 'express-validator';
```

3. Fügen Sie Validierungsregeln für die gewünschten Routen hinzu. Zum Beispiel, um die Titel bei der Erstellung eines neuen Todos zu validieren, fügen Sie die folgenden Regeln hinzu:

```javascript
const todoValidationRules = [
  check('title')
    .notEmpty()
    .withMessage('Titel darf nicht leer sein')
    .isLength({ min: 3 })
    .withMessage('Titel muss mindestens 3 Zeichen lang sein'),
];
```

4. Fügen Sie die Validierungsregeln als Middleware in Ihren Routen hinzu:

```javascript
app.post('/todos', todoValidationRules, async (req, res) => {
  // ...
});
```

5. Überprüfen Sie, ob Validierungsfehler aufgetreten sind, und senden Sie gegebenenfalls eine Fehlerantwort:

```javascript
app.post('/todos', todoValidationRules, async (req, res) => {
  const errors = validationResult(req);
  if (!errors.isEmpty()) {
    return res.status(422).json({ errors: errors.array() });
  }

  // Ihre Logik zum Erstellen eines neuen Todos
});
```

In diesem Beispiel haben wir die Validierung des Titels beim Erstellen eines neuen Todos hinzugefügt. 
**Erstellen Sie weitere Validierungsregeln für andere Routen und fügen Sie sie entsprechend hinzu.**

Weitere Informationen und Beispiele zur Verwendung von `express-validator` finden Sie in der offiziellen [Dokumentation](https://express-validator.github.io/docs/).
