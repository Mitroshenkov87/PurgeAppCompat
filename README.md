# PurgeAppCompat

**PowerShell tool to purge legacy Application Compatibility features from Windows 11.**

Removes unnecessary compatibility infrastructure (PCA, scheduled tasks, registry layers, and optionally `sysmain.sdb`) for users who only run modern software.

## ⚠️ Warning

- **Level 1** is destructive. It renames `sysmain.sdb`, which can break some legacy installers.
- Always create a System Restore point before using Level 1.
- Intended primarily for **Windows 11**.

## Features

- Disables **Program Compatibility Assistant (PCA)**
- Disables **Application Experience** scheduled tasks
- Clears old compatibility **Layers** from registry
- Optional nuclear purge of `sysmain.sdb`
- Automatic backups + System Restore point
- Interactive arrow-key menu
- Full logging

## Usage

### Interactive (recommended)

```powershell
.\PurgeAppCompat.ps1
```

### Non-interactive

```powershell
# Safe recommended purge
.\PurgeAppCompat.ps1 -Level 2

# Full nuclear purge
.\PurgeAppCompat.ps1 -Level 1 -Force
```

## Parameters

| Parameter         | Description                                      |
|-------------------|--------------------------------------------------|
| `-Level`          | `1` = Nuclear, `2` = Safe (default), `3` = Restore |
| `-Force`          | Skip confirmations                               |
| `-NoRestorePoint` | Skip System Restore point                        |

## Levels

| Level | Name                    | Description                                      | Risk  |
|-------|-------------------------|--------------------------------------------------|-------|
| 1     | Complete Purge          | Everything + rename `sysmain.sdb`                | High  |
| 2     | Recommended Safe Purge  | Disable PCA, tasks, clear registry layers        | Low   |
| 3     | Restore Defaults        | Revert all changes                               | None  |

## Requirements

- Windows 11 (best)
- PowerShell 5.1+
- Administrator rights

## Backups

All backups are saved to `C:\AppCompatBackups\`

- Registry exports
- `sysmain.sdb` backups (when Level 1 is used)

## Why?

Windows 11 still carries a large amount of compatibility code from the Windows 7/Vista era. For users running only modern applications, this legacy layer is unnecessary overhead.

PurgeAppCompat gives you control to remove it cleanly.

## Author

Created by Grok for Aleksandr Mitroshenkov

## License

MIT

---

**Use responsibly.** This tool modifies core Windows components.