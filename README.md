# Ingeniero Informático

## Paquete 1: Hardware, Servidores y Software 

### 1. Especificaciones técnicas detalladas para todo el equipamiento informático

**Referencia:** [INFORME-000007-2025-GGR-GRAM-SGGA-FSI.pdf](https://drive.google.com/file/d/1QOJI-HuzLISrTxaA9gB6TQ8S0KN0TKDH/view?usp=drive_link)

#### Análisis Tecnológico Central - Enfoque Híbrido

Para el proyecto SIAR, que requiere un portal web público de alta disponibilidad y al mismo tiempo maneja información geográfica y datos sensibles del Gobierno Regional, se plantea una estrategia con enfoque híbrido (Cloud para usuario final, Local para procesamiento).

| Característica | Servidor Local (On-Premise) | Servicios en la Nube (Cloud) | Recomendación para SIAR |
| :---- | :---- | :---- | :---- |
| **Portal Web y Aplicaciones** | Alto costo inicial y mantenimiento (hosting propio). | Alta disponibilidad, escalabilidad inmediata y pago por uso. | **CLOUD:** Implementar el portal web público y la aplicación móvil en un servicio IaaS/PaaS (AWS, Google Cloud, Azure) garantiza alta accesibilidad (demanda de 1M+ visitas/año) y reduce la carga de infraestructura física. |
| **Almacenamiento y GIS/Bases de Datos** | Control total sobre la data, ideal para datos sensibles o bases de datos internas. | Costos recurrentes, dependencia de la conectividad (internet) para todo acceso. | **LOCAL/HÍBRIDO:** El Servidor Físico debe albergar las bases de datos ambientales (postGIS/Postgresql) y los geodatabases pesados (geoprocesamiento GIS) internos, garantizando el control y la baja latencia para los especialistas en la oficina. La replicación de la data pública se haría a la Nube. |
| **Costo** | Alto costo de inversión (CAPEX) y personal especializado (mantenimiento y seguridad). | Costo operativo recurrente (OPEX). Más predecible y escalable. | **HÍBRIDO:** Se justifica la inversión en un Servidor Físico para el núcleo operativo, cumpliendo con la adquisición prevista, mientras que el Front-end (Web/App) opera en la Nube para eficiencia. |

**Recomendación:** Se sugiere la adquisición del Servidor Físico (On-Premise) para el núcleo de procesamiento GIS y almacenamiento primario, destinando parte del presupuesto a servicios en la Nube para el hosting del Portal Web y Aplicación Móvil.

#### Especificaciones Técnicas Detalladas de Equipamiento Informático (Hardware)

##### 1. PC Workstation para Ingeniería (01 Unidad)

Diseñada para el procesamiento intensivo de datos espaciales, modelamiento y visualización (AutoCAD, ArcGIS, QGIS).

| Componente | Especificación Técnica | Relevancia para SIAR |
| :---- | :---- | :---- |
| **Procesador** | Intel® Core™ i9-13900K 3.00GHz, 24 núcleos, 32 subprocesos (o superior) | Máxima potencia para renderizado y geoprocesamiento paralelo. |
| **Placa Madre** | ASROCK Z790 DDR5 4xDIMM, 3xM.2, 6xSATA, WiFi, ATX (o equivalente) | Soporte para RAM y almacenamiento de alta velocidad (DDR5, PCIe 4.0). |
| **Memoria RAM** | 64GB (32GBx2) DDR5 5200MHz / KINGSTON FURY BEAST v.3 (o equivalente) | Esencial para la gestión de grandes *datasets* geográficos y multizonal. |
| **Almacenamiento Primario** | 1TB M.2 SSD NVMe PCIe 4.0 (KC3000 o equivalente) | Velocidad extrema para el sistema operativo y software de análisis (ArcGIS Pro). |
| **Almacenamiento Secundario** | 1TB M.2 SSD NVMe PCIe 4.0 (KC3000 o equivalente) | Almacenamiento rápido de proyectos activos y bases de datos locales. |
| **HDD Adicional** | 1TB SATA 3.5" 7200RPM (WD BLACK o equivalente) | Respaldo y almacenamiento de archivos de menor acceso. |
| **Tarjeta de Video** | NVIDIA® GeForce RTX™ 4070 SUPER 12GB (o equivalente) | Aceleración de tareas GIS, modelado 3D y visualización de mapas complejos. |
| **Sistema Operativo** | WINDOWS 11 Pro for Workstation (Licencia OEM) | Soporte para hardware de alto rendimiento y seguridad empresarial. |
| **Monitor** | 01 unidad de 27" con puertos HDMI (mínimo) y Displayport (opcional). | Espacio de trabajo suficiente para la visualización de mapas y datos complejos. |

##### 2. Workstation Portátil (01 Unidad)

| Componente | Especificación Técnica | Relevancia para SIAR |
| :---- | :---- | :---- |
| **Modelo Base** | HP ZBook Firefly 16 G11 (o equivalente) | Portabilidad sin sacrificar rendimiento gráfico. |
| **Procesador** | Intel Core Ultra 7 (o equivalente) | Rendimiento moderno con capacidad para tareas de análisis en campo. |
| **Gráficos** | NVIDIA Quadro RTX A500 con 4GB de VRAM (o superior) | Certificación y estabilidad para aplicaciones GIS profesionales. |
| **Memoria** | 32GB DDR5 | Multitarea y ejecución eficiente de software GIS en terreno. |
| **Almacenamiento** | SSD 512GB (o superior) | Rapidez en el inicio y carga de archivos de proyecto. |
| **Pantalla** | 16" en Diagonal WUXGA (1920x1200) IPS. | Calidad de visualización para análisis de imágenes satelitales en campo. |

##### 3. Laptop de Ingeniería Adicional (01 Unidad)

| Componente | Especificación Técnica | Relevancia para SIAR |
| :---- | :---- | :---- |
| **Procesador** | INTEL XEON (o equivalente de alto rendimiento, i7/Ryzen 7 de última generación) | Procesador de alto rendimiento para tareas de oficina y análisis de campo moderado. |
| **Memoria RAM** | 32 GB o Superior | Cumple con el requisito mínimo para manejo de bases de datos. |
| **Almacenamiento** | 240GB o superior SSD (Se recomienda SSD para mejor rendimiento) | Velocidad de acceso a la información. |
| **Video Dedicado** | 6GB (NVIDIA GeForce/Quadro o AMD Radeon Pro) | Capacidad para manejo de proyectos GIS y visualización avanzada. |
| **Sistema Operativo** | WINDOWS 10 PRO 64 BITS (o superior) | Licencia profesional requerida. Se prioriza el uso de licencia OEM en caso por defecto no tenga una. |

##### 4. Plotter / Impresora de Gran Formato (01 Unidad)

Necesario para la impresión de mapas, planos y cartografía ambiental:

- **Modelo Base Referencial:** Impresora HP DesignJet T120 (o equivalente de formato A1/A0)
- **Funcionalidad:** Capacidad para imprimir planos de hasta 24 pulgadas de ancho (A1) con alta resolución

##### 5. Estabilizadores de Estado Sólido (Protección Eléctrica)

| Equipo | Potencia (KVA) | Tecnología | Fases | Voltaje (Entrada/Salida) | Velocidad |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **Equipos de Oficina** | 1.5 KVA \- 1500 DA (o superior) | Estado Sólido al 100% | Monofásico | 220V/220V | 4mseg |
| **Impresoras/Plotter** | 3 KVA \- 3000 DA a más | Estado Sólido al 100% | Monofásico | 220V/220V | 4mseg |

#### Especificaciones Técnicas del Servidor para Almacenamiento

Propuesta técnica del Servidor GIS, Web Backend y Bases de Datos:

| Componente | Especificación Técnica Detallada | Justificación Técnica |
| :---- | :---- | :---- |
| **Factor de Forma** | Rackeable 1U/2U | Optimización de espacio en el ambiente acondicionado de 57.84 m² y mejor ventilación. |
| **Procesador (CPU)** | 1x Intel Xeon Silver de 16 Cores o 2x AMD EPYC (2.5 GHz o superior) | Capacidad de procesamiento para Bases de Datos (SQL Server/PostgreSQL/PostGIS) y servicios web concurrentes. |
| **Memoria RAM** | 128 GB ECC DDR4 (Expandible a 256 GB) | Requerido para la indexación y *caching* de grandes volúmenes de datos espaciales. |
| **Almacenamiento (Discos)** | **Discos Primarios (OS/SQL):** 2x 960 GB SSD NVMe (RAID 1)<br>**Discos Secundarios (Data GIS):** 4x 4TB SAS HDD 10K RPM (RAID 5 o RAID 6) | Separación de la Base de Datos y el Sistema Operativo, con alta redundancia y velocidad de acceso para la data GIS. |
| **Controladora RAID** | Hardware RAID con batería de respaldo (BBU) | Protección crítica contra pérdida de datos por fallo eléctrico o de disco. |
| **Tarjeta de Red** | 2x Puertos Ethernet 1GbE o 1x 10GbE | Conectividad de alta velocidad para la red interna de la GRAMB. |
| **Sistema Operativo** | Windows Server 2022 Standard o Linux Server (Ubuntu/Red Hat) | Se recomienda Windows Server 2022 Standard para compatibilidad nativa con software GIS de ESRI (si es el caso) y bases de datos. |

### 2. Coordinación con Ingeniero Civil

**Actividad crucial:** Reunirse con el Ingeniero Civil para entregarle los requerimientos técnicos de espacio, ventilación/refrigeración (BTU), puntos de energía y de red para la sala de servidores y estaciones de trabajo.

### 3. Cuadro de especificaciones y cantidades de licencias de software

| Tipo de Software | Nombre y Versión Sugerida | Especificación de Licencia (Relevancia para SIAR) | Und. | Cant. |
| :---- | :---- | :---- | :---- | :---- |
| **GIS Profesional (Geoprocesamiento)** | **ArcGIS Pro** (Última versión LTS o equivalente) | Licencia Standard o Advanced por usuario nominal. Incluye extensiones clave (Spatial Analyst, 3D Analyst) para el modelamiento ambiental. | Und. | 3 |
| **GIS de Servidor (Publicación Web)** | **ArcGIS Enterprise** (Standard o superior) | Licencia de Servidor (Base Deployment) para publicar servicios web de mapas y datos, y alimentar el Portal Web del SIAR. | Und. | 1 |
| **Diseño Asistido por Computadora (CAD)** | **AutoCAD** (Última versión) | Licencia por usuario nominal. Esencial para la revisión de planos de uso de suelo, proyectos de infraestructura y cartografía base. | Und. | 1 |
| **Software de Productividad** | **Microsoft Office 365** o **Microsoft Office Pro** | Licencia Estándar/Pro Plus por usuario. Incluye Word, Excel (vital para datos estadísticos), PowerPoint y Outlook. | Und. | 4 |
| **S.O. del Servidor** | **Windows Server Standard** (Última versión) | Licencia de Servidor con 16 núcleos base. Requerida para la instalación del Servidor Físico (On-Premise) y alojar ArcGIS Enterprise y Bases de Datos. | Und. | 1 |
| **Bases de Datos** | **PostgreSQL/PostGIS** | PostgreSQL/PostGIS, que es Open Source y no requiere licencia. | Und. | 1 |

### 4. Obtención de cotizaciones

Obtener 2 cotizaciones para todo el hardware y software. Utilizar la cotización de TELEMATICA S.A. como una de las referencias para ArcGIS.

### 5. Presupuesto detallado

Elaborar el presupuesto detallado (Análisis de Costos) para este paquete.

---

## Paquete 2: Plataformas Digitales

### 1. Coordinación con Ingeniero Ambiental

**Estado:** ✅ Reunión realizada y requisitos funcionales definidos.

#### Acuerdos y Definiciones Principales

Como resultado de la coordinación con el Ingeniero Ambiental, se han establecido los siguientes lineamientos técnicos y funcionales para el desarrollo del Portal Web y Aplicación Móvil del SIAR:

##### 1.1. Estructura de Navegación del Portal

El portal seguirá la estructura organizativa del SINIA Nacional, con los siguientes menús principales:

- **Actualidad:** Novedades y contenidos destacados
- **Publicaciones:** Ambientales, Científicas y Videos
- **Normas:** Normatividad ambiental regional
- **Mapas:** Mapoteca y Visor SINIA
- **Estadísticas Regionales:** Indicadores ambientales por temática
- **Acerca de:** Información institucional (Qué es el SIAR, Contáctenos)
- **Comisión Ambiental Regional (CAR):** Módulo de gobernanza intersectorial

**Navegación transversal por:**
- **Temática:** 13 temáticas ambientales (Agua, Aire, Biodiversidad, etc.)
- **Tipo de información:** Estadística, Bibliográfica/Documental, Normativa, Geoespacial
- **Ámbito territorial:** Departamento → Provincia → Distrito (+ Cuencas cuando aplique)

##### 1.2. Taxonomía de Información (13 Temáticas SINIA)

El sistema gestionará información ambiental clasificada en las siguientes temáticas:

1. **Agua** - Series hidrológicas, balances hídricos, red hidrográfica
2. **Aire y Atmósfera** - Calidad del aire, estaciones de monitoreo
3. **Asuntos Socioambientales** - Comunidades campesinas/nativas, pueblos indígenas
4. **Biodiversidad y Ecosistemas** - ANP, ACR, ecosistemas frágiles
5. **Cambio Climático** - Escenarios, vulnerabilidad, NDC regional
6. **Clima y Eventos Naturales** - Series climáticas, eventos extremos
7. **Consumo Responsable y Producción Sostenible** - P+L, ecoetiquetado
8. **Economía Ambiental y Bionegocios** - Valoración económica, casos
9. **Gestión de Riesgos y Desastres** - Mapas de peligros, susceptibilidad
10. **Gestión, Fiscalización y Participación** - EIA, fiscalización ambiental
11. **Residuos** - Generación, valorización, infraestructura
12. **Salud Ambiental** - Exposición, vigilancia ambiental
13. **Suelo y Tierra** - Uso/cobertura, sitios contaminados

##### 1.3. Modelo de Datos (4 Tipos de Recursos)

El sistema manejará cuatro tipos principales de recursos, alineados con el SINIA:

**A. Indicadores y Series Temporales**
- Campos: nombre, definición, metodología, unidad, frecuencia, tema, ámbito geográfico (UBIGEO/cuenca), fuente, responsable, licencia
- Series asociadas con fecha ISO, valor numérico, flag de calidad

**B. Documentos Bibliográficos**
- Tipos: PDF, HTML, Video, Interactivo
- Metadatos: título, autores, institución, año, resumen, palabras clave, tema, ámbito, URL/DOI, audiencia, licencia

**C. Normas Ambientales**
- Campos: tipo, número, fecha, materia, ámbito, vigencia, resumen, relaciones (deroga/modifica), URL del documento

**D. Capas Geoespaciales**
- Metadatos: título, resumen, tema, tipo de geometría, CRS (EPSG:4326 web, UTM para descarga), escala, fuente, frecuencia de actualización
- Endpoints: WMS, WFS, WMTS, GeoJSON

**Metadatos obligatorios** (todos los recursos): título, resumen, palabras clave, fuente, entidad responsable, cobertura temporal y espacial, clasificación temática, fecha de publicación/actualización, licencia.

##### 1.4. Interoperabilidad con Plataformas Nacionales

El SIAR debe integrarse con las siguientes plataformas mediante servicios OGC (WMS/WFS/WMTS) y APIs:

**Conexiones Core (Imprescindibles):**
- **SINIA** - Sincronización semántica y cosecha de metadatos
- **GeoPerú (IDE Nacional)** - Registro del catálogo SIAR
- **Geoservidor MINAM y Geobosques** - Servicios geoespaciales
- **SERNANP** - Áreas Naturales Protegidas y zonas de amortiguamiento
- **SERFOR** - Ecosistemas frágiles, información forestal
- **ANA - SNIRH** - Información hídrica
- **SENAMHI** - Clima, estaciones meteorológicas
- **MINCUL - BDPI** - Comunidades indígenas, PIACI (con salvaguardas)
- **CENEPRED - SIGRID** - Gestión de riesgos y desastres
- **INGEMMET - GEOCATMIN** - Peligros geológicos
- **OEFA** - Fiscalización ambiental

**Métodos de integración:**
- Capas geográficas vía servicios OGC (WMS/WFS/WMTS)
- Series tabulares vía CSV/JSON/API
- Enlaces profundos a visores externos
- Registro en el catálogo GeoPerú

##### 1.5. Requerimientos Funcionales Específicos

**Backoffice (Gestión de Contenidos):**
- Pipeline Semiautomático: Formularios web, carga de plantillas CSV/PDF
- Pipeline Automático: Registro de endpoints, cosecha programada, control de cambios
- Roles de usuario: Administrador, Editor Ambiental, Editor GIS, Municipalidades

**Visor Geoespacial:**
- Compatible con estándares WMS/WFS/WMTS
- Integración del Visor SINIA (ArcGIS) como acceso rápido
- Herramientas de consulta espacial y descarga de datos

**Salvaguardas de Seguridad:**
- Para información sensible (PIACI, patrimonio cultural): limitar zoom/descargas detalladas
- Redirigir a geoportales sectoriales con disclaimer
- Control de acceso al CMS desde red interna (VPN)

**Políticas de Actualización:**
- Novedades y Normas: Seguimiento semanal
- Mapoteca: Refresh semestral, priorizar capas vivas por servicios OGC
- Depuración de contenido histórico obsoleto

##### 1.6. Entregables de Coordinación

El Ingeniero Ambiental ha proporcionado:
- ✅ Listado completo de tipos de datos y variables que el sistema debe gestionar
- ✅ Estructura de navegación y nomenclatura alineada con SINIA
- ✅ Catálogo de 13 temáticas con tipos de información por cada una
- ✅ Especificación del modelo de datos (4 clases principales)
- ✅ Listado de plataformas para interoperabilidad
- ✅ Requerimientos de salvaguardas para información sensible

**Próximos pasos:** Integrar estos requisitos funcionales en los Términos de Referencia (TDR) del servicio de desarrollo.

### 2. Términos de Referencia (TDR)

Redactar los Términos de Referencia para el "Servicio de Desarrollo e Implementación del Portal Web y Aplicación Móvil del SIAR", integrando los requisitos funcionales definidos.

#### Servicio

**Desarrollo e Implementación del Portal Web y Aplicación Móvil del Sistema de Información Ambiental Regional (SIAR) La Libertad**

**Unidad Solicitante:** Gerencia Regional del Ambiente (GRAMB) – Subgerencia de Gestión Ambiental

#### Objeto

Contratar un servicio especializado para el diseño, desarrollo e implementación de una plataforma digital ambiental regional de alto rendimiento, compuesta por un Portal Web (PWA con SSR) y una Aplicación Móvil funcional, operando bajo una arquitectura desacoplada y centrada en el usuario (Mobile First).

#### Alcance

- Diseño UX/UI y Prototipado navegable con validación de usabilidad
- Implementación del Headless CMS Strapi (Back-end) para la gestión de contenido
- Desarrollo del Front-end (Next.js/Nuxt.js) con arquitectura SPA y SSR
- Despliegue y configuración de la infraestructura en la nube (Cloud)
- Generación y publicación de la Aplicación Móvil (Android/iOS)
- Integración con el Servidor GIS On-Premise del GRAMB (para Geovisor)
- Capacitación y transferencia tecnológica

#### Requisitos No Funcionales

| RNF | Especificación Mínima | Justificación y Criterio de Aceptación |
| :---- | :---- | :---- |
| **Arquitectura Front-end** | Single Page Application (SPA) con Server-Side Rendering (SSR). | Obligatorio el uso de un *framework* moderno (Next.js) para optimizar el SEO y el TTFB (Time To First Byte). |
| **Mobile First Estricto** | Todo el diseño, maquetado y prototipado debe ser iniciado y validado para pantallas móviles antes que para escritorio. | Prioriza la accesibilidad ciudadana y el correcto despliegue en la App Móvil. |
| **PWA (Optimización)** | Conversión total a Progressive Web App (PWA), incluyendo Service Workers para el almacenamiento en caché de activos (imágenes, mapas base) y funcionalidad *offline* parcial. | Rendimiento ultrarrápido y resiliencia ante baja conectividad de banda ancha en zonas rurales de La Libertad. |
| **Performance (Lighthouse)** | El portal debe obtener un puntaje mínimo de 90/100 en las métricas de Performance y Accesibilidad de Google Lighthouse en dispositivos móviles. | Medida objetiva de optimización de código y tiempos de carga. |
| **Diseño UX/UI** | Desarrollo de un Sistema de Diseño (paleta, tipografía, componentes) y presentación de un Informe de Pruebas de Usabilidad con usuarios no técnicos de La Libertad. | Asegura la coherencia visual, la escalabilidad y una interfaz amigable y sencilla, contrarrestando la mala UX de plataformas estatales. |
| **Seguridad** | Implementación de medidas de seguridad a nivel API (JWT/OAuth 2.0) y *Front-end* (manejo de *tokens*, protección contra XSS). | El CMS Strapi debe ser accesible sólo a través de la red interna (VPN) o con estricto control de acceso. |

#### Arquitectura y Stack Tecnológico

Arquitectura desacoplada donde el Front-end reside en el Cloud público y consume datos vía API.

##### 1. Front-end (Portal Web / App Móvil)

- **Framework:** Next.js (Última versión LTS)
- **Lenguaje:** JavaScript / TypeScript
- **Estrategia Móvil:** Uso de herramientas de *wrapping* (ej. Capacitor, Ionic) para convertir el código web en aplicación móvil nativa (Android APK, iOS IPA)
- **Librería GIS:** Leaflet, Mapbox GL JS o OpenLayers (librerías ligeras)

##### 2. Back-end Central (API + CMS)

**CMS:** Strapi (Open Source). Debe ser configurado para gestionar:

- Modelos de Contenido Personalizados para Normas, Publicaciones, Noticias y Estadísticas
- Roles y Permisos de edición y publicación (Administrador, Editor Ambiental, Municipalidades, Editor GIS)
- Integración con almacenamiento de archivos (ej. AWS S3, Google Cloud Storage, o filesystem del servidor GRAMB) para los PDF y documentos pesados

**Lenguaje API:** Node.js (preferido por compatibilidad con Strapi), Go o PHP 8+

**Contrato API:** La API debe seguir el estándar RESTful (o GraphQL) para todas las consultas.

- Implementar filtros, paginación y ordenamiento eficientes
- Todas las respuestas de API deben estar en formato JSON

##### 3. Bases de Datos y Almacenamiento

**Bases de Datos:** PostgreSQL/PostGIS (Residente en el Servidor On-Premise del GRAMB) para datos espaciales y la Base de Datos del CMS.

**Integración GIS:** El Back-end debe consumir y servir datos geoespaciales desde los servicios (OGC/REST) del Servidor ArcGIS/Geoserver del GRAMB.

#### Requisitos Funcionales

*(Pendiente de desarrollo)*

### 3. Identificación de proveedores

Identificar empresas de desarrollo de software y obtener 2 cotizaciones para el servicio.

### 4. Presupuesto detallado

Elaborar el presupuesto detallado para este servicio.