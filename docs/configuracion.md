# Comparación de configuraciones

## Preferencia de Julian (31/10/2026)

**Ala volante / cuerpo de ala integrada (BWB) triangular + rotores basculantes**, inspirada en la forma del Airbus ZEROe de ala integrada. Motivo: la forma triangular sustenta con todo el cuerpo y permitiría usar pocos rotores.

Contexto: el ZEROe de ala integrada era un concepto de avión de línea a hidrógeno, sin despegue vertical. Su forma se toma como inspiración, no como referencia de números.

## Análisis de Claude: ventajas y riesgos a evaluar

Son hipótesis cualitativas; el sizing y la geometría las confirman o las descartan.

### A favor

- **Todo el cuerpo sustenta**, no solo el ala.
- **Mucho volumen interno** para repartir baterías y cabinas.
- **Mucha superficie para montar rotores** en puntas, borde de ataque o borde de fuga, alrededor del centro de gravedad.

### Riesgos

1. **Efecto de escala.** Las ventajas de un BWB están estudiadas para aviones grandes, donde la cabina entra holgada en el espesor del cuerpo central. En una aeronave de unas 3 t, la altura de una cabina con gente sentada obliga a un cuerpo central muy grueso respecto de su cuerda, y eso agrega resistencia. Hay que verificar con la geometría si todavía conviene.
2. **Estabilidad sin cola.** Un ala volante tiene un rango de centro de gravedad estrecho. Con dos cabinas, una adelante y otra atrás, el centro de gravedad se mueve según quién viaje y dónde. Soluciones posibles: baterías ubicadas para compensar, perfiles con borde de fuga levantado (reflex), flecha con torsión, superficies verticales o una cola chica.
3. **Descarga en hover.** En vuelo estacionario, la estela de los rotores golpea el ala y le resta empuje útil. Un ala triangular grande debajo de los rotores puede agravarlo. Conviene ubicar los rotores por fuera de la planta o que la parte que bascula los saque del ala.
4. **Pocos rotores contra tolerancia a fallas.** Pocos rotores grandes son más eficientes en hover, porque tienen menos carga de disco. Pero si falla uno, los demás tienen que sostener la aeronave, y la norma (EASA SC-VTOL, categoría reforzada) exige seguir volando y aterrizar de forma segura después de una falla. Al ser autónomo y sin piloto, la tolerancia a fallas pesa todavía más. La cantidad de rotores se decide con el sizing, comparando variantes.
5. **Ventanas laterales.** En un BWB la cabina queda "adentro" del ala: solo los asientos cercanos al borde del cuerpo central tienen ventana. La cabina trasera, en especial, puede quedar sin vista lateral. Lo mismo pasa con las salidas de emergencia.

### Propuesta de comparación

Para saber si el BWB conviene hace falta una **referencia convencional** contra la cual medirlo:

| Variante | Descripción |
| --- | --- |
| A | BWB triangular + rotores basculantes (preferencia de Julian) |
| B | Referencia: fuselaje + ala convencional + rotores basculantes, misma misión y misma cabina |

Y para cada una, variantes de cantidad de rotores. `PENDIENTE` de aprobación.

| Criterio | A: BWB | B: convencional | Fuente |
| --- | --- | --- | --- |
| Peso máximo de despegue | | | sizing |
| Potencia en hover | | | sizing |
| L/D en crucero | | | VSPAERO / CFD |
| Energía de batería | | | sizing |
| Rango de centro de gravedad | | | geometría |
| Tolerancia a falla de un rotor | | | sizing |
| Ventanas y salidas | | | CAD |

## Decisión

`PENDIENTE`
