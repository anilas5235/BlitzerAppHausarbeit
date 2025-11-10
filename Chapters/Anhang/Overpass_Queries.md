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