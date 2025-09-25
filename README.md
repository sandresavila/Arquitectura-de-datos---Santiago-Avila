# Arquitectura-de-datos---Santiago-Avila
NOTA: La base de datos y el archivo de Power BI pesan mas de 1GB, por ende no me deja subirlo a github, comparto el enlace de la carpeta en GoogleDrive. 
- Descargar archivo Power BI y base de datos: https://drive.google.com/drive/folders/13GB1ge4clwGaWVklKP-2d6TiNLshD88f?usp=sharing

Actividad en clase - Casos positivos de COVID-19 en Colombia.

A continuación, se describen los pasos que se llevaron a cabo en Power BI para preparar, limpiar y visualizar la información contenida en el conjunto de datos proporcionados por el instituto de salud. 

1. Carga del conjunto de datos.
Se inició el proceso importando la base de datos llamada “Casos positivos de COVID-19 en Colombia” desde el portal de Datos Abiertos del Gobierno de Colombia. Este conjunto contiene información detallada sobre los casos reportados en el país desde marzo de 2020, incluyendo variables como fecha de diagnóstico, estado del caso, ubicación geográfica, edad, sexo, entre otros.

2. Transformación de columnas de fechas.
Una vez cargada la base de datos, se procedió a trabajar con las columnas relacionadas con fecha de diagnóstico
Se cambió el tipo de dato de estas columnas al formato de texto, con el fin de facilitar la elaborqación de las graficas

3. Separación de fechas por componentes.
Con el objetivo de realizar análisis más específicos, se extrajeron los componentes individuales de las fechas, separándolos en: aAño, mes y dia.
Esta separación se hizo duplicando las columnas originales y aplicando transformaciones para obtener cada elemento temporal por separado.

4. Limpieza de datos.
Después de preparar las columnas de fechas, se realizó un proceso de limpieza del conjunto de datos:
Eliminación de columnas innecesarias: se retiraron aquellas que no eran relevantes para el análisis o que contenían información redundante.
Corrección y eliminación de errores: se eliminaron registros con valores nulos o con errores en diferentes columnas, garantizando así la calidad y consistencia de la información final.

5. Creación de visualizaciones gráficas.
Una vez transformados y depurados los datos, se procedió a la creación de gráficos interactivos en Power BI para facilitar la interpretación de los resultados. Algunas de las visualizaciones generadas fueron:
Gráfico de barras por estado del caso: muestra el número de casos leves, graves, fallecidos, etc.
Gráfico de columnas por año: representa la cantidad total de casos reportados por año desde 2020.
Gráfico de barras por municipio: presenta el recuento de casos por ubicación geográfica, destacando las ciudades con mayor número de contagios.
