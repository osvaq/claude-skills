---
name: gacetas-semanales-pa
description: >-
  Genera un resumen de TODAS las normas publicadas durante una semana en la Gaceta Oficial de
  Panamá. Usa SIEMPRE este skill cuando el usuario pida el "resumen semanal de la gaceta", "qué se
  publicó esta semana en la Gaceta Oficial", "normas de la semana en Panamá", "boletín / digesto
  semanal de gacetas", "gacetas de esta semana", "resumen de la Gaceta Oficial", o invoque
  /gacetas-semanales-pa — aunque no mencione las palabras exactas "Legispan" o "Gaceta Oficial".
  El skill enumera las gacetas de la semana en Legispan (asamblea.gob.pa) y luego extrae el índice
  de cada una desde gacetaoficial.gob.pa para producir un resumen ordenado. Requiere el navegador
  (Claude in Chrome) porque Legispan se renderiza con JavaScript.
---

# Resumen semanal de la Gaceta Oficial de Panamá

## Qué hace este skill

Produce un **digesto de todas las normas publicadas en una semana** en la Gaceta Oficial de Panamá:
ley por ley, decreto por decreto, resolución por resolución, acuerdo municipal por acuerdo
municipal, más avisos y edictos. Para cada norma da: entidad emisora, tipo y número, fecha,
título oficial (la "sumilla") y el enlace al PDF.

La razón de existir del skill es que **la página de Gaceta Oficial no tiene un buscador por
semana** — solo muestra la gaceta más reciente y permite buscar por número. En cambio **Legispan**
(la base de datos legislativa de la Asamblea) sí lista las gacetas en orden cronológico con su
fecha bien visible. Por eso el flujo es: *enumerar en Legispan → leer el contenido en Gaceta
Oficial*. Respeta ese orden; intentar enumerar la semana directamente en Gaceta Oficial es un
callejón sin salida.

## Requisitos

- **Claude in Chrome conectado.** Legispan es una app Ionic/JavaScript: `web_fetch` devuelve vacío,
  hay que navegarla con el navegador. Si Chrome no está conectado, díselo al usuario y pídele que
  lo conecte antes de continuar; no intentes sustituirlo con `web_fetch` ni con `curl`.
- Las páginas de Gaceta Oficial (`/gaceta/{id}`) sí se leen con `web_fetch`, que es la forma más
  limpia de extraer el índice (devuelve una tabla con los enlaces a PDF). Úsalo para esa parte.

## Paso 0 — Preguntar la semana y fijar el rango

**Lo primero, antes de buscar nada, pregunta al usuario qué semana quiere** (con la herramienta de
preguntas si está disponible; si no, pregúntalo en el chat y espera la respuesta):

> ¿Qué semana resumo? **1) Semana en curso** (lunes a viernes de esta semana) · **2) Semana
> anterior** (lunes a viernes de la semana pasada)

