# Convención: identificadores, fichas, árbol y carpetas

Lo único que el nivel superior fija es la convención. Todo lo demás se decide por PR en cada
catálogo.

## Identificadores

Toda ficha, regla, skill, agente y MCP lleva un identificador estable, independiente de su ruta y
de su título: un prefijo de tipo y ocho caracteres aleatorios en base32 minúscula.

| Prefijo | Tipo |
|---|---|
| `fi-` | ficha de conocimiento |
| `rg-` | regla |
| `sk-` | skill |
| `ag-` | agente |
| `mc-` | MCP o utilidad |
| `rs-` | responsabilidad |
| `pr-` | proyecto |

El identificador se asigna una vez y nunca se recalcula. Una referencia es siempre un
identificador; el validador comprueba que todas resuelven y que ninguno se repite.

## La ficha

Un fichero Markdown por concepto, con cabecera YAML:

```markdown
---
id: fi-k7m2q9xa
titulo: Cierre mensual con fecha de corte
nivel: proyecto            # proyecto | departamento | maestro
categoria: funcional       # funcional | proceso | tecnica
estado: candidata          # candidata | confirmada | contradicha
origenes:
  - tipo: work-item
    ref: "12345"
  - tipo: extracto
    fecha: 2026-10-20
relacionadas: [fi-a3b8c1dz]
---

## Enunciado
Una frase que afirma cómo se comporta el producto o el proceso.

## Casos
Los casos que confirman el enunciado, generalizados.

## Excepciones
Lo que no cumple el enunciado y por qué.
```

`candidata` es lo que propone el consolidador; `confirmada`, lo que una persona fusionó;
`contradicha`, lo que otra ficha o un work item contradice y espera resolución. Lo funcional se
escribe generalizado; una instancia concreta con nombres no es una ficha, es un work item.

## El árbol

Un fichero YAML en el catálogo maestro con departamentos, y por cada uno sus responsabilidades y
proyectos, cada nodo con su identificador y su nombre de rol. Cada departamento tiene una bandeja
de entrada para lo que todavía no tiene sitio.

```yaml
departamentos:
  - id: dp-x1y2z3w4
    nombre: Desarrollo
    rol: desarrollo
    responsabilidades:
      - id: rs-q8r7s6t5
        nombre: Calidad
        rol: desarrollo-calidad
        aplica_a: [pr-m4n3b2v1]
    proyectos:
      - id: pr-m4n3b2v1
        nombre: Producto A
        rol: desarrollo-producto-a
    bandeja: bandeja/
```

## El catálogo

Un catálogo maestro o de departamento es un repositorio con esta forma:

```
catalogo/
  .claude-plugin/marketplace.json   el marketplace: un plugin por responsabilidad
  arbol.yaml                        solo en el maestro
  plugins/<nombre>/                 agentes, skills, hooks, MCPs, plantillas de tarea
  fichas/                           conocimiento del nivel, servido como wiki
  bandeja/                          lo que todavía no tiene sitio
```

Un plugin de responsabilidad declara en su esquema los huecos que el proyecto debe rellenar:

```yaml
# plugins/calidad/config.schema.yaml
huecos:
  test_command: { obligatorio: true, descripcion: "comando que ejecuta la suite" }
  rutas_vigiladas: { obligatorio: false, por_defecto: ["src/"] }
```

## La carpeta de responsabilidades en el proyecto

```
responsabilidades/<nombre>/
  config.yaml      plugin, versión fijada y valores de los huecos
  reglas/          particularidades que solo aplican aquí, como reglas de Claude Code
  fichas/          fichas de esta responsabilidad sobre este proyecto
```

```yaml
# responsabilidades/calidad/config.yaml
plugin: calidad@departamento-desarrollo
version: 1.4.0
valores:
  test_command: "npm test"
  rutas_vigiladas: ["src/", "lib/"]
```

El plugin lee la carpeta al arrancar la sesión. Si falta un valor obligatorio, lo dice y no inventa
uno. El proyecto fija la versión; subirla es una PR en el proyecto.
