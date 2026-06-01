# 🧹 PurgeAppCompat

> A powerful Windows 11 tool to **aggressively disable** legacy Application Compatibility features.

[![.NET](https://img.shields.io/badge/.NET-10.0-blueviolet)](https://dotnet.microsoft.com/)
[![Platform](https://img.shields.io/badge/Platform-Windows%2011-blue)](https://www.microsoft.com/windows/windows-11)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## ✨ What It Does

PurgeAppCompat helps you completely remove **legacy Application Compatibility** mechanisms from Windows 11 — features that have remained since the Windows Vista/7/8 era.

### Available Purge Levels

| Level | Name                        | Description                                              | Risk Level |
|-------|-----------------------------|----------------------------------------------------------|------------|
| **1** | 🔥 Nuclear Purge            | Maximum aggressive cleanup (recommended for power users) | 🔴 High    |
| **2** | 🛡️ Safe Recommended Purge   | Recommended safe option for most users                   | 🟢 Low     |
| **3** | ↩️ Restore Defaults         | Revert all changes made by the tool                      | 🟡 Medium  |

---

## 🚀 Features

- ✅ Creates **System Restore Point** before dangerous operations
- ✅ Robust backup system before making changes
- ✅ Disables **Program Compatibility Assistant** service
- ✅ Applies aggressive compatibility policies
- ✅ Disables **Application Experience** scheduled tasks
- ✅ Completely clears **Compatibility Layers** from registry
- ✅ Clean, resizable interface with proper HiDPI support
- ✅ Detailed logging of all operations

---

## ⚠️ Important Warning

> **Level 1 (Nuclear Purge)** is a very aggressive operation.  
> After running it, some very old legacy applications may stop working correctly.

**Always** back up important data before using Level 1.

---

## 📥 Installation & Usage

### Option 1: Download Release (Recommended)

1. Go to **[Releases](https://github.com/Mitroshenkov87/PurgeAppCompat/releases)**
2. Download the latest `PurgeAppCompat-vX.X.zip`
3. Extract the archive
4. Run `PurgeAppCompat.exe` **as Administrator**

### Option 2: Build from Source

```bash
git clone https://github.com/Mitroshenkov87/PurgeAppCompat.git
cd PurgeAppCompat
dotnet build -c Release
```

The executable will be located at:
```
bin\Release\net10.0-windows\PurgeAppCompat.exe
```

---

## 🛡️ Safety Features

- Automatic System Restore Point creation before Level 1
- Multi-stage confirmation for dangerous operations
- Detailed logging of every action
- Clean, modern architecture for reliability

---

## 🛠️ Technical Details

- Built with **.NET 10** + Windows Forms
- Clean architecture (Logger, StatusChecker, PurgeEngine, BackupManager, etc.)
- `PerMonitorV2` HiDPI support
- Resizable and responsive interface

---

## 📄 License

MIT License

---

**PurgeAppCompat** — For those who want a truly clean Windows 11 without legacy ballast. 🔥
