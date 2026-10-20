--Documentación de README--
•	¿Cuántas filas devuelve cada consulta y por qué son distintas? Explicá con ejemplos concretos de los datos qué filas se eliminaron con UNION.
Las consultas con UNION devuelve la los registros sin duplicados, en cambio las consultas con UNION ALL devuelve la totalidad de registros, incluyendo duplicados como:
-	Monitor 4K 27”
-	Teclado Mecánico

•	¿Por qué UNION ALL es más eficiente que UNION? ¿Qué operación adicional realiza UNION internamente que consume más recursos?
UNION ALL contabiliza la totalidad de registros, lo que resulta útil al querer saber la totalidad de productos que se tienen en stock (y por ende no pierde tiempo ni memoria filtrando estos datos), a comparación de UNION que cruza la información de las tablas y filtra aquellos productos que se repiten (utilizando más tiempo y memoria realizando dicha tarea).

•	¿En qué casos de negocio usarías cada uno? Dá al menos dos ejemplos reales distintos a los del ejercicio.
El uso de UNION es útil por ejemplo para campañas de Marketing, el envío de mails masivos puede llegar a todos los contactos y de esta manera se puede filtrar entre un usuario registrado en “usuarios_newsletter” y ser “cliente”, evitando de esta manera que le llegue 2 veces.
El uso de UNION ALL puede ser útil en migraciones de registros históricos, donde se unifica la tabla de clientes activos con los clientes dados de baja. El uso de UNION ALL es más rápido porque el motor de la base de datos no gasta tiempo ni memoria filtrando nombres repetidos.

•	¿Qué pasa si las columnas de ambas consultas no coinciden en número o tipo? ¿Qué error genera SQL?
Si las columnas no coinciden, SQL arroja un error de sintaxis o de conversión.
