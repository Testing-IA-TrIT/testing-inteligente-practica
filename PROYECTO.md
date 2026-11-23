# Testing Inteligente · El proyecto

AstroBookings vende plazas en lanzamientos espaciales. El enunciado de la práctica está en el [README](README.md).

## Qué incluye

| Proyecto | Carpeta           | Tecnología                                         | Puerto |
| -------- | ----------------- | -------------------------------------------------- | ------ |
| back     | `projects/back/`  | Node.js, TypeScript, Express 5, SQLite             | 3000   |
| front    | `projects/front/` | TypeScript, Vite, Web Components nativos, Pico CSS | 4000   |
| e2e      | `e2e/`            | Playwright, TypeScript                             | —      |

- Las specs están en `specs/<id>-<slug>/`.
- Las pruebas e2e están en `e2e/tests/<id>-<slug>/`.
- Las skills de los agentes están en `.agents/skills/`. Cuando una skill tiene guías en `resources/`, su `SKILL.md` indica cuándo leer cada una.
- Las reglas del proyecto para los agentes están en `AGENTS.md`.

## Cabecera YAML de una spec

- `type` distingue una funcionalidad (`feature`), un arreglo (`bug-fix`), un cambio interno (`refactor`) y un cambio de comportamiento (`change`).
- `solution-mode` indica si `Solution` describe el comportamiento actual (`descriptive`) o define el trabajo de implementación (`prescriptive`). Si falta el campo, la spec se interpreta como prescriptiva.

## Instalar (una vez)

Necesitas Git y Node `^22.18`, `^24.11` o `>=26`. El proyecto se ha probado con Node 26.

Desde la raíz, ejecuta `npm run setup` para instalar las dependencias y Chromium. La configuración por defecto funciona sin archivos `.env`.

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

- `npm run test:e2e` detiene los servidores que inició `npm start`. Si Playwright arranca el back, recrea su base SQLite antes de cargar los datos de prueba. En local, si reutiliza un back que ya está en marcha, ese back conserva su base.
- Para recrear la base a mano, ejecuta `npm run stop` y después `npm run reset`. Si aparece `Cannot delete`, detén el proceso que tiene abierto el archivo y repite el reinicio.

## Hook de commit

El hook pre-commit ejecuta `vp staged`. Aplica `vp check --fix` a los archivos preparados y ejecuta las pruebas unitarias relacionadas con los `.ts`. Un fallo detiene el commit.
