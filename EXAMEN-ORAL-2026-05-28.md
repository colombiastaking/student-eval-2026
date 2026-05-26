# EXAMEN ORAL — HIDROGRAFÍA CATEGORÍA A
## CMFP S5A — Escuela Naval de Cadetes "Almirante Padilla"

**Fecha del examen:** 28 de mayo de 2026
**Evaluador:** Capitán de Coberta Álvarez Orduz Omar Sebastián
**Curso:** Hidrográfica Categoría A

---

## GRUPO A (COTECMAR) — Nota: 7.5/10
**Proyecto:** Levantamiento Multidisciplinario — Dársena COTECMAR, Bocagrande

---

### PÉREZ LONDOÑO ROBERTO (Jefe de Campo)

#### PREGUNTA 1: Seguridad operativa y contingencia
"Durante la adquisición del 16 de febrero, tu generador se sobrecalentó y el motor de estribor falló. Como Jefe de Campo, no documentaste un plan de contingencia. Explícame el árbol de decisiones que aplicarías en ese momento: ¿abortas la operación, continuas con potencia reducida, o modificas los parámetros de adquisición? ¿Qué principio específico de IHO S-44 justifica tu elección?"

**ARGUMENTOS PARA EL EVALUADOR:**
- NO debe abortar inmediatamente — una dársena portuaria tiene ventanas operativas limitadas y costos de embarcación asociados.
- **Primera evaluación:** ¿Qué equipo queda operativo? Si el multihaz (EM2040P) depende del generador para procesamiento en tiempo real, pero el monohaz (EA440) usa menos energía, podría priorizar la adquisición SB.
- **Modificación de parámetros:** Reducir el swath width del multihaz para disminuir la carga computacional, o cambiar a modo de adquisición más simple (raw data sin procesamiento en tiempo real).
- **Principio IHO S-44:** Sección 3.3.1 — "La seguridad de la navegación y del personal tiene prioridad sobre la completitud del levantamiento." Si la falla compromete la seguridad de la embarcación (maniobrabilidad reducida en área con tráfico), se debe abortar. Si solo afecta la calidad de los datos, se adapta la metodología.
- **Documentación:** Cualquier decisión debe registrarse en M2-FOR-049 (Diario de Campo) con timestamp y justificación. El grupo no lo hizo.

#### PREGUNTA 2: Control terrestre y datum vertical
"Usaron WGS-84 UTM Zona 18N con datum vertical MSL referenciado al mareógrafo de DIMAR. Pero sus instrucciones dicen 'Lowest Astronomical Tide (LAT)' en sección 8.2.2, y luego aplicaron MSL en el procesamiento. Para un buque Panamax con calado de 12.5m acercándose a LAT, ¿su carta es segura o insegura? Calcula el error del margen de seguridad."

**ARGUMENTOS PARA EL EVALUADOR:**
- **MSL vs LAT:** En Cartagena, el rango tidal es aproximadamente 0.4m. LAT = nivel más bajo teórico = MSL - 0.2m (aproximado, depende de armónicos locales).
- **Si la carta usa MSL y el buque navega a LAT:** Las profundidades cartografiadas son MÁS PROFUNDAS que la realidad en LAT. Ejemplo: carta dice -10.0m MSL, pero en LAT es -10.2m (más profundo).
- **Resultado:** La carta es CONSERVADORA (más segura) porque muestra menos profundidad que la disponible en LAT.
- **PERO:** Si el puerto diseña dragado a -16.5m MSL y la carta usa MSL, el dragado real será más profundo en LAT. Esto cuesta MILLONES en dragado innecesario.
- **Su error:** No documentar la transformación MSL→LAT ni justificar por qué usaron MSL en vez de LAT para diseño portuario.

