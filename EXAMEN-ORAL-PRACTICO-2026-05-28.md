# EXAMEN ORAL PRÁCTICO — HIDROGRAFÍA CATEGORÍA A
## CMFP S5A — Escuela Naval de Cadetes "Almirante Padilla"
**Fecha del examen:** 28 de mayo de 2026
**Evaluador:** Capitán de Coberta Álvarez Orduz Omar Sebastián

---

## DATOS TÉCNICOS EXTRAÍDOS DE LOS PROYECTOS

### GRUPO A (COTECMAR) — 16 febrero 2026
| Parámetro | Valor |
|-----------|-------|
| Embarcación | Soundermax |
| MB | Kongsberg EM2040P (pin 6 z-pole, babor) |
| SB | Kongsberg EA440 (estribor, polo único) |
| GNSS | SeaPath 130 + Trimble R10 |
| Motion sensor | MRU 5+ |
| **Offset MRU 5+** | **(0, -0.195, -0.445) — relativo al transductor MB** |
| **Offset GNSS MB** | **(0.35, -0.44, -3.14) — relativo al transductor MB** |
| **Offset GNSS SB** | **(0, 0, -1.53) — 1.20m a línea de agua + 0.33m a transductor** |
| **SVP** | **2 perfiles: 8:30 (6.38m prof) y 12:00 (3.10m prof)** |
| **Tide** | **RLC_BCA del CIOH DIMAR, corrección -0.025m a LAT** |
| **Blancos** | **NO SE ADQUIRIERON** |
| Calado | 0.40m |
| Área | Dársena COTECMAR, Bocagrande |

### GRUPO B (ESCOLLERA) — 30 enero + 16 febrero 2026
| Parámetro | Valor |
|-----------|-------|
| Embarcación | Soundermax / Soundermax VII |
| MB | Kongsberg EM2040P (400 kHz) |
| SB | Kongsberg EA440SP (38+200 kHz) |
| GNSS | Trimble R12i RTK |
| Motion sensor | MRU 5+ |
| **SVP** | **2 perfiles: 8:29 (15m) y 13:44 (15m)** |
| **Tide** | **RLS_BCA del CIOH DIMAR (SPOM/Hydras), corrección -0.025m a LAT** |
| **Blancos** | **SÍ: Boya E1 Verde y E2 Roja (ambas 5.56m)** |
| Área | Escollera Bahía de Cartagena |
| Duración | 2 días (30 enero MB, 16 febrero SB) |

---

## PREGUNTAS PRÁCTICAS POR ESTUDIANTE

---

## GRUPO A (COTECMAR) — Nota: 7.5

### PÉREZ LONDOÑO ROBERTO (Jefe de Campo)

#### PREGUNTA 1: Ubicación del motion sensor y offsets
"En su M2-FOR-065 para multihaz, el MRU 5+ está en offset (0, -0.195, -0.445) relativo al transductor EM2040P. El SeaPath 130 está en (0.35, -0.44, -3.14). Pero en el monohaz, el GNSS está en (0, 0, -1.53) porque usaron un polo único en estribor. ¿Por qué la configuración del multihaz usa montaje USM en pin 6 del z-pole en babor mientras que el monohaz usa polo único en estribor? ¿Qué error de roll introduce esto si la embarcación lista 3° durante un giro?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Configuración MB:** USM (Underwater Sensor Mount) en pin 6 = z-pole de 3.14m. Esto aleja el transductor del casco para evitar burbujas y ruido del motor.
- **Configuración SB:** Polo único en estribor = instalación superficial simple. No requiere profundidad porque el SB no es sensible a burbujas como el MB.
- **Error de roll:** Si la embarcación lista 3° a estribor, el z-pole en babor se mueve en sentido contrario. La corrección de roll del MRU compensa, pero el offset Y de -0.195m significa que el MRU no está exactamente sobre el eje de roll.
- **Cálculo del error:** Error horizontal = offset Y × sin(roll) = 0.195m × sin(3°) ≈ 0.010m = **1cm de error**. Pequeño pero acumulativo.
- **Lo que NO hicieron:** No documentaron por qué eligieron pin 6 (hay 12 posiciones) ni evaluaron si pin 4 o 5 habrían sido mejores para esta dársena.

