# 🚢 Shipping Market Analysis Dashboard

[![Looker Studio](https://img.shields.io/badge/Looker%20Studio-4285F4?style=flat&logo=googlelooker&logoColor=white)](https://lookerstudio.google.com/)
[![Google BigQuery](https://img.shields.io/badge/Google%20BigQuery-669DF6?style=flat&logo=googlecloud&logoColor=white)](https://cloud.google.com/bigquery)
[![SQL](https://img.shields.io/badge/SQL-003B57?style=flat&logo=postgresql&logoColor=white)](https://en.wikipedia.org/wiki/SQL)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0-blue.svg)]()

---

## 📋 Tabla de Contenidos

- [Descripción General](#-descripción-general)
- [Características Principales](#-características-principales)
- [Contenido del Proyecto](#-contenido-del-proyecto)
- [Herramientas y Tecnologías](#️-herramientas-y-tecnologías-utilizadas)
- [Configuración del Entorno](#️-configuración-del-entorno)
- [Estructura del Repositorio](#-estructura-del-repositorio)
- [Consultas SQL Implementadas](#-consultas-sql-implementadas)
- [Vistas Previas](#️-vistas-previas-del-proyecto)
- [Autor](#-autor)
- [Licencia](#-licencia)

---

## 📃 Descripción General

Dashboard de **Análisis del Mercado Naviero** desarrollado en **Looker Studio**, diseñado para analizar el flujo de importaciones y exportaciones del mercado peruano mediante datos de comercio marítimo. Este proyecto transforma datos de transporte marítimo en información estratégica para el sector logístico mediante:

- 🚢 **2 Vistas Analíticas:** Importación y Exportación con toggle (control de página) interactivo.
- 🌍 **Análisis Geográfico:** Cuota de mercado por continente, país y rutas marítimas.
- 📈 **Sector Económico:** Desglose por sectores clave: Agroindustria, Pesca, Textil, Minería y No Commodities.
- 🖱️ **Interactividad Avanzada:** Filtros dinámicos por año, mes, drill-down en jerarquías y enlaces a detalles.

---

## ✨ Características Principales

### 🔄 Transformaciones en BigQuery
- Carga y unificación de 3 archivos `.csv` históricos (2023, 2024, 2025) de ~75MB cada uno.
- Creación de una vista unificada (`Consolidado`) utilizando wildcards de tabla para optimizar la consulta y el mantenimiento.
- Limpieza y tipado de datos para asegurar la compatibilidad con los campos de Looker Studio.

### 📐 Modelo de Datos
- **Fuente Unificada:** Vista `Naviera.Consolidado` que actúa como tabla de hechos y dimensiones combinadas.
- **Campos Clave:** Año, Mes, Tipo de Operación (Import/Export), Línea Naviera, Continente, País, Puerto, Tipo de Contenedor, Tipo de Carga, Sector Económico y TEUs (Twenty-foot Equivalent Units).

### 🎨 Diseño Interactivo
- Navegación fluida entre vistas de Importación y Exportación mediante controles de página.
- Segmentación de datos (filtros) por período (Año/Mes) y categoría económica.
- Visualizaciones geoespaciales y gráficos de barras apiladas para análisis de participación de mercado.

---

## 📊 Contenido del Proyecto

| Página / Sección | Descripción | Contenido Principal |
|--------|-------------|---------------------|
| **Participación de Mercado** | Vista macro del flujo comercial | TEUs totales desglosados por Línea Naviera, Continente, País de origen/destino y rutas marítimas principales. |
| **Participación Portuaria** | Análisis de infraestructura | TEUs por tipo de contenedor (Dry, Reefer, etc.), tipo de carga y ranking de participación por puerto peruano (Callao, Paita, etc.). |
| **Bienes Primarios y Productos** | Análisis sectorial | Desglose detallado de productos finales y commodities (Agroindustria, Pesca, Textil, Minería) y su impacto en el volumen de carga. |

---

## 🛠️ Herramientas y Tecnologías Utilizadas

### Software Requerido
- **Looker Studio** (herramienta de visualización en la nube)
- **Google BigQuery** (almacenamiento y procesamiento de datos)
- Navegador web moderno (Chrome, Edge, Firefox)

### Fuente de Datos
- 📄 Archivos `.csv` históricos (2023, 2024, 2025) cargados en BigQuery.
- 🔗 Vista de BigQuery: `my-project-dashboard-468021.Naviera.Consolidado`

### Lenguajes y Tecnologías
- **SQL (Standard SQL de Google)** - Consulta, unión y transformación de datos en BigQuery.
- **Looker Studio Calculated Fields** - Métricas y dimensiones personalizadas dentro del reporte.

---

## ⚙️ Configuración del Entorno

### Prerequisitos
1. Tener una cuenta de Google activa.
2. Acceso a un proyecto de **Google Cloud Platform (GCP)** con la API de BigQuery habilitada.
3. Acceso a **Looker Studio**.

### Paso 1: Cargar Datos en BigQuery
1. Acceder a la consola de [Google Cloud BigQuery](https://console.cloud.google.com/bigquery).
2. Crear un Dataset llamado `Naviera`.
3. Cargar los 3 archivos `.csv` (Datos 2023, 2024, 2025) como tablas independientes con un prefijo común, por ejemplo: `Datos_2023`, `Datos_2024`, `Datos_2025`.

### Paso 2: Crear la Vista Unificada
Ejecutar la siguiente consulta SQL en BigQuery para crear una vista que unifique todos los años automáticamente:

<details>
<summary>📄 Ver Script SQL - Crear Vista Consolidada</summary>

```sql
CREATE OR REPLACE VIEW `my-project-dashboard-468021.Naviera.Consolidado` AS
SELECT * 
FROM `my-project-dashboard-468021.Naviera.Datos_*`;
```

</details>

### Paso 3: Conectar Looker Studio
1. Abrir <a href="https://lookerstudio.google.com">Looker Studio</a>.
2. Crear un Informe en blanco.
3. Seleccionar BigQuery como conector de datos.
4. Elegir el proyecto my-project-dashboard-468021, el dataset Naviera y la tabla/vista Consolidado.
5. Configurar los tipos de datos correctos (ej. Año como Número, Fecha como Fecha, TEUs como Número entero).
6. Insertar los gráficos, filtros y controles de página según el diseño del dashboard.

## 📂 Estructura del Repositorio

```
.
├── Análisis_Mercado_Naviero_(Perú).pdf   # Documento PDF con las capturas de todas las páginas del proyecto
├── .gitignore                            # Archivo de configuración Git
└── README.md                             # Este archivo de documentación
```

## 🧮 Consultas SQL Implementadas
El proyecto utiliza Standard SQL de Google BigQuery para la preparación de datos. A continuación se detallan las consultas clave:
### 🗄️ Unificación de Datos (Wildcard Tables)

<details>
<summary>Ver consulta de unificación</summary>
Esta consulta aprovecha las "Wildcard Tables" de BigQuery para unir todas las tablas que comienzan con Datos_ en una sola vista coherente, facilitando la actualización anual sin modificar el reporte.

```sql
CREATE OR REPLACE VIEW `my-project-dashboard-468021.Naviera.Consolidado` AS
SELECT 
    *
FROM `my-project-dashboard-468021.Naviera.Datos_*`;
```
</details>

### 📊 Ejemplo de Consulta Analítica (Participación por Puerto)

<details>
<summary>Ver consulta analítica de ejemplo</summary>

Consulta que podría utilizarse para pre-calcular o validar la participación de TEUs por puerto peruano en BigQuery antes de la visualización.

```sql
SELECT 
    Puerto,
    SUM(TEUs) AS Total_TEUs,
    ROUND(SUM(TEUs) * 100.0 / SUM(SUM(TEUs)) OVER(), 2) AS Porcentaje_Participacion
FROM `my-project-dashboard-468021.Naviera.Consolidado`
WHERE Tipo_Operacion = 'Importación'
GROUP BY Puerto
ORDER BY Total_TEUs DESC;
```

</details>

### 📅 Filtrado Temporal Dinámico
<details>
<summary>Ver consulta de filtrado temporal</summary>

Looker Studio inyecta parámetros de fecha, pero la estructura subyacente permite consultas eficientes como:

```sql
SELECT 
    EXTRACT(YEAR FROM Fecha) AS Anio,
    EXTRACT(MONTH FROM Fecha) AS Mes,
    Sector_Economico,
    SUM(TEUs) AS Total_TEUs
FROM `my-project-dashboard-468021.Naviera.Consolidado`
WHERE EXTRACT(YEAR FROM Fecha) IN (2023, 2024, 2025)
GROUP BY Anio, Mes, Sector_Economico
ORDER BY Anio DESC, Mes DESC;
```

</details>

## 🖼️ Vistas Previas del Proyecto
<details>
<summary>📸 Ver Capturas de Pantalla</summary>

  <img width="1028" height="1029" alt="image" src="https://github.com/user-attachments/assets/58c86df2-6e79-444c-b7ca-f29d16cf8fe3" />
  <img width="1033" height="1027" alt="image" src="https://github.com/user-attachments/assets/b56eb58b-4ddd-4316-b27c-7e46fc749700" />
</details>

<details>
<summary>🎥 Ver Video Demostrativo</summary>

   
   Ver en YouTube: https://youtu.be/V2xN9GXihJU?si=AaJ3NEEd8mwk4nzM
</details>

## 👤 Autor
Giancarlo Barrantes

Business Intelligence Developer | Power BI Specialist


<a href="https://www.linkedin.com/in/gb25"><img width="70" height="20" alt="image" src="https://github.com/user-attachments/assets/e0d69586-c6f9-4f66-9a3d-bc8dfa146463" /></a>
<a href="https://www.instagram.com/gbarrantes25"><img width="70" height="20" alt="image" src="https://github.com/user-attachments/assets/68773029-5e0f-49da-92e9-fb93a223dd09" />
</a>
<a href="https://www.tiktok.com/@gbarrantes25"><img width="65" height="20" alt="image" src="https://github.com/user-attachments/assets/349c87c0-1f3a-4368-8517-64a6012565c0" /></a>
<a href="https://www.youtube.com/@gbarrantes25"><img width="70" height="20" alt="image" src="https://github.com/user-attachments/assets/d9e2cb69-29ec-47fc-93ae-30896a7b533d" />
</a>

## 📝 Licencia
Este proyecto está bajo la Licencia MIT - ver el archivo <a href="https://mit-license.org/">LICENSE</a> para más detalles.

## ⭐ Agradecimientos
Si este proyecto te resultó útil, considera darle una ⭐ en GitHub y compartirlo con otros profesionales de Business Intelligence.

<div align="center">
   Hecho por <a href="https://gbarrantes25.github.io/">Giancarlo Barrantes</a>
</div>
