# Instalación

Paso a paso para levantar este pipeline en tu máquina. Al terminar tienes un agente que investiga con fuentes verificadas, redacta con tus reglas y rinde documentos editables. Tiempo total: 30–45 minutos.

## Requisitos previos

- Un agente que lea skills en formato `SKILL.md` (zCode, Claude Code, OpenCode, Cursor, Codex…)
- `git`
- Python 3.10+ con pip (solo para la capa de producción: `pip install python-docx`; `pymupdf` si además quieres verificación programática del PDF)

## 1. Crea tu carpeta de skills

```bash
mkdir -p ~/.zcode/skills    # o ~/.claude/skills, ~/.codex/skills… según tu agente
```

Cada skill es una carpeta con su `SKILL.md` adentro. Instalar = copiar la carpeta.

## 2. Instala las skills abiertas

| Capa | Skill | Origen | Licencia |
|---|---|---|---|
| Investigar | deep-research (outline editable → agentes paralelos → reporte) | [Weizhena/Deep-Research-skills](https://github.com/Weizhena/Deep-Research-skills) | MIT |
| Investigar | paper-lookup, liteparse, scientific-critical-thinking, citation-management | [K-Dense/scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) | MIT |
| Redactar | bookwright (pipeline editorial de no-ficción) | [adrianmastronardi/bookwright](https://github.com/adrianmastronardi/bookwright) | MIT |
| Diseñar | theme-factory (paletas+tipografía) | [anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 |
| Diseñar | visual-design-foundations | [wshobson/agents](https://github.com/wshobson/agents) | MIT |
| Producir | docx (render) | [anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 |

```bash
git clone --depth 1 https://github.com/<repo> /tmp/skill-src
cp -r /tmp/skill-src/<carpeta-de-la-skill> ~/.zcode/skills/
```

Ojo con K-Dense: son 177 skills y el clon completo es pesado. Descarga solo las 4 carpetas que necesitas (vía botón de archivo individual en la web, o `git sparse-checkout`) — clonar todo puede agotar la conexión.

## 3. Escribe TU skill de redacción (la parte no distribuible)

El corazón del pipeline es una skill personal con **tus** reglas de escritura — por eso no viene en este repo. La tuya debe definir, como mínimo:

- **Estructura didáctica**: qué es → por qué importa → cómo se usa + ejemplo real; cifras en el cuerpo del texto, no en notas.
- **Disciplina de solidez**: cada dato etiquetado (I-xx) con nivel (sólido / verificado en terceros / provisional); lo disputado se marca; se busca activamente al menos una fuente que contradiga la premisa.
- **Cuatro pasadas de edición**: borrador → line editing → copyedit → lectura ciega.
- **Escaneo anti "huellas de IA"** en el copyedit (negación muleta, tríadas, señalización vacía…). Puntos de partida: [Xamfonos technical-writing](https://github.com/Xamfonos/technical-writing-best-practices) y [Book Genesis](https://github.com/felipelobomotta-blip/book-genesis-studio) (MIT).
- **Aparato didáctico** por capítulo: objetivos, preguntas de reflexión, puntos clave, glosario.
- **Constantes tipográficas del render** (fuente serif 11pt, interlineado 120–145%, márgenes generosos).

## 4. Arma tu proyecto

```
mi-taller/
  AGENTS.md            # el cableado: qué skill carga cada capa
  informes/<tema>/     # investigacion.md (fuente única) → draft.md → output/
  libros/<libro>/      # pipeline bookwright: manifesto, voice, toc, capítulos
```

`AGENTS.md` mínimo (adáptalo):

```markdown
# AGENTS.md — Mi taller
Pipeline: investigar → redactar → diseñar → producir.

## Parámetros de apertura
- modo: `web` (default, fuentes generales) | `academico`
  (Google Académico/arXiv/SciELO/OA; Elicit obligatorio; references.bib desde el día 1)

## Pasos por informe
1. Investigar con deep-research + paper-lookup → informes/<tema>/investigacion.md
   (datos I-xx con solidez; buscar fuente que contradiga la premisa)
2. Redactar con mi skill de redacción → draft.md
3. Cuatro pasadas de edición + aparato didáctico
4. Render docx con constantes tipográficas → output/
5. Revisión visual del render; commit por etapa

## Reglas
- Fuente única: nada se afirma fuera de investigacion.md
- Veredicto = la dimensión más baja
```

## 5. Prueba de humo

1. Abre tu agente en la carpeta del proyecto.
2. Pide: *"Investiga [tu tema] en modo web"*. Éxito = `investigacion.md` con datos etiquetados, niveles de solidez y al menos una fuente en contra buscada explícitamente.
3. Pide: *"Redacta el informe"*. Éxito = estructura didáctica, cifras en el cuerpo, aparato didáctico.
4. Pide: *"Renderiza el docx"*. Éxito = `output/` con el documento abrible y tipografía de libro, no de chat.

Si los cuatro puntos pasan, el pipeline está vivo. Lo que salga de aquí es un **borrador trazable** — el juicio final sobre qué entra y cómo se dice es tuyo.

## PDF (opcional)

El render nativo es docx (editable, que es el punto). Para PDF: en Windows con Word, exportar desde el propio agente; en Linux/Mac, `soffice --headless --convert-to pdf archivo.docx` con LibreOffice.
