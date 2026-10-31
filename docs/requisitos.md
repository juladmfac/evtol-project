# Requisitos de misión

Cada requisito lleva su valor, su justificación y su fuente. Lo que no tenga fuente se rotula `SUPUESTO`. Lo marcado `PENDIENTE` espera una decisión de Julian.

## Misión

- **Qué es:** taxi aéreo de pasajeros, **autónomo** (vuela con IA, sin piloto), sin cabina de tripulación. Decidido por Julian el 31/10/2026.
- **Qué transporta:** pasajeros y su equipaje o carga.
- **Trayecto:** área metropolitana de Buenos Aires (Julian, 31/10/2026). Dos casos:
  - **Tramo simple:** Puerto Madero → Tigre.
  - **Ruta con escalas:** La Plata → Puerto Madero → Tigre → Pilar.

### Distancias

En línea recta, calculadas por Claude con coordenadas aproximadas del centro de cada lugar. `SUPUESTO`: verificar con la herramienta "medir distancia" de Google Maps entre los puntos exactos de despegue y aterrizaje. La ruta real puede ser más larga si sigue corredores aéreos.

| Tramo | Distancia (km) | Tiempo a 180 km/h (min) |
| --- | --- | --- |
| La Plata → Puerto Madero | ≈ 51 | ≈ 17 |
| Puerto Madero → Tigre | ≈ 29 | ≈ 10 |
| Tigre → Pilar | ≈ 31 | ≈ 10 |
| **Ruta completa** | **≈ 110** | **≈ 37** |

Los tiempos son solo de crucero: no incluyen despegue, transición, ascenso, descenso ni aterrizaje.

### Misión de diseño

`PENDIENTE`: ¿se recarga en cada escala?

- **Con recarga en cada escala:** la batería se dimensiona para el tramo más largo (La Plata → Puerto Madero, ≈ 51 km) más la reserva.
- **Sin recarga:** la batería se dimensiona para la ruta completa (≈ 110 km), con 4 despegues y 4 aterrizajes verticales (el hover es la fase que más energía consume), más la reserva.

Propuesta de Claude: el sizing calcula las dos y se decide con los números.

### Nota operativa

Aeroparque Jorge Newbery queda entre Puerto Madero y Tigre, sobre la costa: el tramo atraviesa espacio aéreo controlado. No afecta al sizing, pero sí a la altura y la ruta reales.

### Nota regulatoria sobre la autonomía

A la fecha, las reglas de aeronavegabilidad y de operación de eVTOL de pasajeros que se consultaron (EASA SC-VTOL, FAA powered-lift) suponen un piloto. El transporte autónomo de pasajeros no tiene todavía un camino de certificación. Para el diseño conceptual se adoptan los requisitos de aeronavegabilidad de un eVTOL pilotado y se agrega la autonomía como requisito propio. Implicancias a cuantificar en el sizing:

- **A favor:** sin piloto, su asiento y su masa quedan para un pasajero; sin cabina de mando, más libertad en la forma.
- **En contra:** sensores, computadoras y enlaces redundantes que suman masa y consumo.

## Requisitos

| Requisito | Valor | Justificación | Fuente |
| --- | --- | --- | --- |
| Pasajeros | 4, en un fuselaje más ancho (confirmado) | Si la aeronave lleva igual 4 góndolas + 2 propulsoras, conviene que transporte más gente | Julian, 31/10/2026 (reemplaza los 2 pasajeros) |
| Masa total | `PENDIENTE`. Propuesta de Claude: que el peso máximo de despegue salga del sizing | Los 3000–3500 kg iniciales se fijaron para 2–4 pasajeros; usarlos solo como referencia de control | Julian, 31/10/2026 |
| Carga útil | `PENDIENTE` (pasajeros + equipaje + equipamiento) | Se divide más adelante | Julian, 31/10/2026 |
| Alcance | `PENDIENTE` | Sale del trayecto elegido | — |
| Reserva de energía | 20 min como mínimo; estudio de sensibilidad con 30 min | Criterio regulatorio | Julian, 31/10/2026; FAA, ver abajo |
| Velocidad de crucero | 180 km/h (50 m/s), valor inicial | Puede ajustarse después del sizing | Julian, 31/10/2026 |
| Altitud de crucero | `PENDIENTE` | | |

### Reserva de energía: estado de la normativa (consultado el 31/10/2026)

