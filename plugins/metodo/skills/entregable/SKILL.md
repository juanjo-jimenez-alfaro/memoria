---
name: entregable
description: Crea o actualiza un entregable de un proyecto. Usala cuando pidan 'prepara el documento de...', 'necesito un documento con...', 'documenta lo que decidimos sobre...', o 'actualiza el entregable X'.
---

# Entregable

Crear o actualizar un entregable. Reglas de estructura, cabecera y nombres: la skill `convenciones`. Estilo de redacción: la skill `estilo`, sin excepciones, porque un entregable sale del proyecto.

## Cuándo

**Crear**: "prepara el mapa del proceso", "necesito un documento con X", "documenta lo que decidimos sobre Y".

**Actualizar**: "actualiza el flujo de aprobación", "esto cambia el modelo de datos", o cuando una decisión registrada afecta a un entregable existente.

## Qué leo antes de escribir nada

1. `empresa/contexto.md` y `empresa/glosario.md`, para el vocabulario de la casa
2. `<area>/area.md`, su bloque `Proyectos`, para saber qué entregables vigentes hay ya en el área
3. `<area>/<proyecto>/proyecto.md`
4. `decisiones.md` **completo**, no solo las últimas. Un entregable que contradice una decisión de hace ocho meses es peor que no tenerlo
5. Las cabeceras de los demás entregables del proyecto
6. La plantilla de `empresa/plantillas/` que corresponda al tipo de documento: `brief.md`, `comparativo.md`, `reporte-de-decision.md` o `handoff.md`
7. `empresa/sistemas.md`, si el documento toca un sistema
8. Las fuentes concretas que apliquen, de `fuentes/`
9. Si el entregable ya existe, el entregable entero

## Antes de escribir

Tres comprobaciones, resueltas con el usuario en dos o tres líneas, no con un interrogatorio.

**¿Ya existe algo que cubra esto?** Si hay un entregable vigente sobre el mismo tema, en este proyecto o en otro del área según el bloque `Proyectos`, se actualiza ese o se construye encima. No se crea uno nuevo. Una sola verdad por tema.

**¿Quién lo va a leer?** Un documento para el equipo del proyecto y uno para el comité de dirección no se escriben igual. Si es para fuera del proyecto, el estilo se aplica con más rigor y se asume que el lector no conoce el contexto.

**¿De dónde sale cada cosa?** Toda afirmación no obvia tiene que poder rastrearse a un archivo de `construido_a_partir_de`. Si algo importante viene solo de la conversación de hoy, se guarda primero en `fuentes/` como nota y luego se cita. Lo que solo existe en el chat se pierde. Toda cifra lleva fecha o fuente en el mismo párrafo.

## Qué escribo y dónde

**Ubicación**: `entregables/`, dentro del proyecto. Nombre en minúsculas y guiones, estable de por vida, sin número de fase ni de versión.

**Cabecera**: `estado: borrador` siempre al crear, el dueño del proyecto salvo que se diga otra cosa, la fecha de hoy, y en `construido_a_partir_de` todas las rutas que se usaron de verdad. La clave la escribo yo siempre; la persona no tiene que rellenarla. No se listan archivos que se leyeron por encima y no aportaron nada.

La lista vacía `[]` solo se admite para material adoptado, que ya existía antes de entrar en la estructura y del que no hay forma de saber de dónde salió. Un entregable escrito aquí siempre tiene fuentes, aunque sea una sola nota en `fuentes/`. Un `[]` lo detiene `revisar` antes de publicar.

Un entregable a medias vive en `entregables/` con `estado: borrador`, no en otra carpeta. El estado es lo que avisa a los demás de que todavía no se puede consumir.

**Cuerpo**: título en `#` inmediatamente después de la cabecera. Estructura según la plantilla del tipo de documento; si el documento no encaja en ninguno de los cuatro tipos, la que pida el contenido, con la conclusión primero.

**Al actualizar**: se reescribe en su sitio, porque un entregable es un archivo vivo. No se acumulan secciones de "actualización de agosto". Se pone la fecha nueva en `actualizado` y se añaden las fuentes nuevas.

**Al reemplazar**: cuando un entregable queda superado por otro distinto, el viejo pasa a `estado: reemplazado` con la clave `reemplazado_por` y su ruta. No se borra nunca, porque alguien puede tenerlo citado.

**Cuando respalda una decisión**: si el documento es el análisis detrás de una entrada de `decisiones.md` (opciones, tablas, cifras), la entrada lo cita en `Afecta a` o en `Por qué` y el análisis vive aquí, no en el registro.

**Formatos finales** (PPTX, HTML, PDF): se generan desde el `.md` y se guardan junto a él, con el mismo nombre. El `.md` sigue siendo la fuente de verdad y el derivado se regenera cuando cambia. Un derivado editado a mano deja de ser un entregable y pasa a ser un problema.

## Qué respondo al terminar

Dónde quedó, en qué estado, y qué le falta para poder pasar a revisión. Dos o tres líneas.

Si al escribirlo aparecieron decisiones que nadie había tomado, se listan al usuario. No se meten en el documento como si estuvieran cerradas.

## Lo que nunca hago

- Marcar un entregable como `vigente`. Eso lo pide el dueño de forma explícita
- Escribir una afirmación que no sale de una fuente citable
- Dejar `construido_a_partir_de` vacía en un entregable que escribí yo
- Citar en `construido_a_partir_de` un archivo de `sesiones.md` o cualquier taller de otro proyecto
- Construir sobre un entregable que no esté `vigente`, sin avisar de que no lo está
- Crear un entregable nuevo cuando ya hay uno vigente sobre el mismo tema
- Borrar un entregable superado
- Escribir una cifra sin fecha ni fuente
- Rellenar huecos con supuestos razonables. Un hueco se marca como hueco

## Ejemplo completo

**Usuario:** prepara el mapa del proceso de compras actual

**Respuesta:**

> Antes de escribir, dos cosas.
>
> En `compras/area.md` no hay ningún entregable vigente sobre el proceso actual, y en `entregables/` de este proyecto tampoco, así que lo creo nuevo. Voy a construirlo con la grabación de la entrevista con Ana, el export de órdenes y las tres decisiones registradas sobre los topes por monto, siguiendo la plantilla de brief.
>
> ¿Esto lo va a leer solo el equipo del proyecto, o también Finanzas y Sistemas?

**Usuario:** también Finanzas y Sistemas

**Respuesta:**

> Listo: `entregables/mapa-proceso-actual.md`, en `borrador`.
>
> Escrito para alguien de fuera de Compras, con el glosario de la empresa para las siglas del ERP. Construido a partir de la entrevista con Ana, el export de órdenes de 2025 y `decisiones.md`; las tres rutas están en la cabecera.
>
> Le falta una cosa para pasar a revisión: en el paso de validación presupuestal, la entrevista y el export se contradicen sobre quién aprueba entre 5.000 y 20.000 MXN. Lo dejé marcado como hueco en el documento en lugar de elegir uno.
