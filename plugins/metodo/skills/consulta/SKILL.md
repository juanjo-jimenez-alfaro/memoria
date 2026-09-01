---
name: consulta
description: Responde preguntas sobre lo que la organizacion ya sabe, leyendo solo la superficie publica de la raiz y sin escribir nada. Usala cuando pregunten 'que sabemos de X?', 'alguien ya trabajo esto?', 'que se decidio sobre...?', 'hay algo hecho sobre...?' o 'quien lleva...?'.
---

# Consulta

Responder una pregunta con lo que ya está escrito en la raíz, diciendo de dónde sale cada cosa. Es la skill que usa alguien de otra área, un programador antes de tocar código, o cualquiera que quiera saber si algo ya existe antes de empezarlo. Reglas de lectura y de qué es público: la skill `convenciones`.

## Cuándo

"¿Qué sabemos de X?", "¿alguien ya trabajó esto?", "¿qué se decidió sobre los topes de aprobación?", "¿hay algo hecho sobre proveedores?", "¿quién lleva el tema de facturación?".

También cuando en medio de otra tarea hace falta saber qué hizo otra área antes de construir encima.

No es abrir sesión. Si la pregunta es sobre el proyecto en el que el usuario va a trabajar hoy, eso es la skill `sesion`.

## Qué leo antes de responder

Por el camino de lectura de `convenciones`, y me paro en el primer nivel que responde:

1. `guia.md`: qué áreas hay y quién responde por cada una
2. `empresa/glosario.md`, para entender los términos de la pregunta, y `empresa/contexto.md` si la pregunta es sobre la organización
3. `area.md` de las áreas pertinentes, su bloque `Proyectos`. Casi siempre esto ya dice si existe algo y dónde
4. Solo si hace falta, del proyecto que toque: `proyecto.md`, `decisiones.md` completo y las cabeceras de `entregables/`
5. El cuerpo de un entregable `vigente`, solo si la pregunta pide el contenido y no basta con saber que existe
6. `empresa/sistemas.md`, si la pregunta es sobre un sistema

Un entregable en `borrador` o `en-revision` se menciona si existe, con su estado, pero no se cita su contenido como si fuera verdad de la organización.

## Qué respondo

Respuesta corta y primero la respuesta, no el recorrido. Después, una línea por cada cosa que digo, con la ruta de donde salió:

> Sí, Compras decidió el 29 de agosto que las órdenes bajo 5.000 MXN no pasan por aprobación. Lo decidió Ana Pérez.
>
> De dónde sale: `compras/automatizacion-ordenes/decisiones.md`, entrada del 2026-08-29. El flujo completo está en `compras/automatizacion-ordenes/entregables/flujo-aprobacion.md`, vigente desde el 2026-08-30.

Si hay varias fuentes que se contradicen, se dicen las dos con su fecha y no se elige una.

Si no hay nada escrito sobre el tema, se dice en una línea y se propone dónde debería vivir: qué área y, si aplica, si merece un proyecto nuevo con la skill `proyecto-nuevo` o una entrada en `empresa/`. No se inventa una respuesta con lo que parece razonable.

Si la pregunta es sobre quién lleva algo, la respuesta es la persona con nombre y apellido que dice `guia.md`, `area.md` o `proyecto.md`, nunca el nombre del área.

## Lo que nunca hago

- Escribir o modificar ningún archivo. Consultar es solo lectura
- Leer `sesiones.md` ni `fuentes/` de ningún proyecto de otra área. Son taller privado y no responden a nadie de fuera
- Leer todo. Si `area.md` ya responde, no abro el proyecto; si `proyecto.md` responde, no abro los entregables
- Citar el contenido de un entregable que no esté `vigente` como si lo estuviera
- Responder desde la memoria de la conversación en vez de desde los archivos
- Dar una respuesta sin la ruta de donde salió
- Inventar una respuesta cuando no hay nada escrito

## Ejemplo completo

**Usuario:** ¿alguien ya trabajó lo de los topes de aprobación por monto? Lo necesito para el conector del ERP

**Respuesta:**

> Sí. Compras lo tiene decidido y documentado.
>
> La decisión: las órdenes bajo 5.000 MXN no pasan por aprobación; entre 5.000 y 20.000 MXN aprueba el jefe de área. Decidió Ana Pérez el 29 de agosto de 2026. Sale de `compras/automatizacion-ordenes/decisiones.md`.
>
> El flujo completo, con los estados que espera el ERP, está en `compras/automatizacion-ordenes/entregables/flujo-aprobacion.md`, vigente desde el 30 de agosto. Es lo que tendrías que citar en tu `decisiones.md` cuando ancles la lógica del conector.
>
> Hay además un `mapa-proceso-actual.md` en el mismo proyecto, pero está en revisión: no lo uses como base todavía.

---

**Usuario:** ¿qué sabemos de la evaluación de proveedores de logística?

**Respuesta:**

> Nada escrito. Ni `operaciones/area.md` ni `compras/area.md` tienen un proyecto sobre proveedores de logística, y en `empresa/contexto.md` solo aparece el nombre del proveedor actual.
>
> Si se va a trabajar, le corresponde a Operaciones, cuyo dueño es Marta Ruiz según `guia.md`. Sería un proyecto nuevo; si quieres lo arrancamos con `proyecto-nuevo`.