#### PREGUNTA 3: Roles y responsabilidades
"Usted se definió como Jefe de Campo, pero nunca definió los roles de Trujillo o Huertas. Bajo normativa naval colombiana, ¿quién es legalmente responsable si un miembro sin rol definido causa daño a equipos — usted como Jefe, o el individuo no definido?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Responsabilidad del Jefe de Campo:** Como líder designado, tiene la obligación de definir roles y responsabilidades de todo el equipo antes de iniciar operaciones.
- **Normativa:** La omisión de definir roles no exime al Jefe de Campo de responsabilidad. Es negligencia en planificación.
- **Documentación:** M2-FOR-056 debe incluir matriz de responsabilidades. Solo 2 de 4 miembros tenían roles claros.
- **Consecuencia práctica:** En un contrato real con DEME/ITB, esto generaría disputas legales sobre responsabilidad en caso de daños.

---

### RODRÍGUEZ PUENTES NICOLAS (Proceso)

#### PREGUNTA 1: Calibración y bias sistemático
"Documentaron un check bar de 0.99m vs 1.00m nominal. En Caris HIPS existe el campo 'System Bias' en el archivo de embarcación. ¿Lo aplicaron? Si sí, muéstrame el valor. Si no, explique por qué dejar un error sistemático del 1% es aceptable para un cliente portuario que diseña maniobras de buques."

**ARGUMENTOS PARA EL EVALUADOR:**
- **NO debe ser aceptable.** Un bias del 1% en 10m de profundidad = 10cm. En maniobras de buques con calado crítico, 10cm puede ser la diferencia entre tocar fondo o no.
- **En Caris HIPS:** System Bias se aplica en Vessel Configuration → Sonar → Calibration. Valor típico: -0.01m (si mide 0.99m en vez de 1.00m, el bias es +0.01m para corregir).
- **IHO S-44 Orden Especial:** TVU requerido = ±0.25m para profundidades <40m. Un bias de 0.01m es pequeño vs TVU, pero **acumulativo** con otros errores (SVP, mareas, GPS).
- **Profesionalismo:** No corregir bias sistemático demuestra falta de rigor QC. Caris tiene herramientas específicas para esto — no usarlas es negligencia técnica.

#### PREGUNTA 2: Patch test sin resultados
"Mencionan patch test en su documentación pero no entregan resultados. Sin patch test documentado, ¿cómo demuestran que sus datos multihaz cumplen con el THU requerido por IHO S-44 Orden Especial?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Patch test obligatorio:** Es el único método para determinar offsets angulares (roll, pitch, yaw) entre el sistema de referencia de la embarcación y el sonar.
- **Sin patch test:** No se pueden aplicar correcciones de apuntamiento (steering angles), lo que afecta directamente el THU horizontal.
- **THU requerido:** IHO S-44 Orden Especial exige THU ≤ 2m para levantamientos de seguridad de navegación. Sin patch test, el THU es desconocido.
- **Consecuencia:** Los datos pueden estar dentro o fuera de tolerancia — no hay forma de demostrarlo. Es una violación del estándar.

#### PREGUNTA 3: TPU sin comparar con IHO
"Su cálculo de TPU muestra 0.241m de incertidumbre total. Pero IHO S-44 Orden Especial les exige comparar contra los límites específicos de la ORDEN, no solo calcular el TPU de su sistema. ¿A qué profundidad su TPU de 0.241m viola Orden Especial si el umbral de detección de objetos es 1m³?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **IHO S-44 §4.2.3:** Orden Especial requiere que TVU ≤ a + (b × profundidad), donde a = 0.5m, b = 0.013.
- **Cálculo:** Para TVU = 0.241m, resolviendo para profundidad: 0.241 = 0.5 + (0.013 × d) → Esto da profundidad NEGATIVA, lo que indica que 0.241m está DENTRO de tolerancia para todas las profundidades.
- **PERO:** El TPU de 0.241m NO considera el THU horizontal. Para un objeto de 1m³, el error horizontal proyectado a la profundidad del objeto afecta la detección.
- **Profundidad crítica:** Aproximadamente 15-20m, donde la combinación de THU + TVU hace que el objeto de 1m³ quede fuera de la detección confiable.

---

### TRUJILLO JARAMILLO JULIÁN (Team Member)

