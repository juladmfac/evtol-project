# Comparación de configuraciones

## Configuración actual (31/10/2026)

Boceto de Julian: [`bocetos/2026-10-31-fuselaje-ala-alta-cola-v.jpg`](bocetos/2026-10-31-fuselaje-ala-alta-cola-v.jpg)

Lectura de Claude del boceto, confirmada y corregida por Julian:

- **Fuselaje convencional** con nariz redondeada y ventanas, ensanchado para 4 pasajeros (antes 2).
- **Ala alta**, recta, montada sobre el fuselaje.
- **Cola en V** arriba de la parte trasera.
- **4 góndolas basculantes sobre brazos, cada una con 2 rotores coaxiales**: 8 rotores en 4 posiciones (Julian, 31/10/2026). Los de adelante y los de atrás quedan a distinta altura. Las góndolas traseras cuelgan de un brazo que sale de abajo de la cola ([`bocetos/2026-10-31-detalle-gondola.jpg`](bocetos/2026-10-31-detalle-gondola.jpg), cola vista de costado). Posición exacta de las delanteras `PENDIENTE` de plano.
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

### Tolerancia a la falla de un rotor en hover

Julian (31/10/2026): integrar 6 rotores basculantes en el ala es muy complejo; prefiere mantener 4 basculantes + 2 propulsoras y ensanchar el fuselaje para 4 pasajeros. Boceto de detalle: [`bocetos/2026-10-31-detalle-gondola.jpg`](bocetos/2026-10-31-detalle-gondola.jpg) (cola vista de costado; de abajo sale el brazo que sostiene una góndola basculante trasera).

Con 4 posiciones de rotor, el problema de perder uno en hover sigue abierto. Opciones de Claude que no obligan a meter más rotores en el ala:

| Opción | Qué es | A favor | En contra |
| --- | --- | --- | --- |
| Coaxiales | Dos rotores superpuestos, girando en sentidos opuestos, en cada una de las 4 góndolas: 8 rotores en 4 posiciones | Si falla uno, el otro de la misma góndola sigue empujando; no hay que agregar góndolas | El rotor de abajo trabaja en la estela del de arriba y rinde menos; góndola más pesada y compleja. Leishman trata el rendimiento de rotores coaxiales `[cita sin verificar]` |
| Motores redundantes | Cada rotor movido por dos motores, o por un motor con bobinados independientes | Cubre la falla del motor o de su electrónica, que son las más probables | No cubre la rotura de una pala ni la falla del mecanismo de basculación |
| 2 rotores en la cola | 4 en el ala + 2 en las puntas de la cola en V: 6 posiciones sin agregar nada al ala | La cola en V ya existe y queda lejos del centro de gravedad, buen brazo para controlar | La cola tiene que soportar las góndolas; la disposición del Joby S4 es parecida (verificar) |

### Arquitecturas a comparar

| Variante | Hover | Crucero | Comentario |
| --- | --- | --- | --- |
| T4c+P2 | 4 góndolas basculantes coaxiales (8 rotores) | 4 góndolas + 2 propulsoras | **Elegida por Julian** |
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
3. **4 rotores y falla de uno.** Con 4 rotores, si falla uno en hover queda un empuje asimétrico difícil de compensar. La norma (EASA SC-VTOL, categoría reforzada) exige seguir volando y aterrizar de forma segura después de una falla, sin fijar una cantidad de rotores. **Respuesta elegida por Julian: rotores coaxiales en las 4 góndolas** (ver "Tolerancia a la falla de un rotor en hover").
4. **Estela de los rotores sobre la cola en V en crucero**, si los traseros basculan hacia adelante y quedan a la altura de la cola. A revisar con la geometría.
5. **Centro de gravedad:** en hover, los rotores tienen que rodear el centro de gravedad en planta. Con 4 pasajeros y baterías, ubicarlas para que el centro de gravedad quede entre los pares de rotores.

### Propuesta de comparación

Julian eligió 4 góndolas basculantes coaxiales + 2 propulsoras (T4c+P2). Las otras arquitecturas quedan como alternativas por si el sizing no cierra:

| Criterio | T4c+P2 | T6 | L+P2 | T6+P2 | Fuente |
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

Configuración preferida (Julian, 31/10/2026): fuselaje ensanchado para 4 pasajeros + ala alta + cola en V + 4 góndolas basculantes con rotores coaxiales (8 rotores) + 2 hélices propulsoras fijas atrás + varios paquetes de baterías independientes. Se confirma o se corrige con el sizing.

## Arquitectura eléctrica

Julian (31/10/2026): varios paquetes de baterías por seguridad.

### Serie o paralelo

| | En serie | En paralelo |
| --- | --- | --- |
| Qué se suma | La **tensión** (volts). La corriente es la misma en todos | La **capacidad** (amperes-hora) y la corriente que pueden entregar. La tensión es la misma |
| Energía total | La suma de los paquetes | La suma de los paquetes |
| Para qué sirve | Llegar a una tensión alta: para la misma potencia circula menos corriente, los cables son más finos y livianos y se pierde menos en calor | Sumar autonomía y corriente sin subir la tensión |
| Si falla un paquete | Se corta la cadena entera: **todo lo que depende de esa serie se queda sin energía** | Los demás siguen entregando, con menos autonomía |
| Cuidados | Aislación y arcos eléctricos a tensión alta; cada celda vigilada | Conectar paquetes a la misma tensión (si no, circulan corrientes entre ellos); un paquete en cortocircuito recibe la corriente de los otros, así que cada uno lleva fusible o contactor propio |

En la práctica se usan las dos: **dentro** de cada paquete las celdas van en serie (para la tensión) y en paralelo (para la capacidad). **Entre** paquetes, para seguridad, lo habitual es no unirlos en una sola barra sino formar **circuitos independientes**: cada paquete alimenta a un grupo de motores, y una falla queda encerrada en su grupo.

### Propuesta de Claude: cada paquete alimenta dos rotores en diagonal

Góndolas: delantera izquierda (DI), delantera derecha (DD), trasera izquierda (TI), trasera derecha (TD). Cada una con rotor superior (S) e inferior (I), que giran en sentidos opuestos.

| Paquete | Rotores que alimenta |
| --- | --- |
| 1 | DI-S + TD-I |
| 2 | DD-S + TI-I |
| 3 | TI-S + DD-I |
| 4 | TD-S + DI-I |

Si falla un paquete, se pierde un rotor en dos góndolas opuestas en diagonal, y esos dos rotores giran en sentidos contrarios. El empuje que se pierde queda simétrico respecto del centro de gravedad (si está en el centro de las 4 góndolas) y los pares de giro se compensan. Quedan 6 rotores, que tienen que poder sostener la aeronave: eso fija cuánto margen de potencia necesita cada motor, y lo calcula el sizing.

Además: cada paquete en su propio compartimento resistente al fuego, para que un incendio de celdas (embalamiento térmico) no se propague, y con su propio sistema de gestión (BMS). Las propulsoras: `PENDIENTE` si tienen paquete propio o comparten. Tensión del sistema: `PENDIENTE`, sale del sizing. Toda la tabla es una propuesta `PENDIENTE` de aprobación.
