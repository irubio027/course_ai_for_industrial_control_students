# Carro-péndulo: RL frente a control clásico (n19) - Cuestionario de evaluación

- **Grupo:** ________________________________
- **Nombres:** ________________________________
- **Uso de IA: no / sí, para…** ________________________________

Criterio de corrección: se valora sobre todo que entendáis los conceptos y los expliquéis con vuestras palabras y vuestros resultados.

Entrega el cuestionario en formato `.md`, no PDF. Cuando una pregunta pida cifras, cópialas de **vuestra** ejecución (y, si habéis cambiado algún parámetro, indicad cuál).

## Información
- **Fecha**: ________________________________
- **Asignatura**: Aplicaciones de la IA para Control Industrial
- **Notebook**: n19 - Carro-péndulo: aprendizaje por refuerzo (DQN) frente a PID y LQR

## 📋 Instrucciones
Ejecutad `n19_cartpole_rl_vs_control.ipynb` completo con `QUICK_RUN = False`. Las preguntas de la sección 3 piden que activéis uno o más ejercicios (`RUN_... = True`). En las preguntas de opción múltiple, elegid una opción **y justificadla** con una frase.

---

## Sección 1: La planta y el control clásico

**Pregunta 1**: Copiad los autovalores de $A$ en lazo abierto que imprime vuestro notebook. ¿Qué autovalor hace que el sistema sea inestable y qué significa físicamente su valor? Usadlo para estimar cuánto tarda el péndulo en caer sin control desde 3° y comparadlo con la animación «Sin control».

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 2**: En el PID de dos lazos, $K_{px}$ y $K_{dx}$ son **positivos**: si el carro está a la derecha ($x>0$), el controlador empuja primero hacia la **derecha**. ¿Por qué? ¿Qué pasó en vuestro Laboratorio 1 cuando les cambiasteis el signo?

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 3**: Rellenad la tabla con vuestras pruebas del Ejercicio 2 (Laboratorio 1, empujón de 15 N salvo que se indique otra cosa):

| Prueba | Ganancias o pesos usados | ¿Aguanta? | Retorno | Esfuerzo $\sum u^2\Delta t$ |
|---|---|---|---|---|
| PID que aguanta 20 N | | | | |
| LQR con $R$ = 0.01 | | | | |
| LQR con $R$ = 0.1 (nominal) | | | | |
| LQR con $R$ = 1 | | | | |

Explicad con vuestras palabras qué representa $R$ y qué observáis en $u(t)$ y en $x(t)$ al cambiarlo.

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 4**: ¿Cuál es la masa máxima (masa ×) con la que vuestro LQR **nominal** aguanta el empujón de 15 N? ¿Por qué un controlador diseñado con un modelo deja de funcionar si la planta real es distinta?

_Masa máxima:_ ________________________________

_Explicación:_ _______________________________________________________________________________

---

## Sección 2: El agente de RL

**Pregunta 5**: Completad la tabla de equivalencias con vuestras palabras (no copiéis la del notebook: explicad qué es cada cosa **en este problema**):

| Control | RL | ¿Qué es en el carro-péndulo? |
|---|---|---|
| estado $x$ | estado $s$ | |
| entrada $u$ | acción $a$ | |
| coste $x^\top Q x + u^\top R u$ | recompensa $r$ | |
| ley de control $u = -Kx$ | política $\pi(s)$ | |
| coste acumulado $x^\top P x$ | función de valor $V(s)$ | |

**Pregunta 6**: Con $\gamma = 0.99$ y $\Delta t$ = 20 ms, ¿cuántos segundos «mira hacia el futuro» el agente, aproximadamente? ¿Qué creéis que pasaría con $\gamma = 0.9$ en esta tarea?

_Vuestra respuesta:_

_______________________________________________________________________________

**Pregunta 7**: En `train_dqn`, el fin de episodio por tiempo (`trunc`) **no** se guarda como estado terminal, pero la caída (`term`) sí. ¿Por qué es importante esta diferencia para los valores Q?

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 8**: Copiad los resultados de **vuestro** entrenamiento:

