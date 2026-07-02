# gacetas-semanales-pa

Skill para [Claude Cowork](https://claude.ai) que genera un **resumen semanal de todas las normas publicadas en la Gaceta Oficial de Panamá**: leyes, decretos ejecutivos, decretos de gabinete, resoluciones, acuerdos municipales, avisos y edictos, con enlace al PDF oficial de cada norma.

Autor: Osvaldo Quintero
---

## Qué hace

- Enumera las gacetas publicadas en una semana dada usando **Legispan** (asamblea.gob.pa), que lista las ediciones en orden cronológico con fecha visible.
- Lee el índice de cada gaceta directamente desde **Gaceta Oficial** (gacetaoficial.gob.pa), extrayendo entidad, tipo y número, fecha y sumilla de cada norma.
- Produce un **digesto estructurado en Markdown** con sección de destacados, detalle por gaceta y enlaces a PDF verificables.
- Cubre semana en curso o semana anterior (a elección del usuario), y advierte cuando las ediciones más recientes aún no están disponibles por el desfase conocido de Legispan.

## Requisitos

- **Claude in Chrome conectado.** Legispan es una aplicación Ionic/JavaScript que no se puede leer con `web_fetch`; el skill la navega con el navegador.
- Las páginas de Gaceta Oficial sí se leen con `web_fetch`.

## Cómo usar

Una vez instalado el skill en Claude Cowork, escribe `/gacetas-semanales-pa` o pide:

- "resumen semanal de la Gaceta Oficial"
- "qué se publicó esta semana en la Gaceta"
- "normas de la semana en Panamá"
- "boletín / digesto semanal de gacetas"

El skill te preguntará qué semana resumir (en curso o anterior) y entregará el resultado en el chat.

---

## ⚠️ Avisos importantes

### Este skill no es asesoramiento legal

El resumen producido tiene carácter **informativo** y se basa en los títulos del índice oficial. No constituye asesoramiento legal ni puede sustituir la lectura del texto completo de cada norma en la Gaceta Oficial. Para el texto y los efectos exactos de cualquier disposición, descargue el PDF correspondiente.

### Vigencia de la información

El skill accede a las fuentes oficiales en tiempo real, pero está sujeto a la disponibilidad de Legispan y Gaceta Oficial, y al desfase habitual de ~1 día de Legispan respecto a la publicación oficial.

### Limitaciones del modelo de IA

Claude puede cometer errores al extraer o resumir títulos. Verifique siempre con el PDF oficial antes de actuar sobre cualquier norma.

### Advertencia de datos personales

No comparta en el chat documentos con datos personales al utilizar este skill sin la autorización de sus titulares.

---

## Licencia

Este skill se distribuye bajo la **Licencia Apache 2.0**.

Fue desarrollado íntegramente por **Osvaldo Quintero**.

El texto completo de la licencia se encuentra en el archivo [`LICENSE`](./LICENSE).

## Contribuciones

Las contribuciones son bienvenidas. Si el flujo de navegación de Legispan cambia, si Gaceta Oficial modifica su estructura o tienes mejoras al formato del resumen, abre un issue o un pull request.
