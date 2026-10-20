# Plan de la fase 1: la recopilación del conocimiento existente

Una persona, desde cero. La infraestructura entra cuando un paso la necesita, nunca antes. Nada de
lo que falta hace falta el primer día.

## Punto de partida

| Tengo | Me falta |
|---|---|
| Claude Code en mi máquina, con agentes, skills y reglas en local | Los catálogos: maestro y departamento |
| Un tracker con repositorios y backlog | El plugin de captura y el filtro |
| Proyectos con su repositorio | El extractor y el consolidador |

Dónde viven los catálogos, en el tracker de la organización o en GitHub, es una decisión
pendiente; este repositorio está en GitHub para poder continuar desde cualquier PC.

## Semana 1: la semilla

| Día | Qué |
|---|---|
| 1 | Dos repositorios: catálogo maestro y catálogo del departamento. En el maestro, el árbol, las decisiones, la convención y un validador mínimo: identificadores únicos y referencias que resuelven. Un marketplace vacío pero válido. |
| 2 | Inventario de lo local: cada agente, skill, regla y MCP de la carpeta de Claude y de los proyectos, en una tabla, con una pregunta por fila: ¿es de la empresa, del departamento o de un proyecto? Solo clasificar. |
| 3 | Migración: cada cosa a su nivel como plugin. Instalar desde los catálogos y borrar las copias locales. Si Claude sigue trabajando igual, la migración está bien. |
| 4 | Las responsabilidades propias como plugins mínimos: un agente, una plantilla de tarea y el esquema de configuración con huecos. En el primer proyecto, la carpeta de responsabilidades con la configuración rellena. |
| 5 | El primer flujo completo a mano: una tarea, trabajo con Claude en el proyecto, y una nota de relevo escrita por la persona. Sin hooks ni captura. Lo que se mide esta semana es si la estructura estorba o ayuda. |

**Al final de la semana 1:** dos catálogos con validador y ninguna copia local; un proyecto con su
carpeta de responsabilidades y la versión de los catálogos fijada; una opinión formada sobre si la
estructura ayuda.

## Semanas 2 y 3: captura y primer bucle

| Semana | Qué |
|---|---|
| 2 | Plugin de captura, solo en una máquina: hook de fin de sesión y de subagente que copia el transcript a una carpeta local de trabajo, etiquetado con proyecto y responsabilidad; fichero personal con rutas privadas. |
| 2 | Filtro determinista: la lista de patrones y la lista de términos del departamento, probadas contra los transcripts de la semana 1. |
| 2 | Extractor nocturno por cron o systemd, que deja extractos en el buzón. Al principio se leen a mano cada mañana. |
| 3 | Consolidador nocturno que abre PRs a los catálogos. Se ajusta su prompt, en el catálogo maestro, por PR. |
| 3 | Pasada inicial sobre el backlog: bugs y PBIs cerrados del último año del proyecto, para sacar las primeras fichas funcionales. |

**Al final de la semana 3:** extractos cada noche y la primera PR de conocimiento fusionada; las
primeras fichas funcionales salidas del backlog; el filtro probado contra transcripts reales.

## Qué significa hecho

| Semana 1 | Mes 1 |
|---|---|
| Se instala desde los catálogos, sin copias locales | Extractos cada noche y PRs de conocimiento fusionadas |
| Un proyecto con su carpeta de responsabilidades | Primeras fichas funcionales salidas del backlog |
| Una tarea con su relevo | El primer ascensor al departamento, si algo se repite |

## Lo que queda para la fase 2

Estado de tareas, relevos y preguntas en el tracker; alarma de coste; identidad, secretos y acceso
de los agentes; agentes críticos. El diseño de la fase 1 no debe impedir nada de eso, y no lo
construye.

## Mañana

Crear los dos catálogos y el árbol. Es media mañana de trabajo y no necesita a nadie más.
