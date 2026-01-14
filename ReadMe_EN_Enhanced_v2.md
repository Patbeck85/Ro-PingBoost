# Ragnarok+ PingBoost Enhanced v2.0

## 📋 Overview

Ragnarok+ PingBoost is an automated PowerShell tool that optimizes network connections for Ragnarok+ and monitors real-time ping to the game server. The tool applies proven Windows network optimizations and displays current latency in a system tray icon.

## ✨ Features

### Network Optimizations (Level 1)
- **Disable Network Throttling**: Prevents Windows network throttling
- **Maximize System Responsiveness**: Prioritizes foreground applications
- **QoS Policy**: Prioritizes game server traffic with DSCP marking
- **Process Priority**: Sets Ragnarok+ to "High" priority
- **DNS Cache Optimization**: Clears cache for optimal name resolution
- **TCP Optimizations**: Enables TcpAckFrequency & TCPNoDelay
- **MTU Adjustment**: Configurable Maximum Transmission Unit

### Monitoring & Statistics
- **Real-time Ping Display**: Color-coded system tray icon
  - 🟢 Green: < 70ms (Excellent)
  - 🟠 Orange: 70-130ms (Good)
  - 🔴 Red: > 130ms or connection lost
- **Detailed Statistics**: Min/Max/Average, Packet Loss
- **History Tracking**: Stores last 100 measurements
- **Log File**: Complete log of all optimizations

### Security
- ✅ Automatic backup of all original settings
- ✅ Complete rollback on exit
- ✅ Error handling for all optimizations
- ✅ No dangerous system services are stopped

## 🚀 Installation & Usage

### Requirements
- Windows 10/11 (or Windows Server 2016+)
- PowerShell 5.1 or higher
- **Administrator rights** (required for Registry & QoS)
- Ragnarok+ game installed

### Installation

1. **Copy files to Ragnarok+ folder**
   - `R+PingBoost.exe` - Main launcher
   - `monitor.ps1` - PowerShell script
   - `MTU_Finder.bat` - MTU optimization tool (optional)
   - **IMPORTANT**: All files must be in the same folder as Ragnarok+!
   - Example: `C:\Games\Ragnarok+\` (where Ragnarok+.exe is located)

2. **⚠️ IMPORTANT: Rename Ragnarok+ Executable**
   - In the Ragnarok+ folder: Find the file `Ragnarok+.exe`
   - **Rename it to**: `Ragnarokplus.exe` (without the + sign!)
   - **Reason**: PowerShell has issues with the "+" character in filenames
   - **Note**: The game works normally after renaming!

3. **Optimize MTU** (Recommended)
   - **Right-click** on `MTU_Finder.bat` → "Run as Administrator"
   - The tool automatically tests different MTU values to the game server
   - Shows the optimal MTU value
   - Automatically creates the `mtu.cfg` file with the best value
   - **Important**: Only run this once!

4. **Start PingBoost**
   - **Right-click** on `R+PingBoost.exe` → **"Run as Administrator"**
   - The tool automatically starts:
     - The PowerShell script with admin rights
     - Ragnarok+ (from `Ragnarokplus.exe`)
   - Applies all optimizations automatically
   
   **Tip**: Create a shortcut and set "Run as Administrator" in properties, then a simple double-click is enough!

**Alternative: Manual MTU configuration**
   - Create a file `mtu.cfg` in the same folder
   - Enter your MTU value (e.g., `1472`)
   - If not present, default MTU 1500 will be used

### Process

1. Start `R+PingBoost.exe` by double-clicking
2. Launcher waits 30 seconds (countdown)
3. Waits for Ragnarokplus.exe (up to 2 minutes)
4. Applies all optimizations
5. Starts ping monitoring (every 3 seconds)
6. Displays ping in system tray icon
7. On game exit: Automatic cleanup & rollback

## 📊 Usage

### System Tray Icon
- **Right-click** on icon opens menu:
  - **Show Statistics**: Detailed ping statistics
  - **View Log**: Opens log file in Notepad
  - **Exit & Reset Settings**: Closes script and resets all settings

### Log File
- File: `pingboost.log` (in script folder)
- Shows all applied optimizations
- Logs errors and warnings
- Format: `[HH:mm:ss] [TYPE] Message`

## ⚙️ Configuration

### MTU_Finder.bat - Automatic MTU Optimization

**Usage:**
1. **Right-click** on `MTU_Finder.bat` → "Run as Administrator"
2. The tool tests MTU values from 1500 to 1200 in 8-byte steps
3. Shows for each value whether fragmentation is needed
4. Recommends the optimal MTU value
5. Automatically creates `mtu.cfg` with the best value

**Example output:**
```
Testing MTU to 138.201.124.56...
MTU 1500: Needs fragmentation
MTU 1492: Needs fragmentation
MTU 1472: OK - No fragmentation!
MTU 1464: OK - No fragmentation!