#### PREGUNTA 2: SVP — Cuántos, dónde y por qué
"Según su M2-FOR-067, tomaron 2 perfiles de SVP: uno a las 8:30 en 6.38m de profundidad y otro a las 12:00 en 3.10m. ¿Por qué el segundo perfil está en agua más somera? ¿Detectaron estratificación térmica entre ambos perfiles? ¿Por qué no tomaron un tercer perfil a las 15:00 cuando la temperatura superficial del agua habría cambiado después de 6 horas de insolación?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Horario 8:30:** Primera SVP antes de iniciar = condición matutina, agua más fría, posiblemente más homogénea.
- **Horario 12:00:** Segunda SVP en agua más somera (3.10m vs 6.38m) = probablemente cerca de la costa o en zona diferente de la dársena.
- **Estratificación:** No documentaron comparación entre perfiles. En febrero (época seca), el Caribe colombiano tiene estratificación térmica débil pero presente.
- **Tercer perfil:** No lo tomaron. La justificación correcta sería: "No fue necesario porque la diferencia entre perfiles fue menor al umbral de significancia para el rango de profundidades del levantamiento." Pero ellos NO evaluaron esto.
- **IHO S-44:** Recomienda SVP cada 4 horas o cuando cambien condiciones. Con 3.5 horas entre perfiles, estuvieron dentro del umbral, pero el cambio de profundidad del perfil sugiere que movieron el equipo sin documentar por qué.

#### PREGUNTA 3: Tide gauge — Distancia y benchmark
"Aplicaron corrección de mareas del mareógrafo RLS del CIOH en Cartagena con corrección de -0.025m a LAT. ¿A qué distancia está el mareógrafo de la dársena COTECMAR? Si es más de 2km, ¿cómo justifican que la corrección es representativa para su área de 200m de ancho? ¿Hicieron verificación vertical con un benchmark local?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Distancia CIOH-COTECMAR:** Aproximadamente 3-4km (COTECMAR Bocagrande vs CIOH en Manga).
- **IHO S-44 §5.2.3:** La estación mareográfica debe estar "dentro del área de levantamiento" o justificarse la extrapolación. A 4km, el gradiente de marea puede ser significativo en bahías complejas.
- **Verificación vertical:** **NO LA HICIERON.** Su M2-FOR-069 dice "NO SE ADQUIRIÓ TOMA DE BLANCOS."
- **Benchmark rápido:** Para verificación vertical rápida:
  1. Identificar un punto fijo en la estructura portuaria (muelle, balaustrada)
  2. Medir elevación con GPS RTK respecto a MSL
  3. Comparar con la reducción de marea en ese instante
  4. Diferencia >0.05m = problema con el datum
- **Su error:** No documentaron verificación independiente del datum vertical. Confiaron ciegamente en el mareógrafo remoto.

---

### RODRÍGUEZ PUENTES NICOLAS (Proceso)

#### PREGUNTA 1: TPU y el sensor mareográfico
"En su cálculo de TPU, usaron error del sensor mareográfico = 0.002m. Pero nunca verificaron que el mareógrafo del CIOH estuviera calibrado. Si el mareógrafo tuviera un error de 0.05m (común en sensores de presión sin mantenimiento), ¿cuánto aumentaría su TPU de 0.241m? ¿Cómo habrían detectado esto en campo sin equipo especializado?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Cálculo:** TPU = √(THU² + TVU²). El TVU incluye el error del mareógrafo.
- **Error actual:** 0.002m (asumido del datasheet del fabricante).
- **Error real potencial:** 0.05m (25× mayor).
- **Nuevo TPU:** √(0.24² + (0.025² + 0.05²)) = √(0.0576 + 0.003125) = √0.0607 ≈ **0.246m** (vs 0.241m actual).
- **Diferencia:** +0.005m = **5mm**. Pequeña pero crítica para Orden Especial.
- **Detección sin equipo:** Comparar la reducción de marea con la elevación GPS del punto de amarre en el muelle. Si el GPS dice +0.50m MSL y la marea dice +0.45m, hay 0.05m de discrepancia.
- **Lo que NO hicieron:** No verificaron independientemente. Solo confiaron en el archivo descargado.

