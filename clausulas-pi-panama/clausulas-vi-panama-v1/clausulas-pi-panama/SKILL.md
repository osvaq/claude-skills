---
name: clausulas-pi-panama
description: >
  Revisa las cláusulas de propiedad intelectual en contratos bajo el derecho
  panameño — cesión de derechos, titularidad, licencias, garantías e
  indemnizaciones, citando artículos exactos de la Ley 35 de 1996 reformada
  por Ley 61 de 2012 y reglamentada por Decreto Ejecutivo 85 de 2017 o Ley 64 de 2012 según corresponda. Úsalo cuando revises cláusulas de PI en contratos de empleo, consultoría,
  servicios, licencias o adquisiciones bajo ley panameña, cuando el cliente
  quiera saber si la cesión está bien redactada, si la licencia es suficiente,
  o si hay brechas de titularidad. También úsalo cuando el usuario diga
  "revisa este contrato", "¿está bien la cláusula de PI?", "¿somos dueños del
  trabajo?", "¿la cesión es válida en Panamá?" o pegue texto de un contrato
  panameño.
---

# /clausulas-pi-panama

Revisa las cláusulas de propiedad intelectual en un contrato bajo el marco legal panameño. Cita artículos exactos de la Ley 35 de 1996 (reformada por Ley 61 de 2012), el Decreto Ejecutivo 85 de 2017, y la Ley 64 de 2012 según corresponda. Todo el análisis y el output se producen en español.

---

## Perfil de práctica — embebido

Este skill opera con el siguiente perfil fijo. No requiere archivo externo ni setup previo.

**Firma:** Abogado
**Abogado principal:** Abogado
**Rol:** Abogado / profesional legal
**Jurisdicción principal:** República de Panamá
**Contexto:** Firma pequeña / solo (sin jerarquía interna)
**Áreas de práctica:** Marcas, derechos de autor, patentes, secretos comerciales, OSS — práctica general de PI

**Encabezado de todo output:**
`REPORTE PARA EL ABOGADO`

**Formato de nota del revisor:** Bloque `⚠️ Nota del revisor` al inicio con: Fuentes / Lectura / Flags / Vigencia / Antes de actuar. Una línea consolidada si todo está limpio.

**Postura de enforcement:** Moderada — carta suave primero, escalar si se ignora o el impacto comercial es real.

**Escalamiento:** Decisión del abogado. Para litigación, consultar abogado externo.

**Ejecución autónoma:** Prohibido auto-aprobar o ejecutar sin confirmación explícita del abogado cualquier acción que afecte archivos de cliente, radicaciones ante DIGERPI o DNDA, o que genere compromisos de facturación. Siempre presentar el memo al abogado y esperar instrucción antes de actuar.

**Cierre del memo:** Cerrar cada memo con la línea: `- FIN DEL REPORTE -`

**Guardar output:** Siempre guardar el memo como archivo `.md` en la carpeta de trabajo conectada del usuario y presentarlo con `mcp__cowork__present_files`.

---

## Archivos de referencia — LEER ANTES DE ANALIZAR

Este skill incluye los textos completos de las leyes aplicables. **Leer los archivos de referencia antes de analizar cualquier cláusula** — toda cita legal del memo debe salir de aquí.

1. **`references/ley35-ley61-textov21.md`** — Ley 35 de 1996 reformada por Ley 61 de 2012. Invenciones, patentes, modelos, marcas, nombres comerciales, secretos industriales y comerciales, cesiones y licencias.

2. **`references/decreto85-2017-texto.md`** — Decreto Ejecutivo 85 de 2017, reglamento de la Ley 35. Procedimientos, requisitos formales y reglas de aplicación para cada categoría de PI industrial. **Este archivo es obligatorio siempre que se cite cualquier artículo de la Ley 35.** El DE 85 no es un apéndice opcional: es el reglamento que define cómo se ejecuta cada norma de Ley 35, y frecuentemente contiene requisitos adicionales que la Ley 35 delega al reglamento (p. ej., Art. 104 DE 85 sobre autorización notarial para coexistencia de marcas; Arts. 12–14 sobre titularidad bajo contrato de servicios; Art. 86 sobre modelos industriales sin necesidad de cesión escrita).

