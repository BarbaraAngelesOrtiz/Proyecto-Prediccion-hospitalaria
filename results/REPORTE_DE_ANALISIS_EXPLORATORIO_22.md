# **REPORTE DE ANÁLISIS EXPLORATORIO - PREDICCIÓN DE OCUPACIÓN HOSPITALARIA**

**Fuente de información:**  
https://datosabiertos.jcyl.es/web/es/datos-abiertos-castilla-leon.html

La información corresponde a datos de ocupación hospitalaria tanto en planta como en UCI (unidades de cuidados intensivos) en todos los hospitales de las provincias 'Burgos', 'León', 'Valladolid', 'Segovia', 'Zamora', 'Ávila', 'Soria', 'Salamanca', 'Palencia' de Castilla y León. Actualización diaria.

- Hasta el 8 de septiembre no se incluyen Cunas, Incubadoras, Pediatría, Obstetricia, ni Psiquiatría.
- El número de camas en unidades de críticos incluye las de UCI (unidades de cuidados intensivos), REA (unidades de reanimación), URPA (unidades de reanimación postanestésica), y otras unidades con adecuada dotación para la atención de pacientes críticos.
- El número de camas en planta incluye aquellas a mayores que se han habilitado para la atención de enfermos COVID.
- El dato de camas iniciales corresponde a febrero de 2020.

Se busca analizar la información post-covid para predicción de demanda de camas hospitalarias, entendiendo la pandemia como un hecho extraordinario con una demanda extraordinaria a prever con programas de contingencia específicos.

![Tabla](/results/media/Imagen1.png)

> El dataset es de tipo estructurado, con un total de 20.190 filas y 10 columnas.
> 
> En ninguna de las columnas contamos con valores nulos.
> 
> El dataset tiene 1 una columna con información del tipo fecha/hora, dos columnas con información de tipo categórica: hospital y provincia, 1 columna con números enteros y siente con números decimales.
> 
> Por el momento se conservan todas las columnas, entendiendo que todas pueden aportar información a nuestro análisis, incluyendo el 'codigo_ine' que identifica el Municipio al que pertenece el hospital (más allá de la Provincia).

![Gráfico de líneas](/results/media/Imagen2.png)

![Gráfico de barras](/results/media/Imagen3.png)

De las gráficas de Número de camas disponibles y ocupadas por provincia se observa un momento especifico en el tiempo, entre junio 2023 y julio 2023, con un número mucho menor que el resto de los días para todas las provincias. Aún se desconoce si son datos reales que responden a una situación específica o un error en la carga de datos. A simple vista se observa que no responde a un patrón anual de variación de datos.

Se ha consultado a la Dirección General de Salud Digital - Consejería de Sanidad al email: dgsd.grs@saludcastillayleon.es

## ESTADÍSTICAS POR PROVINCIA - CAMAS OCUPADAS PLANTA

| Provincia   | N    | Media      | Mediana | Desv. Estándar | Coef. Variación (%) | p-value Normalidad | Es Normal? |
|-------------|------|------------|---------|----------------|---------------------|---------------------|------------|
| Salamanca   | 1345 | 600.548699 | 602.0   | 52.126248      | 8.679770            | 6.085570e-124       | No         |
| Ávila       | 1344 | 248.404018 | 249.0   | 22.820528      | 9.186859            | 1.488616e-01       | Sí         |
| Zamora      | 1344 | 289.274554 | 290.0   | 27.040502      | 9.347695            | 9.716148e-01       | Sí         |
| Palencia    | 1343 | 294.855547 | 297.0   | 31.132747      | 10.558644           | 5.315362e-33       | No         |
| Soria       | 1343 | 167.934475 | 168.0   | 21.068096      | 12.545426           | 4.340855e-06       | No         |
| Segovia     | 1338 | 214.436472 | 212.0   | 60.963349      | 28.429562           | 0.000000e+00       | No         |
| León        | 2690 | 448.235316 | 414.5   | 184.772997     | 41.222320           | 0.000000e+00       | No         |
| Valladolid  | 4032 | 306.808532 | 396.0   | 180.385992     | 58.794321           | 0.000000e+00       | No         |
| Burgos      | 4025 | 229.504596 | 69.0    | 239.345222     | 104.287768          | 0.000000e+00       | No         |

Como puede observarse la distribución de los datos varían por provincia: Salamanca es la provincia que tiene mayor demanda de camas y la que menor variabilidad tiene. Burgos, es la provincia que aparece con mayor variabilidad.

**Se entiende conveniente que a la hora de predecir el número de camas diario se realicen modelos de predicción por separado para cada provincia.**

![Gráfico](/results/media/Imagen4.png)

![Gráfico en cascada](/results/media/Imagen5.png)

En los diagramas BoxPlot se vuelve a poner en evidencia la variabilidad entre provincias. A su vez hay provincias que presentan **outliers (valores extremos) muy altos**, que podrían deberse a picos de demanda o demandas significativas en relación al tamaño del hospital.

Las medias de camas ocupadas en UCI están por debajo de las medias de las camas ocupadas en planta, pero mantienen la variabilidad en los datos.

![Gráfico](/results/media/Imagen6.png)

***

