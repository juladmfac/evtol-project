# Aerodinámica y simulación del flujo

Recomendaciones para medir la eficiencia aerodinámica y simular el flujo de aire alrededor del eVTOL. Acordado el 31/10/2026.

## Qué se mide

Un eVTOL tiene dos eficiencias distintas y hay que medir las dos:

| Fase | Medida | Qué dice |
| --- | --- | --- |
| Crucero | **L/D** (sustentación / resistencia) | Cuánto peso sostiene por cada unidad de resistencia |
| Hover | **Figura de mérito** de los rotores | Qué tanto se acerca el rotor al rotor ideal de la teoría de cantidad de movimiento |
| Comparar configuraciones | **L/D equivalente = W·V / P** | Pone en la misma escala a configuraciones con y sin ala |

## Escalera de herramientas

Se sube un escalón solo cuando el anterior ya está resuelto y validado. Cada escalón sirve para controlar al siguiente.

| # | Qué | Programa | Dónde corre | Cuándo |
| --- | --- | --- | --- | --- |
| 1 | Perfil 2D: polares Cl, Cd, Cm | XFLR5 (XFOIL adentro) | PC | Etapa 4 |
| 2 | Ala + empenaje 3D | XFLR5 | PC | Etapa 4 |
| 3 | Aeronave completa: L/D | OpenVSP + VSPAERO + **Parasite Drag** | PC | Etapa 4 |
| 4 | Rotores en hover: figura de mérito, potencia | Python, teoría del elemento de pala | Nube | Etapa 3–4 |
| 5 | Interacción rotor–ala, transición | DUST | Nube | Paso 5 de la secuencia |
| 6 | Flujo completo: presiones, líneas de corriente, estela | **OpenFOAM** (SimScale para aprender) | Nube | Paso 6 de la secuencia |
| 7 | Visualización | ParaView | PC | Paso 8 de la secuencia |

## Recomendaciones para que el CFD salga bien

### Antes de simular

1. **Geometría estanca y limpia.** La superficie exportada (STL) tiene que estar cerrada, sin agujeros, sin caras superpuestas y sin detalles que no influyen en el flujo (bulones, juntas). Se exporta desde Fusion u OpenVSP y se revisa antes de mallar.
2. **Escala real y unidades en metros.** Se simula la aeronave a tamaño real, al número de Reynolds de vuelo. El prototipo a escala vuela a otro Reynolds y su aerodinámica es distinta: si se quiere simular el prototipo, es un caso aparte.
3. **Media aeronave cuando el caso es simétrico.** En crucero sin deslizamiento se simula la mitad con un plano de simetría: la mitad de celdas por el mismo detalle.
4. **Condición de vuelo escrita.** Velocidad, altitud, densidad, viscosidad y ángulo de ataque salen de `docs/requisitos.md` y del sizing, no se eligen al simular.

### Malla y modelo

5. **Dominio grande.** Las paredes del túnel virtual tienen que estar lejos para no afectar el flujo: del orden de decenas de longitudes de la aeronave, sobre todo aguas abajo, para que entre la estela.
6. **Capas de borde sobre la superficie.** Celdas finas y aplastadas pegadas a la piel, que es donde se genera la resistencia de fricción. Se controla el parámetro y+ según el modelo de pared elegido.
7. **Modelo de turbulencia k-ω SST** como punto de partida: es el habitual para flujo externo aeronáutico con posible desprendimiento.
8. **Estudio de convergencia de malla.** El mismo caso con tres mallas (gruesa, media, fina). Si CL y CD cambian poco de la media a la fina, la malla alcanza. Sin este estudio, el resultado no vale.
9. **Convergencia de la solución.** Los residuos bajan y CL y CD dejan de cambiar entre iteraciones. Se guardan los gráficos.

### Rotores

10. **No se simulan las palas girando al principio.** Es muy costoso. En crucero, los rotores de sustentación detenidos o retraídos; los que empujan, como **disco actuador** (un disco que acelera el aire sin palas). Las palas reales, solo si un resultado lo justifica.
11. **La interacción rotor–ala se estudia con DUST**, que está hecho para eso y es mucho más barato que el CFD completo.
12. **Hover y transición son casos aparte del crucero.** En hover importa la **descarga** (download): la estela de los rotores golpea el ala y resta empuje útil. En una planta alar grande, como un ala triangular, puede ser importante.

### Validación

13. **Primero un caso con resultado conocido.** Antes de simular el eVTOL se reproduce un caso publicado con datos de túnel de viento (por ejemplo, un perfil NACA con los datos de Abbott y von Doenhoff, o un ala de ensayo documentada). Si el caso conocido no da, el del eVTOL tampoco va a dar.
14. **Comparación cruzada.** El L/D del CFD se compara con XFLR5, VSPAERO y el sizing. Si difieren mucho, se busca la causa antes de creerle a cualquiera.
15. **Todo se documenta:** malla, modelo, condiciones, convergencia y validación, en `geometria/` o en una carpeta `cfd/` por caso.

### Del resultado a la app

16. **ParaView** extrae líneas de corriente y mapas de presión sobre la superficie, y los exporta (VTK, glTF).
17. **Blender** los coloca sobre el modelo para el modo "flujo de aire".
18. **Lo que no salga de una simulación se rotula como ilustrativo** (regla 6 de `CLAUDE.md`).

## Reparto del trabajo

- **Julian (PC con Windows):** geometría en Fusion u OpenVSP, exportación STL, XFLR5, VSPAERO, visualización en ParaView.
- **Claude (sesiones en la nube, Linux):** intentar instalar y correr OpenFOAM y DUST en el contenedor; malla, caso y ejecución; devolver los resultados para ParaView. Hay que probar si el contenedor alcanza (4 núcleos, unos 15 GB de RAM a la fecha); si no, SimScale.
- **SimScale:** para aprender a armar un caso desde el navegador. En el plan gratuito los proyectos son públicos (verificar condiciones vigentes): no subir la geometría final ahí si se quiere mantener privada.
