# SessionInfo – Desktop Information Overlay (BGInfo Alternative)

## 🚀 Release v1.0.0

**SessionInfo** ist eine moderne, schlanke Alternative zu BGInfo für Windows (.NET 8 / WPF).
Die Anwendung blendet Sitzungs-, Benutzer- und Systeminformationen **unterhalb von Applikationen**,
aber **oberhalb des Desktop-Hintergrunds** ein – vollständig konfigurierbar per INI.

---

## ✨ Features

- Desktop-Overlay (Click-Through, kein Fokus, kein Alt-Tab)
- Automatisches Reload bei Änderung der `config.ini`
- Token-basiertes Anzeige-System
- Lazy-Loading für Advanced Tokens
- Optionales System-Tray-Icon (Refresh / Beenden)
- Ideal für VDI / RDS / FSLogix

---

## ▶ Start

```text
SessionInfo.exe [PfadZurConfig.ini]
```

Ohne Parameter wird automatisch `config.ini` im EXE-Verzeichnis verwendet.

---

## 🧩 Beispiel config.ini

```ini
[Titel]
Text=Session Info
Color=White
Bold=true
Size=20

[Layout]
ContentPosition=Bottom
BottomMargin=25

[Lines]
Line1=Benutzer: {USER}
Line2=PC: {MACHINE}
Line3=Domäne: TEAM-NETZ
Line4=Uptime: {UPTIME}
Line5=Login: {LOGONTIME:dd.MM.yyyy HH:mm}
Line6=Zeit: {TIME:HH:mm:ss}
Line7=FSLogix: {FSLOGIX_PROFILESTATE}

[Style.Line7]
Color=Orange
Bold=true

[Tray]
Enabled=true
Tooltip=Session Info
Icon=Assets\sessioninfo.ico
ShowRefresh=true
ShowExit=true
```

---

## 🔤 Token-System

### Standard Tokens

| Token | Beschreibung |
|------|-------------|
| `{TIME}` | Aktuelle Uhrzeit |
| `{TIME:FORMAT}` | Uhrzeit formatiert |
| `{UPTIME}` | Systemlaufzeit |
| `{LOGONTIME}` | Logon-Zeit |
| `{LOGONTIME:FORMAT}` | Logon-Zeit formatiert |
| `{USER}` | Benutzername |
| `{MACHINE}` | Computername |

---

### Advanced Tokens (Lazy)

Diese Tokens werden **nur ausgewertet, wenn sie in der INI verwendet werden**.

#### FSLogix

| Token | Beschreibung |
|------|-------------|
| `{FSLOGIX_PROFILESTATE}` | RO / RW / NONE |
| `{FSLOGIX_VHDPATH}` | Pfad zur VHD |

Registry-Quelle:
```
HKCU\SOFTWARE\FSLogix\Profiles\Session
VHDOpenedFilePath
```

---

## ⚙ Autostart (optional)

SessionInfo kann z. B. per HKLM Run-Key gestartet werden:

```
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run
```

---

## 🧪 Getestet mit

- Windows 10 / 11
- Azure Virtual Desktop
- FSLogix Profile Container

---

## © Copyright

```
Copyright (c) team-netz consulting GmbH
Alle Rechte vorbehalten.
```