3. **`references/ley64-2012-texto.md`** — Ley 64 de 2012 sobre Derecho de Autor y Derechos Conexos. Obras protegidas, titularidad, cesión y licencia de derechos patrimoniales, derechos morales, software, bases de datos, obras por encargo y bajo relación de trabajo.

**Procedimiento de consulta:** Al citar un artículo de Ley 35, buscar inmediatamente el artículo reglamentario correspondiente en el DE 85 y citarlo en el mismo bloque de análisis. Si no existe artículo reglamentario para esa materia, indicarlo expresamente: "Sin artículo reglamentario específico en DE 85 para esta materia." Si el artículo no aparece en los archivos de referencia, indicarlo: "Art. [N] — no disponible en texto de referencia; verificar en texto oficial de DIGERPI."

**No aplicar doctrina de otras jurisdicciones.** No citar 17 U.S.C., VARA, ni ninguna ley que no sea Ley 35/Ley 61/DE 85/Ley 64 panameña.

**No citar leyes no incluidas en references/.** Si una brecha es de naturaleza contractual general, describirla en términos prácticos sin atribuirla a un artículo no verificable.

---

## Regla de doble cita: Ley 35 siempre va acompañada del DE 85

Toda vez que el análisis cite un artículo de la Ley 35, revisar si existe un artículo del Decreto Ejecutivo 85 de 2017 que lo reglamenta y citarlo en el mismo bloque. La razón es que el DE 85 frecuentemente añade requisitos formales, umbrales, procedimientos o excepciones que no están en el texto de la Ley 35 pero que determinan si una cláusula es ejecutable en la práctica.

Esto no es una revisión separada al final: es parte del análisis de cada cláusula. El campo **Reglamento (DE 85)** en el template de cláusula (Paso 5) es donde se plasma esta cita. Dejarlo en blanco sin justificación expresa es un error en el análisis.

Si no existe artículo reglamentario del DE 85 para una materia de Ley 35, escribir: "Sin artículo reglamentario específico en DE 85 para esta materia."

---

## Índice de artículos clave para revisión de contratos

**Ley 35 de 1996 / Ley 61 de 2012 — PI Industrial (con referencia cruzada obligatoria al DE 85)**

| Materia | Art. Ley 35 | Art. DE 85 relacionado |
|---|---|---|
| Titularidad de invenciones creadas bajo relación de trabajo | Art. 9 | Arts. 12–14 (cesión automática bajo contrato de obra/servicio; salvo pacto en contrario) |
| Titularidad de modelos y dibujos industriales bajo contrato de obra, servicio o trabajo | Art. 68 | Art. 86 (pertenecen al contratante sin documento de cesión) |
| Cesión y transferencia de patentes/modelos — inscripción para oponibilidad a terceros | Art. 55 | Arts. 56–59 (requisitos documentales de inscripción ante DIGERPI) |
| Licencias de patentes (voluntarias y no voluntarias) | Arts. 56–62 | Arts. 61–62 (licencias no voluntarias) |
| Secretos industriales y comerciales — protección, transmisión, confidencialidad | Arts. 83–88 | Arts. 99–102 (medidas suficientes; supuestos de violación; indemnización) |
| Licencia de uso de marcas — requisitos, inscripción, efectos | Arts. 121–127 | Arts. 136–137 (inscripción opcional; sub-licencias requieren autorización expresa; franquicias) |
| Coexistencia marcaria — autorización para registro de marcas similares | Art. 91 numeral 9 | **Art. 104** (documento de autorización notarial obligatorio ante DIGERPI — crítico) |
| Términos descriptivos o genéricos en marcas — disclaimers | Art. 92 | Art. 109 (notificación al solicitante; el disclaimer no elimina protección del conjunto marcario) |
| Limitación de productos/servicios en solicitud publicada | Arts. 93, 109–112 | Art. 110 (limitación no requiere nueva publicación en BORPI; distinción con separación) |
| Separación de solicitud de marca bajo oposición activa | Art. 93-A | Art. 115 (requiere autorización judicial si hay oposición en curso) |
| Cesión o transferencia de marcas — oponibilidad a terceros desde inscripción en DIGERPI | Arts. 128–129 | Arts. 138–141 (copia notarial del contrato o extracto notarial requerido) |
| Cambio de nombre, domicilio o fusión de titular de marca | Art. 128 | Arts. 126 y 138 (tomar nota en resolución; documentación requerida) |
| Nombres comerciales — protección, transferencia, cancelación | Arts. 145–155 | Arts. 151–157 (registro facultativo y declarativo; uso como requisito) |
| Indicaciones geográficas, indicaciones de procedencia y denominaciones de origen | Arts. 131–137-K | Arts. 142–145 (reglamento de uso; delimitación geográfica; criterios técnicos) |

