# 🎮 Ragnarok+ PingBoost

**Professional Network Optimization Tool for Ragnarok Online**

Reduces ping, jitter, and packet loss through intelligent system and network optimizations.

---

## ✨ Features

### 🚀 Network Optimizations
- **Automatic MTU Detection** - Finds optimal MTU value for your server
- **TCP Parameter Tuning** - Disables Nagle's Algorithm, optimizes retransmissions
- **Hardware Optimizations** - Interrupt Moderation, Energy Efficient Ethernet
- **QoS Release** - Frees reserved bandwidth (20% additional speed)
- **DNS Cache Optimization** - Faster connection establishment

### 📊 Real-time Monitoring
- **Ping Display** in System Tray with colored icon
- **Jitter Measurement** - Detects unstable connections
- **Packet Loss Tracking** - Shows connection quality
- **Statistics** - Average, Min/Max values
- **Connection Quality Rating** (Excellent, Good, Fair, Poor)

### 🎯 Game Optimizations
- **Process Priority** set to "High"
- **CPU Affinity** optimized
- **Windows Game Mode** enabled
- **GPU Hardware Scheduling** enabled
- **Background Services** temporarily stopped

### 🔒 Security
- **Automatic Registry Backup** before first changes
- **Complete Rollback** after game ends
- **Logging System** - All actions are logged
- **Admin Rights Check** - Warns about missing permissions

---

## 📦 Installation

### Requirements
- Windows 10/11
- Administrator rights
- Ragnarok Online Client

### Setup
1. **Download files:**
   - `Ragnarok_PingBoost.vbs`
   - `monitor.ps1`

2. **Copy both files to the same folder** (e.g., your Ragnarok folder)

3. **First Start:**
   - Right-click on `Ragnarok_PingBoost.vbs`
   - Select **"Run as Administrator"**
   - Enter game exe name (e.g., `Ragnarokplus.exe`)

---

## 🚀 Usage

### Starting
```
Right-click → Ragnarok_PingBoost.vbs → Run as Administrator
```

### First Start
1. **MTU test runs automatically** (10-15 seconds)
   - Tests optimal MTU value to your server
   - Saves result for future use

2. **Optimizations are applied:**
   - Network parameters
   - Hardware settings
   - Registry tweaks

3. **Game starts automatically**

4. **Ping monitor appears in System Tray:**
   - 🟢 Green = Excellent connection (< 50ms, Jitter < 10ms)
   - 🟡 Yellow = Good connection (50-100ms)
   - 🟠 Orange = Problematic connection (high jitter/ping)
   - 🔴 Red = Critical (Packet loss > 10% or no connection)

### During Gameplay
- **Hover over Tray Icon** for detailed statistics
- **Right-click on Icon** for options:
  - Change Server/Process
  - Exit Monitor

### Exiting
1. **Close the game**
2. **Click OK** in the PingBoost message
3. **All optimizations are automatically reverted**
4. **System returns to default values**

---

## 📊 Monitoring Details

### Tray Icon shows:
- **Current ping value** (e.g., "42" = 42ms)
- **Color code** for connection quality

### Tooltip shows (on hover):
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

## ⚙️ Configuration

### Change Server IP
**File:** `Ragnarok_PingBoost.vbs`  
**Line ~91:**
```vbscript
serverIP = "138.201.124.56"  ' <--- Enter your server IP here
```

### Retest MTU
**Option 1:** Click "NO" when asked on startup  
**Option 2:** Delete file `mtu_test.txt` and restart script

### Change Monitor Settings
- Right-click on Tray Icon → "Change Server/Process"
- Or delete file `monitor_settings.ini`

---

## 📁 Created Files

The script creates the following files:

| File | Description |
|------|-------------|
| `R+_settings.ini` | Saved game exe setting |
| `monitor_settings.ini` | Server IP and process name |
| `mtu_test.txt` | Optimal MTU value |
| `pingboost.log` | All actions and errors |
| `network_backup.reg` | Registry backup (on first run) |
| `priority.ps1` | Temporary for process priority (deleted after) |

---

## 🔧 Optimizations in Detail

### Network
- **MTU:** Automatically tested and optimized
- **Nagle's Algorithm:** Disabled (TcpAckFrequency=1, TCPNoDelay=1)
- **Network Throttling:** Disabled (Index=4294967295)
- **TCP Auto-Tuning:** Normal
- **TCP Timestamps:** Disabled
- **Initial RTO:** 2000ms → 2000ms (optimized)
- **Max Retransmissions:** 3 (reduced)

### Hardware
- **Interrupt Moderation:** Disabled
- **Energy Efficient Ethernet:** Disabled
- **Flow Control:** Disabled
- **Large Send Offload:** Disabled
- **Receive Side Scaling:** Enabled

### System
- **Windows Game Mode:** Enabled
- **GPU Hardware Scheduling:** Enabled
- **Process Priority:** High
- **CPU Affinity:** All cores
- **Services Stopped:** Windows Search, Superfetch, DiagTrack

---

## ❗ Important Notes

### ⚠️ Administrator Rights Required
The script **MUST** be run as Administrator, otherwise optimizations won't work!

### 🔄 Automatic Rollback
**All changes are automatically reverted** when you exit the script. Your system stays safe!

### 📝 Logging
All actions are saved in `pingboost.log`. Check this file if problems occur.

### 🔒 Security
- Registry backup is created automatically
- No permanent system changes
- All values are restored after game ends

---

## 🐛 Troubleshooting

### Script won't start
- **Solution:** Run as Administrator
- **Check:** `pingboost.log` for error messages

### Game not found
- **Solution:** Delete `R+_settings.ini` and restart
- **Check:** Game exe is in the same folder as the script

### Monitor shows no data
- **Solution 1:** Check if `monitor_settings.ini` has correct server IP
- **Solution 2:** Firewall/Antivirus might block ping
- **Solution 3:** Delete `monitor_settings.ini` and reconfigure

### MTU test fails
- **Solution 1:** Check internet connection
- **Solution 2:** Firewall might block ICMP
- **Solution 3:** Check server IP in script (line ~91)

### Optimizations don't work
- **Check:** Script started as Administrator?
- **Check:** `pingboost.log` for error messages
- **Solution:** Double-click `network_backup.reg` to restore backup

---

## 🎯 Recommended Values

### Connection Quality
- **Excellent:** Ping < 50ms, Jitter < 10ms, 0% Loss
- **Good:** Ping < 100ms, Jitter < 20ms, < 2% Loss
- **Acceptable:** Ping < 150ms, Jitter < 30ms, < 5% Loss
- **Poor:** Ping > 150ms, Jitter > 30ms, > 5% Loss

### MTU Values
- **1500** - Standard Ethernet (cable)
- **1492** - PPPoE DSL connections
- **1460-1472** - Optimal for most gaming connections
- **1400** - Conservative for unstable connections

---

## 📞 Support

For problems or questions:
1. Check `pingboost.log` file
2. Check this README
3. Create an issue with log file

---

## 📜 License

This tool is free and open-source.

**Use at your own risk!** The script changes system settings. Even though all changes are automatically reverted, use it responsibly.

---

## 🙏 Credits

Developed for the Ragnarok Online Community.

**Have fun gaming with optimized ping!** 🎮✨