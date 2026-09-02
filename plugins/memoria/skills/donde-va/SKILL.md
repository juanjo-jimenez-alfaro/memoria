---
name: donde-va
description: Coloca cualquier material que llegue en el sitio correcto de la estructura. Usala cuando pregunten 'donde guardo esto?', peguen un documento o un enlace sin decir donde va, o aparezca un archivo suelto en la raiz.
---

# Dónde va

Colocar cualquier cosa que llegue en el sitio correcto de la estructura. Es la skill que decide la adopción entre usuarios que no van a leer las convenciones. Reglas: la skill `convenciones`.

## Cuándo

"¿Dónde guardo esto?", "me llegó este correo, ¿qué hago con él?", o cuando alguien pega un documento, un enlace o unas notas sin decir dónde van.

También cuando aparece un archivo suelto en la raíz o en una carpeta que no le corresponde.

## Qué leo antes

1. `guia.md`: qué áreas hay
2. `<area>/area.md` del área probable, su bloque `Proyectos`
3. El material en sí, lo justo para clasificarlo

## Las seis preguntas, en orden

Se para en la primera que dé un sí.

**1. ¿Es un enlace?** Va a `fuentes/enlaces.md` del proyecto, una fila con qué es, el enlace y qué tener presente. Si el archivo no existe, se crea con su tabla. No se guarda una copia de la página como archivo salvo que el usuario lo pida.

**2. ¿Es material crudo que no hizo el equipo del proyecto?** Exports, PDFs de terceros, transcripciones, correos, capturas. Va a `fuentes/` del proyecto, con un nombre legible. Las fuentes no se editan nunca.

Antes de guardarlo se mira si trae indicios de información confidencial: nombres con RFC, CURP o NSS, facturación por cliente, contratos, contraseñas, datos de salud, salarios, o cualquier cosa que no todos deban ver. Si los trae, lo digo y propongo llevarlo a la unidad confidencial de la organización; el usuario decide si es confidencial o no. Si lo es, el archivo va a la unidad confidencial y en `fuentes/enlaces.md` del proyecto queda una fila con qué es, su liga y qué tener presente (por ejemplo, que a los entregables solo sale el agregado). Nada se mueve sin que el usuario lo confirme.

Si la fuente ya existe en otro proyecto de la misma área, no se copia: se cita la original por su ruta.

**3. ¿Es algo que otra persona va a leer para construir encima?** Va a `entregables/`, y entonces no se guarda tal cual: se convierte en un entregable con su cabecera, con la skill `entregable`.

**4. ¿Es un compromiso que cambia lo que se va a construir?** No es un archivo, es una entrada en `decisiones.md`. Se propone la entrada y se pide confirmación antes de registrarla.

**5. ¿Es contexto de la organización y no de un proyecto?** Organigrama, sistemas, políticas, vocabulario. Va a `base/`, que no se toca. Se prepara el texto y se le pasa al responsable de contexto para que lo incorpore. Si es un sistema, el texto va en el formato de la tabla de `sistemas.md`: sistema, para qué, quién da acceso, antes de usarlo.

**6. Ninguna de las anteriores.** Va a `fuentes/` del proyecto más probable, con una línea diciendo qué es y que está sin clasificar. Se decide más adelante, cuando esté claro.

No hay carpeta de borradores. Lo que no es material ni entregable ni decisión se guarda como fuente sin clasificar, o no se guarda.

## Si no hay proyecto al que pertenezca

Dos salidas, y ninguna es dejarlo suelto:

- Si el material sugiere un trabajo que va a durar, se propone crear el proyecto con la skill `nuevo`
- Si es contexto general de la organización, va por la vía de la pregunta 5

Nada se queda en la raíz ni en la carpeta del área. Un archivo huérfano hoy es un archivo que nadie encuentra en tres meses.

## Qué respondo

Una ruta concreta y un nombre de archivo propuesto. Un solo destino, no un menú de opciones. Si de verdad hay ambigüedad entre dos proyectos, una sola pregunta para desempatar.

Después de colocarlo, se dice en una línea qué es lo siguiente que hay que hacer con ese material, si es que hay algo.

## Lo que nunca hago

- Crear una carpeta nueva para acomodar algo que no encaja. Si no encaja, es la pregunta 6
- Dejar algo en la raíz o en la carpeta de un área
- Escribir directamente en `base/`
- Guardar en `fuentes/` un archivo con indicios de información confidencial sin haberlo dicho y preguntado antes
- Mover algo a la unidad confidencial sin que el usuario lo confirme
- Copiar a `fuentes/` una fuente que ya existe en otro proyecto del área
- Mover archivos de un área que no es la del usuario
- Colocar material en un proyecto ajeno sin avisar a su dueño
- Guardar un documento de terceros en `entregables/` tal cual, sin convertirlo
- Poner número de fase, fecha o versión en el nombre
- Dar tres opciones y dejar que el usuario elija. Si dudo, pregunto una cosa y decido

## Ejemplo completo

**Usuario:** me pasaron esto en una reunión, no sé dónde meterlo *[pega una tabla con los tiempos de aprobación por departamento]*

**Respuesta:**

> Es material crudo de una reunión, así que va a `compras/automatizacion-ordenes/fuentes/tiempos-aprobacion-por-departamento.md`. Lo guardo tal cual, con una nota de quién lo pasó y en qué reunión.
>
> Lo siguiente: estos tiempos contradicen el export del ERP en el rango de 5.000 a 20.000 MXN, que es justo el hueco abierto del mapa de proceso. Cuando quieras lo miramos.

---

**Usuario:** y este Excel con los sueldos del equipo de compras, que lo necesito para el cálculo del tope

**Respuesta:**

> Trae nombres con salario, así que no lo guardo en `fuentes/`, donde lo lee todo el equipo. Propongo llevarlo a `Acme · Confidencial` y dejar en `compras/automatizacion-ordenes/fuentes/enlaces.md` una fila: qué es, su liga, que lo pasó Recursos Humanos el 1 de septiembre y que a los entregables solo sale el total agregado. ¿Lo tratamos como confidencial?

**Usuario:** sí

**Respuesta:**

> Hecho. Para el cálculo del tope uso el total agregado, sin nombres.

---

**Usuario:** ¿y el organigrama nuevo de compras?

**Respuesta:**

> Eso es contexto de la organización, no de proyecto, así que va a `base/contexto.md` y esa carpeta no la toco yo.
>
> Te preparo el párrafo redactado para que se lo pases a quien mantiene el contexto. También conviene, porque `contexto.md` lleva 104 días sin actualizarse.
