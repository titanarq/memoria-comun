# Memoria común: instrucciones para agentes

## Qué es esto

El proyecto de construcción de un sistema de conocimiento compartido para trabajar con agentes:
catálogos de plugins de Claude Code en tres niveles, una captura opcional del trabajo diario que
nunca saca el transcript de la máquina, y un bucle que convierte la producción en reglas, skills,
agentes y fichas, por PR. El diseño está en `docs/diseno/`, las decisiones en `docs/adr/` y el plan
en `docs/plan/`. Léelos en ese orden antes de tocar nada.

## Idiomas

Conversación con el propietario y documentación del repositorio: español. Código, identificadores,
nombres de fichero de código, mensajes de commit y comentarios de código: inglés
(`docs/adr/2026-10-20-idioma-de-la-documentacion.md`).

## Alcance

Este repositorio contiene la fase 1, la recopilación del conocimiento existente. La fase 2, la
gestión del trabajo con agentes, no entra hasta que el propietario la abra: ni estado en el tracker,
ni protocolo del responsable, ni coste, ni identidad, ni agentes críticos. Si un cambio la necesita,
se deja escrito como pendiente, no se construye.

## Dónde va cada cosa

| Qué es | Dónde va |
|---|---|
| Una decisión con su porqué y sus alternativas | `docs/adr/<fecha>-<slug>.md` |
| Diseño de un mecanismo | `docs/diseno/<nn>-<tema>.md`, numerado en orden de lectura |
| Un diagrama | `docs/diagramas/<tema>.svg`, autónomo, con sus estilos dentro |
| El plan y sus comprobaciones de "hecho" | `docs/plan/` |
| Convenciones de catálogo, ficha e identificadores | `docs/diseno/07-convencion.md` |

## Reglas

- Ningún nombre de empresa, cliente, persona ni sistema interno en el repositorio. Los ejemplos
  usan nombres genéricos.
- Ninguna credencial, token ni URL interna, ni en documentos ni en ejemplos.
- Lo que sube de nivel pierde nombres y gana parámetros: un documento del catálogo maestro no
  menciona un proyecto concreto.
- El trabajo llega como PR en una rama; nunca directo a `main`. Commits en inglés.
- Un documento de diseño cambia cuando cambia el mecanismo que describe, en su sección, sin crecer
  si se puede evitar. Una decisión nueva es un ADR nuevo, no una edición de uno viejo.
