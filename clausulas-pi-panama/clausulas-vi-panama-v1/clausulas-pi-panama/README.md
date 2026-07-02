# clausulas-pi-panama

Skill para [Claude Cowork](https://claude.ai) que revisa cláusulas de propiedad intelectual en contratos bajo el derecho panameño, citando artículos exactos de la Ley 35 de 1996 (reformada por Ley 61 de 2012), el Decreto Ejecutivo 85 de 2017 y la Ley 64 de 2012 sobre Derecho de Autor.  - Version 1.0 - publicado 7 jun 2026.

---

## Qué hace

- Identifica el tipo de PI involucrado en el contrato (marcas, patentes, secretos industriales, software, obras de autor) y aplica la ley panameña correspondiente.
- Verifica la validez formal de cesiones, licencias, titularidades y derechos morales.
- Produce un memo estructurado con hallazgos por severidad (🔴🟠🟡🟢), citas textuales de la ley aplicable y redacción sugerida de reemplazo.
- Funciona para contratos de empleo, consultoría, servicios, licencias, adquisiciones y acuerdos de coexistencia marcaria bajo ley panameña.

## Cómo usar

Una vez instalado el skill en Claude Cowork, escribe `/clausulas-pi-panama` seguido de:

- El texto del contrato (pegado directamente), o
- Una instrucción como "revisa el contrato en esa carpeta", o
- Una pregunta específica: "¿está bien la cláusula de PI?", "¿somos dueños del trabajo?", "¿la cesión es válida en Panamá?"

## Leyes de referencia incluidas

El skill incluye los textos completos de:

| Archivo | Contenido |
|---|---|
| `references/ley35-ley61-texto.md` | Ley 35 de 1996 reformada por Ley 61 de 2012 — PI industrial (marcas, patentes, modelos, secretos industriales) |
| `references/decreto85-2017-texto.md` | Decreto Ejecutivo 85 de 2017 — Reglamento de la Ley 35 |
| `references/ley64-2012-texto.md` | Ley 64 de 2012 — Derecho de Autor y Derechos Conexos (software, obras literarias, artísticas y científicas) |

---

## ⚠️ Avisos importantes

### Este skill no es un sustituto de asesoramiento legal profesional

**El análisis producido por este skill tiene carácter informativo y orientativo únicamente. No constituye asesoramiento legal, no crea una relación abogado-cliente y no puede ser utilizado como opinión jurídica profesional.**

Las salidas de este skill son un punto de partida para la revisión legal, no un dictamen final. Toda decisión sobre contratos que involucren propiedad intelectual debe ser tomada con el apoyo de un abogado panameño habilitado para el ejercicio de la profesión, que pueda evaluar el contexto completo de la operación, los intereses de las partes y la legislación vigente al momento de la consulta.

El autor del skill y Anthropic (operador de Claude) no asumen responsabilidad por decisiones tomadas con base en el análisis generado por este skill.

### Vigencia de la información legal

Las leyes de referencia incluidas corresponden a los textos vigentes al momento de creación del skill. La legislación panameña puede ser modificada. Verifique siempre con las fuentes oficiales (DIGERPI, DNDA, Gaceta Oficial) antes de actuar sobre cualquier análisis producido.

### Limitaciones del modelo de IA

Claude es un modelo de lenguaje. Puede cometer errores en la interpretación de cláusulas contractuales complejas, en la cita de artículos o en la evaluación de riesgos jurídicos. El análisis debe ser revisado por un profesional del derecho antes de ser utilizado.

### Advertencia de Protección de Datos Personales

No suba documentos ni cláusulas con DATOS PERSONALES al utilizar este skill en la IA CLAUDE sin autorización expresa de sus titulares. De no contar con dicha autorización bórrelos o anonímicelos antes.

---

## Licencia y atribuciones

Este skill se distribuye bajo la **Licencia Apache 2.0**.

Fue desarrollado por **Osvaldo Quintero** a partir del skill `ip-legal:ip-clause-review`, parte del plugin [Claude for Legal](https://github.com/anthropics/claude-legal) de Anthropic, distribuido también bajo Licencia Apache 2.0.

```

Obra derivada de ip-legal:ip-clause-review
Copyright Anthropic — distribuido bajo Licencia Apache 2.0

Se concede permiso para usar, copiar, modificar y distribuir este
software y su documentación conforme a los términos de la Licencia
Apache 2.0: http://www.apache.org/licenses/LICENSE-2.0

Este software se distribuye "TAL CUAL", SIN GARANTÍAS NI CONDICIONES
DE NINGÚN TIPO, ya sean expresas o implícitas. Véase la Licencia
para el texto que rige los permisos y limitaciones aplicables.
```

El texto completo de la Licencia Apache 2.0 se encuentra en el archivo [`LICENSE`](./LICENSE).

---

## Contribuciones

Las contribuciones son bienvenidas. Si detectas un artículo mal citado, una disposición desactualizada o tienes sugerencias para mejorar la cobertura del skill, abre un issue o un pull request.
