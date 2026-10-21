# Haushaltspunkte einrichten

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
4. Unter **Verlauf → Jemanden einladen** den Link teilen. Die andere Person öffnet ihn, tippt „Beitreten“ und gibt ihren Namen ein.

## Gut zu wissen
- **Handy gewechselt oder Browserdaten gelöscht?** Mit dem Code wieder beitreten und auf „Ich bin …“ tippen. Es geht nichts verloren.
- **Offline:** Was ihr ohne Netz eintragt, wird übertragen, sobald wieder Verbindung besteht.
- **Kostenlose Grenzen:** Firestore erlaubt im Spark-Tarif 50.000 Lesezugriffe und 20.000 Schreibzugriffe pro Tag. Für einen Haushalt reicht das um ein Vielfaches. Wird ein Limit doch erreicht, pausiert die Datenbank bis zum nächsten Tag. Es entstehen keine Kosten.
- **Sicherheit:** Wer den 8-stelligen Code kennt, kann mitmachen. Teilt ihn also nur mit eurer Wohnung.
- **App ändern:** Neue Version von `index.html` im GitHub-Repository hochladen. `config.js` bleibt dabei unverändert.
