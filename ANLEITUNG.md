# Kakaokasse einrichten

Einmalig etwa 15 Minuten. Danach braucht niemand ein Konto: Die anderen öffnen einfach den Einladungslink.
Alles läuft im kostenlosen Tarif von Firebase („Spark“) und auf GitHub Pages. Eine Kreditkarte braucht ihr nicht.

Du brauchst einmalig ein Google-Konto (für Firebase) und ein GitHub-Konto (für die Webseite).

## 1. Firebase-Projekt anlegen
1. Öffne https://console.firebase.google.com und melde dich mit deinem Google-Konto an.
2. „Projekt erstellen“ → Name z. B. `haushaltspunkte` → Google Analytics kannst du ausschalten.
3. Wenn nach einem Tarif gefragt wird: beim kostenlosen **Spark**-Tarif bleiben. Kein Abrechnungskonto verknüpfen, sonst wird das Projekt automatisch auf den Bezahltarif umgestellt.

## 2. Web-App registrieren und config.js ausfüllen
1. Auf der Projektübersicht auf das Web-Symbol **</>** klicken („App hinzufügen“).
2. Spitzname z. B. `punkte`. Firebase Hosting **nicht** anhaken.
3. Firebase zeigt einen Block `const firebaseConfig = { apiKey: "...", ... }`.
4. Öffne `config.js` und ersetze die `HIER_EINFUEGEN`-Werte durch diese Werte.

Die Werte sind nicht geheim. Eure Daten schützen die Regeln aus Schritt 4.

## 3. Anonyme Anmeldung einschalten
Menü links: **Build → Authentication → Loslegen → Anmeldemethode → Anonym → Aktivieren → Speichern**.

Damit bekommt jedes Handy unsichtbar eine Geräte-ID. Niemand muss sich registrieren.

## 4. Datenbank anlegen
1. Menü links: **Build → Firestore Database → Datenbank erstellen**.
2. Falls gefragt: Edition **Standard**. Standort **europe-west3 (Frankfurt)**. Modus **Produktion**.
3. Reiter **Regeln**: Lösche den vorhandenen Text, füge den kompletten Inhalt von `firestore.rules` ein und klicke **Veröffentlichen**.

## 5. Webseite kostenlos veröffentlichen (GitHub Pages)
1. Auf https://github.com anmelden → oben rechts **+ → New repository** → Name `haushaltspunkte` → **Public** → **Create repository**.
2. Auf „uploading an existing file“ klicken und **alle Dateien aus diesem Ordner** hineinziehen (index.html, config.js, manifest.webmanifest, die drei icon-PNGs). Unten **Commit changes**.
3. **Settings → Pages** → bei „Branch“ `main` und `/ (root)` wählen → **Save**.
4. Nach 1–2 Minuten ist die App erreichbar unter `https://DEIN-GITHUB-NAME.github.io/haushaltspunkte/`.
5. Zur Sicherheit in Firebase: **Authentication → Einstellungen → Autorisierte Domains → Domain hinzufügen** → `DEIN-GITHUB-NAME.github.io`.

## 6. Loslegen
1. Öffne die Adresse auf deinem Handy.
2. **Tipp:** Füge die Seite zuerst zum Home-Bildschirm hinzu (iPhone: Teilen → „Zum Home-Bildschirm“; Android: Menü → „App installieren“) und öffne sie von dort. Auf dem iPhone merkt sich die Home-Bildschirm-App ihre Gruppe getrennt von Safari.
3. „Neue Gruppe gründen“ → deinen Namen eingeben.
4. Unter **Gruppe → Jemanden einladen** den Link teilen. Die andere Person öffnet ihn, tippt „Beitreten“ und gibt ihren Namen ein.

## Master, Rechte und Passwort
- Wer die Gruppe gründet, ist **Master**. Unter **Gruppe → Mitglieder → Verwalten** kann ein Master anderen Master-Rechte geben oder entziehen. Es bleibt immer mindestens ein Master.
- Master geben neue Aufgaben, Belohnungen und Freitext-Punkte frei, verwalten die Gruppe und können einzelnen Personen Rechte entziehen: Erledigtes bestätigen, Vorschläge machen, Freitext melden.
- Erledigte Aufgaben zählen erst, wenn jemand anderes sie bestätigt. Niemand kann sich selbst bestätigen.
- Unter **Gruppe → Gruppe verwalten** (nur für Master): Gruppenname und **Beitritts-Passwort**. Ist es gesetzt, brauchen neue Mitglieder Code und Passwort.

## Push-Nachrichten (kostenlos über ntfy)
1. In der App unter **Gruppe → Push-Nachrichten** auf **Push einrichten** tippen.
2. Die kostenlose App **ntfy** aus dem App Store bzw. Google Play Store installieren.
3. In ntfy auf **+** tippen und das angezeigte Thema eintragen (Server: ntfy.sh). Mit **Test senden** prüfen.
Das Thema ist dein persönlicher Kanal. Gib es nicht weiter.

## Archiv
- Abgeschlossene Einträge, die älter als 60 Tage sind, fasst die App automatisch pro Person zu einem **Übertrag** zusammen. Die Einzelheiten wandern ins Archiv: **Verlauf → Älteren Verlauf laden**.
- Der Kontostand bleibt dabei exakt gleich. So bleibt die App auch nach Jahren schnell und innerhalb der kostenlosen Grenzen.
- Dafür muss in den Firestore-Regeln `'archive'` in der Liste der erlaubten Sammlungen stehen (siehe `firestore.rules`).

## Gut zu wissen
- **Handy gewechselt oder Browserdaten gelöscht?** Mit dem Code wieder beitreten, auf „Ich bin …“ tippen und mit dem persönlichen Passwort anmelden. Es geht nichts verloren.
- **Persönliches Passwort:** Jede Person legt beim Beitreten ein eigenes Passwort fest. Ändern unter **Gruppe → Mitglieder → Passwort ändern**. Vergessen? Ein Master kann es unter **Verwalten** zurücksetzen.
- **Offline:** Was ihr ohne Netz eintragt, wird übertragen, sobald wieder Verbindung besteht.
- **Kostenlose Grenzen:** Firestore erlaubt im Spark-Tarif 50.000 Lesezugriffe und 20.000 Schreibzugriffe pro Tag. Für einen Haushalt reicht das um ein Vielfaches. Wird ein Limit doch erreicht, pausiert die Datenbank bis zum nächsten Tag. Es entstehen keine Kosten.
- **Sicherheit:** Wer den 8-stelligen Code kennt, kann mitmachen. Teilt ihn also nur mit eurer Wohnung.
- **App ändern:** Neue Version von `index.html` im GitHub-Repository hochladen. `config.js` bleibt dabei unverändert.
