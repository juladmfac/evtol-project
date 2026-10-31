# eVTOL propio: diseño conceptual

## Objetivo

Diseño conceptual propio de un eVTOL, documentado y justificado con bibliografía, que termine en un plano de tres vistas y, si se puede, en un prototipo a escala que vuele. Meta final: una app web interactiva con texto superpuesto y modos de vista (render, rayos X, térmico, flujo de aire, despiece), como Volar en 2050.

- **Sí entra:** requisitos de misión, elección de configuración, dimensionamiento, geometría, aerodinámica básica, planos, render y un prototipo radiocontrolado.
- **No entra:** construir o certificar una aeronave tripulada.

## Reglas

1. **Primero los números, después la forma y al final los planos.** Cada decisión queda escrita con su porqué y su fuente en `docs/decisiones.md`.
2. **No inventar datos ni cifras.** Todo supuesto queda escrito y rotulado como `SUPUESTO`, con su origen.
3. **Preguntar antes de cada decisión de diseño.** Claude propone; Julian decide.
4. **Cada fórmula lleva libro, edición, capítulo y ecuación**, en un comentario del código y en `docs/metodo.md`. Si la cita no se verificó contra el libro de Julian, se marca `[cita sin verificar]`.
5. **El diseño se hace primero en papel.** Los cálculos a mano de Julian se pasan a tests en `sizing/tests/`: el código tiene que reproducirlos.
6. **Lo que no salga de una simulación se rotula como ilustrativo** en la app y en los renders.
7. **Es una espiral, no una línea:** si la geometría o la simulación muestran un problema, se vuelve al sizing.
8. **Los PDF de los libros no se suben al repositorio** (derechos de autor). Para citar una página, se sube la captura a la sesión.

## Etapas

| # | Etapa | Entregable |
| --- | --- | --- |
| 1 | Requisitos de misión | `docs/requisitos.md` |
| 2 | Configuración | `docs/configuracion.md` |
| 3 | Dimensionamiento | `sizing/` con tests; peso, carga de disco, potencia, batería |
| 4 | Geometría y aerodinámica | `perfiles/`, `geometria/` |
| 5 | CAD y planos | `cad/`, `planos/` |
| 6 | Estructura y sistemas | Cargas, tren de potencia, centro de gravedad |
| 7 | Prototipo a escala | `prototipo/` |
| 8 | Presentación | `render/`, app web |

## Secuencia de programas (elegida el 29/10/2026)

| # | Programa | Qué se hace |
| --- | --- | --- |
| 1 | Python + Jupyter | Dimensionamiento |
| 2 | XFLR5 | Perfiles y predimensionado de ala y cola |
| 3 | OpenVSP + VSPAERO | Geometría conceptual, sustentación y resistencia, comparar configuraciones |
| 4 | Fusion 360 | CAD detallado, exportar STEP y OBJ/STL |
| 5 | DUST | Rotores: estela, interacción rotor–ala, transición |
| 6 | SU2 u OpenFOAM (o SimScale) | CFD de la aeronave |
| 7 | PyBaMM + OpenFOAM | Térmica de la batería |
| 8 | ParaView | Exportar líneas de corriente y mapas (VTK, glTF) |
| 9 | Blender | Malla, despiece, materiales, animación, GLB |
| 10 | React Three Fiber | App web |

Núcleo mínimo: pasos 1, 2, 3, 4, 9 y 10. CATIA queda para cuando el diseño esté maduro.

## Dónde corre cada cosa

- **PC de Julian (Windows):** XFLR5, OpenVSP, Blender y Fusion 360, con interfaz gráfica. Los diseños a mano en papel.
- **Sesiones de Claude en la nube:** Python, tests y notebooks; más adelante herramientas sin interfaz (XFOIL, API de OpenVSP, Blender en segundo plano). El contenedor es temporal: las dependencias se instalan con `pip install -r requirements.txt` y todo lo que importe se commitea.

## Libros de referencia

Las ediciones están por confirmar; la numeración de ecuaciones cambia entre ediciones.

| Libro | Edición | Uso |
| --- | --- | --- |
| Raymer, *Aircraft Design: A Conceptual Approach* (AIAA) | a confirmar | Método completo de diseño conceptual |
| Gudmundsson, *General Aviation Aircraft Design: Applied Methods and Procedures* | a confirmar | Criterios prácticos y ejemplos numéricos |
| Roskam, *Airplane Design*, partes I a VIII | a confirmar | Pesos, configuración, estabilidad paso a paso |
| Leishman, *Principles of Helicopter Aerodynamics* (Cambridge) | a confirmar | Cantidad de movimiento, elemento de pala, figura de mérito, hover |
| Johnson, *Rotorcraft Aeromechanics* (Cambridge) | a confirmar | Referencia avanzada de rotorcraft |

Roskam por parte: I sizing preliminar · II configuración preliminar e integración de la planta propulsora · III cabina, fuselaje, ala y empenaje · IV tren de aterrizaje y sistemas · V estimación de pesos por componente · VI aerodinámica, empuje y potencia · VII estabilidad, control y actuaciones · VIII costos.

## Normativa

Verificar siempre la versión vigente en el sitio de cada autoridad: EASA SC-VTOL, FAA powered-lift, ANAC (aeronave y operación de drones para el prototipo).

## Estructura del repositorio

```text
CLAUDE.md
docs/          requisitos, configuración, método, aerodinámica, decisiones
sizing/        Python: dimensionamiento, con tests en sizing/tests/
notebooks/     estudios de sensibilidad y gráficos
perfiles/      polares de XFOIL o XFLR5
geometria/     modelo OpenVSP (.vsp3) y resultados de VSPAERO
cad/           archivos del CAD y exportación STEP
planos/        plano de tres vistas en PDF
prototipo/     electrónica, parámetros de ArduPilot o PX4, ensayos
render/        escenas de Blender, imágenes, video
```
