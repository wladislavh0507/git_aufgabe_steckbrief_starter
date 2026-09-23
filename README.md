# Git-Aufgabe – Steckbrief (Starter-Repository)

Dieses Starter-Repo enthält eine **HTML-Steckbriefvorlage** und eine `README.md`.
Sie ist für die Git-Übungsaufgabe gedacht, in der ein `dev`-Branch erstellt,
Änderungen vorgenommen und anschließend per **Fast-Forward** auf `main` gemergt werden.

## Struktur
```
.
├─ index.html           # Steckbrief-Vorlage (bearbeiten)
├─ README.md            # Diese Datei
└─ assets/
   └─ profil.jpg        # Platzhalterbild (optional ersetzen)
```

## Schnellstart (lokal)
1. Öffne eine Git Bash / Terminal im Ordner dieses Projekts.
2. Initialisiere das Repository:
   ```bash
   git init
   git add .
   git commit -m "Initialer Import: Steckbrief-Vorlage"
   ```
3. Erstelle und wechsle auf einen neuen Branch `dev`:
   ```bash
   git switch -c dev
   ```
4. Nimm Änderungen an `index.html` und dieser `README.md` vor und committe sinnvoll:
   ```bash
   git add index.html README.md
   git commit -m "Profil: Name/Klasse ergänzt; Interests aktualisiert"
   ```
5. Wechsle zurück auf `main` und führe einen **Fast-Forward-Merge** durch:
   ```bash
   git switch main
   git merge --ff-only dev
   ```
6. (Optional) Branch aufräumen:
   ```bash
   git branch -d dev
   ```

## Hinweise
- Ein Fast-Forward gelingt nur, wenn `main` **keine** neuen Commits seit dem Abzweigen erhalten hat.
- Prüfe die Historie und Branch-Situation:
  ```bash
  git log --oneline --graph --decorate --all
  git status
  ```

Viel Erfolg!