#### PREGUNTA 1: Trazabilidad documental
"Entregaron 11 de 18 formularios requeridos. Faltan: M2-FOR-049, 066, 071, 073, 075, 076. El cliente DEME exige trazabilidad total bajo ISO 9001. ¿Qué formulario faltante contiene los datos de consumo de combustible que prueban que su embarcación operó dentro de parámetros charter — y por qué su ausencia invalida todo su log de adquisición con marcas de tiempo?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **M2-FOR-049 = Diario de Campo / Log de Operaciones.** Este formulario registra: horas de motor, consumo de combustible, coordenadas GPS de inicio/fin de cada línea, condiciones meteorológicas, problemas operativos.
- **Sin M2-FOR-049:** No hay evidencia de que la embarcación operó continuamente durante las líneas documentadas. ¿Estuvo anclada 2 horas y no adquirió? ¿Cambió de tripulación?
- **ISO 9001 / Trazabilidad:** Requiere "registros demostrables de la realización de actividades." Sin log de operaciones, los timestamps en los archivos de datos no tienen contexto operativo.
- **Específicamente combustible:** Si el charter era por 8 horas y el consumo muestra 12 horas de motor, hay inconsistencia. Si no hay registro de combustible, no se puede validar el tiempo de adquisición.

#### PREGUNTA 2: Metadatos y estándares
"Sus metadatos son 'nombres de archivo básicos' sin esquema. Si le doy un archivo .KMALL crudo de su levantamiento y una superficie .csar procesada, nombren cinco campos de metadatos que deben vincularlos para cumplimiento IHO S-100. ¿Cuáles de estos cinco documentaron realmente?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Cinco campos obligatorios:**
  1. **Identificador de levantamiento** (survey ID)
  2. **Fecha/hora de adquisición** (ISO 8601)
  3. **Sistema de coordenadas** (EPSG code, e.g., 32618 para UTM 18N)
  4. **Datum vertical** (MSL, LAT, etc.)
  5. **Parámetros de sonar** (frecuencia, ángulo de apertura, resolución)
- **Lo que documentaron:** Solo nombres de archivo con fecha básica. No hay esquema XML/ISO 19115.
- **Consecuencia:** Los datos no son interoperables con otros sistemas SIG. Un cliente como DEME no puede integrarlos sin reprocesamiento.

#### PREGUNTA 3: Artefactos y análisis estadístico
"Su análisis de artefactos es visual en editores Caris, sin análisis estadístico. Un operador visual puede detectar artefactos obvios, pero ¿qué tipo de artefacto específico del EM2040P en aguas someras de puerto se detecta SOLO con análisis estadístico de series temporales?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Artefacto: Multipath en ecos de superficie.** En aguas someras (<10m) con paredes verticales (dársena), los ecos de superficie rebotan en paredes y llegan al transductor con retardo.
- **Visualmente:** Aparecen como picos aislados que pueden parecer datos válidos.
- **Estadísticamente:** El análisis de autocorrelación temporal muestra patrones periódicos consistentes con el tiempo de viaje pared-transductor.
- **Solución:** Filtro de mediana móvil con ventana temporal + detección de picos con amplitud anómala. Solo detectable con análisis estadístico, no visual.

---

### HUERTAS QUINTERO WILMER (Team Member)

#### PREGUNTA 1: Protocolos ambientales
"La Bahía de Cartagena incluye el ecosistema Varadero y el área protegida Islas del Rosario. Su M2-FOR-056 dice 'protocolos ambientales' pero lista cero. Si se encuentra un fragmento de coral en su traza de eco del monohaz, ¿cuál es el protocolo específico bajo Resolución 0264/2019 — y quién tiene autoridad legal para autorizar la continuación del levantamiento?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Resolución 0264/2019:** Establece el Sistema Nacional de Áreas Protegidas (SINAP). Requiere informe de hallazgo a Parques Nacionales dentro de 48 horas.
- **Protocolo:** Detener operaciones, fotografiar ubicación exacta (GPS), notificar a autoridad ambiental (Corpocaribe o Parques Nacionales), esperar autorización.
- **Autoridad legal:** El Ministerio de Ambiente y Desarrollo Sostenible, a través de Parques Nacionales Naturales de Colombia, tiene autoridad exclusiva sobre áreas protegidas.
- **Su omisión:** No documentar protocolos demuestra desconocimiento del marco legal ambiental, crítico para proyectos en zonas protegidas.

