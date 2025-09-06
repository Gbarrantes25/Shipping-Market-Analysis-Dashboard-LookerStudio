# Shipping Market Analysis (Perú)


## Consideraciones: 
- Los datos empleados no son datos reales.
- Fuentes de datos en formato de texto .csv.
- Los 3 archivos .csv se cargaron a Big Query, y se creó una vista llamada "Consolidado" utilizando la siguiente consulta SQL:  


  <code>CREATE VIEW `Naviera.Consolidado` AS (SELECT * FROM `my-project-dashboard-468021.Naviera.Datos_*`)</code>

  
  _Nota:_ El "\*" al final de `my-project-dashboard-468021.Naviera.Datos_*` en Big Query, representa que tomará todas las tablas que tengan como prefijo "Datos_\*".

   <img width="414" height="284" alt="image" src="https://github.com/user-attachments/assets/563351e4-dc8f-4ba7-ab19-2a0961620bc0" />

   
- ¿No era más fácil subir los archivos .csv directamnente a Looker Studio? Sí, pero Looker Studio y Big Query admiten archivos de .csv de máximo 100MB. Los archivos unidos superan ese límite.
- Looker Studio usará como fuente de datos una conexión a Big Query para extraer información de la vista "Consolidado".

  <code>SELECT * FROM `my-project-dashboard-468021.Naviera.Consolidado`</code>



  <details>
    <summary> Click para ver capturas </summary>
    <img width="1607" height="1050" alt="image" src="https://github.com/user-attachments/assets/a37ffab7-eeb0-46e0-875b-df7a73d185f5" />

    <img width="1671" height="947" alt="image" src="https://github.com/user-attachments/assets/0e159bf6-bbb0-4cf8-9ae6-7a7373e7a561" />
  </details>





## Objetivo: 

- Analizar la cuota de mercado (TEU's) que tenemos por continente, país y puerto de (origen/destino).
- Analizar la cuota de mercado (TEU's) por puerto peruano, así como ver el tipo de carga (LCL/FCL) y tipo de contenedor.
- Analizar los top de productos y bienes primarios más importados y exportados.
- <a href="https://lookerstudio.google.com/reporting/586bef1d-15bd-47a8-a943-0ab27c5edd9e" target="_blank">Enlace de proyecto</a>




# Shipping Market Analysis (Perú)

## 📃 Descripción General
Diseñado para analizar las importaciones y exportaciones, enfocado al mercado peruano.


## 📊 Contenido del proyecto
  - Participación de Mercado: Contiene una vista de información de TEU's por Línea naviera, contiennete, país y rutas marítimas.
  - Participación Portuaria: Contiene una vista de información de TEU's por tipo de contenedor, tipo de carga y participación por puerto peruano.
  - Bienes primarios y Productos: Contiene un análisis de productos finales y commodities.


## 🛠️ Herramientas y Tecnologías Utilizadas
- Visualización: Looker Studio.
- Fuente de Datos: Vista de Big Query
  - Comando de consulta: <code>CREATE VIEW `Naviera.Consolidado` AS (SELECT * FROM `my-project-dashboard-468021.Naviera.Datos_*`)</code>
- Lenguajes: SQL.


## ⚙️ Configuración del Entorno
- Software Necesario: Looker Studio y Big Query.
- Instalación:
  - Ingresar al enlace: [Proyecto](https://lookerstudio.google.com/reporting/586bef1d-15bd-47a8-a943-0ab27c5edd9e)


## 📂 Estructura del Repositorio
<code>.
  ├── Análisis_Mercado_Naviero_(Perú).pdf     # PDF con las vistas de todas las páginas del proyecto.
  └── README.md                               # Este archivo
</code>


## ✅ Características Principales
- Transformaciones en Power Query: Se realizaron procesos de limpieza y modelado de datos para optimizar el rendimiento.
- Medidas DAX: Se implementaron cálculos para análisis de empleados y segmentación por género.
  - <code>Unidades Vendidas = SUM(Ventas[Unidades])</code>
  - <code>Productos Distintos = DISTINCTCOUNT(Ventas[CódigoProducto])</code>
  - <code>Porcentaje de Ventas = DIVIDE([Unidades Vendidas],CALCULATE([Unidades Vendidas],ALL(Vendedores[Representante])))</code>
- Diseño Interactivo: Uso de segmentación de datos y segmentación de botones para agregar imagen.


## 🖼️ Vistas Previas del proyecto
<details>
  <summary>Escritorio</summary>
  <img width="1777" height="978" alt="image" src="https://github.com/user-attachments/assets/73e82d59-e64d-4c56-8c8a-3e1232fdb825" />
</details>
<details>
  <summary>Mobile</summary>
  <img width="538" height="886" alt="image" src="https://github.com/user-attachments/assets/e60adaf3-ddf0-4acf-af04-f10324ac0c70" />
  <img width="541" height="916" alt="image" src="https://github.com/user-attachments/assets/f585bc48-3841-4113-8d1b-f1e0090fbb82" />
</details>


## 👤 Autor
- Giancarlo Barrantes
- Lima, Perú
- [Linkedin](https://www.linkedin.com/in/gb25/)
