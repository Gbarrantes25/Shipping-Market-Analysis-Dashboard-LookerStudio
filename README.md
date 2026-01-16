# Shipping Market Analysis (Perú)

## 📃 Descripción General
Diseñado para analizar las importaciones y exportaciones, enfocado al mercado peruano (incluye datos ficticios).


## 📊 Contenido del proyecto
  - Participación de Mercado: Contiene una vista de información de TEU's por Línea naviera, contiennete, país y rutas marítimas.
  - Participación Portuaria: Contiene una vista de información de TEU's por tipo de contenedor, tipo de carga y participación por puerto peruano.
  - Bienes primarios y Productos: Contiene un análisis de productos finales y commodities.


## 🛠️ Herramientas y Tecnologías Utilizadas
- Fuente de datos:
  - [Datos 2023](https://docs.google.com/spreadsheets/d/1NFHB9kHIePkW-gXVcUuxzk06gSXOMJvK0COD3KpIrV0/edit?usp=sharing)
  - [Datos 2024](https://docs.google.com/spreadsheets/d/1YjHdPmS_foWoBMGu3F8W9wfiZD7Vyr_yX780QreKBbY/edit?usp=sharing)
  - [Datos 2025](https://docs.google.com/spreadsheets/d/1-tSD6dO8szA_4wIGgMLv7jaxSXKdnwA2AyyZEaSPDqQ/edit?usp=sharing)
- Visualización: Looker Studio.
- Fuente de Datos: Vista de Big Query
  - Comando de consulta: <code>SELECT * FROM my-project-dashboard-468021.Naviera.Consolidado</code>


- Lenguajes: SQL.


## ⚙️ Configuración del Entorno
- Software Necesario: Looker Studio y Big Query.
- Instalación:
  - Ingresar con tu cuenta de gmail a [Looker Studio](https://lookerstudio.google.com/overview)
  - Ingresar con tu cuenta de gmail a [Big Query](https://cloud.google.com/bigquery?utm_source=google&utm_medium=cpc&utm_campaign=latam-LATAM-all-es-dr-SKWS-all-all-trial-b-dr-1710136-LUAC0020579&utm_content=text-ad-none-any-DEV_c-CRE_688140023012-ADGP_Hybrid+%7C+SKWS+-+BRO+%7C+Txt_Usecases-Big+Query-KWID_43700079279114646-kwd-35927591586&utm_term=KW_big%20query-ST_big+query&gclsrc=aw.ds&gad_source=1&gad_campaignid=20946471024&gclid=EAIaIQobChMI0PamzJ_FjwMVxkVIAB3DahxvEAAYASAAEgK_m_D_BwE)
- [Enlace de Proyecto](https://lookerstudio.google.com/reporting/586bef1d-15bd-47a8-a943-0ab27c5edd9e)


## 📂 Estructura del Repositorio
<code>.
  ├── Análisis_Mercado_Naviero_(Perú).pdf     # PDF con las vistas de todas las páginas del proyecto.
  └── README.md                               # Este archivo
</code>


## ✅ Características Principales
- Carga de 3 archivos .CSV (peso aprox 75MB c/u, Big Query admite máximo 100MB) en Big Query
- Transfromación de datos en Big Query: Creación vista "Consolidado" para unir los 3 archivos .CSV con la siguiente consulta.

  
  <code>CREATE VIEW Naviera.Consolidado AS (SELECT * FROM my-project-dashboard-468021.Naviera.`Datos_*`)</code> 


- Diseño Interactivo: Uso de segmentación de datos y segmentación de botones para agregar imagen.


## 🖼️ Vistas Previas del proyecto
<details>
  <summary>Capturas</summary>
  Importación  
  <img width="1607" height="1050" alt="image" src="https://github.com/user-attachments/assets/a37ffab7-eeb0-46e0-875b-df7a73d185f5" />
  Exportación
  <img width="1671" height="947" alt="image" src="https://github.com/user-attachments/assets/0e159bf6-bbb0-4cf8-9ae6-7a7373e7a561" />
</details>


## 👤 Autor
- Giancarlo Barrantes
- Lima, Perú
- [Linkedin](https://www.linkedin.com/in/gb25/)
