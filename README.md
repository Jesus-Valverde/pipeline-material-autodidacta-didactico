# Pipeline para material autodidacta y didáctico

Un pipeline personal de IA para **investigar, redactar y producir** dos tipos de material: informes completos para aprender temas por cuenta propia, y libros didácticos o estudiantiles. No es un SaaS ni una app: es un flujo de trabajo armado sobre un agente de IA (skills en formato abierto `SKILL.md`), configurado con reglas propias y verificable hasta la fuente.

## Qué es y qué no es

**Es un generador de borradores de alta calidad, no un producto final desatendido.**

Esto no es escepticismo de marketing: se midió. El pipeline se corrió desde cero sobre el mismo outline de una conferencia escrita a mano, en corrida semi-ciega (ver [la comparación completa](ejemplos/informe-conferencia/comparacion-pipeline-vs-manual.md)). Resultado: empató en didáctica y en manejo de datos (9/10 en ambos), y perdió en oratoria (6/10) — no genera la anécdota propia del ponente, ni la variación de registro, ni el momento en que el público dice la frase ancla. Esas cosas las pone el autor.

El trato es honesto: el pipeline te entrega un borrador **trazable hasta la fuente** (cada dato con su cita y su nivel de solidez), y tú le inyectas lo que solo tú tienes. En un libro didáctico de 15 capítulos, eso significa recibir el manuscrito estructurado, verificado y con aparato pedagógico, y trabajar sobre él — no empezar de la página en blanco.

## Cómo funciona: cuatro capas

| Capa | Qué hace | Herramientas |
|---|---|---|
| **1. Investigar** | Reúne datos con procedencia; cada afirmación queda etiquetada (I-xx) con nivel de solidez: SÓLIDO / VERIFICADO EN TERCEROS / PROVISIONAL; lo disputado se marca como disputado | agente de investigación (deep research) + búsqueda en APIs académicas (OpenAlex, arXiv, Semantic Scholar, Crossref...) + paso opcional por Elicit para extracción estructurada de papers |
| **2. Redactar** | Redacta desde la fuente única con reglas fijas: estructura didáctica (*qué es → por qué importa → cómo se usa* + ejemplo real), cifras en el cuerpo, una idea por párrafo, aparato didáctico por capítulo (objetivos, preguntas, puntos clave, glosario) | skill propia de redacción didáctica + escaneo anti-"huellas de IA" en la prosa (negación muleta, tríadas, señalización vacía...) |
| **3. Diseñar** | Aplica paleta y tipografía coherentes; los libros de texto conservan tipografía editorial (serif 11pt, interlineado 120–145%) | skill de temas (color+tipografía) + fundamentos de diseño |
| **4. Producir** | Render final (docx/PDF) y verificación visual página por página contra criterios de aceptación | skill de documentos + revisión visual automatizada |

Reglas transversales: **fuente única** (nada se afirma que no esté en la investigación), **veredicto = la dimensión más baja** (un documento con contenido 9 y fuentes 4 no pasa), y **edición en cuatro pasadas** (borrador → line editing → copyedit → lectura ciega).

## Ejemplos

- **[Libro: Stack de desarrollo de Software con IA](ejemplos/libro-stack-con-ia/)** — libro didáctico de 15 capítulos generado con el pipeline completo: entrevista inicial de alcance, investigación con fuentes, tres pasadas editoriales por capítulo, evaluación final de "editor adquisidor" leyendo el PDF ciego. PDF completo incluido.
- **[Prueba contra material hecho a mano](ejemplos/informe-conferencia/comparacion-pipeline-vs-manual.md)** — el mismo guion de conferencia, escrito a mano vs. generado por el pipeline, comparado dato por dato: cobertura 71%, conflictos adjudicados contra fuente primaria, y el veredicto por dimensión que origina el posicionamiento de este repo.

## Las investigaciones: qué evalué, qué tomé y qué rechacé

Durante el armado se evaluaron ~20 herramientas y colecciones. El registro completo está en [investigaciones.md](investigaciones.md). La moraleja que sale de todas: casi todo lo que se vende como "generador de X con IA" es una interfaz sobre los mismos modelos que un agente propio ya orquesta — la pregunta filtro que mata el 90% de las compras es **"¿qué fase de mi pipeline resuelve esto, y qué tengo yo ya instalado para esa fase?"**

## Cómo replicarlo

El pipeline vive entero en skills de formato abierto (`SKILL.md` — el estándar que leen Claude Code, zCode, Cursor, Codex y compañía):

1. **Consigue un agente que lea skills** y una carpeta de skills propia.
2. **Cada capa es una skill**: investigación con solidez, redacción con tu canon personal (esto es lo no-distribuible: TUS reglas), temas de diseño, render. Los componentes de terceros que uso vienen de repos abiertos: [scientific-agent-skills](https://github.com/K-Dense-AI/scientific-agent-skills) (K-Dense, MIT), [bookwright](https://github.com/adrianmastronardi/bookwright) (pipeline editorial de libros, MIT), [anthropics/skills](https://github.com/anthropics/skills) (temas y documentos, Apache-2.0), y adaptaciones propias del [guía de escritura técnica de Xamfonos](https://github.com/Xamfonos/technical-writing-best-practices) y de los [AI-tells de Book Genesis](https://github.com/felipelobomotta-blip/book-genesis-studio) (MIT).
3. **Estructura tu proyecto** por entregable: carpeta del tema → `investigacion.md` (fuente única) → borrador → render.
4. **Versiona todo** — un libro son semanas de trabajo; sin git es una apuesta.

## Contexto

Armado y estrenado en octubre de 2026 por [Jesús Valverde](https://github.com/Jesus-Valverde), docente universitario. El libro de ejemplo fue su primer producto: del material fuente al manuscrito completo en corridas de trabajo con un agente. Licencia MIT — toma lo que te sirva.

*Advertencia de método: los precios y límites de las herramientas evaluadas cambian cada mes; cada dato de [investigaciones.md](investigaciones.md) lleva su fecha y su nivel de solidez. Verifica antes de decidir con tu dinero.*