#### PREGUNTA 2: Patch test y check bar
"Su check bar dio 0.99m vs 1.00m nominal — error del 1%. En Caris HIPS, ¿en qué campo específico se aplica esta corrección? Pero el patch test — ¿lo hicieron? Si no, ¿cómo afecta la falta de patch test al error de apuntamiento del swath en aguas de 8.9m de profundidad máxima?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Check bar:** Corrección en Vessel Configuration → Sonar → System Bias = +0.01m.
- **Patch test:** **NO LO HICIERON.** O si lo hicieron, no documentaron resultados.
- **Error sin patch test:** Los offsets angulares (roll, pitch, yaw) entre el MRU 5+ y el transductor EM2040P no están verificados.
- **Efecto en 8.9m:**
  - Error de roll de 0.1° = 8.9m × tan(0.1°) × 2 = **0.031m = 3.1cm** en los bordes del swath
  - Error de pitch de 0.1° = 8.9m × tan(0.1°) = **0.016m = 1.6cm** en lo longitudinal
  - Estos errores se suman al THU horizontal
- **IHO S-44 Orden Especial:** THU ≤ 2m. El patch test es obligatorio para demostrar cumplimiento.
- **Respuesta correcta del estudiante:** "No hicimos patch test documentado porque..." [debe justificar]. Si dice "no fue necesario" = incorrecto, es obligatorio.

#### PREGUNTA 3: Procesamiento CUBE vs superficie real
"Usaron CUBE con resolución 0.1m para el multihaz. Pero en una dársena portuaria con paredes verticales de concreto, CUBE asume superficie continua y suave. ¿Cómo afecta esto la detección de objetos de 1m³ que podrían estar en la base de los muelles? ¿Qué alternativa a CUBE habría sido mejor para este entorno artificial?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **CUBE:** Algoritmo estadístico que assume distribución gaussiana del error. Funciona bien en fondos naturales irregulares.
- **Problema en dársena:** Las paredes verticales de concreto crean ecos múltiples (multipath) y sombras acústicas. CUBE puede interpretar estos artefactos como "fondo real" o suavizarlos.
- **Objetos 1m³:** En la base de muelles, objetos pequeños pueden quedar ocultos en la sombra acústica o confundidos con el eco del muro.
- **Alternativa mejor:**
  - **Módulo "Shoal Detection" de Caris HIPS:** Diseñado específicamente para detectar objetos sobresalientes.
  - **Análisis de amplitud de retrodispersión:** Los objetos metálicos/artificiales tienen firma acústica diferente al sedimento.
  - **Visualización 3D con umbral de profundidad:** Superficies con gradiente >45° = probable estructura artificial.
- **Lo que NO hicieron:** No mencionaron limitaciones de CUBE en entornos artificiales. Solo aplicaron el algoritmo estándar.

---

### TRUJILLO JARAMILLO JULIÁN (Team Member)

#### PREGUNTA 1: Backup de datos y protocolo de almacenamiento
"Según la evaluación, no documentaron protocolo de backup de datos. Durante el procesamiento, trabajaron con archivos KMALL y RAW en Caris HIPS. Si el disco duro de la laptop de procesamiento hubiera fallado a las 18:00 del 16 de febrero, ¿qué copias de seguridad tenían y dónde estaban almacenadas? ¿Cumple esto con IHO S-44 para levantamientos de Orden Especial?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **IHO S-44 §6.3:** "Los datos brutos deben archivarse de manera segura y estar disponibles para posible re-procesamiento."
- **Protocolo estándar:**
  1. Copia en disco duro externo inmediatamente después de cada día de campo
  2. Copia en nube/servidor institucional dentro de 24 horas
  3. Verificación de integridad (checksum MD5/SHA)
- **Lo que documentaron:** "Archivos KMALL y RAW. Estructura carpetas no detallada. Sin protocolo backup."
- **Respuesta esperada:** "No teníamos protocolo formal pero..." [debe explicar qué hicieron realmente]. Si dice "confiamos en el disco de la laptop" = insuficiente.
- **Profesionalismo:** En un proyecto real con DEME, la pérdida de datos brutos invalida el contrato y requiere re-levantamiento a costo del contratista.

#### PREGUNTA 2: Identificación de artefactos
"En su informe de procesamiento, mencionan análisis visual en editores Caris pero sin análisis estadístico. En una dársena artificial con paredes verticales, el multipath produce ecos fantasma que parecen fondo real. ¿Cómo distingue visualmente un eco de multipath de un objeto real en el swath editor? ¿Qué patrón espacial característico tiene el multipath en líneas paralelas?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Multipath visual:** Aparece como líneas rectas o arcos concéntricos que siguen la geometría del muro. No tienen textura de fondo natural.
- **Patrón espacial:** En líneas paralelas, el multipath aparece en la MISMA posición relativa al muro (misma distancia horizontal, misma profundidad aparente). Los objetos reales varían de posición entre líneas.
- **Diferenciación:**
  - **Multipath:** Consistente entre líneas adyacentes, forma regular, profundidad relacionada con la pared
  - **Objeto real:** Variable entre líneas, forma irregular, profundidad independiente de estructuras
