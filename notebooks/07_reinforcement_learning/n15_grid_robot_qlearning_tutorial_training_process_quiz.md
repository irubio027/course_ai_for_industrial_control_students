# Q-learning: robot en una rejilla 2D (n15) - Cuestionario de evaluación

- **Grupo:** ________________________________
- **Nombres:** ________________________________
- **Uso de IA: no / sí, para…** ________________________________

Criterio de corrección: se valora sobre todo que entendáis los conceptos y los expliquéis con vuestras palabras y vuestros resultados.

Entrega el cuestionario en formato `.md`, no PDF. Cuando una pregunta pida cifras, cópialas de **vuestra** ejecución (y, si habéis cambiado algún parámetro, indicad cuál).

## Información
- **Fecha**: ________________________________
- **Asignatura**: Aplicaciones de la IA para Control Industrial
- **Notebook**: n15 - Q-learning: un robot que aprende a moverse por una rejilla 2D

---

## Sección 1: Conceptos básicos

### 1.1 El entorno

**Pregunta 1**: ¿Cuál es el objetivo principal del robot en la rejilla? Elegid una opción y justificadla.
- a) Llegar a la meta evitando las trampas
- b) Visitar todas las celdas de la rejilla una sola vez
- c) Llegar a la meta en el mínimo número de pasos
- d) Quedarse en la salida y no moverse

**Pregunta 2**: Completad la configuración de la rejilla 5×5:
- Posición de salida: ________________________________
- Posición de la meta: ________________________________
- Recompensa de la meta: ________________________________
- Posiciones de las trampas: ________________________________
- Coste por paso: ________________________________

**Pregunta 3**: ¿Qué representa el valor Q(s,a) en Q-learning? Elegid una opción y justificadla.
- a) La recompensa inmediata por tomar la acción a en el estado s
- b) La recompensa acumulada esperada por tomar la acción a en el estado s y seguir después la política óptima
- c) La probabilidad de tomar la acción a en el estado s
- d) El número de veces que se ha tomado la acción a en el estado s

**Pregunta 4**: ¿Cuáles son las cuatro acciones posibles del robot?
1. ________________________________
2. ________________________________
3. ________________________________
4. ________________________________

### 1.2 Mecánica básica del Q-learning

**Pregunta 5**: ¿Qué pasa cuando el robot intenta salirse de la rejilla? Buscad en las **actualizaciones de Q** que imprime vuestro notebook un ejemplo de esta situación y copiadlo (estado, acción, recompensa, Q antes y después).

_Vuestra respuesta:_
_______________________________________________________________________________
_______________________________________________________________________________

---

## Sección 2: El algoritmo de Q-learning

### 2.1 Fundamentos matemáticos

**Pregunta 6**: Completad la regla de actualización del Q-learning:

Q(s, a) ← Q(s, a) + α [________________________________]

Donde:
- s: ________________________________
- a: ________________________________
- α: ________________________________
- γ: ________________________________
- r: ________________________________

**Pregunta 7**: Explicad con vuestras palabras el papel de cada hiperparámetro:

**Tasa de aprendizaje (α = 0.1):**
_______________________________________________________________________________

**Factor de descuento (γ = 0.9):**
_______________________________________________________________________________

**ε inicial (ε = 1.0):**
_______________________________________________________________________________

### 2.2 El proceso de entrenamiento

**Pregunta 8**: Describid en orden los cuatro pasos principales del bucle de entrenamiento:
1. ________________________________
2. ________________________________
3. ________________________________
4. ________________________________

**Pregunta 9**: ¿Qué es la política ε-greedy y por qué es importante?

_Definición:_
_______________________________________________________________________________

_Importancia:_
_______________________________________________________________________________

---

## Sección 3: Exploración frente a explotación

### 3.1 La estrategia

**Pregunta 10**: Si ε = 0.2, ¿qué porcentaje del tiempo el agente…
- explora (acción aleatoria): ________________________________ %
- explota (mejor acción conocida): ________________________________ %

**Pregunta 11**: ¿Por qué ε suele ir bajando durante el entrenamiento?

_Vuestra respuesta:_
_______________________________________________________________________________
_______________________________________________________________________________

**Pregunta 12**: ¿Qué pasaría si ponemos…? Comprobadlo en el **laboratorio** y contad lo que habéis visto.
- **Tasa de aprendizaje α = 0** (o casi, 0.01): ________________________________
- **Factor de descuento γ = 0**: ________________________________

### 3.2 Análisis del rendimiento

**Pregunta 13**: En la **animación del entrenamiento**, describid qué hace el robot en el episodio 1, en el 60 y en el 1000. ¿Desde dónde empiezan a «propagarse» los valores Q positivos en el mapa de la derecha y por qué?

_Vuestra respuesta:_
_______________________________________________________________________________
_______________________________________________________________________________

---

## Sección 4: Proceso de entrenamiento y resultados

### 4.1 Seguimiento del rendimiento

**Pregunta 14**: ¿Qué información se registra durante el entrenamiento para seguir el rendimiento del agente? Citad al menos 4 métricas y copiad el valor final de **vuestra** ejecución:

| Métrica | Valor final (vuestro) |
|---|---|
| | |
| | |
| | |
| | |

**Pregunta 15**: ¿Qué significa que los valores Q «convergen» durante el entrenamiento? Usad la tabla de evolución de Q del estado (2, 2) de vuestro notebook como ejemplo.

_Vuestra respuesta:_
_______________________________________________________________________________
_______________________________________________________________________________

### 4.2 Análisis crítico

**Pregunta 16**: Durante un entrenamiento observáis que:
- La recompensa por episodio sube durante 200 episodios y luego se estanca
- La tasa de éxito llega al 85 % hacia el episodio 150
- Los valores Q de los pares estado-acción óptimos se estabilizan hacia el episodio 180
- ε ha bajado de 1.0 a 0.1

Analizad la situación y explicad qué indica sobre el proceso de aprendizaje:

_Vuestro análisis:_
_______________________________________________________________________________
_______________________________________________________________________________
_______________________________________________________________________________

---

## Sección 5: Vuestros experimentos (laboratorio)

**Pregunta 17**: Copiad la tabla del **barrido α × γ** de vuestro notebook (episodio en que se alcanza un 90 % de éxito). ¿Qué combinación aprende antes? ¿Hay alguna que no llegue nunca? Explicad por qué.

_Vuestra respuesta:_
_______________________________________________________________________________
_______________________________________________________________________________

**Pregunta 18**: En el laboratorio, poned la **recompensa por paso** a 0 y después a +1 (con el resto por defecto). ¿Qué hace la política final en cada caso? ¿Qué os enseña esto sobre el diseño de la recompensa en un problema industrial?

_Con 0:_ ________________________________

_Con +1:_ ________________________________

_Conclusión:_ _______________________________________________________________________________
