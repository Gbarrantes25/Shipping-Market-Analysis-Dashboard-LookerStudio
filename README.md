# Análisis de Mercado Naviero (Perú)


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


- [Enlace de Proyecto](https://lookerstudio.google.com/reporting/586bef1d-15bd-47a8-a943-0ab27c5edd9e)


