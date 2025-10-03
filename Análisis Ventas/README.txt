Integrantes: 
Jaider Andrés Diaz Buitrago
Santiago Andrés Avila Bohórquez

Este documento describe detalladamente el proceso llevado a cabo para la limpieza, transformación e integración de múltiples archivos CSV en Power BI utilizando Power Query, con el objetivo de preparar un modelo de datos consistente y listo para análisis. A continuación, se detallan los pasos realizados con cada conjunto de datos.

1. Contactos (Empleados, Clientes y Proveedores)

Se trabajó con tres archivos CSV diferentes (contactos_empleados, contactos_clientes y contactos_proveedores). El proceso aplicado a cada uno fue el siguiente:

a) Preparación inicial

	1. Se asignó la primera fila como encabezado en cada archivo.

	2. Se crearon columnas personalizadas para corregir y validar los campos Correo, Teléfono y País, utilizando expresiones condicionales en lenguaje M para identificar 	valores 	válidos y reasignarlos cuando fuera necesario.

b) Transformaciones aplicadas

	1. Nombre: Los valores "NA" se reemplazaron por null.

	2. Correo: Se validó la presencia del carácter @ para identificar correos correctos; en caso contrario, se verificaron otras columnas para ubicar el dato válido.

	3. Teléfono: Se validó el formato mediante prefijos comunes (+, 5, 3, etc.) y, si no coincidían, se buscó en otras columnas.

	4. País: Se creó una lista de valores válidos y se comprobó si el dato pertenecía a ella; de lo contrario, se buscó el valor correcto en otras columnas (Teléfono, 	Correo, 	Columna_extra, etc.).

c) Ajustes adicionales

	1. En contactos_proveedores, se reemplazaron las abreviaciones de país por su nombre completo.

	2. Se eliminaron las columnas originales después de crear las columnas personalizadas.

	3. Las nuevas columnas fueron renombradas con sus nombres originales.

	4. Finalmente, se renombraron los campos de las tres tablas para estandarizarlos y se utilizaron las funciones de “Anexar consultas” para unificarlas en una sola 	tabla 	consolidada de contactos.

2. Productos (productos_erp)

	El archivo de productos se trató de la siguiente forma:

	1. Se utilizó la función “Extraer tabla mediante ejemplos” para estructurar correctamente los datos desde el archivo fuente.

	2. Se asignó la primera fila como encabezado.

	3. Se aplicó un reemplazo de valores en la columna ProductoID para eliminar comillas dobles.

	4. Las columnas PrecioLista y Costo fueron convertidas a tipo decimal fijo.

	5. En la columna Activo, se normalizaron los valores para que solo existieran dos opciones: SI y NO.

	6. Se eliminó una columna irrelevante que no aportaba al análisis.

3. Ventas mensuales (ventas_mensuales)

	Para el archivo de ventas mensuales se realizaron los siguientes pasos:

	1. Se cargó el CSV sin delimitador debido a errores en la carga inicial.

	2. Se utilizó la herramienta “Separar columnas por delimitador”, ajustando el número de columnas a 14 para evitar columnas adicionales vacías.

	3. Se limpiaron los valores de los meses eliminando caracteres extraños como $ y ;.

	4.Todos los valores fueron convertidos a tipo número.

	5.Los errores detectados fueron reemplazados por el valor 0 para asegurar consistencia en los cálculos posteriores.

4. Ventas detalle (ventas_detalle)

	El archivo ventas_detalle fue procesado con el objetivo de estructurar los datos correctamente y permitir su relación con las órdenes:

	1. Se asignó la primera fila como encabezado.

	2. Se dividieron las columnas cuando fue necesario (por ejemplo, OrderID, ProductID, Cantidad, PrecioUnitario).

	3. Se cambiaron los tipos de datos:

		OrderID → Número entero

		Cantidad → Número entero

		PrecioUnitario → Decimal fijo

		ProductID → Texto

	4. La tabla quedó lista para ser relacionada con ventas_ordenes mediante el campo OrderID.

5. Ventas órdenes (ventas_ordenes)

	El archivo de órdenes de venta (ventas_ordenes) se procesó de la siguiente forma:

	1. Se asignó la primera fila como encabezado.

	2. Se separaron los valores en columnas correspondientes (OrderID, CustomerID, FechaOrden, Total, Estado).

	3. En la columna Total, se eliminaron símbolos como $ y comas, y se convirtió a decimal fijo.

	4. Se aplicaron transformaciones a la columna Estado para normalizar los valores (Enviado, Cancelado, Reembolsado, Pendiente).

	5. Se identificaron registros incorrectos (VO_mal) y se separaron en una nueva tabla, que posteriormente se combinó con los registros limpios (VObien) para crear una tabla 	unificada.

	6. Se eliminaron los duplicados en OrderID

	7. La columna FechaOrden fue transformada para unificar el formato y garantizar que el tipo de dato fuera Fecha.

6. Modelado y relaciones

	Una vez transformadas todas las tablas:

	Se establecieron las relaciones entre ellas en el modelo de datos:

	ventas_ordenes → ventas_detalle 
		Prueba: Cada orden registrada en ventas_ordenes puede tener muchos productos asociados en ventas_detalle.
	productos_erp → ventas_detalle
		Prueba: Cada producto en productos_erp puede aparecer en muchas ventas dentro de ventas_detalle.

	Se creó un modelo relacional coherente para análisis de ventas, productos y órdenes.

Conclusión

	El proceso de transformación de datos permitió limpiar, estructurar y consolidar la información proveniente de múltiples fuentes en un modelo de datos sólido, confiable y listo 	para análisis en Power BI. La combinación de funciones como columnas personalizadas, anexar consultas, reemplazo de valores, tipado de datos, y relaciones entre tablas facilitó la 	construcción de un sistema analítico integral que soporta visualizaciones precisas y toma de decisiones basada en datos.