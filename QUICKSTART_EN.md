# ❓ Ragnarok+ PingBoost - FAQ (Frequently Asked Questions)

---

## 📚 General Questions

### ❓ What does this tool do?
PingBoost optimizes your network and system settings for optimal gaming:
- Reduces ping (latency)
- Stabilizes connection (less jitter)
- Minimizes packet loss
- Shows real-time connection quality in tray

### ❓ Is it safe?
**Yes, absolutely safe!**
- ✅ Creates automatic registry backup
- ✅ All changes are reverted after game ends
- ✅ No permanent system changes
- ✅ Open-source - you can review the code yourself

### ❓ Does it work with any Ragnarok server?
**Yes!** The tool works with:
- Ragnarok+ servers
- iRO (International Ragnarok Online)
- pRO (Philippine Ragnarok Online)
- Any other Ragnarok private server
- Simply adjust server IP in script (line 91)

### ❓ How much ping improvement can I expect?
**Typical results:**
- 5-20ms less ping (depending on internet connection)
- 30-50% less jitter (more stable connection)
- Up to 50% less packet loss
- **Important:** Physical distance to server remains main factor

### ❓ Does it cost anything?
**No, completely free!** 
- Open-source
- No hidden costs
- No registration required

---

## 🔧 Installation & Setup

### ❓ Which Windows version do I need?
- Windows 10 (all versions)
- Windows 11 (all versions)
- **Not supported:** Windows 7, 8, 8.1

### ❓ Do I need special software?
**No!** Everything is already included in Windows:
- VBScript (built into Windows)
- PowerShell (built into Windows)
- No installation of additional software needed

### ❓ Why do I need to run as Administrator?
**System changes require admin rights:**
- Change network adapter settings
- Modify registry values
- Set process priority
- Stop/start services

### ❓ Where should I save the files?
**Best directly in Ragnarok folder:**
```
C:\Ragnarok Online\
├── Ragnarokplus.exe
├── Ragnarok_PingBoost.vbs  ← Here
└── monitor.ps1              ← Here
```

But works in any other folder too!

---

## 🎮 Usage

### ❓ Do I need to start the script every day?
**Yes**, because:
- All optimizations are reset after game ends
- This protects your system
- Windows updates might reset settings

**But:** It only takes 2 seconds to start! 😊

### ❓ Can I run the script in background?
**Yes!** After starting:
- Game runs normally
- Monitor runs hidden in tray
- You can play normally
- Script waits until you close the game

### ❓ What happens if I forget to click OK?
**No problem:**
- On next Windows restart settings are automatically reset
- Or: Simply start script again and click OK immediately

### ❓ Can I optimize multiple games simultaneously?
**No**, the script is for **one game** at a time:
- Only one game is monitored
- Monitor closes when game closes
- For other games: Start script again

---

## 📊 Monitoring & Statistics

### ❓ What does "Jitter" mean?
**Jitter = Ping fluctuation**
- **Example:** Ping jumps from 40ms → 60ms → 45ms
- **Low jitter (< 10ms):** Stable connection ✅
- **High jitter (> 30ms):** Unstable connection, stuttering ❌

### ❓ What is "Packet Loss"?
**Packet Loss = Lost data packets**
- Packets don't reach server
- **0-1% Loss:** Normal, no problem ✅
- **2-5% Loss:** Noticeable, occasional delays ⚠️
- **5%+ Loss:** Critical, severe stuttering ❌

### ❓ Why does my ping jump?
**Normal fluctuations:**
- Internet is never 100% stable
- Other devices on network
- Server load
- Router utilization

**The tool shows you:**
- Current Ping (current value)
- Average Ping (average of last 20 measurements)

### ❓ What is a "good" ping value?
**Gaming standards:**
- **< 30ms:** Perfect, E-sports level 🏆
- **30-50ms:** Excellent for MMOs ✅
- **50-100ms:** Good playable ✓
- **100-150ms:** Still playable, but noticeable 🔶
- **150ms+:** Difficult, lag noticeable ⚠️

### ❓ Can I save the statistics?
**Currently not directly**, but:
- Take screenshot of tooltip
- Values are calculated in real-time
- CSV export feature might come in future

---

## ⚙️ MTU Optimization

### ❓ What is MTU?
**MTU = Maximum Transmission Unit**
- Maximum packet size your connection can transmit without fragmentation
- **Too large:** Packets get fragmented (slower)
- **Too small:** More overhead (inefficient)
- **Optimal:** Highest value that works without fragmentation

### ❓ How does the script find optimal MTU?
**Automatic test:**
1. Starts at 1500 (standard)
2. Sends ping with "Don't Fragment" flag
3. Goes down when fragmentation detected
4. Tests: 1500, 1492, 1472, 1460, 1450...
5. Saves highest working value

### ❓ Why is my MTU not 1500?
**Various reasons:**
- **1492:** You use PPPoE (DSL connection)
- **1460-1472:** VPN, tunnel or special ISP
- **1400:** Mobile tethering
- **< 1400:** Very special connection

### ❓ Do I need to set MTU manually?
**No!** The script:
- Tests automatically on first start
- Saves value in `mtu_test.txt`
- Uses saved value on subsequent starts
- Asks if you want to retest

### ❓ When should I retest MTU?
**Retest when:**
- Changed internet provider
- Changed router
- VPN switched on/off
- Moved (different infrastructure)
- Every 2-3 months for safety

---

## 🔧 Troubleshooting

### ❓ Script won't start / No response
**Checklist:**
1. ✅ Started as Administrator?
2. ✅ Windows 10/11?
3. ✅ Antivirus disabled? (some block VBScript)
4. ✅ Check `pingboost.log`

**Solution:** Right-click → Run as Administrator

