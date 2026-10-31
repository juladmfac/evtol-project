# Registro de decisiones

Una entrada por decisión, la más nueva arriba.

## 31/10/2026: trayecto, reserva y puerta

- **Decisión:** misión en el área metropolitana de Buenos Aires: Puerto Madero → Tigre, o la ruta La Plata → Puerto Madero → Tigre → Pilar. Reserva de 20 min como mínimo. Una sola puerta tipo puerta-escalera, con bisagra abajo.
- **Por qué:** elección de Julian.
- **Pendiente:** si se recarga en cada escala (define la misión de diseño); verificar las distancias en un mapa; si la norma pide una salida de emergencia adicional.

## 31/10/2026: ala recta y cabina 2 y 2 enfrentados

- **Decisión:** ala recta con estrechamiento y puntas con una pequeña curva hacia atrás. Cabina de pasajeros amplia, 4 asientos en 2 filas enfrentadas, con ventanas laterales.
- **Por qué:** a 180 km/h (Mach ≈ 0,15) la flecha no aporta y cuesta sustentación y peso; las puntas curvadas dan el aspecto buscado sin costo aerodinámico apreciable. Distribución de cabina elegida por Julian.
- **Pendiente:** medidas de cabina (Roskam Parte III o Raymer) y ubicación de las puertas.

## 31/10/2026: góndolas traseras más altas

- **Decisión:** las góndolas traseras van más altas que las delanteras, sobre un pilón en la punta trasera de cada viga.
- **Por qué:** quedan fuera de la estela de los delanteros en transición y del chorro de las hélices delanteras y de la estela del ala en crucero.
- **Pendiente:** cuánto más altas (DUST, VSPAERO); forma del ala (Claude propone recta con estrechamiento, ver `docs/configuracion.md`).

## 31/10/2026: una viga por lado

- **Decisión:** las góndolas delantera y trasera de cada lado van montadas en una viga por lado, por debajo del ala, en lugar de 4 brazos.
- **Por qué:** menos piezas, más rigidez contra la vibración de las góndolas y las cargas pasan directo al larguero del ala.
- **Pendiente:** altura de las góndolas traseras respecto de las delanteras; Claude propone traseras más altas (ver `docs/configuracion.md`).

## 31/10/2026: vista en planta y cola tipo S-97

- **Decisión:** se adopta la cola tipo S-97 con una sola propulsora en el eje. Se mantiene el ala. 4 góndolas basculantes coaxiales: 2 delante del ala en brazos desde la nariz, 2 detrás del ala en brazos desde el fuselaje. Boceto en `docs/bocetos/2026-10-31-vista-en-planta.png`.
- **Por qué:** disposición elegida por Julian.
- **Pendiente:** propuesta de una viga por lado en lugar de 4 brazos; forma del ala; distribución de los 4 pasajeros.

## 31/10/2026: reparto de baterías en diagonal y propuesta de cola tipo S-97

- **Decisión:** se aprueba el reparto de baterías en circuitos independientes, cada paquete alimentando dos rotores en diagonal.
- **En evaluación:** reemplazar la cola en V y las 2 propulsoras por una cola como la del Sikorsky S-97 con una sola propulsora en el eje. Julian duda de que hagan falta 2 propulsoras y quiere poder avanzar sin bascular las góndolas. Análisis en `docs/configuracion.md`.
- **Pendiente:** dónde van las góndolas traseras con la cola nueva; comparar en el sizing con y sin propulsora.

## 31/10/2026: rotores coaxiales y baterías independientes

- **Decisión:** las 4 góndolas basculantes llevan 2 rotores coaxiales cada una (8 rotores). Varios paquetes de baterías independientes. Se confirman 4 pasajeros. Las góndolas traseras cuelgan de un brazo bajo la cola.
- **Por qué:** según Julian, los coaxiales dan tolerancia a la falla de un rotor en hover sin agregar góndolas al ala, y los paquetes separados, seguridad. 4 pasajeros porque la aeronave va a ser pesada de todos modos.
- **Pendiente:** aprobar la propuesta de circuitos independientes (cada paquete alimenta dos rotores en diagonal, ver `docs/configuracion.md`), alimentación de las propulsoras y tensión del sistema.

