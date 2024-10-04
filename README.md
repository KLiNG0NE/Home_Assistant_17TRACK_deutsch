# Home Assistant 17TRACK deutsch


![Static Badge](https://img.shields.io/badge/Home_Assistant-2024.10.0-3BC5F3?logo=homeassistant&logoColor=white&logoSize=auto&label=Home%20Assistant&labelColor=3BC5F3&color=grey) ![Static Badge](https://img.shields.io/badge/17-TRACK-FF8C00?logoSize=auto&labelColor=FF8C00&color=003A9B&)


Mit diesen Markdown-Dateien werden die Ausgaben der _17TRACK-Integration_ im Frontend von _Home Assistant_ in die deutsche Sprache übersetzt.

Dies sind Markdown-Dateien, die im Frontend von Home Assistant genutzt werden können.

---

## Vorraussetzungen
1. Benutzerkonto _(kostenlos)_ bei 17TRACK:  
   [17track.net](https://www.17track.net/de)
1. Installation der Integration von 17TRACK in Home Assistant:  
   [home-assistant.io](https://www.home-assistant.io/integrations/seventeentrack/)

Deine Sendungsnummern kannst du anschließend auf der Website von 17TRACK eintragen. (Diese erhältst du normalerweise vom Versender deines Pakets.) – Unter _‚Memo‘_ solltest du am besten einen Hinweis zum Paketinhalt hinterlassen. Dieser wird später als „Paketname“ angezeigt.

---

## Einrichtung
1. Lege am besten in der Übersicht eine neue _Kategrie_ z. B. mit dem Namen ``Pakete`` oder ``Zustellungen`` an.  
   Als _‚Symbol‘_ kannst du z. B. ``mdi:package-variant-closed`` nutzen.
1. Füge eine neue _Karte_ hinzu.
1. Als Karten-Typ nutzt du _Markdown_.
1. Gib als _‚Titel‘_ einen sprechenden Namen wie ``Pakete in Zustellung`` an.
1. In dem Feld _‚Code‘_ kannst du den gewünschten Inhalt einer Markdown-Datei einfügen.
1. Füge auf gleiche Weise Karten für _„Pakete bereit zur Abholung“_ sowie _„Zugestellte Pakete“_ hinzu.
1. Bei der Karte _„Pakete bereit zur Abholung“_ bietet es sich an, die Sichbarkeit einzuschränken. Hierzu bei _‚Sichtbarkeit‘_ die Einträge ``Entitätszustand`` die Entität ``17Track Bereit zur Abholung`` und ``Zustand ist nicht gleich`` Zustand ``0`` eintragen. – So wird diese Karte nur angezeigt, sobald Pakete zur Abholung bereit sind.

---

#### Info
Dies ist ein rein privates Projekt. – Es bestehen weder mit [Home Assistant](https://www.home-assistant.io/) noch mit [17TRACK](https://www.17track.net/de) finanzielle Verbindungen.
