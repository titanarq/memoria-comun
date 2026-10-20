# Tres niveles de catálogo con la misma forma

## Contexto

El conocimiento adquirido en un proyecto tiene que poder extenderse a otros, y el arranque de un
proyecto nuevo tiene que partir de algo. Las responsabilidades transversales corren sobre cada
proyecto, pero tienen particularidades por proyecto.

## Decisión

- Un catálogo es siempre lo mismo: marketplace de plugins, fichas con identificador y árbol. Hay
  uno maestro para la organización, uno por departamento, y el de cada proyecto, que no es un
  repositorio aparte sino una estructura de carpetas dentro del repositorio del proyecto.
- Hacia abajo se hereda y lo más específico gana, salvo lo que el nivel superior marca como
  obligatorio. Hacia arriba se generaliza: lo que sube pierde nombres y gana parámetros.
- El ascensor es una pasada del consolidador: lo que se repite en dos proyectos sube al
  departamento, generalizado, y cada proyecto sustituye su copia por una referencia más sus
  parámetros. Lo que no se repite se queda donde está.
- Cada catálogo se etiqueta con versiones; un proyecto fija las versiones de los catálogos que usa.
- Dónde corre una cosa no es dónde vive: el plugin de una responsabilidad transversal vive en el
  catálogo del departamento, escrito con huecos; la configuración, las reglas particulares y las
  fichas de esa responsabilidad sobre un proyecto viven en una carpeta del proyecto, con nombre
  fijo por convención.

## Alternativas descartadas

- Un único repositorio con todo: deja el conocimiento de un proyecto atado a él y obliga a que el
  departamento edite lo que es del proyecto.
- Guardar la configuración por proyecto en el repositorio del departamento: separa la
  configuración del sitio donde se aplica y de quien la conoce.

## Consecuencias

Clonar un proyecto trae todo lo necesario para ejecutar sus responsabilidades. El arranque de un
proyecto es instanciar los catálogos, no partir de cero.
