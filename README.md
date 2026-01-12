============================================================
           RAGNAROK+ PINGBOOST TOOLKIT (v2026)
============================================================

------------------------------------------------------------
DEUTSCH / GERMAN
------------------------------------------------------------

🚀 ÜBER DIESES TOOL
Dieses Toolkit optimiert deine Windows-Netzwerkeinstellungen auf Systemebene, 
um Verzögerungen (Input-Lag) zu minimieren und die Paketübertragung für 
Ragnarok+ zu beschleunigen.

⚠️ WICHTIGER HINWEIS: DATEI UMBENENNEN
Damit der Monitor und die Optimierungen funktionieren, MUSST du deine 
Spieldatei von "Ragnarok+.exe" in "Ragnarokplus.exe" umbenennen.
- Grund: Das Sonderzeichen "+" verursacht Fehler in der PowerShell-Überwachung.
- Stelle sicher, dass der Launcher (R+_PingBoost.bat) im selben Ordner liegt.

🛠 WAS WIRD VERBESSERT?
1. Nagle's Algorithm: Verhindert das Sammeln kleiner Pakete. Daten werden 
   SOFORT gesendet.
2. MTU-Optimierung: Verhindert Paket-Fragmentierung (Aufteilen von Daten), 
   was Paketverlust reduziert.
3. Network Throttling: Verhindert, dass Windows die Netzwerkleistung für 
   Hintergrunddienste drosselt.
4. Hardware-Tweaks: Deaktiviert die Interrupt-Moderation der Netzwerkkarte 
   für schnellere CPU-Reaktionszeiten.



🎮 NUTZUNG
1. Einmalig: Starte die "MTU_Finder.bat" als Administrator, um deine Leitung 
   zu kalibrieren. Das Tool testet mit 3 Versuchen pro Paketgröße für 
   maximale Genauigkeit.
2. Täglich: Starte das Spiel über die "R+_PingBoost.bat" (Rechtsklick -> Als 
   Administrator).
3. Monitor: Nach 30s erscheint ein farbiges Icon in der Taskleiste (unten rechts).
   - Rechtsklick auf das Icon -> "Show Statistics" zeigt Ping-Verlauf und 
     Packet Loss.
4. Beenden: Schließe einfach das Spiel. Alle Änderungen werden automatisch 
   auf Windows-Standard zurückgesetzt.
------------------------------------------------------------
🌟 COMMUNITY & CREDITS
------------------------------------------------------------

Ein riesiges Dankeschön an das Ragnarok+ Team für die harte 
Arbeit und an alle Spieler, die den Geist des Spiels am 
Leben erhalten! Auf gute gemeinsame Stunden beim Grinden! ❤️


============================================================

------------------------------------------------------------
ENGLISH / ENGLISCH
------------------------------------------------------------

🚀 ABOUT THIS TOOL
This toolkit performs low-level system optimizations to minimize input lag 
and accelerate data packet transmission for Ragnarok+.

⚠️ IMPORTANT: RENAME YOUR GAME FILE
For the monitor and optimizations to work, you MUST rename your game 
executable from "Ragnarok+.exe" to "Ragnarokplus.exe".
- Reason: PowerShell cannot accurately track processes containing the "+" character.
- Ensure the launcher (R+_PingBoost.bat) is in the same folder as the EXE.

🛠 TECHNICAL IMPROVEMENTS
1. Nagle's Algorithm: Stops Windows from buffering small packets. Actions 
   are sent INSTANTLY.
2. MTU Optimization: Prevents packet fragmentation, a major cause of 
   stuttering and packet loss.
3. Network Throttling: Prevents Windows from limiting gaming traffic in 
   favor of background services.
4. Hardware Tweaks: Disables "Interrupt Moderation" on your network card 
   to speed up packet processing.

🎮 HOW TO USE
1. Setup: Run "MTU_Finder.bat" as Administrator once to calibrate your 
   connection. It uses 3 retries per size for maximum precision.
2. Daily: Launch via "R+_PingBoost.bat" (Right-click -> Run as Administrator).
3. Monitor: After 30s, a colored icon appears in your system tray (bottom right).
   - Right-click Icon -> "Show Statistics" to view average ping and 
     Packet Loss.
4. Exit: Simply close the game. All system changes will automatically 
   revert to Windows defaults.

⚙️ MANUAL CONFIGURATION (IP/Port)
If the server IP changes, open "monitor.ps1" with Notepad and edit the 
$CONFIG section at the top:
- ServerAddress = "138.201.124.56"
- ServerPort = 5121


------------------------------------------------------------
🌟 COMMUNITY & CREDITS
------------------------------------------------------------

A huge shoutout to the Ragnarok+ Team for their hard work 
and to all players for keeping the spirit alive! 
Let's keep grinding together! ❤️

============================================================
============================================================
           RAGNAROK+ PINGBOOST TOOLKIT (v2026)
============================================================