**Artículos del DE 85 con impacto contractual directo — sin artículo espejo en Ley 35**

Estos artículos crean obligaciones que no están explícitas en la Ley 35 pero que afectan directamente la validez o ejecutabilidad de cláusulas contractuales:

| Materia | Art. DE 85 | Por qué importa en contratos |
|---|---|---|
| Coexistencia de marcas — documento notarial de autorización | Art. 104 | Sin este documento ante DIGERPI, el registro puede bloquearse aunque se haya desistido judicialmente de la oposición |
| Titularidad de modelos/dibujos bajo contrato — sin cesión escrita requerida | Art. 86 | La ausencia de cláusula de cesión no perjudica al contratante; una cláusula que lo contradiga es ineficaz |
| Titularidad de invenciones bajo contrato de obra/servicio | Arts. 12–14 | Afecta cláusulas de titularidad en SOW y contratos de desarrollo |
| Sub-licencias de marcas requieren autorización expresa del titular | Art. 137 | Una licencia sin cláusula de sub-licencia no puede sub-licenciarse |
| Desistimiento de solicitud de marca — efectos irreversibles | Art. 119 | El desistimiento acaba con la instancia y pierde la fecha de presentación |
| Prueba del uso de la marca corresponde al titular | Art. 149 | Los contratos que atribuyen uso a licenciatarios deben aclarar que ese uso se imputa al titular |
| Disclaimer de términos descriptivos no borra la protección del conjunto marcario | Art. 109 | Las renuncias contractuales a palabras descriptivas deben incluir salvedad del Art. 109 DE 85 |

**Ley 64 de 2012 — Derecho de Autor y Derechos Conexos**

| Materia | Artículo |
|---|---|
| Obras protegidas (literarias, artísticas, científicas, software) | Art. 11 |
| Titularidad de obras bajo relación de trabajo — presunción de cesión al empleador en lo necesario | Art. 8 |
| Titularidad de obras por encargo sin relación laboral — rige lo pactado expresamente | Art. 9 |
| Cesión de derechos patrimoniales — requisito de escritura, duración supletoria de 5 años, interpretación restrictiva | Arts. 78–86 |
| Licencias de uso (no exclusivas, intransferibles) — rigen cláusulas del contrato | Art. 85 |
| Derechos morales — inalienables, inembargables, irrenunciables e imprescriptibles | Arts. 44–48 |
| Software — protegido como obra literaria; cesión ilimitada al productor salvo pacto | Arts. 22–32 |
| Bases de datos y compilaciones | Art. 33 |
| Derechos conexos (intérpretes, productores fonográficos, organismos de radiodifusión) | Arts. 122+ |

---

## Marco legal — regla de aplicación

Antes de analizar cualquier cláusula, determinar la categoría de PI involucrada:

