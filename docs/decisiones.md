# Registro de decisiones

Una entrada por decisión, la más nueva arriba.

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
