================================================================================
    RAGNAROK+ PINGBOOST - QUICK START GUIDE
    Windows 7 / 8 / 10 / 11 compatible
================================================================================

🚀 BETTER PING IN 4 STEPS!

--------------------------------------------------------------------------------
STEP 0: COPY FILES TO RAGNAROK+ FOLDER
--------------------------------------------------------------------------------

📁 Copy ALL files to your Ragnarok+ installation folder:
   - R+PingBoost.exe
   - RagnarokPingBoost.ps1
   - MTU_Finder.bat

   Example: C:\Games\Ragnarok+\
   (Where Ragnarok+.exe is located!)

   ⚠️ IMPORTANT: All files MUST be in the same folder!

--------------------------------------------------------------------------------
STEP 1: RENAME RAGNAROK+ (One-time, very important!)
--------------------------------------------------------------------------------

⚠️ THIS STEP IS MANDATORY! ⚠️

1. In Ragnarok+ folder: Find the file "Ragnarok+.exe"
2. Right-click → "Rename"
3. New name: "Ragnarokplus.exe" (WITHOUT the + sign!)
4. Press Enter

   ❓ Why? PowerShell has problems with the "+" character!
   ✅ The game works normally after renaming!

--------------------------------------------------------------------------------
STEP 2: OPTIMIZE MTU (Only once needed!)
--------------------------------------------------------------------------------

1. Right-click on "MTU_Finder.bat"
2. Select "Run as Administrator"
3. Wait until optimal MTU value is found
4. Done! File "mtu.cfg" is created automatically

   ⏱️ Takes about 30 seconds

--------------------------------------------------------------------------------
STEP 3: CREATE SHORTCUT (Recommended, makes life easier!)
--------------------------------------------------------------------------------

1. Right-click on "R+PingBoost.exe"
2. Select "Create shortcut"
3. Right-click on new shortcut → "Properties"
4. Click "Advanced..." button
5. Check "Run as administrator"
6. OK → Apply → OK
7. Drag shortcut to desktop (optional)

   ✅ From now on: Just double-click instead of right-click!

--------------------------------------------------------------------------------
STEP 4: START PINGBOOST
--------------------------------------------------------------------------------

Option A - With shortcut (recommended):
   → Double-click on shortcut
   → R+PingBoost automatically starts Ragnarok+
   → Done!

Option B - Without shortcut:
   1. Right-click on "R+PingBoost.exe"
   2. Select "Run as Administrator"
   3. R+PingBoost automatically starts Ragnarok+
   4. Done!

That's it! PingBoost is running and Ragnarok+ is starting! 🎮

================================================================================
WHAT HAPPENS NOW?
================================================================================

✅ R+PingBoost automatically starts Ragnarok+ (from Ragnarokplus.exe)
✅ Once the game is running, all optimizations are activated
✅ You see a colored icon in System Tray (taskbar bottom right):
   🟢 Green  = Ping under 70ms (Excellent!)
   🟠 Orange = Ping 70-130ms (Good)
   🔴 Red    = Ping over 130ms or connection problems

✅ Right-click on icon shows:
   - "Show Statistics" → Shows detailed ping info
   - "View Log" → Shows what PingBoost did
   - "Exit & Reset Settings" → Exits PingBoost cleanly

✅ When you close Ragnarok+:
   - PingBoost closes automatically
   - All settings are reset
   - Your system is back to original state

================================================================================
DAILY USAGE
================================================================================

1. Start R+PingBoost (via shortcut or right-click)
2. Ragnarok+ starts automatically
3. Play with better ping! 🎮
4. Close Ragnarok+ when done
5. PingBoost cleans up automatically

That's it! Same every day - super easy! ✨

================================================================================
FREQUENTLY ASKED QUESTIONS
================================================================================

❓ Do I need to run MTU_Finder every time?
   → No! Only once, unless you change ISP/Router/VPN

❓ Does this work on Windows 7?
   → YES! Fully compatible (except QoS Policy)
   → QoS is just a small part, everything else works!
   → Might need to install PowerShell 5.1

❓ Do I really need to rename Ragnarok+.exe?
   → YES! Very important! PowerShell won't work otherwise!
   → Rename to: Ragnarokplus.exe (without +)

❓ Do files need to be in Ragnarok+ folder?
   → YES! All files must be where Ragnarok+ is installed!

❓ Do I forget "Run as Administrator" sometimes?
   → Create a shortcut with Auto-Admin (see Step 3)!

❓ How do I see if it's working?
   → Right-click on Tray-Icon → "Show Statistics"
   → Or open "pingboost.log" in script folder

❓ My Antivirus blocks the .exe!
   → Normal for unknown tools, just add exception
   → The .exe is safe and only does network optimizations

❓ Can I keep PingBoost running always?
   → Yes! It starts Ragnarok+ automatically and exits automatically too

❓ Ragnarok+ doesn't start?
   → Did you rename Ragnarok+.exe to Ragnarokplus.exe?
   → Are ALL files in the Ragnarok+ folder?
   → Is R+PingBoost.exe in same folder as Ragnarokplus.exe?

❓ What if I have problems?
   → Check "README_EN.md" → Troubleshooting
   → Or open "pingboost.log" for details

================================================================================
EXPECTED IMPROVEMENTS
================================================================================

What you should notice:
✅ 5-15ms lower ping on average
✅ Fewer "lag spikes" (ping drops)
✅ Smoother, more responsive gameplay
✅ More stable connection to server

Note: Actual improvement depends on your internet
      connection and your system!

================================================================================
IMPORTANT!
================================================================================

⚠️ ALWAYS "Run as Administrator"!
   → Without admin rights PingBoost cannot optimize anything

⚠️ ALL files must be in Ragnarok+ folder!
   → R+PingBoost.exe, .ps1 and .bat in same folder as game

⚠️ Ragnarok+.exe MUST be renamed to Ragnarokplus.exe!
   → PowerShell has problems with "+" character
   → Do this once, then everything works!

⚠️ Don't just close it!
   → Use "Exit & Reset Settings" in Tray menu
   → Or just close Ragnarok+ (Auto-Cleanup!)

================================================================================
SUPPORT
================================================================================

📖 Detailed guide: README_EN.md
📝 What changed: CHANGELOG_EN.md
📋 View log file: pingboost.log (in script folder)

Have fun and low ping! 🎮🚀

The Ragnarok+ Community ❤️

================================================================================