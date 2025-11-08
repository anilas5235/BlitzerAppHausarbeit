# Anhang

## A. Beispiel-Overpass-Queries

### A.1 Stationäre Blitzer (robust: mehrere Tags)

```
[out:json][timeout:25];
(
  node["highway"="speed_camera"]({{bbox}});
  node["man_made"="speed_camera"]({{bbox}});
  node["enforcement"="maxspeed"]({{bbox}});
);
out tags center;
```

Hinweise: bbox = süd, west, nord, ost; Rate-Limits beachten; kleinere Bounding Boxes und inkrementelle Updates
bevorzugen.

### A.2 Geschwindigkeitsbegrenzungen (Kontext)

```
[out:json][timeout:25];
way["maxspeed"]({{bbox}});
out tags center;
```

## B. OSM Notes API – Beispiel

Neues Note anlegen (anonym):

```
POST https://api.openstreetmap.org/api/0.6/notes.json
?lat=<LAT>&lon=<LON>&text=<HINWEIS>
```

Antwort enthält u. a. eine ID für die Note. Hinweis: Notes sind öffentlich sichtbar; sensible Informationen vermeiden.
OAuth-Authentifizierung ist optional möglich und wird nur mit Opt-in unterstützt.

## C. Glossar (Ergänzung)

- OSM: OpenStreetMap – offene Geodatenplattform.
- Overpass API: Dienst/Abfragesprache für OSM-Daten (Read-Only).
- OSM Notes: Einfaches Meldesystem in OSM, mit Koordinate + Text.
- Nominatim: Geocoding/Reverse-Geocoding für OSM.
- Geofencing: Ereignisbasierte Standortüberwachung beim Betreten/Verlassen definierter Regionen.
- TTL (Time To Live): Gültigkeitsdauer von Cache-Einträgen.