#### PREGUNTA 2: Corrección de mareas
"Usaron el archivo RLC_BCA para corrección de mareas, pero no documentaron la distancia al mareógrafo ni la validación. Si el mareógrafo está a 5km de su área de levantamiento, ¿cómo afecta la variación espacial de la marea a su datum vertical en una dársena de 200m de ancho?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Variación espacial:** En una bahía semi-cerrada como Cartagena, la marea tiene gradiente espacial. A 5km de distancia, la diferencia de nivel puede ser 2-5cm.
- **Efecto en datum:** Si no se documenta la distancia al mareógrafo, el cliente no puede evaluar si la corrección es representativa.
- **IHO S-44:** Requiere que la estación mareográfica esté "dentro del área de levantamiento" o se justifique la extrapolación.
- **Solución correcta:** Instalar mareógrafo temporal en el sitio o documentar el gradiente con modelos hidrodinámicos.

#### PREGUNTA 3: Control terrestre GNSS
"No establecieron control terrestre con GNSS. Para una dársena de 200m de ancho, ¿a qué distancia máxima de la costa puede operar un RTK con base en tierra antes de que el error horizontal exceda su THU documentado de 0.24m?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Error RTK:** El error horizontal RTK típico es 1cm + 1ppm (parte por millón) de la distancia a la base.
- **Cálculo:** Para THU = 0.24m (24cm), resolviendo: 24cm = 1cm + (1 × 10⁻⁶ × distancia) → distancia ≈ 23km.
- **PERO:** Esto es error instrumental. En práctica, hay interferencias (edificios, vegetación, multipath) que reducen significativamente este rango.
- **Rango práctico:** 5-10km en entorno urbano/portuario. Su dársena de 200m está bien dentro de este rango.
- **PREGUNTA TRAMPA:** El verdadero problema no es la distancia, sino la **ausencia de control terrestre independiente** para validar el RTK.

---

## GRUPO B (ESCOLLERA) — Nota: 8.8/10
**Proyecto:** Levantamiento Hidrográfico de la Escollera — Bahía de Cartagena

---

### STEVEN POSADA CIRO (Responsable Área Hidrografía)

#### PREGUNTA 1: Análisis multi-temporal sin ground-truth
"Su análisis multi-temporal (2016-2026) muestra tendencias de erosión. Pero planificaron SSS y LiDAR y no los usaron. Un side-scan sonar habría detectado transiciones de fondo duro vs blando. Sin esta verdad de campo, ¿cómo distingue entre erosión real del lecho y movilidad sedimentaria estacional en su comparación de 4 levantamientos?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Debe reconocer:** Sin SSS, no tiene ground-truth de composición del fondo.
- **Diferenciación:**
  - **Erosión real:** Cambio permanente de profundidad en áreas de fondo duro (roca, concreto) — detectable por consistencia en múltiples levantamientos.
  - **Movilidad sedimentaria:** Cambios estacionales en zonas de fondo blando (arena, lodo) — varían entre levantamientos.
- **Su análisis:** Solo usa datos batimétricos (profundidad). No tiene clasificación de fondo.
- **¿Cómo debería haberlo hecho?**
  - Usar SSS para mapear extensión de fondo duro/blando
  - Correlacionar zonas de cambio con tipo de fondo
  - Si cambios ocurren solo en zonas blandas = movilidad sedimentaria
  - Si cambios ocurren en zonas duras = erosión real
- **Profesionalismo:** Omitir SSS (que estaba planificado) sin justificar es una omisión técnica grave.

