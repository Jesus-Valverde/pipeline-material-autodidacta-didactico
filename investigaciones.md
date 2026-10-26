# Investigaciones: qué evalué, qué tomé, qué rechacé y por qué

Registro de las evaluaciones hechas al armar el pipeline (octubre 2026). Cada entrada: qué es, veredicto de una línea, y la razón. Precios y límites con la fecha de verificación — cambian cada mes.

## Herramientas de redacción de libros con agentes

| Herramienta | Veredicto | Razón |
|---|---|---|
| [bookwright](https://github.com/adrianmastronardi/bookwright) (MIT) | ✅ **Adoptado** | Pipeline editorial de no-ficción: manifiesto → voz → índice → outline → 3 pasadas por capítulo → evaluación final leyendo el PDF ciego. Artefactos markdown releídos cada sesión = coherencia entre semanas de trabajo |
| [Book Genesis / book-genesis-studio](https://github.com/felipelobomotta-blip/book-genesis-studio) (MIT) | ⚠️ No adoptado, **saqueado** | Excelente para ficción (anti-AI-tells, beta-readers, score por dimensión mínima). Género equivocado para no-ficción didáctica — pero robé dos ideas: las huellas de prosa-IA adaptadas al español y la regla de "la nota es tu dimensión más baja" |
| [Claude-Book](https://github.com/ThomasHoussin/Claude-Book), [story-skills](https://github.com/danjdewhurst/story-skills) | ❌ Rechazados | Multi-agente para novelas / libro vía PRs — ficción |
| TeraBook ($49 "lifetime", oct-2026) | ❌ Rechazada | Fábrica de libros para Amazon KDP (novelas, self-help). Filosofía opuesta: autónoma, sin verificación de fuentes — el riesgo #1 en didáctico es la fabricación, no la velocidad |
| WordWriter, Sudowrite, NovelCrafter | ❌ Rechazadas | Todas optimizan voz/consistencia de personajes — ficción |

## Colecciones de skills científicas/académicas

| Colección | Veredicto | Razón |
|---|---|---|
| [K-Dense scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) — 177 skills, MIT | ⚠️ Cherry-pick de 5 | La mayoría es bio/química/física pesada. Tomé: paper-lookup (18 APIs académicas), liteparse (parseo local de PDFs), scientific-critical-thinking (grading de evidencia), markdown-mermaid-writing (diagramas), citation-management (BibTeX) |
| Skills "académicas" nativas de Kimi | ❌ Rechazadas | Atrapadas en su plataforma; género paper-de-revista (IMRaD), no didáctico |
| open-notebook | ❌ Rechazado | NotebookLM self-hosted — ya pago NotebookLM Pro; otra plataforma que mantener |
| exa-search, parallel-web, research-lookup | ❌ Rechazadas | Requieren API keys o servicios externos de pago; mi stack investiga sin ellas |

## Diseño

| Herramienta | Veredicto | Razón |
|---|---|---|
| [theme-factory](https://github.com/anthropics/skills) (Anthropic, Apache-2.0) | ✅ Adoptada | 10 temas de paleta+tipografía aplicables a docs/slides/reportes + generación de temas al vuelo |
| [visual-design-foundations](https://github.com/wshobson/agents) (MIT) | ✅ Adoptada | La educación de diseño que le falta al agente: escalas tipográficas, grid de 8 puntos, color semántico |
| [frontend-slides](https://github.com/zarazhangrui/frontend-slides) (30.9k★) | Ya la tenía | Decks HTML — la categoría presentaciones ya estaba cubierta |
| Diseño de documentos docx/PDF | ❌ No existe | Ninguna skill en ningún catálogo diseña libros docx/PDF — lo cubre tipografía editorial clásica (Butterick) en el render |
| Typst (min-book ago-2026, Quarto+Typst mar-2026) | 🔜 Futuro | Upgrade del render cuando el libro pase de 100 páginas; hoy el docx basta |

## Herramientas para docentes (evaluadas como complemento del aula)

| Herramienta | Veredicto | Razón |
|---|---|---|
| MagicSchool (free con límites; Plus $8.33/mes anual, oct-2026) | ❌ Rechazada | Buena para docentes SIN agente propio; duplica lo que este pipeline produce (decks, tareas, exámenes, rúbricas) con sesgo K-12. Su privacidad institucional (FERPA/SOC 2) no aplica si la regla es no subir datos de alumnos |
| Perusall (lectura social) | ❌ Rechazada | Dejó de ser gratis jul-2026: $5–25 por alumno o licencia institucional — traslada el costo a los estudiantes |
| Quizizz → ahora "Wayground" (oct-2026) | 🧪 A probar | Único hueco real: quizzing interactivo EN CLASE requiere plataforma estudiante-facing que un agente no puede sustituir. Free existe; límites exactos solo en la app |
| Curipod, Diffit, Khanmigo, Gradescope | ❌ Rechazadas | Trasladan el pipeline de decks propio / K-12 / calificación a escala innecesaria para grupos pequeños |

## Investigación como servicio (SaaS cerrado)

| Herramienta | Veredicto | Razón |
|---|---|---|
| [hanademi](https://hanademi.com/how-it-works) ($9/pieza; 6 por $49, 25 por $199, oct-2026) | ❌ Rechazada, **saqueada una idea** | Convierte una pregunta en un explainer visual o deck de gráficas: lee ~1,000 páginas de ~300 sitios, cada cifra con link a su fuente, fuentes en conflicto mostradas en paralelo, datos débiles marcados, proyecciones etiquetadas. Mismo espíritu que la capa 1, pero cerrado: entregan su formato (no una fuente única editable), sin redacción didáctica, sin papers (gobierno/prensa/filings, no arXiv/SciELO), y $9 por pieza contra los centavos de una corrida propia. **Idea robada**: buscar activamente fuentes que contradigan la premisa — no solo marcar lo disputado cuando aparece |

## Las 5 listas de "mejores herramientas IA" evaluadas

Durante el armado cayeron cinco listas circulando en internet (incluida la de la propia Kimi). Patrón repetido al 90%: recomiendan (a) lo que este pipeline ya hace, en versión más limitada y con mensualidad, o (b) herramientas de otro género (papers de revista, novelas, K-12). Las listas sirvieron de examen de validación — el pipeline las pasó todas.

## Lecciones de método (aplicables a tu propio proceso)

1. **La pregunta filtro**: "¿qué fase de mi pipeline resuelve esto, y qué tengo ya instalado para esa fase?" — mata el 90% de las compras de herramientas.
2. **Verifica precios en la página del vendedor**, con fecha — los roundups de terceros copian cifras viejas.
3. **Los links de los artículos mueren**: el repo real de una herramienta no siempre es el que el artículo menciona (me pasó con Book Genesis — el link del artículo daba 404).
4. **Género primero**: ficción vs no-ficción vs didáctico vs paper son necesidades distintas; la mayoría de las tools de "escribir libros" son de ficción.
5. **Antes de rechazar una cifra, llega al primario**: "no la encontré" no es "no existe" (lección de la corrida de prueba, caso FBI IC3).
