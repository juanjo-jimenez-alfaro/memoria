---
name: sesion
description: Abre y cierra sesiones de trabajo sobre un proyecto. Usala cuando digan 'abre sesion', 'retomamos X', 'en que quedamos con...', 'cierra la sesion', 'guarda lo de hoy' o 'terminamos'.
---

# Sesión

Abrir y cerrar una sesión de trabajo sobre un proyecto. Reglas de estructura, cabecera y nombres: `metodo/convenciones.md`.

## Cuándo

**Abrir**: "abre sesión en compras", "retomamos automatización de órdenes", "¿en qué quedamos con X?", o cualquier arranque de trabajo sobre un proyecto existente.

**Cerrar**: "cierra la sesión", "guarda lo de hoy", "terminamos".

Si no queda claro el proyecto, preguntarlo antes de leer nada. Nunca asumir el último proyecto usado.

---

# Abrir sesión

Abrir es solo lectura. No se escribe ningún archivo al abrir.

## Qué leo antes de responder

En este orden:

1. `metodo/convenciones.md`, solo la versión del método
2. `empresa/contexto.md` y `empresa/glosario.md`
3. `<area>/area.md`
4. `<area>/<proyecto>/proyecto.md`
5. `decisiones.md`, las 5 entradas más recientes
6. `sesiones.md`, las 3 entradas más recientes
7. `entregables/`, solo las cabeceras de cada archivo: nombre, estado, dueño, actualizado

No leo `fuentes/` al abrir. Se lee cuando el trabajo del día lo pida.

## Qué respondo

Tres bloques, en este orden y sin encabezados largos.

**Dónde quedó todo.** Cuatro o cinco líneas: objetivo del proyecto en una frase, qué se hizo en la última sesión, qué quedó pendiente. Nada de recapitular el proyecto entero.

**Avisos**, solo si aplican. Cuatro comprobaciones:

- La versión del método instalada es anterior a la de `metodo/convenciones.md`
- `empresa/contexto.md` lleva más de 90 días sin actualizarse
- Algún entregable tiene en `construido_a_partir_de` un archivo cuya fecha `actualizado` es posterior a la suya, y por tanto puede estar desfasado
- Algún entregable lleva más de 30 días en `borrador` o `en-revision`

Si no hay avisos, no se menciona que no los hay.

**Propuesta de trabajo.** Dos o tres focos posibles, tomados de los siguientes pasos de `proyecto.md` y de lo que quedó pendiente en la última sesión, cada uno con una línea de por qué ahora. Se ordenan por lo que desbloquea a otros: primero lo que otra persona está esperando, después lo que cierra algo empezado, al final lo que abre frente nuevo. Termina preguntando por cuál empezamos, y espera respuesta.

Si un aviso afecta al foco propuesto, se dice ahí mismo. No se empieza a trabajar sobre un entregable posiblemente desfasado sin avisar antes.

---

# Cerrar sesión

## Qué escribo y dónde

**1. `sesiones.md`.** Entrada nueva arriba del todo, sin tocar las anteriores:

```markdown
## 2026-08-29
Trabajamos en: rediseño del flujo de aprobación por monto.
Avances: mapa del proceso actual terminado y pasado a en-revision.
Pendiente: confirmar con Finanzas el tope de 5.000 MXN.
```

Tres líneas. Si una sesión no cabe en tres líneas, es que hubo decisiones y esas van a su archivo.

**2. `decisiones.md`, solo si hubo decisiones.** Antes de escribir, se listan al usuario las decisiones detectadas y se pide confirmación explícita. El registro no se puede corregir después, así que nada entra sin que alguien lo confirme. Formato:

```markdown
## 2026-08-29 · Las órdenes bajo 5.000 MXN no pasan por aprobación
Decidió: Ana Pérez
Por qué: el 70% del volumen son órdenes pequeñas y consumían el 80% del tiempo de aprobación.
Descartamos: tope acumulado mensual por proveedor, porque el ERP no expone el acumulado en tiempo real.
Afecta a: entregables/flujo-aprobacion.md
```

Una decisión es un compromiso que cambia lo que se va a construir. Una preferencia expresada en voz alta no lo es. Ante la duda, se pregunta.

**3. `proyecto.md`.** Se reescriben `Estado actual` y `Siguientes pasos`. Es un archivo vivo: se sustituye el contenido anterior, no se acumula.

**4. Cabeceras de lo que se tocó.** Se actualiza `actualizado` en cada archivo modificado y se añade a `construido_a_partir_de` cualquier fuente nueva que se haya usado.

**5. Rotación.** Si `sesiones.md` supera las 1.500 líneas o cambia el año, se renombra con el año (`sesiones-2026.md`) y se abre uno nuevo. Sin preguntar.

## Qué respondo al terminar

Dos o tres líneas: qué archivos se escribieron y qué queda para la próxima. Nada más. El resumen largo ya está en los archivos.

---

## Lo que nunca hago

- Escribir algo al abrir sesión
- Editar una entrada existente de `sesiones.md` o `decisiones.md`, ni para corregir una errata
- Registrar una decisión que el usuario no confirmó en esta sesión
- Cambiar el `estado` de un entregable a `vigente`. Eso lo pide el dueño de forma explícita
- Tocar archivos fuera del proyecto activo
- Escribir en `empresa/` o en `metodo/`
- Rellenar un pendiente con una suposición. Si no sé si algo quedó cerrado, pregunto

---

## Ejemplo completo

**Usuario:** retomamos automatización de órdenes

**Respuesta al abrir:**

> El proyecto busca quitar aprobaciones manuales en compras de bajo monto. La última sesión, el 14 de agosto, terminaste las entrevistas con Ana y con el equipo de Finanzas y quedó pendiente decidir el criterio de corte.
>
> Dos avisos: `empresa/contexto.md` no se toca desde hace 104 días, y `entregables/mapa-proceso.md` está en `en-revision` desde hace 41 días esperando a Ana.
>
> Tres focos posibles para hoy:
>
> 1. Cerrar el criterio de corte por monto. Es lo que bloquea el flujo de aprobación y Finanzas está esperando.
> 2. Empujar la revisión del mapa de proceso, que lleva seis semanas parado.
> 3. Empezar el modelo de datos del conector con el ERP, que todavía no depende de nadie.
>
> ¿Por cuál empezamos?

**Usuario:** por el 1. [conversación de trabajo] ... cierra la sesión

**Antes de escribir:**

> Detecté una decisión en la conversación de hoy:
>
> Las órdenes bajo 5.000 MXN no pasan por aprobación. Decidió Ana Pérez. Descartamos el tope acumulado mensual porque el ERP no lo expone en tiempo real.
>
> ¿La registro así en `decisiones.md`?

**Usuario:** sí

**Respuesta al cerrar:**

> Escribí la entrada en `decisiones.md`, la sesión de hoy en `sesiones.md` y actualicé los siguientes pasos en `proyecto.md`. Marqué `entregables/flujo-aprobacion.md` como afectado por la decisión.
>
> Para la próxima queda validar el criterio con Finanzas y reanudar la revisión del mapa de proceso.
