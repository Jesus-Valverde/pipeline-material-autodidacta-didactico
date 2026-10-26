# Comparación — prueba del pipeline del taller (25-oct-2026)

**Pregunta de la prueba:** ¿el pipeline del taller (deep-research → redaccion-didactica), corrido desde cero sobre el mismo outline, produce material al nivel del que se hizo a mano para la conferencia (9-oct-2026)?

**Diseño:** variable controlada = `tema-outline.yaml` (los mismos 12 items). Corrida semi-ciega: no se leyó `investigacion.md`, `guion.md` ni `results/` originales hasta esta etapa. **Caveat de contaminación:** ya conocía por memoria los 5 hallazgos del fact-check original (teléfono 75 años, WAU vs MAU, DNR viejo, Peng vs METR, formas del validador). La prueba no mide un cerebro fresco; mide si el pipeline produce sistemáticamente lo que la corrida manual produjo, y dónde falla.

---

## 1. Investigación: cobertura contra los 24 datos originales

| Corrida nueva (30 datos) vs original (24) | Resultado |
|---|---|
| Redescubiertos completos (7) | 100M/2meses; ChatGPT 1.2B WAU; Gemini 1B MAU; meme teléfono ❌; Schwab cita; DNR 62%; Arup |
| Redescubiertos y mejorados (2) | FDA (1,600+ a sep-2026 vs "1,000+" a ene-2025); Peng vs METR (con IC, nº tareas, arXiv, actualización METR feb-2026) |
| Parciales (4) | Curvas OWID (mismo fuente, umbral distinto: 25% vs 50%); Tailandia (caso sí, números 91.4%/76%/7,651 no); McKinney (FP/FN sí, muestras y "12% de carga" no); AlphaFold (Nobel sí, "2M investigadores/190 países" no) |
| Perdidos (9) | Internet global mitad en 2019; Galaxy AI 400M dispositivos; AI Overviews 2,500M; métricas de creatividad (130M/700M imágenes, Veo 230M, Suno); Copilot 20M/46% código; Maps DeepMind ETA; Gmail 10% en 2016; PNAS caras 48.2% (el dato más fuerte del bloque "elegir u obedecer"); T&C/primogénito/Facebook |
| En conflicto, adjudicados (2) | FBI IC3 $893M; Translate billón de palabras/mes — ver §2 |

**Cobertura:** 13/24 redescubiertos completos o mejorados (54%); 17/24 contando parciales (71%).

**Aportaciones de la corrida nueva que el original no tiene:** Apple×Gemini y Siri AI (jun-2026); descontinuación de Sora (26-abr-2026) como lección de pico viral ≠ adopción; detalle del DevDay (Sol, agentes always-on); FDA fresco con cohorte 2025; límites del IC (+2%..+39%) y alcance de METR; extras del DNR (confianza 37%, 20% en respuestas de IA, 39% de evasión, >75% en Nigeria/Kenia); Pew 66% clonación de voz + petición FTC; caso de voz UK €220k (2019); Gerlich 2025 (descarga cognitiva); trazas de origen alternativas del meme (BI→DOJ→OCDE, complementarias a la de WSJ→Morgan Stanley); umbrales alternativos de adopción (25%/80%).

## 2. Los dos conflictos, adjudicados contra fuente primaria

Ambos los **ganó el original**, y ambos son la misma modalidad de fallo de mi corrida: la búsqueda general devolvió agregadores o cifras viejas y no llegó al primario.

