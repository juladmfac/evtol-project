# Comparación de configuraciones

## Configuración actual (31/10/2026)

Boceto de Julian: [`bocetos/2026-10-31-fuselaje-ala-alta-cola-v.jpg`](bocetos/2026-10-31-fuselaje-ala-alta-cola-v.jpg)

Lectura de Claude del boceto (`PENDIENTE` que Julian la confirme):

- **Fuselaje convencional** con nariz redondeada y ventanas, para 2 pasajeros.
- **Ala alta**, recta, montada sobre el fuselaje.
- **Cola en V** arriba de la parte trasera.
- **4 rotores basculantes en góndolas sobre brazos**, dibujados en posición de hover: un par alto, a la altura del ala, y un par bajo, en brazos que salen de la parte inferior del fuselaje. Los de adelante y los de atrás quedan a distinta altura. Basculan los 4 (confirmado por Julian, 31/10/2026). Julian anticipa que la norma lo lleve a 6 o más.
- **2 hélices propulsoras fijas** en la parte trasera del fuselaje, al pie de la cola en V, que solo empujan hacia adelante (Julian, 31/10/2026). Ubicación marcada en [`bocetos/2026-10-31-ubicacion-helices-propulsoras.png`](bocetos/2026-10-31-ubicacion-helices-propulsoras.png).

### Hélices propulsoras traseras: análisis de Claude

Es una disposición posible y usada: varios eVTOL de sustentación + crucero llevan una hélice propulsora atrás, como el Wisk Cora o el Aurora PAV de Boeing.

**Aportan**

- **Transición:** empujan hacia adelante mientras los rotores siguen verticales, y la aeronave gana velocidad sin depender solo de bascular.
- **Crucero:** una hélice diseñada solo para crucero puede rendir más que un rotor basculante, que es un compromiso entre hover y crucero.
- **Redundancia en crucero:** si falla un rotor basculante en crucero, queda empuje.

**No resuelven**

- **La falla de un rotor en hover.** En hover las propulsoras no sostienen nada: sostienen solo los 4 rotores basculantes, así que el problema de perder 1 de 4 sigue igual.

**Riesgos**

1. **Dos sistemas para la misma función.** Si los 4 rotores basculan para crucero y además están las propulsoras, se carga con el peso del mecanismo de basculación y el de las propulsoras, y ambos empujan en crucero. Hay que justificar con números que la suma conviene.
2. **Flujo perturbado.** Una hélice propulsora trabaja en la estela del fuselaje y cerca de la cola en V: más ruido y vibración, y la cola puede quedar en el chorro de la hélice o afectarla.
3. **Centro de gravedad hacia atrás.** Motores y hélices en la cola mueven el centro de gravedad hacia atrás; hay que compensar con la ubicación de las baterías.
4. **Espacio libre.** Diámetro de las hélices contra el suelo y contra la cola en V.

### Arquitecturas a comparar

| Variante | Hover | Crucero | Comentario |
| --- | --- | --- | --- |
| T4+P2 | 4 rotores basculantes | 4 basculantes + 2 propulsoras | Configuración actual de Julian |
| T6 | 6 rotores basculantes | 6 basculantes | Sin propulsoras; mejor tolerancia a falla en hover |
| L+P2 | 4, 6 u 8 rotores **fijos** de sustentación | 2 propulsoras | Sin mecanismo de basculación; los rotores fijos quedan detenidos y hacen resistencia en crucero |
| T6+P2 | 6 rotores basculantes | 6 basculantes + 2 propulsoras | Tolerancia a falla en hover y propulsoras para transición |

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

Ya no hace falta una "referencia convencional": esta configuración lo es. Se comparan las arquitecturas de la tabla anterior (`PENDIENTE` de aprobación de Julian):

| Criterio | T4+P2 | T6 | L+P2 | T6+P2 | Fuente |
| --- | --- | --- | --- | --- | --- |
| Peso máximo de despegue | | | | | sizing |
| Potencia en hover, normal y con un rotor caído | | | | | sizing |
| L/D en crucero | | | | | VSPAERO / CFD |
| Energía de batería | | | | | sizing |
| Rango de centro de gravedad | | | | | geometría |

## Configuración descartada: ala volante / BWB triangular

Preferencia inicial de Julian (31/10/2026), inspirada en el Airbus ZEROe de ala integrada. Descartada el mismo día por Julian por ser muy compleja. Riesgos que se habían identificado:

1. **Efecto de escala:** a unas 3 t, la cabina obliga a un cuerpo central muy grueso para su cuerda.
2. **Estabilidad sin cola** con dos cabinas que mueven el centro de gravedad.
3. **Descarga en hover** por el ala grande debajo de los rotores.
4. **Pocos rotores contra tolerancia a fallas.**
5. **Ventanas laterales** difíciles con la cabina dentro del ala.

## Decisión

`PENDIENTE`: configuración preferida, fuselaje + ala alta + cola en V + 4 rotores basculantes + 2 hélices propulsoras fijas atrás. Falta decidir la arquitectura final con el sizing.