- **Herramienta Caris:** Swath Editor con visualización de amplitud (backscatter) ayuda — el multipath tiene amplitud anómala.
- **Lo que NO hicieron:** No documentaron criterios de identificación de artefactos. Solo dijeron "edición visual."

#### PREGUNTA 3: Metadatos IHO S-100
"Sus metadatos son 'nombres de archivo básicos' sin esquema. Según IHO S-100 (que reemplaza S-57), todo producto hidrográfico debe tener metadatos XML con 12 campos obligatorios. Nombren 5 de esos campos que USTEDES deberían haber documentado para que su .csar sea interoperable con el sistema SIG de la Autoridad Marítima de Colombia (Dimar)."

**ARGUMENTOS PARA EL EVALUADOR:**
- **12 campos obligatorios IHO S-100:**
  1. fileIdentifier (UUID único del producto)
  2. title (nombre descriptivo del levantamiento)
  3. abstract (resumen del propósito y alcance)
  4. purpose (uso previsto: navegación, dragado, etc.)
  5. lineage (procesamiento aplicado: CUBE, filtros, etc.)
  6. spatialRepresentation (sistema de coordenadas EPSG)
  7. verticalDatum (LAT, MSL, CD, etc. con justificación)
  8. source (instrumentos utilizados con serie/fabricante)
  9. qualityScope (Orden IHO aplicado: Orden Especial)
  10. dateStamp (fecha de creación del producto)
  11. responsibleParty (nombre del hidrógrafo responsable)
  12. securityConstraints (restricciones de uso: militar, público, etc.)
- **Lo que documentaron:** Solo nombres de archivo tipo "261_Cotecmar_Darsena_HF"
- **Consecuencia:** Dimar no puede integrar su producto al Esquema Cartográfico Nacional sin reprocesamiento completo.

---

### HUERTAS QUINTERO WILMER (Team Member)

#### PREGUNTA 1: Control terrestre y transformaciones
"Usaron UTM-WGS-84 Zona 18N con datum vertical MSL, pero no establecieron control terrestre ni vínculo con la red geodésica nacional. La dársena está dentro de la Base Naval ARC 'Bolívar'. Si el Capitán de Puerto les exige que su carta esté referenciada al datum oficial de Colombia (MAGNA-SIRGAS 2011), ¿cómo harían la transformación sin puntos de control comunes?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **MAGNA-SIRGAS 2011 vs WGS-84:** Diferencia de aproximadamente 0.5-1.0m en Colombia debido a la actualización del marco geodésico.
- **Sin control terrestre:** No hay puntos comunes para calcular la transformación.
- **Solución después del levantamiento:**
  1. Identificar estructuras permanentes en la carta (esquinas de muelles, postes de amarre)
  2. Medir esas estructuras con GPS RTK en MAGNA-SIRGAS
  3. Calcular transformación Helmert 7-parámetros
  4. Aplicar a toda la superficie
- **Pero:** Esto requiere regresar al campo = costo adicional.
- **Respuesta correcta:** "Deberíamos haber establecido control terrestre ANTES del levantamiento. La solución post-hoc es..."
- **Su error:** No planificaron el vínculo geodésico. Asumieron WGS-84 = MAGNA-SIRGAS, lo cual es falso.

#### PREGUNTA 2: Protocolos en áreas protegidas
"La Bahía de Cartagena incluye el ecosistema de manglares de La Boquilla y zonas protegidas. Su M2-FOR-056 dice 'protocolos ambientales' pero lista cero. Si durante el levantamiento su embarcación derrama 2 litros de aceite hidráulico del generador, ¿cuál es el protocolo específico según la Resolución 0264/2019 y quién tiene la autoridad legal para sancionar la infracción?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Resolución 0264/2019:** Establece el Plan Nacional de Contingencias para Derrames de Hidrocarburos.
- **Protocolo inmediato:**
  1. Contener el derrame con barreras absorbentes
  2. Notificar a Corpocaribe dentro de 2 horas
  3. Documentar coordenadas GPS, volumen estimado, condiciones ambientales
  4. Iniciar limpieza con materiales aprobados (NO dispersantes en aguas someras)