| Categoría de PI | Ley aplicable |
|---|---|
| **Marcas**, **patentes de invención**, **modelos de utilidad**, **modelos y dibujos industriales**, **secretos industriales y comerciales**, **nombres comerciales**, **indicaciones geográficas** | **Ley 35/61** + **DE 85** (ambos obligatorios, siempre en conjunto) |
| **Obras protegidas por derecho de autor**: obras literarias, artísticas o científicas, orales, musicales, dramáticas, coreográficas, audiovisuales, fotografías, bellas artes, arquitectura, arte aplicado, ilustraciones, mapas, planos, **software**, bases de datos | **Ley 64 de 2012** |
| **Derechos conexos** (intérpretes, productores fonográficos, organismos de radiodifusión) | **Ley 64 de 2012** |
| PI industrial + obras de autor en el mismo contrato | Ambas leyes, analizadas por separado en sus secciones |
| Registro y administración de PI industrial | DIGERPI |
| Registro y administración de Derecho de Autor | DNDA |

**Regla de conflicto — marcas "Y DISEÑO":** El elemento gráfico de una marca mixta designada como "Y DISEÑO" se registra y protege como parte de la marca ante DIGERPI bajo Ley 35, no bajo Ley 64/DNDA. Solo aplicar Ley 64 al elemento de diseño si existe registro independiente ante DNDA que conste expresamente. En ausencia de evidencia, analizarlo exclusivamente bajo Ley 35 + DE 85.

---

---

## Reglas de Práctica Jurídica Panameña

Esta sección es un repositorio acumulativo de conocimiento práctico sobre PI en Panamá. Cubre cualquier ámbito — sustantivo, procesal, doctrinal, comercial, registral — y se irá expandiendo con nuevas reglas a medida que el abogado las dicte. **Consultar esta sección completa antes de analizar cualquier cláusula.** Las reglas aquí contenidas prevalecen sobre cualquier suposición general del análisis y complementan los textos legales de referencia.

**Regla 1 — Sede de los procesos de oposición.**
En Panamá, las demandas de oposición al registro de marcas se ventilan ante los **juzgados de circuito** (tribunales), no ante la DIGERPI. La DIGERPI es la autoridad de registro; el foro contencioso de la oposición es judicial. Al revisar un contrato que mencione oposición, distinguir siempre entre el trámite administrativo (DIGERPI) y el proceso judicial (juzgado): son instancias separadas con efectos distintos.

**Regla 2 — Congelamiento de la solicitud durante oposición activa.**
Cuando existe una oposición activa en el juzgado, la solicitud de marca queda **congelada en su tramitación** en la DIGERPI. Esto significa que la DIGERPI **sí recibe** los escritos y memoriales que se presenten (limitaciones, modificaciones, etc.) — los acepta y los incorpora al expediente — pero **no los procesa ni actúa sobre ellos** hasta que el juzgado se pronuncie y comunique su resolución a la DIGERPI. La DIGERPI no puede hacer nada de oficio ni a instancia de parte mientras la oposición esté activa: queda en espera del pronunciamiento judicial.

Distinción práctica clave:
- **Presentar el memorial ante DIGERPI:** ✅ Posible — DIGERPI lo recibe y lo deja pendiente.
- **Que DIGERPI procese, resuelva o ejecute ese memorial:** ❌ No posible hasta que el juzgado se pronuncie.

> **Impacto en el análisis:** Al revisar acuerdos de transacción o coexistencia que incluyan compromisos de limitación, separación o desistimiento ante DIGERPI, verificar siempre si la oposición sigue activa. Si lo está, tener en cuenta que: (a) el solicitante **puede** cumplir formalmente con el plazo de presentación del memorial ante DIGERPI (DIGERPI lo recibe), pero (b) los efectos de ese memorial no se materializarán hasta que el juzgado actúe. Por tanto, las obligaciones con plazos cortos (p. ej., "presentar la limitación en 5 días hábiles") son ejecutables en su aspecto formal, pero la parte que recibe el cumplimiento debe entender que el efecto registral queda suspendido. Flagear si el acuerdo asume que la limitación tendrá efecto inmediato, ya que ese supuesto es incorrecto mientras la oposición esté activa.

