# Método

Marketplace con el plugin `metodo`: el método de trabajo y documentación por proyecto.

Once skills que escriben y mantienen una estructura de carpetas compartida en Drive, con sesiones, decisiones y entregables en Markdown, para que la carpeta sirva de memoria que la IA lee antes de ayudar a cualquiera.

## Instalación

En Claude Code, Claude Desktop o Cowork:

```
/plugin marketplace add <usuario>/<repo>
/plugin install metodo@metodo-marketplace
```

Para probar en local antes de publicar, desde la carpeta del repo:

```
/plugin marketplace add .
/plugin install metodo@metodo-marketplace
```

En una organización de Claude Team o Enterprise, el propietario puede distribuir el plugin a todos los usuarios sin que cada uno lo instale.

## Qué incluye

| Skill | Para qué |
|---|---|
| `convenciones` | Contrato base: estructura, cabeceras, estados, cómo se lee, qué es público |
| `estilo` | Normas de redacción, siempre activas |
| `sesion` | Abrir y cerrar sesión de trabajo sobre un proyecto |
| `proyecto-nuevo` | Crear el paquete completo de un proyecto |
| `entregable` | Crear o actualizar un entregable |
| `revisar` | Revisar, detectar desfase y publicar |
| `donde-va` | Colocar material que llega en el sitio correcto |
| `consulta` | Responder qué sabe ya la organización, sin escribir nada |
| `area-nueva` | Crear un área con su `area.md` y anotarla en `guia.md` |
| `organizacion-nueva` | Montar la raíz completa de una organización |
| `migrar` | Adoptar una carpeta que venía de otra estructura, sin borrar los originales |

El plugin trae además las cuatro plantillas del método (brief, comparativo, reporte de decisión, handoff) y el archivo `metodo.md` generado.

## Cómo se usa con una organización

Cada organización tiene una raíz sincronizada en Drive, autocontenida, con `guia.md`, `metodo.md` y `empresa/`, y una carpeta por área. La monta la skill `organizacion-nueva`.

`guia.md` es para personas: qué es la carpeta, qué áreas hay, el texto para pegar en las instrucciones de un proyecto de Cowork y qué hacer si programas. `metodo.md` lo genera el plugin y nadie lo edita: reúne el contrato, el estilo y el índice de skills, para que funcionen también con Gemini o con quien abra la carpeta sin el plugin.

El número de versión vive en el plugin y en la primera línea de `metodo.md`. Al abrir sesión se comparan y se avisa si la raíz se quedó atrás; ponerla al día es regenerar `metodo.md` con `plugins/metodo/build-metodo.sh` y copiarlo a la raíz.

## Versiones

**1.2** · Desaparece la carpeta `metodo/` de la raíz; en su lugar hay un `metodo.md` generado desde el plugin y un `guia.md` para personas, con el texto para Cowork y el párrafo para programadores. `area.md` tiene estructura fija y su bloque Proyectos es el índice del área, escrito por las skills. Sección nueva en el contrato sobre cómo se lee la raíz por niveles. Formato único de decisiones con `Afecta a` entre áreas: al abrir sesión se barren las decisiones de toda la raíz y al cerrar se recuerda avisar. `empresa/sistemas.md`, `fuentes/enlaces.md` opcional, nota junto a archivos sensibles y permisos en Drive. Cuatro skills nuevas: `consulta`, `migrar`, `area-nueva` y `organizacion-nueva`, con las cuatro plantillas. En estilo, umbral de guiones largos y cifras con fecha o fuente.

**1.1** · Desaparece la carpeta `borrador/`, que colisionaba con `estado: borrador`. Un entregable a medias vive en `entregables/` con ese estado, y el material sin clasificar en `fuentes/`. El dueño pasa a ser bloqueante al crear un proyecto.

**1.0** · Primera versión.
