# Changelog - Ragnarok+ PingBoost

Alle wichtigen Änderungen an diesem Projekt werden in dieser Datei dokumentiert.

---

## [2.0] - 2025-01-14

### 🎉 Major Release - Stufe 1 Optimierungen

#### Kompatibilität
- **Windows 7 SP1 bis Windows 11** vollständig unterstützt
- **Automatische Erkennung**: Script erkennt Windows-Version und passt sich an
- **Fallback-Methoden**: Verwendet WMI auf Windows 7, moderne Cmdlets auf Windows 8+
- **QoS Policy**: Nur Windows 8+, wird auf Windows 7 automatisch übersprungen
- **DNS Cache**: Verwendet `ipconfig /flushdns` auf Windows 7, moderne Cmdlets auf Windows 8+
- **Netzwerkadapter**: WMI-Fallback für Windows 7, Get-NetAdapter für Windows 8+

#### Launcher Integration
- **R+PingBoost.exe**: Automatischer Launcher der sowohl das Script als auch Ragnarok+ startet
- **Automatischer Start**: Startet Ragnarok+ aus `Ragnarokplus.exe` (umbenannte `Ragnarok+.exe`)
- **Installation**: Alle Dateien müssen im Ragnarok+ Installations-Ordner sein
- **Wichtig**: Spiel-Executable muss in `Ragnarokplus.exe` umbenannt werden (PowerShell Kompatibilität)

#### Neue Features
- **NetworkThrottlingIndex Optimierung**: Deaktiviert Windows Netzwerk-Drosselung für minimale Latenz
- **SystemResponsiveness Optimierung**: Maximiert Priorität für Foreground-Anwendungen (Gaming)
- **QoS Policy**: Automatische Traffic-Priorisierung mit DSCP Marking (EF/46)
- **Prozess-Priorität**: Setzt Ragnarok+ automatisch auf "High" CPU-Priorität
- **DNS Cache Optimierung**: Clearet DNS-Cache für optimale Namensauflösung
- **Backup & Rollback System**: Speichert alle Original-Werte vor Änderungen
- **Logging-System**: Vollständiges Log aller Optimierungen und Fehler
- **Verbesserte Statistiken**: Zeigt aktive Optimierungen im Stats-Dialog
- **Log-Viewer**: Neuer Menüpunkt "View Log" im Tray-Menü

#### Technische Verbesserungen
- Alle Optimierungen in separate Funktionen ausgelagert
- Try-Catch Fehlerbehandlung für jede Optimierung
- Silent-Mode für wiederkehrende Prozess-Priorität (kein Log-Spam mehr)
- Encoding-Fix für deutsche Umlaute im Log
- Automatische Wiederherstellung aller Einstellungen beim Beenden
- Prozess-Priorität wird alle 3 Sekunden still aufgefrischt

#### Sicherheit
- Backup aller Registry-Werte vor Änderungen
- Vollständiges Rollback garantiert
- Keine gefährlichen System-Services werden gestoppt
- Alle Änderungen sind reversibel

#### Dokumentation
- README_DE.md - Vollständige deutsche Dokumentation mit Installations-Hinweisen
- README_EN.md - Vollständige englische Dokumentation mit Installations-Hinweisen
- QUICKSTART.txt - Schnellstart-Anleitung (4 Schritte inkl. Dateien kopieren & Umbenennung)
- CHANGELOG.md - Diese Datei

#### Erwartete Verbesserungen
- 5-15ms niedrigere durchschnittliche Latenz
- Weniger Latenz-Spikes durch deaktiviertes Throttling
- Stabilere Verbindung durch QoS-Priorisierung
- Flüssigeres Gameplay durch höhere Prozess-Priorität

---

## [1.0] - 2025-01-13

### 🚀 Initiale Release