Optimal MTU: 1472
Created mtu.cfg with value: 1472
```

**Note**: MTU_Finder only needs to be run **once**, unless:
- You change Internet Service Provider
- You change router/modem
- You use VPN (VPN often has lower MTU)

### mtu.cfg - Manual Configuration
```
1472
```
Recommended MTU values:
- **1500**: Standard Ethernet
- **1472**: Optimal for many DSL connections
- **1492**: PPPoE connections
- **1452**: Some cable/fiber connections

Test MTU (manually):
```cmd
ping 138.201.124.56 -f -l 1472
```
Reduce value if "Packet needs to be fragmented" appears.

**Tip**: Use `MTU_Finder.bat` instead of manual testing!

### Create Auto-Admin Shortcut (Optional)

So you don't have to right-click every time:

1. **Right-click** on `R+PingBoost.exe` → "Create shortcut"
2. **Right-click** on the shortcut → "Properties"
3. Click on "Advanced..." button
4. Check "Run as administrator"
5. OK → Apply → OK
6. From now on: Simply double-click the shortcut!

### Server Configuration
Adjust in script (lines 6-7):
```powershell
ServerAddress  = "138.201.124.56"
ServerPort     = 5121
```

## 🔧 What Gets Changed?

### Registry Settings
```
HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile
├── NetworkThrottlingIndex = 0xffffffff (Default: 10)
└── SystemResponsiveness = 0 (Default: 20)

HKLM:\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\Interfaces\{GUID}
├── TcpAckFrequency = 1
└── TCPNoDelay = 1
```

### Network Settings
- **MTU**: Set to configured value
- **QoS Policy**: "RagnarokPlus_QoS" with DSCP 46
- **DNS Cache**: Cleared on start

### Process Settings
- **Ragnarokplus.exe**: PriorityClass = "High"

**All changes are automatically reverted when the script exits!**

## 📈 Expected Improvements

- ✅ **5-15ms** lower average latency
- ✅ **Fewer latency spikes** through disabled throttling
- ✅ **More stable connection** through QoS prioritization
- ✅ **Smoother gameplay** through higher process priority

**Note**: Actual improvements depend on your internet connection, hardware, and network configuration.

## ❗ Important Notes

### Security
- ✅ Script only changes temporary network settings
- ✅ No data is downloaded or uploaded
- ✅ No external connections except to game server
- ✅ Open source - code is viewable

### Known Limitations
- Requires administrator rights
- Only works while Ragnarok+ is running
- QoS works best with QoS-capable router
- Some network adapters don't support all optimizations

### Troubleshooting

**R+PingBoost.exe doesn't start**
- **Right-click** → **"Run as Administrator"** (very important!)
- Check if PowerShell is installed
- Antivirus might block .exe (add exception)
- Windows SmartScreen: "More info" → "Run anyway"

**Ragnarok+ doesn't start automatically**
- Check if `Ragnarok+.exe` was renamed to `Ragnarokplus.exe`!
- **Check if all files are in the Ragnarok+ folder!**
- Check if Ragnarokplus.exe exists and is functional
- Antivirus might block Ragnarokplus.exe

**MTU_Finder.bat shows errors**
- Run as Administrator
- Check internet connection
- Firewall might block ICMP (Ping)

**"Execution Policy" Error**
```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

**QoS Policy Error**
- Check if Windows Firewall is active
- Check if Group Policy blocks QoS

**Script doesn't find game**
- **Important**: Did you rename `Ragnarok+.exe` to `Ragnarokplus.exe`?
- Check if process name is correct (`Ragnarokplus.exe`)
- Wait until game is fully loaded
- Start R+PingBoost.exe as Administrator

**High CPU usage**
- Normal: Script uses <1% CPU
- If higher: Check log for error loops

## 🔄 Updates & Versions

### v2.0 (Current)
- ✅ Level 1 optimizations implemented
- ✅ Backup & rollback system
- ✅ Logging system
- ✅ Improved statistics

### v1.0
- Basic network optimizations
- Ping monitoring
- System tray icon

## 📝 License & Liability

This tool is provided "as is". The author assumes no liability for:
- System changes
- Connection problems
- Game issues
- Data loss

**Use at your own risk!**

Recommended: Create a Windows restore point before first use.

## 🆘 Support & Contact

- **Check log file**: `pingboost.log` contains detailed error info
- **Reset script**: "Exit & Reset Settings" in tray menu
- **Manual rollback**: Restart Windows to reset most settings

## 🙏 Acknowledgments

This tool was developed with ❤️ for the Ragnarok+ community.

**Special thanks to:**
- **All Ragnarok+ Players** - For your support, feedback, and passion for the game. You make this community amazing!
- **The Ragnarok+ Server Operators** - For your hard work, stable servers, and the great gaming experience you create for all of us. Thank you for keeping this awesome project alive!
- **The Community** - For testing, bug reports, and suggestions for improvement

This tool is based on proven Windows network optimizations for gaming and has been specifically adapted for Ragnarok+.

**You are awesome! Together we make Ragnarok+ even better!** 🎮✨

---

**Good luck and low ping!** 🎮🚀