| Dato | Vuestro valor |
|---|---|
| Tiempo de entrenamiento [s] | |
| Episodios jugados | |
| Transiciones usadas | |
| Mejor evaluación del DQN (máx. 500) | |
| Evaluación del LQR | |
| Evaluación del PID | |
| ¿En qué paso aproximado empieza el DQN a aguantar los 6 s? | |

Describid la curva de evaluación: ¿sube de forma monótona? Si no, ¿por qué creéis que guardamos **la mejor** red y no la última?

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 9**: En la animación «Durante el entrenamiento», describid **con vuestras palabras** qué hace la red a 0 pasos, a la mitad y al final. ¿Qué aprende primero el agente: no dejar caer el péndulo o mantener el carro centrado? ¿Por qué creéis que es así, mirando la recompensa?

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 10**: Mirad el **mapa de la política**. ¿En qué porcentaje de la rejilla empujan el DQN y el LQR en el mismo sentido (vuestro valor)? ¿Dónde se parecen más y dónde menos? ¿Por qué el mapa del DQN es «a escalones»?

_Porcentaje:_ ________________________________

_Explicación:_ _______________________________________________________________________________

---

## Sección 3: Comparativa, robustez y diseño

**Pregunta 11**: Copiad las tablas de **vuestra** comparativa:

| Controlador | Retorno medio | Éxito [%] | RMS θ [°] | Esfuerzo | Variación media de u | µs por acción |
|---|---|---|---|---|---|---|
| LQR | | | | | | |
| PID | | | | | | |
| DQN | | | | | | |

| Controlador | Empujón máx. recuperado [N] | Masa máx. con 100 % éxito [×] | Éxito con ruido ×4 [%] |
|---|---|---|---|
| LQR | | | |
| PID | | | |
| DQN | | | |

¿Cuál es más robusto ante cada tipo de perturbación? ¿Coincide con lo que esperabais? Proponed una explicación para el resultado que más os haya sorprendido.

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 12**: El DQN se entrenó con empujones de 5 a 20 N y con la masa nominal. Mirando vuestras curvas de robustez, ¿qué pasa fuera de esos rangos? Relacionadlo con la diferencia entre **interpolar** y **extrapolar** en aprendizaje automático.

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 13**: Sección 7 (identificación + LQR). ¿Con cuántas transiciones consigue el LQR identificado un retorno parecido al del LQR con el modelo exacto? ¿Cuántas veces más datos ha usado el DQN? ¿Por qué hay tanta diferencia? Pista: ¿cuántos números tiene que aprender cada enfoque?

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 14**: Elegid **uno** de los ejercicios 4, 5 o 6, activadlo (`RUN_... = True`) y contad qué habéis cambiado, qué cifras habéis obtenido (comparadas con las del DQN original) y qué conclusión sacáis. Si es el ejercicio 4, explicad qué término del $Q$ del LQR hace el mismo papel que el término de $x$ de la recompensa.

_Ejercicio elegido:_ ________________________________

_Cifras (vuestras):_ _______________________________________________________________________________

_Conclusión:_ _______________________________________________________________________________

**Pregunta 15**: Ejercicio 7 (supervisor). ¿Qué umbral habéis usado? En la prueba de estrés, ¿cuántos pasos actúa el LQR y aguanta el sistema? ¿Qué ventajas e inconvenientes tiene esta arquitectura en una planta real?

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

**Pregunta 16**: Sois el equipo de automatización de una fábrica con un **puente grúa** que mueve bobinas de acero y la carga oscila. El jefe de planta propone «poner una IA de aprendizaje por refuerzo». Con lo que habéis visto en este notebook, ¿qué le recomendaríais y por qué? Mencionad al menos: datos/ensayos necesarios, seguridad, robustez ante cargas distintas y qué haríais primero.

_Vuestra respuesta:_

_______________________________________________________________________________

_______________________________________________________________________________

_______________________________________________________________________________
