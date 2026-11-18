# Testing Inteligente · Práctica final

Aplica el proceso de todo el curso a una funcionalidad nueva: defínela, impleméntala y valídala con agentes. Entrega el resultado en tu GitHub.

## La petición

> Ahora una reserva no se puede cancelar. Queremos permitirlo.
>
> Un operador con sesión cancela la reserva de un pasajero desde la página de pasajeros del lanzamiento. Cada reserva tiene su opción de cancelar.
>
> Al cancelar, la reserva no se borra. Queda en la lista, marcada como cancelada y sin la opción de cancelar. Las plazas libres aumentan en una. Otro pasajero puede ocupar esa plaza. El mismo pasajero también puede volver a reservar.
>
> Solo se puede cancelar en lanzamientos planificados o confirmados. En los otros estados, la página no ofrece la opción y el sistema rechaza la cancelación.
>
> El sistema también rechaza la cancelación de una reserva que no existe, la de una reserva ya cancelada, la de un usuario sin sesión y la de un pasajero.
>
> Fuera de alcance: reembolsos, avisos a pasajeros, deshacer una cancelación, filtrar las reservas canceladas y confirmación antes de cancelar.

## El journey

Cuando la cancelación funcione, prueba también el objetivo completo del operador:

> El operador entra, reserva una plaza para un pasajero en un lanzamiento y cancela esa reserva. Al final ve otra vez la plaza libre.

- El código es `J0002`. El `.feature` va en `specs/J0002-<slug>/J0002-<slug>.feature`. No tiene `spec.md`.
- Cada paso apunta a un criterio que existe, por ejemplo `S0005-R1`. El journey no añade reglas nuevas.
- Si un paso no tiene criterio, la spec tiene un hueco. Corrige la spec, no el journey.

## Preparar el proyecto

Necesitas Git y Node `^22.18`, `^24.11` o `>=26`. El proyecto se ha probado con Node 26.

Haz un fork de este repositorio, o crea el tuyo con «Use this template». Clónalo. Después, ejecuta este comando en la carpeta raíz:

```text
npm run setup
```

Comprueba tu versión de Node, instala todos los proyectos e instala Chromium. No necesitas crear archivos `.env`.

El archivo [PROYECTO.md](PROYECTO.md) describe las carpetas, los comandos y el hook de commit.

## Ejecutar las pruebas

Todo se ejecuta en la carpeta raíz. No es necesario entrar en `e2e/`.

| Qué | Comando |
| --- | --- |
| Formato, lint y tipos | `npx vp check` |
| Pruebas unitarias | `npm test` |
| Toda la suite e2e | `npm run test:e2e` |
| Solo una spec o un journey | `npm run test:e2e -- --grep "@<id>"` |
| Todas las comprobaciones | `npm run verify` |

Antes de empezar y antes de entregar, comprueba que `npm run verify` pasa.

## La base de datos

- `npm run test:e2e` para los servidores de `npm start`, vacía la base de datos y arranca el back y el front. Cada ejecución empieza con la base de datos vacía.
- Para vaciarla a mano, ejecuta `npm run stop` y después `npm run reset`. Con los servidores en marcha, `npm run reset` falla con `Cannot delete`.

## Qué debes hacer

Aplica el proceso del curso: cada responsable en su propia conversación y con sus skills. Si una prueba falla, haz el triage antes de corregir. No debilites una prueba para que pase.

1. Define e implementa la spec de la cancelación.
2. Prueba la spec.
3. Prueba el journey `J0002`.
4. Ejecuta toda la suite y corrige los fallos que encuentres.

### Qué debes entregar

La URL de tu repositorio, público y sin secretos, con:

1. La spec y sus `.feature`.
2. El `.feature` del journey `J0002`.
3. El código del back y del front, con sus pruebas unitarias.
4. Las pruebas e2e de la spec y del journey, y el informe `e2e-report.md` de toda la suite.
5. Commits convencionales, con la spec antes que el código.

### Cómo se evalúa

| Criterio | Puntos |
| --- | --- |
| Definir: la spec y los escenarios cubren la petición. Cada paso del journey apunta a un criterio que existe | 30 |
| Implementar: el código cumple la spec | 30 |
| Validar: las pruebas de la spec y del journey siguen las reglas del curso. Si una prueba falla, el triage está en `fix.spec.md` antes de la corrección | 30 |
| Proceso: los commits muestran el trabajo por pasos | 10 |

Si ninguna prueba falla, no necesitas un triage. La evidencia es el informe `e2e-report.md` de toda la suite, en verde.

No es válida si la suite falla o si has debilitado una prueba para que pase.
