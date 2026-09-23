# Antworten zu Git Branches und Merging

## 1. Was ist der Unterschied zwischen Working Directory, Staging Area und Repository?

### Working Directory
Das Working Directory ist dein aktueller Arbeitsbereich auf dem Computer. Hier bearbeitest, erstellst oder löschst du Dateien.

### Staging Area
Die Staging Area ist ein Zwischenbereich. Hier landen Änderungen, die du für den nächsten Commit vormerken möchtest.

Beispiel:
```bash
git add datei.txt
```

### Repository
Das Repository enthält die vollständige Versionshistorie des Projekts. Änderungen werden dort durch Commits dauerhaft gespeichert.

**Ablauf:**

```text
Working Directory -> Staging Area -> Repository
      bearbeiten        git add       git commit
```

---

## 2. Woran erkennst du, ob ein Merge Fast-Forward war?

Ein Merge war ein **Fast-Forward-Merge**, wenn Git keinen zusätzlichen Merge-Commit erstellen musste.

Merkmale:

- Der Ziel-Branch wird einfach auf den neuesten Commit des Quell-Branchs verschoben.
- In der Historie erscheint kein Merge-Commit.
- Beim Merge gibt Git häufig folgende Meldung aus:

```text
Fast-forward
```

Beispiel:

```bash
git merge dev
```

Ausgabe:

```text
Updating a1b2c3d..e4f5g6h
Fast-forward
```

---

## 3. Warum kann `git merge --ff-only` manchmal fehlschlagen?

Der Befehl:

```bash
git merge --ff-only
```

funktioniert nur, wenn ein Fast-Forward-Merge möglich ist.

Er schlägt fehl, wenn:

- beide Branches eigene neue Commits besitzen,
- die Historien auseinander gelaufen sind,
- ein Merge-Commit erforderlich wäre.

Beispiel einer Fehlermeldung:

```text
fatal: Not possible to fast-forward, aborting.
```

---

## 4. Was ist der Vorteil, Änderungen zuerst auf einem Branch wie `dev` zu machen?

Vorteile eines Entwicklungs-Branches:

- Der Haupt-Branch (`main`) bleibt stabil.
- Neue Funktionen können getestet werden.
- Fehler gefährden nicht direkt die produktive Version.
- Mehrere Entwickler können parallel arbeiten.
- Änderungen können vor dem Merge überprüft werden.

Dadurch wird das Risiko von Problemen im Haupt-Branch deutlich reduziert.

---

## 5. Mit welchem Befehl siehst du den aktuellen Branch?

```bash
git branch
```

Der aktuelle Branch wird mit einem Stern (`*`) markiert:

```text
* main
  dev
```

Alternativ:

```bash
git status
```

Ausgabe:

```text
On branch main
```

---

## 6. Mit welchen Befehlen machst du Änderungen sichtbar und dauerhaft (Staging & Commit)?

### Änderungen in die Staging Area übernehmen

Eine Datei:

```bash
git add datei.txt
```

Alle Dateien:

```bash
git add .
```

### Änderungen dauerhaft speichern

Commit erstellen:

```bash
git commit -m "Beschreibung der Änderung"
```

### Gesamter Ablauf

```bash
git add .
git commit -m "Neue Funktion hinzugefügt"
```

Damit werden die Änderungen zuerst gestaged und anschließend dauerhaft im Repository gespeichert.