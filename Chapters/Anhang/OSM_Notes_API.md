## B. OSM Notes API – Beispiel

Neues Note anlegen (anonym):

```
POST https://api.openstreetmap.org/api/0.6/notes.json
?lat=<LAT>&lon=<LON>&text=<HINWEIS>
```

Antwort enthält u. a. eine ID für die Note. Hinweis: Notes sind öffentlich sichtbar; sensible Informationen vermeiden.
OAuth-Authentifizierung ist optional möglich und wird nur mit Opt-in unterstützt.