#### PREGUNTA 2: Volumetría para dragado
"Su informe de 53 páginas menciona 'volumetría' pero no la calcula. Para una escollera de 980m con profundidad de diseño -15.38m MSL, si su levantamiento muestra -14.8m en la zona del pie, ¿cuál es el volumen de sobre-dragado requerido — y su clasificación Orden Especial ¿justifica esa precisión para certificación de pagos?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Sobre-dragado:** -14.8m medido vs -15.38m diseño = 0.58m de material adicional que debe removerse.
- **Volumen aproximado:** 980m × ancho promedio zona del pie (estimado 20m) × 0.58m = 11,368 m³.
- **Orden Especial y certificación:** Sí justifica. Orden Especial permite ±0.25m TVU en profundidades <40m. El sobre-dragado de 0.58m es 2.3× el TVU, lo que es conservador y aceptable.
- **PERO:** Para certificación de pagos, el contrato de dragado requiere volumetría DETALLADA por secciones transversales, no estimación.
- **Su omisión:** No calcular volumetría por secciones demuestra que no entienden la aplicación práctica de sus datos para ingeniería de costas.

#### PREGUNTA 3: Tecnologías auxiliares
"Planificaron SSS, LiDAR y muestras de sedimento, pero no ejecutaron ninguna. Para un diseño de protección de escollera con 30 años de historia, ¿qué información crítica para el cálculo de estabilidad del revestimiento perdiste al omitir estas tecnologías?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **SSS:** Detecta objetos sumergidos (anclas, tuberías, restos) que pueden dañar el revestimiento durante construcción.
- **LiDAR:** Mapea exactamente la línea de costa y escarpes sobre el nivel del agua, crítico para el diseño del coronamiento.
- **Muestras de sedimento:** Determinan granulometría del fondo, que afecta la selección de material de filtro y capa de protección.
- **Información crítica perdida:**
  - Pendiente del talud subacuático (para estabilidad)
  - Tipo de suelo de cimentación (para asentamiento)
  - Obstáculos sumergidos (para excavación segura)
- **Consecuencia:** El diseñador debe asumir condiciones conservadoras, aumentando costos en 15-20%.

---

### NATALIA MILENA TORRES PIMIENTA (Jefe Sección Levantamientos)

#### PREGUNTA 1: Presentación oral incompleta
"Logró 100% de formularios completados (20/20), documentación excepcional, y puntajes técnicos altos. Sin embargo su T76 (presentación oral) es 5.0 — incompleto. ¿Esto se debe a que priorizó entregables escritos sobre habilidades de comunicación, o porque el componente oral revela vacíos no visibles en documentos? ¿Qué vacío podría ser?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Es una trampa intencional.** Los puntajes perfectos en escritos pero oral incompleto es **sospechoso**.
- **Posibilidad 1 (priorización):** Foco excesivo en documentación técnica, descuidando habilidades de presentación. Común en perfiles analíticos.
- **Posibilidad 2 (vacíos ocultos):** El oral revela comprensión vs. memorización. Puede escribir bien pero no **defender** su trabajo.
- **Vacíos potenciales que el oral revelaría:**
  - No entiende por qué eligió CUBE vs otros métodos de interpolación
  - No puede explicar la selección de parámetros del EM2040P en tiempo real
  - No sabe responder a "¿qué haría diferente?"
- **Como evaluador:** La discrepancia escritos/oral es una bandera roja. Puede indicar:
  - Trabajo grupal desigual (ella escribió, otros hicieron campo)
  - Uso de plantillas sin comprensión profunda
  - Falta de preparación para comunicación técnica
- **Recomendación:** En el oral, presionar en la **justificación de decisiones técnicas**, no en los resultados.

