# PurgeAppCompat

**Advanced PowerShell tool to purge legacy Application Compatibility features from Windows 11.**

Removes unnecessary compatibility infrastructure (PCA, scheduled tasks, registry layers, and optionally `sysmain.sdb`) for users who only run modern software and want a cleaner Windows 11 experience in 2026.

## ⚠️ Warning

- **Level 1** is destructive. It renames `sysmain.sdb` (Microsoft's main shim database). Some legacy installers and very old applications may stop working correctly.
- **Always create a System Restore point** before using Level 1 (the script does this by default).
- Intended primarily for **Windows 11** power users.

## Features

- Disables **Program Compatibility Assistant (PCA)** service and policy
- Disables **Application Experience** scheduled tasks
- Clears old compatibility **Layers** from registry
- Optional nuclear purge of `sysmain.sdb`
- Automatic **backups** + **System Restore point**
- Beautiful interactive arrow-key menu
- Full logging to file
- Safe restore mode (Level 3)

## Usage

### Interactive Mode (Recommended)

```powershell
.\PurgeAppCompat.ps1
```

Use arrow keys to navigate, Enter to select.

### Non-Interactive

```powershell
# Safe recommended purge (Level 2)
.\PurgeAppCompat.ps1 -Level 2

# Full nuclear purge (Level 1) — use with caution
.\PurgeAppCompat.ps1 -Level 1 -Force

# Skip System Restore point creation
.\PurgeAppCompat.ps1 -Level 2 -NoRestorePoint
```

## Parameters

| Parameter         | Description                                      |
|-------------------|--------------------------------------------------|
| `-Level`          | `1` = Nuclear Purge, `2` = Safe (default), `3` = Restore |
| `-Force`          | Skip confirmation prompts                        |
| `-NoRestorePoint` | Do not create a System Restore point             |

## Levels Explained

| Level | Name                    | What it does                                      | Risk     |
|-------|-------------------------|---------------------------------------------------|----------|
| 1     | Complete Purge (Nuclear)| Everything + renames `sysmain.sdb`                | High     |
| 2     | Recommended Safe Purge  | Disables PCA, tasks, clears registry layers       | Low      |
| 3     | Restore Defaults        | Re-enables everything                             | None     |

## Requirements

- Windows 11 (recommended)
- PowerShell 5.1 or PowerShell 7+
- Administrator privileges

## Backups & Recovery

All backups are saved to `C:\AppCompatBackups\`:

- Registry exports (`Registry\AppCompatFlags_*.reg`)
- `sysmain.sdb` backups (when Level 1 is used) in `sysmain_YYYYMMDD_HHMMSS\`

**To restore `sysmain.sdb` manually** after Level 1:  
Rename `sysmain.sdb.DEAD` back to `sysmain.sdb` and reboot.

## Why PurgeAppCompat?

Windows 11 still carries a significant amount of compatibility code from the Windows Vista/7 era. For users running only modern applications, this legacy layer is unnecessary overhead and a potential attack surface.

PurgeAppCompat gives you precise control to remove it cleanly and safely.

## Author & Credits

Created with ❤️ by **Grok** for **Aleksandr Mitroshenkov** (@Mitroshenkov87)

Original concept refined across iterations.

## License

MIT License — feel free to use, modify and share.

---

**Use responsibly.** This tool modifies core Windows compatibility mechanisms. Always have backups. 

**Repository:** https://github.com/Mitroshenkov87/PurgeAppCompat