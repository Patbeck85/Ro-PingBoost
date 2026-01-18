# Changelog - Ragnarok+ PingBoost

All notable changes to this project will be documented in this file.

---

## [2.0] - 2025-01-14

### 🎉 Major Release - Level 1 Optimizations

#### Compatibility
- **Windows 7 SP1 to Windows 11** fully supported
- **Automatic Detection**: Script detects Windows version and adapts automatically
- **Fallback Methods**: Uses WMI on Windows 7, modern cmdlets on Windows 8+
- **QoS Policy**: Windows 8+ only, automatically skipped on Windows 7
- **DNS Cache**: Uses `ipconfig /flushdns` on Windows 7, modern cmdlets on Windows 8+
- **Network Adapter**: WMI fallback for Windows 7, Get-NetAdapter for Windows 8+

#### Launcher Integration
- **R+PingBoost.exe**: Automatic launcher that starts both the script and Ragnarok+
- **Automatic Start**: Starts Ragnarok+ from `Ragnarokplus.exe` (renamed `Ragnarok+.exe`)
- **Installation**: All files must be in Ragnarok+ installation folder
- **Important**: Game executable must be renamed to `Ragnarokplus.exe` (PowerShell compatibility)

#### New Features
- **NetworkThrottlingIndex Optimization**: Disables Windows network throttling for minimal latency
- **SystemResponsiveness Optimization**: Maximizes priority for foreground applications (gaming)
- **QoS Policy**: Automatic traffic prioritization with DSCP marking (EF/46) - Windows 8+ only
- **Process Priority**: Sets Ragnarok+ automatically to "High" CPU priority
- **DNS Cache Optimization**: Clears DNS cache for optimal name resolution
- **Backup & Rollback System**: Saves all original values before changes
- **Logging System**: Complete log of all optimizations and errors
- **Improved Statistics**: Shows active optimizations in stats dialog
- **Log Viewer**: New "View Log" menu item in tray menu

#### Technical Improvements
- All optimizations separated into individual functions
- Try-Catch error handling for each optimization
- Silent mode for recurring process priority (no more log spam)
- Encoding fix for special characters in log
- Automatic restoration of all settings on exit
- Process priority refreshed silently every 3 seconds
- **Windows version detection** and automatic adaptation
- **Fallback methods** for older Windows versions

#### Security
- Backup of all registry values before changes
- Complete rollback guaranteed
- No dangerous system services are stopped
- All changes are reversible

#### Documentation
- README_DE.md - Complete German documentation with installation instructions
- README_EN.md - Complete English documentation with installation instructions
- QUICKSTART.txt - Quick start guide (4 steps incl. file copy & renaming)
- QUICKSTART_EN.txt - English quick start guide
- CHANGELOG.md - German version of this file
- CHANGELOG_EN.md - This file

#### Expected Improvements
- 5-15ms lower average latency
- Fewer latency spikes through disabled throttling
- More stable connection through QoS prioritization
- Smoother gameplay through higher process priority

---

## [1.0] - 2025-01-13

### 🚀 Initial Release

