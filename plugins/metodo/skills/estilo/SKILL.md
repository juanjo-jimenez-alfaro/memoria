---
name: estilo
description: Normas de estilo de redaccion. Aplicala por defecto al redactar o revisar cualquier texto que se vaya a firmar o compartir, sin que la invoquen, y cuando pidan 'que suene menos a IA', 'mas ejecutivo', 'mas al grano' o 'revisa el estilo'.
---

# Estilo

Estilo de todo lo que se escribe, firma o comparte en esta estructura:

> **Ejecutivo y al grano: el hecho relevante desde el inicio, sin rodeos ni expresiones que no aporten de manera directa.**

Este archivo es la fuente canónica del estilo. Si una plantilla de `empresa/plantillas/` lo contradice, manda este archivo.

## Cuándo se aplica

Siempre, sin que nadie la invoque, en cualquier redacción o revisión. Y de forma explícita cuando alguien pide que suene menos a IA, más ejecutivo, más al grano, o que le quiten los rodeos.

## Las dos preguntas que resuelven casi todo

1. **¿La primera frase ya dice el hecho, o lo anuncia?** Si lo anuncia, empieza por el hecho.
2. **¿Puedo borrar esta palabra y no se pierde información?** Entonces sobra.

## Seis patrones a evitar

**1. Metadiscurso, frases que anuncian en vez de decir.** El patrón que más suena a IA: construye expectativa antes de entregar contenido.

- Mal: *"El punto central es que el motor propio sale más barato."* · *"Y el hallazgo que reordena la pregunta: no existe API fiscal mexicana."* · *"Lo que conviene tener claro:"* · *"para una lectura equilibrada"*
- Bien: *"El motor propio sale 5× más barato."* · *"No existe API fiscal mexicana en el mercado."*

**2. Guiones largos como muletilla.** Cuando el guion sustituye a dos puntos, coma o punto y coma, usa la puntuación normal. Resérvalos para incisos que funcionan como paréntesis.

- Mal: *"La decisión es clara — modernizar el motor."*
- Bien: *"La decisión es clara: modernizar el motor."*
- Bien, inciso legítimo: *"El motor —heredado de 2007— sigue en producción."*

**3. Negaciones en espejo.** *"No es X, es Y."* Legítimas solo cuando corrigen una expectativa falsa que el lector traía. Si no la traía, di Y directamente.

- Mal: *"No es un problema de producto, es un problema de go-to-market."* (si nadie dijo que fuera de producto)
- Bien: *"El problema es de go-to-market."*

**4. Rodeos en las conclusiones.** La conclusión es lo que menos tolera preámbulo.

- Mal: *"La postura de fondo es modernizar."* → Bien: *"Modernizar."*

**5. Negritas como subrayado nervioso.** Una negrita destaca; cinco no destacan ninguna. En documentos internos ayudan a escanear; en un documento para terceros, tres por párrafo cansan.

**6. Signos que no se leen en voz alta en español.** Si no puedes leer el signo en voz alta, escribe la palabra. El caso cerrado es `§`, que no aparece en ningún documento.

- Mal: *"ver §4.1"* · *"§§ 2, 3"* · *"del §8"* · *"§ Nómina"*
- Bien: *"ver la sección 4.1"* · *"secciones 2 y 3"* · *"de la sección 8"* · *"sección Nómina"*
- Se conservan `%`, `·`, `→`, el `#` de un ticket, y cualquier signo que sea parte de un identificador citado literalmente.

## Alcance

- **Entregables y cualquier texto que salga del proyecto:** los seis patrones, sin excepción.
- **Registros** (`sesiones.md`, `decisiones.md`): pueden ser más extensos, porque su función es dejar constancia del razonamiento. El metadiscurso y los rodeos sobran igual.

## Al revisar un texto existente

1. Señala los pasajes concretos y propón la reescritura. No reescribas el documento entero en silencio.
2. Cuenta los guiones largos antes y después. Es la medida más rápida de si el texto mejoró.
3. No toques las citas textuales de terceros ni los nombres propios de documentos y decisiones.
4. Corregir el estilo de un entregable de otro proyecto o de otra área es tocar contenido ajeno, no forma. Se propone al dueño, no se aplica.
