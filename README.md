# MLRM-Juegos-Olimpicos
Modelo de Regresión Lineal de los Juegos Olímpicos de Verano


## PLANTEAMIENTO DEL PROBLEMA
En la investigación realizada para este proyecto, se trataron de analizar distintos factores que afectaran el medallero olímpico. Modelos remotos proponen dos variables como los mayores determinantes: el Producto Interno Bruto per cápita (PIB per cápita) y el tamaño de la población, con la premisa de que a mayor población y mayor potencial económico un país obtendría más medallas. Sin embargo, estos dos no son aspectos que afecten la competencia real, por lo que ninguno es directamente responsable por las medallas de los ganadores.

Ahora bien, como dijo Joseph Stiglitz: “Lo que medimos afecta las decisiones que tomamos”. Debemos tomar dejar claro que un mayor potencial económico no nos indica mejoras en el bienestar de las personas. Por lo que para este modelo se propondrá también el análisis del Índice Desarrollo Humano (IDH), como un factor determinante ya que en él se toman en cuenta tres variables en una: el índice de salud (esperanza de vida), el índice de educación (alfabetización de adultos y tasa bruta de matrícula) y el PIB per cápita.

Si suponemos que el talento deportivo se reparte equitativamente en los habitantes, el tamaño de la población de cada país también influiría la posibilidad de tener un atleta y por ende, tener un medallista olímpico. A mayor cantidad de participantes por país, habrá mayor probabilidad de obtener una medalla. La hipótesis en este caso es que una participación equitativa entre hombres y mujeres, incrementaría o incluso doblaría las oportunidades de tener atletas medallistas. Por lo tanto, la siguiente variable a considerar será la paridad de género, es decir, el número de mujeres participantes por cada país. Cabe mencionar que, se ha demostrado que al incrementarse la participación de mujeres, se decrementó el porcentaje de países con cero medallas

También tomaremos en cuenta si el país tuvo o tiene un gobierno soviético-comunista, debido a que en estos regímenes las Olimpiadas eran un instrumento político donde los atletas se entrenan desde muy jóvenes para llegar a un nivel de élite y reflejar el poderío del país.

Otro efecto interesante, en eventos como este, es la confianza que los equipos tienen al haber logrado obtener una medalla en emisiones anteriores. En otras palabras, ganar una medalla en los juegos anteriores aumenta la probabilidad de ganar en la siguiente emisión. Del mismo modo, los países que no ganan medallas pueden repetir ese resultado en un futuro. Por último, tomaremos en cuenta el fenómeno “host”. Luego de analizar los medalleros a lo largo del tiempo, se puede afirmar que el país anfitrión tiene ventajas: el equipo no viaja lejos, entonces está menos fatigado; el orgullo nacional y el hecho de estar familiarizado con las condiciones e instalaciones. Estas dos últimas variables serán evaluadas con variables dummy. Para este análisis, centraremos nuestra atención en los juegos a partir de la década de los noventas, puesto que fue a partir de ese año que el IDH se comenzó a calcular por el Programa de las Naciones Unidas para el Desarrollo (PNUD). De modo que, centraremos la atención en los juegos de 1992 a 2016. En la última competencia (Río 2016), se convocaron 207 naciones. Para fines prácticos tomaremos una muestra de 28 países que se escogerán con dos criterios. El primer punto es la constancia en los juegos, esto es, países con más participaciones en los juegos o que al menos cubran las que se analizarán. En segundo lugar, para tener variación en la muestra tenemos al menos dos participantes por continente; además se tomó en cuenta la accesibilidad a la información de cada país. La fuente de los datos no olímpicos, como el IDH, provienen de las bases de datos del Banco Mundial (BM) y Naciones Unidas (UN). Por otro lado, toda información relacionada con las Olimpiadas, proviene de las páginas del Comité Olímpico Internacional (COI) o en algunos casos del comité de cada nación.

## PLANTEAMIENTO DEL MODELO
En el curso de econometría, aprendimos que una herramienta para predecir
es la aplicación del Modelo de Regresión Lineal. En este caso, se quiere
entender la relación funcional entre la variable dependiente y las variables
independientes, además de estudias las posibles causas de la variación que se
pueda dar. En el Modelo de Regresión Lineal Múltiple se define

$𝑦 = 𝛽0 + 𝛽1𝑥1 + 𝛽2𝑥2 + ⋯ + 𝛽𝑘𝑥𝑘 + 𝑢$

Donde
𝑦: Es la variable dependiente
𝑥1, 𝑥2, … , 𝑥𝑘: Son las variables independientes
𝛽0: Es el coeficiente constante o intercepto
𝛽1, 𝛽2, … , 𝛽𝑘: Son los parámetros desconocidos que estarán bajo el
efecto ceteris paribus
𝑢: Es el término de error
En este trabajo, se propone analizar las variables mencionadas anteriormente
para el MRLM, que se estructuran de la siguiente forma
𝑚𝑒𝑑𝑎𝑙𝑠 = 𝛽0 + 𝛽1 𝐼𝐷𝐻 + 𝛽2 𝑙𝑜𝑔𝑝𝑜𝑝 + 𝛽3 𝑤𝑜𝑚𝑒𝑛 + 𝛽4 ℎ𝑜𝑠𝑡 + 𝛽5 𝑔𝑜𝑏
+ 𝛽6 𝑙𝑎𝑠𝑡 + 𝑢
Donde
𝑚𝑒𝑑𝑎𝑙𝑠: Es el total de medallas obtenidas por una nación
𝐼𝐷𝐻: Es el Índice Desarrollo Humano [0,1]
𝑙𝑜𝑔𝑝𝑜𝑝: Es el logaritmo del total del tamaño de la población
𝑤𝑜𝑚𝑒𝑛: Indica el número de mujeres participantes
ℎ𝑜𝑠𝑡: Indica si el país es anfitrión dummy {1,0}
𝑔𝑜𝑏: Indica si el país tiene o tuvo un gobierno comunista dummy {1,0}
𝑙𝑎𝑠𝑡: Es la cantidad de medallas obtenidas en los JJOO anteriores