- **Autoridad sancionadora:** El Ministerio de Ambiente y Desarrollo Sostenible, a través de la Dirección de Costas y Aguas Internas, con apoyo de Corpocaribe.
- **Sanciones:** Multas de 1-10 SMMLV, suspensión de actividades hasta reparación del daño.
- **Su omisión:** No tenían ni barreras absorbentes ni contactos de Corpocaribe en su plan de contingencia.
- **Respuesta esperada:** "No teníamos protocolo específico, pero deberíamos haber..." [listar elementos]. Si no sabe quién sanciona = desconocimiento grave.

#### PREGUNTA 3: Velocidad de adquisición y cobertura
"Hicieron 20 líneas de multihaz (4889m) y 37 líneas de monohaz (2352m) en un solo día de campo. El monohaz tiene más líneas pero menos metros totales. ¿Cuál fue la velocidad media de adquisición de cada sistema? Si la velocidad del monohaz fue mayor que la recomendada para EA440 en aguas someras, ¿cómo afecta esto a la resolución del eco doble usado para detectar sedimentos?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Velocidad MB:** 4889m ÷ (20 líneas × tiempo por línea). Si asumimos 15 min/línea = 4889 ÷ 300 min = **16.3 m/min = 0.27 m/s = 0.5 nudos**.
- **Velocidad SB:** 2352m ÷ (37 líneas × tiempo). Si 10 min/línea = 2352 ÷ 370 = **6.4 m/min = 0.11 m/s = 0.2 nudos**.
- **Velocidad recomendada EA440:** 2-4 nudos para resolución óptima. A 0.2 nudos = muy lento, posiblemente demasiado lento (problemas de acumulación de datos).
- **Eco doble:** La separación entre ecos de fondo duro y blando depende del pulso. A velocidad muy baja, el haz incide repetidamente en el mismo punto, aumentando la resolución temporal pero no espacial.
- **Problema real:** A 0.2 nudos, la embarcación puede derivar por corriente, creando trazas no rectas que complican la interpretación del eco doble.
- **Lo que documentaron:** Velocidad de embarcación en M2-FOR-070 pero no la relacionaron con la calidad del eco doble.

---

## GRUPO B (ESCOLLERA) — Nota: 8.8

### STEVEN POSADA CIRO (Responsable Área Hidrografía)

#### PREGUNTA 1: Ubicación del motion sensor
"En su M2-FOR-065, el GNSS está en offset (0, 0, -1.53) y el transductor en (0, 2.06, -0.07) — todo en un polo único en estribor. PERO para el multihaz EM2040P usaron la misma configuración básica. El EM2040P requiere un MRU 5+ para corrección de pitch/roll en tiempo real. ¿Dónde estaba físicamente el MRU 5+ en la embarcación Soundermax VII? Si estaba en el mismo polo que el GNSS, ¿qué problema de sincronización temporal introduce la separación de 2.06m en Y entre el MRU y el transductor?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Configuración:** Mismo polo para GNSS + MRU + transductor = instalación simplificada.
- **Offset Y = 2.06m:** El MRU está 2.06m atrás (o adelante) del transducer en el eje longitudinal de la embarcación.
- **Problema de sincronización:** El MRU mide el movimiento en su posición, pero el transducer está 2.06m away. La compensación de movimiento tiene que proyectar las correcciones de actitud a la posición del transducer.
- **Caris HIPS:** Esto se maneja automáticamente si los offsets están correctos. PERO si el MRU no está perfectamente alineado con el eje de la embarcación, hay error residual.
- **Verificación:** Patch test = verifica que la proyección de offsets es correcta. **No documentaron patch test con resultados.**
- **Respuesta esperada:** "El MRU estaba en [posición]. La separación de 2.06m se compensa en Caris mediante..."

#### PREGUNTA 2: SVP — 2 perfiles a 15m
"Tomaron 2 perfiles de SVP a 15 metros de profundidad: uno a las 8:29 y otro a las 13:44. Ambos a la MISMA profundidad. Pero su área de levantamiento tiene fondos entre 0.5m (coronamiento escollera) y 15m (pie de escollera). ¿Por qué no tomaron un perfil en agua más somera cerca del coronamiento donde la estratificación térmica diurna es máxima? ¿Cómo afecta usar un SVP de 15m en agua de 0.5m a la trayectoria del rayo acústico?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **SVP de 15m:** Captura el perfil completo de la columna de agua en la zona más profunda.
- **Pero en agua somera (0.5m):** El SVP de 15m no aplica porque la columna de agua es mucho más delgada. La velocidad del sonido en los primeros 0.5m puede variar significativamente por:
  - Calentamiento superficial diurno
  - Aporte de agua dulce (lluvia, escorrentía)
  - Mezcla por oleaje
