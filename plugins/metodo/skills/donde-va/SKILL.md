---
name: donde-va
description: Coloca cualquier material que llegue en el sitio correcto de la estructura. Usala cuando pregunten 'donde guardo esto?', peguen un documento o un enlace sin decir donde va, o aparezca un archivo suelto en la raiz.
---

# Dónde va

Colocar cualquier cosa que llegue en el sitio correcto de la estructura. Es la skill que decide la adopción entre usuarios que no van a leer las convenciones. Reglas: `metodo/convenciones.md`.

## Cuándo

"¿Dónde guardo esto?", "me llegó este correo, ¿qué hago con él?", o cuando alguien pega un documento, un enlace o unas notas sin decir dónde van.

También cuando aparece un archivo suelto en la raíz o en una carpeta que no le corresponde.

## Qué leo antes

1. La estructura de la raíz: qué áreas hay y qué proyectos tiene cada una
2. `<area>/area.md` del área probable
3. El material en sí, lo justo para clasificarlo

## Las cinco preguntas, en orden

Se para en la primera que dé un sí.

**1. ¿Es material crudo que no hizo el equipo del proyecto?** Exports, PDFs de terceros, transcripciones, correos, capturas. Va a `fuentes/` del proyecto, con un nombre legible. Las fuentes no se editan nunca.

**2. ¿Es algo que otra persona va a leer para construir encima?** Va a `entregables/`, y entonces no se guarda tal cual: se convierte en un entregable con su cabecera, usando `metodo/entregable.md`.

**3. ¿Es un compromiso que cambia lo que se va a construir?** No es un archivo, es una entrada en `decisiones.md`. Se propone la entrada y se pide confirmación antes de registrarla.

**4. ¿Es contexto de la empresa y no de un proyecto?** Organigrama, sistemas, políticas, vocabulario. Va a `empresa/`, que no se toca. Se prepara el texto y se le pasa al responsable de contexto para que lo incorpore.

**5. Ninguna de las anteriores.** Va a `fuentes/` del proyecto más probable, con una línea diciendo qué es y que está sin clasificar. Se decide más adelante, cuando esté claro.

No hay carpeta de borradores. Lo que no es material ni entregable ni decisión se guarda como fuente sin clasificar, o no se guarda.

## Si no hay proyecto al que pertenezca

Dos salidas, y ninguna es dejarlo suelto:

- Si el material sugiere un trabajo que va a durar, se propone crear el proyecto con `metodo/proyecto-nuevo.md`
- Si es contexto general de la empresa, va por la vía de la pregunta 4

Nada se queda en la raíz ni en la carpeta del área. Un archivo huérfano hoy es un archivo que nadie encuentra en tres meses.

## Qué respondo

Una ruta concreta y un nombre de archivo propuesto. Un solo destino, no un menú de opciones. Si de verdad hay ambigüedad entre dos proyectos, una sola pregunta para desempatar.

Después de colocarlo, se dice en una línea qué es lo siguiente que hay que hacer con ese material, si es que hay algo.

## Lo que nunca hago

- Crear una carpeta nueva para acomodar algo que no encaja. Si no encaja, es la pregunta 5
- Dejar algo en la raíz o en la carpeta de un área
- Escribir directamente en `empresa/`
- Mover archivos de un área que no es la del usuario
- Colocar material en un proyecto ajeno sin avisar a su dueño
- Guardar un documento de terceros en `entregables/` tal cual, sin convertirlo
- Dar tres opciones y dejar que el usuario elija. Si dudo, pregunto una cosa y decido

## Ejemplo completo

**Usuario:** me pasaron esto en una reunión, no sé dónde meterlo *[pega una tabla con los tiempos de aprobación por departamento]*

**Respuesta:**

> Es material crudo de una reunión, así que va a `compras/automatizacion-ordenes/fuentes/tiempos-aprobacion-por-departamento.md`. Lo guardo tal cual, con una nota de quién lo pasó y en qué reunión.
>
> Lo siguiente: estos tiempos contradicen el export del ERP en el rango de 5.000 a 20.000 MXN, que es justo el hueco abierto del mapa de proceso. Cuando quieras lo miramos.

---

**Usuario:** ¿y el organigrama nuevo de compras?

**Respuesta:**

> Eso es contexto de empresa, no de proyecto, así que va a `empresa/contexto.md` y esa carpeta no la toco yo.
>
> Te preparo el párrafo redactado para que se lo pases a quien mantiene el contexto. También conviene, porque `contexto.md` lleva 104 días sin actualizarse.