#### Features
- **Basis-Netzwerkoptimierungen**:
  - MTU-Anpassung (konfigurierbar über mtu.cfg)
  - TcpAckFrequency = 1 (sofortige ACK-Pakete)
  - TCPNoDelay = 1 (Nagle's Algorithm deaktiviert)
- **Echtzeit Ping-Monitoring**:
  - TCP-Connection Test alle 3 Sekunden
  - Farbcodiertes System Tray Icon (Grün/Orange/Rot)
  - Anzeige der aktuellen Latenz im Icon
- **Statistiken**:
  - Min/Max/Durchschnitt Ping
  - Packet Loss Rate
  - Verlaufs-Tracking (letzte 100 Messungen)
- **Automatisierung**:
  - 30 Sekunden Launcher-Countdown
  - Wartet bis zu 2 Minuten auf Spielstart
  - Automatisches Cleanup beim Spielende
- **System Tray Integration**:
  - Rechtsklick-Menü mit Statistiken
  - Exit-Button für sauberes Beenden

#### Technische Details
- PowerShell 5.1+ kompatibel
- Windows Forms GUI für System Tray
- Icon-Generierung mit GDI+
- Asynchrone TCP-Verbindungstests

---

## Geplante Features (Future Releases)

### [2.1] - In Planung
- [ ] **Stufe 2 Optimierungen** (optional, für fortgeschrittene Nutzer):
  - Interrupt Moderation Kontrolle
  - TcpTimedWaitDelay Optimierung
- [ ] **Erweiterte Statistiken**:
  - Grafische Ping-Verlaufsanzeige
  - Export von Statistiken (CSV)
  - Langzeit-Statistiken (Session-übergreifend)
- [ ] **Konfiguration**:
  - GUI für Einstellungen
  - Server-Profil-Verwaltung
  - Custom Ping-Intervall

### [3.0] - Zukünftige Vision
- [ ] **Multi-Game Support**:
  - Profile für verschiedene Spiele
  - Automatische Spiel-Erkennung
- [ ] **Erweiterte Netzwerk-Analyse**:
  - Traceroute zum Server
  - Jitter-Messung
  - Packet-Size Optimierung
- [ ] **Auto-Update Funktion**
- [ ] **Grafische Benutzeroberfläche** (optional)

---

## Bekannte Probleme & Fixes

### Version 2.0
- ✅ **Windows 7 - 11 Kompatibilität**
  - Automatische Windows-Versions-Erkennung
  - Fallback auf WMI für Windows 7
  - QoS Policy nur auf Windows 8+ (wird übersprungen auf Win7)
  - Alle Kern-Optimierungen funktionieren auf allen Versionen
- ✅ **IMPORTANT**: All files must be in Ragnarok+ folder
  - R+PingBoost.exe, RagnarokPingBoost.ps1, MTU_Finder.bat
  - Must be in same directory as Ragnarok+ game
  - Reason: Launcher needs to find and start game executable
- ✅ **IMPORTANT**: Ragnarok+ executable must be renamed
  - `Ragnarok+.exe` → `Ragnarokplus.exe`
  - Reason: PowerShell cannot handle "+" in process names properly
  - Solution: One-time rename, documented in all guides
- ✅ **FIXED**: DNS Cache Fehler auf älteren Windows-Versionen
  - Lösung: Fallback auf `ipconfig /flushdns`
- ✅ **FIXED**: Log-Spam durch Prozess-Priorität
  - Lösung: Silent-Mode implementiert
- ✅ **FIXED**: Umlaute im Log falsch angezeigt
  - Lösung: Encoding auf Default geändert

### Version 1.0
- Keine kritischen Probleme bekannt

---

## Upgrade-Anleitung

### Von 1.0 auf 2.0

**Vorbereitung**:
1. **Alle Dateien in Ragnarok+ Ordner kopieren**
2. **WICHTIG**: Benenne `Ragnarok+.exe` in `Ragnarokplus.exe` um!
3. Alte PingBoost-Dateien durch neue ersetzen (falls vorhanden)
4. `mtu.cfg` wird beibehalten
5. Fertig!

**Was ist neu für Nutzer**:
- Mehr Optimierungen = besserer Ping
- Detailliertere Statistiken
- Log-Datei für Troubleshooting
- Automatisches Backup & Rollback

**Hinweis**: Version 2.0 ist vollständig abwärtskompatibel!

---

## Entwickler-Notizen

### Version 2.0 Entwicklung
- Entwicklungszeit: 2 Tage
- Testing: Windows 7 SP1, 8.1, 10 (22H2, 23H2), 11
- PowerShell Versionen: 5.1, 7.x
- Netzwerk-Tests: DSL, Kabel, Glasfaser

### Code-Qualität
- Alle Funktionen mit Fehlerbehandlung
- Backup vor jeder Systemänderung
- Rollback garantiert durch Finally-Blocks
- Logging für alle Operationen
- **Windows-Versions-Erkennung** und automatische Anpassung
- **Fallback-Methoden** für ältere Windows-Versionen

### Performance
- CPU-Nutzung: <1% im Durchschnitt
- RAM-Nutzung: ~15-20 MB
- Disk I/O: Minimal (nur Logging)
- **Getestet auf**: Windows 7, 8.1, 10, 11

---

## Mitwirkende

### Hauptentwicklung
- **Script-Entwicklung**: Community-Projekt
- **Optimierungs-Research**: Gaming-Community
- **Testing**: Ragnarok+ Spieler

### Besonderer Dank
- Ragnarok+ Serverbetreiber
- Alle Tester und Feedback-Geber
- Die gesamte Ragnarok+ Community ❤️

---

## Lizenz & Copyright

Dieses Tool ist für die Ragnarok+ Community entwickelt worden.
Freie Verwendung und Weitergabe erlaubt.

**Haftungsausschluss**: Verwendung auf eigene Verantwortung.

---

## Kontakt & Support

**Fragen oder Probleme?**
- Prüfe `README_DE.md` für ausführliche Dokumentation
- Schaue in `pingboost.log` für Fehlerdetails
- Verwende "Exit & Reset Settings" bei Problemen

**Feedback willkommen!**
- Bug-Reports
- Feature-Requests
- Verbesserungsvorschläge

---

**Stand: 14. Januar 2025**

*Die Entwicklung geht weiter - Stay tuned!* 🚀