- **Error en trayectoria de rayo:** Si usan el SVP de 15m para corregir datos en 0.5m, asumen una columna de agua que no existe. El error angular puede ser de 0.1-0.3°, que en 0.5m de profundidad = **8-25cm de error horizontal** en la posición del punto sondado.
- **Solución correcta:** Tomar SVP adicional en agua somera o extrapolar el perfil superficial.
- **Lo que documentaron:** "Perfil aplicado correctamente" sin mencionar limitaciones en agua somera.

#### PREGUNTA 3: Análisis multi-temporal sin verificación
"Su análisis compara 4 levantamientos (2016, 2020, 2023, 2026). Pero no tomaron muestras de sedimento ni usaron SSS. Sin ground-truth, ¿cómo distinguen entre erosión real de la escollera y simple movilidad sedimentaria estacional? Muestre un ejemplo concreto de su informe donde esta distinción sea ambigua."

**ARGUMENTOS PARA EL EVALUADOR:**
- **Erosión real:** Cambio permanente en estructura de concreto/roca = fondo duro expuesto, bordes afilados, consistente en todas las épocas.
- **Movilidad sedimentaria:** Arena/lodo que se acumula/erosiona estacionalmente = cambios reversibles entre levantamientos.
- **Ejemplo ambiguo:** Zonas donde el fondo cambió -1.6m entre 2023-2026 pero eran zonas de transición escollera-sedimento en levantamientos anteriores.
- **Sin SSS:** No pudieron verificar si el fondo era roca (erosión) o arena (movilidad).
- **Sin muestras:** No pudieron analizar granulometría para confirmar tipo de sedimento.
- **Respuesta esperada:** "Tenemos ambigüedad en [zona específica]. Sin SSS no podemos confirmar, pero inferimos..." [debe reconocer la limitación].

---

### NATALIA MILENA TORRES PIMIENTA (Jefe Sección Levantamientos)

#### PREGUNTA 1: Blancos y verificación de posicionamiento
"En su M2-FOR-069 tomaron 2 blancos: Boya E1 Verde y E2 Roja (ambas a 5.56m). Estas boyas son estructuras flotantes ancladas, NO puntos fijos geodésicos. Si el ancla de la boya se mueve 2m por efecto de corriente o temporal, ¿sigue siendo un blanco válido para verificar el posicionamiento RTK? ¿Qué tipo de blanco deberían haber usado para control absoluto?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Boya flotante:** Se mueve dentro del radio de amarre (típicamente 5-15m dependiendo de la profundidad y longitud de cadena).
- **No es blanco fijo:** La posición varía. Tomarla como blanco de control introduce error en la verificación del posicionamiento.
- **Blanco correcto:**
  - **Estructura fija:** Pilote de muelle, defensa de concreto, reja de desagüe
  - **Punto geodésico conocido:** Monumento de la red de control de Dimar
  - **Punto topográfico:** Señalización terrestre con coordenadas conocidas en MAGNA-SIRGAS
- **Verificación RTK:** Comparar posición medida del blanco fijo vs coordenadas conocidas. Error <0.10m = RTK funcionando correctamente.
- **Su error:** Usaron boyas flotantes porque son visibles y fáciles de detectar, pero NO sirven para control absoluto.
- **Respuesta esperada:** "Reconocemos que las boyas no son ideales, pero fueron lo único disponible. Para control absoluto deberíamos haber..."

#### PREGUNTA 2: Pronósticos DIMAR vs realidad
"Su M2-FOR-066 documenta que esperaron desde el 13 de enero hasta el 30 de enero por condiciones adversas (vientos hasta 22 nudos, oleaje 1.3m). Pero el 30 de enero registraron oleaje de 1.1m durante el levantamiento. El EM2040P tolera máximo 0.5m de oleaje para calidad óptima. ¿Por qué no abortaron o reducieron el swath? ¿Cómo afectó el oleaje de 1.1m a la calidad de datos en los bordes del swath?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Tolerancia EM2040P:** Especificación del fabricante = operación óptima con roll <2°, pitch <1°. Con oleaje 1.1m, el roll puede alcanzar 3-5°.
- **Efecto en swath:**
  - Roll de 3° = pérdida de datos en bordes del swath (outer beams)
  - Cobertura 100% comprometida en zonas de mayor profundidad
  - Datos de bordes tienen mayor TVU