- **FAA:** la regla final para powered-lift (Federal Register 2024-24886, publicada el 21/11/2024) dejó de lado la reserva de avión (30 min de día, 45 de noche) y permite a los powered-lift usar la de helicópteros, 20 min en VFR, cuando pueden aterrizar verticalmente en cualquier punto de la ruta. **Verificar el texto exacto de la regla.**
- **EASA:** propone una reserva basada en desempeño, equivalente a la energía para un escape (go-around) más una aproximación, sin minutos fijos. **Verificar si ya fue adoptada y su texto vigente.**
- **ANAC:** no se encontró norma específica de eVTOL. **Verificar.**

**Decisión (Julian, 31/10/2026):** 20 min como mínimo, a velocidad de mejor alcance, con un estudio de sensibilidad con 30 min. Es la única cifra fija vigente encontrada.

## Cabina

Sin cabina de mando. 4 pasajeros en una cabina amplia, **2 y 2 enfrentados**, cada uno con ventana lateral (Julian, 31/10/2026).

Implicancias a resolver en la geometría:

- **Largo de cabina:** dos filas enfrentadas necesitan espacio para las piernas entre ellas. Medidas de asientos, pasillos y espacio para piernas: tomarlas de Roskam, Parte III (diseño de cabina y fuselaje) o de Raymer, no suponerlas.
- **Centro de gravedad:** la cabina conviene centrada bajo el ala, que es donde cae el centro de gravedad. Así, volar con 1 o con 4 pasajeros lo mueve poco.
- **Puerta:** una sola, a un costado, bajo el ala, entre las góndolas delanteras y traseras. Se abre de arriba hacia abajo, con la bisagra abajo, como una puerta-escalera (*airstair*) de avión ejecutivo: abierta, sirve de escalón (Julian, 31/10/2026). Vista lateral: [`bocetos/2026-10-31-vista-lateral.png`](bocetos/2026-10-31-vista-lateral.png).
  - `PENDIENTE` verificar en la normativa (SC-VTOL) si con 4 pasajeros alcanza una sola puerta o hace falta una salida de emergencia adicional.
  - Los escalones de la puerta abierta tienen que quedar lejos de los discos de las góndolas.

Historial, todo del 31/10/2026: dos cabinas con 6 asientos (4 adelante en 2 bancos enfrentados, 2 atrás de "clase alta") → 2 pasajeros → 4 pasajeros.

## Perfil de misión

Gráfico de altura contra distancia. Cada tramo lleva su duración o distancia, su altura y su velocidad. Valores `PENDIENTE`.

```text
altura
  │              3 ascenso          4 crucero (180 km/h)          5 descenso
  │                 ╱‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾‾╲
  │   2 transición ╱                                               ╲ 6 transición
  │      ┌────────╯                                                 ╰────────┐
  │      │ 1 despegue vertical                      7 aterrizaje vertical    │   8 reserva
  └──────┴────────────────────────────────────────────────────────────────────┴────────────▶ distancia
```

| # | Segmento | Duración o distancia | Altura | Velocidad | Fuente |
| --- | --- | --- | --- | --- | --- |
| 1 | Despegue vertical (hover) | `PENDIENTE` | | 0 | |
| 2 | Transición a vuelo con ala | `PENDIENTE` | | | |
| 3 | Ascenso | `PENDIENTE` | | | |
| 4 | Crucero | `PENDIENTE` (sale del trayecto) | `PENDIENTE` | 180 km/h | Julian |
| 5 | Descenso | `PENDIENTE` | | | |
| 6 | Transición a hover | `PENDIENTE` | | | |
| 7 | Aterrizaje vertical (hover) | `PENDIENTE` | | 0 | |
| 8 | Reserva | `PENDIENTE` (ver reserva) | | | |

Fuente candidata para las duraciones de hover y transición: la misión de referencia de los vehículos conceptuales de NASA para taxi aéreo (Johnson, Silva y Solis, *Concept Vehicles for VTOL Air Taxi Operations*, AHS, 2018). `[cita sin verificar]`: leer el paper y adoptar sus valores solo si Julian lo aprueba.

## Configuración candidata

Fuselaje ensanchado + ala alta + cola en V + 4 góndolas basculantes con rotores coaxiales (8 rotores) + 2 hélices propulsoras fijas en la parte trasera del fuselaje + varios paquetes de baterías independientes. Reemplaza al ala volante triangular. Análisis y riesgos en `docs/configuracion.md`.

## Prototipo a escala

- **Escala:** `PENDIENTE`
- **Peso máximo:** `PENDIENTE`, según la normativa de la ANAC para drones (verificar versión vigente)
