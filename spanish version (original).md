# Cybersecurity Risk Assessment (Real case study)

## Introducción

*El nombre de la organización ha sido modificado por motivos de confidencialidad. Este documento corresponde a un caso de estudio real realizado en un entorno corporativo, y los análisis, hallazgos y recomendaciones se basan en información obtenida de dicho entorno.*

BioTerra es una industria productora de biocombustibles, principalmente etanol, del cual derivan subproductos como burlanda y aceite. Complementariamente, opera dos plantas de biogás alimentadas por los desechos del proceso productivo. Todo ello en un entorno 100% On-Premise donde la convergencia IT/OT es el eje del negocio, y donde garantizar la continuidad operativa y la integridad de los datos es el objetivo central de la estrategia de ciberseguridad.

## Perfil Organizacional — Activos Críticos

### Capital Humano y Endpoints

- 300 empleados en total

- 280 equipos informáticos

- Alta densidad de dispositivos móviles (smartphones personales y corporativos, ratio superior a 1:1)

### Infraestructura de Red

- Doble anillo de fibra óptica para segmentación física de tráfico

- Red IT (Corporativa): Active Directory + Fortinet. Incluye redes inalámbricas para invitados y corporativos, acceso cableado para invitados con autenticación vía RADIUS (802.1X)

- Red OT (Automatismo): switching HP, aislada de internet salvo tres puntos críticos de convergencia IT/OT

- Centro de Datos: 8 servidores físicos (4 IT / 4 OT). La infraestructura es 100% On-Premise, con una única excepción: el backup diario que se replica en Microsoft Azure como copia offsite dentro de la estrategia de respaldo en tres medios

### Estructura y Gobernanza IT

- Nivel Estratégico: Junta Directiva (accionistas y socios) — define inversiones y visión

- Nivel Ejecutivo: CEO → Gerencia Administrativa

- Nivel Operativo:

  - 1 Líder de IT (que reporta a Gerencia Administrativa)

  - 3 asistentes especializados: Desarrollo de Aplicaciones, Infraestructura y Ciberseguridad

## Madurez y Estrategia de Ciberseguridad

### Contexto de Inversión (2023–2026)

Tras la ola de incidentes de ransomware en el sector agroindustrial regional argentino, BioTerra inició un plan de inversión sostenido. La Junta Directiva reconoció que el riesgo de interrupción de planta (OT) supera con creces el costo de prevención.

### Modelo de Co-gestión

BioTerra opera con un asistente interno de Ciberseguridad y una consultoría tercerizada especializada, que provee:

- Asesoría estratégica alineada con NIST

- Implementación de EDR y gestión de firewalls Fortinet

- Monitoreo continuo y soporte técnico avanzado para los 4 servidores IT

- SOC monitoreado 24/7

### Esquema de Evaluación y Hoja de Ruta

- Continuar el monitoreo IT (85% integrado con Fortinet: 2 FortiGates en HA, EDR en servidores y workstations, MFA, SOC tercerizado)

- Extender visibilidad a la red OT, especialmente en los 3 nodos críticos de convergencia IT/OT

- Implementar herramientas de evaluación periódica de vulnerabilidades, prioritariamente en OT

- Ejercicios mensuales de phishing y ransomware segmentados por perfil; métricas de clics y reportes. Red team previsto con consultores externos en 2 años

- Pentesting planificado para 2027 (redes IT, OT y nodos de convergencia)

## Concientización

### Estado Actual

A fines de 2025, BioTerra lanzó un programa de Security Awareness con campañas de simulación de phishing y ransomware para evaluar la respuesta del personal. El programa continúa hasta fines de 2026 y se ejecuta mediante la alianza con Telecom, cuyas herramientas de capacitación están bonificadas íntegramente en un abono vigente. Los resultados iniciales son favorables.

### Objetivo y Alcance

Reducir el riesgo en el factor humano para proteger la continuidad operativa y la integridad de los datos. El plan abarca la totalidad del personal de BioTerra.

### Propuestas de Contenido

- **Casos reales de referencia:** Análisis del caso de ransomware en la empresa AGD trazando paralelismos con BioTerra.

- **Confidencialidad:** Herramientas para proteger datos personales y corporativos.

- **Gestión de credenciales:** Complejidad, unicidad, rotación, MFA y uso de gestores de contraseñas.

- **Campañas por perfil:** Junta Directiva (whaling/spear phishing), personal administrativo (correo y datos internos), operarios OT (dispositivos externos y equipos no autorizados).

- **Identificación de amenazas:** Ransomware y malware en general, transversal a todos los perfiles.

### Metodología

- **Capacitación inicial anual:** Clase presencial para todo el personal (incluye nuevos ingresos). Frecuencia: anual.

