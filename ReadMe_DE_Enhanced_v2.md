# Ragnarok+ PingBoost Enhanced v2.0

## 📋 Überblick

Ragnarok+ PingBoost ist ein automatisiertes PowerShell-Tool, das die Netzwerkverbindung für Ragnarok+ optimiert und in Echtzeit den Ping zum Spielserver überwacht. Das Tool wendet bewährte Windows-Netzwerkoptimierungen an und zeigt die aktuelle Latenz in einem System Tray Icon an.

## ✨ Features

### Netzwerk-Optimierungen (Stufe 1)
- **Network Throttling deaktivieren**: Verhindert Windows-Netzwerkdrosselung
- **System Responsiveness maximieren**: Priorisiert Foreground-Anwendungen
- **QoS Policy**: Priorisiert Spielserver-Traffic mit DSCP Marking
- **Prozess-Priorität**: Setzt Ragnarok+ auf "High" Priorität
- **DNS Cache Optimierung**: Clearet Cache für optimale Namensauflösung
- **TCP Optimierungen**: TcpAckFrequency & TCPNoDelay aktiviert
- **MTU Anpassung**: Konfigurierbare Maximum Transmission Unit

### Monitoring & Statistiken
- **Echtzeit Ping-Anzeige**: Farbcodiertes System Tray Icon
  - 🟢 Grün: < 70ms (Ausgezeichnet)
  - 🟠 Orange: 70-130ms (Gut)
  - 🔴 Rot: > 130ms oder Verbindung verloren
- **Detaillierte Statistiken**: Min/Max/Durchschnitt, Packet Loss
- **Verlaufs-Tracking**: Speichert letzte 100 Messungen
- **Log-Datei**: Vollständiges Protokoll aller Optimierungen

### Sicherheit
- ✅ Automatisches Backup aller Original-Einstellungen
- ✅ Vollständiges Rollback beim Beenden
- ✅ Fehlerbehandlung für alle Optimierungen
- ✅ Keine gefährlichen System-Services werden gestoppt

## 🚀 Installation & Verwendung

### Voraussetzungen
- Windows 10/11 (oder Windows Server 2016+)
- PowerShell 5.1 oder höher
- **Administrator-Rechte** (erforderlich für Registry & QoS)
- Ragnarok+ Spiel installiert

### Installation

1. **Dateien in Ragnarok+ Ordner kopieren**
   - `R+PingBoost.exe` - Haupt-Launcher
   - `monitor.ps1` - PowerShell Script
   - `MTU_Finder.bat` - MTU-Optimierungs-Tool (optional)
   - **WICHTIG**: Alle Dateien müssen im gleichen Ordner wie Ragnarok+ sein!
   - Beispiel: `C:\Games\Ragnarok+\` (dort wo auch Ragnarok+.exe liegt)

2. **⚠️ WICHTIG: Ragnarok+ Executable umbenennen**
   - Im Ragnarok+ Ordner: Suche die Datei `Ragnarok+.exe`
   - **Benenne sie um in**: `Ragnarokplus.exe` (ohne + Zeichen!)
   - **Grund**: PowerShell hat Probleme mit dem "+" Zeichen im Dateinamen
   - **Hinweis**: Das Spiel funktioniert nach dem Umbenennen ganz normal!

3. **MTU optimieren** (Empfohlen)
   - **Rechtsklick** auf `MTU_Finder.bat` → "Als Administrator ausführen"
   - Das Tool testet automatisch verschiedene MTU-Werte zum Spielserver
   - Zeigt den optimalen MTU-Wert an
   - Erstellt automatisch die `mtu.cfg` Datei mit dem besten Wert
   - **Wichtig**: Diesen Schritt nur einmal durchführen!

4. **PingBoost starten**
   - **Rechtsklick** auf `R+PingBoost.exe` → **"Als Administrator ausführen"**
   - Das Tool startet automatisch:
     - Das PowerShell Script mit Admin-Rechten
     - Ragnarok+ (aus `Ragnarokplus.exe`)
   - Wendet alle Optimierungen automatisch an
   
   **Tipp**: Erstelle eine Verknüpfung und setze "Als Administrator ausführen" in den Eigenschaften, dann reicht später ein Doppelklick!

**Alternativ: Manuelle MTU-Konfiguration**
   - Erstelle eine Datei `mtu.cfg` im gleichen Ordner
   - Trage deinen MTU-Wert ein (z.B. `1472`)
   - Falls nicht vorhanden, wird Standard-MTU 1500 verwendet

### Ablauf

1. Starte `R+PingBoost.exe` per Rechtsklick → "Als Administrator ausführen"
2. Launcher startet automatisch:
   - PowerShell Script mit Optimierungen
   - Ragnarok+ (aus `Ragnarokplus.exe`)
3. Script wartet 30 Sekunden (Countdown)
4. Wendet alle Optimierungen an sobald Ragnarok+ läuft
5. Startet Ping-Monitoring (alle 3 Sekunden)
6. Zeigt Ping im System Tray Icon
7. Bei Spiel-Ende: Automatisches Cleanup & Rollback

## 📊 Verwendung

### System Tray Icon
- **Rechtsklick** auf Icon öffnet Menü:
  - **Show Statistics**: Detaillierte Ping-Statistiken
  - **View Log**: Öffnet Log-Datei in Notepad
  - **Exit & Reset Settings**: Beendet Script und setzt alle Einstellungen zurück

### Log-Datei
- Datei: `pingboost.log` (im Script-Ordner)
- Zeigt alle angewendeten Optimierungen
- Protokolliert Fehler und Warnungen
- Format: `[HH:mm:ss] [TYPE] Nachricht`

## ⚙️ Konfiguration

### MTU_Finder.bat - Automatische MTU-Optimierung

**Verwendung:**
1. **Rechtsklick** auf `MTU_Finder.bat` → "Als Administrator ausführen"
2. Das Tool testet MTU-Werte von 1500 bis 1200 in 8-Byte-Schritten
3. Zeigt für jeden Wert ob Fragmentierung notwendig ist
4. Empfiehlt den optimalen MTU-Wert
5. Erstellt automatisch `mtu.cfg` mit dem besten Wert

**Ausgabe-Beispiel:**
```
Testing MTU to 138.201.124.56...
MTU 1500: Needs fragmentation
MTU 1492: Needs fragmentation
MTU 1472: OK - No fragmentation!
MTU 1464: OK - No fragmentation!