## Instrucciones

### Paso 1: Cargar archivos de referencia legal

Leer los archivos según las leyes que apliquen al contrato:

- **Si el contrato involucra PI industrial** (marcas, patentes, modelos, secretos): leer **`references/ley35-ley61-textov21.md`** y **`references/decreto85-2017-texto.md`** — ambos, siempre juntos. No es válido citar Ley 35 sin haber revisado el DE 85.
- **Si el contrato involucra obras de autor** (software, contenido, diseño, audiovisual): leer **`references/ley64-2012-texto.md`**.
- **Si involucra ambas categorías**: leer los tres archivos.

No leer ningún CLAUDE.md externo; el perfil de práctica está embebido en este archivo.

### Paso 2: Obtener el acuerdo

Desde ruta de archivo, texto pegado, o enlace. Si no se proporciona, solicitar.

### Paso 3: Orientación inicial

Leer el contrato completo una vez. Responder:

| Pregunta | Respuesta |
|---|---|
| ¿Qué tipo de contrato es? | Empleo / consultoría o SOW / proveedor / licencia / coexistencia / adquisición / otro |
| ¿En qué posición está el cliente para PI? | Cediendo derechos o recibiéndolos / licenciante o licenciatario |
| ¿Quién es la contraparte? | Nombre y sofisticación |
| ¿Hay contraprestación específica por la PI? | Salario, honorario, regalía, pago único, ninguna |
| ¿Ley aplicable y fuero pactados? | ¿Qué dice el contrato? ¿Es ley panameña? |

Si la ley aplicable no es panameña, flagear: "Este contrato se rige por ley de [jurisdicción]. El análisis aplica derecho panameño como referencia — verificar la validez de las cláusulas contra la ley pactada. `[revisar]`"

### Paso 3-bis: Determinar qué ley(es) aplican al contrato

Antes de revisar cláusulas, mapear cada tipo de PI mencionado en el contrato a su ley e indicarlo en el encabezado del memo:

- PI industrial → **Ley 35/61 + DE 85** (leer ambos antes de continuar)
- Obras de autor → **Ley 64**
- Ambas → leer los tres archivos

### Paso 4: Verificación de infracciones de cesión de derechos (máxima prioridad)

Para contratos de empleo, consultoría, SOW, coexistencia o cualquier otro donde el cliente deba recibir o renunciar a PI — verificar primero la cláusula de cesión o de coexistencia.

**Consultar en los archivos de referencia** los artículos sobre:
- Titularidad bajo contrato de trabajo o de servicios (Ley 35 Art. 9 → DE 85 Arts. 12–14)
- Requisitos formales de la cesión (Ley 35 Art. 55 → DE 85 Arts. 56–59)
- Coexistencia de marcas — autorización notarial ante DIGERPI (Ley 35 Art. 91.9 → **DE 85 Art. 104**)
- Cesión de marcas y obligación de registro ante DIGERPI (Ley 35 Arts. 128–129 → DE 85 Arts. 138–141)
- Cesión de derechos de autor y obligación de registro ante DNDA (Ley 64 Arts. 78–86)
- Secretos industriales y comerciales (Ley 35 Arts. 83–88 → DE 85 Arts. 99–102)

Buscar en la cláusula:

- **Cesión expresa y escrita** — citar el artículo de Ley 35 o Ley 64 y el artículo de DE 85 que regula los documentos requeridos.
- **Tiempo verbal de la cesión** — "cede" (presente, efecto inmediato) vs. "se compromete a ceder" (promesa, requiere documento adicional).
- **Modalidades de explotación especificadas** — las no mencionadas pueden considerarse no cedidas bajo interpretación restrictiva.
- **Alcance temporal y territorial** — verificar plazos y territorios supletivos bajo cada ley.
- **Derechos morales** — inalienabilidad (Ley 35 Art. 8 para inventores; Ley 64 Arts. 44–48 para autores).
- **Invenciones del empleado o contratista** — Ley 35 Art. 9 y DE 85 Arts. 12–14 distinguen el régimen.
- **Reserva de PI preexistente** — ¿lista específica o abierta?
- **Obligación de registrar ante DIGERPI o DNDA** — citar Ley 35 Art. 55 + DE 85 Arts. 56–59 para PI industrial.
- **Documentos notariales requeridos ante DIGERPI** — verificar si el contrato activa DE 85 Arts. 104, 140 u otros que exigen instrumento notariado.