#### PREGUNTA 2: Pronósticos meteorológicos
"Su M2-FOR-056 cita pronósticos DIMAR para ambos días de levantamiento. Pero los pronósticos meteorológicos tienen incertidumbre temporal y espacial. ¿Cuál fue el intervalo de confianza del pronóstico (en horas y km) para su ventana específica de levantamiento — y a qué umbral habría abortado la adquisición del primer día?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Intervalo de confianza DIMAR:** Los pronósticos de altura de ola del SIPSEM tienen resolución espacial de ~10km y temporal de 3 horas.
- **Para su escollera:** A 980m de longitud, la resolución de 10km es suficiente (más fina que el área).
- **Umbral de aborto:**
  - **Multihaz EM2040P:** Altura de ola >0.5m causa pérdida de datos en bordes del swath (roll de embarcación).
  - **Monohaz EA440SP:** Tolera hasta 1.0m por ser punto a punto.
- **Si pronóstico muestra ola >0.5m para las 4 horas de ventana:** Abortar multihaz, continuar solo con monohaz o reprogramar.
- **Su documentación:** No menciona umbrales específicos de aborto. Dice "plan B definido" pero no lo detalla.

#### PREGUNTA 3: Correlación eventos climáticos
"Su análisis muestra datos 2016-2023-2026. El intervalo 2020-2023 muestra erosión acelerada. No correlaciona esto con ningún evento meteorológico específico. ¿No hubo evento, u omitió el frente frío de enero 2023 que causó alturas de ola anómalas en Cartagena? ¿Cómo verificaría esto ahora?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Evento real:** Enero 2023 tuvo un frente frío ("invierno") con olas de hasta 2.5m en Cartagena (DIMAR reportó alturas significantes anómalas).
- **Efecto en escollera:** Olas de 2.5m exceden la altura de diseño típica (1.5-2.0m) para escolleras de protección en Bahía de Cartagena.
- **Omisión grave:** No correlacionar la erosión acelerada con eventos extremos invalida la interpretación. Puede atribuirse a "tendencia natural" cuando fue evento puntual.
- **Verificación ahora:**
  1. Consultar registros DIMAR de enero 2023 para alturas de ola
  2. Comparar con umbrales de diseño de la escollera
  3. Revisar fotografías aéreas/satélite post-evento
  4. Entrevistar a operadores portuarios sobre daños reportados
- **Consecuencia:** Si no identifica eventos extremos, el diseño de mantenimiento subestima el riesgo.

---

### FRANCISCO JAVIER MURILLO QUINTERO (Jefe de Campo)

#### PREGUNTA 1: Equipo reducido y QC
"Dirigió un equipo de 3 personas versus 4 estándar. Su documentación no aborda la distribución de carga de trabajo. Durante la adquisición del 16 de febrero, si un miembro del equipo se hubiera incapacitado, ¿podría continuar con 2 personas manteniendo los requisitos de QC de IHO S-44? ¿Qué paso específico de QC eliminaría primero, y por qué?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Con 2 personas:** Posible pero riesgoso. IHO S-44 no especifica tamaño de equipo, pero sí requiere que QC no se comprometa.
- **Roles mínimos indispensables:**
  1. **Operador de embarcación** (navegación, seguridad)
  2. **Operador de adquisición** (monitoreo de datos, QC en tiempo real)
- **Con 2 personas:** Uno maneja embarcación + monitorea datos; el otro opera equipos + QC básico. **No hay redundancia.**
- **QC que se eliminaría PRIMERO:** Verificación cruzada de datos en tiempo real (un operador no puede monitorear multihaz + monohaz + navegación simultáneamente).
- **QC que NUNCA se elimina:** Patch test, check bar, SVP — estos son pre-operacionales y no requieren personal extra.
- **Su documentación:** No menciona contingencia de personal. Esto es una falla de planificación.
- **Realidad:** 3 personas para 2 días de campo con multihaz + monohaz es carga alta. La ausencia de plan de contingencia refleja optimismo no realista.

#### PREGUNTA 2: RTK y degradación de señal
"Su equipo usó Trimble R12i RTK y logró excelentes resultados. Pero RTK requiere operación continua de la estación base. Si su base hubiera tenido falla de energía a mitad del levantamiento, ¿cuál es la duración máxima que puede continuar con 'RTK float' antes de que la incertidumbre horizontal exceda los límites de Orden Especial? Muestre la curva de degradación."

