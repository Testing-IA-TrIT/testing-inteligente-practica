# Testing Inteligente · El proyecto

Proyecto base de la práctica final del curso Testing Inteligente: pruebas e2e con inteligencia artificial y Playwright. El enunciado de la práctica está en el [README](README.md).

AstroBookings es una agencia que vende plazas en lanzamientos espaciales. El proyecto tiene una API, una web, las specs, las pruebas y las skills de los agentes.

## Qué incluye

| Proyecto | Carpeta           | Tecnología                                         | Puerto |
| -------- | ----------------- | -------------------------------------------------- | ------ |
| back     | `projects/back/`  | Node.js, TypeScript, Express 5, SQLite             | 3000   |
| front    | `projects/front/` | TypeScript, Vite, Web Components nativos, Pico CSS | 4000   |
| e2e      | `e2e/`            | Playwright, TypeScript                             | —      |

- Las specs están en `specs/<id>-<slug>/`.
- Las pruebas e2e están en `e2e/tests/<id>-<slug>/`.
- Las skills de los agentes están en `.agents/skills/`.
- Las reglas del proyecto para los agentes están en `AGENTS.md`.

## Instalar (una vez)

Necesitas Git y Node `^22.18`, `^24.11` o `>=26`. En la carpeta raíz, ejecuta:

```text
npm run setup
```

Este comando comprueba la versión de Node, instala todos los proyectos e instala Chromium. No necesitas archivos `.env`.

## Comprobaciones y pruebas

Ejecuta estos comandos en la carpeta raíz:

| Comando                            | Qué hace                                                    |
| ---------------------------------- | ----------------------------------------------------------- |
| `npm run check`                    | Formato, lint y tipos. Aplica las correcciones automáticas. |
| `npm test`                         | Pruebas unitarias del back y del front.                     |
| `npm run test:e2e`                 | Toda la suite e2e.                                          |
| `npm run test:e2e -- --grep "@<id>"` | Solo una spec o un journey, por ejemplo `@S0005`.         |
| `npm run verify`                   | `check`, unitarias y e2e, en ese orden. Para si un paso falla. |
| `npm start` / `npm run stop`       | Arranca o para el back y el front.                          |

## La base de datos

- `npm run test:e2e` para los servidores de `npm start`, vacía la base de datos y arranca el back y el front. Cada ejecución empieza con la base de datos vacía.
- Para vaciarla a mano, ejecuta `npm run stop` y después `npm run reset`.

## Hook de commit

El hook pre-commit ejecuta `vp staged`:

- Aplica `vp check --fix` a los archivos del commit.
- Ejecuta las pruebas unitarias relacionadas con los archivos `.ts` del commit.
- Si un comando falla, el commit no se hace.

El hook no ejecuta Playwright. No sustituye a `npm run verify`.
