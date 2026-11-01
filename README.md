# WG-Putzplan

Gemeinsamer Putzplan für großes Bad, kleines Bad, Küche, Wohnung saugen und eine wechselnde Sonderaufgabe, dazu eine gemeinsame Einkaufsliste. Fünf Leute (Flo, Yurai, Son, Dominik, Bram) wechseln sich wöchentlich ab. Abhaken, Tauschen und die Einkaufsliste werden über Firebase Firestore synchronisiert. Es gibt keinen Login, wer den Link hat, kann eintragen.

## Einrichtung (eigenes Firebase-Projekt)

1. **Projekt anlegen:** In der [Firebase-Konsole](https://console.firebase.google.com) auf „Projekt hinzufügen“, Name z. B. `wg-putzplan`. Google Analytics kannst du ausschalten.
2. **Firestore:** Build → Firestore Database → Datenbank erstellen. Produktionsmodus, Standort `eur3 (europe)`.
3. **Regeln:** Firestore → Regeln, den Inhalt von `firestore.rules` einfügen und veröffentlichen.
4. **Web-App:** Projekteinstellungen (Zahnrad) → Deine Apps → Web-Symbol `</>`, Name `Putzplan`. Den angezeigten `firebaseConfig`-Block oben im Script von `index.html` einfügen.
5. **Online stellen**, eine der beiden Varianten:
   - **GitHub Pages:** Repo `wg-putzplan` anlegen, die Dateien hochladen, Settings → Pages → Branch `main`, Ordner `/ (root)`.
   - **Firebase Hosting:** Im Ordner `npm install -g firebase-tools`, dann `firebase login`, `firebase use --add` (Projekt wählen), `firebase deploy`. Die Seite liegt danach unter `wg-putzplan.web.app`, Regeln werden gleich mit hochgeladen.
6. Link in die WG-Gruppe schicken. Auf dem Handy über „Zum Startbildschirm hinzufügen“ fühlt es sich wie eine App an.

## Anpassen

- Personen und Reihenfolge: `PEOPLE` im Script.
- Aufgaben: `TASKS` im Script. Neue Aufgaben-IDs auch in `firestore.rules` ergänzen.
- Startwoche der Rotation: `ANCHOR` (ein Montag).
