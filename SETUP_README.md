# Universal Python Setup Script

Version: 1.0.0  
Author: retoro-sen  
License: MIT

## Übersicht

Ein universelles, OS-übergreifendes Setup-Script für Python-Projekte, das die Installation vollständig automatisiert.

## Features

### ✨ Automatische Installation
- 🔍 **OS-Erkennung** - Erkennt automatisch Linux, Windows und macOS
- 🐍 **Python-Versions-Check** - Validiert Python 3.8+
- 📦 **Tkinter-Installation** - Installiert Tkinter automatisch (Linux)
- 🔧 **Virtual Environment** - Erstellt und konfiguriert automatisch
- 📚 **Dependency Management** - Liest requirements.txt und installiert alle Pakete
- 🚀 **Starter-Scripts** - Erstellt plattformspezifische Launcher
- 🖥️ **Desktop-Integration** - Optionaler Desktop-Launcher/Shortcut
- ✅ **Installations-Test** - Verifiziert die Installation am Ende

### 🐧 Linux-Spezifisch
- Automatische Distro-Erkennung (Debian/Ubuntu, Fedora/RHEL, Arch)
- Tkinter-Installation mit passendem Package-Manager
- `.desktop` Datei für Anwendungsmenü
- Update der Desktop-Datenbank
- Automatische Icon-Integration

### 🪟 Windows-Spezifisch
- `.bat` Starter-Script
- Desktop-Verknüpfung (mit pywin32)
- Automatisches Icon-Assignment

### 🍎 macOS-Spezifisch
- `.sh` Starter-Script
- Hinweise für Dock-Integration

## Verwendung

### Basis-Setup

```bash
python3 setup.py
```

Das Script führt dich interaktiv durch:
1. System-Erkennung und Validierung
2. Tkinter-Check/-Installation
3. Virtual Environment Erstellung
4. Dependencies-Installation
5. Starter-Script Erstellung
6. Optional: Desktop-Launcher (auf Anfrage)
7. Installations-Test

### Für eigene Projekte anpassen

Das Script ist generisch und kann für jedes Python-Projekt verwendet werden:

1. Kopiere `setup.py` in dein Projekt-Verzeichnis
2. Stelle sicher, dass eine `requirements.txt` existiert
3. Führe `python3 setup.py` aus

**Optional**: Passe folgende Bereiche an:
- Desktop-Entry Name (Zeile ~270): wird automatisch aus Ordnernamen generiert
- Icon (Zeile ~278): Standard ist `application-pdf`, anpassbar
- Starter-Script Name (Zeile ~220, ~224): Standard ist projektspezifisch

## Anforderungen

### Minimal
- Python 3.8+
- `requirements.txt` im Projekt-Root

### Optional (für Desktop-Integration)
- **Linux**: `update-desktop-database` (meist vorinstalliert)
- **Windows**: `pywin32` (wird im Script erwähnt, falls fehlend)

## Ausgabe

Nach erfolgreicher Installation erstellt das Script:

```
project/
├── .venv/                      # Virtual Environment
├── start_project.sh/.bat       # Starter-Script
└── ~/.local/share/applications/
    └── project.desktop         # Desktop-Launcher (Linux, optional)
```

## Technische Details

### Farbiges Terminal-Output
- ✓ Grün: Erfolg
- ℹ Blau: Information
- ⚠ Gelb: Warnung
- ✗ Rot: Fehler

Farben werden auf Windows automatisch deaktiviert falls nicht unterstützt.

### Linux Distro-Erkennung
Liest `/etc/os-release` und ermittelt:
- Debian/Ubuntu → `apt-get install python3-tk`
- Fedora/RHEL → `dnf install python3-tkinter`
- Arch → `pacman -S tk`

### Test-Mechanismus
Testet Import aller kritischen Module:
```python
import tkinter
import fitz  # falls in requirements.txt
from PIL import Image  # falls in requirements.txt
```

## Fehlerbehandlung

Das Script ist robust designed:
- Prüft jeden Schritt einzeln
- Gibt aussagekräftige Fehlermeldungen
- Erlaubt Fortsetzung bei nicht-kritischen Fehlern
- Catch-All für unerwartete Exceptions

## Changelog

### [1.0.0] - 2025-11-16
#### Added
- Initial Release
- OS-übergreifende Installation (Linux/Windows/macOS)
- Tkinter Auto-Installation (Linux)
- Virtual Environment Management
- requirements.txt Parser
- Starter-Script Generator
- Desktop-Launcher Integration (Linux)
- Desktop-Shortcut (Windows mit pywin32)
- Farbiges Terminal-Output
- Installations-Test
- Interaktive Prompts für optionale Features

## Lizenz

MIT License - Frei verwendbar für alle Projekte

## Autor

retoro-sen
- GitHub: [@retoro-sen](https://github.com/retoro-sen)
- E-Mail: retoro-sen@protonmail.ch

## Verwendung in anderen Projekten

Dieses Setup-Script ist als universelle Lösung konzipiert und kann frei in eigenen Projekten verwendet werden. Einfach kopieren und anpassen!

**Empfehlung**: 
- Füge `setup.py` zu deinem Repository hinzu
- Erwähne in deiner README: "Installation mit `python3 setup.py`"
- Keine weiteren Dependencies für das Setup selbst nötig

---

⭐ Wenn dir dieses Script hilft, gib dem Projekt einen Stern auf GitHub!
