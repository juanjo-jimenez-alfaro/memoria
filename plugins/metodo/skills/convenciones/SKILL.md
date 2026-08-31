---
name: convenciones
description: Contrato base del metodo de trabajo: estructura de carpetas, cabecera de los archivos, estados y que es publico. Consultala antes de crear o modificar cualquier archivo dentro de la estructura de un cliente, y cuando pregunten como se organiza algo, donde va, o que significa un estado.
---

# Convenciones

Contrato base del método. El resto de archivos de `metodo/` referencian este documento en lugar de repetir sus reglas. Si un archivo del método contradice algo de aquí, manda este documento.

Versión del método: **1.1**

## 1. Las tres capas de propiedad

| Capa | Quién escribe | Qué contiene |
|---|---|---|
| `metodo/` | Solo el responsable del método | Cómo se trabaja. Idéntico en todos los clientes |
| `empresa/` | Un único responsable de contexto | Quién es la empresa, cómo se organiza, qué sistemas usa |
| Cada área | El dueño del área | El trabajo real |

Nadie escribe fuera de su capa. Un área lee `empresa/` y `metodo/`, nunca los modifica.

La raíz es la carpeta que contiene `guia.md` y `empresa/`. Ninguna instrucción del método usa rutas absolutas, porque cada usuario tiene la carpeta sincronizada en un sitio distinto.

## 2. Estructura

```
RAIZ/
  guia.md
  metodo/
  empresa/
    contexto.md
    glosario.md
    plantillas/
    mantenimiento.md
  <area>/
    area.md
    <proyecto>/
      proyecto.md
      decisiones.md
      sesiones.md
      entregables/
      fuentes/
```

Tres niveles como máximo: área, proyecto, carpeta del proyecto. Un cuarto nivel significa que ahí había dos proyectos.

## 3. Los archivos de un proyecto

| Archivo | Tipo | Qué contiene |
|---|---|---|
| `proyecto.md` | Vivo | Objetivo, alcance, estado actual, siguientes pasos |
| `decisiones.md` | Registro | Qué se decidió, cuándo, por qué y qué se descartó |
| `sesiones.md` | Registro | Qué se avanzó cada día y qué quedó pendiente |
| `entregables/` | Vivo | El producto del proyecto, en cualquier estado |
| `fuentes/` | Inmutable | Insumos crudos: exports, PDFs, transcripciones, material sin clasificar |

Los tres archivos de la raíz del proyecto y las dos carpetas existen siempre, aunque estén vacías. `sesiones.md` es obligatorio y lo escribe la skill de cierre de sesión, no el usuario.

No hay carpeta de borradores. Un entregable a medias vive en `entregables/` con `estado: borrador`, y lo que todavía no es nada vive en la conversación hasta que merezca ser un archivo.

### Estructura de `proyecto.md`

Fija, porque varias skills escriben en ella:

```markdown
# [Nombre del proyecto]

## Objetivo
[Una frase. Qué problema resuelve y para quién.]

## Terminado significa
[Cómo sabremos que se acabó. Concreto y comprobable.]

## Alcance
Sí: [lo que entra]
No: [lo que queda fuera]

## Quién participa
Dueño: [nombre] ([área])
Consumen esto: [áreas o personas]

## Estado actual
[Dos o tres líneas]

## Siguientes pasos
- [Lista corta]
```

`Estado actual` y `Siguientes pasos` son las dos únicas secciones que reescribe el cierre de sesión. El resto cambia poco y solo a petición del dueño.

## 4. Vivo o registro, nunca las dos cosas

**Un archivo vivo se reescribe** y siempre refleja el presente. Nadie necesita leer su historia para entenderlo.

**Un registro solo crece.** Las entradas nuevas van arriba y las anteriores no se editan jamás, ni para corregir. Si una decisión cambia, se añade una entrada nueva que dice que reemplaza a la anterior.

Un registro nunca vive dentro de un archivo vivo, porque la primera reescritura lo borra.

## 5. Cabecera

Todo `.md` empieza con estas claves y ninguna más:

```yaml
---
estado: vigente
dueno: Ana Pérez
actualizado: 2026-08-29
construido_a_partir_de:
  - empresa/contexto.md
  - compras/automatizacion-ordenes/fuentes/entrevista-ana.md
---
```

Inmediatamente después va el título en `#`, para que quien abra el archivo sin renderizador vea de qué trata en la primera línea legible.

**estado**, cuatro valores y nada más:

- `borrador`: lo está escribiendo alguien, no se construye encima
- `en-revision`: terminado, esperando aprobación del dueño
- `vigente`: aprobado, se puede consumir
- `reemplazado`: superado. Requiere una quinta clave, `reemplazado_por`, con la ruta del sustituto

El paso a `vigente` lo pide siempre el dueño de forma explícita y tiene requisitos: `metodo/revisar.md`. Ninguna otra skill cambia ese estado por su cuenta.

**dueno**: una persona con nombre y apellido. Nunca un área ni un equipo.

**actualizado**: fecha en formato `AAAA-MM-DD`, la del último cambio de contenido real.

**construido_a_partir_de**: rutas relativas a la raíz de todo lo que se usó para escribir el archivo. Es lo que permite detectar que un entregable quedó desactualizado cuando cambia algo aguas arriba. Los registros y las fuentes no llevan esta clave.

Las claves van sin acentos ni eñes.

## 6. Nombres

Minúsculas, guiones en vez de espacios, sin acentos ni eñes, sin fechas ni números de versión. `flujo-aprobacion.md`, no `Flujo de Aprobación v2 FINAL.md`.

El nombre de un archivo es estable durante toda su vida. La versión la lleva Drive y el estado lo lleva la cabecera.

## 7. Qué es público

La superficie pública de un proyecto son `entregables/` y `decisiones.md`. Es lo único que otra persona puede leer para construir encima, y solo si el entregable está `vigente`.

`sesiones.md` y `fuentes/` son taller privado. Nadie de fuera del proyecto los lee ni los cita en `construido_a_partir_de`.

## 8. Rotación

Cuando un registro pasa de unas 1.500 líneas o cambia el año, se archiva con el año en el nombre (`sesiones-2026.md`) y se abre uno nuevo. Lo hace la skill de cierre de sesión, sin preguntar.

## 9. Lo que no existe en este sistema

- Carpetas numeradas (`01-`, `02-`)
- Carpetas llamadas `varios`, `otros`, `temp` o `borrador`
- Un archivo por decisión
- Enlaces wiki `[[asi]]`, callouts propietarios, archivos `.canvas`
- Rutas absolutas dentro de cualquier archivo
- Estado guardado en la memoria del modelo o en un proyecto de Claude. Si un dato importa, está en un `.md`
- Cualquier archivo que el usuario tenga que rellenar a mano

## 10. Actualización del método

`metodo/` se actualiza empujando una versión nueva del paquete. Al abrir sesión se compara la versión instalada contra la de este archivo y se avisa si el cliente se quedó atrás. Nadie edita `metodo/` dentro de la carpeta de un cliente.
