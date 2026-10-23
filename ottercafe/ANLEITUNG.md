# Café Otterliebe einrichten

Das Café nutzt dasselbe Firebase-Projekt und dasselbe GitHub-Repository wie die Kakaokasse.
Es liegt im Unterordner `ottercafe/`, die Kakaokasse läuft unverändert weiter.

## 1. Firestore-Regeln ergänzen (einmalig)
1. https://console.firebase.google.com/project/haushaltspunkte-28d07/firestore/databases/-default-/rules öffnen.
2. Den Block **„Café Otterliebe (neu)“** aus `firestore.rules` direkt unter den Kakaokasse-Block einfügen
   (vor den beiden letzten schließenden Klammern `}`).
3. Darin `DEIN-PASSWORT` durch dasselbe Gründungs-Passwort ersetzen, das schon oben steht.
4. **Veröffentlichen.**

## 2. Dateien hochladen
1. Im GitHub-Repo `haushaltspunkte` auf **Add file → Upload files**.
2. Den ganzen Ordner `ottercafe` hineinziehen (nicht nur die Dateien darin).
3. **Commit changes.**
4. Nach 1–2 Minuten: `https://kf6glhye.github.io/haushaltspunkte/ottercafe/`

## 3. Café eröffnen
1. Die Adresse auf dem Handy öffnen und zum Home-Bildschirm hinzufügen.
2. **Neues Café eröffnen**: Gründungs-Passwort, Name, persönliches Passwort. Wer eröffnet, ist **Wirt**.
3. Unter **Café → Jemanden einladen** den Link schicken. Neue Personen setzen sich als **Gast** dazu.

## So funktioniert das Café
- **Karte:** Der Wirt schreibt Gerichte mit Punkten und Kategorie. Specials gibt es einmalig mit Countdown oder jede Woche an einem Tag (mit Erinnerung per Push).
- **Bestellen:** Der Gast bestellt jetzt oder für später. Der Wirt serviert unter **Bestellungen**. Erst serviert, dann auf dem Deckel.
- **Deckel:** zählt alle servierten Bestellungen. Ab der Grenze (Start 100, einstellbar unter **Café**) ist die Rechnung fällig; bestellt werden kann trotzdem.
- **Gefallen:** Der Wirt bietet sie mit Wert an, der Gast nimmt an und bezahlt damit. Mehr bezahlt als offen? Das wird Guthaben.
- **Extras:** Wunsch-Brett, Preis-Meinung (fair / zu teuer), Monatsrückblick mit „Liebling des Monats“.
- **Push:** unter **Café → Push-Nachrichten** über die App ntfy, für jede Person einzeln einstellbar.

## Datenmenge
Pro Woche gibt es ein Dokument mit allen Bestellungen. Wochen, die älter als 10 Wochen sind und nichts Offenes mehr enthalten,
werden automatisch in einen Übertrag gefaltet. Ein Öffnen der App liest so rund 10 Dokumente.
