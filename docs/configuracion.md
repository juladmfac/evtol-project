# Comparación de configuraciones

## Configuración actual (31/10/2026)

Boceto de Julian: [`bocetos/2026-10-31-fuselaje-ala-alta-cola-v.jpg`](bocetos/2026-10-31-fuselaje-ala-alta-cola-v.jpg)

Lectura de Claude del boceto (`PENDIENTE` que Julian la confirme):

- **Fuselaje convencional** con nariz redondeada y ventanas, para 2 pasajeros.
- **Ala alta**, recta, montada sobre el fuselaje.
- **Cola en V** arriba de la parte trasera.
- **4 rotores en góndolas sobre brazos**, dibujados en posición de hover: un par alto, a la altura del ala, y un par bajo, en brazos que salen de la parte inferior del fuselaje. Los de adelante y los de atrás quedan a distinta altura. Julian anticipa que la norma lo lleve a 6 o más.
- **Rotores basculantes**: `PENDIENTE` si basculan los 4 o solo algunos.

### Opinión de Claude

Hipótesis cualitativas; el sizing y la geometría las confirman o las descartan.

**A favor**

1. **Se puede calcular con los libros.** Fuselaje, ala alta y cola son la configuración que cubren Raymer, Roskam y Gudmundsson, con métodos de pesos y aerodinámica directamente aplicables. Con el ala triangular había que adaptar casi todo.
2. **Ala alta:** deja el piso de la cabina cerca del suelo para subir y bajar, buena vista hacia abajo desde las ventanas, y la estela de los rotores bajos no la golpea de lleno en hover.
3. **Cola en V:** dos superficies en vez de tres, menos superficie mojada y menos resistencia. La contra habitual, que los mandos de profundidad y dirección quedan mezclados, no importa en una aeronave autónoma: la computadora de vuelo hace la mezcla.
4. **Rotores delanteros y traseros a distinta altura:** ayuda a que los traseros no traguen la estela de los delanteros, ni en hover ni en transición.

**Riesgos a evaluar**

1. **Brazos largos.** Pesan, suman resistencia en crucero y son flexibles. En rotores basculantes hay un fenómeno conocido, el *whirl flutter* (vibración acoplada entre la góndola y el rotor), que empeora cuando el soporte es flexible. Alternativa: apoyar las góndolas en el ala o en vigas (booms) bajo el ala, que comparten estructura.
2. **Rotores bajos a la altura de la puerta.** Los pasajeros suben al lado de rotores que pueden estar girando, y las palas quedan cerca del suelo. En una aeronave sin piloto, que nadie supervisa en el embarque, es un punto de seguridad importante.
3. **4 rotores y falla de uno.** Con 4 rotores, si falla uno en hover queda un empuje asimétrico difícil de compensar. La norma (EASA SC-VTOL, categoría reforzada) exige seguir volando y aterrizar de forma segura después de una falla, sin fijar una cantidad de rotores. Conviene dibujar desde ya una geometría donde entren 6 en posiciones simétricas, y comparar 4, 6 y 8 en el sizing.
4. **Estela de los rotores sobre la cola en V en crucero**, si los traseros basculan hacia adelante y quedan a la altura de la cola. A revisar con la geometría.
5. **Centro de gravedad:** en hover, los rotores tienen que rodear el centro de gravedad en planta. Con 2 pasajeros y baterías, ubicarlas para que el centro de gravedad quede entre los pares de rotores.

### Propuesta de comparación

Ya no hace falta una "referencia convencional": esta configuración lo es. Se comparan variantes de la misma configuración:

| Variante | Rotores | Qué bascula |
| --- | --- | --- |
| C-4 | 4 | `PENDIENTE` |
| C-6 | 6 | `PENDIENTE` |
| C-8 | 8 | `PENDIENTE` |

| Criterio | C-4 | C-6 | C-8 | Fuente |
| --- | --- | --- | --- | --- |
| Peso máximo de despegue | | | | sizing |
| Potencia en hover, normal y con un rotor caído | | | | sizing |
| L/D en crucero | | | | VSPAERO / CFD |
| Energía de batería | | | | sizing |
| Rango de centro de gravedad | | | | geometría |

## Configuración descartada: ala volante / BWB triangular

Preferencia inicial de Julian (31/10/2026), inspirada en el Airbus ZEROe de ala integrada. Descartada el mismo día por Julian por ser muy compleja. Riesgos que se habían identificado:

1. **Efecto de escala:** a unas 3 t, la cabina obliga a un cuerpo central muy grueso para su cuerda.
2. **Estabilidad sin cola** con dos cabinas que mueven el centro de gravedad.
3. **Descarga en hover** por el ala grande debajo de los rotores.
4. **Pocos rotores contra tolerancia a fallas.**
5. **Ventanas laterales** difíciles con la cabina dentro del ala.

## Decisión

`PENDIENTE`: configuración preferida, fuselaje + ala alta + cola en V + rotores basculantes. Falta definir la cantidad y el reparto de rotores.