Si el usuario, en su mensaje inicial, ya indicó otra semana concreta ("del 15 al 19 de junio", "la
primera semana de mayo"), respétalo y no preguntes.

Calcula las fechas con `bash` para no equivocarte con el calendario:

```bash
# Semana EN CURSO
date -d "monday this week" +%Y-%m-%d ; date -d "friday this week" +%Y-%m-%d
# Semana ANTERIOR
date -d "monday last week" +%Y-%m-%d ; date -d "friday last week" +%Y-%m-%d
```

Confirma brevemente el rango que vas a resumir (ej. "Resumo la semana en curso: lunes 22 al viernes
26 de junio de 2026") y sigue.

Nombres de meses en español para emparejar fechas: enero, febrero, marzo, abril, mayo, junio,
julio, agosto, septiembre, octubre, noviembre, diciembre.

**Desfase conocido de Legispan.** Legispan suele ir **~1 día atrasado** respecto a Gaceta Oficial
(puede que aún no liste la(s) gaceta(s) del último día, e incluso alguna edición de días ya
cubiertos). Es conocido y aceptado: trabaja con lo que Legispan lista; **no** cruces con Gaceta
Oficial para "descubrir" gacetas adicionales. Si la semana objetivo incluye hoy/ayer, agrega al
final una nota recordando que la(s) gaceta(s) más reciente(s) podrían aparecer al día siguiente.

## Paso 1 — Enumerar las gacetas de la semana en Legispan

1. Navega a `https://legispan.asamblea.gob.pa/tabloids` (pestaña "Gacetas").
2. La lista carga ~20 gacetas. Cada una es un enlace `a.search-result` con el texto exacto:
   `GACETA {número}[-{edición}] DE {día} de {mes} de {año}` — por ejemplo
   `GACETA 30553-D DE 24 de junio de 2026`. La fecha que importa es esta **fecha de publicación**
   (no la fecha interna de cada norma, que puede ser de semanas antes).
3. **Cargar más con scroll** (infinite scroll: cada scroll abajo carga ~20 gacetas más):
   - `computer` → `action:"scroll"`, `coordinate:[400,300]`, `scroll_direction:"down"`,
     `scroll_amount:10`. Espera 1–2 s a que aparezca/desaparezca el spinner (tres puntos).
   - Repite hasta que la gaceta **más antigua** cargada sea anterior al **lunes** de tu semana
     objetivo (así garantizas tener toda la semana).
   - **No uses loops de JavaScript con `setTimeout`/`await` para scrollear**: congelan la pestaña
     Ionic (el renderer se cuelga y da timeouts). Scrollea con la acción del navegador y lee el
     estado con llamadas `javascript_tool` cortas y **síncronas**.
4. Extrae la lista con una llamada corta:

   ```javascript
   JSON.stringify(Array.from(document.querySelectorAll('a.search-result')).map(x=>x.innerText.trim()))
   ```

5. **Filtra** a las gacetas cuya fecha de publicación cae en tu rango lunes→viernes. Conserva
   **todas las ediciones** de cada día (sin sufijo, -A, -B, -C, …). Ordena por fecha y edición.

## Paso 2 — Leer el índice de cada gaceta en Gaceta Oficial

Gaceta Oficial expone cada gaceta en una URL propia `https://www.gacetaoficial.gob.pa/gaceta/{id}`,
donde `{id}` es un id interno (no derivable del número). Para obtener ese id de forma confiable usa
el **endpoint de catálogo** del sitio (es lo que alimenta el buscador "Buscar por número de
Gaceta"):

### 2a. Mapear número+edición → id (recomendado)

Estando en una pestaña de `https://www.gacetaoficial.gob.pa/`, ejecuta en el navegador:

```javascript
const r = await fetch('https://www.gacetaoficial.gob.pa/ajax/cbx/gacetas?term=3055',
  {headers:{'X-Requested-With':'XMLHttpRequest'}});
const j = await r.json();   // { results: [ {id, text}, ... ] }  más recientes primero
JSON.stringify(j.results.slice(0,40))
```

- `text` viene como `"30551"` o `"30551 A"` (con **espacio** antes de la edición). En Legispan la
  edición va con **guion** (`30551-A`): normaliza (guion ↔ espacio) al emparejar.
- El `term` prácticamente no filtra; el endpoint devuelve el catálogo completo más-reciente-primero.
  Usa como `term` el prefijo de 5 dígitos de la época (ej. `3055`) y quédate con las primeras
  decenas de resultados, que cubren la semana. Construye un mapa `texto → id`.
- Para cada gaceta de tu lista de Legispan, busca su `id` en el mapa. Si una edición de Legispan no
  aparece en el catálogo, anótala como "no disponible aún en Gaceta Oficial" y sigue.

### 2b. Leer y parsear cada índice

Para cada `id`, lee `https://www.gacetaoficial.gob.pa/gaceta/{id}`. Dos opciones:

- **Con `web_fetch`** (lo más limpio): devuelve la "Tabla de Contenido" como tablas Markdown, con
  el número y fecha de la gaceta, los encabezados de entidad, y por cada norma su tipo+número,
  fecha y enlace PDF. Ignora la barra lateral ("Las 5 más recientes", "Base Legal", etc.).
- **Parseo en el navegador** (útil para muchas gacetas a la vez): haz `fetch` same-origin de la
  página y parsea con `DOMParser`. Quédate solo con los `<a>` cuyo href cumpla
  `/storage/gacetas/AAAA/MM/{número}(_EDICIÓN)?/...pdf` (eso descarta los enlaces de "Base Legal"
  del encabezado, que apuntan a otros números). Trata los href con `/ae/` como **avisos y
  edictos** (cuéntalos) y los `GacetaNo_*.pdf` como el PDF completo de la gaceta. La **entidad** es
  el encabezado `h3`–`h6` inmediatamente anterior; el **tipo + número + fecha** está en la primera
  celda de la tabla que contiene el `<a>`; el **título** es el texto del `<a>`.

  > Importante: `javascript_tool` trunca las respuestas largas (~1–2 KB). No intentes devolver el
  > documento completo armado por esa vía. Devuelve los datos **por gaceta** (o por día), o usa
  > `web_fetch` por gaceta, y arma el Markdown final fuera del navegador.

De cada norma extrae: **entidad**, **tipo y número** (Ley N° 534, Decreto Ejecutivo N° 20,
Resolución N° …, Acuerdo Municipal N° 015, Orden General N° …), **fecha de la norma** (puede diferir
de la fecha de la gaceta), **título/sumilla** y **enlace al PDF**.

## Paso 3 — Compilar el resumen (Markdown, en el chat)

Entrega el resultado **en Markdown en la conversación** (no como archivo, salvo que el usuario pida
un documento). Profundidad: **a nivel de título del índice** — usa el título oficial de cada norma
tal cual; no abras los PDFs de cada norma salvo que el usuario lo pida. Cubre **todas** las normas.

Estructura:

```markdown
# Resumen semanal — Gaceta Oficial de Panamá
**Semana:** lunes {dd} al viernes {dd} de {mes} de {año}  ({en curso | anterior})
**Gacetas:** {N} ediciones ({lista de números})
**Total de normas:** {N}  ·  **Avisos y edictos:** {N}

## Destacados de la semana
3–8 viñetas con lo de mayor alcance: leyes de la Asamblea Nacional, decretos ejecutivos y de
gabinete, y resoluciones de entidades nacionales relevantes. Cada viñeta: tipo, número y una frase.

## Detalle por gaceta
### Gaceta {número}{ -edición} — {día} {dd} de {mes} ([PDF completo]({url}))
**{ENTIDAD}**
- **{Tipo} N° {núm}** ({fecha de la norma}) — {título / sumilla} [PDF]({url})
- …
*Avisos y edictos: {N}*

## Fuentes
- Lista de gacetas: https://legispan.asamblea.gob.pa/tabloids
- Contenido: https://www.gacetaoficial.gob.pa/ (páginas /gaceta/{id})
```

Pautas:
- **No inventes ni interpretes de más**: el título oficial ya describe la norma; reprodúcelo o
  acórtalo con fidelidad. No cites artículos ni efectos que no estén en el índice.
- Agrupa por entidad dentro de cada gaceta. Conserva los enlaces a PDF (son la fuente verificable).
- Para semanas grandes (decenas de normas), apóyate en "Destacados" para el panorama rápido arriba,
  pero incluye igualmente el detalle completo.

## Nota legal

Es un resumen informativo basado en los títulos del índice oficial, no asesoría legal. Para el
texto y los efectos exactos de cualquier norma hay que leer el PDF de la Gaceta Oficial.

## Paso 4 — Cerrar los tabs abiertos durante la búsqueda

**Después de entregar el resumen**, cierra todos los tabs que el skill abrió en Chrome.
Esto mantiene el navegador limpio y evita dejar pestañas residuales de Legispan y Gaceta Oficial.

### Procedimiento

1. Llama `tabs_context_mcp` para obtener la lista de tabs abiertos.
2. Filtra los tabs cuya URL contenga alguno de estos dominios:
   - `legispan.asamblea.gob.pa`
   - `gacetaoficial.gob.pa`
3. Pasa sus `tabId` a `tabs_close_mcp` para cerrarlos.

Ejemplo:

```
# Ver tabs abiertos
tabs_context_mcp()

# Cerrar los que correspondan
tabs_close_mcp(tabIds=[<ids de legispan y gacetaoficial>])
```

**Importante:**
- Cierra **solo** tabs de esos dos dominios; no toques lo que el usuario tenía abierto antes.
- Si `tabs_context_mcp` o `tabs_close_mcp` no están disponibles en el momento, menciona
  brevemente al usuario que puede cerrar manualmente las pestañas de Legispan y Gaceta Oficial.
