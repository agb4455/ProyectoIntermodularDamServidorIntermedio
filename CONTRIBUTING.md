# Guía de contribución

Gracias por colaborar en el middle server de Viking Clan Wars.

Este repositorio contiene el motor del juego: API HTTP, Socket.IO, coordinación de partidas, manejo del Time Wheel y sincronización con el DB server.

## 1. Objetivo del repositorio

El middle server es la capa de orquestación central del proyecto. Gestiona:

- autenticación y tokens JWT
- estado de las partidas en memoria
- eventos y sincronización en tiempo real
- integración con Redis, MinIO y DB server
- validación de acciones de juego y flujo de partidas

## 2. Requisitos

- Node.js 22
- npm
- Redis disponible
- acceso a DB server y MinIO en local o a través del entorno de Docker

## 3. Inicio rápido

```bash
npm install
npm run dev
```

Para arrancarlo sin recarga automática:

```bash
npm start
```

## 4. Reglas de desarrollo

- Mantén la lógica de juego centralizada y consistente.
- No compartas secretos ni claves reales en el código ni en commits.
- Si cambias la API o los eventos de Socket.IO, revisa el frontend y el orquestador.
- Usa validación y sanitización en requests y payloads.
- Si añades una nueva regla o balance del juego, documenta el cambio o actualiza la documentación relevante.

## 5. Estructura útil

- `src/config`: configuración central y carga del entorno
- `src/game`: motor, acciones y estado de partidas
- `src/http`: rutas y controladores HTTP
- `src/middleware`: seguridad y validación intermedia
- `src/socket`: eventos Socket.IO y conexión real-time
- `src/db`: acceso y sincronización con DB server

## 6. Convenciones de cambio

Usa ramas descriptivas como:

- `feature/socket-event-battle-sync`
- `fix/matchmaking-join-limit`
- `refactor/time-wheel-state`
- `docs/update-middle-server-guide`

## 7. Convenciones de commits

Ejemplos:

- `feat: add clan join validation`
- `fix: prevent duplicate game sync on restart`
- `refactor: simplify time wheel process loop`
- `docs: improve setup and environment variables`

## 8. Pull requests

Antes de abrir un PR:

- ejecuta `npm test`
- verifica que la API sigue funcionando con el DB server
- revisa que la lógica del juego no rompe el estado de partidas en vivo
- documenta cualquier variable de entorno nueva o cambio de configuración

## 9. Seguridad

- no compartas `JWT_SECRET`, `DB_HANDSHAKE_SECRET` ni credenciales de MinIO
- valida todos los payloads entrantes
- gestiona rate limiting y autenticación en middleware
- revisa qué información se registra en logs para evitar fugas de datos sensibles

## 10. Coordinación con otros repos

- [Orquestador](https://github.com/agb4455/tfm)
- [Frontend](https://github.com/agb4455/ProyectoIntermodularDamFrontend)
- [DB Server](https://github.com/agb4455/ProyectoIntermodularDamBackend)

Gracias por mantener el motor del juego estable y fiable.
