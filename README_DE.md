# 🎮 Ragnarok+ PingBoost

**Professionelles Netzwerk-Optimierungs-Tool für Ragnarok Online**

Reduziert Ping, Jitter und Paketverlust durch intelligente System- und Netzwerk-Optimierungen.

---

## ✨ Features

### 🚀 Netzwerk-Optimierungen
- **Automatische MTU-Erkennung** - Findet den optimalen MTU-Wert für deinen Server
- **TCP-Parameter-Tuning** - Deaktiviert Nagle's Algorithm, optimiert Retransmissions
- **Hardware-Optimierungen** - Interrupt Moderation, Energy Efficient Ethernet
- **QoS-Freigabe** - Gibt reservierte Bandbreite frei (20% zusätzliche Geschwindigkeit)
- **DNS-Cache-Optimierung** - Schnellere Verbindungsaufbauten

### 📊 Echtzeit-Monitoring
- **Ping-Anzeige** im System Tray mit farbigem Icon
- **Jitter-Messung** - Erkennt instabile Verbindungen
- **Paketverlust-Tracking** - Zeigt Verbindungsqualität
- **Statistiken** - Durchschnitt, Min/Max Werte
- **Verbindungsqualität-Rating** (Excellent, Good, Fair, Poor)

### 🎯 Game-Optimierungen
- **Prozess-Priorität** auf "High"
- **CPU-Affinity** optimiert
- **Windows Game Mode** aktiviert
- **GPU Hardware Scheduling** aktiviert
- **Hintergrunddienste** temporär gestoppt

### 🔒 Sicherheit
- **Automatisches Registry-Backup** vor ersten Änderungen
- **Vollständiger Rollback** nach Spielende
- **Logging-System** - Alle Aktionen werden protokolliert
- **Admin-Rechte-Check** - Warnt bei fehlenden Berechtigungen

---

## 📦 Installation

### Voraussetzungen
- Windows 10/11
- Administrator-Rechte
- Ragnarok Online Client

### Setup
1. **Dateien herunterladen:**
   - `Ragnarok_PingBoost.vbs`
   - `monitor.ps1`

2. **Beide Dateien in den gleichen Ordner kopieren** (z.B. in deinen Ragnarok-Ordner)

3. **Erster Start:**
   - Rechtsklick auf `Ragnarok_PingBoost.vbs`
   - **"Als Administrator ausführen"** wählen
   - Game-Exe-Name eingeben (z.B. `Ragnarokplus.exe`)

---

## 🚀 Verwendung

### Starten
```
Rechtsklick → Ragnarok_PingBoost.vbs → Als Administrator ausführen
```

### Beim ersten Start
1. **MTU-Test läuft automatisch** (10-15 Sekunden)
   - Testet optimalen MTU-Wert zu deinem Server
   - Speichert Ergebnis für zukünftige Nutzung

2. **Optimierungen werden angewendet:**
   - Netzwerk-Parameter
   - Hardware-Einstellungen
   - Registry-Tweaks

3. **Game startet automatisch**

4. **Ping-Monitor erscheint im System Tray:**
   - 🟢 Grün = Exzellente Verbindung (< 50ms, Jitter < 10ms)
   - 🟡 Gelb = Gute Verbindung (50-100ms)
   - 🟠 Orange = Problematische Verbindung (hoher Jitter/Ping)
   - 🔴 Rot = Kritisch (Paketverlust > 10% oder keine Verbindung)

### Während des Spielens
- **Hover über Tray-Icon** für detaillierte Statistiken
- **Rechtsklick auf Icon** für Optionen:
  - Change Server/Process
  - Exit Monitor

### Beenden
1. **Game schließen**
2. **OK klicken** in der PingBoost-Meldung
3. **Alle Optimierungen werden automatisch rückgängig gemacht**
4. **System kehrt zu Standardwerten zurück**

---

## 📊 Monitoring-Details

### Tray-Icon zeigt:
- **Aktueller Ping-Wert** (z.B. "42" = 42ms)
- **Farbcode** für Verbindungsqualität

### Tooltip zeigt (beim Hovern):
```
Ragnarok+ Monitor
━━━━━━━━━━━━━━━
Server: 138.201.124.56
Quality: ★ EXCELLENT ★

Ping:
  Current: 42ms
  Average: 45ms
  Min: 38ms / Max: 58ms

Jitter:
  Current: 3ms
  Average: 5ms
  Max: 12ms

Packet Loss:
  0.5% (2/400 lost)
```

---

## ⚙️ Konfiguration

### Server-IP ändern
**Datei:** `Ragnarok_PingBoost.vbs`  
**Zeile ~91:**
```vbscript
serverIP = "138.201.124.56"  ' <--- Hier deine Server-IP eintragen
```

### MTU neu testen
**Option 1:** Beim Start "NO" klicken wenn gefragt  
**Option 2:** Datei `mtu_test.txt` löschen und Script neu starten