- **Decisiones posibles:**
  - Abortar y esperar mejor ventana
  - Reducir swath al 60% para mantener solo beams centrales
  - Aumentar velocidad de adquisición para completar antes de empeoramiento
- **Lo que documentaron:** "Condiciones aceptables" sin justificar por qué 1.1m fue aceptable vs especificación.
- **Respuesta esperada:** "Evaluamos que 1.1m era manejable porque..." [debe justificar con criterios técnicos, no con impaciencia].

#### PREGUNTA 3: Fusión de datos MB + SB
"Usaron CUBE para el multihaz y probablemente interpolación simple para el monohaz. Pero no fusionaron ambas superficies en una única. Para un diseño de ingeniería de costas, el contratista necesita UNA superficie continua. ¿Cómo habrían fusionado los datos de MB (resolución 0.1m) y SB (resolución 1m) sin crear artefactos en la zona de transición?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Problema de fusión:**
  - MB = alta resolución, cobertura total
  - SB = menor resolución, pero mayor precisión en puntos específicos
  - Zona de transición = donde terminan las líneas MB y empiezan las SB
- **Métodos de fusión:**
  1. **CUBE combinado:** Importar ambos datasets al mismo proyecto CUBE, dejar que el algoritmo pesifique según incertidumbre
  2. **Máscara de transición:** Definir zona de transición (ej. 10m) donde se promedian ambas fuentes
  3. **Prioridad por fuente:** MB primero, SB solo donde no hay MB
- **Artefactos comunes:**
  - Escalón en la transición (diferente nivel medio)
  - Patrón de "cuadriculado" (diferente resolución)
  - Huecos donde ninguna fuente tiene datos
- **Su respuesta:** No fusionaron. Entregaron 2 superficies separadas. Para ingeniería de costas, esto requiere trabajo adicional del contratista.
- **Respuesta esperada:** "No fusionamos por [razón]. La metodología correcta habría sido..."

---

### FRANCISCO JAVIER MURILLO QUINTERO (Jefe de Campo)

#### PREGUNTA 1: Equipo reducido y seguridad
"Dirigió 3 oficiales alumnos + 3 suboficiales hidrógrafos orgánicos. Los suboficiales son de apoyo técnico, no son responsables de decisiones. Durante el levantamiento del 30 de enero con oleaje de 1.1m, si un alumno se mareaba y debía ser evacuado, ¿cómo reorganizaba el equipo para mantener QC sin interrumpir la adquisición? ¿Quién asume la responsabilidad legal si el alumno enfermo cae al agua durante la transferencia?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Seguridad primero:** IHO S-44 §3.3.1 = "La seguridad del personal tiene prioridad sobre la completitud del levantamiento."
- **Reorganización:**
  - Un suboficial conduce la embarcación
  - Un suboficial opera el equipo de adquisición (monitoreo básico)
  - Jefe de Campo coordina evacuación y continúa QC mínimo
- **Responsabilidad legal:**
  - **Jefe de Campo:** Responsable directo por planificación y decisión de continuar o abortar
  - **Institución (Escuela Naval):** Responsable subsidiaria por formación y supervisión
  - **Suboficiales:** Solo responsables de tareas asignadas, no de decisiones estratégicas
- **Lo que documentaron:** "Personal a bordo: 03 oficiales, 03 suboficiales" sin plan de contingencia médica.
- **Respuesta esperada:** "Mi plan de contingencia era..." [debe demostrar que pensó en esto]. Si no tiene plan = falla grave de liderazgo.

#### PREGUNTA 2: RTK float y degradación
"Usaron Trimble R12i RTK. Si la base RTK en tierra perdió comunicación por 2 minutos, ¿cuánto tiempo pueden continuar en 'RTK float' antes de que el error horizontal exceda los 2m permitidos por Orden Especial? ¿Qué hacen con los datos adquiridos durante ese período — los descartan, los marcan como sospechosos, o los usan igual?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **RTK float:** Precisión decimétrica (10-50cm), degradando con el tiempo.
- **Degradación típica:**
  - 0-30s: error <0.5m (aceptable)
  - 30-60s: error 0.5-1.5m (marginal)
  - 60-120s: error >1.5m (fuera de especificación)
