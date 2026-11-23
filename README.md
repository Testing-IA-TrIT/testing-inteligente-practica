# Testing Inteligente · Práctica final

Define, implementa y valida una funcionalidad nueva con los agentes del curso.

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

- El código es `J0002`. El `.feature` que define el journey va en `specs/J0002-<slug>/J0002-<slug>.feature`.
- Vincula cada paso con un criterio existente, como `S0005-R1`. Si falta un criterio, completa la spec correspondiente.

## Preparar el proyecto

Haz un fork o crea tu repositorio con «Use this template». Clónalo y sigue las [instrucciones de instalación](PROYECTO.md#instalar-una-vez).

Antes de empezar y antes de entregar, comprueba que `npm run verify` pasa. Consulta los [comandos y el reinicio de la base de datos](PROYECTO.md#comprobaciones-y-pruebas).

## Qué debes hacer

Usa las skills del curso. Trabaja con cada responsable en su propia conversación.

1. Define e implementa la spec de la cancelación.
2. Prueba la spec.
3. Prueba el journey `J0002`.
4. Ejecuta `detect-bugs` con el código de la spec de cancelación y el alcance «suite completa». Si hay fallos, corrígelos y vuelve a generar el informe.

### Qué debes entregar

Entrega la URL de tu repositorio público de GitHub, sin secretos. Incluye estos archivos y commits.

1. La spec de la cancelación en `specs/<id>-<slug>/<id>.spec.md` y sus archivos `.feature`.
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

Para que la entrega sea válida, el informe debe mostrar la suite completa en verde y las pruebas deben conservar sus comprobaciones.

---

**[Alberto Basalo](https://albertobasalo.dev)**

- [LinkedIn](https://www.linkedin.com/in/albertobasalo/)
- [x/twitter](https://twitter.com/albertobasalo)
- [AI Code Academy](https://aicode.academy)
- [AIDDbot](https://aiddbot.com)
