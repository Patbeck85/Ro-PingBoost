================================================================================
    RAGNAROK+ PINGBOOST - SCHNELLSTART-ANLEITUNG
    Windows 7 / 8 / 10 / 11 kompatibel
================================================================================

🚀 IN 4 SCHRITTEN ZUM BESSEREN PING!

--------------------------------------------------------------------------------
SCHRITT 0: DATEIEN IN RAGNAROK+ ORDNER KOPIEREN
--------------------------------------------------------------------------------

📁 Kopiere ALLE Dateien in deinen Ragnarok+ Installations-Ordner:
   - R+PingBoost.exe
   - RagnarokPingBoost.ps1
   - MTU_Finder.bat

   Beispiel: C:\Games\Ragnarok+\
   (Dort wo auch Ragnarok+.exe liegt!)

   ⚠️ WICHTIG: Alle Dateien MÜSSEN im gleichen Ordner sein!

--------------------------------------------------------------------------------
SCHRITT 1: RAGNAROK+ UMBENENNEN (Einmalig, sehr wichtig!)
--------------------------------------------------------------------------------

⚠️ DIESER SCHRITT IST ZWINGEND ERFORDERLICH! ⚠️

1. Im Ragnarok+ Ordner: Suche die Datei "Ragnarok+.exe"
2. Rechtsklick → "Umbenennen"
3. Neuer Name: "Ragnarokplus.exe" (OHNE das + Zeichen!)
4. Enter drücken

   ❓ Warum? PowerShell hat Probleme mit dem "+" Zeichen!
   ✅ Das Spiel funktioniert danach ganz normal weiter!

--------------------------------------------------------------------------------
SCHRITT 2: MTU OPTIMIEREN (Nur einmal nötig!)
--------------------------------------------------------------------------------

1. Rechtsklick auf "MTU_Finder.bat"
2. "Als Administrator ausführen" wählen
3. Warten bis der optimale MTU-Wert gefunden wurde
4. Fertig! Die Datei "mtu.cfg" wird automatisch erstellt

   ⏱️ Dauert ca. 30 Sekunden

--------------------------------------------------------------------------------
SCHRITT 3: VERKNÜPFUNG ERSTELLEN (Empfohlen, macht das Leben einfacher!)
--------------------------------------------------------------------------------

1. Rechtsklick auf "R+PingBoost.exe"
2. "Verknüpfung erstellen" wählen
3. Rechtsklick auf die neue Verknüpfung → "Eigenschaften"
4. Klick auf "Erweitert..." Button
5. Häkchen bei "Als Administrator ausführen" setzen
6. OK → Übernehmen → OK
7. Verknüpfung auf den Desktop ziehen (optional)

   ✅ Ab jetzt: Nur noch Doppelklick statt Rechtsklick!

--------------------------------------------------------------------------------
SCHRITT 4: PINGBOOST STARTEN
--------------------------------------------------------------------------------

Option A - Mit Verknüpfung (empfohlen):
   → Doppelklick auf die Verknüpfung
   → R+PingBoost startet automatisch Ragnarok+
   → Fertig!

Option B - Ohne Verknüpfung:
   1. Rechtsklick auf "R+PingBoost.exe"
   2. "Als Administrator ausführen" wählen
   3. R+PingBoost startet automatisch Ragnarok+
   4. Fertig!

Das war's! PingBoost läuft jetzt und Ragnarok+ startet! 🎮

================================================================================
WAS PASSIERT JETZT?
================================================================================

✅ R+PingBoost startet automatisch Ragnarok+ (aus Ragnarokplus.exe)
✅ Sobald das Spiel läuft, werden alle Optimierungen aktiviert
✅ Du siehst ein buntes Icon im System Tray (Taskleiste rechts unten):
   🟢 Grün   = Ping unter 70ms (Ausgezeichnet!)
   🟠 Orange = Ping 70-130ms (Gut)
   🔴 Rot    = Ping über 130ms oder Verbindungsprobleme

✅ Rechtsklick auf das Icon zeigt:
   - "Show Statistics" → Zeigt detaillierte Ping-Infos
   - "View Log" → Zeigt was PingBoost gemacht hat
   - "Exit & Reset Settings" → Beendet PingBoost sauber