**ARGUMENTOS PARA EL EVALUADOR:**
- **RTK float vs RTK fixed:**
  - **Fixed:** Precisión 1-2cm (centimétrica)
  - **Float:** Precisión 10-50cm (decimétrica), degradando con el tiempo
- **Degradación:** El receptor pierde la solución ambigua del ciclo de portadora. Cada segundo en float aumenta la incertidumbre.
- **Tiempo crítico:** Para Orden Especial (THU ≤ 2m), el float tolera aproximadamente 30-60 segundos antes de que la acumulación de error exceda 2m.
- **Curva aproximada:**
  - 0-10s: error <0.5m
  - 10-30s: error 0.5-1.5m
  - 30-60s: error 1.5-2.0m (límite)
  - >60s: error >2m (fuera de especificación)
- **Acción correcta:** Si float >30s, detener adquisición y reestablecer base, o cambiar a modo de navegación visual con waypoints pre-programados.
- **Su documentación:** No menciona protocolo para pérdida de RTK fixed.

#### PREGUNTA 3: Ventana tidal y eficiencia
"Tuvieron solo 2 días en campo. Día 1: multihaz. Día 2: monohaz. Su M2-FOR-058 muestra 100% de cumplimiento cada día. Para un rango tidal de 0.4m en Cartagena, ¿consideraron restricciones de ventana tidal en su planificación de líneas? ¿En qué estado tidal iniciaron cada día, y cómo afectó esto su eficiencia de adquisición monohaz vs multihaz?"

**ARGUMENTOS PARA EL EVALUADOR:**
- **Rango tidal Cartagena:** 0.3-0.4m (micro-mareas).
- **Efecto en levantamiento:**
  - **Multihaz:** Menos sensible a mareas porque opera en tiempo real con corrección de heave. Pero el calado de la embarcación varía, afectando el offset Z del transductor.
  - **Monohaz:** Más sensible porque la reducción de sondas usa tabla de mareas fija. Si la marea cambia durante la línea, la corrección es inconsistente.
- **Ventana óptima:** Operar en pleamar o bajamar estables (marea "muerta"), evitando las horas de máximo flujo.
- **Su documentación:** No menciona estado tidal en el cronograma. Dice "06:00 inicio" sin especificar si es bajamar o pleamar.
- **Eficiencia:** Si iniciaron en flujo máximo, la corrección de marea era menos precisa para el monohaz, requiriendo más líneas de verificación.
- **PREGUNTA CLAVE:** ¿Ajustaron la velocidad de adquisición según el estado tidal? Probablemente no, ya que no documentaron esta variable.

---

## NOTAS PARA EL EVALUADOR

### Técnicas de examen oral recomendadas:
1. **Escuchar primero, corregir después:** Permita que el estudiante desarrolle su respuesta completa antes de interrumpir.
2. **Preguntas de seguimiento:** Cada pregunta principal tiene 2-3 preguntas de profundidad preparadas.
3. **Presionar en la justificación, no en el resultado:** "¿Por qué eligió X?" es más revelador que "¿Cuál es X?"
4. **Documentar respuestas:** Use la columna "Observaciones del Evaluador" para notas en tiempo real.

### Criterios de calificación oral:
- **9-10:** Respuesta completa con justificación técnica, menciona normativa, propone alternativas.
- **7-8:** Respuesta correcta pero superficial, falta profundidad en justificación.
- **5-6:** Respuesta parcial, evade la pregunta, o muestra desconocimiento del estándar.
- **3-4:** Respuesta incorrecta o irrelevante, demuestra falta de comprensión fundamental.
- **1-2:** No responde o admite desconocimiento total.

---

*Documento preparado el 26 de mayo de 2026*
*Evaluador: Capitán de Coberta Álvarez Orduz Omar Sebastián*
*Asistente: Alice (AI Mission Recorder)*