Optimal MTU: 1472
Created mtu.cfg with value: 1472
```

**Hinweis**: MTU-Finder muss nur **einmal** ausgeführt werden, außer:
- Du wechselst den Internetanbieter
- Du wechselst Router/Modem
- Du verwendest VPN (VPN hat oft niedrigere MTU)

### mtu.cfg - Manuelle Konfiguration
```
1472
```
Empfohlene MTU-Werte:
- **1500**: Standard Ethernet
- **1472**: Optimal für viele DSL-Verbindungen
- **1492**: PPPoE-Verbindungen
- **1452**: Einige Kabel-/Glasfaser-Verbindungen

MTU testen (manuell):
```cmd
ping 138.201.124.56 -f -l 1472
```
Reduziere den Wert wenn "Paket muss fragmentiert werden" erscheint.

**Tipp**: Verwende `MTU_Finder.bat` statt manueller Tests!

### Verknüpfung mit Auto-Admin erstellen (Optional)

So musst du nicht jedes Mal Rechtsklick machen:

1. **Rechtsklick** auf `R+PingBoost.exe` → "Verknüpfung erstellen"
2. **Rechtsklick** auf die Verknüpfung → "Eigenschaften"
3. Klicke auf "Erweitert..." Button
4. Häkchen bei "Als Administrator ausführen"
5. OK → Übernehmen → OK
6. Ab jetzt: Einfach Doppelklick auf die Verknüpfung!

### Server-Konfiguration
Im Script anpassen (Zeile 6-7):
```powershell
ServerAddress  = "138.201.124.56"
ServerPort     = 5121
```

## 🔧 Was wird geändert?

### Registry-Einstellungen
```
HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile
├── NetworkThrottlingIndex = 0xffffffff (Standard: 10)
└── SystemResponsiveness = 0 (Standard: 20)