- **Píldoras mensuales:** Contenido de menos de 1 minuto en pantallas y banners internos de la planta. Frecuencia: mensual.

- **Simulacros de phishing:** Segmentados por perfil (whaling para Junta Directiva, fraude del CEO para administración, alertas técnicas para IT y OT). Canal: correo. Frecuencia: trimestral.

- **Comunicaciones móviles:** Píldoras, alertas y actualizaciones ante nuevos ataques o campañas en curso. Canal: mensajería móvil. Frecuencia: según necesidad.

## Ransomware

### Estado Actual de BioTerra frente al Ransomware

### Protección con FortiEDR

FortiEDR actúa como la última línea de defensa. A diferencia de un antivirus tradicional, monitorea en tiempo real el comportamiento de cada proceso: si detecta actividad sospechosa (ej. cifrado masivo de archivos), bloquea la acción de forma automática e inmediata, incluso ante ataques de día cero.

### Segmentación de Red

La red IT se fragmenta en VLANs gestionadas por los firewalls Fortinet, eliminando tráfico innecesario entre redes inalámbricas, cableadas, de invitados e IoT.

### SOC — Security Operations Center

BioTerra opera con un SOC administrado por una firma especializada externa bajo un modelo de co-gestión. A continuación, la distribución de responsabilidades y horarios:

| Actor                      | Responsabilidad                              | Días        | Horario        |
|----------------------------|----------------------------------------------|------------|----------------|
| Firma especializada (SOC)   | Monitoreo continuo de alertas y análisis en tiempo real | 7 días      | 24 hs          |
| Equipo IT interno          | Revisión de reportes generados por el SOC tercerizado   | Lun–Vie     | 08:00–17:00 hs |


### Medidas Preventivas y Recursos Asignados

Las siguientes medidas conforman la estrategia de defensa en profundidad. Se detalla el responsable, la dedicación estimada y el estado actual de cada acción:

| Medida                           | Responsable  | Dedicación / Frecuencia                      | Estado               |
|----------------------------------|-------------|----------------------------------------------|----------------------|
| Patch Management                 | IT Interno  | Según disponibilidad del equipo IT           | Activo (continuo)    |
| Higiene Digital                  | IT Interno  | A planificar en 2do semestre 2026            | Pendiente            |
| Seguridad RDP / VPN + MFA        | IT Interno  | A planificar en 2do semestre 2026            | Pendiente            |
| Least Privilege            | IT Interno           | Según disponibilidad del equipo IT               | Activo (continuo)    |
| Monitoreo SOC             | Firma especializada  | 24 hs / 7 días (continuo)                        | Activo               |
| Revisión de reportes SOC  | IT Interno           | Lun–Vie, 08:00–17:00 hs                          | Activo               |
| Aislamiento y contención  | IT Interno           | Respuesta inmediata ante incidente               | Protocolo definido   |
| Restauración de backups   | IT Interno           | Diario, semanal y mensual                        | Protocolo definido   |
| Forense y BCP             | IT Interno           | Post-incidente                                   | Pendiente            |
| Segmentación red OT       | IT Interno           | Según responsabilidad del equipo OT             | Pendiente            |

### Detalle de Medidas

- **Patch Management:** Actualización de servidores IT y OT según la disponibilidad y criterio del equipo IT interno. Principio: no puede protegerse lo que no se ve.

- **Least Privilege:** Ningún usuario (salvo IT) opera con cuentas de administrador en tareas diarias. Gestión continua a cargo del equipo IT.

- **Higiene Digital (2do semestre 2026):** Deshabilitar macros y PowerShell si no son necesarios, bloquear nodos TOR en Fortinet, mostrar extensiones de archivo.

- **RDP / Acceso Remoto (2do semestre 2026):** Escritorio remoto restringido detrás de VPN con MFA obligatorio.

- **Segmentación de red OT:** implementación y reglas estrictas en los firewalls Fortinet, con políticas de acceso mínimo en los tres nodos críticos de convergencia IT/OT. Como paso
siguiente, se prevé incorporar un SOC dedicado para OT, replicando el modelo ya implementado en la red IT. Esta implementación tiene como meta estar lista para finales de 2026.

- **Forense y BCP:** El proceso de Análisis Forense y el Plan de Continuidad de Negocio (BCP) se encuentran actualmente en etapa de definición. Se prevé formalizar ambos documentos antes del cierre del primer semestre de 2026, con la participación del equipo IT interno, la empresa tercerizada de ciberseguridad y los jefes de área, bajo la validación del CEO.

### Propuesta para bajar el impacto del Ransomware:

#### Contexto