### Monitor-Einstellungen ändern
- Rechtsklick auf Tray-Icon → "Change Server/Process"
- Oder Datei `monitor_settings.ini` löschen

---

## 📁 Erstellte Dateien

Das Script erstellt folgende Dateien:

| Datei | Beschreibung |
|-------|-------------|
| `R+_settings.ini` | Gespeicherte Game-Exe Einstellung |
| `monitor_settings.ini` | Server-IP und Prozess-Name |
| `mtu_test.txt` | Optimaler MTU-Wert |
| `pingboost.log` | Alle Aktionen und Fehler |
| `network_backup.reg` | Registry-Backup (beim ersten Start) |
| `priority.ps1` | Temporär für Prozess-Priorität (wird gelöscht) |

---

## 🔧 Optimierungen im Detail

### Netzwerk
- **MTU:** Automatisch getestet und optimiert
- **Nagle's Algorithm:** Deaktiviert (TcpAckFrequency=1, TCPNoDelay=1)
- **Network Throttling:** Deaktiviert (Index=4294967295)
- **TCP Auto-Tuning:** Normal
- **TCP Timestamps:** Deaktiviert
- **Initial RTO:** 2000ms → 2000ms (optimiert)
- **Max Retransmissions:** 3 (reduziert)

### Hardware
- **Interrupt Moderation:** Deaktiviert
- **Energy Efficient Ethernet:** Deaktiviert
- **Flow Control:** Deaktiviert
- **Large Send Offload:** Deaktiviert
- **Receive Side Scaling:** Aktiviert

### System
- **Windows Game Mode:** Aktiviert
- **GPU Hardware Scheduling:** Aktiviert
- **Prozess-Priorität:** High
- **CPU-Affinity:** Alle Cores
- **Dienste gestoppt:** Windows Search, Superfetch, DiagTrack

---

## ❗ Wichtige Hinweise

### ⚠️ Administrator-Rechte erforderlich
Das Script **MUSS** als Administrator ausgeführt werden, sonst funktionieren die Optimierungen nicht!

### 🔄 Automatischer Rollback
**Alle Änderungen werden automatisch rückgängig gemacht**, wenn du das Script beendest. Dein System bleibt sicher!

### 📝 Logging
Alle Aktionen werden in `pingboost.log` gespeichert. Bei Problemen diese Datei prüfen.

### 🔒 Sicherheit
- Registry-Backup wird automatisch erstellt
- Keine permanenten Systemänderungen
- Alle Werte werden nach Spielende wiederhergestellt

---

## 🐛 Troubleshooting

### Script startet nicht
- **Lösung:** Als Administrator ausführen
- **Prüfe:** `pingboost.log` für Fehlermeldungen

### Game wird nicht gefunden
- **Lösung:** `R+_settings.ini` löschen und neu starten
- **Prüfe:** Game-Exe ist im gleichen Ordner wie das Script

### Monitor zeigt keine Daten
- **Lösung 1:** Prüfe ob `monitor_settings.ini` korrekte Server-IP hat
- **Lösung 2:** Firewall/Antivirus könnte Ping blockieren
- **Lösung 3:** `monitor_settings.ini` löschen und neu konfigurieren

### MTU-Test schlägt fehl
- **Lösung 1:** Prüfe Internetverbindung
- **Lösung 2:** Firewall könnte ICMP blockieren
- **Lösung 3:** Server-IP in Script prüfen (Zeile ~91)

### Optimierungen funktionieren nicht
- **Prüfe:** Script als Administrator gestartet?
- **Prüfe:** `pingboost.log` für Fehlermeldungen
- **Lösung:** `network_backup.reg` doppelklicken um Backup wiederherzustellen

---

## 🎯 Empfohlene Werte

### Verbindungsqualität
- **Exzellent:** Ping < 50ms, Jitter < 10ms, 0% Loss
- **Gut:** Ping < 100ms, Jitter < 20ms, < 2% Loss
- **Akzeptabel:** Ping < 150ms, Jitter < 30ms, < 5% Loss
- **Schlecht:** Ping > 150ms, Jitter > 30ms, > 5% Loss

### MTU-Werte
- **1500** - Standard Ethernet (Kabel)
- **1492** - PPPoE DSL-Verbindungen
- **1460-1472** - Optimal für die meisten Gaming-Verbindungen
- **1400** - Konservativ für instabile Verbindungen

---

## 📞 Support

Bei Problemen oder Fragen:
1. Prüfe `pingboost.log` Datei
2. Prüfe diese README
3. Erstelle ein Issue mit Log-Datei

---

## 📜 Lizenz

Dieses Tool ist kostenlos und open-source.

**Nutzung auf eigene Gefahr!** Das Script ändert Systemeinstellungen. Auch wenn alle Änderungen automatisch rückgängig gemacht werden, nutze es verantwortungsvoll.

---

## 🙏 Credits

Entwickelt für die Ragnarok Online Community.

**Viel Spaß beim Spielen mit optimiertem Ping!** 🎮✨