- **FBI IC3 ~$893M en quejas con IA.** Mi corrida lo rechazó como "re-atribución de categorías que el FBI no reporta". El [reporte anual IC3 2025](https://www.ic3.gov/AnnualReport/Reports/2025_IC3Report.pdf) (publicado abr-2026) sí estrenó la categoría: 22,364 quejas, $893M en pérdidas ajustadas, con [comunicado del FBI](https://www.fbi.gov/news/press-releases/cryptocurrency-and-ai-scams-bilk-americans-of-billions). **Falso negativo de mi fact-check.** Lección: rechazar una cifra también exige llegar al primario; "no la encontré" no es "no existe". El rechazo de los agregadores (+1,210%, +442%, "1 de 10") sigue en pie.
- **Google Translate.** Yo di por válida la cifra "100B palabras/día" (~2016) y la presenté como piso por "no haber cifra fresca". El original tenía razón: Google publicó cifras oficiales en el 20 aniversario (abr-2026): 1B usuarios/mes, ~1 billón (10¹²) de palabras/mes, 250+ idiomas. Además quedó al descubierto una **inconsistencia interna de Google**: 100B/día en 2016 implica ~3×10¹²/mes, incompatible con el billón oficial de 2026 — la cifra de 2016 era PR con otra métrica. Lección: antes de declarar "cifra oficial vieja", buscar el comunicado de aniversario/earnings.

Ambas correcciones ya están aplicadas en `investigacion.md`, `results/*.json` y `draft.md` de esta corrida.

## 3. Higiene de medición: dos chuletas

Las dos corridas produjeron una chuleta de trampas (9 y 9). **Compartidas:** WAU vs MAU, fechas convencionales del WEF, auto-reportadas sin auditoría, picos de lanzamiento ≠ tasas, pérdidas reportadas ≠ reales. **Solo el original:** billón≠trillion (la mía la incorporó en copyedit al corregir Translate), "puntos porcentuales ≠ porcentajes" (mi `investigacion.md` dice "9.4%" sin precisar puntos — defecto real de mi corrida), "presente en ≠ usado por", "en archivos donde está activo" (Copilot). **Solo la mía:** anunciado ≠ disponible, pico viral ≠ adopción (muerte de Sora), retrospectivo ≠ prospectivo, correlación ≠ causalidad, agregadores sin metodología, y "cifra oficial vieja → busca el comunicado de aniversario" (nacida del propio error de esta corrida).

Balance: la del original protege mejor contra errores de *número*; la mía contra errores de *lectura*. El pipeline reproduce la disciplina, no idénticamente la misma lista.

## 4. Frescura (corrida al 23-oct vs 8-oct)

Nueva fresca: Sora discontinuada (abr), FDA 1,600+ (sep), Apple/Siri (jun), extras DNR 2026, detalle DevDay. Vieja fresca que la mía no levantó: Suno 2M/$300M (2-oct-2026, la más fresca de todas), IC3 2025 (abr), Translate 20 aniversario (abr), AI Overviews 2.5B (may), Galaxy AI 400M (2025). **La corrida nueva no ganó el marco de frescura por defecto**: traer "lo más nuevo" dependió de que las queries acertaran al comunicado; dos veces no acertaron.

## 5. Redacción: guion contra guion

**Datos duros:** original 4,740 palabras ≈ 39.5 min, 26 cues, tiempos por sección, ancla repetida 3× con cierre participativo ("díganla conmigo"). Nueva: 4,493 ≈ 37.4 min, 24 cues, ancla 3× (apertura/movimiento final/cierre), aparato didáctico explícito (objetivos, puntos clave, preguntas, glosario) y bitácora de las 4 pasadas. Ambas en la ventana de duración.

**Lo que la oratoria del original hace y la nueva no:**
1. **Anécdota propia del ponente** (SLIDE 15: su oficio, sus alumnos, "la IA no reemplaza el oficio — reemplaza el aburrimiento del oficio"). La nueva no tiene historia personal en ningún punto.
2. **Dispositivo participativo**: la frase ancla se dice 3× y la tercera la dice el público. La nueva repite el ancla pero no convierte al público en coautor.
3. **El bloque humano** ("la semana de tus papás" vs la tuya): narración sensorial, acumulación rítmica, nostalgia. La nueva compara con datos, no con escenas.
4. **Registro con variación**: el original alterna análisis con calor mexicano coloquial ("la piel chinita", "Dios los agarre confesados", "el compadre"). La nueva es más uniforme, más clase que plática.
5. **Criterios de bolsillo accionables**: "buena herramienta es la que te devuelve tiempo y decisión"; "la urgencia es la herramienta del estafador"; "enseña a los que tienes al lado". La nueva da tres ideas pero menos manuales.

**Lo que la nueva hace mejor:**
1. **Trazabilidad completa dato→fuente→solidez→guion** (I-xx visibles; bitácora de pasadas; los ❌ citados como desmentidos y los ⚠️ con su caveat *en voz*).
2. **Didáctica más explícita**: jerga expandida en el momento (WAU/MAU, retrospectivo, plegado de proteínas), una analogía por concepto y retirada, aparato didáctico reutilizable para el Q&A.
3. **Estructura más limpia para editar**: sin tiempos fijos, secciones autocontenidas.

**Coincidencias independientes** (señal de que el pipeline sí lleva el ADN del taller): ambas abren desmontando el meme con autocrítica del ponente ("ni el ponente se salva" / "yo tengo que dar el ejemplo"); ambas usan la enumeración de usos invisibles de la mañana; ambas dedican su bloque central de productividad al contraste Peng/METR con la percepción sesgada como remate; ambas cierran devolviendo la tesis.

**Veredicto de redacción:** la nueva pasa como guion didáctico (didáctica 9, datos 9) y flojea como oratoria (calor/participación 6). Por la regla de la dimensión más baja, **la redacción del pipeline, sola, no sustituye al guion original**: requiere el paso humano de inyectar anécdota propia y dispositivo participativo (exactamente lo que el original marca como nota para el ponente).

## 6. Veredicto del pipeline y lecciones

| Etapa | Veredicto |
|---|---|
| Investigación | **Pasa con matiz**: 71% de cobertura con parciales, chuleta de trampas equivalente en disciplina, más fresca en productos (FDA, Sora) pero perdió 9 datos y falló 2 veces por no llegar al primario. Requiere pase de "fuentes de aniversario/earnings" en la plantilla de queries. |
| Redacción | **Pasa como didáctica, no como oratoria**: estructura, higiene y trazabilidad al nivel del original; le faltan anécdota propia, participación del público y variación de registro. Añadir a la plantilla de guion hablado: bloque de historia personal + frase ancla participativa. |
| Proceso | Las 4 pasadas y el aparato didáctico son productivas y auditablemente aplicadas. El validador de JSONs (12/12 al 100%) funcionó como red de calidad real (atrapó el typo de campo). |

**Lecciones concretas para el pipeline:**
1. **Buscar el primario antes de rechazar**: el fact-check debe incluir "¿existe un reporte oficial que establezca esta cifra?" para toda cifra que se vaya a descalificar (el caso IC3).
2. **Queries de aniversario/earnings**: para métricas de empresas, la fuente fresca vive en posts de aniversario y llamadas de ganancias, no en la búsqueda general (Translate, AI Overviews).
3. **Plantilla de guion hablado**: añadir "bloque de anécdota propia" y "ancla participativa (3ª vez la dice el público)" como secciones obligatorias; la didáctica sola produce clase, no conferencia.
4. **Puntos porcentuales**: añadir a la chuleta estándar la distinción puntos/porcentaje en toda cifra de deltas.
5. **Corrida en paralelo tiene valor real**: la comparación encontró en cada corrida datos que la otra no vio (71% + 9 perdidos ↔ el original también carece de Sora-muerte, Apple/Siri, Pew-voz, Gerlich, extras DNR). Para entregables críticos, doble corrida + cruce es más potente que una corrida más larga.

## 7. Notas de ejecución (herramientas)

- El despacho de subagentes `general-purpose` falló de forma determinista (proveedor configurado inexistente: `zai-api/GLM-5.3`); `Explore` es de solo lectura y no puede escribir los JSONs. La investigación corrió **inline** con la metodología `web-researcher.md` (14 búsquedas). La prueba midió el pipeline de *contenidos*, no el de *paralelización*.
- El validador (`validate_json.py`) exigió `fields: {categoría: [...]}` + `uncertain: []` arriba y atrapó un typo de campo (`corroboring` vs `corroborating`) en los 12 JSONs; 12/12 PASS al 100% antes de cerrar la etapa.
- Commits por etapa: setup (833b716), investigación (440f836), redacción (2133c8e), comparación (este).

## 8. Veredicto final de la prueba

**El pipeline del taller, corrido solo, produce un 70-75% del material de la conferencia en investigación y una redacción didácticamente sólida pero fría.** Para el estándar "listo para subir al escenario" falta: (a) el pase de primarios en fact-check, (b) la inyección de voz propia del ponente en redacción, (c) la doble corrida cruzada para máxima cobertura. Como sistema de *borrador avanzado* con trazabilidad total, el pipeline funciona y es reproducible; como reemplazo completo del proceso manual, todavía no.