## 31/10/2026: 4 pasajeros y fuselaje más ancho

- **Decisión:** se mantienen 4 rotores basculantes + 2 propulsoras. Se ensancha el fuselaje para llevar 4 pasajeros en vez de 2.
- **Por qué:** según Julian, integrar 6 rotores basculantes en el ala es muy complejo; y si la aeronave lleva igual 6 hélices, conviene que transporte más gente.
- **Pendiente:** cómo resolver la falla de un rotor en hover con 4 posiciones (coaxiales, motores redundantes o 2 rotores en la cola en V; ver `docs/configuracion.md`). Distribución de los 4 asientos.

## 31/10/2026: rotores basculantes y hélices propulsoras

- **Decisión:** basculan los 4 rotores. Se agregan 2 hélices propulsoras fijas en la parte trasera del fuselaje, al pie de la cola en V, que solo empujan hacia adelante.
- **Por qué:** idea de Julian.
- **Pendiente:** las propulsoras no aportan en hover, así que no resuelven la falla de un rotor en hover. Claude propone comparar cuatro arquitecturas en el sizing (T4+P2, T6, L+P2, T6+P2). Ver `docs/configuracion.md`.

## 31/10/2026: nueva configuración y 2 pasajeros

- **Decisión:** se descarta el ala volante triangular. Nueva configuración: fuselaje + ala alta + cola en V + rotores basculantes, 4 rotores en primera instancia, probablemente 6 o más por norma. Transporta 2 pasajeros.
- **Por qué:** según Julian, el ala triangular era muy compleja; con 2 pasajeros la aeronave es más chica y lleva menos carga.
- **Consecuencias:** la masa total de 3000–3500 kg y la cabina de 6 asientos quedan sin efecto. Boceto en `docs/bocetos/2026-10-31-fuselaje-ala-alta-cola-v.jpg`.
- **Pendiente:** cantidad y reparto de rotores, qué rotores basculan, distribución de los 2 asientos.

## 31/10/2026: misión y configuración preferida

- **Decisión:** taxi aéreo de pasajeros autónomo (IA), sin cabina de tripulación. Masa total 3000–3500 kg, velocidad de crucero inicial 180 km/h. Dos cabinas con asientos enfrentados y vista lateral. Configuración preferida: ala volante / BWB triangular con rotores basculantes.
- **Por qué:** según Julian, más valioso que un taxi tripulado o que un dron de carga. La forma triangular sustenta con todo el cuerpo y permitiría usar pocos rotores.
- **Pendiente:** cantidad de pasajeros (2–4 contra 6 asientos), si la masa total es el peso máximo de despegue, trayecto y alcance, reserva de energía. Ver `docs/requisitos.md` y `docs/configuracion.md`.

## 31/10/2026: método para la aerodinámica y el flujo

- **Decisión:** escalera de herramientas XFLR5 → OpenVSP/VSPAERO → DUST → OpenFOAM, con validación contra un caso publicado y estudio de convergencia de malla. Detalle en `docs/aerodinamica.md`.
- **Por qué:** cada escalón controla al siguiente; el CFD solo vale si está validado.

## 30/10/2026: herramientas instaladas y repositorio

- **Decisión:** XFLR5, OpenVSP y Blender instalados en la PC. Fusion 360 disponible. Repositorio `evtol-project` creado, separado de Volar 2050.
- **Por qué:** checklist del primer día del instructivo.

## 29/10/2026: secuencia de programas

- **Decisión:** se sigue la secuencia de diez pasos de Python a React Three Fiber (ver `CLAUDE.md`). CATIA queda para cuando el diseño esté maduro.
- **Por qué:** la facultad no tiene licencias de CATIA ni de SolidWorks; el camino arranca con herramientas gratuitas.