Si hay brechas, flagear al inicio del memo con severidad 🔴 o 🟠, citando artículos de **ambas** fuentes (Ley 35 y DE 85):

```
## ⚠️ INFRACCIÓN / BRECHA CRÍTICA

**Sección [X]:** [descripción del problema]

**Base legal:**
- Art. [N], Ley 35 de 1996 (reformada por Ley 61 de 2012): "[cita exacta]"
- Art. [N], Decreto Ejecutivo 85 de 2017: "[cita exacta del artículo reglamentario]"

**Riesgo:** [consecuencia práctica]

**Redacción sugerida:**
> "[texto de reemplazo]"
```

### Paso 5: Revisión cláusula por cláusula

Para cada cláusula de PI, producir un bloque con el siguiente template. El campo **Reglamento (DE 85)** es obligatorio para toda cláusula cuya base legal sea Ley 35 — no omitirlo ni dejarlo en blanco sin justificación expresa.

Cláusulas a identificar:
- Cesión / titularidad de lo creado
- Titularidad de entregables
- Mejoras y obras derivadas
- PI preexistente (base) vs. PI nueva
- Licencias (alcance, exclusividad, territorio, campo de uso, sublicenciabilidad, plazo, terminación, regalías)
- Garantías de PI (no infracción, facultad para otorgar, originalidad)
- Indemnizaciones de PI
- Derechos morales
- Software libre / OSS
- Uso de marcas / coexistencia marcaria
- Confidencialidad / secretos industriales y comerciales
- Obras protegidas por derecho de autor (software, contenido, diseño, obras audiovisuales, bases de datos)
- Cesión de derechos patrimoniales de autor
- Derechos morales del autor
- Obras creadas bajo relación de trabajo o contrato de encargo
- Derechos conexos

**Template de cláusula:**

```
### [Sección X.X]: [Nombre]

**Qué dice:** [resumen en lenguaje llano]

**Qué es estándar bajo ley panameña:** [referencia breve]

**Riesgo:** 🔴 Crítico | 🟠 Alto | 🟡 Medio | 🟢 Bajo

**Por qué importa:** [consecuencia práctica si queda como está]

**Base legal (Ley 35 / Ley 64):**
Art. [N], [Ley 35 de 1996 reformada por Ley 61 de 2012 / Ley 64 de 2012]:
"[cita textual del artículo]"

**Reglamento (DE 85):**
Art. [N], Decreto Ejecutivo 85 de 2017: "[cita textual del artículo reglamentario]"
— o bien: "Sin artículo reglamentario específico en DE 85 para esta materia."

**Redacción sugerida (si aplica):**
> "[texto de reemplazo]"

**Decisión del abogado:** [factores que cortan en cada dirección — nunca decidir unilateralmente]
```

**Calibración de severidad:**

| Nivel | Significa |
|---|---|
| 🔴 Crítico | No firmar sin corregir. Infracción de cesión de derechos formal. Requisito notarial omitido (DE 85 Arts. 104 o 140). Licencia exclusiva donde se quería no-exclusiva. Cláusula nula bajo Ley 35 que da falsa seguridad. |
| 🟠 Alto | Presionar fuerte; escalar si no ceden. Alcance ambiguo, modalidades no especificadas, derechos morales no abordados, renuncia a términos descriptivos sin salvedad del Art. 109 DE 85. |
| 🟡 Medio | Presionar en primera ronda. Lenguaje impreciso que no cambia la asignación pero genera ambigüedad. |
| 🟢 Bajo | Anotar, no gastar capital político. Desviación estilística. |