BioTerra no cuenta actualmente con un Plan de Continuidad de Negocio (BCP) ni un procedimiento de respuesta a incidentes formalizado. Esta sección establece los lineamientos base para actuar ante un ataque de ransomware confirmado, priorizando siempre la continuidad operativa de la planta. Todas las acciones recaen sobre el equipo IT interno.

#### Tiempos de Recuperación Objetivo

La disponibilidad de etanol almacenado es el factor crítico: superadas las 72 hs sin producción, el despacho se ve comprometido. La restauración de OT es siempre la prioridad. Estos tiempos fueron evaluados junto al Gerente de Producción y avalados por el CEO.

| Área            | Tiempo Máximo Tolerable | Tiempo Deseable | Objetivo |
|-----------------|------------------------|----------------|----------|
| Producción (OT) | 72 hs                  | 48 hs          | 24 hs    |
| Administrativa (IT) | 120 hs             | 72 hs          | 48 hs    |

#### Estrategia de Backup

BioTerra implementa un esquema de respaldo en tres medios, cumpliendo la regla 3-2-1 (3 copias, 2 medios distintos, 1 offsite):

- **QNAP (disco local):** primera línea de restauración, recuperación rápida.

- **Nube (Azure):** copia offsite, fuera del alcance del cifrado local.

- **Cinta LTO (offline):** al estar desconectada de la red es inmune al cifrado. Protección definitiva contra ransomware.

#### Frecuencia:

- **Diario (Lun–Jue):** mínima pérdida de datos operativa.

- **Semanal (viernes):** consolidación de la semana.

- **Mensual (último viernes):** resguardo histórico en cinta LTO.

#### Procedimientos implementados

#### Detección y Contención

- FortiEDR aísla automáticamente los endpoints comprometidos.

- El equipo IT bloquea las cuentas afectadas e informa al SOC.

- Se ha segmentado la red IT para proteger la planta de los activos.

#### Procedimiento de Respuesta

**1. Evaluación del Alcance**

- Determinar qué sistemas fueron cifrados y hasta dónde llegó la intrusión.

- Identificar el backup limpio más reciente disponible (QNAP → Azure → LTO).

- Estimar el tiempo de restauración y contrastarlo contra los tiempos objetivos.

**2. Restauración (prioridad OT)**

- Restaurar primero los sistemas OT críticos para retomar la producción dentro de las 24–72 hs.

- Validar la integridad del backup antes de restaurar para evitar reinfección.

- Restaurar los sistemas administrativos IT en segunda instancia.

**3. Decisión sobre el Rescate**

- No pagar. No hay garantía de recuperación de la clave ni de que el atacante no vuelva a cifrar.

- La estrategia de tres medios de backup hace innecesario el pago si los procedimientos se cumplen.

**4. Gestión de la Exfiltración**

**La mayoría del ransomware moderno utiliza doble extorsión. Ante ello:**

- Evaluar si hubo robo de información sensible.

- Notificar a clientes, proveedores y empleados potencialmente afectados.

- Monitorear filtraciones en ransomware.live y misp-project.org.

**5. Análisis Forense**

- Identificar el vector de entrada mediante logs de Fortinet y endpoints. Verificados por la empresa tercerizada que asesora a BioTerra en materia de ciberseguridad.

- Documentar el incidente y ajustar controles para evitar reincidencia.

- Evaluar la responsabilidad legal de la empresa ante la filtración de datos.

#### Sugerencias para Fortalecer la Postura

- **Formalizar el BCP:** Documentar el procedimiento de respuesta con roles, responsables y tiempos límite por sistema. Debe concretarse durante el primer semestre, consensuado entre todos los jefes de área.

- **Pruebas de restauración periódicas:** verificar al menos trimestralmente que los backups son funcionales y que los tiempos de recuperación son alcanzables. Un backup no probado no es un backup confiable.

- **Proteger el QNAP:** al estar conectado a la red es el medio más vulnerable. Se recomienda configurar snapshots inmutables y acceso restringido sólo desde el servidor de backup.

- **Definir un Playbook:** una guía paso a paso que establece roles, decisiones y acciones concretas para que el equipo pueda responder bajo presión sin improvisar.

Para su implementación se propone conformar un Comité de Crisis integrado por el CEO, los jefes de área, el líder de IT y la empresa tercerizada de ciberseguridad, con el objetivo de tenerlo constituido y operativo antes de fin de 2026. Este comité tendría las siguientes responsabilidades:

- Tomar decisiones ejecutivas críticas durante el incidente (parada de planta, comunicación a clientes, intervención legal).

- Coordinar las acciones entre IT interno, la empresa tercerizada y los jefes de área.

- Autorizar la restauración priorizada de sistemas según el impacto operativo.

- Gestionar la comunicación externa ante una posible filtración de datos.

- Revisar y actualizar el Playbook periódicamente en base a nuevos incidentes o cambios en la infraestructura.
