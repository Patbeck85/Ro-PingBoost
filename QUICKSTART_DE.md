# ⚡ Ragnarok+ PingBoost - Schnellstart

**In 3 Minuten zu besserem Ping!**

---

## 🚀 Schnellinstallation

### 1️⃣ Download
Lade diese 2 Dateien herunter:
- ✅ `Ragnarok_PingBoost.vbs`
- ✅ `monitor.ps1`

### 2️⃣ Installation
Kopiere beide Dateien in deinen **Ragnarok-Ordner** (wo deine `Ragnarokplus.exe` liegt)

### 3️⃣ Starten
```
Rechtsklick auf Ragnarok_PingBoost.vbs
→ "Als Administrator ausführen"
```

### 4️⃣ Fertig!
- MTU wird automatisch getestet (15 Sek)
- Game startet automatisch
- Ping-Monitor erscheint in der Taskleiste

---

## 📊 Was bedeuten die Farben?

| Icon | Bedeutung | Ping | Jitter | Loss |
|------|-----------|------|--------|------|
| 🟢 | **EXZELLENT** | < 50ms | < 10ms | 0% |
| 🟡 | **GUT** | < 100ms | < 20ms | < 2% |
| 🟠 | **PROBLEMATISCH** | < 150ms | < 30ms | < 5% |
| 🔴 | **KRITISCH** | > 150ms | > 30ms | > 5% |

---

## 🎯 Die 3 wichtigsten Funktionen

### 1. Automatischer MTU-Test
Beim ersten Start findet das Script **automatisch** den besten MTU-Wert für deinen Server.

**Du musst nichts tun!** ✨

### 2. Echtzeit Ping-Monitor
Sieh deinen Ping **direkt in der Taskleiste**:
- Aktueller Ping-Wert im Icon
- Hover für Details (Jitter, Packet Loss, Statistiken)

### 3. Automatischer Rollback
Nach Spielende werden **alle Änderungen rückgängig gemacht**.

**Dein System bleibt sicher!** 🔒

---

## ⚙️ Häufigste Einstellungen

### Server-IP ändern
**Wenn du einen anderen Ragnarok-Server nutzt:**

1. Öffne `Ragnarok_PingBoost.vbs` mit Editor
2. Suche Zeile ~91: `serverIP = "138.201.124.56"`
3. Ändere die IP zu deinem Server
4. Speichern & Script neu starten

### MTU neu testen
**Wenn deine Verbindung sich ändert:**

1. Lösche Datei `mtu_test.txt`
2. Script neu starten
3. MTU wird automatisch neu getestet

### Monitor-Einstellungen ändern
**Server-IP oder Prozess-Name ändern:**

- **Rechtsklick** auf Tray-Icon
- **"Change Server/Process"** wählen
- Neue Werte eingeben

---

## ❓ Häufige Probleme (Quick Fix)

### ❌ "Script startet nicht"
**Lösung:** Als Administrator ausführen!
```
Rechtsklick → Als Administrator ausführen
```

### ❌ "Game wird nicht gefunden"
**Lösung:** 
1. Lösche `R+_settings.ini`
2. Script neu starten
3. Richtigen Game-Namen eingeben (z.B. `Ragnarokplus.exe`)

### ❌ "Ping-Monitor zeigt nichts"
**Lösung:**
1. Lösche `monitor_settings.ini`
2. Script neu starten
3. Server-IP und Prozess-Name eingeben

### ❌ "Optimierungen funktionieren nicht"
**Lösung:** Prüfe `pingboost.log` Datei für Fehler

---

## 🔄 Normale Verwendung

### Jeden Tag spielen:

1. **Starte Script** (als Admin)
2. **Spiele Ragnarok**
3. **Beende Game**
4. **Klicke OK** in PingBoost-Meldung
5. **Fertig!** ✅

### Das wars! Kein kompliziertes Setup nötig.

---

## 💡 Pro-Tipps

### Tipp #1: Taskleiste immer sichtbar
Stelle Windows so ein, dass die Taskleiste immer sichtbar ist:
- So siehst du deinen Ping **während** du spielst!

### Tipp #2: MTU regelmäßig testen
Teste MTU alle 2-3 Monate neu:
- Internetanbieter ändern manchmal Einstellungen
- Lösche `mtu_test.txt` und lass Script neu testen

### Tipp #3: Log-Datei checken
Bei Problemen immer zuerst `pingboost.log` öffnen:
- Zeigt genau was das Script macht
- Hilft bei der Fehlersuche

### Tipp #4: Vergleiche vorher/nachher
Notiere deinen Ping **vor** und **nach** PingBoost:
- So siehst du die Verbesserung!
- Typische Verbesserung: 5-20ms weniger Ping

---

## 📱 Erweiterte Features

### Rechtsklick auf Monitor-Icon
- **Change Server/Process** - Einstellungen ändern
- **Exit Monitor** - Monitor beenden

### Hover über Monitor-Icon
Zeigt:
- Current/Average/Min/Max Ping
- Current/Average/Max Jitter  
- Packet Loss (%)
- Verbindungsqualität-Rating

---

## 🎮 Was wird optimiert?

### Netzwerk
✅ MTU automatisch optimiert  
✅ Nagle's Algorithm deaktiviert  
✅ Network Throttling deaktiviert  
✅ TCP-Parameter optimiert  
✅ DNS-Cache geleert  

### Hardware
✅ Interrupt Moderation aus  
✅ Energy Efficient Ethernet aus  
✅ Receive Side Scaling an  

### System
✅ Game-Priorität: HIGH  
✅ Windows Game Mode  
✅ GPU Scheduling  
✅ Hintergrunddienste gestoppt  

---

## 📞 Hilfe benötigt?

**Reihenfolge:**
1. ✅ Diese Quick-Start-Guide lesen
2. ✅ `README_DE.md` lesen (detaillierte Anleitung)
3. ✅ `pingboost.log` prüfen
4. ✅ Issue erstellen mit Log-Datei

---

## ⚡ Zusammenfassung

```
Download → In Ragnarok-Ordner kopieren → Als Admin starten → Fertig!
```

**So einfach ist das!** 🎯

Viel Spaß mit niedrigerem Ping! 🎮✨