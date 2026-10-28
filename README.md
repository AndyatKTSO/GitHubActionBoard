# GitHub Actions Monitor – öffentliche Repositories

Eine einzige `index.html`, die die öffentlichen Repositories des Kontos `AndyatKTSO` über die offizielle GitHub REST API untersucht.

## Auf GitHub Pages veröffentlichen

1. Ein **öffentliches** Repository `GitHubActionsMonitor` erstellen.
2. `index.html` aus diesem Paket **ins Hauptverzeichnis** hochladen.
3. In **Settings → Pages → Build and deployment** `Deploy from a branch` auswählen; Branch `main`, Ordner `/ (root)`.
4. Webseite öffnen: `https://andyatktso.github.io/GitHubActionsMonitor/`.

Die Seite lädt automatisch beim Öffnen. Mit «Jetzt aktualisieren» wird der Zwischenspeicher ignoriert.

## Daten und Einschränkungen

- Ausschliesslich öffentlich sichtbare Repositories und Workflow-Daten. Keine Anmeldung, kein Token, keine eigenen GitHub Actions notwendig.
- GitHub API: üblicherweise max. 60 nicht authentifizierte API-Anfragen pro Stunde und IP-Adresse. Ein Ladevorgang braucht ungefähr 1 + 2 × Anzahl Repositories API-Anfragen; YAML-Dateien werden separat über raw.githubusercontent.com geladen.
- Bei über 100 Workflow-Ausführungen in einem Repository wird nur unter den letzten 100 nach dem letzten Lauf je Workflow gesucht. Das wird als Hinweis gemeldet.
- YAML-Cron ist als UTC ausgewiesen, sofern nicht eine andere Zeitzone im Workflow konfiguriert ist; bei komplexen Cron-Ausdrücken wird der Originalausdruck angezeigt.
- Externe Taktungen, z. B. über cron-job.org, sind **nicht** über die öffentliche GitHub-API feststellbar. Ein Workflow mit `workflow_dispatch` und ohne `schedule` kann trotzdem von extern gestartet werden.
- Der erste vollständige Live-Lauf muss auf GitHub Pages geprüft werden. Fehler pro Repository werden angezeigt; die Anwendung verändert keine Repositories.