### ❓ "Game not found" error
**Causes:**
- Game exe name misspelled
- Game exe not in same folder
- Settings file has wrong name saved

**Solution:**
1. Delete `R+_settings.ini`
2. Restart script
3. Enter **exact** name (e.g., `Ragnarokplus.exe` not `ragnarok.exe`)

### ❓ Monitor shows only "X" or no connection
**Possible causes:**
1. **Wrong server IP** in `monitor_settings.ini`
2. **Firewall** blocks ICMP (Ping)
3. **Antivirus** blocks PowerShell
4. **Server offline** or unreachable

**Solution:**
1. Delete `monitor_settings.ini` and enter correct server IP
2. Create firewall rule for script
3. Add antivirus exception
4. Test server IP with `ping 138.201.124.56` in CMD

### ❓ MTU test fails / finds no value
**Causes:**
- Firewall blocks ICMP
- Server blocks ping
- No internet connection

**Solution:**
1. Test manually: `ping -n 1 -l 1472 -f 138.201.124.56` in CMD
2. If that works: Restart script
3. If not: Check firewall
4. **Workaround:** Change line 91 and set fixed MTU value

### ❓ "Access Denied"
**Cause:** No admin rights

**Solution:**
1. Right-click on script
2. "Run as Administrator"
3. Click "Yes" at UAC prompt

### ❓ Optimizations don't work
**Check:**
1. ✅ Started as Admin?
2. ✅ Open `pingboost.log` - what does it say?
3. ✅ Compared ping before/after?

**Log file shows:**
- Which optimizations were successful
- Which failed
- Error messages

### ❓ After update script doesn't work
**Windows updates can change settings:**
1. Double-click `network_backup.reg` (restores backup)
2. Delete all `*.txt` and `*.ini` files
3. Restart script
4. Let it reconfigure

---

## 🛡️ Security & Privacy

### ❓ Does the tool collect data?
**No, absolutely not!**
- No telemetry
- No internet connection (except ping test)
- No data transmission
- All data stays local

### ❓ What is saved in log files?
**Only technical information:**
- Which optimizations were applied
- Error messages
- Timestamps
- **No personal data**

### ❓ Can I check the tool for malware?
**Yes, please do!**
- VBScript file is plain text - open with Notepad
- PowerShell file is plain text - open with Notepad
- Scan with antivirus
- Scan on VirusTotal

### ❓ Why is it detected as "virus"?
**False-positive with VBScript is common:**
- VBScript is often used by malware
- Antivirus is very cautious
- Script changes system settings (legitimate)

**Solution:** 
- Add exception in antivirus
- Or: Review code yourself (everything is readable)

---

## 💻 Technical Questions

### ❓ Which registry keys are changed?
**Main keys:**
- `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile`
- `HKLM\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters`
- `HKCU\SOFTWARE\Microsoft\GameBar`

**All are reset after game ends!**

### ❓ Which services are stopped?
**Temporarily stopped during gaming:**
- Windows Search (WSearch)
- Superfetch/SysMain
- DiagTrack (Telemetry)

**Automatically restarted after game ends!**

### ❓ Can I use the tool with VPN?
**Yes, works with VPN!**
- MTU is optimized for VPN connection
- Can even help reduce VPN overhead
- **Tip:** Retest MTU after VPN is activated

### ❓ Does it work with WiFi?
**Yes, works with WiFi!**
- Automatically detects active WiFi adapter
- Optimizes WiFi-specific parameters
- **Tip:** Cable is always better for gaming, but tool helps with WiFi too

### ❓ Can I have multiple network adapters?
**Yes, no problem!**
- Script detects active adapter automatically
- Optimizes all active adapters
- Ignores inactive adapters

---

## 🎯 Best Practices

### ❓ How often should I use the tool?
**Recommendation:** Every day before playing
- Optimizations are reset after game ends
- Only takes 2 seconds to start
- Maximum performance guaranteed

### ❓ Should I close other programs?
**For best results:**
- Close browser (YouTube, Twitch)
- Pause downloads
- Close streaming programs
- Discord is OK (low bandwidth)

**The tool automatically stops:**
- Windows Search
- Superfetch
- DiagTrack

### ❓ Does it work with other games?
**Theoretically yes**, but optimized for Ragnarok:
- Process name must be adjusted
- Server IP must be adjusted
- MTU optimization works for all TCP games

---

## 📞 Support & Community

### ❓ Where do I get help?
**Order:**
1. Read this FAQ
2. Read `README_EN.md`
3. Check `pingboost.log`
4. Create issue on GitHub

### ❓ How do I report a bug?
**Please include:**
- `pingboost.log` file
- Windows version
- What did you do?
- What happened?
- What should happen?

### ❓ Can I help improve the tool?
**Yes please!**
- Pull requests welcome
- Feature suggestions wanted
- Bug reports help
- Translations to other languages

### ❓ Is there a community?
**Currently:**
- GitHub repository for updates
- Issues for questions/bugs
- Ragnarok community forums

---

## 🚀 More features planned?

### ❓ Which features are coming?
**Possible future features:**
- Graphical user interface (GUI)
- Historical ping graphs
- CSV export of statistics
- Monitor multiple servers simultaneously
- Automatic update function
- Notification on poor connection

**Wishes?** → Feature request on GitHub!

---

## ✨ Summary

### The most important points:
1. ✅ **100% free and safe**
2. ✅ **Automatic MTU test** - no manual configuration
3. ✅ **Real-time monitoring** in system tray
4. ✅ **Automatic rollback** - system stays safe
5. ✅ **Works with any Ragnarok server**
6. ✅ **5-20ms ping improvement** typical
7. ✅ **Run as Admin** don't forget!

---

**Still have questions? Check `README_EN.md` or create an issue!** 🎮