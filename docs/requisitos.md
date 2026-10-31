# Requisitos de misión

Cada requisito lleva su valor, su justificación y su fuente. Lo que no tenga fuente se rotula `SUPUESTO`. Lo marcado `PENDIENTE` espera una decisión de Julian.

## Misión

- **Qué es:** taxi aéreo de pasajeros, **autónomo** (vuela con IA, sin piloto), sin cabina de tripulación. Decidido por Julian el 31/10/2026.
- **Qué transporta:** pasajeros y su equipaje o carga.
- **Trayecto:** `PENDIENTE`. Elegir dos puntos reales y medir la distancia en un mapa.

### Nota regulatoria sobre la autonomía

A la fecha, las reglas de aeronavegabilidad y de operación de eVTOL de pasajeros que se consultaron (EASA SC-VTOL, FAA powered-lift) suponen un piloto. El transporte autónomo de pasajeros no tiene todavía un camino de certificación. Para el diseño conceptual se adoptan los requisitos de aeronavegabilidad de un eVTOL pilotado y se agrega la autonomía como requisito propio. Implicancias a cuantificar en el sizing:

- **A favor:** sin piloto, su asiento y su masa quedan para un pasajero; sin cabina de mando, más libertad en la forma.
- **En contra:** sensores, computadoras y enlaces redundantes que suman masa y consumo.

## Requisitos

| Requisito | Valor | Justificación | Fuente |
| --- | --- | --- | --- |
| Pasajeros | `PENDIENTE`: 2–4 según Julian, pero la distribución de cabina pedida suma 6 | Ver "Cabina" | Julian, 31/10/2026 |
| Masa total | 3000–3500 kg | `PENDIENTE` confirmar si es el peso máximo de despegue (avión + pasajeros + carga) | Julian, 31/10/2026 |
| Carga útil | `PENDIENTE` (pasajeros + equipaje + equipamiento) | Se divide más adelante | Julian, 31/10/2026 |
| Alcance | `PENDIENTE` | Sale del trayecto elegido | — |
| Reserva de energía | `PENDIENTE`: propuesta de 20 min, ver abajo | Criterio regulatorio | FAA / EASA, ver abajo |
| Velocidad de crucero | 180 km/h (50 m/s), valor inicial | Puede ajustarse después del sizing | Julian, 31/10/2026 |
| Altitud de crucero | `PENDIENTE` | | |

### Reserva de energía: estado de la normativa (consultado el 31/10/2026)

- **FAA:** la regla final para powered-lift (Federal Register 2024-24886, publicada el 21/11/2024) dejó de lado la reserva de avión (30 min de día, 45 de noche) y permite a los powered-lift usar la de helicópteros, 20 min en VFR, cuando pueden aterrizar verticalmente en cualquier punto de la ruta. **Verificar el texto exacto de la regla.**
- **EASA:** propone una reserva basada en desempeño, equivalente a la energía para un escape (go-around) más una aproximación, sin minutos fijos. **Verificar si ya fue adoptada y su texto vigente.**
- **ANAC:** no se encontró norma específica de eVTOL. **Verificar.**

**Propuesta de Claude:** usar 20 min a velocidad de mejor alcance como base, porque es la única cifra fija vigente encontrada, y hacer un estudio de sensibilidad con 30 min. `PENDIENTE` de decisión.

## Cabina

Pedido de Julian (31/10/2026): dos cabinas, sin cabina de tripulación.

- **Cabina delantera:** 4 pasajeros en 2 bancos de 2 asientos, enfrentados, cada pasajero con vista lateral a una ventana.
- **Cabina trasera ("clase alta"):** 2 asientos individuales enfrentados, con vista lateral a las ventanas.

`PENDIENTE`: la distribución suma **6 asientos**, y el requisito dice 2–4 pasajeros. Hay que definir si el diseño es para 6 o si la cabina cambia.

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

Ala volante / cuerpo de ala integrada (forma triangular, inspirada en el concepto Airbus ZEROe de ala integrada) con rotores basculantes. Análisis y riesgos en `docs/configuracion.md`.

## Prototipo a escala

- **Escala:** `PENDIENTE`
- **Peso máximo:** `PENDIENTE`, según la normativa de la ANAC para drones (verificar versión vigente)