#### Features
- **Basic Network Optimizations**:
  - MTU adjustment (configurable via mtu.cfg)
  - TcpAckFrequency = 1 (immediate ACK packets)
  - TCPNoDelay = 1 (Nagle's Algorithm disabled)
- **Real-time Ping Monitoring**:
  - TCP connection test every 3 seconds
  - Color-coded system tray icon (Green/Orange/Red)
  - Display current latency in icon
- **Statistics**:
  - Min/Max/Average ping
  - Packet loss rate
  - History tracking (last 100 measurements)
- **Automation**:
  - 30 seconds launcher countdown
  - Waits up to 2 minutes for game start
  - Automatic cleanup on game exit
- **System Tray Integration**:
  - Right-click menu with statistics
  - Exit button for clean shutdown

#### Technical Details
- PowerShell 5.1+ compatible
- Windows Forms GUI for system tray
- Icon generation with GDI+
- Asynchronous TCP connection tests

---

## Planned Features (Future Releases)

### [2.1] - In Planning
- [ ] **Level 2 Optimizations** (optional, for advanced users):
  - Interrupt Moderation control
  - TcpTimedWaitDelay optimization
- [ ] **Advanced Statistics**:
  - Graphical ping history display
  - Export statistics (CSV)
  - Long-term statistics (cross-session)
- [ ] **Configuration**:
  - GUI for settings
  - Server profile management
  - Custom ping interval

### [3.0] - Future Vision
- [ ] **Multi-Game Support**:
  - Profiles for different games
  - Automatic game detection
- [ ] **Advanced Network Analysis**:
  - Traceroute to server
  - Jitter measurement
  - Packet size optimization
- [ ] **Auto-Update Function**
- [ ] **Graphical User Interface** (optional)

---

## Known Issues & Fixes

### Version 2.0
- ✅ **Windows 7 - 11 Compatibility**
  - Automatic Windows version detection
  - Fallback to WMI for Windows 7
  - QoS Policy only on Windows 8+ (skipped on Win7)
  - All core optimizations work on all versions
- ✅ **IMPORTANT**: All files must be in Ragnarok+ folder
  - R+PingBoost.exe, RagnarokPingBoost.ps1, MTU_Finder.bat
  - Must be in same directory as Ragnarok+ game
  - Reason: Launcher needs to find and start game executable
- ✅ **IMPORTANT**: Ragnarok+ executable must be renamed
  - `Ragnarok+.exe` → `Ragnarokplus.exe`
  - Reason: PowerShell cannot handle "+" in process names properly
  - Solution: One-time rename, documented in all guides
- ✅ **FIXED**: DNS Cache error on older Windows versions
  - Solution: Fallback to `ipconfig /flushdns`
- ✅ **FIXED**: Log spam from process priority
  - Solution: Silent mode implemented
- ✅ **FIXED**: Special characters in log displayed incorrectly
  - Solution: Encoding changed to Default

### Version 1.0
- No critical issues known

---

## Upgrade Guide

### From 1.0 to 2.0

**Preparation**:
1. **Copy all files to Ragnarok+ folder**
2. **IMPORTANT**: Rename `Ragnarok+.exe` to `Ragnarokplus.exe`!
3. Replace old PingBoost files with new ones (if present)
4. `mtu.cfg` will be kept
5. Done!

**What's new for users**:
- More optimizations = better ping
- More detailed statistics
- Log file for troubleshooting
- Automatic backup & rollback
- Windows 7 compatibility

**Note**: Version 2.0 is fully backward compatible!

---

## Developer Notes

### Version 2.0 Development
- Development time: 2 days
- Testing: Windows 7 SP1, 8.1, 10 (22H2, 23H2), 11
- PowerShell versions: 5.1, 7.x
- Network tests: DSL, Cable, Fiber

### Code Quality
- All functions with error handling
- Backup before each system change
- Rollback guaranteed through Finally blocks
- Logging for all operations
- **Windows version detection** and automatic adaptation
- **Fallback methods** for older Windows versions

### Performance
- CPU usage: <1% average
- RAM usage: ~15-20 MB
- Disk I/O: Minimal (logging only)
- **Tested on**: Windows 7, 8.1, 10, 11

---

## Contributors

### Main Development
- **Script Development**: Community project
- **Optimization Research**: Gaming community
- **Testing**: Ragnarok+ players

### Special Thanks
- Ragnarok+ server operators
- All testers and feedback providers
- The entire Ragnarok+ community ❤️

---

## License & Copyright

This tool was developed for the Ragnarok+ community.
Free use and distribution permitted.

**Disclaimer**: Use at your own risk.

---

## Contact & Support

**Questions or problems?**
- Check `README_EN.md` for detailed documentation
- Look at `pingboost.log` for error details
- Use "Exit & Reset Settings" if problems occur

**Feedback welcome!**
- Bug reports
- Feature requests
- Suggestions for improvement

---

**As of: January 14, 2025**

*Development continues - Stay tuned!* 🚀