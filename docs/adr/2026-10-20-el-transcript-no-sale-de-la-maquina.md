# El transcript no sale de la máquina

## Contexto

Un agente que revisa el trabajo diario de Claude Code vería información personal y privada, técnica
y también funcional: nombres de clientes, condiciones, situaciones particulares.

## Decisión

El transcript nunca sale de la máquina de la persona. Lo que sale es un extracto, y el filtro actúa
antes de que exista el extracto. Cuatro barreras, de fuera a dentro:

1. Alcance por lista blanca: solo se captura lo vinculado a un proyecto o responsabilidad
   declarados; una ruta marcada como privada no se lee.
2. Filtro determinista, sin modelo: secretos, credenciales, correos, teléfonos, identificadores
   personales, y una lista de términos de la organización, sustituidos por marcadores.
3. Clasificación por el extractor: lo personal no sale; lo funcional sale solo generalizado. La
   instancia concreta vive en el work item de su proyecto, que ya tiene control de acceso.
4. Comprobación en destino: el catálogo rechaza cualquier PR con un secreto o un término de la
   lista.

La captura es opcional por persona; para quien se apunte, el buzón de salida se revisa a mano
antes de sincronizar.

## Alternativas descartadas

- Filtrar en el consolidador central: para entonces el transcript ya ha salido.
- Confiar solo en el modelo para redactar: un filtro determinista caza lo mecánico sin depender de
  que el modelo lo vea.

## Consecuencias

El consolidador nunca ve un transcript. Las métricas de coste no incluyen el contenido de los
prompts salvo activación expresa.
