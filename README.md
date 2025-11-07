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
  - [2.2.4. Arquitectura General del Sistema](#224-arquitectura-general-del-sistema)
    - [Vista General de la Arquitectura](#vista-general-de-la-arquitectura)
    - [Flexibilidad Tecnológica y Alternativas](#flexibilidad-tecnológica-y-alternativas)
  - [2.2.5. Componentes del Sistema por Capas](#225-componentes-del-sistema-por-capas)
    - [Servidor Geoespacial](#servidor-geoespacial-geoserver)
    - [Capa de Presentación - Frontend](#capa-de-presentación---frontend)
      - [Aplicación Móvil Colaborativa](#aplicación-móvil-colaborativa-producto-independiente)
    - [Capa de Aplicación - Backend CMS](#capa-de-aplicación---backend-cms)
      - [Strapi Headless CMS](#strapi-headless-cms)
      - [Integración con API del MINAM](#integración-con-api-del-minam-para-publicación-en-siar)
      - [API Pública Documentada para Uso Externo](#api-pública-documentada-para-uso-externo)
    - [Capa de Datos - Arquitectura Híbrida](#capa-de-datos---arquitectura-híbrida)
      - [Base de Datos en la Nube](#base-de-datos-en-la-nube-postgresqlpostgis-managed)
      - [Base de Datos On-Premise](#base-de-datos-on-premise-postgresqlpostgis-local)
      - [Flujo de Datos y Sincronización ETL](#flujo-de-datos-y-sincronización-etl)
      - [Gestión de Archivos GIS](#gestión-de-archivos-gis---pipeline-de-carga-usuario-gis)
      - [Seguridad y Acceso](#seguridad-y-acceso)
  - [2.2.6. Requisitos](#226-requisitos)
    - [Aplicación Móvil Colaborativa](#aplicación-móvil-colaborativa)
      - [Requisitos No Funcionales de la App Móvil](#requisitos-no-funcionales-de-la-app-móvil)
      - [Requisitos Funcionales de la App Móvil](#requisitos-funcionales-de-la-app-móvil)
  - [2.2.7. Despliegue y DevOps](#227-despliegue-y-devops)
    - [Entornos de Desarrollo](#entornos-de-desarrollo)
    - [CI/CD Pipeline](#cicd-pipeline)
    - [Monitoreo](#monitoreo)
    - [Backups y Recuperación ante Desastres](#backups-y-recuperación-ante-desastres)
  - [2.2.8. Entregables y Transferencia de Conocimiento](#228-entregables-y-transferencia-de-conocimiento)
    - [Documentación Técnica Requerida](#documentación-técnica-requerida)
    - [Transferencia de Conocimiento](#transferencia-de-conocimiento)
    - [Mantenimiento y Soporte Post-Implementación](#mantenimiento-y-soporte-post-implementación)
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

Propuesta técnica del Servidor para Bases de Datos:

| Componente | Especificación Técnica Detallada | Justificación Técnica |
| :---- | :---- | :---- |
| **Factor de Forma** | Rackeable 1U/2U | Optimización de espacio en el ambiente acondicionado de 57.84 m² y mejor ventilación. |
| **Procesador (CPU)** | 1x Intel Xeon Silver de 16 Cores o 2x AMD EPYC (2.5 GHz o superior) | Capacidad de procesamiento para Bases de Datos (PostgreSQL/PostGIS) y servicios concurrentes. |
| **Memoria RAM** | 128 GB ECC DDR4 (Expandible a 256 GB) | Requerido para la indexación y *caching* de grandes volúmenes de datos espaciales. |
| **Almacenamiento (Discos)** | **Discos Primarios (OS/PostgreSQL):** 2x 960 GB SSD NVMe (RAID 1)<br>**Discos Secundarios (Data GIS):** 4x 4TB SAS HDD 10K RPM (RAID 5 o RAID 6) | Separación de la Base de Datos y el Sistema Operativo, con alta redundancia y velocidad de acceso para la data GIS. |
| **Controladora RAID** | Hardware RAID con batería de respaldo (BBU) | Protección crítica contra pérdida de datos por fallo eléctrico o de disco. |
| **Tarjeta de Red** | 2x Puertos Ethernet 1GbE o 1x 10GbE | Conectividad de alta velocidad para la red interna de la GRRNGA. |
| **Sistema Operativo** | Ubuntu Server 22.04 LTS (Linux - Open Source) | Sistema operativo open source recomendado para optimización de costos. Compatible con PostgreSQL/PostGIS y toda la stack open source. Excelente rendimiento y estabilidad para servidores de bases de datos. |

### 1.2. Coordinación con Ingeniero Civil

**Actividad crucial:** Reunirse con el Ingeniero Civil para entregarle los requerimientos técnicos de espacio, ventilación/refrigeración (BTU), puntos de energía y de red para la sala de servidores y estaciones de trabajo.

### 1.3. Licencias de Software

| Tipo de Software | Nombre y Versión Sugerida | Especificación de Licencia (Relevancia para SIAR) | Und. | Cant. |
| :---- | :---- | :---- | :---- | :---- |
| **GIS Profesional (Geoprocesamiento)** | **ArcGIS Pro** (Última versión LTS o equivalente) | Licencia Standard o Advanced por usuario nominal. Incluye extensiones clave (Spatial Analyst, 3D Analyst) para el modelamiento ambiental. | Und. | 3 |
| **Diseño Asistido por Computadora (CAD)** | **AutoCAD** (Última versión) | Licencia por usuario nominal. Esencial para la revisión de planos de uso de suelo, proyectos de infraestructura y cartografía base. | Und. | 3 |
| **Software de Productividad** | **Microsoft Office 365** o **Microsoft Office Pro** | Licencia Estándar/Pro Plus por usuario. Incluye Word, Excel (vital para datos estadísticos), PowerPoint y Outlook. | Und. | 3 |
| **S.O. del Servidor** | **Ubuntu Server 22.04 LTS** (Open Source - Gratuito) | Sistema operativo Linux recomendado para optimización de costos. Compatible con PostgreSQL/PostGIS y toda la stack open source. Soporte LTS hasta 2027. | Und. | 1 |

### 1.4. Obtención de cotizaciones

Obtener 2 cotizaciones para todo el hardware y software. Para software GIS comercial (ArcGIS Pro, AutoCAD), se puede utilizar la cotización de TELEMATICA S.A. como una de las referencias.

### 1.5. Presupuesto detallado

Elaborar el presupuesto detallado (Análisis de Costos) para este paquete.

---

## 2. PAQUETE 2: Plataformas Digitales

### 2.1. Coordinación con Ingeniero Ambiental

**Estado:** Reunión realizada y requisitos funcionales definidos.

#### 2.1.1. Estructura de Información para el SIAR

**NOTA:** Ya no se desarrolla un portal web propio. La información se publicará en el **SIAR del MINAM** mediante su API. La estructura de información debe seguir la organización del SINIA Nacional para compatibilidad con el SIAR del MINAM. Los datos se organizarán según los siguientes módulos principales:

- **Actualidad:** Novedades y contenidos destacados
- **Publicaciones:** Ambientales, Científicas y Videos
- **Normas:** Normatividad ambiental regional
- **Mapas:** Mapoteca y Visor SINIA
- **Estadísticas Regionales:** Indicadores ambientales por temática
- **Acerca de:** Información institucional (Qué es el SIAR, Contáctenos)
- **Comisión Ambiental Regional (CAR):** Módulo de gobernanza intersectorial

**Organización transversal de datos:**
- **Temática:** 13 temáticas ambientales (Agua, Aire, Biodiversidad, etc.)
- **Tipo de información:** Estadística, Bibliográfica/Documental, Normativa, Geoespacial
- **Ámbito territorial:** Departamento → Provincia → Distrito (+ Cuencas cuando aplique)

**Esta estructura se utilizará para:**
- Organizar datos en Strapi CMS
- Formatear datos para envío al API del MINAM
- Visualización en el SIAR del MINAM (página La Libertad)

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

Redactar los Términos de Referencia para el "Servicio de Desarrollo e Implementación de la Aplicación Móvil Colaborativa y Sistema de Integración con el SIAR del MINAM del SIAR", integrando los requisitos funcionales definidos.

#### 2.2.1. Servicio

**Desarrollo e Implementación de la Aplicación Móvil Colaborativa y Sistema de Integración con el SIAR del MINAM del Sistema de Información Ambiental Regional (SIAR) La Libertad**

**Unidad Solicitante:** Gerencia Regional de Recursos Naturales y Gestión Ambiental (GRRNGA) – Subgerencia de Gestión Ambiental

#### 2.2.2. Objeto

Contratar un servicio especializado para el diseño, desarrollo e implementación de una **Aplicación Móvil colaborativa nativa multiplataforma** (React Native u otra tecnología multiplataforma) que permite a usuarios aportar información ambiental desde el campo, un **Backend CMS** para gestión de contenido y contribuciones, y un **sistema de integración con la API del MINAM** para publicar la información en el SIAR del MINAM (que ya cuenta con páginas del SIAR de cada gobierno regional). La información se visualizará en el SIAR del MINAM mediante su API, sin necesidad de desarrollar un portal web propio.

#### 2.2.3. Alcance

- Diseño UX/UI y Prototipado navegable con validación de usabilidad para la aplicación móvil
- Implementación del Headless CMS Strapi (Back-end) en la nube para la gestión de contenido y contribuciones colaborativas
- **Desarrollo de la Aplicación Móvil colaborativa** con tecnología multiplataforma nativa (React Native u otra) que permite a usuarios aportar información ambiental desde el campo
- **Sistema de cuentas y usuarios** para la aplicación móvil colaborativa (OAuth 2.0 con Google/Apple)
- **Funcionalidades colaborativas en la App Móvil** que permitan a usuarios externos aportar información ambiental de la región desde el campo
- **Almacenamiento de datos brutos de la app móvil** en la base de datos Cloud (Strapi)
- **Sistema de recopilación de datos en On-Premise** para especialistas GIS (datos brutos y análisis) mediante QGIS/ArcGIS Pro, sin acceso directo a la base de datos
- **Sistema de replicación ETL** de datos desde On-Premise hacia Cloud para sincronización
- **Integración con la API del MINAM** para publicar información en el SIAR del MINAM (el MINAM ya cuenta con la estructura y páginas del SIAR de cada gobierno regional)
- **Sistema de sincronización** que envíe datos desde Cloud hacia el API del MINAM para visualización en el SIAR
- Despliegue y configuración de la infraestructura en la nube (Cloud) para Backend CMS
- Compilación y publicación de la Aplicación Móvil nativa (Android APK/AAB e iOS IPA)
- Integración con el Servidor GIS On-Premise de la GRRNGA (GeoServer) para servicios OGC
- **Arquitectura flexible** que permita el uso de tecnologías alternativas manteniendo la estructura arquitectónica
- **Entrega del código fuente completo** con todos los derechos de propiedad intelectual para el Gobierno Regional de La Libertad
- **Repositorio Git** con todo el código fuente de las aplicaciones (App Móvil y Backend CMS) con historial completo de commits
- Capacitación y transferencia tecnológica

#### 2.2.4. Arquitectura General del Sistema

##### Vista General de la Arquitectura

La plataforma SIAR implementa una **arquitectura híbrida desacoplada** que combina servicios en la nube (Backend CMS y App Móvil) con infraestructura On-Premise (Servidor Geoespacial y Base de Datos GIS), e integración con la API del MINAM para visualización en el SIAR del MINAM.

**Diagrama de Arquitectura:**

```mermaid
graph TB
    subgraph USUARIOS["USUARIOS FINALES"]
        CIUDADANOS[Usuarios Ciudadanos]
        ESPECIALISTAS[Especialistas GIS]
    end

    subgraph CLOUD["CLOUD"]
        subgraph PRESENTACION["CAPA DE PRESENTACIÓN"]
            APP[App Móvil Colaborativa<br/>React Native / Flutter]
        end
        
        subgraph APLICACION["CAPA DE APLICACIÓN"]
            STRAPI[Strapi CMS<br/>Backend Node.js<br/>- Gestión contribuciones<br/>- Moderación<br/>- Integración API MINAM]
        end
        
        subgraph DATOS_CLOUD["CAPA DE DATOS (Cloud)"]
            BD_CLOUD[(PostgreSQL Cloud<br/>Schema: strapi<br/>Schema: public_data)]
        end
    end

    subgraph ONPREMISE["ON-PREMISE (GRRNGA)"]
        QGIS[Estaciones GIS<br/>QGIS / ArcGIS Pro]
        POSTGIS[(PostgreSQL + PostGIS<br/>- gis_working<br/>- gis_master<br/>- gis_temp)]
        GEOSERVER[GeoServer<br/>Puerto 8080<br/>Servicios OGC]
        ETL[Script ETL Python<br/>Cron: Diario 2:00 AM]
    end

    subgraph EXTERNO["EXTERNO"]
        API_MINAM[API del MINAM<br/>HTTPS]
        SIAR_MINAM[SIAR del MINAM<br/>Visualización Pública]
    end

    CIUDADANOS -->|Contribuciones| APP
    APP -->|REST API HTTPS| STRAPI
    STRAPI -->|Lee datos| BD_CLOUD
    STRAPI -->|HTTP POST/PUT HTTPS| API_MINAM
    API_MINAM --> SIAR_MINAM

    ESPECIALISTAS -->|Carga datos| QGIS
    QGIS -->|Conexión local| POSTGIS
    POSTGIS -->|SQL queries| GEOSERVER
    GEOSERVER -.->|Servicios OGC| APP
    
    POSTGIS -->|Lee datos| ETL
    ETL -->|Replicación<br/>VPN/TLS| BD_CLOUD
    
    style CLOUD fill:#e1f5ff
    style ONPREMISE fill:#fff4e1
    style EXTERNO fill:#e8f5e9
```

**Flujo de Datos:**

1. **App Móvil → Cloud:**
   - Usuario ciudadano → App Móvil → Strapi API (HTTPS) → PostgreSQL Cloud (schema:strapi)

2. **Especialistas GIS → On-Premise:**
   - Especialista → QGIS/ArcGIS Pro → PostgreSQL On-Premise (conexión local)

3. **On-Premise → Cloud (Replicación):**
   - Script ETL (On-Premise) lee PostgreSQL On-Premise (localhost)
   - Script ETL se conecta a PostgreSQL Cloud (VPN/conexión TLS)
   - Replica datos a schema:public_data

4. **Cloud → MINAM:**
   - Strapi CMS lee datos de PostgreSQL Cloud (ambos schemas)
   - Strapi procesa y transforma datos
   - Strapi envía al API del MINAM (HTTPS)
   - MINAM publica en SIAR

##### Flexibilidad Tecnológica y Alternativas

**Principio de Flexibilidad Arquitectónica:**

El arquitecto o jefe de proyecto de la empresa proveedora del servicio **puede elegir tecnologías alternativas** a las mencionadas en este documento, siempre y cuando se **respete la estructura y arquitectura** descrita. La arquitectura debe mantener sus principios fundamentales: desacoplamiento, escalabilidad, seguridad y cumplimiento de estándares.

**Estructura Arquitectónica Obligatoria:**

La siguiente estructura de capas y flujos debe mantenerse independientemente de las tecnologías elegidas:

1. **Capa de Presentación** (App Móvil)
   - Aplicación móvil nativa multiplataforma
   - Arquitectura desacoplada del backend
   - Comunicación mediante APIs REST/GraphQL estandarizadas
   - Almacenamiento de contribuciones en Cloud (NO On-Premise)

2. **Capa de Aplicación** (Backend CMS en Cloud)
   - Headless CMS o Backend API
   - Gestión de contenido y contribuciones colaborativas
   - Integración con API del MINAM para publicación
   - APIs para App Móvil

3. **Capa de Datos**
   - Separación Cloud (CMS y contribuciones) / On-Premise (GIS especialistas)
   - Replicación ETL de On-Premise a Cloud
   - Estándares de datos geoespaciales (OGC)
   - Esquemas de base de datos definidos

4. **Integración Externa**
   - API del MINAM para publicación en SIAR
   - Sincronización de datos validados desde Cloud

**Tecnologías Alternativas Permitidas:**

**NOTA:** Ya no se desarrolla un Portal Web propio. La visualización se realiza mediante el SIAR del MINAM usando su API.

**Aplicación Móvil (Tecnologías Permitidas):**
- **React Native** - Framework multiplataforma nativo (recomendado)
- **Flutter** - Framework multiplataforma con Dart
- **Xamarin/.NET MAUI** - Para equipos .NET
- **Kotlin Multiplatform Mobile (KMM)** - Lógica compartida con UI nativa
- **Requirement:** Debe ser tecnología multiplataforma nativa con renderizado nativo y acceso completo a APIs del dispositivo

**Backend CMS (Alternativas a Strapi):**
- **Directus** - Headless CMS con SQL
- **Payload CMS** - TypeScript-first CMS
- **Sanity** - Headless CMS con editor en tiempo real
- **Contentful** (SaaS) - CMS gestionado
- **WordPress Headless** (Headless WordPress)
- **DatoCMS** (SaaS) - CMS moderno
- **Requirement:** Debe soportar autenticación, roles, APIs REST/GraphQL, gestión de usuarios colaborativos

**Base de Datos (Alternativas a PostgreSQL):**
- **MySQL/MariaDB** con extensión espacial
- **MongoDB** (para CMS, mantener PostGIS para GIS)
- **CockroachDB** (PostgreSQL compatible)
- **Requirement:** Para GIS On-Premise, mantener PostgreSQL/PostGIS (estándar)

**Servidor Geoespacial (Alternativas a GeoServer - todas Open Source):**
- **MapServer** - Open source, más ligero que GeoServer
- **QGIS Server** - Basado en QGIS, open source
- **Requirement:** Debe exponer servicios OGC estándar (WMS, WFS, WMTS), debe ser open source

**Librerías de Mapas (Alternativas a Leaflet/MapLibre):**
- **OpenLayers** - Librería robusta para GIS web
- **Cesium** - Para visualización 3D
- **Google Maps API** / **Mapbox** - Si presupuesto lo permite
- **Requirement:** Compatible con servicios OGC

**Proceso de Aprobación de Alternativas:**

1. **Propuesta Técnica:**
   - La empresa proveedora debe presentar justificación técnica de tecnologías alternativas
   - Comparativa con tecnologías sugeridas
   - Análisis de impacto en mantenibilidad y escalabilidad

2. **Criterios de Evaluación:**
   - Cumplimiento de requisitos funcionales
   - Compatibilidad con estándares (OGC, REST, OpenAPI)
   - Rendimiento y escalabilidad equivalentes
   - Facilidad de mantenimiento y transferencia de conocimiento
   - Costos de licencias (si aplica)

3. **Aprobación:**
   - Revisión por parte de GRRNGA (Ingeniero Informático)
   - Aprobación escrita antes de inicio de desarrollo
   - Documentación de decisiones técnicas en el proyecto

**Documentación Requerida para Alternativas:**

- Diagrama de arquitectura actualizado con tecnologías elegidas
- Justificación técnica de cada elección
- Matriz de compatibilidad con requisitos
- Plan de transferencia de conocimiento con tecnologías elegidas
- Guías de instalación y configuración

**Garantías y Compatibilidad:**

Independientemente de las tecnologías elegidas, el sistema debe:
- Mantener **interoperabilidad** con sistemas externos (SINIA, GeoPerú)
- Cumplir con **estándares de seguridad** (OAuth 2.0, JWT, HTTPS)
- Soportar **APIs públicas documentadas** (OpenAPI/Swagger)
- Ser **escalable** para 1M+ visitas/año
- Tener **documentación técnica completa** para mantenimiento

**Ejemplo de Aplicación:**

Si el arquitecto decide usar **Flutter en lugar de React Native** para la app móvil:
- Debe ser framework multiplataforma nativo equivalente
- Debe consumir APIs del backend Strapi
- Debe almacenar contribuciones directamente en Cloud (Strapi)
- Debe tener renderizado nativo y acceso completo a APIs del dispositivo
- Debe integrarse con servicios OGC del GeoServer para mapas

#### 2.2.5. Componentes del Sistema por Capas

##### Servidor Geoespacial (GeoServer)

El Servidor Geoespacial es el **intermediario esencial** que permite que la App Móvil consuma los datos geográficos de forma segura y optimizada.

##### ¿Por qué es necesario?

**La App Móvil NUNCA se conecta directamente a la base de datos PostGIS.** En su lugar, la App Móvil consume **servicios web estandarizados (OGC)** que expone el Servidor Geoespacial.

**Flujo:**
```
App Móvil (React Native Maps) 
    → HTTP Request: http://gis.regionlalibertad.gob.pe:8080/geoserver/siar/wms?layer=anp&bbox=...
        → GeoServer recibe petición
            → GeoServer consulta PostGIS: SELECT geom FROM anp WHERE ...
                → GeoServer renderiza y transforma
                    → GeoServer devuelve PNG/JSON a la App Móvil
```

Las aplicaciones móviles **no pueden** ejecutar consultas SQL directamente contra PostgreSQL por razones de seguridad y compatibilidad. El Servidor Geoespacial realiza esta transformación de forma segura.

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

**5. Expone Servicios OGC que consume la App Móvil**

Estos servicios HTTP son consumidos por la aplicación móvil para mostrar mapas:

| Servicio | URL Ejemplo | Qué retorna | Consumido por |
|----------|-------------|-------------|---------------|
| **WMS** | `http://gis.regionlalibertad.gob.pe:8080/geoserver/siar/wms?LAYERS=anp&...` | Imagen PNG del mapa | **App Móvil** (visualización de mapas) |
| **WFS** | `http://gis.regionlalibertad.gob.pe:8080/geoserver/siar/wfs?TYPENAME=cuencas&...` | GeoJSON con geometrías | **App Móvil** (descargas, análisis) |
| **WMTS** | `http://gis.regionlalibertad.gob.pe:8080/geoserver/gwc/service/wmts?layer=siar:basemap&...` | Tile PNG 256x256 | **App Móvil** (cache offline para modo sin conexión) |
| **WCS** | `http://gis.regionlalibertad.gob.pe:8080/geoserver/siar/wcs?COVERAGEID=dem&...` | GeoTIFF (raster) | **App Móvil** (descargas especializadas) |

**Nota:** El dominio `gis.regionlalibertad.gob.pe` corresponde al dominio específico del Gobierno Regional de La Libertad para el servidor geoespacial. Este dominio debe configurarse según el dominio oficial del Gobierno Regional de La Libertad. GRRNGA = Gerencia Regional de Recursos Naturales y Gestión Ambiental.

**IMPORTANTE:** La App Móvil SOLO hace peticiones HTTP a estos endpoints. Nunca ejecuta SQL ni se conecta directamente a PostgreSQL.

**6. Control de Acceso y Seguridad**
- Autenticación básica o integración con LDAP/Active Directory
- Reglas de acceso por capa: `anp_piaci` solo visible para usuarios autenticados
- Rate limiting: 100 requests/minuto por IP
- Logs de auditoría: quién descargó qué capa y cuándo

##### ¿Dónde se instala?

**Ubicación:** Servidor físico On-Premise GRRNGA (mismo servidor que aloja PostgreSQL/PostGIS)

**Configuración de red:**
- **IP interna:** 192.168.X.X (red local GRRNGA)
- **Firewall:** Puerto 8080 (GeoServer) abierto para:
  - Acceso interno: Red local GRRNGA (sin restricciones)
  - Acceso externo: Solo desde IPs del servicio cloud que aloja Strapi y desde donde se conecta la App Móvil
- **DNS/NAT:** `gis.regionlalibertad.gob.pe` (o el dominio específico del Gobierno Regional de La Libertad) redirige al servidor On-Premise
  - **Nota:** Este dominio debe ser el dominio oficial del Gobierno Regional de La Libertad. Debe configurarse según el dominio institucional disponible.

**Requisitos de hardware (ya incluidos en especificaciones del Paquete 1):**
- RAM: 16-32 GB dedicados (del total de 128 GB del servidor)
- CPU: 4-8 cores asignados
- Disco: 100-200 GB para cache de tiles

##### ¿Cómo se integra con el resto de la arquitectura?

**Conexiones de la App Móvil - Arquitectura Desacoplada:**

La App Móvil tiene **DOS conexiones independientes**:
1. **App Móvil → Strapi (REST API) → BD Cloud:** Obtiene metadatos, noticias, indicadores, texto editorial
2. **App Móvil → GeoServer (OGC HTTP) → BD PostGIS On-Premise:** Obtiene capas geográficas (imágenes, tiles, vectores)

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
   - Campo `endpoints.wms`: `http://gis.regionlalibertad.gob.pe:8080/.../wms`
   - Campo `endpoints.wfs`: `http://gis.regionlalibertad.gob.pe:8080/.../wfs`
5. **App Móvil** consulta Strapi API para obtener metadatos:
   - `GET /api/geo-layers?filters[theme][slug]=biodiversidad`
   - Respuesta incluye URLs de servicios OGC del GeoServer
6. **App Móvil** (React Native Maps) hace peticiones HTTP a GeoServer:
   ```javascript
   // App Móvil hace petición HTTP al GeoServer, NO a la BD
   <MapView>
     <UrlTile
       urlTemplate="http://gis.regionlalibertad.gob.pe:8080/geoserver/siar/gwc/service/wmts?layer=siar:areas_protegidas&..."
     />
   </MapView>
   ```
7. **GeoServer** consulta PostGIS, renderiza y devuelve PNG/Tiles a la App Móvil
8. **Usuario final** visualiza el mapa en tiempo real en su dispositivo móvil

**Decisión Tecnológica - GeoServer (Open Source):**

Se utiliza **GeoServer** como servidor geoespacial para el proyecto SIAR debido a:

**Ventajas:**
- **Costo cero en licencias** - Optimización del presupuesto
- **Open Source (GPL)** - Sin restricciones de uso
- **Integración perfecta** con PostgreSQL/PostGIS (stack open source completo)
- **Compatibilidad nativa** con PostGIS - Sin configuración adicional compleja
- **Formatos soportados** - 50+ formatos (Shapefile, GeoTIFF, MBTiles, etc.)
- **Comunidad activa** - OSGeo Foundation con documentación extensa
- **Performance excelente** con configuración correcta para la escala del proyecto
- **Escalabilidad suficiente** para 1M+ visitas/año del portal
- **Instalación simple** - Java (JRE 11+), standalone o Tomcat
- **Interfaz web intuitiva** - Curva de aprendizaje media

**Requisitos de Instalación:**
- Java Runtime Environment (JRE 11+) o Java Development Kit (JDK 11+)
- Puede ejecutarse standalone o sobre servidor de aplicaciones (Tomcat, Jetty)
- Compatible con sistemas operativos Linux (recomendado) y Windows

##### Capa de Presentación - Frontend

**NOTA IMPORTANTE:** Ya no se desarrolla un Portal Web propio. La visualización de la información se realiza mediante el **SIAR del MINAM**, que ya cuenta con la estructura y páginas del SIAR para cada gobierno regional. El sistema desarrollado se enfoca únicamente en:

1. **Aplicación Móvil Colaborativa** - Para recopilación de datos desde el campo
2. **Backend CMS** - Para gestión y procesamiento de datos
3. **Integración con API del MINAM** - Para publicación en el SIAR

##### Aplicación Móvil Colaborativa (Producto Independiente)

**La aplicación móvil es un producto completamente separado del portal web**, desarrollada con tecnología multiplataforma nativa con enfoque colaborativo. **Es la única plataforma que permite a usuarios aportar información ambiental desde el campo**. No se genera a partir del portal web ni utiliza Capacitor o tecnologías híbridas basadas en WebView.

**Propósito Colaborativo:**
La app móvil está diseñada específicamente para permitir que ciudadanos, investigadores, instituciones y organizaciones aporten información ambiental de manera colaborativa directamente desde sus dispositivos móviles mientras están en campo, aprovechando sensores del celular (GPS, cámara, etc.).

**Tecnología Principal Recomendada:**
- **React Native** (Meta/Facebook) - Framework multiplataforma más popular
  - Desarrollo con JavaScript/TypeScript
  - Compilación nativa para Android e iOS
  - Acceso completo a APIs nativas del dispositivo
  - Comunidad grande y ecosistema robusto

**Tecnologías Alternativas Permitidas (Arquitecto decide):**
- **Flutter** (Google/Dart) - Framework multiplataforma de alto rendimiento
- **Xamarin/.NET MAUI** (Microsoft) - Para equipos con experiencia .NET
- **Kotlin Multiplatform Mobile (KMM)** - Para aplicaciones nativas con lógica compartida

**Requisitos para la Tecnología Móvil:**
- Debe ser tecnología multiplataforma nativa con renderizado nativo
- Debe proporcionar acceso completo a APIs nativas del dispositivo (GPS, cámara, sensores)
- Debe permitir compilación nativa para Android e iOS

**Arquitectura de la App Móvil:**

**IMPORTANTE - Almacenamiento de Datos:**
- **La App Móvil guarda datos DIRECTAMENTE en Cloud (Strapi)**, NO en On-Premise
- Las contribuciones ciudadanas se envían inmediatamente a Strapi API (Cloud)
- Los datos brutos (fotos, coordenadas GPS, observaciones) se almacenan en BD Cloud (schema:strapi)
- **NO hay almacenamiento intermedio en On-Premise** para datos de la app móvil

**Separación completa:**
- Código base independiente (repositorio separado)
- Ciclo de desarrollo independiente
- Despliegue independiente a Play Store / App Store
- Comparte únicamente las APIs del backend:
  - Strapi REST API para contenido y autenticación (Cloud)
  - GeoServer OGC para servicios geoespaciales (On-Premise, solo lectura)

**Stack Tecnológico Recomendado (React Native):**
- **React Native 0.72+** con **TypeScript**
- **React Navigation** (navegación)
- **React Query / TanStack Query** (gestión de estado servidor)
- **Zustand / Redux Toolkit** (gestión de estado local)
- **React Hook Form + Zod** (formularios)
- **React Native Maps** (integración de mapas nativos)
- **React Native Camera** o **expo-camera** (acceso a cámara)
- **React Native Geolocation** (GPS nativo)
- **AsyncStorage / MMKV** (almacenamiento local)
- **React Native Paper** o **NativeBase** (UI components)

**Sistema de Usuarios y Autenticación:**

**IMPORTANTE - Usuarios de la App Móvil:**
- **La aplicación móvil está dirigida a la ciudadanía general** - No es para uso interno del Gobierno Regional
- **Autenticación mediante OAuth 2.0** - Integración con proveedores externos:
  - **Google Sign-In** (OAuth 2.0)
  - **Apple Sign-In** (OAuth 2.0)
  - Autenticación simple y general para facilitar el acceso ciudadano
- **No requiere credenciales internas** - Los usuarios se registran con sus cuentas personales (Google/Apple)

**Tipos de Usuario en la App Móvil (Ciudadanía):**
1. **Usuario Registrado** (contribuyente colaborativo ciudadano)
   - Registro mediante OAuth 2.0 (Google o Apple)
   - Perfil de usuario personalizable
   - Contribución de datos ambientales desde el campo (sujeto a moderación)
   - Historial de contribuciones personales
   - Sistema de reputación/badges

2. **Usuario Verificado** (instituciones, investigadores externos)
   - Verificación manual mediante documentación subida desde la app
   - Mayor credibilidad en contribuciones
   - Contribuciones con menor moderación
   - Acceso a estadísticas de sus aportes

**Funcionalidades Colaborativas en la App Móvil:**

**Módulo de Contribuciones (Funcionalidad Principal):**

1. **Formularios Colaborativos por Temática Ambiental:**
   - **Reporte de Observaciones Ambientales:**
     - Calidad del agua (transparencia, color, presencia de residuos)
     - Calidad del aire (visibilidad, olores, contaminación visible)
     - Estado de biodiversidad (presencia de especies, estado de ecosistemas)
   - **Registro Fotográfico Geo-referenciado:**
     - Fotos de especies, ecosistemas, amenazas ambientales
     - Captura automática de coordenadas GPS
     - Timestamp automático
     - Descripción y etiquetas
   - **Carga de Datos de Campo:**
     - Mediciones ambientales (temperatura, pH, etc.)
     - Series temporales desde campo
     - Datos de monitoreo ciudadano
   - **Reporte de Incidencias:**
     - Vertimientos, deforestación, contaminación
     - Ubicación precisa con GPS
     - Evidencia fotográfica/videográfica
   - **Registro de Especies:**
     - Aves, flora, fauna observada
     - Ubicación exacta
     - Fotos y descripción

2. **Características Técnicas de Contribuciones:**
   - Captura automática de coordenadas GPS (alta precisión)
   - Integración con cámara nativa para fotos/videos
   - Selección de ubicación en mapa si GPS no disponible
   - Modo offline: guardar contribuciones localmente y sincronizar después
   - Validación de formularios antes de envío
   - Preview de contribución antes de enviar

3. **Sistema de Moderación:**
   - Cola de revisión para contribuciones
   - Workflow de aprobación multi-nivel
   - Notificaciones push sobre estado de aportes
   - Historial completo de cambios y versionado
   - Feedback a contribuyentes sobre aprobación/rechazo

4. **Reconocimiento y Participación:**
   - Dashboard personal de contribuciones del usuario
   - Ranking de colaboradores más activos
   - Badges por número de aportes validados
   - Certificados de participación (opcional, descargables)
   - Créditos en publicaciones generadas con datos colaborativos

**Requisitos Funcionales Móviles:**
- **Gestión de cuentas de usuario** completa para ciudadanía (registro, login, perfil)
- **Autenticación mediante OAuth 2.0** - Integración con Google Sign-In y Apple Sign-In (no credenciales internas)
- **Contribuciones colaborativas** como funcionalidad principal
- Carga de fotografías/videos geo-referenciadas con cámara nativa
- Captura automática de GPS de alta precisión
- Modo offline completo: trabajar sin conexión, sincronizar después
- Visualización de mapas con servicios OGC (WMS/WMTS)
- Descarga de capas geoespaciales para uso offline
- Notificaciones push sobre estado de contribuciones

**Outputs Nativos:**
- **Android APK/AAB** (API Level 26+, Android 8.0+) - **Prioritario**
  - Compilación nativa desde código React Native
  - Firma con keystore para Play Store
  - Compatibilidad con 95%+ de dispositivos en Perú
- **iOS IPA** (iOS 13+) - **Opcional fase 2**
  - Compilación nativa desde código React Native
  - Requiere cuenta de desarrollador Apple
  - Solo si el presupuesto lo permite

**Características Móviles Específicas:**
- Acceso completo a sensores nativos (GPS de alta precisión, cámara, acelerómetro)
- Modo offline-first: funcionalidad completa sin conexión
- Sincronización bidireccional al recuperar conectividad
- Almacenamiento local de contribuciones pendientes
- Push notifications nativas para notificaciones de moderación
- Optimización de bundle size para datos móviles
- Uso eficiente de batería para trabajo en campo prolongado

**Flujo de Datos de la App Móvil:**

1. **Usuario ciudadano** captura datos en campo (foto, GPS, observación)
2. **App Móvil** guarda localmente (modo offline) o envía inmediatamente
3. **Strapi API (Cloud)** recibe la contribución
4. **BD Cloud (schema:strapi)** almacena datos brutos
5. **Editor Ambiental** modera y valida en Strapi CMS
6. **Datos validados** se procesan y preparan para publicación
7. **API del MINAM** recibe datos validados desde Strapi
8. **SIAR del MINAM** publica y visualiza la información

**NOTA:** La visualización final se realiza en el SIAR del MINAM, no en un portal propio.

##### Capa de Aplicación - Backend CMS

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

7. **UserContribution** (Contribuciones Colaborativas)
   - contributor (relation → User)
   - contributionType (enum: Observation, Photo, DataSeries, GeoLayer, Suggestion)
   - title, description, location (JSON coordinates)
   - files (media: photos, videos, documents)
   - theme (relation), scope (relation)
   - status (enum: Pending, Approved, Rejected, Published)
   - moderationNotes (text, solo para editores)
   - metadata (JSON: fecha observación, condiciones ambientales, etc.)
   - publishedAt, moderatedAt, moderatedBy (relation → User)
   - votes/likes (count)

8. **User** (Usuarios de la Plataforma)
   - username, email, password (hashed)
   - firstName, lastName, institution (optional)
   - userType (enum: Public, Registered, Verified, Editor)
   - verificationStatus (enum: Unverified, Pending, Verified)
   - verificationDocuments (media, optional)
   - profileImage (media)
   - contributions (relation → UserContribution, one-to-many)
   - reputationScore (integer)
   - badges (array)
   - apiTokens (relation → ApiToken, one-to-many)

9. **ApiToken** (Tokens de API Externa)
   - token (hashed), name, description
   - user (relation → User)
   - scopes (array: read, write, geo, etc.)
   - rateLimit (integer: requests per minute)
   - expiresAt (datetime, optional)
   - lastUsedAt (datetime)
   - isActive (boolean)

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

**Roles y Permisos del CMS:**

**IMPORTANTE - Usuarios del CMS (Backend):**
- **El CMS es exclusivo para uso interno del Gobierno Regional de La Libertad y Municipalidades**
- **Acceso restringido** - Solo personal autorizado puede acceder al panel de administración
- **Autenticación específica** - Credenciales administradas por el Gobierno Regional (no OAuth externo)
- **Separado de usuarios de la App Móvil** - Los usuarios ciudadanos de la app no tienen acceso al CMS

**Roles del CMS (Personal del Gobierno Regional y Municipalidades):**

1. **Super Admin** (GRRNGA)
   - Control total del sistema
   - Gestión de usuarios y permisos
   - Configuración general del sistema

2. **Editor Ambiental** (GRRNGA)
   - CRUD completo sobre Indicators, Documents, News, LegalNorms
   - Moderación y aprobación de contribuciones colaborativas de la app móvil
   - Gestión de contenido editorial

3. **Editor GIS** (GRRNGA)
   - CRUD sobre GeoLayers
   - Actualización de endpoints de servicios OGC
   - Gestión de metadatos geoespaciales

4. **Editor Municipal** (Municipalidades)
   - CREATE/UPDATE limitado a su ámbito territorial específico
   - Gestión de contenido relacionado con su jurisdicción
   - Sin acceso a contenido de otras municipalidades

**Notas Importantes:**
- **Portal Web:** Es público, no tiene usuarios ni autenticación
- **App Móvil:** Usuarios ciudadanos con OAuth 2.0 (Google/Apple) - separados del CMS
- **CMS:** Usuarios específicos del Gobierno Regional y Municipalidades - acceso restringido
- Las contribuciones colaborativas solo se pueden realizar desde la aplicación móvil, no desde el portal web

**APIs Generadas:**
- **REST API:** `/api/indicators`, `/api/documents`, etc.
  - Filtros: `?filters[theme][slug][$eq]=agua`
  - Población: `?populate=theme,scope,timeSeries`
  - Paginación: `?pagination[page]=1&pagination[pageSize]=25`
  - Ordenamiento: `?sort[0]=publishedAt:desc`
- **GraphQL API:** Endpoint `/graphql` con schema auto-generado

**Autenticación del CMS:**
- **Autenticación interna** - Sistema de credenciales propio del CMS (email/password)
- **No usa OAuth externo** - Los usuarios del CMS se autentican con credenciales administradas por el Gobierno Regional
- **JWT** para sesiones de administración
- **API Tokens** para integraciones externas (API pública documentada)
- **Acceso restringido** - Solo desde red interna (VPN) o con control de acceso estricto

**Hosting Recomendado (uno de los siguientes):**
- **AWS:** EC2 + RDS PostgreSQL + S3
- **Google Cloud:** Cloud Run + Cloud SQL + Cloud Storage (recomendado por facilidad)
- **Railway/Render** (alternativas económicas para instituciones públicas)

##### Integración con API del MINAM para Publicación en SIAR

**Objetivo:** Publicar la información ambiental de La Libertad en el SIAR del MINAM mediante su API. El MINAM ya cuenta con la estructura y páginas del SIAR para cada gobierno regional.

**¿Quién realiza la integración?**
- **Strapi CMS (Cloud)** - Sistema automatizado que envía datos al API del MINAM
- **Editor Ambiental (GRRNGA)** - Valida y aprueba datos antes de publicación
- **Sistema programado** - Sincronización automática según frecuencia configurada

**¿Cómo se realiza la integración?**
- **Método:** Consumo de API REST del MINAM (HTTPS)
- **Autenticación:** API Key o OAuth 2.0 proporcionado por el MINAM
- **Formato de datos:** JSON según especificación del API del MINAM
- **Transformación:** Strapi transforma datos internos al formato requerido por el MINAM

**¿Cuándo se realiza la integración?**
- **Frecuencia programada:** Diaria (2:00 AM) o según configuración
- **Trigger manual:** Editor Ambiental puede forzar sincronización desde Strapi CMS
- **Eventos:** Cuando se aprueban contribuciones colaborativas o se actualizan datos

**¿Dónde se realiza la integración?**
- **Origen de datos:** PostgreSQL Cloud (BD Cloud con datos validados en schemas:strapi y public_data)
- **Procesador:** Strapi CMS en Cloud (aplicación Node.js que lee de PostgreSQL y procesa)
- **Destino:** API del MINAM (endpoint HTTPS proporcionado por el MINAM)
- **Visualización final:** SIAR del MINAM - Página del SIAR La Libertad

**Aclaración:**
- PostgreSQL Cloud no envía directamente al MINAM (las bases de datos no hacen HTTP requests)
- Strapi CMS (aplicación Node.js) lee de PostgreSQL Cloud y envía al API del MINAM mediante HTTP

**Flujo de Integración con MINAM:**

1. **Recopilación de Datos:**
   - **App Móvil:** Contribuciones ciudadanas → Strapi API (Cloud) → PostgreSQL Cloud (schema:strapi)
   - **Especialistas GIS:** Datos y análisis → PostGIS On-Premise (schema:gis_working) → Validación → PostGIS On-Premise (schema:gis_master)

2. **Replicación ETL (On-Premise → Cloud):**
   - **Script ETL** (ejecutado en servidor On-Premise) lee datos de PostGIS On-Premise (schema:gis_master)
   - **Conexión segura** (VPN o conexión directa con firewall) hacia PostgreSQL Cloud
   - **Replicación** de datos procesados a PostgreSQL Cloud (schema:public_data)
   - **Frecuencia:** Diaria 2:00 AM o manual

3. **Procesamiento y Validación en Strapi:**
   - **Editor Ambiental:** Modera contribuciones colaborativas en Strapi CMS (desde BD Cloud schema:strapi)
   - **Editor GIS:** Valida datos geoespaciales replicados (desde BD Cloud schema:public_data)
   - **Datos validados** se marcan como "listos para publicación" en Strapi

4. **Preparación para MINAM (Strapi lee de PostgreSQL Cloud):**
   - **Strapi CMS** lee datos validados desde PostgreSQL Cloud:
     - Datos colaborativos: schema:strapi (contribuciones aprobadas)
     - Datos geoespaciales: schema:public_data (datos replicados desde On-Premise)
   - **Strapi procesa y transforma** los datos al formato JSON requerido por API del MINAM
   - **Validación** de metadatos obligatorios según estándares SINIA
   - **Agregación** de datos de ambos schemas si es necesario

5. **Envío al API del MINAM:**
   - **Strapi CMS** (aplicación Node.js) envía datos mediante HTTPS al API del MINAM
   - **Método:** HTTP POST/PUT requests desde Strapi hacia endpoints del MINAM
   - **Autenticación:** API Key o OAuth 2.0 proporcionado por el MINAM
   - **Formato:** JSON según especificación del API del MINAM
   - **Confirmación:** Strapi recibe respuesta del MINAM y registra estado

6. **Publicación en SIAR:**
   - **MINAM procesa** los datos recibidos desde Strapi
   - **MINAM publica** en el SIAR (página La Libertad)
   - **Visualización** en el SIAR del MINAM
   - **Usuarios finales** acceden al SIAR del MINAM para consultar información

**Diagrama del Flujo:**

```mermaid
flowchart LR
    subgraph ONPREMI["On-Premise"]
        POSTGIS_LOCAL[(PostgreSQL On-Premise<br/>gis_master)]
        ETL_SCRIPT[Script ETL Python<br/>Lee datos]
    end
    
    subgraph CLOUD_BD["Cloud - Base de Datos"]
        POSTGIS_CLOUD[(PostgreSQL Cloud<br/>public_data)]
    end
    
    subgraph CLOUD_APP["Cloud - Aplicación"]
        STRAPI[Strapi CMS<br/>Node.js<br/>Lee, procesa y transforma]
    end
    
    subgraph MINAM_EXT["Externo"]
        API_MINAM[API del MINAM<br/>HTTPS]
        SIAR[SIAR del MINAM<br/>Visualización]
    end
    
    POSTGIS_LOCAL -->|1. Lee datos| ETL_SCRIPT
    ETL_SCRIPT -->|2. Replica<br/>VPN/TLS| POSTGIS_CLOUD
    POSTGIS_CLOUD -->|3. Lee datos| STRAPI
    STRAPI -->|4. Envía datos<br/>HTTP POST/PUT<br/>HTTPS| API_MINAM
    API_MINAM -->|5. Publica| SIAR
    
    style ONPREMI fill:#fff4e1
    style CLOUD_BD fill:#e1f5ff
    style CLOUD_APP fill:#e1f5ff
    style MINAM_EXT fill:#e8f5e9
```

**Aclaración:**
- PostgreSQL es una base de datos, no puede enviar HTTP requests
- Strapi es una aplicación Node.js que puede hacer HTTP requests
- Strapi (capa de aplicación) lee de PostgreSQL Cloud y envía al API del MINAM
- Flujo: BD → Aplicación (Strapi) → API Externa (MINAM)

**Endpoints del API del MINAM (Ejemplo - Confirmar con MINAM):**
- `POST /api/siar/regiones/lalibertad/indicadores` - Publicar indicadores
- `POST /api/siar/regiones/lalibertad/documentos` - Publicar documentos
- `POST /api/siar/regiones/lalibertad/capas-geoespaciales` - Publicar capas
- `PUT /api/siar/regiones/lalibertad/actualizar/:id` - Actualizar datos existentes
- `GET /api/siar/regiones/lalibertad/estado` - Verificar estado de sincronización

**Requisitos Técnicos:**
- **Formato de datos:** JSON según especificación del MINAM
- **Metadatos obligatorios:** Título, resumen, temática, ámbito territorial, fecha, fuente
- **Estándares:** Compatible con estructura SINIA y taxonomía de 13 temáticas
- **Versionado:** Mantener historial de cambios para auditoría
- **Manejo de errores:** Reintentos automáticos en caso de fallo de conexión
- **Logging:** Registro completo de sincronizaciones y errores

**Monitoreo:**
- Dashboard en Strapi CMS con estado de sincronización
- Alertas por email en caso de fallos
- Logs de todas las operaciones de integración
- Métricas de datos enviados y publicados

##### API Pública Documentada para Uso Externo

**Objetivo:** Proporcionar acceso controlado y documentado a los datos del SIAR para desarrolladores externos, otras aplicaciones, instituciones y personas interesadas en integrar información ambiental regional.

**Portal de Documentación API:**

**Características del Portal:**
- **URL pública:** `https://api.siar.regionlalibertad.gob.pe/docs` o `https://siar.regionlalibertad.gob.pe/api-docs`
  - **Nota:** Estos dominios deben ser los dominios oficiales del Gobierno Regional de La Libertad. Deben configurarse según el dominio institucional disponible.
- **Interfaz interactiva** tipo Swagger UI / OpenAPI / Redoc
- **Documentación completa** de todos los endpoints disponibles
- **Ejemplos de código** en múltiples lenguajes (JavaScript, Python, cURL)
- **Try it out** (probador interactivo de endpoints)
- **Sistema de solicitud de permisos** integrado

**Endpoints de la API Pública:**

**1. Endpoints Públicos (Sin Autenticación):**
- `GET /api/public/indicators` - Listado de indicadores ambientales públicos
- `GET /api/public/indicators/:id` - Detalle de indicador
- `GET /api/public/documents` - Documentos públicos
- `GET /api/public/norms` - Normas ambientales vigentes
- `GET /api/public/geo-layers/catalog` - Catálogo de capas geoespaciales disponibles
- `GET /api/public/statistics/theme/:slug` - Estadísticas por temática

**2. Endpoints Protegidos (Requieren Autenticación):**
- `GET /api/v1/indicators/full` - Indicadores con series temporales completas
- `GET /api/v1/geo-layers/:id/data` - Descarga de datos geoespaciales (GeoJSON, Shapefile)
- `POST /api/v1/contributions` - Envío de contribuciones colaborativas (requiere usuario registrado)
- `GET /api/v1/user/contributions` - Historial de contribuciones del usuario autenticado
- `GET /api/v1/geo-layers/query` - Consultas espaciales avanzadas (buffer, intersection)
- `POST /api/v1/time-series/bulk` - Carga masiva de series temporales (requiere permisos especiales)

**Sistema de Autenticación y Autorización:**

**1. Registro de Aplicaciones/Desarrolladores:**
- Formulario web para solicitar acceso a la API
- Campos requeridos:
  - Nombre de la aplicación/organización
  - Tipo de uso (Aplicación móvil, Sistema institucional, Investigación, Otro)
  - Descripción del propósito
  - Información de contacto
  - Términos y condiciones de uso
- Proceso de revisión manual por parte de GRRNGA
- Aprobación/Rechazo con notificación por email

**2. Métodos de Autenticación:**

**API Keys (Nivel Básico):**
- Al aprobar solicitud, se genera API Key única
- Incluida en header: `Authorization: Bearer <api_key>`
- Scopes limitados: solo lectura de datos públicos
- Rate limit: 1000 requests/día

**OAuth 2.0 (Nivel Avanzado):**
- Para aplicaciones que requieren permisos de escritura o acceso a datos sensibles
- Flow: Authorization Code Grant
- Scopes disponibles:
  - `read:indicators` - Lectura de indicadores
  - `read:geodata` - Lectura de datos geoespaciales
  - `write:contributions` - Escritura de contribuciones colaborativas
  - `read:full-series` - Acceso a series temporales completas
- Refresh tokens con expiración configurable
- Rate limit: según nivel de permisos (hasta 10,000 requests/día)

**3. Control de Acceso y Seguridad:**

**Rate Limiting:**
- Por API Key/Token: límites configurables según nivel
- Por IP: protección contra abuso (100 requests/minuto por IP)
- Headers de respuesta indican límites: `X-RateLimit-Limit`, `X-RateLimit-Remaining`

**CORS (Cross-Origin Resource Sharing):**
- Configuración por dominio registrado
- Solo dominios aprobados pueden hacer requests desde navegador
- Headers CORS apropiados en todas las respuestas

**Versionado:**
- Versión actual: `/api/v1/`
- Mantener versiones anteriores para compatibilidad
- Documentación clara de cambios entre versiones

**Validación y Sanitización:**
- Validación estricta de parámetros de entrada
- Sanitización de queries para prevenir SQL injection
- Validación de coordenadas geográficas y rangos permitidos

**Monitoreo y Auditoría:**
- Logging de todas las peticiones API (timestamp, IP, endpoint, usuario)
- Dashboard de métricas de uso por aplicación
- Alertas de uso anormal o potencial abuso
- Reportes mensuales de uso de API

**Documentación Técnica:**

**Formato OpenAPI 3.0:**
- Especificación completa en formato YAML/JSON
- Compatible con herramientas: Swagger UI, Postman, Insomnia
- Auto-generación de clientes SDK en múltiples lenguajes

**Secciones de Documentación:**
1. **Introducción** - Descripción general, casos de uso
2. **Autenticación** - Guía paso a paso para obtener credenciales
3. **Endpoints** - Documentación detallada de cada endpoint:
   - Método HTTP y URL
   - Parámetros (query, path, body)
   - Ejemplos de request/response
   - Códigos de error posibles
   - Rate limits específicos
4. **Modelos de Datos** - Schemas JSON de todas las entidades
5. **Ejemplos de Integración** - Casos de uso comunes
6. **Changelog** - Historial de cambios en la API
7. **Soporte** - Contacto para ayuda técnica

**Ejemplo de Solicitud de Permisos:**

Flujo en el portal de documentación:
1. Usuario visita `/api-docs`
2. Sección "Solicitar Acceso" → Formulario
3. Envío de solicitud → Notificación a administradores GRRNGA
4. Revisión manual (2-5 días hábiles)
5. Aprobación → Generación automática de API Key
6. Email con credenciales y guía de inicio rápido
7. Acceso inmediato a endpoints públicos
8. Solicitud de permisos adicionales si requiere endpoints protegidos

**Casos de Uso de la API Externa:**

1. **Aplicaciones Móviles de Terceros:**
   - Integración de mapas ambientales en apps turísticas
   - Alertas de calidad del aire en apps meteorológicas

2. **Sistemas Institucionales:**
   - Municipalidades integrando datos ambientales en sus portales
   - Universidades para proyectos de investigación
   - ONGs para monitoreo ambiental

3. **Plataformas de Análisis:**
   - Dashboards de Business Intelligence
   - Herramientas de visualización de datos (Tableau, Power BI)
   - Scripts de análisis estadístico (Python, R)

4. **Servicios Web:**
   - Mashups con otras fuentes de datos
   - Servicios de notificación automática
   - Webhooks para integraciones en tiempo real

##### Capa de Datos - Arquitectura Híbrida

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
- Ubuntu Server 22.04 LTS (Linux - Open Source, recomendado) o otra distribución Linux Server

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

**Servicios Geoespaciales:**
- **GeoServer 2.24+** (Open Source - Gratuito, recomendado)
- Conectado a PostgreSQL/PostGIS local
- Publica servicios OGC:
  - **WMS** (Web Map Service) - visualización
  - **WFS** (Web Feature Service) - descarga de vectores
  - **WMTS** (Web Map Tile Service) - tiles cacheados
  - **WCS** (Web Coverage Service) - rasters

**Endpoints Ejemplo:**
```
http://gis.regionlalibertad.local:8080/geoserver/siar/wms
http://gis.regionlalibertad.local:8080/geoserver/siar/wfs
```

##### Flujo de Datos y Sincronización ETL - Detalle Completo

**Dirección del Flujo:** On-Premise → Cloud (unidireccional)

**¿Quién realiza la replicación?**
- **Sistema automatizado (Script ETL)** - Ejecutado en servidor On-Premise o Cloud
- **Administrador TI (GRRNGA)** - Configura y monitorea el proceso
- **Editor GIS (GRRNGA)** - Marca datos como "listos para replicar" en gis_master

**¿Cómo se realiza la replicación?**

**Método de Comunicación On-Premise → Cloud:**

**Opción 1: Script ETL en Servidor On-Premise (RECOMENDADO)**
- El script ETL se ejecuta **directamente en el servidor On-Premise**
- Se conecta a PostgreSQL local (localhost) para leer datos
- Se conecta a PostgreSQL Cloud mediante:
  - **VPN Site-to-Site** entre red GRRNGA y Cloud Provider (AWS/Azure/GCP)
  - O **Conexión directa con firewall** permitiendo solo IP del servidor On-Premise
  - Puerto 5432 (PostgreSQL) abierto solo desde IP del servidor On-Premise
  - Autenticación mediante usuario/password o certificados SSL

**Opción 2: Script ETL en Cloud (ALTERNATIVA)**
- El script ETL se ejecuta **en un servidor/interfaz en Cloud** (ej: Lambda, Cloud Function, VM)
- Se conecta a PostgreSQL On-Premise mediante:
  - **VPN Site-to-Site** o **VPN Client** desde Cloud hacia red GRRNGA
  - O **SSH Tunnel** (port forwarding) para acceso seguro
  - O **Conexión directa** si el servidor On-Premise tiene IP pública (con firewall estricto)

**Configuración de Red Recomendada:**

```mermaid
graph LR
    subgraph ONPREM["ON-PREMISE (GRRNGA)"]
        POSTGRES_LOCAL[PostgreSQL<br/>IP: 192.168.1.10<br/>Puerto: 5432]
        ETL_CRON[Script ETL<br/>Cron Job<br/>Lee: localhost:5432]
    end
    
    subgraph CONEXION["Conexión Segura"]
        VPN[VPN Site-to-Site<br/>o<br/>Conexión Directa<br/>TLS/SSL]
    end
    
    subgraph CLOUD_BD["CLOUD (AWS/Azure/GCP)"]
        POSTGRES_CLOUD[PostgreSQL Cloud<br/>IP: db.cloud.com<br/>Puerto: 5432<br/>Firewall: Solo IP On-Premise]
    end
    
    POSTGRES_LOCAL -->|Lee datos| ETL_CRON
    ETL_CRON -->|Escribe datos| VPN
    VPN -->|PostgreSQL/TLS| POSTGRES_CLOUD
    
    style ONPREM fill:#fff4e1
    style CONEXION fill:#ffe0e0
    style CLOUD_BD fill:#e1f5ff
```

**Herramientas y Método:**
- **Script Python** con librerías: psycopg2, sqlalchemy, pandas, geopandas
- **pg_dump/pg_restore** para migraciones completas
- **ogr2ogr** (GDAL) para conversión de formatos geoespaciales
- **Transformación:** Simplificación de geometrías, validación de datos, conversión de formatos

**Seguridad:**
- **Autenticación:** Usuario/password fuerte o certificados SSL
- **Encriptación:** TLS/SSL en todas las conexiones
- **Firewall:** Solo permite conexiones desde IPs autorizadas
- **VPN:** Recomendado para mayor seguridad
- **Auditoría:** Logs de todas las conexiones y operaciones

**¿Cuándo se realiza la replicación?**
- **Frecuencia programada:** Diaria a las 2:00 AM (horario de menor uso)
- **Trigger manual:** Editor GIS puede solicitar replicación urgente desde Strapi CMS
- **Eventos:** Cuando se marcan datos como "publicables" en gis_master

**¿Dónde se realiza la replicación?**
- **Origen:** PostgreSQL/PostGIS On-Premise (schema:gis_master) en servidor físico GRRNGA
- **Destino:** PostgreSQL/PostGIS Cloud (schema:public_data) en servicio managed (RDS/Cloud SQL)
- **Ejecución del Script:** Servidor On-Premise (recomendado) o servidor/interfaz en Cloud

**Pipeline de Sincronización Detallado:**

**1. Preparación de Datos (On-Premise) - Editor GIS:**
```sql
-- Editor GIS marca datos como listos para replicación
UPDATE gis_master.layers_full 
SET replication_status = 'ready', updated_at = NOW()
WHERE validation_status = 'approved';

-- Simplificación de geometrías para web (automático o manual)
CREATE MATERIALIZED VIEW gis_master.layer_web_simplified AS
SELECT 
    id,
    name,
    ST_Simplify(geom, 0.001) AS geom_simplified, -- Tolerancia ajustable
    attributes,
    updated_at,
    replication_status
FROM gis_master.layers_full
WHERE replication_status = 'ready';

-- Refresh programado o manual
REFRESH MATERIALIZED VIEW gis_master.layer_web_simplified;
```

**2. Extracción y Transformación (Script ETL Automatizado):**

**Ubicación del Script:** Servidor On-Premise o Cloud (con acceso a ambas BD)

**Herramientas utilizadas:**
- **Python 3.9+** con librerías: psycopg2, sqlalchemy, pandas, geopandas
- **ogr2ogr** (GDAL) para conversión de formatos geoespaciales
- **pg_dump/pg_restore** para migraciones completas

**Script ETL (Ejemplo conceptual):**
```python
# Script ETL - etl_replication.py
import psycopg2
from sqlalchemy import create_engine
import logging
from datetime import datetime

# Configuración de logging
logging.basicConfig(
    filename='/var/log/siar/etl_replication.log',
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s'
)

def replicate_data():
    try:
        # Conexión a BD On-Premise (desde servidor On-Premise)
        conn_local = psycopg2.connect(
            host="localhost",  # o IP del servidor On-Premise
            database="siar_local",
            user="etl_user",  # Usuario con permisos de lectura
            password="***"
        )
        
        # Conexión a BD Cloud (mediante VPN o conexión segura)
        engine_cloud = create_engine(
            "postgresql://user:pass@rds.amazonaws.com:5432/siar_cloud"
        )
        
        # Extracción de datos procesados desde gis_master
        query = """
            SELECT 
                id, 
                name, 
                ST_AsGeoJSON(geom_simplified) as geom, 
                attributes,
                updated_at
            FROM gis_master.layer_web_simplified
            WHERE replication_status = 'ready'
            AND updated_at > %s
        """
        
        cursor = conn_local.cursor()
        last_sync = get_last_sync_date()  # Obtener última fecha de sincronización
        cursor.execute(query, (last_sync,))
        
        # Transformación y validación
        records = cursor.fetchall()
        validated_records = validate_and_transform(records)
        
        # Carga a Cloud (schema:public_data)
        if validated_records:
            df = pd.DataFrame(validated_records)
            df.to_sql(
                'geo_layers', 
                engine_cloud, 
                schema='public_data', 
                if_exists='append',
                index=False
            )
            
            # Marcar como replicado en On-Premise
            update_replication_status(conn_local, [r['id'] for r in validated_records])
            
            logging.info(f"Replicados {len(validated_records)} registros exitosamente")
        
        conn_local.close()
        
    except Exception as e:
        logging.error(f"Error en replicación: {str(e)}")
        send_alert_email(str(e))
        raise

if __name__ == "__main__":
    replicate_data()
```

**3. Programación y Ejecución:**

**Ubicación:** Servidor On-Premise (Ubuntu Server 22.04 LTS)

**Método de programación:**
- **Cron Job** (Linux) configurado en servidor On-Premise
- **Archivo crontab:** `/etc/cron.d/siar-etl-replication`
- **Configuración ejemplo:**
```bash
# Replicación diaria a las 2:00 AM
0 2 * * * /usr/bin/python3 /opt/siar/scripts/etl_replication.py >> /var/log/siar/etl.log 2>&1
```

**Frecuencias:**
- **Diaria (recomendado):** 2:00 AM para datos no críticos
- **Manual:** Editor GIS puede solicitar desde Strapi CMS
- **Urgente:** Administrador TI puede ejecutar script manualmente

**4. Validación y Logging:**

**Validaciones realizadas:**
- Verificación de integridad (checksums, conteo de registros)
- Validación de geometrías (ST_IsValid)
- Verificación de metadatos obligatorios
- Comparación de conteos antes/después de replicación

**Logging:**
- **Archivo de log:** `/var/log/siar/etl_replication.log`
- **Tabla de auditoría:** `public_data.replication_log` en BD Cloud
- **Campos:** timestamp, registros_replicados, estado, errores

**Notificaciones:**
- **Email automático** en caso de fallo a Administrador TI
- **Dashboard en Strapi CMS** con estado de última replicación
- **Alertas** si no se replica en 24 horas

**5. Seguridad de la Replicación:**

- **Conexión segura:** VPN o SSH Tunnel entre On-Premise y Cloud
- **Credenciales:** Usuario con permisos mínimos (solo lectura en On-Premise, escritura en Cloud)
- **Encriptación:** TLS/SSL en todas las conexiones
- **Auditoría:** Log completo de todas las operaciones de replicación

##### Gestión de Archivos GIS - Pipeline de Carga (Especialistas GIS)

**IMPORTANTE - Restricción de Acceso:**
- **Los especialistas GIS NO tienen acceso directo a la base de datos PostgreSQL/PostGIS**
- **NO pueden ejecutar consultas SQL directamente**
- **Solo pueden trabajar mediante QGIS o ArcGIS Pro** que se conectan a PostGIS
- **El acceso a la BD es controlado** mediante permisos de usuario limitados

**¿Quién realiza la carga de datos?**
- **Especialistas GIS (GRRNGA)** - Personal técnico con conocimiento en QGIS/ArcGIS Pro
- **Editor GIS (GRRNGA)** - Responsable de validar y aprobar datos para publicación

**¿Cómo se realiza la carga?**
- **Método:** QGIS (gratuito) o ArcGIS Pro (licenciado) como cliente de escritorio
- **Conexión:** QGIS/ArcGIS Pro se conecta a PostgreSQL/PostGIS On-Premise mediante DB Manager
- **Permisos:** Usuario de BD con permisos limitados (INSERT, UPDATE en schemas específicos, NO DELETE, NO DDL)
- **Sin acceso SQL directo:** Los especialistas NO pueden ejecutar comandos SQL manualmente

**¿Cuándo se realiza la carga?**
- **Según necesidad:** Cuando se recopilan nuevos datos o se completan análisis
- **Frecuencia:** Variable, según proyectos y recopilación de datos
- **Validación:** Editor GIS valida datos antes de marcarlos como "publicables"

**¿Dónde se realiza la carga?**
- **Origen:** Archivos GIS locales (Shapefiles, GeoTIFF, GeoJSON) en estaciones de trabajo
- **Destino:** PostgreSQL/PostGIS On-Premise (schema:gis_working inicialmente)
- **Procesamiento:** Datos se mueven de gis_working → gis_master después de validación

**Flujo de Trabajo Detallado:**

**1. Recopilación de Datos Brutos:**
- Especialista GIS recopila datos en campo o procesa información
- Archivos GIS se guardan localmente en estación de trabajo
- Formatos: Shapefile, GeoTIFF, GeoJSON, etc.

**2. Carga a PostGIS (vía QGIS/ArcGIS Pro):**
```
Especialista GIS:
1. Abre QGIS o ArcGIS Pro en estación de trabajo
2. Se conecta a PostgreSQL/PostGIS On-Premise mediante DB Manager
   - Host: IP del servidor On-Premise (red interna)
   - Database: siar_local
   - Usuario: gis_editor (permisos limitados)
   - Password: ***
3. Importa Shapefile/GeoTIFF a schema gis_working
   - QGIS: DB Manager → Import Layer/File
   - ArcGIS Pro: Catalog → Database → Import
4. Valida datos: CRS, atributos, geometrías
5. Aplica transformaciones necesarias (reproyección, limpieza)
```

**3. Validación y Procesamiento:**
- Editor GIS revisa datos en gis_working
- Valida calidad, completitud de metadatos
- Aplica correcciones si es necesario
- Marca como "validado" y mueve a gis_master

**4. Configuración en GeoServer:**
- Editor GIS accede a GeoServer (Web UI en puerto 8080)
- Crea nueva capa desde tabla PostGIS (gis_master)
- Configura estilos SLD
- Define permisos de acceso
- Genera cache de tiles (opcional)

**5. Registro de Metadatos en Strapi:**
- Editor GIS accede a Strapi CMS (vía VPN o red interna)
- Crea entrada en Content Type `GeoLayer`
- Registra metadatos: título, descripción, temática, etc.
- Asocia URLs de servicios OGC del GeoServer

**6. Replicación a Cloud:**
- Datos en gis_master se replican a Cloud mediante ETL (ver sección anterior)
- Editor GIS marca datos como "listos para replicar"

**Restricciones de Seguridad:**
- **Usuario de BD limitado:** Solo permisos INSERT/UPDATE en schemas específicos
- **Sin acceso a comandos DDL:** No puede crear/eliminar tablas o schemas
- **Sin acceso DELETE:** No puede eliminar datos directamente
- **Logging:** Todas las operaciones se registran en logs de auditoría
- **VPN requerida:** Acceso a Strapi CMS solo desde red interna o VPN

**Recomendación:** **QGIS/ArcGIS Pro** como método estándar. Es la solución más práctica, segura y eficiente, aprovechando herramientas que los especialistas ya dominan.

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

#### 2.2.6. Requisitos

**NOTA IMPORTANTE:** Ya no se desarrolla un Portal Web propio. La visualización de la información se realiza mediante el **SIAR del MINAM**, que ya cuenta con la estructura y páginas del SIAR para cada gobierno regional. Los requisitos se enfocan únicamente en:

1. **Aplicación Móvil Colaborativa** - Para recopilación de datos desde el campo
2. **Backend CMS** - Para gestión y procesamiento de datos
3. **Integración con API del MINAM** - Para publicación en el SIAR

##### Aplicación Móvil Colaborativa

**Requisitos No Funcionales de la App Móvil:**

| RNF | Especificación Mínima | Justificación y Criterio de Aceptación |
| :---- | :---- | :---- |
| **Arquitectura Móvil** | Desarrollo nativo multiplataforma (React Native u otra tecnología) como producto completamente separado del portal web. | La app móvil debe funcionar de manera independiente, con su propio ciclo de desarrollo y despliegue, compartiendo únicamente las APIs del backend. |
| **Modo Offline** | Funcionalidad completa sin conexión a internet, con sincronización posterior al recuperar conectividad. | Esencial para trabajo en campo donde la conectividad es limitada o inexistente. |
| **Acceso a Hardware** | Acceso completo a sensores nativos del dispositivo (GPS de alta precisión, cámara, acelerómetro). | Requerido para captura de datos geo-referenciados y fotografías en campo. |
| **Rendimiento** | Tiempo de inicio < 3 segundos, navegación fluida entre pantallas. | Experiencia de usuario óptima en dispositivos de gama media. |
| **Consumo de Batería** | Optimización para trabajo prolongado en campo (mínimo 4 horas de uso continuo con GPS activo). | Necesario para sesiones de trabajo en campo. |
| **Almacenamiento Local** | Capacidad de almacenar contribuciones pendientes y datos cacheados sin límites de espacio excesivos. | Permitir múltiples contribuciones offline antes de sincronizar. |
| **Seguridad** | Autenticación mediante OAuth 2.0 (Google Sign-In, Apple Sign-In) para ciudadanía, encriptación de datos sensibles en almacenamiento local. | Protección de datos de usuarios y contribuciones. Sistema de autenticación simple y general para facilitar acceso ciudadano. |
| **Notificaciones Push** | Sistema de notificaciones push nativas para alertas sobre estado de contribuciones. | Mantener a usuarios informados sobre moderación de sus aportes. |
| **Diseño UX/UI Nativo** | Interfaces que siguen las guías de diseño de Android (Material Design) e iOS (Human Interface Guidelines). | Experiencia nativa y familiar para usuarios. |

**Requisitos Funcionales de la App Móvil:**

La aplicación móvil está enfocada en la **colaboración ciudadana** para aportar información ambiental desde el campo. Basado en el modelo de datos acordado (2.1.3) y las temáticas ambientales (2.1.2), debe implementar:

**1. Sistema de Autenticación y Usuarios (Ciudadanía):**

- **Autenticación mediante OAuth 2.0** - Integración con proveedores externos:
  - **Google Sign-In** (OAuth 2.0)
  - **Apple Sign-In** (OAuth 2.0)
  - Autenticación simple sin necesidad de crear cuenta nueva
- Registro automático mediante OAuth (no requiere validación de email adicional)
- Perfil de usuario personalizable
- Gestión de preferencias de notificaciones
- Historial de contribuciones personales
- Dashboard personal con estadísticas de aportes
- **Nota:** Este sistema es para ciudadanía general, no para personal del Gobierno Regional

**2. Módulo de Contribuciones Colaborativas (Funcionalidad Principal):**

Basado en las 13 temáticas ambientales (2.1.2) y los tipos de recursos del modelo de datos (2.1.3):

- **Formularios de Contribución por Temática:**
  - **Reporte de Observaciones Ambientales:**
    - Calidad del agua (transparencia, color, presencia de residuos)
    - Calidad del aire (visibilidad, olores, contaminación visible)
    - Estado de biodiversidad (presencia de especies, estado de ecosistemas)
    - Condiciones del suelo (erosión, degradación)
    - Gestión de residuos (acumulación, vertederos ilegales)
  - **Registro Fotográfico Geo-referenciado:**
    - Captura de fotografías con cámara nativa
    - Captura automática de coordenadas GPS (alta precisión)
    - Timestamp automático
    - Descripción y etiquetas
    - Selección de temática asociada
    - Asociación con especies observadas (opcional)
    - Tipo de observación (amenaza, avistamiento, estado del ecosistema)
  - **Carga de Datos de Campo:**
    - Mediciones ambientales (temperatura, pH, conductividad, etc.)
    - Series temporales desde campo
    - Datos de monitoreo ciudadano
    - Asociación con indicadores ambientales existentes
  - **Reporte de Incidencias Ambientales:**
    - Vertimientos, deforestación, contaminación
    - Ubicación precisa con GPS
    - Evidencia fotográfica/videográfica
    - Descripción detallada del incidente
    - Severidad del impacto
    - Notificación urgente (opcional)
  - **Registro de Especies:**
    - Aves, flora, fauna observada
    - Ubicación exacta con GPS
    - Fotos y descripción
    - Estado de conservación observado
    - Asociación con temática de Biodiversidad

**3. Características Técnicas de Contribuciones:**

- Captura automática de coordenadas GPS (alta precisión)
- Integración con cámara nativa para fotos/videos
- Selección de ubicación en mapa si GPS no disponible
- Modo offline: guardar contribuciones localmente y sincronizar después
- Validación de formularios antes de envío
- Preview de contribución antes de enviar
- Adjuntar múltiples archivos (fotos, videos, documentos)
- Asociación de contribuciones con temáticas ambientales (2.1.2)
- Metadatos automáticos: fecha, hora, coordenadas, usuario

**4. Sistema de Moderación y Seguimiento:**

- Cola de revisión para contribuciones
- Notificaciones push sobre estado de aportes:
  - Contribución recibida
  - Contribución en revisión
  - Contribución aprobada
  - Contribución rechazada (con motivo)
- Historial completo de cambios y versionado
- Feedback a contribuyentes sobre aprobación/rechazo
- Re-envío de contribuciones rechazadas (con correcciones)

**5. Reconocimiento y Participación:**

- Dashboard personal de contribuciones del usuario
- Ranking de colaboradores más activos
- Badges por número de aportes validados
- Certificados de participación (opcional, descargables)
- Créditos en publicaciones generadas con datos colaborativos
- Estadísticas personales:
  - Total de contribuciones
  - Contribuciones aprobadas
  - Contribuciones pendientes
  - Contribuciones por temática

**6. Visualización de Información (Solo Consulta):**

- Acceso a información ambiental del portal (solo lectura):
  - Visualización de mapas con servicios OGC
  - Consulta de indicadores ambientales
  - Visualización de documentos públicos
  - Consulta de normas ambientales
- Descarga de capas geoespaciales para uso offline
- Búsqueda de información ambiental
- Filtros por temática y ámbito territorial

**7. Funcionalidades Offline:**

- Trabajar completamente sin conexión
- Guardar contribuciones pendientes localmente
- Sincronización automática al recuperar conectividad
- Caché de mapas base para uso offline
- Caché de datos consultados recientemente
- Indicador de estado de sincronización

**8. Integración con Servicios del Backend:**

- Consumo de API de Strapi para:
  - Autenticación
  - Envío de contribuciones
  - Consulta de información
  - Notificaciones
- Consumo de servicios OGC (WMS/WMTS) para:
  - Visualización de mapas
  - Descarga de capas para offline

#### 2.2.7. Despliegue y DevOps

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
   - URL: `staging.siar.regionlalibertad.gob.pe`

3. **Production (Cloud + On-Premise)**
   - Ambiente de producción final
   - Alta disponibilidad configurada
   - Monitoreo 24/7
   - URL: `siar.regionlalibertad.gob.pe`

##### CI/CD Pipeline

**Herramientas:**
- **Git** (repositorio de código)
- **Docker** (containerización recomendada pero no obligatoria)

**Repositorio de Código Fuente:**

**Propiedad del Código:**
- **El código fuente completo será propiedad del Gobierno Regional de La Libertad**
- Todos los derechos de propiedad intelectual del código desarrollado corresponden al Gobierno Regional de La Libertad
- El proveedor debe entregar el código fuente completo sin restricciones de uso, modificación o distribución por parte del Gobierno Regional

**Estructura del Repositorio:**
- **Repositorio Git único o múltiples repositorios** (según arquitectura):
  - Repositorio del Portal Web (Next.js/Nuxt.js)
  - Repositorio de la App Móvil (React Native/Flutter)
  - Repositorio del Backend CMS (Strapi u otro)
  - Repositorio de configuración e infraestructura (opcional)
- **Historial completo de commits** desde el inicio del desarrollo
- **Branches organizadas** (main, develop, feature branches)
- **Documentación en el repositorio:**
  - README.md con instrucciones de instalación y configuración
  - Documentación de arquitectura
  - Guías de desarrollo
  - Changelog

**Entrega del Repositorio:**
- Acceso completo al repositorio Git (GitHub, GitLab, Bitbucket u otro)
- Credenciales de acceso para el equipo del Gobierno Regional
- Transferencia de propiedad del repositorio al Gobierno Regional (si aplica)
- Backup del repositorio completo en formato comprimido

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

#### 2.2.8. Entregables y Transferencia de Conocimiento

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

**Entregables de Código Fuente y Repositorio:**
- **Repositorio Git completo** con todo el código fuente de:
  - Portal Web
  - Aplicación Móvil
  - Backend CMS
  - Configuraciones y scripts
- **Documentación técnica del código:**
  - Comentarios en el código
  - Documentación de funciones y clases principales
  - Guías de arquitectura
- **Transferencia de propiedad:**
  - Todos los derechos de propiedad intelectual del código desarrollado corresponden al Gobierno Regional de La Libertad
  - Acceso completo y sin restricciones al repositorio
  - Credenciales de acceso al repositorio
- **Backup del código fuente:**
  - Archivo comprimido del repositorio completo
  - Versionamiento completo con historial de commits

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

### 2.3. Identificación de proveedores

Identificar empresas de desarrollo de software y obtener 2 cotizaciones para el servicio.

### 2.4. Presupuesto detallado

Elaborar el presupuesto detallado para este servicio.