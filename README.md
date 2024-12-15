# Fullstack-Projekt Setup (Vue & Express)

Diese Anleitung führt dich Schritt für Schritt durch das Setup eines Fullstack-Projektes mit einer Vue-Frontend-Applikation (Client) und einem Express-Backend (Server). Die Schritte gehen davon aus, dass du bereits ein Git-Repository angelegt hast.

## Voraussetzungen

- Node.js und npm sind installiert.
- Ein bereits existierendes, initialisiertes Git-Repository liegt vor.

## Schritte

### 1. Projektinitialisierung im Root-Verzeichnis

1. Initialisiere ein neues npm-Projekt:  
   ```bash
   npm init -y
   ```

2. Lege zwei Arbeitsbereiche (Workspaces) für `client` und `server` an:  
   ```bash
   npm init -y -w client -w server
   ```

3. Richte ESLint ein:  
   ```bash
   npm init @eslint/config@latest
   ```

4. Installiere und initialisiere Vuetify (im client-Verzeichnis, wenn abgefragt Projektname `client` angeben):  
   ```bash
   npm init vuetify@latest
   ```

5. Installiere Vitest (zum Testen):  
   ```bash
   npm install -D vitest
   ```
   Ergänze in der `package.json` im Root-Verzeichnis im `scripts`-Abschnitt:
   ```json
   "scripts": {
     "test": "vitest"
   }
   ```

6. Lege eine `.env`-Datei an:  
   ```bash
   touch .env
   ```

### 2. Client-Struktur erstellen

Wechsle in den `client`-Ordner und lege die benötigten Verzeichnisse an:

```bash
mkdir -p src/{assets,components,layouts,pages,plugins,router,services,stores,styles,types,utils}
mkdir -p tests/{unit,integration}
```

### 3. Server-Struktur erstellen

1. Installiere die benötigten Abhängigkeiten:  
   ```bash
   npm install express cors
   ```

2. Erstelle die Verzeichnisstruktur für den Server:
   ```bash
   mkdir -p src/{config,controllers,middleware,models,routes,services,types,utils}
   mkdir -p tests/{unit,integration,e2e}
   ```

3. Lege die Einstiegsdateien für den Server an:
   ```bash
   touch server.js
   touch src/app.js
   ```

### 4. Linting & Formatting Setup

1. Installiere lint-staged im Root:
   ```bash
   npm install lint-staged
   ```

2. Ergänze in der `package.json` im Root-Verzeichnis:
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

3. Initialisiere Husky und installiere Abhängigkeiten:
   ```bash
   npx husky-init && npm install
   ```

4. Füge in der Datei `.husky/pre-commit` folgenden Befehl hinzu:
   ```bash
   npm lint-staged
   npm run test
   ```

## Fertig!

Dein Fullstack-Projekt ist nun grundlegend eingerichtet. Du hast eine klare Verzeichnisstruktur, ein Frontend mit Vue & Vuetify, ein Backend mit Express, sowie Linting- und Formatierungstools vorbereitet. Von hier aus kannst du deine Applikation weiter entwickeln.