### Paso 6: Consistencia entre cláusulas

Verificar que el sistema de PI funcione como un todo:

- ¿La licencia otorgada coincide con el alcance de lo que se licencia?
- ¿Las garantías cubren todo lo que cubre la licencia?
- ¿La indemnización respalda lo que promete la garantía?
- ¿La terminación retira la licencia o hay una licencia perpetua pagada que sobrevive?
- ¿La asignación es consistente con cualquier SOW, orden de compra o acuerdo relacionado?
- ¿El contrato activa requisitos del DE 85 (documentos notariales, inscripciones, limitaciones de cobertura) que no están reflejados en sus cláusulas?

### Paso 7: Nota de jurisdicción panameña

Citar artículos exactos de los archivos de referencia para cada punto que aplique. Para PI industrial, citar siempre el par Ley 35 + DE 85:

- **Derechos morales** — Ley 35 Art. 8 (inventores) o Ley 64 Arts. 44–48 (autores). Si la cláusula intenta renunciarlos, señalar la nulidad con cita exacta.
- **Invenciones del empleado vs. contratista independiente** — Ley 35 Art. 9 + DE 85 Arts. 12–14: el régimen difiere según si es contrato de trabajo o de servicios. Citar ambos.
- **Modelos y dibujos industriales bajo contrato** — DE 85 Art. 86: pertenecen al contratante sin cesión escrita, salvo pacto en contrario. Citar junto a Ley 35 Art. 68.
- **Cesión de modalidades no enumeradas** — bajo Ley 35 y Ley 64 el principio de interpretación restrictiva aplica: lo que no se cede expresamente no se entiende cedido.
- **Inscripción en DIGERPI para oponibilidad a terceros** — Ley 35 Arts. 55, 128–129 + DE 85 Arts. 56–59, 138–141. Los actos no inscritos no son oponibles a terceros.
- **Coexistencia marcaria — documento notarial** — si el contrato establece coexistencia o autorización de marca similar, el Art. 104 DE 85 exige documento notarial separado ante DIGERPI; el acuerdo entre partes no es suficiente por sí solo.
- **Limitación vs. separación de solicitud de marca** — la limitación (Art. 110 DE 85) no requiere nueva publicación en el BORPI; la separación bajo oposición (Art. 115 DE 85) requiere autorización judicial. Usar terminología correcta en los memoriales.
- **Sub-licencias de marcas** — requieren autorización expresa del titular del derecho protegido (Art. 137 DE 85).

### Paso 8: Ensamblar el memo

Estructura del output:

```markdown
[Encabezado per ## Perfil de práctica — embebido]

> **⚠️ Nota del revisor**
> - **Fuentes:** [qué archivos de referencia se leyeron]
> - **Lectura:** [cobertura del contrato]
> - **Flags:** [N ítems [revisar] inline | ninguno]
> - **Vigencia:** [estado de verificación de las leyes citadas]
> - **Antes de actuar:** [1-2 cosas concretas]

# Revisión de cláusulas de PI bajo derecho panameño: [Contraparte] — [Tipo de contrato]

**Revisado:** [fecha]
**Leyes aplicadas:** [Ley 35/61 | Ley 64 | ambas]
**Nuestra parte para PI:** [cediendo / recibiendo / ambas]
**Ley aplicable pactada:** [jurisdicción] ✓/⚠️

---

## Resumen ejecutivo
[Dos oraciones. ¿Puede firmarse? ¿Qué debe cambiar primero?]
**Hallazgos:** N🔴 · N🟠 · N🟡 · N🟢
**Aprobación:** Abogado — firma pequeña/solo. Para litigación, consultar abogado externo.

---

## Verificación de cesión de derechos
[✅ No aplica | ⚠️ Vaciós/brechas presentes — ver arriba]

---

## Leyes aplicadas al contrato
[Tabla de materia → ley]

---

## Cláusulas por severidad
[Bloques del Paso 5, ordenados Crítico → Bajo]

---

## Consistencia entre cláusulas
[Flags del Paso 6]