# Los agentes no guardan nada: cada dato va a su casa

## Contexto

Lo que nace en el hilo de un Claude personal nace y muere allí. Un repositorio parecía quedarse
corto como sitio donde persistirlo todo.

## Decisión

Un agente no conserva nada en su hilo. Todo lo que importa sale de la sesión por hook hacia una
casa según la naturaleza del dato:

- **Conocimiento**, versionado y revisado: catálogos, que son repositorios git con marketplaces de
  plugins de Claude Code, fichas con identificador y un árbol.
- **Extractos y métricas**: un almacén de extractos ya filtrados. Nunca transcripts.
- **Estado** de tareas, relevos y preguntas: el tracker. Esta casa pertenece a la fase 2.

Un repositorio se queda corto solo si se intenta meter en él tres naturalezas de dato. Separadas,
cada una tiene ya una herramienta que existe.

## Alternativas descartadas

- Una base de datos propia de conocimiento: pierde la revisión por PR, el diff y el historial por
  concepto, que son justo lo que hace fiable el conocimiento.
- Subir transcripts a un almacén central: viola la decisión de privacidad.

## Consecuencias

Los agentes se pueden esconder sin perder nada: la persona solo ve lo que sale por las casas. La
continuidad no necesita transcripts, necesita catálogos y estado.
