# 📦 GNUSlashLinux Repository

Das offizielle Software-Repository für **GNUSlashLinux**. Dieses Repository stellt vorkompilierte Pakete (einschließlich AUR-Pakete wie die Noctalia-Shell) für Artix Linux- und Arch Linux-basierte Systeme bereit.

Die Pakete werden lokal gebaut und hochgeladen. Eine automatisierte GitHub Action kümmert sich anschließend im Hintergrund um die Pflege und Aktualisierung der Repository-Datenbank (`GNUSlashLinux.db`).

---

## 🚀 Repository hinzufügen

Um dieses Repository in Ihrem System (oder in der Live-ISO-Konfiguration) zu aktivieren, fügen Sie die folgenden Zeilen an das Ende Ihrer `/etc/pacman.conf` an:

```ini
[GNUSlashLinux]
SigLevel = Optional TrustAll
Server = https://gnuslashlinux.github.io/GNUSlashLinux_Artix_Repo/x86_64
```

> ⚠️ **Hinweis:** Stellen Sie sicher, dass Sie `IhrGitHubUsername` durch Ihren tatsächlichen GitHub-Benutzernamen ersetzen und GitHub Pages in den Repository-Einstellungen für den `main`-Branch (Root-Verzeichnis) aktiviert haben.

### Datenbank aktualisieren

Nachdem Sie die `pacman.conf` gespeichert haben, synchronisieren Sie die Paketdatenbanken mit:

```bash
sudo pacman -Syu
```

---

## 🛠️ Enthaltene Kern-Pakete

Aktuell stellt das Repository unter anderem folgende Pakete bereit:

*   **`noctalia-git`** – Die moderne Shell-Umgebung für den Niri Wayland Compositor.
*   **`shelly`** – CLI- / Systemwerkzeuge.
*   **`zen-browser-bin`** – Ein moderner, auf Privatsphäre ausgerichteter Firefox-Fork.

---

## 🔄 Workflow für Paket-Updates (Entwickler-Notiz)

Wenn Sie neue Pakete hinzufügen oder bestehende aktualisieren möchten:

1. Bauen Sie das Paket lokal auf Ihrem System (z. B. via `makepkg`).
2. Kopieren Sie die neue `.pkg.tar.zst`-Datei in den Ordner `x86_64/`.
3. Committen und pushen Sie die Änderung:
   ```bash
   git add x86_64/
   git commit -m "Neu: paket-name hinzufügen"
   git push origin main
   ```
4. Die GitHub Action erledigt den Rest und aktualisiert die Datenbank vollautomatisch innerhalb weniger Sekunden.
