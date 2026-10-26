# Ejemplo 2 — Prueba del pipeline contra material hecho a mano

La prueba de honestidad del repo: el mismo guion de una conferencia ("El futuro llegó hace rato", 40 min), escrito **a mano** en octubre de 2026 vs. **regenerado por el pipeline** desde cero sobre el mismo outline, en corrida semi-ciega. Después, comparación dato por dato.

**Lo que mide:** si el pipeline produce sistemáticamente lo que una corrida manual produjo, y dónde falla.

**Resultado en una tabla** (el detalle completo en [`comparacion-pipeline-vs-manual.md`](comparacion-pipeline-vs-manual.md)):

| Etapa | Veredicto |
|---|---|
| Investigación | Pasa con matiz: 71% de cobertura de los datos originales (54% completa/mejorada), chuleta de trampas equivalente, más fresca en productos — pero perdió 9 datos y adjudicó mal 2 conflictos por no llegar a la fuente primaria |
| Redacción | Pasa como didáctica (9/10) y como datos (9/10); **no** como oratoria (6/10): sin anécdota propia, sin participación del público |
| Proceso | Las 4 pasadas de edición y el aparato didáctico son productivas y auditables; el validador de calidad atrapó errores reales |

De ahí sale el posicionamiento del repo: **generador de borradores trazables, no producto final** — el paso humano (voz, anécdota, dispositivo participativo) es insustituible y está fuera del pipeline a propósito.
