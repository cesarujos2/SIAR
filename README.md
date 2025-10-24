# Ingeniero Informático - Proyecto SIAR

## Tabla de Contenidos

### 1. PAQUETE 1: Hardware, Servidores y Software
- [1.1. Especificaciones técnicas detalladas del equipamiento](#11-especificaciones-técnicas-detalladas-del-equipamiento)
  - [1.1.1. Análisis Tecnológico Central - Enfoque Híbrido](#111-análisis-tecnológico-central---enfoque-híbrido)
  - [1.1.2. Especificaciones de Hardware](#112-especificaciones-de-hardware)
  - [1.1.3. Especificaciones del Servidor](#113-especificaciones-del-servidor)
- [1.2. Coordinación con Ingeniero Civil](#12-coordinación-con-ingeniero-civil)
- [1.3. Licencias de Software](#13-licencias-de-software)
- [1.4. Obtención de cotizaciones](#14-obtención-de-cotizaciones)
- [1.5. Presupuesto detallado](#15-presupuesto-detallado)

### 2. PAQUETE 2: Plataformas Digitales
- [2.1. Coordinación con Ingeniero Ambiental](#21-coordinación-con-ingeniero-ambiental)
  - [2.1.1. Estructura de Navegación del Portal](#211-estructura-de-navegación-del-portal)
  - [2.1.2. Taxonomía de Información](#212-taxonomía-de-información)
  - [2.1.3. Modelo de Datos](#213-modelo-de-datos)
  - [2.1.4. Interoperabilidad con Plataformas Nacionales](#214-interoperabilidad-con-plataformas-nacionales)
  - [2.1.5. Requerimientos Funcionales Específicos](#215-requerimientos-funcionales-específicos)
  - [2.1.6. Entregables de Coordinación](#216-entregables-de-coordinación)
- [2.2. Términos de Referencia (TDR)](#22-términos-de-referencia-tdr)
  - [2.2.1. Servicio](#221-servicio)
  - [2.2.2. Objeto](#222-objeto)
  - [2.2.3. Alcance](#223-alcance)
  - [2.2.4. Requisitos No Funcionales](#224-requisitos-no-funcionales)
  - [2.2.5. Arquitectura y Stack Tecnológico](#225-arquitectura-y-stack-tecnológico)
  - [2.2.6. El Servidor Geoespacial](#226-el-servidor-geoespacial)
  - [2.2.7. Capa de Presentación - Frontend](#227-capa-de-presentación---frontend)
  - [2.2.8. Capa de Aplicación - Backend CMS](#228-capa-de-aplicación---backend-cms)
  - [2.2.9. Capa de Datos - Arquitectura Híbrida](#229-capa-de-datos---arquitectura-híbrida)
  - [2.2.10. Consideraciones de Despliegue y DevOps](#2210-consideraciones-de-despliegue-y-devops)
  - [2.2.11. Requisitos Funcionales](#2211-requisitos-funcionales)
- [2.3. Identificación de proveedores](#23-identificación-de-proveedores)
- [2.4. Presupuesto detallado](#24-presupuesto-detallado)

---

## 1. PAQUETE 1: Hardware, Servidores y Software

### 1.1. Especificaciones técnicas detalladas del equipamiento

**Referencia:** [INFORME-000007-2025-GGR-GRAM-SGGA-FSI.pdf](https://drive.google.com/file/d/1QOJI-HuzLISrTxaA9gB6TQ8S0KN0TKDH/view?usp=drive_link)

#### 1.1.1. Análisis Tecnológico Central - Enfoque Híbrido

Para el proyecto SIAR, que requiere un portal web público de alta disponibilidad y al mismo tiempo maneja información geográfica y datos sensibles del Gobierno Regional, se plantea una estrategia con enfoque híbrido (Cloud para usuario final, Local para procesamiento).

| Característica | Servidor Local (On-Premise) | Servicios en la Nube (Cloud) | Recomendación para SIAR |
| :---- | :---- | :---- | :---- |
| **Portal Web y Aplicaciones** | Alto costo inicial y mantenimiento (hosting propio). | Alta disponibilidad, escalabilidad inmediata y pago por uso. | **CLOUD:** Implementar el portal web público y la aplicación móvil en un servicio IaaS/PaaS (AWS, Google Cloud, Azure) garantiza alta accesibilidad (demanda de 1M+ visitas/año) y reduce la carga de infraestructura física. |
| **Almacenamiento y GIS/Bases de Datos** | Control total sobre la data, ideal para datos sensibles o bases de datos internas. | Costos recurrentes, dependencia de la conectividad (internet) para todo acceso. | **LOCAL/HÍBRIDO:** El Servidor Físico debe albergar las bases de datos ambientales (postGIS/Postgresql) y los geodatabases pesados (geoprocesamiento GIS) internos, garantizando el control y la baja latencia para los especialistas en la oficina. La replicación de la data pública se haría a la Nube. |
| **Costo** | Alto costo de inversión (CAPEX) y personal especializado (mantenimiento y seguridad). | Costo operativo recurrente (OPEX). Más predecible y escalable. | **HÍBRIDO:** Se justifica la inversión en un Servidor Físico para el núcleo operativo, cumpliendo con la adquisición prevista, mientras que el Front-end (Web/App) opera en la Nube para eficiencia. |

**Recomendación:** Se sugiere la adquisición del Servidor Físico (On-Premise) para el núcleo de procesamiento GIS y almacenamiento primario, destinando parte del presupuesto a servicios en la Nube para el hosting del Portal Web y Aplicación Móvil.

---

#### 1.1.2. Especificaciones de Hardware

##### 1.1.2.1. PC Workstation para Ingeniería (01 Unidad)

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

##### 1.1.2.2. Workstation Portátil (01 Unidad)

| Componente | Especificación Técnica | Relevancia para SIAR |
| :---- | :---- | :---- |
| **Modelo Base** | HP ZBook Firefly 16 G11 (o equivalente) | Portabilidad sin sacrificar rendimiento gráfico. |
| **Procesador** | Intel Core Ultra 7 (o equivalente) | Rendimiento moderno con capacidad para tareas de análisis en campo. |
| **Gráficos** | NVIDIA Quadro RTX A500 con 4GB de VRAM (o superior) | Certificación y estabilidad para aplicaciones GIS profesionales. |
| **Memoria** | 32GB DDR5 | Multitarea y ejecución eficiente de software GIS en terreno. |
| **Almacenamiento** | SSD 512GB (o superior) | Rapidez en el inicio y carga de archivos de proyecto. |
| **Pantalla** | 16" en Diagonal WUXGA (1920x1200) IPS. | Calidad de visualización para análisis de imágenes satelitales en campo. |

##### 1.1.2.3. Laptop de Ingeniería Adicional (01 Unidad)

| Componente | Especificación Técnica | Relevancia para SIAR |
| :---- | :---- | :---- |
| **Procesador** | INTEL XEON (o equivalente de alto rendimiento, i7/Ryzen 7 de última generación) | Procesador de alto rendimiento para tareas de oficina y análisis de campo moderado. |
| **Memoria RAM** | 32 GB o Superior | Cumple con el requisito mínimo para manejo de bases de datos. |
| **Almacenamiento** | 240GB o superior SSD (Se recomienda SSD para mejor rendimiento) | Velocidad de acceso a la información. |
| **Video Dedicado** | 6GB (NVIDIA GeForce/Quadro o AMD Radeon Pro) | Capacidad para manejo de proyectos GIS y visualización avanzada. |
| **Sistema Operativo** | WINDOWS 10 PRO 64 BITS (o superior) | Licencia profesional requerida. Se prioriza el uso de licencia OEM en caso por defecto no tenga una. |

##### 1.1.2.4. Plotter / Impresora de Gran Formato (01 Unidad)

Necesario para la impresión de mapas, planos y cartografía ambiental:

- **Modelo Base Referencial:** Impresora HP DesignJet T120 (o equivalente de formato A1/A0)
- **Funcionalidad:** Capacidad para imprimir planos de hasta 24 pulgadas de ancho (A1) con alta resolución

##### 1.1.2.5. Estabilizadores de Estado Sólido (Protección Eléctrica)

| Equipo | Potencia (KVA) | Tecnología | Fases | Voltaje (Entrada/Salida) | Velocidad |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **Equipos de Oficina** | 1.5 KVA \- 1500 DA (o superior) | Estado Sólido al 100% | Monofásico | 220V/220V | 4mseg |
| **Impresoras/Plotter** | 3 KVA \- 3000 DA a más | Estado Sólido al 100% | Monofásico | 220V/220V | 4mseg |

#### 1.1.3. Especificaciones del Servidor

Propuesta técnica del Servidor GIS, Web Backend y Bases de Datos:

| Componente | Especificación Técnica Detallada | Justificación Técnica |
| :---- | :---- | :---- |
| **Factor de Forma** | Rackeable 1U/2U | Optimización de espacio en el ambiente acondicionado de 57.84 m² y mejor ventilación. |
| **Procesador (CPU)** | 1x Intel Xeon Silver de 16 Cores o 2x AMD EPYC (2.5 GHz o superior) | Capacidad de procesamiento para Bases de Datos (SQL Server/PostgreSQL/PostGIS) y servicios web concurrentes. |
| **Memoria RAM** | 128 GB ECC DDR4 (Expandible a 256 GB) | Requerido para la indexación y *caching* de grandes volúmenes de datos espaciales. |
| **Almacenamiento (Discos)** | **Discos Primarios (OS/SQL):** 2x 960 GB SSD NVMe (RAID 1)<br>**Discos Secundarios (Data GIS):** 4x 4TB SAS HDD 10K RPM (RAID 5 o RAID 6) | Separación de la Base de Datos y el Sistema Operativo, con alta redundancia y velocidad de acceso para la data GIS. |
| **Controladora RAID** | Hardware RAID con batería de respaldo (BBU) | Protección crítica contra pérdida de datos por fallo eléctrico o de disco. |
| **Tarjeta de Red** | 2x Puertos Ethernet 1GbE o 1x 10GbE | Conectividad de alta velocidad para la red interna de la GRRNGA. |
| **Sistema Operativo** | Windows Server 2022 Standard o Linux Server (Ubuntu/Red Hat) | Se recomienda Windows Server 2022 Standard para compatibilidad nativa con software GIS de ESRI (si es el caso) y bases de datos. |

### 1.2. Coordinación con Ingeniero Civil

**Actividad crucial:** Reunirse con el Ingeniero Civil para entregarle los requerimientos técnicos de espacio, ventilación/refrigeración (BTU), puntos de energía y de red para la sala de servidores y estaciones de trabajo.

### 1.3. Licencias de Software

| Tipo de Software | Nombre y Versión Sugerida | Especificación de Licencia (Relevancia para SIAR) | Und. | Cant. |
| :---- | :---- | :---- | :---- | :---- |
| **GIS Profesional (Geoprocesamiento)** | **ArcGIS Pro** (Última versión LTS o equivalente) | Licencia Standard o Advanced por usuario nominal. Incluye extensiones clave (Spatial Analyst, 3D Analyst) para el modelamiento ambiental. | Und. | 3 |
| **GIS de Servidor (Publicación Web)** | **ArcGIS Enterprise** (Standard o superior) | Licencia de Servidor (Base Deployment) para publicar servicios web de mapas y datos, y alimentar el Portal Web del SIAR. | Und. | 1 |
| **Diseño Asistido por Computadora (CAD)** | **AutoCAD** (Última versión) | Licencia por usuario nominal. Esencial para la revisión de planos de uso de suelo, proyectos de infraestructura y cartografía base. | Und. | 1 |
| **Software de Productividad** | **Microsoft Office 365** o **Microsoft Office Pro** | Licencia Estándar/Pro Plus por usuario. Incluye Word, Excel (vital para datos estadísticos), PowerPoint y Outlook. | Und. | 4 |
| **S.O. del Servidor** | **Windows Server Standard** (Última versión) | Licencia de Servidor con 16 núcleos base. Requerida para la instalación del Servidor Físico (On-Premise) y alojar ArcGIS Enterprise y Bases de Datos. | Und. | 1 |
| **Bases de Datos** | **PostgreSQL/PostGIS** | PostgreSQL/PostGIS, que es Open Source y no requiere licencia. | Und. | 1 |

### 1.4. Obtención de cotizaciones

Obtener 2 cotizaciones para todo el hardware y software. Utilizar la cotización de TELEMATICA S.A. como una de las referencias para ArcGIS.

### 1.5. Presupuesto detallado

Elaborar el presupuesto detallado (Análisis de Costos) para este paquete.

---

## 2. PAQUETE 2: Plataformas Digitales

### 2.1. Coordinación con Ingeniero Ambiental

**Estado:** Reunión realizada y requisitos funcionales definidos.

#### 2.1.1. Estructura de Navegación del Portal

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

#### 2.1.2. Taxonomía de Información

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

#### 2.1.3. Modelo de Datos

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

#### 2.1.4. Interoperabilidad con Plataformas Nacionales

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

#### 2.1.5. Requerimientos Funcionales Específicos

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

#### 2.1.6. Entregables de Coordinación

El Ingeniero Ambiental ha proporcionado:
- Listado completo de tipos de datos y variables que el sistema debe gestionar
- Estructura de navegación y nomenclatura alineada con SINIA
- Catálogo de 13 temáticas con tipos de información por cada una
- Especificación del modelo de datos (4 clases principales)
- Listado de plataformas para interoperabilidad
- Requerimientos de salvaguardas para información sensible

**Próximos pasos:** Integrar estos requisitos funcionales en los Términos de Referencia (TDR) del servicio de desarrollo.

### 2.2. Términos de Referencia (TDR)

Redactar los Términos de Referencia para el "Servicio de Desarrollo e Implementación del Portal Web y Aplicación Móvil del SIAR", integrando los requisitos funcionales definidos.

#### 2.2.1. Servicio

**Desarrollo e Implementación del Portal Web y Aplicación Móvil del Sistema de Información Ambiental Regional (SIAR) La Libertad**

**Unidad Solicitante:** Gerencia Regional de Recursos Naturales y Gestión Ambiental (GRRNGA) – Subgerencia de Gestión Ambiental

#### 2.2.2. Objeto

Contratar un servicio especializado para el diseño, desarrollo e implementación de una plataforma digital ambiental regional de alto rendimiento, compuesta por un Portal Web (PWA con SSR) y una Aplicación Móvil funcional, operando bajo una arquitectura desacoplada y centrada en el usuario (Mobile First).

#### 2.2.3. Alcance

- Diseño UX/UI y Prototipado navegable con validación de usabilidad
- Implementación del Headless CMS Strapi (Back-end) para la gestión de contenido
- Desarrollo del Front-end (Next.js/Nuxt.js) con arquitectura SPA y SSR
- Despliegue y configuración de la infraestructura en la nube (Cloud)
- Generación y publicación de la Aplicación Móvil (Android/iOS)
- Integración con el Servidor GIS On-Premise de la GRRNGA (para Geovisor)
- Capacitación y transferencia tecnológica

#### 2.2.4. Requisitos No Funcionales

| RNF | Especificación Mínima | Justificación y Criterio de Aceptación |
| :---- | :---- | :---- |
| **Arquitectura Front-end** | Single Page Application (SPA) con Server-Side Rendering (SSR). | Obligatorio el uso de un *framework* moderno (Next.js) para optimizar el SEO y el TTFB (Time To First Byte). |
| **Mobile First Estricto** | Todo el diseño, maquetado y prototipado debe ser iniciado y validado para pantallas móviles antes que para escritorio. | Prioriza la accesibilidad ciudadana y el correcto despliegue en la App Móvil. |
| **PWA (Optimización)** | Conversión total a Progressive Web App (PWA), incluyendo Service Workers para el almacenamiento en caché de activos (imágenes, mapas base) y funcionalidad *offline* parcial. | Rendimiento ultrarrápido y resiliencia ante baja conectividad de banda ancha en zonas rurales de La Libertad. |
| **Performance (Lighthouse)** | El portal debe obtener un puntaje mínimo de 90/100 en las métricas de Performance y Accesibilidad de Google Lighthouse en dispositivos móviles. | Medida objetiva de optimización de código y tiempos de carga. |
| **Diseño UX/UI** | Desarrollo de un Sistema de Diseño (paleta, tipografía, componentes) y presentación de un Informe de Pruebas de Usabilidad con usuarios no técnicos de La Libertad. | Asegura la coherencia visual, la escalabilidad y una interfaz amigable y sencilla, contrarrestando la mala UX de plataformas estatales. |
| **Seguridad** | Implementación de medidas de seguridad a nivel API (JWT/OAuth 2.0) y *Front-end* (manejo de *tokens*, protección contra XSS). | El CMS Strapi debe ser accesible sólo a través de la red interna (VPN) o con estricto control de acceso. |

#### 2.2.5. Arquitectura y Stack Tecnológico

La plataforma SIAR implementa una **arquitectura híbrida desacoplada** que combina servicios en la nube (Frontend y Backend CMS) con infraestructura On-Premise (Servidor Geoespacial y Base de Datos GIS).

```
                        USUARIOS FINALES
                              │
                              ▼
     ┌────────────────────────────────────────────────┐
     │         CAPA DE PRESENTACIÓN (Cloud)           │
     │  ┌─────────────────┐  ┌──────────────────┐     │
     │  │  Portal Web PWA │  │  App Móvil       │     │
     │  │  (Next.js)      │  │  (Capacitor)     │     │
     │  └────┬──────┬─────┘  └────┬──────┬──────┘     │
     └───────┼──────┼─────────────┼──────┼────────────┘
             │      │             │      │
             │      └────Build────┘      │
             │                           │
    REST/GraphQL (contenido)             │
             │                           │ HTTP
             ▼                           │ (servicios OGC:
     ┌──────────────────────┐            │  WMS, WFS, WMTS)
     │  CAPA DE APLICACIÓN  │            │
     │      (Cloud)         │            │
     │  ┌────────────────┐  │            │
     │  │  Strapi CMS    │  │            │
     │  └───────┬────────┘  │            │
     └──────────┼───────────┘            │
                │ PostgreSQL             │
                ▼                        │
     ┌──────────────────────┐            │
     │  BD CLOUD (ÚNICA)    │            │
     │  ┌────────────────┐  │            │
     │  │ Schema:strapi  │  │            │
     │  ├────────────────┤  │            │
     │  │ Schema:        │  │            │
     │  │ public_data    │  │            │
     │  └────────────────┘  │            │
     └──────────▲───────────┘            │
                │ ETL                    │
  ══════════════╪════════════════════════╪═══════════
  ON-PREMISE    │                        │
  ══════════════╪════════════════════════╪═══════════
                │                        │
     ┌──────────┴────────────────────────┼─────────┐
     │                                   ▼         │
     │         ┌───────────────────────────────┐   │
     │         │  SERVIDOR GEOESPACIAL         │   │
     │         │  GeoServer / ArcGIS Server    │   │
     │         │  Puerto: 8080 / 6080          │   │
     │         │                               │   │
     │         │  Expone servicios OGC:        │   │
     │         │  • WMS (mapas imagen)         │   │
     │         │  • WFS (vectores)             │   │
     │         │  • WMTS (tiles)               │   │
     │         └───────────┬───────────────────┘   │
     │                     │ SQL Queries           │
     │                     ▼                       │
     │         ┌───────────────────────────────┐   │
     │         │  PostgreSQL + PostGIS         │   │
     │         │  (On-Premise)                 │   │
     │         │  ┌─────────────────────────┐  │   │
     │         │  │ gis_master (publicable) │  │   │
     │         │  │ gis_working (edición)   │  │   │
     │         │  │ gis_temp (análisis)     │  │   │
     │         │  └─────────────────────────┘  │   │
     │         └───────────┬───────────────────┘   │
     │                     │ Conexión directa      │
     │                     ▼                       │
     │         ┌───────────────────────────────┐   │
     │         │  Estaciones de Trabajo GIS    │   │
     │         │  • 1 PC Workstation           │   │
     │         │  • 2 Laptops                  │   │
     │         │  Software: ArcGIS Pro / QGIS  │   │
     │         └───────────────────────────────┘   │
     └─────────────────────────────────────────────┘

FLUJO DE DATOS:
1. Frontend → Strapi (REST API) → BD Cloud [contenido editorial]
2. Frontend → GeoServer (OGC) → BD PostGIS On-Premise [mapas]
3. BD PostGIS On-Premise → ETL → BD Cloud (public_data) [opcional]
```

#### 2.2.6. El Servidor Geoespacial (GeoServer/ArcGIS Server)

El Servidor Geoespacial es el **intermediario esencial** que permite que el frontend (Portal Web y App Móvil) consuma los datos geográficos de forma segura y optimizada.

##### ¿Por qué es necesario?

**El frontend NUNCA se conecta directamente a la base de datos PostGIS.** En su lugar, el frontend consume **servicios web estandarizados (OGC)** que expone el Servidor Geoespacial.

**Flujo correcto:**
```
Frontend (Leaflet/MapLibre) 
    → HTTP Request: http://geoserver.grrnga.gob.pe/wms?layer=anp&bbox=...
        → GeoServer recibe petición
            → GeoServer consulta PostGIS: SELECT geom FROM anp WHERE ...
                → GeoServer renderiza y transforma
                    → GeoServer devuelve PNG/JSON al Frontend
```

Los navegadores web **no pueden** ejecutar consultas SQL directamente contra PostgreSQL por razones de seguridad y compatibilidad. El Servidor Geoespacial realiza esta transformación de forma segura.

##### ¿Qué hace exactamente?

**1. Conexión ÚNICAMENTE a PostgreSQL/PostGIS On-Premise**
- Se conecta SOLO a la base de datos espacial On-Premise (localhost en el servidor)
- Ejecuta consultas SQL espaciales: `SELECT ST_AsGeoJSON(geom) FROM capas WHERE tema='agua'`
- Accede a tablas del schema: `gis_master` (capas publicables para el portal)
- **NUNCA se conecta a la BD Cloud** - esa es responsabilidad exclusiva de Strapi

**2. Transformación y Renderización**
- **Vectores → Imágenes:** Convierte polígonos/líneas/puntos en imágenes PNG/JPEG con estilos aplicados
- **Reproyección:** Transforma coordenadas EPSG:32717 (UTM WGS84 Zona 17S) a EPSG:4326 (WGS84 geográfico) al vuelo
- **Generalización:** Simplifica geometrías según el nivel de zoom para optimizar rendimiento

**3. Aplicación de Estilos Cartográficos (SLD/CSS)**
```xml
<!-- Ejemplo: Estilo para Áreas Naturales Protegidas -->
<FeatureTypeStyle>
  <Rule>
    <PolygonSymbolizer>
      <Fill>
        <CssParameter name="fill">#00AA00</CssParameter>
        <CssParameter name="fill-opacity">0.6</CssParameter>
      </Fill>
      <Stroke>
        <CssParameter name="stroke">#006600</CssParameter>
        <CssParameter name="stroke-width">2</CssParameter>
      </Stroke>
    </PolygonSymbolizer>
    <TextSymbolizer>
      <Label><PropertyName>nombre_anp</PropertyName></Label>
    </TextSymbolizer>
  </Rule>
</FeatureTypeStyle>
```

**4. Generación de Tiles (Mosaicos de Mapas)**
- Pre-renderiza tiles de 256x256 píxeles en niveles de zoom 0-18
- Almacena en caché local (`/geowebcache`) para servir miles de peticiones/segundo
- Actualiza automáticamente cuando detecta cambios en PostGIS

**5. Expone Servicios OGC que el Frontend consume**

Estos servicios HTTP son lo que el frontend (Leaflet/MapLibre) consume para mostrar mapas:

| Servicio | URL Ejemplo | Qué retorna | Consumido por |
|----------|-------------|-------------|---------------|
| **WMS** | `http://gis.grrnga.gob.pe:8080/geoserver/siar/wms?LAYERS=anp&...` | Imagen PNG del mapa | **Frontend Portal Web** (visualización) |
| **WFS** | `http://gis.grrnga.gob.pe:8080/geoserver/siar/wfs?TYPENAME=cuencas&...` | GeoJSON con geometrías | **Frontend Portal Web** (descargas, análisis) |
| **WMTS** | `http://gis.grrnga.gob.pe:8080/geoserver/gwc/service/wmts?layer=siar:basemap&...` | Tile PNG 256x256 | **App Móvil** (cache offline) |
| **WCS** | `http://gis.grrnga.gob.pe:8080/geoserver/siar/wcs?COVERAGEID=dem&...` | GeoTIFF (raster) | **Frontend** (descargas especializadas) |

**IMPORTANTE:** El frontend SOLO hace peticiones HTTP a estos endpoints. Nunca ejecuta SQL ni se conecta directamente a PostgreSQL.

**6. Control de Acceso y Seguridad**
- Autenticación básica o integración con LDAP/Active Directory
- Reglas de acceso por capa: `anp_piaci` solo visible para usuarios autenticados
- Rate limiting: 100 requests/minuto por IP
- Logs de auditoría: quién descargó qué capa y cuándo

##### ¿Dónde se instala?

**Ubicación:** Servidor físico On-Premise GRRNGA (mismo servidor que aloja PostgreSQL/PostGIS)

**Configuración de red:**
- **IP interna:** 192.168.X.X (red local GRRNGA)
- **Firewall:** Puerto 8080 (GeoServer) o 6080 (ArcGIS Server) abierto para:
  - Acceso interno: Red local GRRNGA (sin restricciones)
  - Acceso externo: Solo desde IPs del servicio cloud que aloja Strapi/Frontend
- **DNS/NAT:** `gis.grrnga.gob.pe` redirige al servidor On-Premise

**Requisitos de hardware (ya incluidos en especificaciones del Paquete 1):**
- RAM: 16-32 GB dedicados (del total de 128 GB del servidor)
- CPU: 4-8 cores asignados
- Disco: 100-200 GB para cache de tiles

##### ¿Cómo se integra con el resto de la arquitectura?

**Conexiones del Frontend - Arquitectura Desacoplada:**

El frontend tiene **DOS conexiones independientes**:
1. **Frontend → Strapi (REST API) → BD Cloud:** Obtiene metadatos, noticias, indicadores, texto editorial
2. **Frontend → GeoServer (OGC HTTP) → BD PostGIS On-Premise:** Obtiene capas geográficas (imágenes, tiles, vectores)

**Flujo de Trabajo Completo (de carga a visualización):**

1. **Editor GIS** carga capa nueva a PostgreSQL On-Premise (vía QGIS/ArcGIS Pro)
2. **PostgreSQL/PostGIS** almacena la capa en schema `gis_master`
3. **Editor GIS** registra la capa en GeoServer:
   - Crea un nuevo "Layer" conectado a la tabla PostGIS
   - Aplica estilo SLD
   - Define permisos de acceso
   - Genera cache de tiles (opcional, para capas estáticas)
4. **Editor GIS** registra metadatos en Strapi CMS:
   - Crea entrada en Content Type `GeoLayer`
   - Campo `endpoints.wms`: `http://gis.grrnga.gob.pe:8080/.../wms`
   - Campo `endpoints.wfs`: `http://gis.grrnga.gob.pe:8080/.../wfs`
5. **Frontend (Next.js)** consulta Strapi API para obtener metadatos:
   - `GET /api/geo-layers?filters[theme][slug]=biodiversidad`
   - Respuesta incluye URLs de servicios OGC del GeoServer
6. **Leaflet (biblioteca del navegador)** hace peticiones HTTP a GeoServer:
   ```javascript
   // Frontend hace petición HTTP al GeoServer, NO a la BD
   L.tileLayer.wms('http://gis.grrnga.gob.pe:8080/geoserver/siar/wms', {
     layers: 'siar:areas_protegidas',
     format: 'image/png',
     transparent: true
   }).addTo(map);
   ```
7. **GeoServer** consulta PostGIS, renderiza y devuelve PNG al navegador
8. **Usuario final** visualiza el mapa en tiempo real en su navegador

##### GeoServer vs ArcGIS Server: Comparativa

| Criterio | GeoServer | ArcGIS Server |
|----------|-----------|---------------|
| **Licencia** | Open Source (GPL) - **Gratuito** | Comercial - **$12,000+ USD/año** |
| **Instalación** | Java (JRE 11+), standalone o Tomcat | Requiere Windows Server + ArcGIS Enterprise |
| **Compatibilidad PostGIS** | Nativa y optimizada | Requiere configuración adicional |
| **Performance** | Excelente con configuración correcta | Superior con datasets masivos (>10M features) |
| **Formatos soportados** | 50+ formatos (Shapefile, GeoTIFF, MBTiles, etc.) | Todos los formatos GIS |
| **Curva de aprendizaje** | Media (interfaz web intuitiva) | Alta (requiere conocimiento ESRI) |
| **Comunidad** | Grande (OSGeo Foundation) | Soporte comercial ESRI |
| **Recomendación SIAR** | **Recomendado** (costo $0, suficiente para la escala del proyecto) | Solo si ya tienen licencias ArcGIS Enterprise |

**Decisión:** Se recomienda **GeoServer** para el proyecto SIAR debido a:
- Costo cero en licencias (presupuesto optimizado)
- Integración perfecta con PostgreSQL/PostGIS (stack open source completo)
- Comunidad activa y documentación extensa
- Escalabilidad suficiente para 1M+ visitas/año del portal

#### 2.2.7. Capa de Presentación - Frontend

##### Portal Web (Progressive Web App)

**Framework y Tecnologías Core:**
- **Next.js 14+** (App Router con Server Components)
  - Server-Side Rendering (SSR) para SEO optimizado
  - Static Site Generation (SSG) para páginas estáticas
  - Incremental Static Regeneration (ISR) para contenido semi-dinámico
- **TypeScript 5+** (Tipado estricto en todo el proyecto)
- **React 18+** (Librería UI con Concurrent Features)

**PWA Implementation:**
- **Service Workers** (Workbox / next-pwa)
  - Cache Strategy: Network First para datos dinámicos, Cache First para assets
  - Offline Fallback Pages para contenido crítico
  - Background Sync para formularios offline
- **Web App Manifest** (manifest.json)
  - Iconos adaptables (192x192, 512x512, maskable)
  - Splash screens para Android/iOS
  - Display mode: standalone
  - Theme color y background color definidos
- **IndexedDB** (Dexie.js)
  - Almacenamiento local de capas base y datos consultados
  - Sincronización con backend al recuperar conectividad

**Librerías Geoespaciales:**
- **Leaflet 1.9+** o **MapLibre GL JS 3+** (mapas base)
  - Soporte de tiles raster y vector
  - Control de capas dinámico
  - Integración con servicios WMS/WMTS
- **Turf.js** (análisis espacial del lado del cliente)
- **Proj4js** (transformaciones de coordenadas CRS)

**UI/UX Libraries:**
- **Tailwind CSS 3+** (Utility-first styling)
- **Shadcn/ui** o **Radix UI** (componentes accesibles)
- **React Hook Form + Zod** (formularios validados)

**Optimizaciones de Performance:**
- Code Splitting automático por rutas
- Lazy Loading de mapas y componentes pesados
- Image Optimization (WebP/AVIF)

##### Aplicación Móvil Multiplataforma (Wrapping)

**Tecnología de Wrapping:**
- **Capacitor 5+** (recomendado) o **Ionic Framework**
  - Build del código web Next.js a WebView nativo
  - Acceso a APIs nativas (Geolocation, Camera, File System, Network Status)
  - Plugins: @capacitor/geolocation, @capacitor/filesystem, @capacitor/network

**Outputs Nativos:**
- **Android APK/AAB** (API Level 26+, Android 8.0+) - **Prioritario**
  - Firma con keystore para Play Store
  - Compatibilidad con 95%+ de dispositivos en Perú
- **iOS IPA** (iOS 13+) - **Opcional fase 2**
  - Solo si el presupuesto lo permite

**Características Móviles:**
- Modo offline con caché de mapas base
- Detección automática de conectividad
- Optimización de bundle size para datos móviles

#### 2.2.8. Capa de Aplicación - Backend CMS

##### Strapi Headless CMS

**Versión y Runtime:**
- **Strapi v4.x** (última versión estable)
- **Node.js 18 LTS** o **20 LTS**
- **npm/pnpm** para gestión de dependencias

**Content Types (Modelos de Datos):**

**Collection Types:**
1. **Indicator** (Indicadores Ambientales)
   - name, definition, methodology, unit, frequency
   - theme (relation → Theme), scope (relation → Scope)
   - timeSeries (relation → TimeSeries, one-to-many)
   - source, responsibleEntity, license
   - publishedAt, createdAt, updatedAt

2. **TimeSeries** (Series Temporales)
   - indicator (relation → Indicator)
   - date (datetime ISO 8601)
   - value (decimal)
   - qualityFlag (enum: validated, provisional, estimated)
   - metadata (JSON)

3. **Document** (Documentos/Publicaciones)
   - title, abstract, keywords (array)
   - authors (array), institution, year
   - documentType (enum: PDF, HTML, Video, Interactive)
   - file (media), externalURL, doi
   - theme (relation), scope (relation)
   - audience (enum: General, Técnico, Académico)
   - license, publishedAt

4. **LegalNorm** (Normas Ambientales)
   - normType (enum: Ley, Decreto, Resolución, Ordenanza)
   - number, issueDate, subject
   - scope (enum: Nacional, Regional, Provincial, Distrital)
   - status (enum: Vigente, Derogada, Modificada)
   - relatedNorms (relation → LegalNorm, many-to-many)
   - documentURL, publishedAt

5. **GeoLayer** (Capas Geoespaciales)
   - title, abstract, keywords
   - geometryType (enum: Point, Line, Polygon, Raster)
   - crs (string: "EPSG:4326", "EPSG:32717")
   - scale, source, updateFrequency
   - endpoints (JSON: {wms, wfs, wmts, geojson})
   - theme (relation), scope (relation)
   - metadata (JSON: ISO 19115 subset)
   - publishedAt

6. **News** (Noticias/Actualidad)
   - title, content (richtext), coverImage (media)
   - theme (relation), tags (array)
   - publishedAt

**Single Types:**
- **HomePage** (contenido de portada)
- **SiteConfig** (configuración general del sitio)
- **CARModule** (contenido CAR)

**Taxonomías (Shared Models):**
- **Theme** (13 temáticas SINIA): name, slug, description, icon
- **Scope** (Ámbito territorial): level (enum: Departamento, Provincia, Distrito), ubigeo, name, geometry (relation → GeoLayer)
- **Institution** (Instituciones): name, acronym, type, contactInfo

**Plugins Esenciales:**
- **@strapi/plugin-users-permissions** (autenticación y autorización)
- **@strapi/plugin-upload** (gestión de media)
- **strapi-plugin-seo** (opcional, metadatos SEO)

**Roles y Permisos:**
1. **Super Admin** - Control total
2. **Editor Ambiental** - CRUD sobre Indicators, Documents, News, LegalNorms
3. **Editor GIS** - CRUD sobre GeoLayers, actualización de endpoints
4. **Editor Municipal** - CREATE/UPDATE limitado a su ámbito territorial
5. **Viewer** - Solo lectura (API pública)

**APIs Generadas:**
- **REST API:** `/api/indicators`, `/api/documents`, etc.
  - Filtros: `?filters[theme][slug][$eq]=agua`
  - Población: `?populate=theme,scope,timeSeries`
  - Paginación: `?pagination[page]=1&pagination[pageSize]=25`
  - Ordenamiento: `?sort[0]=publishedAt:desc`
- **GraphQL API:** Endpoint `/graphql` con schema auto-generado

**Autenticación:**
- **JWT** para frontend web/mobile
- **API Tokens** para integraciones externas

**Hosting Recomendado (uno de los siguientes):**
- **AWS:** EC2 + RDS PostgreSQL + S3
- **Google Cloud:** Cloud Run + Cloud SQL + Cloud Storage (recomendado por facilidad)
- **Railway/Render** (alternativas económicas para instituciones públicas)

#### 2.2.9. Capa de Datos - Arquitectura Híbrida

##### Base de Datos en la Nube (PostgreSQL/PostGIS Managed)

**Importante:** Existe **UNA SOLA base de datos Cloud** que cumple dos funciones principales mediante schemas separados.

**Servicio Recomendado:**
- AWS RDS PostgreSQL con PostGIS
- Google Cloud SQL for PostgreSQL (recomendado)
- Azure Database for PostgreSQL

**Versiones:**
- PostgreSQL 15+ o 16
- PostGIS 3.3+ o 3.4

**Configuración Inicial:**
- **Instancia:** 2 vCPU, 4-8 GB RAM (escalable según demanda)
- **Storage:** 100 GB SSD con auto-scaling
- **Backups:** Automáticos diarios (retención 7 días)

**Schemas Principales:**
```sql
-- Schema 1: Para Strapi CMS (creado automáticamente por Strapi)
CREATE SCHEMA strapi;

-- Schema 2: Para datos GIS procesados (cargados desde On-Premise vía ETL)
CREATE SCHEMA public_data;

-- Extensiones PostGIS
CREATE EXTENSION IF NOT EXISTS postgis;
CREATE EXTENSION IF NOT EXISTS postgis_topology;
CREATE EXTENSION IF NOT EXISTS pg_trgm; -- búsqueda full-text
```

**Contenido Almacenado:**

**1. Schema `strapi` (Base de datos del CMS):**
   - Todos los Content Types de Strapi (Indicators, Documents, News, GeoLayers, etc.)
   - Relaciones entre entidades
   - Usuarios, roles y permisos
   - Configuración del sistema
   - Referencias a archivos en S3/Cloud Storage
   - **NO contiene geometrías pesadas, solo metadatos**

**2. Schema `public_data` (Datos GIS procesados):**
   - Geometrías simplificadas vía `ST_Simplify()` para web
   - Series temporales agregadas (mensuales, anuales)
   - Capas geoespaciales optimizadas (<1 MB por capa)
   - Índices espaciales: `CREATE INDEX idx_geom ON layers USING GIST(geom);`
   - **Este schema se actualiza mediante ETL desde On-Premise**

**Optimizaciones:**
- Connection Pooling (incluido en servicios managed)
- Índices espaciales GIST para consultas geográficas
- Materialized Views para reportes frecuentes

##### Base de Datos On-Premise (PostgreSQL/PostGIS Local)

**Infraestructura:**
- Instalada en el Servidor Físico especificado en Paquete 1
- PostgreSQL 15+ / PostGIS 3.3+
- Windows Server 2022 o Linux (Ubuntu Server 22.04 LTS recomendado)

**Hardware Asignado:**
- Discos SSD NVMe (RAID 1) para el motor de BD
- Discos HDD (RAID 5/6) para datos GIS pesados

**Contenido Almacenado:**
1. **Geodatabases Completas (Alta Resolución)**
   - Capas vectoriales sin simplificar
   - Rasters de alta resolución (DEM, ortofotos, imágenes satelitales)
   - Topología completa de redes (hidrografía, vías)

2. **Archivos de Análisis GIS**
   - Proyectos de ArcGIS Pro / QGIS
   - Modelos de geoprocesamiento
   - Outputs intermedios de análisis

3. **Backups y Archivos Históricos**
   - Versiones anteriores de capas
   - Datos crudos pre-procesamiento

**Schemas:**
```sql
-- Schema para datos operativos GIS
CREATE SCHEMA gis_working;

-- Schema para datos maestros (a replicar a cloud)
CREATE SCHEMA gis_master;

-- Schema para archivos temporales de análisis
CREATE SCHEMA gis_temp;
```

**Servicios Geoespaciales (GeoServer/ArcGIS Server):**
- **GeoServer 2.24+** (Open Source, recomendado) o **ArcGIS Server**
- Conectado a PostgreSQL/PostGIS local
- Publica servicios OGC:
  - **WMS** (Web Map Service) - visualización
  - **WFS** (Web Feature Service) - descarga de vectores
  - **WMTS** (Web Map Tile Service) - tiles cacheados
  - **WCS** (Web Coverage Service) - rasters

**Endpoints Ejemplo:**
```
http://gis.grrnga.local:8080/geoserver/siar/wms
http://gis.grrnga.local:8080/geoserver/siar/wfs
```

##### Flujo de Datos y Sincronización ETL

**Dirección del Flujo:** On-Premise → Cloud (unidireccional)

**Pipeline de Sincronización:**

**1. Preparación de Datos (On-Premise):**
```sql
-- Simplificación de geometrías para web
CREATE MATERIALIZED VIEW gis_master.layer_web_simplified AS
SELECT 
    id,
    name,
    ST_Simplify(geom, 0.001) AS geom_simplified, -- Tolerancia ajustable
    attributes,
    updated_at
FROM gis_master.layers_full;

-- Refresh programado
REFRESH MATERIALIZED VIEW gis_master.layer_web_simplified;
```

**2. Extracción y Transformación:**

Herramientas opcionales:
- **pg_dump/pg_restore** (para migraciones completas)
- **ogr2ogr** (GDAL, para conversión de formatos)
- **FME** (ETL comercial avanzado, si está disponible)
- **Python Script personalizado:**

```python
# Script ETL (ejemplo conceptual)
import psycopg2
from sqlalchemy import create_engine

# Conexión a BD local
conn_local = psycopg2.connect(
    host="localhost",
    database="siar_local",
    user="gis_user",
    password="***"
)

# Conexión a BD cloud
engine_cloud = create_engine(
    "postgresql://user:pass@rds.amazonaws.com:5432/siar_cloud"
)

# Extracción de datos procesados
query = """
    SELECT id, name, ST_AsGeoJSON(geom_simplified) as geom, attributes
    FROM gis_master.layer_web_simplified
    WHERE updated_at > %s
"""
cursor = conn_local.cursor()
cursor.execute(query, (last_sync_date,))

# Carga a cloud
df = pd.DataFrame(cursor.fetchall())
df.to_sql('geo_layers', engine_cloud, schema='public_data', if_exists='append')
```

**3. Programación:**
- **Cron Jobs** (Linux) o **Task Scheduler** (Windows)
- Frecuencia: Diaria (2:00 AM) para datos no críticos
- Trigger manual para actualizaciones urgentes

**4. Validación y Logging:**
- Verificación de integridad (checksums, conteo de registros)
- Log de errores en tabla de auditoría
- Notificaciones por correo en caso de fallo

##### Gestión de Archivos GIS - Pipeline de Carga (Usuario GIS)

**Problema a Resolver:** Permitir que el Editor GIS suba archivos espaciales (Shapefiles, GeoTIFF, GeoJSON) a la base de datos espacial de forma eficiente.

**Soluciones Propuestas:**

**Opción 1: Cliente de Escritorio QGIS/ArcGIS Pro** ⭐ **RECOMENDADO**

Método tradicional y probado:
1. Editor GIS trabaja en **QGIS** (gratuito) o **ArcGIS Pro** (licenciado)
2. Conexión directa a PostgreSQL/PostGIS via DB Manager
3. Importación con control total: Shapefile → PostGIS tabla
4. Configuración de capa en GeoServer (Web UI o REST API)
5. Registro de metadatos en Strapi (formulario web simple)

**Ventajas:**
- Sin desarrollo adicional (ahorro de costos)
- Aprovecha herramientas que el usuario ya domina
- Control total sobre transformaciones y validación
- Implementación inmediata

**Flujo de trabajo:**
```
1. Editor abre QGIS → Conecta a PostGIS On-Premise
2. Importa Shapefile a tabla gis_master.anp_nuevas
3. Valida datos, aplica transformaciones (CRS, limpieza)
4. Accede a GeoServer → Crea capa desde tabla PostGIS
5. Accede a Strapi → Registra metadatos + URL de servicios OGC
```

**Opción 2: Plugin de Strapi para Upload GIS** (Desarrollo custom)

Solo si hay presupuesto para desarrollo adicional:
- Custom plugin que acepta ZIP (Shapefile), GeoJSON, GeoTIFF
- Procesa con Node.js GDAL bindings
- Inserta automáticamente en PostGIS y GeoServer
- **Costo estimado:** 40-60 horas de desarrollo

**Recomendación Final:** **Opción 1 (QGIS/ArcGIS Pro)** como solución pragmática y eficiente. La Opción 2 puede considerarse en una segunda fase si se requiere automatización masiva.

##### Seguridad y Acceso

**Seguridad en Tránsito:**
- HTTPS obligatorio (TLS 1.3)
- Certificados SSL de Let's Encrypt o DigiCert

**Seguridad en Reposo:**
- Encriptación de BD en cloud (AES-256)
- Encriptación de volúmenes en servidor on-premise (LUKS/BitLocker)

**Acceso al CMS:**
- VPN requerida para acceso desde fuera de la red de la GRRNGA
- Firewall: Solo IPs de la GRRNGA pueden acceder al admin panel
- 2FA (Two-Factor Authentication) para usuarios administradores

**Seguridad de APIs:**
- Rate Limiting (100 req/min por IP)
- CORS configurado (solo dominios autorizados)
- API Key rotation cada 90 días

#### 2.2.10. Consideraciones de Despliegue y DevOps

##### Entornos de Desarrollo

**Tres entornos recomendados:**

1. **Development (Local/Cloud)**
   - Para desarrollo activo del equipo
   - Base de datos local con datos de prueba
   - Hot-reload habilitado

2. **Staging (Cloud)**
   - Replica exacta de producción
   - Datos anonimizados de producción
   - Testing pre-deployment
   - URL: `staging.siar.grrnga.gob.pe`

3. **Production (Cloud + On-Premise)**
   - Ambiente de producción final
   - Alta disponibilidad configurada
   - Monitoreo 24/7
   - URL: `siar.grrnga.gob.pe`

##### CI/CD Pipeline

**Herramientas:**
- **Git** (repositorio de código)
- **Docker** (containerización recomendada pero no obligatoria)

**Pipeline Básico:**
1. Desarrollo local → Pruebas
2. Deploy manual a Staging
3. Validación → Deploy a Producción

##### Monitoreo

**Herramientas Mínimas Requeridas:**
- **Uptime Monitoring:** UptimeRobot (gratuito) para verificar disponibilidad
- **Error Tracking:** Logs del servidor + Strapi built-in logging
- **Analytics:** Google Analytics 4 (uso del portal)

**Alertas Críticas:**
- Downtime > 15 minutos
- Servidor On-Premise no responde

##### Backups y Recuperación ante Desastres

**Backups Esenciales:**

**Base de Datos Cloud:**
- Backups automáticos diarios incluidos en el servicio managed

**Base de Datos On-Premise:**
- Backup semanal completo (script automatizado)
- Almacenamiento en disco externo
- Copia mensual en servicio cloud (Google Drive/AWS S3)

**Plan de Recuperación:**
- Tiempo máximo de recuperación: 24 horas
- Prueba de restauración: Semestral

##### Documentación Técnica Requerida

**Documentación Mínima Requerida:**

1. **Manual de Administrador Strapi** (PDF/Wiki)
   - Gestión de contenidos
   - Procedimientos de backup
   - Solución de problemas comunes

2. **Manual de Editor GIS** (PDF/Wiki)
   - Carga de capas a PostgreSQL
   - Configuración en GeoServer
   - Registro de metadatos

3. **Manual de Usuario Portal Web** (integrado en el portal)
   - Guía de navegación
   - FAQ básico

4. **Diagrama de Arquitectura** (imagen + descripción)
   - Componentes y conexiones
   - Flujo de datos

##### Transferencia de Conocimiento

**Capacitaciones Requeridas:**

1. **Administradores Strapi (8 horas presenciales)**
   - Gestión de contenidos
   - Usuarios y permisos
   - Publicación de recursos

2. **Editor GIS (12 horas presenciales + 4 horas prácticas)**
   - Conexión QGIS → PostgreSQL
   - Importación de capas
   - Configuración GeoServer
   - Registro en Strapi

3. **Soporte Técnico TI (8 horas)**
   - Arquitectura general
   - Procedimientos de backup
   - Solución de problemas básicos

**Entregables de Capacitación:**
- Manuales en PDF
- Videos tutoriales (opcional)
- Acceso al código fuente documentado

##### Mantenimiento y Soporte Post-Implementación

**Período de Garantía:** Mínimo 12 meses desde la puesta en producción

**Soporte Técnico Incluido:**

| Severidad | Descripción | Tiempo de Respuesta | Tiempo de Resolución |
|-----------|-------------|---------------------|----------------------|
| **Crítico** | Sistema caído, pérdida de datos | 4 horas laborables | 24 horas |
| **Alto** | Funcionalidad principal afectada | 1 día laborable | 3 días laborables |
| **Medio** | Funcionalidad secundaria afectada | 3 días laborables | 2 semanas |
| **Bajo** | Consultas, mejoras | 5 días laborables | Según acuerdo |

**Actualizaciones:**
- Parches de seguridad críticos (cuando sea necesario)
- Corrección de bugs (durante el período de garantía)

#### 2.2.11. Requisitos Funcionales

*(Pendiente de desarrollo detallado - Se definirán en función de la coordinación con el Ingeniero Ambiental ya completada)*

**Módulos Principales Confirmados:**

1. **Módulo de Estadísticas e Indicadores**
   - Visualización de series temporales con gráficos interactivos
   - Filtros por temática, ámbito territorial y período
   - Exportación de datos (CSV, Excel, JSON)
   - Comparativas entre distritos/provincias

2. **Módulo de Documentos y Publicaciones**
   - Buscador avanzado con filtros multiples
   - Visualizador de PDFs integrado
   - Sistema de etiquetado y categorización
   - Descarga y compartir en redes sociales

3. **Módulo de Normas Ambientales**
   - Línea de tiempo de normatividad
   - Buscador por tipo, año, materia
   - Relaciones entre normas (deroga/modifica)
   - Alertas de nuevas normas (suscripción)

4. **Módulo de Mapas (Geovisor)**
   - Visor de capas geoespaciales interactivo
   - Control de capas (activar/desactivar)
   - Herramientas de consulta espacial (click, polígono)
   - Descarga de datos geográficos (Shapefile, GeoJSON, KML)
   - Generación de mapas estáticos para impresión

5. **Módulo de Actualidad**
   - Noticias y eventos ambientales
   - Galería de imágenes
   - Videos embebidos
   - Integración con redes sociales

6. **Módulo CAR (Comisión Ambiental Regional)**
   - Información de miembros
   - Documentos y acuerdos
   - Calendario de sesiones
   - Proyectos en curso

7. **Buscador Global**
   - Búsqueda full-text en todos los contenidos
   - Filtros por tipo de recurso
   - Resultados paginados con relevancia
   - Sugerencias de búsqueda

### 2.3. Identificación de proveedores

Identificar empresas de desarrollo de software y obtener 2 cotizaciones para el servicio.

### 2.4. Presupuesto detallado

Elaborar el presupuesto detallado para este servicio.