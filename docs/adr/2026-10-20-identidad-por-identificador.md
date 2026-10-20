# Identidad por identificador, no por ruta; reorganizar es una pasada más

## Contexto

Al principio habrá pocas responsabilidades definidas y el número crecerá con el uso. Encajar cada
cosa en el mejor sitio tiene que ser constante, no un fallo que corregir.

## Decisión

- Cada ficha, skill, agente y regla tiene un identificador estable, y las referencias son siempre
  por identificador, nunca por ruta. Mover algo no rompe nada, y un validador comprueba que toda
  referencia resuelve.
- "Sin sitio" es un estado legítimo: cada departamento tiene una bandeja de entrada.
- La reorganización es una pasada más del consolidador, con reglas escritas, que propone
  movimientos como PRs: una carpeta que supera un tamaño se parte, una ficha citada por dos
  responsabilidades sube, una bandeja con muchas fichas del mismo tema propone una responsabilidad
  nueva.

## Alternativas descartadas

- Diseñar la estructura completa de antemano: no se conoce, y cambiaría igual.

## Consecuencias

El árbol de departamentos, responsabilidades y proyectos es un fichero pequeño que se edita por PR
como todo lo demás.
