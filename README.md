# setup_vue_express_project
This repository shows how to set up a template fullstack-project using vuejs and express.

# Projekt-Setup für ein Fullstack-Projekt mit Vue (Client) und Express (Server)

Diese Anleitung beschreibt die initiale Einrichtung eines Fullstack-Projekts bestehend aus einem Vue-Frontend und einem Express-Backend.  

## Voraussetzungen

- Node.js (inkl. npm) ist installiert
- Git-Repository ist initialisiert

## Schritte

### 1. Grundkonfiguration im Projekt-Root

1. Erstelle eine `package.json` im Projekt-Root:
   ```bash
   npm init -y
   ```
2. Erstelle jeweils eine `package.json` für Client und Server (Workspaces):
   ```bash
   npm init -y -w client -w server
   ```
3. Richte ESLint im Root-Verzeichnis ein:
   ```bash
   npm init @eslint/config@latest
   ```
4. Erstelle das Vue-Frontend im Client-Verzeichnis:
   ```bash
   npm create vue@latest client
   ```
5. Lege eine `.env`-Datei im Root-Verzeichnis an:
   ```bash
   touch .env
   ```

### 2. Client-Struktur anlegen

1. Erstelle die benötigten Ordner für den Client:
   ```bash
   mkdir -p client/src/{assets,components,composables,services,stores,types,utils,views}
   mkdir -p client/tests/{unit,integration}
   ```

### 3. Server-Struktur anlegen

1. Installiere Express und CORS im Server-Verzeichnis:
   ```bash
   cd server
   npm install express cors
   cd ..
   ```
2. Erstelle die Ordnerstruktur für den Server:
   ```bash
   mkdir -p server/src/{config,controllers,middleware,models,routes,services,types,utils}
   mkdir -p server/tests/{unit,integration,e2e}
   ```
3. Erstelle die Hauptdateien für den Server:
   ```bash
   touch server/server.js
   touch server/src/app.js
   ```

### 4. Code-Qualität und Pre-Commit Hooks

1. Installiere lint-staged im Root:
   ```bash
   npm install lint-staged
   ```
2. Füge im `package.json` (im Root) folgende Konfiguration für `lint-staged` ein:
   ```json
   "lint-staged": {
     "client/**/*.{ts,vue}": [
       "prettier --write",
       "eslint --fix"
     ],
     "server/**/*.ts": [
       "prettier --write",
       "eslint --fix"
     ]
   }
   ```
3. Initialisiere Husky und installiere die Abhängigkeiten:
   ```bash
   npx husky-init && npm install
   ```
4. Öffne die erstellte `.husky/pre-commit` Datei und ergänze den folgenden Befehl:
   ```bash
   npm lint-staged
   ```

### 5. Nächste Schritte

- Konfiguriere bei Bedarf weitere ESlint- und Prettier-Regeln.
- Implementiere erste Routen im Server und teste sie mit dem Client.
- Ergänze Tests in den entsprechenden Verzeichnissen.

---

Diese Schritte bilden die Grundlage für ein sauberes Fullstack-Setup mit Vue und Express. Mit dieser Struktur lassen sich Client- und Server-Code logisch trennen, Workflows via Husky und lint-staged sicherstellen, dass Code-Qualität eingehalten wird, und mittels `eslint` und `prettier` ein einheitlicher Code-Style gewährleistet werden.
