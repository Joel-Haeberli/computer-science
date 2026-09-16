tags: #malware-analysis #lab 

# MAI Labs

links: [[800 MAI MOC|MAI MOC]] - [[themes/000 Index|Index]]

---

# Malware Overview

## 1e3966e77ad1cbf3e3ef76803fbf92300b2b88af39650a1208520e0cdc05645b.exe

Bandok familiy, opens iexplore.exe's, persists itself via CurrentVersion/Run with a zam.exe in AppData Roaming. Identified by hollows_hunter. Rest is easy to find out. We did not analyze it again.

## 6d34ded00c0da9887ba752872093f59c649de72a1f629a32014f5ed8be509363.exe

DarkComet remote access trojan (RAT), opens runddl32.exe (ddl instead of dll!), notepad.exe and two cmd.exe's, persists itself via CurrentVersion/Run with a runddl32.exe in AppData Local. Not identified by hollows_hunter (dump processes and run yara on them). Open apimonitor and attach to all those process to see more maybe. Closes ProcessHacker and procmon sometimes. Probably direct code injection.

## 6562e2ac60afa314cd463f771fcfb8be70f947f6e2b314b0c48187eebb33dd82.exe

GU_Loader (yara), dynamer (VirusTotal), DLL injection (api-ms-win-core-advapi) as visible in the started rundll32.exe. Malicious DLL is in AppData Local Temp. Autostart via CurrentVersion/Run tries to start it from System32. But the DLL is not there. A lot of registry activity. In a few seconds 2 million entries in procmon. After 15min the rundll32.exe process is gone.
svchost.exe with taskhostw.exe's and cmd.exe below. After 15min hollows_hunter finds stuff there. XAgent.

## a380617cf945ca35dbbc3d031bcc612f0dca96c1027a75003182ba5be2851215.exe

Citadel. Loader persists emwiy.exe in AppData Roaming. Create other files also. This exe is also persisted via CurrentVersion/Run. The exe is running and is trying to communicate with a C2 server. Many strings found. emwiy.exe tried to do DLL injections. hollows_hunter finds emwiy.exe and procmon.exe now. Via apimonitor on emwiy.exe the attempted dll injection in procmon.exe can be seen. Probably doesn't work as the dll would be downloaded from the c2 server.

## b3b3bb519dd34a933a0b9920fa905ecaa5ce32c34871a29b5823a5b0fd4d9fc7.exe

Trickbot. Starts a2a2..exe. Both are terminated at some point. With hollows_hunter a svchost.exe process is found. Yara rules from malpedia find it. Persistence via AppData Roaming exe with a very long name. Works via a scheduled task. Multiple RWX regions in the svchost.exe. In strings URLs are found (ipinfo, ripinfo etc.). svchost.exe uses a lot of CPU resources. In apimonitor a lot can be seen but not under our two standard filters. It's more network related probably.

## e30b76f9454a5fd3d11b5792ff93e56c52bf5dfba6ab375c3b96e17af562f5fc.exe

Dridex/drixed. Does nothing for a long time. In the strings we find multiple IP addresses. We also see mentions of crypto related stuff. No persistence found. Looks like it's a keylogger that is trying to send the contents then to those IPs.

## 66490c59cb9630b53fa3fa7125b5c9511afde38edab4459065938c1974229ca8.exe (Lectures)

sodinokibi/revil. Uses a lot of CPU resources. Quickly opens a cmd.exe and MsMpEng.exe process. Many untrusted DLLs are loaded. Ransomware. Encryps all files and kills processes. Hard to analyze as yara rules are encrypted. Looks like a one time run only.

## d4d9d9eccf8badd954deec00ea5e57e31806371003245453fcbb5755c922c658.exe (Lectures)

Not much happened. Wrote a .tmp file that is a PE file. But it can not be started when changing to .exe. Also no persistence. In strings also not that much.
Nothing obvious found. VirusTotal says it's a SmokeLoader. Probably nothing happens because it can not load more without internet. Process stops after 1-2 seconds.

## c39e675a899312f1e812d98038bb75b0c5159006e8df7a715f93f8b3ac23b625.exe (Lectures)

API monitor hands on example with direct code injection.
Started the exe with apimonitor. Saw the typical direct code injection calls. Many RWX regions in the explorer.exe process. One with PE header.
Yara rules say either GU_Loader or "Generic_Threat".

## 07ff5290bca33bcd25f479f468f9a0c0371b3aac25dc5bb846b55ba60ca658ed.exe (Lectures. Not done again)

Sphinx Zbot. Direct code injection. (RWX)

## 76ede4f29dbd8a75b643e46cabd369ac888b8012630b8b244e08e0baac8535e6.exe (Lectures. Not done again)

Persistence example via a Service.

## 16017353e67868fd3b785aa22db51efb.dll (Lectures. Not done again)

Start DLL with rundll32.exe 16017353e67868fd3b785aa22db51efb.dll,#1

## b7fc1397e20c93b42ee14ca1a8b1773a52390e402689703bb93428a9f72f1fe9.exe (Lectures. Not done again)

Cerbu crypto miner. Easy example.

---
links: [[800 MAI MOC|MAI MOC]] - [[themes/000 Index|Index]]