✅ Wenn du Ragnarok+ beendest:
   - PingBoost beendet sich automatisch
   - Alle Einstellungen werden zurückgesetzt
   - Dein System ist wieder im Original-Zustand

================================================================================
TÄGLICHE NUTZUNG
================================================================================

1. Starte R+PingBoost (über Verknüpfung oder Rechtsklick)
2. Ragnarok+ startet automatisch
3. Spiele mit besserem Ping! 🎮
4. Beende Ragnarok+ wenn fertig
5. PingBoost räumt automatisch auf

Das war's! Jeden Tag das gleiche - ganz einfach! ✨

================================================================================
HÄUFIGE FRAGEN
================================================================================

❓ Muss ich MTU_Finder jedes Mal ausführen?
   → Nein! Nur einmal, außer du wechselst Internet/Router/VPN

❓ Funktioniert das auf Windows 7?
   → JA! Vollständig kompatibel (außer QoS Policy)
   → QoS ist nur ein kleiner Teil, Rest funktioniert!
   → Eventuell PowerShell 5.1 nachinstallieren

❓ Muss ich Ragnarok+.exe wirklich umbenennen?
   → JA! Sehr wichtig! PowerShell funktioniert sonst nicht!
   → Umbenennen in: Ragnarokplus.exe (ohne +)

❓ Müssen die Dateien im Ragnarok+ Ordner sein?
   → JA! Alle Dateien müssen dort sein wo auch Ragnarok+ installiert ist!

❓ Vergesse ich manchmal "Als Administrator"?
   → Erstelle eine Verknüpfung mit Auto-Admin (siehe Schritt 3)!

❓ Wie sehe ich ob es funktioniert?
   → Rechtsklick auf Tray-Icon → "Show Statistics"
   → Oder öffne "pingboost.log" im Script-Ordner

❓ Mein Antivirus blockiert die .exe!
   → Normal bei unbekannten Tools, einfach Ausnahme hinzufügen
   → Die .exe ist sicher und macht nur Netzwerk-Optimierungen

❓ Kann ich PingBoost immer laufen lassen?
   → Ja! Es startet Ragnarok+ automatisch und beendet sich auch automatisch

❓ Ragnarok+ startet nicht?
   → Hast du Ragnarok+.exe in Ragnarokplus.exe umbenannt?
   → Sind ALLE Dateien im Ragnarok+ Ordner?
   → Ist R+PingBoost.exe im gleichen Ordner wie Ragnarokplus.exe?

❓ Was wenn ich Probleme habe?
   → Schau in "README_DE.md" → Fehlerbehebung
   → Oder öffne "pingboost.log" für Details

================================================================================
ERWARTETE VERBESSERUNGEN
================================================================================

Was du merken solltest:
✅ 5-15ms niedrigerer Ping im Durchschnitt
✅ Weniger "Lag-Spikes" (Ping-Aussetzer)
✅ Flüssigeres, responsiveres Gameplay
✅ Stabilere Verbindung zum Server

Hinweis: Die tatsächliche Verbesserung hängt von deiner
         Internet-Verbindung und deinem System ab!

================================================================================
WICHTIG!
================================================================================

⚠️ IMMER "Als Administrator ausführen"!
   → Ohne Admin-Rechte kann PingBoost nichts optimieren

⚠️ ALLE Dateien müssen im Ragnarok+ Ordner sein!
   → R+PingBoost.exe, .ps1 und .bat im gleichen Ordner wie das Spiel

⚠️ Ragnarok+.exe MUSS in Ragnarokplus.exe umbenannt werden!
   → PowerShell hat Probleme mit dem "+" Zeichen
   → Einmalig machen, dann funktioniert alles!

⚠️ Nicht einfach beenden!
   → Verwende "Exit & Reset Settings" im Tray-Menü
   → Oder beende einfach Ragnarok+ (Auto-Cleanup!)

================================================================================
SUPPORT
================================================================================

📖 Ausführliche Anleitung: README_DE.md
📝 Was wurde geändert: CHANGELOG.md
📋 Log-Datei anschauen: pingboost.log (im Script-Ordner)

Viel Spaß und niedrigen Ping! 🎮🚀

Die Ragnarok+ Community ❤️

================================================================================