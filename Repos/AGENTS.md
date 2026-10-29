# Repos

> **TL;DR:** Índice de los repositorios de código clonados en este espacio de trabajo. Cada clon tiene su propio git y NO se versiona aquí; solo este archivo se sube.

## Propósito

Esta carpeta guarda los clones de los repositorios de código sobre los que trabaja el agente. El `.gitignore` del espacio de trabajo excluye todo `Repos/` excepto este `AGENTS.md`, así que cada repo conserva su propio historial y remoto.

## Repositorios

| Repo | Ruta | Remoto | Rama principal | Qué es |
|------|------|--------|----------------|--------|
| lab5-paradigmas-meli | [lab5-paradigmas-meli/](lab5-paradigmas-meli/) | https://github.com/melissa-system/lab5-paradigmas-meli | `main` | UNA Chat (Laboratorio 5 y continuación) |

Para clonar de nuevo:

```bash
cd Repos
git clone https://github.com/melissa-system/lab5-paradigmas-meli.git
cd lab5-paradigmas-meli && npm install
```

## lab5-paradigmas-meli — UNA Chat

- **Stack:** Node.js + Express 5 + Socket.IO 4.8; frontend en `index.html` con jQuery (sin build).
- **Entrada:** `server.js` sirve `index.html` y reenvía el evento Socket.IO `Evento-Mensaje-Server` tras validarlo con `libs/unalib.js`.
- **Validación:** `libs/unalib.js` sanea texto (XSS), detecta URLs de imagen, video y YouTube.
- **Comandos:**
  - `npm start` → servidor en http://localhost:3000
  - `npm test` → pruebas unitarias (Mocha, `test/`)
  - `npx jest tests/integration --runInBand --env=node` → integración (Jest + socket.io-client)
  - `npx playwright test --project=chromium` → E2E (`tests/e2e/`)
  - `npm run snyk:test` → escaneo de dependencias
- **Spec framework:** OpenSpec en `openspec/` (specs `chat-message-validation`, `chat-ux`; cambios archivados en `openspec/changes/archive/`). Los comandos `/opsx-*` están en `.opencode/commands/`. OpenSpec se ejecuta desde dentro del repo, no desde la raíz del espacio de trabajo.
- **Siguiente trabajo:** US-01, autenticación social con Auth0 y despliegue en Vercel (Laboratorio 8).

## Convenciones

- Trabajar los cambios del código dentro del repo y commitear ahí; no mezclar con commits del espacio de trabajo.
- Nunca subir `.env` ni credenciales; usar `.env.example`.