- **Con 2 minutos (120s):** Error probable >2m = **FUERA de Orden Especial.**
- **Datos durante float:**
  - **Opción 1:** Descartar = pérdida de cobertura
  - **Opción 2:** Marcar como "sospechosos" = procesar separadamente con mayor TPU
  - **Opción 3:** Usar igual = violación del estándar
- **Mejor práctica:** Marcar en el log de adquisición los tiempos de float, procesar con TPU ajustado, decidir si aceptar o re-levantar.
- **Lo que documentaron:** "RTK funcionando correctamente" — no mencionaron contingencia de float.

#### PREGUNTA 3: Ventana tidal de 2 días
"Trabajaron 30 de enero (MB) y 16 de febrero (SB). ¿Por qué separaron MB y SB en días diferentes? Si la marea en Cartagena tiene rango de 0.4m, ¿cómo aseguraron que el datum vertical fuera consistente entre ambos días si el estado de marea era diferente?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Separación MB/SB:** Posiblemente por disponibilidad de embarcación o personal. Pero no documentaron la razón.
- **Consistencia del datum:**
  - Día 1 (30 ene): Marea en LAT -0.025m (corrección aplicada)
  - Día 2 (16 feb): Marea en LAT -0.025m (misma corrección)
  - **PERO:** El archivo de mareas es diferente para cada día. ¿Usaron el archivo correcto para cada día?
- **Verificación:** Comparar la reducción de marea en un punto común (ej. boya E1) en ambos días. Si la profundidad reducida difiere >0.10m = problema con el datum.
- **Lo que documentaron:** Usaron archivos RLS_BCA_20260101_20260228_MSL_LAT_HL.tid y RLS_BCA_20260101_20260228_MSL_LAT_UTC.tid. Esto cubre ambos días.
- **Pregunta trampa:** ¿Verificaron que la corrección de -0.025m era la MISMA para ambos días? En realidad, la corrección LAT-MSL varía mensualmente.

---

## ASIGNACIÓN ESTRATÉGICA DE PREGUNTAS

| Estudiante | Debilidad Principal | Pregunta más efectiva |
|-----------|---------------------|----------------------|
| **Grupo A - Pérez Londoño** | Sin plan de contingencia, roles mal definidos | Pregunta 1 (offsets + error de roll) + seguimiento de seguridad |
| **Grupo A - Rodríguez Puentes** | Patch test sin resultados, bias no corregido | Pregunta 2 (patch test + error de apuntamiento) |
| **Grupo A - Trujillo Jaramillo** | Sin protocolo backup, metadatos básicos | Pregunta 1 (backup) + seguimiento de metadatos IHO |
| **Grupo A - Huertas Quintero** | Sin control terrestre, sin protocolos ambientales | Pregunta 1 (MAGNA-SIRGAS) + seguimiento de derrame |
| **Grupo B - Posada Ciro** | Sin ground-truth, tecnologías planificadas no usadas | Pregunta 3 (erosión vs movilidad) — más difícil |
| **Grupo B - Torres Pimienta** | Puntajes perfectos, oral incompleto | Pregunta 1 (blancos flotantes vs fijos) — expone debilidad oculta |
| **Grupo B - Murillo Quintero** | Sin problemas documentados, todo "perfecto" | Pregunta 1 (evacuación + responsabilidad legal) — rompe ilusión de perfección |

---

## TÉCNICAS DE EXAMEN ORAL RECOMENDADAS

1. **Empezar con pregunta directa:** "Muestreme en su M2-FOR-065 dónde estaba el MRU 5+"
2. **Esperar que muestre el documento:** Si no lo tiene a mano = no revisó su propio trabajo
3. **Seguimiento inmediato:** "Si el MRU está aquí, ¿qué pasa si la embarcación lista 3°?"
4. **Presionar en la justificación, no en el número:** "¿Por qué eligió 2 perfiles y no 3?"
5. **Usar comparación entre grupos:** "El Grupo B tomó blancos, ustedes no. ¿Por qué?"
6. **Pregunta de ética profesional:** "Si el Capitán de Puerto exige MAGNA-SIRGAS y ustedes no tienen control terrestre, ¿qué le dice al cliente?"
7. **Trampa temporal:** "Es 15:00 del día de campo. El generador falla. ¿Qué hace AHORA?"

---

*Documento preparado el 26 de mayo de 2026, 23:00*
*Evaluador: Capitán de Coberta Álvarez Orduz Omar Sebastián*
*Asistente: Alice (AI Mission Recorder)*