HKLM:\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces\{GUID}
├── TcpAckFrequency = 1
└── TCPNoDelay = 1
```

### Netzwerk-Einstellungen
- **MTU**: Gesetzt auf konfigurierten Wert
- **QoS Policy**: "RagnarokPlus_QoS" mit DSCP 46
- **DNS Cache**: Geleert bei Start

### Prozess-Einstellungen
- **Ragnarokplus.exe**: PriorityClass = "High"

**Alle Änderungen werden beim Script-Ende automatisch rückgängig gemacht!**

## 📈 Erwartete Verbesserungen

- ✅ **5-15ms** niedrigere durchschnittliche Latenz
- ✅ **Weniger Latenz-Spikes** durch deaktiviertes Throttling
- ✅ **Stabilere Verbindung** durch QoS-Priorisierung
- ✅ **Flüssigeres Gameplay** durch höhere Prozess-Priorität

**Hinweis**: Tatsächliche Verbesserungen hängen von deiner Internet-Verbindung, Hardware und Netzwerk-Konfiguration ab.

## ❗ Wichtige Hinweise

### Sicherheit
- ✅ Script ändert nur temporäre Netzwerk-Einstellungen
- ✅ Keine Daten werden heruntergeladen oder hochgeladen
- ✅ Keine externen Verbindungen außer zum Spielserver
- ✅ Open Source - Code ist einsehbar

### Bekannte Einschränkungen
- Erfordert Administrator-Rechte
- Funktioniert nur während Ragnarok+ läuft
- QoS funktioniert am besten mit QoS-fähigem Router
- Einige Netzwerkadapter unterstützen nicht alle Optimierungen

### Fehlerbehebung

**R+PingBoost.exe startet nicht**
- **Rechtsklick** → **"Als Administrator ausführen"** (sehr wichtig!)
- Prüfe ob PowerShell installiert ist
- Antivirus könnte .exe blockieren (Ausnahme hinzufügen)
- Windows SmartScreen: "Weitere Informationen" → "Trotzdem ausführen"

**Ragnarok+ startet nicht automatisch**
- Prüfe ob `Ragnarok+.exe` in `Ragnarokplus.exe` umbenannt wurde!
- **Prüfe ob alle Dateien im Ragnarok+ Ordner sind!**
- Prüfe ob Ragnarokplus.exe vorhanden und funktionsfähig ist
- Antivirus könnte Ragnarokplus.exe blockieren

**MTU_Finder.bat zeigt Fehler**
- Als Administrator ausführen
- Prüfe Internetverbindung
- Firewall könnte ICMP (Ping) blockieren

**"Execution Policy" Fehler**
```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

**QoS Policy Fehler**
- Prüfe ob Windows Firewall aktiv ist
- Prüfe ob Group Policy QoS blockiert

**Script findet Spiel nicht**
- **Wichtig**: Hast du `Ragnarok+.exe` in `Ragnarokplus.exe` umbenannt?
- Prüfe ob Prozessname korrekt ist (`Ragnarokplus.exe`)
- Warte bis Spiel vollständig geladen ist
- Starte R+PingBoost.exe als Administrator

**Hohe CPU-Nutzung**
- Normal: Script nutzt <1% CPU
- Falls höher: Prüfe Log auf Fehler-Loops

## 🔄 Updates & Versionen

### v2.0 (Aktuell)
- ✅ Stufe 1 Optimierungen implementiert
- ✅ Backup & Rollback System
- ✅ Logging-System
- ✅ Verbesserte Statistiken

### v1.0
- Basis-Netzwerkoptimierungen
- Ping-Monitoring
- System Tray Icon

## 📝 Lizenz & Haftung

Dieses Tool wird "wie besehen" bereitgestellt. Der Autor übernimmt keine Haftung für:
- Systemänderungen
- Verbindungsprobleme
- Spielprobleme
- Datenverlust

**Verwende auf eigene Verantwortung!**

Empfohlen: Erstelle einen Windows-Wiederherstellungspunkt vor der ersten Verwendung.

## 🆘 Support & Kontakt

- **Log-Datei prüfen**: `pingboost.log` enthält detaillierte Fehlerinfos
- **Script zurücksetzen**: "Exit & Reset Settings" im Tray-Menü
- **Manuelles Rollback**: Windows neu starten setzt die meisten Einstellungen zurück

## 🙏 Danksagungen

Dieses Tool wurde mit ❤️ für die Ragnarok+ Community entwickelt.

**Besonderen Dank an:**
- **Alle Ragnarok+ Spieler** - Für eure Unterstützung, euer Feedback und eure Leidenschaft für das Spiel. Ihr macht die Community großartig!
- **Die Serverbetreiber von Ragnarok+** - Für eure harte Arbeit, den stabilen Server und das tolle Spielerlebnis, das ihr für uns alle erschafft. Danke, dass ihr dieses großartige Projekt am Leben haltet!
- **Die Community** - Für Testing, Bug-Reports und Verbesserungsvorschläge

Dieses Tool basiert auf bewährten Windows-Netzwerkoptimierungen für Gaming und wurde speziell für Ragnarok+ angepasst.

**Ihr seid großartig! Gemeinsam machen wir Ragnarok+ noch besser!** 🎮✨

---

**Viel Erfolg und niedrigen Ping!** 🎮🚀